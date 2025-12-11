---
title: Roadmap
---

## Our Approach

NPS park managers confronting ecosystem vulnerability in a changing climate need to navigate a wide range of academic literature, expert opinion, inventory and monitoring data, research results, and public opinion when making decisions regarding vegetation management—especially post-fire or after other large-scale disturbances.

DSE's intent is to create a "toolbox" of analytical approaches to synthesize these information sources and support NPS managers in making resource-efficient decisions regarding post-disturbance vegetation management.

### Design Goals

The modules are designed to be:

- **Flexible** — allow users to quickly import their own data sources, export intermediate steps, and modify analysis approaches for their particular needs
- **Scalable** — designed to work across environments, park unit sizes, and resource constraints
- **Modular** — each works in isolation, or in any combination, adding to one another when used together

---

## Module Status

| Module | Status | Description |
|:-------|:-------|:------------|
| **Disturbance Severity** | **Beta** | Operational, actively used by NPS partners at Joshua Tree and Mojave National Preserve |
| **Vegetation Modeling (josh)** | **Beta** | Core simulation engine complete; model development and parameterization ongoing |
| **Resource Optimization** | In Design | Architecture defined; actively seeking input on approach |
| **Monitoring & Validation** | Long-term | Approach in development; will close feedback loop through remote sensing validation and model updating |

---

## Disturbance Severity

### Why we built it

Federal agencies produce burn severity maps after major fires, but these typically arrive weeks after the event and use calibrations designed for high-biomass forests. In low-biomass environments like the Mojave Desert, standard spectral indices underestimate severity because there's less vegetation signal to begin with.

Our partners needed severity assessments that were: (1) faster—available within days, not weeks; (2) tuned for their landscape; and (3) directly linked to vegetation community data for grant applications and internal reporting.

### Current capabilities

- Generate severity maps within days of a fire, given cloud-free imagery
- Provide Relativized Burn Ratio (RBR) appropriate for low-biomass environments, alongside absolute metrics (dNBR)
- Link severity to vegetation community data for impact reporting
- Output cloud-optimized GeoTIFFs for downstream use

---

## Vegetation Modeling with josh

### Why we're building it

Empirical models need data that are both spatially and temporally rich at the taxonomic resolution of interest. In practice, this almost never exists. To model something like Joshua tree recovery specifically, we would need decades of repeated measurements across the landscape—data that don't exist and likely never will.

Instead, we take a "bottom-up" approach: building vegetation models from first principles using life history data from the ecological literature.

### Current capabilities

[`josh`](https://joshsim.org) is an open-source, spatially explicit simulation engine that makes process-based modeling accessible:

- Domain-specific language for specifying organisms, life stages, demographic rates, and environmental interactions
- Runs in browser for small simulations, scales to cloud computing for landscape-level analysis
- Transparent models that ecologists can inspect, critique, and modify

### In progress

- Model parameterization and validation for Mojave Desert vegetation communities
- Integration with Disturbance Severity outputs
- Climate scenario incorporation

---

## Resource Optimization

### The problem

After characterizing a disturbance and building vegetation models, managers face a combinatorial explosion of choices: Where to seed? Where to plant? Remove invasives first? How much labor per hectare? What if seed supply is limited? What if seedlings need to be near roads for watering access?

### Planned approach

Resource Optimization will sit between manager intent and vegetation modeling:

1. Take constraints (seed, labor, budget, logistics) and candidate strategies
2. Drive josh to run appropriate simulations (many replicates per scenario)
3. Structure comparison of outputs so managers can evaluate tradeoffs

### We want input

We're actively seeking input on how to approach these challenges. [Contact us](/contact) if you have experience with post-fire resource allocation or ideas about scenario comparison.

---

## Monitoring & Validation

### Why it matters

We need to close the feedback loop. If an intervention is predicted to increase seedling survival but doesn't, we need to know—both for model improvement and future management decisions.

### Planned approaches

- Remote sensing validation: track whether recovery trajectories match projections
- Long-term monitoring integration: field data to validate abundance predictions
- Model updating: when observations diverge from predictions, feed back into parameterization

This is the furthest-out component, but we're committed to building something because without it the rest is flying blind.

---

## Related Work

### ESIIL Sagebrush Proposal

This work connects to a related ESIIL working group proposal focused on sagebrush ecosystems, sharing much of the same workflow philosophy. Key elements include:

- Phased approach: (1) stable baseline models, (2) add intervention capabilities, (3) climate scenario analysis
- Emphasis on RAD framework (Resist-Accept-Direct) for management decisions
- Collaboration with NC RISCC, NC CASC, USGS researchers

### RAD Framework

Resist-Accept-Direct is an NPS management paradigm for decision-making under climate change:

- **Resist:** try to maintain historical conditions
- **Accept:** allow system to change along current trajectory
- **Direct:** actively guide system toward preferred new state

The toolbox is designed to support RAD decision-making by quantifying projected outcomes under different strategies.
