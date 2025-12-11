---
title: DSE Disturbance Toolbox
width: full
---

{{< callout >}}

**A suite of tools for post-fire decision support, developed in partnership between UC Berkeley's [Eric and Wendy Schmidt Center for Data Science and Environment](https://dse.berkeley.edu/) and the [National Park Service](https://www.nps.gov).**

{{< /callout >}}

## The Challenge

After a wildfire, land managers face a "decision crush": they need to rapidly assess damage, predict vegetation recovery trajectories, decide on management interventions, and eventually evaluate whether those interventions worked—all under time pressure, budget constraints, and deep uncertainty.

Our toolbox addresses four sequential questions that every manager must answer:

---

## The Workflow

| Question | Tool | Status |
|:---------|:-----|:-------|
| **What happened?** | [Disturbance Severity](#disturbance-severity) | **Beta** - active use with NPS partners |
| **What is going to happen?** | [Vegetation Modeling](#vegetation-modeling) (with [`josh`](https://joshsim.org)) | **Beta** - core engine complete, model development ongoing |
| **What should we do?** | [Resource Optimization](#resource-optimization) | In design |
| **Did it work?** | Monitoring & Validation | Long-term; approach in development |

---

### How the Tools Connect

The modules are designed to work together, with data flowing between them:

1. **Disturbance Severity** generates the disturbance/severity map from satellite imagery
2. **Vegetation Modeling** receives the severity map (plus climate scenarios and model parameters) and runs `josh` simulations—potentially many replicates to characterize uncertainty
3. **Resource Optimization** triggers Vegetation Modeling runs with different management interventions and captures results, creating structured comparisons between strategies
4. **Monitoring & Validation** closes the feedback loop, comparing predictions to outcomes and updating models

---

## Disturbance Severity

*"What happened?"*

Uses Sentinel-2 satellite imagery to generate burn severity maps by comparing pre-fire and post-fire conditions. Provides Relativized Burn Ratio (RBR)—appropriate for low-biomass environments like the Mojave Desert—alongside standard dNBR metrics. Links severity to vegetation community data for immediate impact reporting.

**Outputs:** Cloud-optimized GeoTIFFs (severity rasters) that feed directly into Vegetation Modeling.

{{< cards >}}
{{< card link="/tools/disturbance-severity" title="Demo" subtitle="Try the Disturbance Severity tool" icon="play" >}}
{{< card link="/about/methodology" title="Methodology" subtitle="How severity metrics are calculated" icon="academic-cap" >}}
{{< /cards >}}

---

## Vegetation Modeling

*"What is going to happen?"*

Simulates multi-decadal vegetation dynamics using process-based models built from ecological literature (germination rates, growth curves, mortality schedules, competitive interactions). The [`josh`](https://joshsim.org) simulation engine runs these models—in browser for small areas, or at scale on cloud infrastructure.

**Inputs:** Severity raster (from Disturbance Severity) + climate scenarios + model parameters
**Outputs:** Spatiotemporal projections of vegetation recovery under different scenarios

{{< cards >}}
{{< card link="/tools/josh" title="josh Demo" subtitle="Try the josh simulation engine" icon="play" >}}
{{< card link="https://joshsim.org" title="joshsim.org" subtitle="Full josh documentation" icon="external-link" >}}
{{< /cards >}}

---

## Resource Optimization

*"What should we do?"*

Sits between manager intent and vegetation modeling. Takes constraints (seed availability, labor, budget, logistics like road access) and candidate management strategies, then drives josh to run appropriate simulations. Structures comparison of outputs so managers can evaluate tradeoffs between strategies.

**Inputs:** Constraints + candidate strategies
**Outputs:** Structured comparisons of projected outcomes across scenarios

*Currently in design phase. [Contact us](/contact) if you'd like to provide input.*

---

## Design Principles

**Partner-driven development.** We build tools in close collaboration with land managers, prioritizing features that address real operational needs.

**Transparency over black boxes.** Process-based models with inspectable logic—domain experts can examine and modify the underlying mechanisms.

**Collaborative modeling.** Models as shared assets developed jointly by field ecologists, land managers, and quantitative scientists.

**Honesty about uncertainty.** We quantify and communicate uncertainty rather than hiding it behind false precision.

**Open tools.** All components (including josh) are open-source.

---

{{< cards >}}
{{< card link="/about" title="About" image="/static/about.png" subtitle="More about this project" >}}
{{< card link="/about/how_to" title="How To" image="/static/how_to.png" subtitle="How to use the tools" >}}
{{< card link="/roadmap" title="Roadmap" subtitle="Development status and plans" icon="map" >}}
{{< /cards >}}
