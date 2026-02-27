---
title: Roadmap
---

## Development Status

| Module | Status | Current Focus |
|:-------|:-------|:--------------|
| **Disturbance Severity** | **Beta** | Operational; actively used by NPS partners at Joshua Tree and Mojave National Preserve |
| **Vegetation Modeling (<span class="josh">josh</span>)** | **Beta** | Core simulation engine complete; model parameterization and validation ongoing |
| **Resource Optimization** | In Design | Architecture defined; seeking input on approach |
| **Monitoring & Validation** | Long-term | Approach in development |

---

## Module Details

{{< tabs items="Disturbance Severity,Vegetation Modeling,Resource Optimization,Monitoring & Validation" >}}

{{< tab >}}

**Status: Beta**  -  [Methodology](/tools/disturbance-severity/methodology)

The Disturbance Severity tool is operational and in active use with NPS partners.

**Current capabilities:**
- Generate severity maps within days of a fire, given cloud-free imagery
- Provide Relativized Burn Ratio (RBR) appropriate for low-biomass environments, alongside absolute metrics (dNBR)
- Link severity to vegetation community data for impact reporting
- Output cloud-optimized GeoTIFFs for downstream use

**Development history:**
- Initial development driven by partner need for faster severity assessments tuned for desert environments
- Partners were receiving dNBR from federal agencies but needed RBR for low-biomass landscapes

{{< /tab >}}

{{< tab >}}

**Status: Beta**  -  [Methodology](/tools/vegetation-modeling/methodology) | [<span class="josh">josh</span> Website](https://joshsim.org)

The [<span class="josh">josh</span>](https://joshsim.org) simulation engine is complete and functional. Current work focuses on model development and parameterization for specific vegetation communities.

**Current capabilities:**
- Domain-specific language for specifying organisms, life stages, demographic rates, and environmental interactions
- Runs in browser for small simulations, scales to cloud computing for landscape-level analysis
- Transparent models that ecologists can inspect, critique, and modify

**In progress:**
- Model parameterization and validation for Mojave Desert vegetation communities
- Integration with Disturbance Severity outputs (automatic loading of severity rasters)
- Climate scenario incorporation
- [joshpy](https://github.com/SchmidtDSE/joshpy) Python client available for programmatic model development and batch analysis

**Next steps:**
- Complete baseline Joshua tree community model
- Parameterize fire response and management intervention effects
- Validation against available monitoring data

{{< /tab >}}

{{< tab >}}

**Status: In Design**  -  [Methodology](/tools/resource-optimization/methodology)

Resource Optimization will sit between manager intent and vegetation modeling, helping structure and compare intervention strategies.

**Planned capabilities:**
- Translate management constraints (seed availability, labor, budget, logistics) into simulation specifications
- Drive <span class="josh">josh</span> to run appropriate scenarios (many replicates, multiple strategies) using [joshpy](https://github.com/SchmidtDSE/joshpy) for programmatic simulation batches
- Structure side-by-side comparison of projected outcomes
- Surface tradeoffs between cost, effort, and ecological outcomes

**Design considerations:**
- How to specify constraints in a flexible but structured way
- What output metrics best support manager decision-making
- How to present uncertainty in strategy comparisons

**We want input:** If you have experience with post-fire resource allocation or ideas about scenario comparison, please [contact us](/contact).

{{< /tab >}}

{{< tab >}}

**Status: Long-term**

This component will close the feedback loop by comparing predictions to outcomes and updating models accordingly.

**Planned approaches:**
- Remote sensing validation: track whether recovery trajectories match projections
- Long-term monitoring integration: field data to validate abundance predictions
- Model updating: when observations diverge from predictions, feed back into parameterization

Validation is essential to adaptive management, which requires knowing whether interventions achieved their intended effects.

{{< /tab >}}

{{< /tabs >}}
