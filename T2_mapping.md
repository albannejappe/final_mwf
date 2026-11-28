---
title: T2 Mapping & Multi-Exponential Foundations
---

# T2 Mapping & Multi-Exponential Foundations

## Overview

In quantitative Magnetic Resonance Imaging (MRI), **T2 Mapping** estimates the transverse relaxation time ($T_2$) of biological tissues by fitting a mathematical decay model to images acquired at multiple echo times ($TE$). Unlike conventional $T_2$-weighted images that only offer qualitative contrast, quantitative $T_2$ values reflect underlying tissue microstructure.

While a **mono-exponential model** ($S(TE) = S_0 e^{-TE/T_2}$) assumes a single uniform water environment per voxel, brain tissue contains multiple microstructural water compartments with distinct relaxation rates.

::::{dropdown} Original content from the qMRI mOOC (qMRLab)
:color: info
:icon: book

*The following summary reflects the foundational concepts already covered in the [qMRI mOOC T2 Mapping chapter](https://qmrlab.org/mooc/t2-mapping/):*

- **Mono-exponential $T_2$ vs. $T_2^*$:** Transverse magnetization decays due to spin-spin interactions ($T_2$) as well as macroscopic and microscopic magnetic field inhomogeneities ($T_2^*$, where $\frac{1}{T_2^*} = \frac{1}{T_2} + \frac{1}{T_2'}$).
- **Multi-Spin Echo (MSE / CPMG) sequences:** Multiple $180^\circ$ refocusing pulses generate an echo train within a single acquisition, reducing scan time compared to repeated single-echo scans.
- **Stimulated echoes & $B_1$ imperfections:** Imperfect refocusing flip angles produce stimulated echoes that contaminate the decay curve. Standard strategies include discarding the first echo, fitting even echoes only, or using Extended Phase Graph (EPG) modeling.
- **General Multi-exponential $T_2$ Mapping:** Voxel signal is modeled as a sum or continuous distribution of exponential decays ($S(TE) = \sum_{i=1}^{N} A_i e^{-TE/T_{2,i}}$), typically solved via regularized Non-Negative Least Squares (NNLS).
::::

---

## 1. Bi-Exponential Model for Myelin Water Imaging

To study myelination in white matter, the multi-exponential signal is commonly simplified into two main water compartments (neglecting free cerebrospinal fluid, $T_2 > 1000\text{ ms}$):

$$
S(TE) = A_{MW} e^{-TE/T_{2,MW}} + A_{IEW} e^{-TE/T_{2,IEW}}
$$

where:
- **Myelin water (MW):** Water tightly trapped between the lipid bilayers of the myelin sheath, characterized by a **short $T_2$ relaxation time** ($\approx 10\text{–}40\text{ ms}$ at 3T).
- **Intra- and extracellular water (IEW):** Water inside axons, glial cells, and the extracellular space, characterized by a **longer $T_2$ relaxation time** ($\approx 60\text{–}120\text{ ms}$).
- **$A_{MW}$ and $A_{IEW}$:** Initial signal amplitudes of each compartment at $TE = 0$.

---

## 2. Myelin Water Fraction (MWF) Definition

The **Myelin Water Fraction (MWF)** is defined as the fraction of the initial MRI signal originating from myelin-associated water:

$$
MWF = \frac{A_{MW}}{A_{MW} + A_{IEW}} \times 100 \quad (\%)
$$

In practice, when fitting a continuous $T_2$ distribution using Non-Negative Least Squares (NNLS), the MWF corresponds to the area under the short-$T_2$ peak ($T_2 < 40\text{ ms}$) divided by the total area of the $T_2$ spectrum.

### Practical Challenges & Limitations

- **Need for short first echo ($TE_1$):** Because myelin water decays rapidly, acquisitions must start at a short echo time ($TE_1 \le 10\text{ ms}$) with tight echo spacing ($\Delta TE \approx 8\text{–}10\text{ ms}$) to capture the fast-decaying component.
- **Noise sensitivity (SNR):** Separating two decaying exponentials is an ill-posed inverse problem; low SNR blurs the $T_2$ peaks and introduces estimation bias.
- **Indirect biomarker:** MWF measures water trapped within myelin sheaths rather than myelin lipids directly, and can be influenced by water exchange or inflammation.

---

## 3. Interactive Modules: Exploring MWF

The following interactive chapters expand on the qMRI mOOC by allowing you to manipulate bi-exponential parameters, inspect spatial MWF maps, and compare healthy versus demyelinated tissue models:

:::{seealso}
- {doc}`1-mwf_interactive`: Simulate how MWF and compartmental $T_2$ values shape the decay curve and relative MW contribution.
- {doc}`2-mwf_maps`: Explore spatial MWF distributions and compare synthetic maps with real brain MRI data.
- {doc}`3-healthy_demyelinated`: Compare healthy white matter against demyelinated tissue models (e.g., multiple sclerosis).
:::
