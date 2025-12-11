---
title: How To
type: docs
weight: 1
---

## Getting Started with josh

For full documentation on using the josh simulation engine, visit [joshsim.org](https://joshsim.org).

*Detailed how-to documentation for toolbox-specific workflows is in development.*

---

## Toolbox Integration

When using josh within the Disturbance Toolbox workflow:

1. **Obtain a severity raster** from [Disturbance Severity](/tools/disturbance-severity)
2. **Load the raster** into a pre-parameterized josh model as initial conditions
3. **Configure scenarios** (climate projections, management interventions)
4. **Run simulations** with multiple replicates to characterize uncertainty
5. **Export outputs** for analysis or comparison in [Resource Optimization](/tools/resource-optimization)

---

## Current Limitations

- Models must be parameterized before use—new vegetation communities or intervention types require model development
- Landscape-scale simulations require cloud computing resources
- Model validation is ongoing for Mojave Desert communities
