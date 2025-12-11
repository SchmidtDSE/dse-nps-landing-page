---
title: Methodology
type: docs
weight: 2
math: true
---

## Disturbance Severity Metrics

The process of deriving disturbance severity metrics from satellite imagery involves comparing imagery from before and after a disturbance event to determine how different these images are in terms of reflective vegetation. Specifically, these metrics exploit the difference in two spectral bands provided by satellite imagery:

- **Near Infrared (NIR)**, which is highly reflective in healthy vegetation
- **Shortwave Infrared (SWIR)**, which is highly reflective in burned areas

![Exploiting Spectral Response Curves](https://tf-rest-burn-severity-ohi6r6qs2a-uc.a.run.app/static/home/nir_swir.jpg)

---

## Absolute Metrics

Absolute metrics, such as the _Normalized Burn Ratio_ ($NBR$), describe the _absolute difference_ in reflectiveness of healthy vegetation, regardless of how much vegetation existed there in the first place.

$$ NBR = \frac{NIR - SWIR}{NIR + SWIR} $$

$$ dNBR = NBR_{prefire} - NBR_{postfire} $$

In theory, higher differences represent larger magnitudes of lost healthy vegetation. However, dNBR tends to be biased low in low-biomass areas or areas with sparse vegetation, because the absolute loss of vegetation—even in what would be considered an extreme fire event—is lower than the possible loss of vegetation in a higher biomass area.

---

## Relative Metrics

Relative metrics scale the estimate of fire intensity at any particular point to its own prefire conditions. Essentially, the intensity of a fire is expressed as a percentage of how much healthy vegetative signal was lost.

**Relativized differenced NBR (RdNBR):**

$$RdNBR = \frac{dNBR}{|(NBR_{prefire})^{0.5}|}$$

**Relativized Burn Ratio (RBR):**

$$ RBR = \frac{dNBR}{NBR_{prefire} + 1.001}$$

This means that, between low and high biomass areas, you would observe equivalent $RBR$ values even if the high biomass area experienced higher $dNBR$ values than the low biomass area.

---

## Why We Use RBR

For our partners working in the Mojave Desert and similar low-biomass environments, RBR provides a more accurate picture of fire severity than dNBR. A fire that completely consumes desert vegetation will register as "moderate" on dNBR scales calibrated for forests, but will correctly register as "high severity" on RBR.

We provide both metrics in our outputs so users can choose the appropriate metric for their context and compare with federal severity products that use dNBR.
