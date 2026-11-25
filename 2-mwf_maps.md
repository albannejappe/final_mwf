---
title: Exploring Myelin Water Fraction Maps
kernelspec:
  name: python3
  display_name: Python 3
---

# Exploring Myelin Water Fraction Maps

## Learning objectives

The Myelin Water Fraction (MWF) can be estimated voxel by voxel, allowing the generation of quantitative maps.

Unlike conventional T2-weighted images, which provide qualitative contrast, MWF maps aim to represent the spatial distribution of the myelin-associated water signal.

They can therefore be used to investigate regional variations in myelin content and to study conditions associated with myelin loss, such as multiple sclerosis.

## Interpreting an MWF map

Each pixel in an MWF map represents the estimated fraction of the signal associated with the myelin water compartment.

A lower MWF value may be associated with a reduction in myelin content. However, MWF is an indirect biomarker: it measures the water trapped between myelin sheaths rather than myelin itself.

:::{note}
The map generated in the following notebook is synthetic and is intended for educational purposes only. It does not represent real patient data or a clinically validated MWF map.
:::

## Interactive visualization

Explore the spatial distribution of simulated MWF values using the interactive map.

Hover over the map to inspect local MWF values and their spatial coordinates.

:::{include} notebooks/mwf_maps.ipynb
:tags: [hide-input]
:::
