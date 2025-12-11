---
title: DSE Disturbance Toolbox
width: full
---

{{< callout >}}

**A suite of tools for post-fire decision support, developed in partnership between UC Berkeley's [Eric and Wendy Schmidt Center for Data Science and Environment](https://dse.berkeley.edu/) and the [National Park Service](https://www.nps.gov).**

{{< /callout >}}

NPS park managers confronting ecosystem vulnerability in a changing climate must navigate academic literature, expert opinion, inventory and monitoring data, research results, and public input when making decisions regarding vegetation management—especially post-fire or after other large-scale disturbances.

This toolbox synthesizes these information sources to support managers in making resource-efficient decisions regarding post-disturbance vegetation management:

- **Assess disturbance severity** from satellite imagery, with metrics calibrated for low-biomass environments
- **Project vegetation recovery** under different climate and management scenarios using process-based simulation
- **Compare intervention strategies** under real-world constraints like seed availability, labor, and budget

---

{{< cards >}}

{{< card link="/tools/disturbance-severity" title="Disturbance Severity" subtitle="Generate burn severity maps from satellite imagery" image="/static/about.png" >}}

{{< card link="/tools/vegetation-modeling" title="Vegetation Modeling" subtitle="Simulate recovery trajectories with josh" image="/static/about.png" >}}

{{< card link="/tools/resource-optimization" title="Resource Optimization" subtitle="Compare intervention strategies under constraints" image="/static/about.png" >}}

{{< /cards >}}

---

## How the Tools Connect

[Disturbance Severity](/tools/disturbance-severity) generates burn severity maps from satellite imagery, outputting cloud-optimized GeoTIFFs.

These severity rasters feed into [Vegetation Modeling](/tools/vegetation-modeling), which uses the [`josh`](https://joshsim.org) simulation engine to project recovery trajectories under different climate and management scenarios.

[Resource Optimization](/tools/resource-optimization) drives vegetation modeling runs across candidate intervention strategies, structuring comparisons so managers can evaluate tradeoffs.

Monitoring & Validation closes the loop by comparing predictions to outcomes and updating models accordingly.

---

{{< cards >}}
{{< card link="/about" title="About" image="/static/about.png" subtitle="Project background and approach" >}}
{{< card link="/about/how_to" title="How To" image="/static/how_to.png" subtitle="Getting started with the tools" >}}
{{< card link="/roadmap" title="Roadmap" image="/static/maya.png" subtitle="Development status and plans" >}}
{{< /cards >}}
