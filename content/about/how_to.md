---
title: How To
type: docs
prev: docs/folder/
---

Begin by visiting the [Upload](https://tf-rest-burn-severity-ohi6r6qs2a-uc.a.run.app/upload) page - here you will be able to enter:

- An area of interest, either:
  - A shapefile (containing `.shp`, `.shx`, `.prj` and opitonally, `.dbf`) defining a fire boundary
  - A rough area of interest, where we attempt to derive the fire boundary using the `RBR` metric defined below
- Pre-fire and post-fire date ranges (approximately 1-3 weeks before ignition date, and 1-3 weeks after suppression)
- Fire event name
- Affiliation (for file organization / naming purposes)

After submission, the tool will:

1. Upload the burn boundary (or derive it using your defined AOI)
2. Collect satellite imagery for your selected dates within the burn boundary, producing fire severity metrics
3. Attempt to fetch [Ecological Dynamics Interpretive Tool](https://edit.jornada.nmsu.edu/) dominant cover information
4. Attempt to fetch [Rangeland Analysis Platform](https://rangelands.app/rap/) biomass data

If all four of these processes succeed, you will be presented download links for all of the analytical products generated, including an interactive map visualizing the results. If, at any time, you'd like to access these again, you can simply visit the [Directory](https://tf-rest-burn-severity-ohi6r6qs2a-uc.a.run.app/directory), where you can select your affiliation and fire event name once more to access these files again.
