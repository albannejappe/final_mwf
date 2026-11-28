---
title: Exploring Myelin Water Fraction Maps
kernelspec:
  name: python3
  display_name: Python 3
---

# Exploring Myelin Water Fraction Maps

## Learning objectives

By estimating the **Myelin Water Fraction (MWF)** voxel by voxel across an imaging slice, we obtain a quantitative **MWF map**. In this section, you will learn how to:

- Interpret real *in vivo* MWF maps reconstructed from multi-echo spin-echo MRI data.
- Distinguish qualitative $T_2$-weighted contrast from quantitative MWF maps.
- Identify key brain anatomical structures based on their typical MWF values and recognize focal demyelinating lesions.

---

## Real *in vivo* Brain MRI Example (qMRLab Dataset)

To see what a quantitative MWF map looks like in practice, the interactive visualization below displays **real *in vivo* human brain MRI data downloaded directly from the official [qMRLab](https://qmrlab.org/) example dataset** (`mwf` model).

This dataset consists of a multi-echo $T_2$ (CPMG) acquisition fitted voxel by voxel in MATLAB using qMRLab's multi-exponential $T_2$ (`mwf`) model:

- **Left — First Spin-Echo Image ($TE_1$):** Shows standard anatomical contrast where boundaries between brain tissue and cerebrospinal fluid (CSF) are visible, but myelin content cannot be directly quantified.
- **Right — Quantitative MWF Map (%):** Isolates the short-$T_2$ myelin water fraction in each voxel. Hover over the brain slice to inspect real *in vivo* MWF values across different anatomical regions:
  - **Highly myelinated white matter tracts ($MWF \approx 15\text{–}25\%$):** Dense fiber bundles such as the **corpus callosum** (genu and splenium) and **internal capsules** stand out with the highest values.
  - **Subcortical white matter ($MWF \approx 10\text{–}15\%$):** Displays intermediate-to-high myelin water fraction.
  - **Cortical and deep gray matter ($MWF \approx 3\text{–}6\%$):** Contains much lower myelin density, appearing darker on the map.
  - **Cerebrospinal fluid (CSF, $MWF \approx 0\%$):** Ventricles contain free water with no myelin-trapped compartment.

:::{include} notebooks/mwf_real_qmrlab.ipynb
:::

---

## Interactive Simulation: Healthy vs. Demyelinated Brain Slice

While the real qMRLab dataset above illustrates a healthy brain, simulations help us visualize how pathology alters these maps. Use the buttons above the figure below to switch between a **healthy brain model** and a brain containing a **focal demyelinating lesion** in the left periventricular white matter:

:::{include} notebooks/mwf_maps.ipynb
:::

---

## Guided Interpretation Exercise

Compare the maps in the visualizations above:

1. **Why do the ventricles appear bright on $T_2$-weighted images but completely dark ($0\%$) on quantitative MWF maps?**
2. **In the simulated brain slice, switch to "Demyelinating Lesion (MS)" and hover over the lesion in the upper-left white matter. How do the $T_2$-weighted signal and the MWF behave?**

::::{dropdown} Show solutions
:color: success
:icon: check-circle

1. **Opposite contrast mechanisms:** Cerebrospinal fluid (CSF) has a very long $T_2$ ($>1000\text{ ms}$), so it retains high signal on $T_2$-weighted images (bright). However, it contains no water trapped in myelin bilayers ($A_{MW} = 0$), resulting in $MWF = 0\%$ (dark).
2. **Hyperintense in $T_2$-w, hypointense in MWF:** Inflammation and edema increase free water content, elevating the $T_2$-weighted signal. Simultaneously, myelin loss reduces the short-$T_2$ myelin water fraction from $\sim 15\%$ down to $\sim 3.5\%$.
::::
