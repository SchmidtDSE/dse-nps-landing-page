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

## The <span class="josh">josh</span> Simulation Engine

Vegetation Modeling uses [<span class="josh">josh</span>](https://joshsim.org), a domain-specific language and simulation platform developed by DSE. <span class="josh">josh</span> addresses three challenges in ecological modeling identified by Töpper et al. (2025) and others:

1. **Accessibility**: General Ecological Models (GEMs) offer powerful components but may struggle with landscape-level applications and ecosystem-specific processes (Purves et al., 2013). <span class="josh">josh</span>'s DSL uses friendly syntax inspired by HyperTalk (Wheeler, 2004), lowering the barrier for ecologists without extensive programming backgrounds.

2. **Flexibility**: Unlike frameworks with rigid structural assumptions, <span class="josh">josh</span> provides library-like components that can express sophisticated patch-based or agent-based logic, including stochastic, spatial, and stateful operations.

3. **Scalability**: Portable, scalable performance typically requires difficult systems-level programming (Breitwieser et al., 2023). <span class="josh">josh</span> compiles to both JVM and WebAssembly, enabling seamless scaling from browser-based prototyping to distributed cloud execution without code changes.

## Why This Approach?

As described in the [Vegetation Modeling overview](/tools/vegetation-modeling), process-based models can be parameterized from disparate sources - germination studies, growth curves, mortality estimates from varied contexts - without requiring a single comprehensive dataset.

**The tradeoff**: Process-based models require more ecological knowledge to build and may be less accurate in interpolating within well-observed conditions. But they are designed to extrapolate to novel conditions (new fire regimes, climate scenarios, management interventions) where empirical models may not apply.

---

## Transparency and Collaboration

A key design goal is that vegetation ecologists and land managers can engage directly with models, not just receive outputs. This means:

- Model logic is inspectable - users can trace why a simulation produced a particular outcome
- Parameters are explicit and documented - disagreements about values can be identified and discussed
- Models become shared assets representing collective understanding of how the system works

---

## Validation Approach

We validate process-based models differently than empirical models:

- **Ecological plausibility**: Do simulated dynamics match qualitative expectations from field experience?
- **Population stability**: Do populations persist or crash under baseline conditions?
- **Sensitivity analysis**: Which parameters most strongly influence outcomes?
- **Hindcasting**: Where historical data exist, do simulations reproduce observed patterns?

These models carry inherent uncertainty, and their outputs are intended to support decision-making rather than to serve as precise predictions of conditions decades in the future.
