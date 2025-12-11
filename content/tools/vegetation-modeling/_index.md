---
title: Vegetation Modeling
weight: 2
---

**Status: Beta** — Core engine complete, model development ongoing

Vegetation Modeling uses the [`josh`](https://joshsim.org) simulation engine to project multi-decadal vegetation recovery trajectories. Models are built from ecological first principles—germination rates, growth curves, mortality schedules, competitive interactions—rather than trained on historical data.

{{< cards >}}
{{< card link="https://joshsim.org" title="Launch josh" subtitle="External link to simulation engine" image="/static/about.png" >}}
{{< /cards >}}

## Why Process-Based Modeling?

Empirical models (regressions trained on observed data) require data that are both spatially and temporally rich at the taxonomic resolution of interest. To model Joshua tree recovery specifically, we would need decades of repeated measurements across the landscape—data that don't exist and likely never will.

Process-based models sidestep this limitation by building from ecological literature: how fast do seedlings grow? What conditions trigger germination? How does competition affect survival? These parameters can be estimated from targeted studies even without landscape-scale monitoring data.

## What is josh?

[josh](https://joshsim.org) is an open-source, spatially explicit simulation engine developed by DSE. It provides:

- A domain-specific language for specifying organisms, life stages, demographic rates, and environmental interactions
- Browser-based execution for small simulations
- Cloud scaling for landscape-level analysis
- Transparent models that ecologists can inspect, critique, and modify

josh is a standalone tool that can be used independently of the Disturbance Toolbox.

## Integration with Other Tools

In the context of this toolbox:

- **Inputs**: Severity rasters from [Disturbance Severity](/tools/disturbance-severity), plus climate scenarios and model parameters
- **Outputs**: Spatiotemporal projections of vegetation recovery (occupancy, abundance, community composition over time)
- **Downstream**: Outputs feed into [Resource Optimization](/tools/resource-optimization) for comparing intervention strategies

A josh model must be parameterized and validated *before* a fire event occurs. The model knows how to respond to fire effects (mortality, reduced competition, seed bank impacts) and management interventions (seeding, planting, invasive removal), but these responses need to be built in ahead of time.

---

{{< cards >}}
{{< card link="/tools/vegetation-modeling/how-to" title="How To" subtitle="Getting started with josh" icon="map" >}}
{{< card link="/tools/vegetation-modeling/methodology" title="Methodology" subtitle="Process-based modeling approach" icon="academic-cap" >}}
{{< card link="/tools/vegetation-modeling/references" title="References" subtitle="Key publications" icon="library" >}}
{{< /cards >}}
