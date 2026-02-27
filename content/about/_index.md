---
title: About
next: first-page
---

The **DSE Disturbance Toolbox** is a suite of tools for post-fire decision support, developed in partnership between UC Berkeley's [Eric and Wendy Schmidt Center for Data Science and Environment](https://dse.berkeley.edu/) (DSE) and the [National Park Service](https://www.nps.gov), specifically Joshua Tree National Park and Mojave National Preserve.

## The Problem

After a wildfire, land managers face a "decision crush": they need to rapidly assess damage, predict vegetation recovery trajectories, decide on management interventions, and eventually evaluate whether those interventions worked - all under time pressure, budget constraints, and deep uncertainty.

## The Four Questions

The toolbox is organized around four sequential questions that every manager must answer after a disturbance:

| Question | Tool | What it provides |
|:---------|:-----|:-----------------|
| **What happened?** | Disturbance Severity | Burn severity maps from satellite imagery, linked to vegetation community data |
| **What is going to happen?** | Vegetation Modeling ([<span class="josh">josh</span>](https://joshsim.org)) | Spatiotemporal projections of recovery under different scenarios |
| **What should we do?** | Resource Optimization | Structured comparisons of intervention strategies under real-world constraints |
| **Did it work?** | Monitoring & Validation | Feedback loop comparing predictions to outcomes |

Each tool addresses a distinct phase of the post-disturbance decision process, and data flows between them: severity maps feed into vegetation models, which are driven by the resource optimizer, with monitoring closing the loop.

## Why Relativized Burn Ratio?

Standard burn severity metrics like dNBR can underestimate severity in low-biomass environments. The Disturbance Severity tool provides [Relativized Burn Ratio (RBR)](/tools/disturbance-severity/methodology/#relative-metrics) and [Relative Differenced Normalized Burn Ratio (RdNBR)](/tools/disturbance-severity/methodology/#relative-metrics), both of which scale fire intensity to pre-fire conditions for more accurate assessment across landscape, alongside the traditional metric of [Differenced Normalized Burn Ratio (dNBR)](/tools/disturbance-severity/methodology/#absolute-metrics).

## Why Process-Based Modeling?

The data required to build empirical models of species-level recovery do not currently exist for many ecosystems, and as climate conditions drive novel phenomenon, empirical approaches must reckon with out-of-sample prediction challenges.

Our [Vegetation Modeling](/tools/vegetation-modeling) approach uses process-based models parameterized from ecological literature, enabling simulation of recovery under novel conditions. While these models can be harder to parameterize and evaluate than statistical models, they can be bootstrapped from ecological literature and field observations, they are transparent and inspectable, and they are easily manipulated to evaluate counterfactuals associated with natural disturbances or management interventions. 

## Design Principles

**Partner-driven development.** Tools are developed in close collaboration with land managers, with features prioritized around operational needs.

**Transparency over black boxes.** Process-based models with inspectable logic - domain experts can examine and modify the underlying mechanisms.

**Collaborative modeling.** Models as shared assets developed jointly by field ecologists, land managers, and quantitative scientists.

**Uncertainty quantification.** Model outputs include explicit characterization of uncertainty rather than single-point estimates.

**Open tools.** All components (including <span class="josh">josh</span>) are open-source.

{{< cards >}}
{{< card link="/tools/disturbance-severity" title="Disturbance Severity" subtitle="Severity assessment tool and documentation" icon="fire" >}}
{{< card link="/tools/vegetation-modeling" title="Vegetation Modeling" subtitle="josh simulation engine and documentation" icon="chart-bar" >}}
{{< card link="/tools/resource-optimization" title="Resource Optimization" subtitle="Intervention comparison (in design)" icon="calculator" >}}
{{< card link="/about/dev_notes/" title="Developer Notes" subtitle="Development notes and known issues" icon="code" >}}
{{< /cards >}}
