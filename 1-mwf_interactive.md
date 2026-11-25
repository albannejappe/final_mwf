---
title: Understanding the Myelin Water Fraction
kernelspec:
  name: python3
  display_name: Python 3
---

# Understanding the Myelin Water Fraction

## Learning objectives

This interactive activity explores the relationship between the Myelin Water Fraction (MWF) and the multi-exponential T2 decay signal.

By modifying the initial MWF and the T2 values of the two water compartments, you can investigate how each parameter affects the measured MRI signal.

## Interactive simulation

Use the sliders to modify the model parameters and observe how the signal changes over echo time.

The simulation represents two water compartments:

- **Myelin water (MW):** characterized by a short T2 relaxation time.
- **Intra- and extracellular water (IEW):** characterized by a longer T2 relaxation time.

The MWF is defined as the initial signal fraction associated with myelin water:

$$
MWF = \frac{A_{MW}}{A_{MW}+A_{IEW}}
$$

where $A_{MW}$ and $A_{IEW}$ are the initial signal amplitudes of the two compartments.

As echo time increases, the relative contribution of myelin water decreases because it has a shorter T2 relaxation time.

:::{important}
The MWF defined above corresponds to the signal fraction at $TE=0$. The relative contribution of myelin water at a later echo time is not constant, since the two compartments decay at different rates.
:::

## Explore the simulation

The following notebook provides an interactive visualization of the biexponential signal decay and the relative myelin water contribution over echo time.

:::{include} notebooks/mwf_interactive.ipynb
:tags: [hide-input]
:::
