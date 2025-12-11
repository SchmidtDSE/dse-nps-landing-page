---
title: Methodology
type: docs
weight: 2
---

## Process-Based Modeling

Unlike empirical models that learn patterns from historical data, process-based models simulate ecological dynamics from first principles. Each organism in the model has explicitly defined:

- **Life stages** (seed, seedling, juvenile, adult)
- **Demographic rates** (germination probability, growth rate, mortality schedule)
- **Environmental responses** (drought tolerance, fire mortality, temperature thresholds)
- **Competitive interactions** (resource competition, facilitation)

These parameters are estimated from ecological literature and targeted field studies, then combined to simulate how populations change over time and space.

---

## Why This Approach?

**The data problem**: To build an empirical model of Joshua tree recovery, we would need spatially comprehensive, multi-decadal monitoring data at the species level. Such data don't exist for most ecosystems.

**The solution**: Process-based models can be parameterized from disparate sources—a germination study here, a growth curve there, mortality estimates from another context—without requiring a single comprehensive dataset.

**The tradeoff**: Process-based models require more ecological knowledge to build and may be less accurate in interpolating within well-observed conditions. But they can extrapolate to novel conditions (new fire regimes, climate scenarios, management interventions) where empirical models fail.

---

## Transparency and Collaboration

A key design goal is that vegetation ecologists and land managers can engage directly with models, not just receive outputs. This means:

- Model logic is inspectable—users can trace why a simulation produced a particular outcome
- Parameters are explicit and documented—disagreements about values can be identified and discussed
- Models become shared assets representing collective understanding of how the system works

---

## Validation Approach

We validate process-based models differently than empirical models:

- **Ecological plausibility**: Do simulated dynamics match qualitative expectations from field experience?
- **Population stability**: Do populations persist or crash under baseline conditions?
- **Sensitivity analysis**: Which parameters most strongly influence outcomes?
- **Hindcasting**: Where historical data exist, do simulations reproduce observed patterns?

We are honest about uncertainty—the goal is to inform decisions, not to make precise predictions about conditions decades in the future.
