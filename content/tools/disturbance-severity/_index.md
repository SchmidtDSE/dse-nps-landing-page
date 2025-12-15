---
title: Disturbance Severity
weight: 1
---

**Status: Beta** — Operational and in active use with NPS partners

Disturbance Severity uses Sentinel-2 satellite imagery to generate burn severity maps by comparing pre-fire and post-fire conditions. It provides Relativized Burn Ratio (RBR)—appropriate for low-biomass environments like the Mojave Desert—alongside standard dNBR metrics, and links severity to vegetation community data for immediate impact reporting.

{{< cards >}}
{{< card link="https://storage.googleapis.com/fire-recovery-web/dev/fireSeverity.html" title="Launch Disturbance Severity Tool" subtitle="External link" image="/flavor/severity.png" >}}
{{< /cards >}}

## Why RBR?

Federal agencies produce burn severity maps after major fires, but these typically use differenced Normalized Burn Ratio (dNBR), which is calibrated for high-biomass forests. In low-biomass environments like the Mojave Desert, dNBR is biased low—even complete vegetation loss produces a smaller absolute difference than a moderate fire in a high-biomass forest.

RBR scales fire intensity to pre-fire conditions at each location, so equivalent ecological damage produces equivalent severity values regardless of landscape type.

## Outputs

- **Severity rasters**: Cloud-optimized GeoTIFFs (dNBR, RBR) for use in GIS or downstream modeling
- **Vegetation impact summaries**: Severity statistics by vegetation community, formatted for grant applications and reporting
- **Interactive map**: Web-based visualization of results

## Integration with Other Tools

Severity rasters from this tool feed directly into [Vegetation Modeling](/tools/vegetation-modeling), where they serve as initial conditions for simulating post-fire recovery trajectories.

---

{{< cards >}}
{{< card link="/tools/disturbance-severity/how-to" title="How To" subtitle="Step-by-step guide to using the tool" icon="map" >}}
{{< card link="/tools/disturbance-severity/methodology" title="Methodology" subtitle="Technical details on severity metrics" icon="academic-cap" >}}
{{< card link="/tools/disturbance-severity/references" title="References" subtitle="Key publications" icon="library" >}}
{{< /cards >}}
