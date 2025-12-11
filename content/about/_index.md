---
title: About
next: first-page
---

The **DSE Disturbance Toolbox** is a suite of tools for post-fire decision support, developed in partnership between UC Berkeley's [Eric and Wendy Schmidt Center for Data Science and Environment](https://dse.berkeley.edu/) (DSE) and the [National Park Service](https://www.nps.gov), specifically Joshua Tree National Park and Mojave National Preserve.

## The Problem

After a wildfire, land managers face a "decision crush": they need to rapidly assess damage, predict vegetation recovery trajectories, decide on management interventions, and eventually evaluate whether those interventions worked—all under time pressure, budget constraints, and deep uncertainty.

## The Four Questions

The toolbox is organized around four sequential questions that every manager must answer after a disturbance:

| Question | Tool | What it provides |
|:---------|:-----|:-----------------|
| **What happened?** | Disturbance Severity | Burn severity maps from satellite imagery, linked to vegetation community data |
| **What is going to happen?** | Vegetation Modeling ([`josh`](https://joshsim.org)) | Spatiotemporal projections of recovery under different scenarios |
| **What should we do?** | Resource Optimization | Structured comparisons of intervention strategies under real-world constraints |
| **Did it work?** | Monitoring & Validation | Feedback loop comparing predictions to outcomes |

Each tool addresses a distinct phase of the post-disturbance decision process, and data flows between them: severity maps feed into vegetation models, which are driven by the resource optimizer, with monitoring closing the loop.

## Why Relativized Burn Ratio?

The core of this collaboration emerged from a need to better understand fire severity in low-biomass environments. Standard burn severity assessments use differenced Normalized Burn Ratio (dNBR), which measures absolute difference in vegetation signal. This works well in forests, but in environments like the Mojave Desert, dNBR is biased low—even complete vegetation loss produces a smaller absolute difference than a moderate fire in a high-biomass forest.

Our Disturbance Severity tool provides Relativized Burn Ratio (RBR), which scales fire intensity to pre-fire conditions at each location. This means equivalent ecological damage produces equivalent severity values regardless of landscape type.

## Why Process-Based Modeling?

Empirical models (regressions trained on observed data) require data that are both spatially and temporally rich at the taxonomic resolution of interest. To model Joshua tree recovery specifically, we would need decades of repeated measurements across the landscape—data that don't exist.

Instead, we use process-based models built from ecological literature: germination rates, growth curves, mortality schedules, competitive interactions. The [`josh`](https://joshsim.org) simulation engine makes this approach accessible, with models that domain experts can inspect, critique, and modify.

## Design Principles

**Partner-driven development.** We build tools in close collaboration with land managers, prioritizing features that address real operational needs.

**Transparency over black boxes.** Process-based models with inspectable logic—domain experts can examine and modify the underlying mechanisms.

**Collaborative modeling.** Models as shared assets developed jointly by field ecologists, land managers, and quantitative scientists.

**Honesty about uncertainty.** We quantify and communicate uncertainty rather than hiding it behind false precision.

**Open tools.** All components (including josh) are open-source.

{{< cards >}}
{{< card link="/tools/disturbance-severity" title="Disturbance Severity" subtitle="Severity assessment tool and documentation" icon="fire" >}}
{{< card link="/tools/vegetation-modeling" title="Vegetation Modeling" subtitle="josh simulation engine and documentation" icon="chart-bar" >}}
{{< card link="/tools/resource-optimization" title="Resource Optimization" subtitle="Intervention comparison (in design)" icon="calculator" >}}
{{< card link="/about/dev_notes/" title="Developer Notes" subtitle="Development notes and known issues" icon="code" >}}
{{< /cards >}}
