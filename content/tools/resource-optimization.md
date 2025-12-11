---
title: Resource Optimization
type: docs
---

## Status: In Design

Resource Optimization is currently in the design phase. This module will sit between manager intent and vegetation modeling to help structure and compare intervention strategies.

### What it will do

- Translate management constraints (seed availability, labor, budget, logistics) into simulation specifications
- Drive [`josh`](https://joshsim.org) to run appropriate scenarios (many replicates, multiple strategies)
- Structure side-by-side comparison of projected outcomes
- Surface tradeoffs between cost, effort, and ecological outcomes

### What it won't do

- Tell managers what to do—decisions involve values, risk tolerance, and local knowledge that can't be automated
- Test interventions that haven't been parameterized in the vegetation model—new interventions require model development first
- Solve the "optimal" management problem—that requires agreement on criteria we can't assume

### How it connects to other tools

1. Receives **severity rasters** from Disturbance Severity as the foundation for simulations
2. Specifies **candidate interventions** and drives Vegetation Modeling to run josh simulations
3. Collects and catalogs **simulation outputs** for structured comparison
4. Presents **tradeoff analysis** to managers for decision-making

### We want your input

We're actively seeking input on how to approach these challenges well. If you have experience with post-fire resource allocation decisions or ideas about how to structure scenario comparisons, please [contact us](/contact).
