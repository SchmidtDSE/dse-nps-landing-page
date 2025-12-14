---
title: How To
type: docs
weight: 1
math: false
---

## Using Disturbance Severity

Begin by visiting the [Disturbance Severity tool](https://tf-rest-burn-severity-prod-ohi6r6qs2a-uc.a.run.app/upload). There are two routes you can take to analyze a fire event: one where you upload a shapefile defining a fire boundary, and another where you draw an approximate boundary on the map.

In either case, you will provide the following information:

{{% steps %}}

### Park Unit

Select the park unit where the fire event occurred. Currently, Joshua Tree National Park and Mojave National Preserve are supported.

### Fire Event Name

A unique name for this particular fire event.

### Severity Metric

The fire severity metric to use for analysis. Three options are available:

- **Relativized Burn Ratio (RBR)** - Recommended for low-biomass environments like the Mojave Desert. RBR normalizes severity relative to pre-fire vegetation, so a fire that completely consumes sparse desert vegetation registers as high severity even though the absolute change is small.

- **Relativized differenced NBR (RdNBR)** - Similar to RBR but uses a different normalization approach. Useful for comparison with some federal severity products.

- **differenced NBR (dNBR)** - Measures absolute change in vegetation reflectance. Best suited for high-biomass environments like forests. In low-biomass areas, dNBR may underestimate severity because there is less vegetation to lose.

See [Methodology](/tools/disturbance-severity/methodology) for technical details on how these metrics are calculated.

### Date Ranges

Pre-fire and post-fire date ranges to collect imagery. We recommend 2-3 week windows before and after the fire event. Wider windows include more satellite passes but may introduce phenological bias.

{{% /steps %}}

{{< tabs items="Shapefile Route, Approximate AOI Route" >}}

{{< tab >}}

{{% steps %}}

#### Step 1 - Set analysis parameters

Fill in the park unit, fire event name, and severity metric. Click "Upload Shapefile" to upload a zipped shapefile defining the fire boundary.

![Set parameters](/how_to/1a.png)

#### Step 2 - Upload boundary shapefile

Select a zipped shapefile (`.zip`) containing your fire boundary. The shapefile should include the standard components (`.shp`, `.shx`, `.prj`, and optionally `.dbf`).

![Upload shapefile](/how_to/1b.png)

#### Step 3 - Set date ranges and submit

Specify the pre-fire and post-fire date ranges, then click "Process Fire Analysis" to begin processing.

![Set dates](/how_to/2.png)

#### Step 4 - Review severity results and accept boundary

After processing, you will see the fire severity map displayed on the right. The interface shows two workflow steps: Boundary Refinement and Vegetation Analysis. Since you uploaded a shapefile, click "Accept" under Boundary Refinement to confirm your boundary.

![Review results](/how_to/4.png)

#### Step 5 - Adjust severity thresholds (optional)

Use the Fire Severity Color Breaks panel to adjust the threshold values that define unburned, low, moderate, and high severity classes. These thresholds affect both the map visualization and the vegetation impact statistics—the breakpoints you set here are used when calculating zonal statistics for each severity class.

![Adjust thresholds](/how_to/8.png)

Click "Apply Changes" to update the visualization.

#### Step 6 - Run vegetation impact analysis

Click "Analyze" under Vegetation Analysis to compare fire severity against the park's vegetation map. This calculates how much of each vegetation community was affected at each severity level, using the threshold breakpoints you configured.

![Vegetation analysis](/how_to/5.png)

The results table shows:
- **Vegetation Community** - the vegetation type from the park's vegetation map
- **Total Hectares** - area of that vegetation type within the fire perimeter
- **% of Fire Perimeter** - proportion of the fire area covered by that vegetation type
- **Severity Distribution** - visual breakdown showing unburned, low, moderate, and high severity areas

Click the expand icon on any row to see detailed statistics including mean severity and standard deviation for each severity class.

#### Step 7 - Save or export results

You can download the vegetation impact data as a CSV file using the "Download CSV" button. To save your analysis state for later, use the "Save State" button. You can reload a previous analysis using "Upload State".

![Save state](/how_to/7.png)

{{% /steps %}}

{{< /tab >}}

{{< tab >}}

{{% steps %}}

#### Step 1 - Set analysis parameters

Fill in the park unit, fire event name, and severity metric.

![Set parameters](/how_to/1a.png)

#### Step 2 - Draw an approximate boundary

Using the polygon drawing tool on the map, draw an approximate boundary around the fire area. This does not need to be precise—you will refine it after viewing the severity results.

#### Step 3 - Set date ranges and submit

Specify the pre-fire and post-fire date ranges, then click "Process Fire Analysis" to begin processing.

![Set dates](/how_to/2.png)

#### Step 4 - Refine the boundary

After processing, you will see the fire severity map displayed. Click "Refine" under Boundary Refinement, then draw a more precise polygon around the burned area using the severity visualization as a guide. The map offers Street Map, Satellite, and Vegetation base layers to help with delineation.

![Draw refined boundary](/how_to/3_1a.png)

Click the first point to close the polygon, then click "Refine". When the shown boundary looks good, click "Accept" to apply your refined boundary.

![Accepted boundary](/how_to/4.png)

#### Step 5 - Adjust severity thresholds (optional)

Use the Fire Severity Color Breaks panel to adjust the threshold values. These thresholds affect both the visualization and the final vegetation impact statistics.

![Adjust thresholds](/how_to/8.png)

#### Step 6 - Run vegetation impact analysis

Click "Analyze" under Vegetation Analysis to compare fire severity against the park's vegetation map.

![Vegetation analysis](/how_to/5.png)

#### Step 7 - Save or export results

Download your results using "Download CSV" or save your analysis state for later using "Save State".

![Save state](/how_to/7.png)

{{% /steps %}}

{{< /tab >}}

{{< /tabs >}}
