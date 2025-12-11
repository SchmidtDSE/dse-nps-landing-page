---
title: How To
type: docs
weight: 1
math: false
---

## Using Disturbance Severity

Begin by visiting the [Disturbance Severity tool](https://tf-rest-burn-severity-prod-ohi6r6qs2a-uc.a.run.app/upload). There are two routes you can take to analyze a fire event: one where you upload a shapefile defining a pre-defined fire boundary, and another where you provide an approximate idea of where the fire is.

In either case, you will provide the following information:

{{% steps %}}

### An area of interest

This will be the area where the fire event occurred. You can either upload a shapefile defining the burn boundary, or you can draw a polygon on the map to define the area of interest. Both routes are described below.

### Date Ranges

Pre-fire and post-fire date ranges to collect imagery. The wider this window, the more satellite passes will be included in the analysis.

### Affiliation

The name (or acronym) for your group or organization. This is used to group individual groups' or users' disturbance analyses.

### Fire Event Name

A unique name for this particular fire event. After analysis, you'll be able to look within your `Affiliation` and find the fire event by name.

{{% /steps %}}

{{< callout type="warning" >}}
**IMPORTANT**: The combination of `Affiliation` and `Fire Event Name` must be unique - if you use a combination that exists already, you will overwrite the products derived from a previous analysis. Feel free to do this intentionally if you want to test out a few options for date ranges!
{{< /callout >}}

{{< tabs items="Approximate AOI Route, Shapefile Route" >}}

{{< tab >}}

{{% steps %}}

#### Step 1 - Draw an approximate AOI

Using the tools available (either a rectangle or polygon), draw an approximate area of interest where the fire event occurred.

![Draw AOI](/static/how_to/aoi_step1.png)

#### Step 2 - Submit fire information

Fill out the form with the required information, described above, and click the `Submit` button.

![Submit form](/static/how_to/both_step2.png)

#### Step 3 - Review intermediate disturbance product

After a few moments (to minutes, depending on the size of the fire), you will be presented with a map of the Relativized Burn Ratio (see [Methodology](/tools/disturbance-severity/methodology)) derived from the satellite imagery within the entire approximate AOI.

![Review RBR](/static/how_to/aoi_step3.png)

#### Step 4 - Mark 'seed' points for fire perimeter segmentation

Using the `Marker` tool (click the point icon on the left side of the map), click within the burn boundary to provide 'seed' points for the fire perimeter segmentation algorithm. Essentially, this limits the burn boundary to those thresholded from your seed points, preventing the algorithm from including areas that are not burned outside of the burn boundary.

You can use multiple seed points to include areas that are not connected together, but that are part of the same fire event.

![Mark seed points](/static/how_to/aoi_step4.png)

#### Step 5 - Submit 'seed' points

Click the submission icon to submit your seed points.

![Submit seeds](/static/how_to/aoi_step5.png)

#### Step 6 - Review derived products

If all steps are successful, you will be presented with download links for the derived products.

![Download products](/static/how_to/aoi_step6.png)

{{% /steps %}}

{{< /tab >}}

{{< tab >}}

{{% steps %}}

#### Step 1 - Upload a shapefile

You can upload a shapefile (containing `.shp`, `.shx`, `.prj` and optionally, `.dbf`) defining a known fire boundary.

![Upload shapefile](/static/how_to/shapefile_step1.png)

#### Step 2 - Submit fire information

Fill out the form with the required information, described above, and click the `Submit` button.

![Submit form](/static/how_to/both_step2.png)

#### Step 3 - Review derived products

If all steps are successful, you will be presented with download links for the derived products.

![Download products](/static/how_to/shapefile_step3.png)

{{% /steps %}}

{{< /tab >}}

{{< /tabs >}}

---

## Backend Process

After submission, the tool will:

{{% steps %}}

### Step 1

Upload the burn boundary to the backend server (or derive it using your defined AOI)

### Step 2

Collect satellite imagery for your selected dates within the burn boundary, producing fire severity metrics. As of now, `Sentinel2` imagery is collected via [Microsoft Planetary Computer's STAC API](https://planetarycomputer.microsoft.com/docs/quickstarts/reading-stac/).

### Step 3

Attempt to fetch [Ecological Dynamics Interpretive Tool](https://edit.jornada.nmsu.edu/) dominant cover information.

### Step 4

Attempt to fetch [Rangeland Analysis Platform](https://rangelands.app/rap/) biomass data.

{{% /steps %}}

If all four of these processes succeed, you will be presented download links for all of the analytical products generated, including an interactive map visualizing the results.
