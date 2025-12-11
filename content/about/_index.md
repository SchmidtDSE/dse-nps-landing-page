---
title: About
next: first-page
---

The **DSE Disturbance Toolbox** is a suite of tools for post-fire decision support, developed in partnership between UC Berkeley's [Eric and Wendy Schmidt Center for Data Science and Environment](https://dse.berkeley.edu/) (DSE) and the [National Park Service](https://www.nps.gov), specifically Joshua Tree National Park and Mojave National Preserve.

## The Problem

After a wildfire, land managers face a "decision crush": they need to rapidly assess damage, predict vegetation recovery trajectories, decide on management interventions, and eventually evaluate whether those interventions worked—all under time pressure, budget constraints, and deep uncertainty.

## Our Approach

The toolbox addresses four sequential questions that every manager must answer:

1. **What happened?** — Disturbance Severity assessment using satellite imagery
2. **What is going to happen?** — Vegetation modeling with [`josh`](https://joshsim.org)
3. **What should we do?** — Resource optimization under constraints
4. **Did it work?** — Monitoring and validation to close the feedback loop

## Why Relativized Burn Ratio?

The core of this collaboration emerged from a need to better understand fire severity in low-biomass environments. Standard burn severity assessments use differenced Normalized Burn Ratio (dNBR), which measures absolute difference in vegetation signal. This works well in forests, but in environments like the Mojave Desert, dNBR is biased low—even complete vegetation loss produces a smaller absolute difference than a moderate fire in a high-biomass forest.

Our Disturbance Severity tool provides Relativized Burn Ratio (RBR), which scales fire intensity to pre-fire conditions at each location. This means equivalent ecological damage produces equivalent severity values regardless of landscape type.

## Why Process-Based Modeling?

Empirical models (regressions trained on observed data) require data that are both spatially and temporally rich at the taxonomic resolution of interest. To model Joshua tree recovery specifically, we would need decades of repeated measurements across the landscape—data that don't exist.

Instead, we use process-based models built from ecological literature: germination rates, growth curves, mortality schedules, competitive interactions. The [`josh`](https://joshsim.org) simulation engine makes this approach accessible, with models that domain experts can inspect, critique, and modify.

{{< cards >}}
{{< card link="/about/how_to/" title="How To" subtitle="How to get started using the tools" icon="map" >}}
{{< card link="/about/methodology/" title="Methodology" subtitle="Technical details on severity metrics" icon="academic-cap" >}}
{{< card link="/about/dev_notes/" title="Developer Notes" subtitle="Development notes and known issues" icon="code" >}}
{{< card link="/about/key_references/" title="Key References" subtitle="Publications informing our approach" icon="library" >}}
{{< /cards >}}
