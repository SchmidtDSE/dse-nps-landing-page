---
title: Methodology
type: docs
weight: 1
---

## Design Considerations

We are actively working through several design questions:

### Constraint Specification

How should managers specify their constraints? Options range from simple forms (seed count, labor hours, budget) to more complex spatial constraints (must be within 500m of roads, avoid sensitive areas).

### Strategy Definition

Should users define candidate strategies manually, or should the system generate candidates from constraints? Manual definition is more transparent; automatic generation may surface non-obvious options.

### Output Metrics

What metrics best support decision-making? Occupancy at year 30? But this loses temporal nuance. Full trajectories? But these may be overwhelming. We are exploring summary statistics that preserve decision-relevant information.

### Uncertainty Presentation

Each strategy will be simulated many times to characterize uncertainty. How do we present the range of outcomes in a way that supports rather than paralyzes decision-making?

---

## Architecture

From the perspective of [Vegetation Modeling](/tools/vegetation-modeling), each scenario is a completely independent simulation. The vegetation model treats each scenario independently.

Resource Optimization's job is:

1. **Cataloging**  -  keep track of which simulations correspond to which strategies
2. **Triggering**  -  drive the vegetation model to run appropriate scenarios
3. **Collecting**  -  gather outputs from completed simulations
4. **Structuring**  -  present comparisons in a decision-relevant format

[joshpy](https://github.com/SchmidtDSE/joshpy) provides the programmatic interface for triggering and tracking <span class="josh">josh</span> simulations (the Triggering and Collecting responsibilities above) via a backend service.

---

## Example Workflow

A manager might say: "I have 10 Joshua tree seedlings, limited labor, and seedlings need to be within 500m of roads for watering access. Compare passive recovery vs. seeding high-severity areas vs. planting seedlings."

Resource Optimization would:

1. Translate these constraints into three simulation specifications
2. Drive <span class="josh">josh</span> to run each scenario (e.g., 1000 replicates each)
3. Collect outputs (spatiotemporal rasters of predicted vegetation)
4. Structure comparison: "Strategy A: 15% occupancy at year 30, high variance. Strategy B: 35% occupancy, moderate variance. Strategy C: 40% occupancy but 3× labor cost."

The manager then decides which tradeoffs are acceptable given their values and context.

---

## We Want Input

If you have experience with post-fire resource allocation decisions or ideas about how to structure scenario comparisons, please [contact us](/contact).
