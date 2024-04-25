---
title: How To
type: docs
prev: docs/folder/
weight: 2
---

## User Process

Begin by visiting the [Upload](/upload) page - here you will be able to enter:

{{% steps %}}

### An area of interest

Either:

- A shapefile (containing `.shp`, `.shx`, `.prj` and opitonally, `.dbf`) defining a fire boundary
- A rough area of interest, where we attempt to derive the fire boundary using the `RBR` metric defined below

### Date Ranges

- Pre-fire and post-fire date ranges to collect imagery. The wider this window, the more satellite passes will be included in the analysis.

### Affiliation

The name (or acronym) for your group or organization. This is used to group individual groups' or users' disturbance analyses within the [Directory](/directory).

### Fire Event Name

A unique name for this particular fire event. After analysis, you'll be able to look within your `Affiliation` and find the fire event by name in the [Directory](/directory).

{{% /steps %}}

{{< callout type="warning" >}}
**IMPORTANT**: The combination of `Affiliation` and `Fire Event Name` must be unique - if you use a combination that exists already, you will overwrite the products derived from a previous analysis. Feel free to do this intentionally if you want to test out a few options for date ranges!
{{< /callout >}}

## Backend Process

After submission, the tool will:

{{% steps %}}

### Step 1

Upload the burn boundary to the backend server (or derive it using your defined AOI)

### Step 2

Collect satellite imagery for your selected dates within the burn boundary, producing fire severity metrics. As of now, `Sentinel2` imagery is collected via [Microsoft Planetary Computers' STAC API](https://planetarycomputer.microsoft.com/docs/quickstarts/reading-stac/).

### Step 3

Attempt to fetch [Ecological Dynamics Interpretive Tool](https://edit.jornada.nmsu.edu/) dominant cover information.

### Step 4

Attempt to fetch [Rangeland Analysis Platform](https://rangelands.app/rap/) biomass data.

{{% /steps %}}

If all four of these processes succeed, you will be presented download links for all of the analytical products generated, including an interactive map visualizing the results. If, at any time, you'd like to access these again, you can simply visit the [Directory](/directory), where you can select your affiliation and fire event name once more to access these files again.
