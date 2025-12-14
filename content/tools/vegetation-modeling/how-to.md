---
title: How To
type: docs
weight: 1
---

{{< callout type="info" >}}
This tool is currently in development. We plan to use the [<span class="josh">josh</span> simulation engine](https://joshsim.org) to perform vegetation modeling analyses. We are experimenting with integration approaches in the [<span class="josh">josh</span>-toolbox-demo](https://github.com/SchmidtDSE/josh-toolbox-demo) repository.
{{< /callout >}}

## Getting Started with <span class="josh">josh</span>

For full documentation on using the <span class="josh">josh</span> simulation engine, visit [joshsim.org](https://joshsim.org).

---

## Planned Toolbox Integration

When using <span class="josh">josh</span> within the Disturbance Toolbox workflow:

1. **Obtain a severity raster** from [Disturbance Severity](/tools/disturbance-severity)
2. **Load the raster** into a pre-parameterized <span class="josh">josh</span> model as initial conditions
3. **Configure scenarios** (climate projections, management interventions)
4. **Run simulations** with multiple replicates to characterize uncertainty
5. **Export outputs** for analysis or comparison in [Resource Optimization](/tools/resource-optimization)

---

## Current Limitations

- Models must be parameterized before use—new vegetation communities or intervention types require model development
- Landscape-scale simulations require cloud computing resources
- Model validation is ongoing for Mojave Desert communities
