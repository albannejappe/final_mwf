---
title: Healthy and Demyelinated Tissue
kernelspec:
  name: python3
  display_name: Python 3
---

# Healthy and Demyelinated Tissue

## Learning objectives

Myelin Water Fraction imaging has been investigated as a potential biomarker of myelin integrity.

In conditions such as multiple sclerosis, demyelination can lead to changes in the myelin-associated water compartment and therefore affect the estimated MWF.

This activity illustrates how a decrease in MWF can influence the measured T2 signal decay.

## Comparing two tissue models

The simulation compares two simplified biexponential models:

- **Healthy tissue:** a relatively high myelin water fraction.
- **Demyelinated tissue:** a lower myelin water fraction.

Both models contain a myelin water compartment and an intra- and extracellular water compartment, but their initial signal fractions differ.

## Interactive simulation

Modify the MWF values using the sliders and observe how the total signal decay changes.

Consider the following questions while exploring the simulation:

1. How does a decrease in MWF affect the initial signal contribution of the myelin water compartment?
2. How does the difference between the two signal curves evolve with echo time?
3. Why might MWF be useful for investigating demyelination?

:::{important}
This is a simplified educational model. A decrease in MWF may be associated with demyelination, but it is not specific to this process and should not be interpreted as a direct measurement of myelin loss.
:::

:::{include} notebooks/healthy_demyelinated.ipynb
:::
