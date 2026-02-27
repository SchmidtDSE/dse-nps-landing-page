---
title: Methodology
type: docs
weight: 2
math: true
---

## Overview

This document describes the scientific methodology employed by the Fire Recovery Assessment System for deriving fire severity metrics from satellite imagery and quantifying vegetation impacts. The system implements a three-stage analytical workflow: (1) fire severity analysis from multispectral satellite data, (2) boundary refinement using severity-informed user delineation, and (3) vegetation impact assessment through zonal statistics.

---

## Disturbance Severity Metrics

The process of deriving disturbance severity metrics from satellite imagery involves comparing imagery from before and after a disturbance event to determine how different these images are in terms of reflective vegetation. Specifically, these metrics exploit the difference in two spectral bands provided by satellite imagery:

- **Near Infrared (NIR)**, which is highly reflective in healthy vegetation
- **Shortwave Infrared (SWIR)**, which is highly reflective in burned areas

![Exploiting Spectral Response Curves](https://tf-rest-burn-severity-ohi6r6qs2a-uc.a.run.app/static/home/nir_swir.jpg)

The system utilizes Sentinel-2 Level-2A imagery, which provides atmospherically corrected surface reflectance. Specifically, Band 8A (central wavelength 865 nm) serves as the NIR input, while Band 12 (central wavelength 2190 nm) provides the SWIR measurement.

---

## Absolute Metrics

Absolute metrics, such as the _Normalized Burn Ratio_ (NBR), describe the _absolute difference_ in reflectiveness of healthy vegetation, regardless of how much vegetation existed there in the first place.

$NBR = \frac{NIR - SWIR}{NIR + SWIR}$

$dNBR = NBR_{prefire} - NBR_{postfire}$

In theory, higher differences represent larger magnitudes of lost healthy vegetation. However, dNBR tends to be biased low in low-biomass areas or areas with sparse vegetation, because the absolute loss of vegetation - even in what would be considered an extreme fire event - is lower than the possible loss of vegetation in a higher biomass area.

---

## Relative Metrics

Relative metrics scale the estimate of fire intensity at any particular point to its own prefire conditions. Essentially, the intensity of a fire is expressed as a percentage of how much healthy vegetative signal was lost.

**Relativized differenced NBR (RdNBR):**

$RdNBR = \frac{dNBR}{|NBR_{prefire}|^{0.5}}$

To ensure numerical stability, the denominator is constrained to a minimum value of 0.001, preventing division by near-zero values in areas with minimal pre-fire vegetation signal.

**Relativized Burn Ratio (RBR):**

$RBR = \frac{dNBR}{NBR_{prefire} + 1.001}$

The additive constant of 1.001 serves two purposes: it ensures numerical stability when pre-fire NBR approaches zero or negative values, and it normalizes the output range for consistent interpretation.

RBR is designed to produce equivalent values across biomass levels, even when the high biomass area exhibits higher dNBR values than the low biomass area.

---

## Satellite Data Acquisition

### Data Source and Access

The system queries Sentinel-2 Level-2A (L2A) surface reflectance products through SpatioTemporal Asset Catalog (STAC) endpoints. The L2A product tier provides bottom-of-atmosphere reflectance with atmospheric corrections pre-applied by the European Space Agency's [Sen2Cor processor](https://step.esa.int/main/snap-supported-plugins/sen2cor/sen2cor-v2-10/).

### STAC Providers and Fallback Logic

The system accesses Sentinel-2 data through two STAC providers, each offering the same underlying satellite products but with different infrastructure and access patterns:

- **Element 84 Earth Search** (primary): A cloud-native STAC API hosted on AWS that provides direct access to Sentinel-2 data without authentication requirements. This provider uses asset naming conventions aligned with the Copernicus Data Space Ecosystem (e.g., `nir08`, `swir22`).

- **Microsoft Planetary Computer** (fallback): A comprehensive geospatial data platform that requires token-based authentication for asset access. This provider uses ESA's original band naming conventions (e.g., `B8A`, `B12`).

The system attempts data acquisition from Element 84 first. If no imagery is available for the requested spatiotemporal extent - or if the provider is temporarily unavailable - the system automatically falls back to Microsoft Planetary Computer. This redundancy ensures data availability even when individual providers experience outages or coverage gaps.

### Temporal Compositing

Rather than relying on single-date imagery, which may be affected by transient atmospheric conditions or sensor artifacts, the system employs temporal median compositing. For both pre-fire and post-fire periods, all available observations within the user-specified date ranges are aggregated using the median value at each pixel location.

The median operator is expected to be robust to outliers: when multiple observations are available, anomalous values caused by undetected clouds, cloud shadows, sensor noise, or atmospheric haze should be suppressed. For example, if five observations are available for a given pixel and one is affected by thin cirrus cloud (resulting in an anomalously high reflectance), the median will select the middle value, reducing the influence of the contaminated observation. Longer temporal windows increase the number of available observations, which we expect to improve the reliability of the median estimate. However, excessively long windows risk capturing phenological changes (seasonal vegetation growth or senescence) unrelated to the fire event, which could bias the severity estimate. We are actively [validating these assumptions](https://github.com/SchmidtDSE/fire-recovery-validation/) across a range of conditions.

### Spatial Processing

User-provided boundary geometries are buffered by 20% of their width and height (capped at 0.25 degrees) prior to data acquisition. This buffering is intended to provide complete data coverage at boundary edges and accommodates potential spatial misalignment between user-drawn boundaries and satellite data grids. All fire severity products are generated in the WGS84 geographic coordinate reference system (EPSG:4326).

### Cloud and Quality Considerations

The L2A product includes a Scene Classification Layer (SCL) that identifies cloud, cloud shadow, and other quality-affecting conditions. While the current implementation does not explicitly mask using SCL, the temporal median compositing strategy implicitly reduces cloud influence: cloud-affected pixels are expected to appear as statistical outliers and be suppressed by the median operator. Users should nevertheless select date ranges that minimize cloud probability for their region of interest.

---

## Fire Severity Analysis Workflow

### Input Requirements

The fire severity analysis requires:
- An approximate boundary polygon defining the area of interest
- A pre-fire date range (recommended: 2-3 weeks prior to fire ignition)
- A post-fire date range (recommended: 2-3 weeks following fire containment)

Shorter temporal windows are preferred because they minimize the risk of capturing vegetation changes unrelated to the fire event. Longer windows may introduce bias from seasonal phenology, drought stress, or other environmental factors that alter vegetation reflectance independently of fire effects.

### Processing Pipeline

1. **Data Acquisition**: Sentinel-2 imagery is queried from STAC endpoints for both temporal windows, filtered to the buffered area of interest.

2. **Temporal Aggregation**: Median reflectance values are computed independently for pre-fire and post-fire periods, yielding two representative composite images.

3. **Spectral Index Calculation**: NBR is computed for both composites, followed by derivation of dNBR, RdNBR, and RBR difference metrics.

4. **Spatial Alignment**: Pre-fire and post-fire arrays are aligned to ensure identical spatial dimensions and coordinate grids prior to differencing operations.

5. **Output Generation**: Each metric is exported as a Cloud Optimized GeoTIFF (COG) with DEFLATE compression, Float32 precision, and multi-resolution overviews for efficient web visualization.

### Output Products

The analysis generates five COG files:
- **Pre-fire NBR**: Baseline vegetation condition
- **Post-fire NBR**: Post-disturbance vegetation condition
- **dNBR**: Absolute severity (pre-fire NBR minus post-fire NBR)
- **RdNBR**: Relativized severity normalized by pre-fire conditions
- **RBR**: Alternative relativized severity with enhanced low-biomass performance

---

## Boundary Refinement

### Purpose

The initial fire severity analysis uses an approximate boundary that may extend beyond or fail to capture the actual fire perimeter. The boundary refinement stage enables users to delineate a more precise fire boundary informed by the severity visualization, ensuring that subsequent vegetation impact analysis accurately represents the affected area.

### Refinement Process

1. **Visual Interpretation**: Users view the fire severity COGs in a web mapping interface, where burned areas are visually distinguishable from unburned areas based on severity values.

2. **Boundary Delineation**: Users draw a refined polygon that more accurately captures the fire perimeter, excluding unburned areas and including burned areas that may have extended beyond the original approximate boundary.

3. **Spatial Clipping**: The system clips all fire severity COGs to the refined boundary geometry using an inclusive boundary treatment (pixels touching the boundary edge are retained).

4. **Product Regeneration**: New COGs are generated with the refined spatial extent, preserving all original data values and metadata within the clipped region.

### Technical Implementation

The clipping operation employs exact geometry intersection rather than bounding-box approximation. This ensures that irregular fire perimeters are accurately represented in the refined products. The original coarse-boundary products are retained for reference, allowing comparison between initial and refined extents.

### Note on Automatic Boundary Derivation

A previous version of this system included automatic fire boundary derivation using image segmentation techniques (specifically, threshold-based segmentation via scikit-image). This approach attempted to delineate fire perimeters algorithmically by identifying pixels exceeding severity thresholds and grouping them into contiguous regions.

This functionality was removed due to limitations in accuracy, particularly for large fires in heterogeneous landscapes. The segmentation algorithm proved overly sensitive to landscape variability: agricultural fields, urban areas, water bodies, and other non-vegetated surfaces frequently triggered false positives or disrupted boundary continuity. Manual refinement generally produced more accurate results than the automated approach in our testing. Exploratory analysis of this derived boundary approach is documented in [this notebook](https://github.com/SchmidtDSE/burn-severity-mapping-poc/blob/dev/exploratory/derived_boundary_eda.ipynb).

Future development may reintroduce automated boundary assistance contingent on improved methodology, potentially incorporating machine learning-based segmentation or multi-criteria classification that accounts for land cover context.

---

## Vegetation Impact Analysis

### Analytical Framework

The vegetation impact analysis quantifies how fire severity is distributed across different vegetation communities within the refined fire boundary. This provides ecologically meaningful summaries that support recovery planning and resource prioritization.

### Data Integration

The analysis integrates three spatial datasets:
- **Fire severity raster**: The RBR (or user-selected metric) COG from fire severity analysis
- **Vegetation map**: A vector dataset (GeoPackage format) containing classified vegetation polygons
- **Fire boundary**: The refined boundary GeoJSON from the boundary refinement stage

### Coordinate Reference System Standardization

To ensure accurate area calculations, all datasets are reprojected to a projected coordinate system (UTM Zone 11N, EPSG:32611) prior to analysis. Geographic coordinates are inappropriate for area measurements due to varying ground distances per degree at different latitudes.

### Severity Classification

Continuous fire severity values are classified into discrete severity categories using user-specified breakpoints provided by the frontend:

- **Unburned**: Severity value below the first threshold
- **Low Severity**: Severity value between first and second thresholds
- **Moderate Severity**: Severity value between second and third thresholds
- **High Severity**: Severity value at or above the third threshold

These thresholds may be adjusted based on the specific severity metric, ecosystem type, and management context.

### Zonal Statistics Computation

For each vegetation community, the system computes area-based statistics using the exactextract algorithm:

1. **Geometry Consolidation**: Multiple polygons of the same vegetation type are unified into a single geometry to prevent double-counting in overlapping regions.

2. **Pixel Counting**: The number of pixels falling within each severity class is enumerated for each vegetation community. Boundary pixels (those intersecting polygon edges) are included using an "all-touched" treatment.

3. **Area Calculation**: Pixel counts are converted to hectares using the product of pixel dimensions derived from the raster geotransform. The NIR and SWIR bands used for NBR calculation are provided at 20-meter resolution; thus each pixel represents approximately 0.04 hectares.

4. **Statistical Aggregation**: Mean severity and standard deviation are computed for each vegetation-severity combination using pixel-weighted averaging across constituent polygons.

5. **Percentage Derivation**: Within-vegetation percentages (proportion of each vegetation community in each severity class) and overall percentages (proportion of total study area represented by each vegetation community) are calculated.

### Output Products

The analysis produces two complementary outputs:

**Tabular Export (CSV)**: A matrix format with vegetation communities as rows and columns containing:
- Hectares in each severity class (unburned, low, moderate, high)
- Percentage of each vegetation community in each severity class
- Mean severity and standard deviation for each severity class
- Total hectares and overall percentage of study area

**Structured Data (JSON)**: A hierarchical format optimized for web visualization, including:
- Vegetation community names and programmatically-assigned display colors
- Nested severity breakdown with hectares, percentages, and statistical measures
- Summary statistics for dashboard displays

---

## Data Quality and Limitations

### Temporal Considerations

Fire severity metrics are sensitive to the selection of pre-fire and post-fire date ranges. Pre-fire imagery should capture typical vegetation conditions prior to fire occurrence, avoiding periods of drought stress, phenological dormancy, or prior disturbance. Post-fire imagery should be acquired after fire suppression activities have concluded but before significant vegetation recovery has occurred.

### Spatial Resolution

Sentinel-2 provides variable spatial resolution depending on the spectral band: 10 meters for visible and broad NIR bands, 20 meters for red-edge, narrow NIR (B8A), and SWIR bands, and 60 meters for atmospheric bands. The NBR calculation uses Band 8A (865 nm) and Band 12 (2190 nm), both of which are provided at 20-meter resolution. This resolution is appropriate for landscape-scale fire mapping but may not capture fine-scale fire effects such as individual tree mortality or small unburned patches within the fire perimeter.

### Vegetation Map Sources and Accuracy

The system currently includes preloaded vegetation maps for two National Park Service units: **Joshua Tree National Park** and **Mojave National Preserve**. These maps were developed through NPS Inventory and Monitoring programs and represent the best available vegetation classification data for these protected areas. The accuracy of vegetation impact statistics is contingent upon the accuracy of these input maps; classification errors in the vegetation layer propagate directly to the impact statistics.

Additional vegetation maps may be incorporated by providing a GeoPackage file with polygon geometries and a vegetation type attribute. The system requires a schema definition that maps the source attribute names to the standard internal representation. Users should consider the vintage, methodology, and documented accuracy of any vegetation maps when interpreting results.

### Edge Effects

Pixels at fire perimeter boundaries may exhibit mixed spectral signatures where burned and unburned areas occur within the same pixel footprint. The "all-touched" pixel selection approach may slightly overestimate affected areas near boundaries.

---

## Output Specifications

### Cloud Optimized GeoTIFF Parameters

| Parameter | Value |
|-----------|-------|
| Data Type | Float32 |
| NoData Value | -9999.0 |
| Compression | DEFLATE |
| Tiling | 256 x 256 pixels |
| Overviews | Generated with average resampling |
| Coordinate Reference System | EPSG:4326 (WGS84) |

### STAC Metadata

All outputs are cataloged using the SpatioTemporal Asset Catalog (STAC) specification, enabling standardized discovery and access. Each fire event generates a STAC Item containing:
- Spatial extent (bounding box and geometry)
- Temporal extent (pre-fire and post-fire date ranges)
- Asset links to COG and vector outputs
- Processing metadata (software version, parameters)

### Public Data Access

The STAC catalog and all generated assets are publicly accessible via Google Cloud Storage. The catalog root is available at:

```
https://storage.googleapis.com/fire-recovery-store/stac/catalog.json
```

The catalog follows the standard STAC hierarchy:
- **Root catalog**: `catalog.json`  -  contains links to all collections
- **Collections**: `collections/{collection-id}/collection.json`  -  fire-severity, fire-boundaries, vegetation-matrices
- **Items**: `collections/{collection-id}/items/{item-id}.json`  -  individual analysis results

All COG assets referenced in STAC items are served from the same storage bucket and support HTTP range requests for efficient partial reads by web mapping clients.
