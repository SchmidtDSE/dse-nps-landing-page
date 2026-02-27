---
title: Vegetation Modeling
weight: 2
---

**Status: Beta**  -  Core engine complete, model development ongoing

Vegetation Modeling is an orchestration layer around the [<span class="josh">josh</span>](https://joshsim.org) simulation engine. It takes fire severity boundaries from [Disturbance Severity](/tools/disturbance-severity) as external data, runs <span class="josh">josh</span> simulations to project vegetation recovery trajectories, and structures the output to help managers understand fire impacts over time.

<span class="josh">josh</span> itself is a standalone, open-source tool that can be used independently of the Disturbance Toolbox. Vegetation Modeling simply provides a streamlined workflow for applying <span class="josh">josh</span> to post-fire recovery scenarios.

![Josh Engine workflow](/static/tools/vegetation-modeling/josh_engine.png)

{{< cards >}}
{{< card link="https://joshsim.org" title="Launch josh" subtitle="External link to simulation engine" image="/static/tools/vegetation-modeling/josh_outlink.png" >}}
{{< /cards >}}

## Why Process-Based Modeling?

Empirical models (regressions trained on observed data) require data that are both spatially and temporally rich at the taxonomic resolution of interest. To model Joshua tree recovery specifically, we would need decades of repeated measurements across the landscape - data that do not currently exist.

Process-based models sidestep this limitation by building from ecological literature: how fast do seedlings grow? What conditions trigger germination? How does competition affect survival? These parameters can be estimated from targeted studies even without landscape-scale monitoring data.

## What is <span class="josh">josh</span>?

[<span class="josh">josh</span>](https://joshsim.org) is an open-source, spatially explicit simulation engine developed by DSE. It uses a domain-specific language (DSL) with friendly syntax inspired by HyperTalk, making stochastic, spatial, and stateful operations accessible without requiring deep software engineering knowledge.

Key features:

- **Domain-specific language** for specifying organisms, life stages, demographic rates, and environmental interactions
- **Scalable execution** from browser-based prototyping (via WebAssembly) to distributed cloud computing on hundreds of machines - with minimal or no code changes
- **Cloud-native geospatial formats** including GeoTIFF and netCDF for seamless integration with fire severity rasters
- **Transparent models** that ecologists can inspect, critique, and modify
- **Open source** under a permissive BSD license

<span class="josh">josh</span> was originally conceived during a cross-disciplinary workshop to address challenges in ecological modeling: the need for landscape-scale, stochastic, spatial simulations without requiring systems-level programming expertise.

<span class="josh">josh</span> is a standalone tool that can be used independently of the Disturbance Toolbox.

## Integration with Other Tools

In the context of this toolbox:

- **Inputs**: Severity rasters from [Disturbance Severity](/tools/disturbance-severity), plus climate scenarios and model parameters
- **Outputs**: Spatiotemporal projections of vegetation recovery (occupancy, abundance, community composition over time)
- **Downstream**: Outputs feed into [Resource Optimization](/tools/resource-optimization) for comparing intervention strategies

A <span class="josh">josh</span> model must be parameterized and validated before it can produce vegetation recovery projections and resource optimization outputs. Ideally, model development is completed in advance of a fire event so that projections are available as soon as severity data are produced. However, model development can also begin after a fire occurs - management planning would then start once the model is ready. The model needs to know how to respond to fire effects (mortality, reduced competition, seed bank impacts) and management interventions (seeding, planting, invasive removal), and these responses need to be built in before simulations can run.

## Python Integration (joshpy)

[joshpy](https://github.com/SchmidtDSE/joshpy) is a Python client library for <span class="josh">josh</span> that enables programmatic simulation execution, parameter sweeps, and experiment tracking from Python workflows. It supports both local (JAR-based) and remote (HTTP API via `Josh Cloud` or your own infrastructure) <span class="josh">josh</span> execution, making it flexible for interactive analysis and batch processing alike.

joshpy is currently used by the DSE team for model development and batch analysis, will later underpin the [Resource Optimization](/tools/resource-optimization) module, and is available for advanced users who want to integrate <span class="josh">josh</span> simulations into their own Python pipelines. See the [joshpy GitHub repository](https://github.com/SchmidtDSE/joshpy) and its associated [documentation](https://schmidtdse.github.io/joshpy/) for details.

---

{{< cards >}}
{{< card link="/tools/vegetation-modeling/how-to" title="How To" subtitle="Getting started with josh" icon="map" >}}
{{< card link="/tools/vegetation-modeling/methodology" title="Methodology" subtitle="Process-based modeling approach" icon="academic-cap" >}}
{{< card link="/tools/vegetation-modeling/references" title="References" subtitle="Key publications" icon="library" >}}
{{< /cards >}}
