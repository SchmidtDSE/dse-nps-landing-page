---
title: Resource Optimization
weight: 3
---

**Status: In Design** — Architecture defined, seeking input on approach

Resource Optimization sits between manager intent and vegetation modeling. It takes real-world constraints (seed availability, labor, budget, logistics) and candidate management strategies, then drives [Vegetation Modeling](/tools/vegetation-modeling) to run appropriate simulations and structures the comparison of outcomes.

{{< callout type="warning" >}}
This module is currently in the design phase. [Contact us](/contact) if you would like to provide input on the approach.
{{< /callout >}}

## The Problem

After characterizing a disturbance and building vegetation models, managers face a combinatorial explosion of choices:

- Where should we seed?
- Where should we plant juveniles?
- Should we remove invasive species first?
- How much labor can we invest per hectare?
- What if seed supply is limited?
- What if seedlings need to be planted near roads for watering access?

Each combination of treatment, location, timing, and intensity produces different projected outcomes. Even for a modest burn scar with a handful of treatment options, the number of permutations quickly exceeds what anyone can reason about intuitively.

## Planned Approach

Resource Optimization will:

1. **Accept constraints** — seed availability, labor hours, budget, logistical requirements (e.g., road access for watering)
2. **Define candidate strategies** — combinations of interventions to compare
3. **Drive simulations** — trigger [Vegetation Modeling](/tools/vegetation-modeling) runs for each strategy, with many replicates per scenario to characterize uncertainty
4. **Structure comparisons** — present outcomes side-by-side so managers can evaluate tradeoffs

## What It Won't Do

- **Tell managers what to do** — decisions involve values, risk tolerance, and local knowledge that can't be automated
- **Test unparameterized interventions** — if you want to simulate an intervention not yet built into the vegetation model (e.g., caging seedlings to prevent herbivory), that requires model development first
- **Solve the "optimal" problem** — optimization requires agreement on objective criteria, which we can't assume

---

{{< cards >}}
{{< card link="/tools/resource-optimization/methodology" title="Methodology" subtitle="Planned approach and design considerations" icon="academic-cap" >}}
{{< /cards >}}
