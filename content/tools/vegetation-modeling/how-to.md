---
title: How To
type: docs
weight: 1
---

{{< callout type="info" >}}
This tool is currently in development. We plan to use the [<span class="josh">josh</span> simulation engine](https://joshsim.org) to perform vegetation modeling analyses. Integration approaches are under development in the [<span class="josh">josh</span>-toolbox-demo](https://github.com/SchmidtDSE/josh-toolbox-demo) repository.
{{< /callout >}}

## Getting Started with <span class="josh">josh</span>

For full documentation on using the <span class="josh">josh</span> simulation engine, visit [joshsim.org](https://joshsim.org).

---

## Planned Toolbox Integration

When using <span class="josh">josh</span> within the Disturbance Toolbox workflow will involve:

{{% steps %}}

### Step 1

**Obtain a disturbance severity map** from [Disturbance Severity](/tools/disturbance-severity)

### Step 2

Using the [Vegetation Modeling](/tools/vegetation-modeling/) tool, **import the disturbance severity map** into a parameterized <span class="josh">josh</span> model for the target ecosystem, as initial conditions indicating where the disturbance occurred and how severe it was

### Step 3

**Configure scenarios** with relevant external data (likely external climate data such as projections of temperature, precipitation, for example, or geographic sources such as a digital elevation map for elevation)

### Step 4

**Run simulation ensembles** with multiple replicates to properly characterize uncertainty

### Step 5

**Export outputs** for vegetation impact analysis, or comparison with management intervention outcomes in [Resource Optimization](/tools/resource-optimization)

{{% /steps %}}

---

## Current Limitations

- Models must be parameterized before use - new vegetation communities or intervention types require model development
- Landscape-scale simulations require cloud computing resources
- Model validation is ongoing for Mojave Desert communities
