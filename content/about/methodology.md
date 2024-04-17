---
title: Methodology
type: docs
prev: docs/folder/
math: true
weight: 3
---

The process of deriving burn severity metrics from satellite imagery typically involves comparing imagery from before and after a fire event, to determine how 'different' these images are in terms of reflective vegetation. Specifically, these metrics exploit the difference in two spectral bands provided by satellite imagery:

- **Near Infrared**, which is highly reflective in healthy vegetation
- **Shortwave Infrared**, which is highly reflective in burned areas

![Exploting Spectral Response Curves](https://tf-rest-burn-severity-ohi6r6qs2a-uc.a.run.app/static/home/nir_swir.jpg)

##### Absolute Metrics

Absolute metrics, such as the _Normalized Burn Ratio_ ($NBR$), tend to be more effective for comparison across high and low biomass areas, since they essentially describe the _absolute difference_ in reflectiveness of healthy vegetation, regardless of how much vegetation existed there in the first place.

$$ NBR = \frac{NIR - SWIR}{NIR + SWIR} $$

$$ dNBR = NBR\_{prefire} - NBR\_{postfire} $$

In theory, this means that higher differences represent larger magnitudes of lost healthy vegetation. However, these tend to be biased low in low biomass areas or areas with sparse vegetation, because the absolute loss of vegetation, even in what would be considered an extreme fire event, is lower than the possible loss of vegetation in a higher biomass area.

##### Relative Metrics

Relative metrics, in contrast, scale the estimate of fire intensity at any particular point to its own prefire conditions - essentially, the intensity of a fire is expressed as a percentage of how much healthy vegetative signal was lost.

$$RdNBR = \frac{dNBR}{|(NBR_{prefire})^{0.5}|}$$

$$ RBR = \frac{dNBR}{NBR\_{prefire} +1.001}$$

This means that, between low and high biomass areas, you would observe equivalent $RBR$ values even if the high biomass area experienced higher $dNBR$ values than the low biomass area.
