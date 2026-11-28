---
title: Understanding the Myelin Water Fraction
kernelspec:
  name: python3
  display_name: Python 3
---

# Understanding the Myelin Water Fraction

## Learning objectives

This interactive activity explores the relationship between the **Myelin Water Fraction (MWF)** and the multi-exponential $T_2$ decay signal. By modifying the initial MWF and the $T_2$ relaxation times of the two water compartments, you will investigate how each parameter shapes the measured MRI signal over echo time ($TE$).

---

::::{dropdown} Original content from the qMRI mOOC (qMRLab)
:color: info
:icon: book

*The following section presents the original Myelin Water Fraction content from the [qMRI mOOC T2 Mapping chapter](https://qmrlab.org/mooc/t2-mapping/):*

Myelin water fraction (MWF) imaging demonstrates the clinical relevance of multi-exponential _T_{sub}`2` mapping [@Kumar2012-uv;@MacKay1994-yv], given that myelin quantification could help identify potential biomarkers for diseases such as multiple sclerosis (MS). Although MWF technically does not directly measure myelin but rather quantifies the amount of total water trapped between the myelin sheaths, it is argued that myelin can be conceptualized as water, as it constitutes its primary composition [@Alonso-Ortiz2015-yj]. 

Conventional _T_{sub}`2`-weighted images often display hyperintense lesions in MS patients. Unfortunately, these hyperintensities lack specificity for the disease and can be indistinguishable from other biological phenomena such as inflammation, edema and axonal loss [@Alonso-Ortiz2015-yj;@Lee2021-jk]. MWF holds promise as a potential biomarker for identifying early microstructural changes in myelin, which could improve our understanding of demyelinating diseases such as MS, facilitating both early diagnosis and monitoring of disease progression. 

As described by [](#t2Eq8), MWF represents the proportion of the MRI signal attributed to myelin water relative to the total water content in the brain. This total water content includes myelin water (MW) and intra/extracellular water (IEW), also referred to as axonal water [@Lee2021-jk]. 

```{math}
:label: t2Eq8
:enumerator:3.8
\begin{equation}
\textit{MWF} = \frac{S_{MW}}{S_{MW} + S_{IEW}}
\end{equation}
```

Direct imaging of myelin itself is challenging due to its very short _T_{sub}`2` relaxation times. Instead, an alternative is to image myelin-associated water (MW), which has slightly longer _T_{sub}`2` relaxation times, typically around 20 ms [@Lee2021-jk]. While these times are still short, they are measurable with standard spin-echo MRI sequences. Myelin Water Fraction (MWF) imaging takes advantage of this to differentiate and quantify the signal from myelin-associated water, providing a more feasible approach to studying myelin. 

::::

## Bi-exponential signal model

In white matter, the transverse MRI signal can be modeled as the sum of two main water compartments:

- **Myelin water (MW):** Water trapped between myelin bilayers, characterized by a **short $T_2$ relaxation time** ($10\text{–}40\text{ ms}$).
- **Intra- and extracellular water (IEW):** Water inside axons, glial cells, and the extracellular space, characterized by a **longer $T_2$ relaxation time** ($60\text{–}120\text{ ms}$).

The total normalized signal at echo time $TE$ is given by:

$$
S(TE) = A_{MW} e^{-TE/T_{2,MW}} + A_{IEW} e^{-TE/T_{2,IEW}}
$$

The **Myelin Water Fraction (MWF)** corresponds to the initial signal fraction associated with myelin water at $TE = 0$:

$$
MWF = \frac{A_{MW}}{A_{MW} + A_{IEW}} \times 100 \quad (\%)
$$

:::{important}
The MWF is defined strictly at **$TE = 0$**. As echo time increases, the relative contribution of myelin water to the total measured signal $\frac{S_{MW}(TE)}{S_{total}(TE)}$ drops rapidly because $T_{2,MW} \ll T_{2,IEW}$.
:::

### Typical physiological reference values (at 3T)

Use the table below as a reference when adjusting parameters in the simulation:

| Brain tissue type | Typical MWF (%) | $T_{2,MW}$ (ms) | $T_{2,IEW}$ (ms) |
| :--- | :---: | :---: | :---: |
| **Healthy white matter** (e.g., corpus callosum) | $10\text{–}20\%$ | $15\text{–}25\text{ ms}$ | $70\text{–}90\text{ ms}$ |
| **Demyelinated lesion** (e.g., multiple sclerosis) | $2\text{–}8\%$ | $15\text{–}25\text{ ms}$ | $90\text{–}130\text{ ms}$ |
| **Cortical gray matter** | $3\text{–}5\%$ | $15\text{–}25\text{ ms}$ | $80\text{–}100\text{ ms}$ |

---

## Interactive simulation

Use the sliders below to vary **MWF**, **$T_{2,MW}$**, and **$T_{2,IEW}$**, and observe:
1. **Left plot:** The individual decay curves of myelin water ($S_{MW}$), intra/extracellular water ($S_{IEW}$), and the total measured signal ($S_{total}$).
2. **Right plot:** The percentage of the total signal coming from myelin water as a function of $TE$.

:::{include} notebooks/mwf_interactive.ipynb
:::

---

## Self-assessment exercise

Use the simulation (or the bi-exponential equation) to answer the following questions:

1. **Decay of myelin water signal:** Set $MWF = 20\%$, $T_{2,MW} = 20\text{ ms}$, and $T_{2,IEW} = 100\text{ ms}$. At approximately what echo time ($TE$) does the relative contribution of myelin water fall below **$5\%$** of the total signal?
2. **Impact of $T_{2,MW}$ on early echoes:** Keep $MWF = 20\%$ and $T_{2,IEW} = 100\text{ ms}$, and compare $T_{2,MW} = 10\text{ ms}$ versus $T_{2,MW} = 30\text{ ms}$. Why is a very short first echo time ($TE_1 \le 10\text{ ms}$) essential in clinical MWF MRI protocols?
3. **Effect of edema / inflammation:** In some lesions, $T_{2,IEW}$ increases (e.g., from $80\text{ ms}$ to $140\text{ ms}$) even if $A_{MW}$ remains unchanged. How does this affect the total signal curve at late echo times ($TE > 100\text{ ms}$)?

::::{dropdown} Show solutions
:color: success
:icon: check-circle

1. **Around $TE \approx 40\text{ ms}$:** At $TE = 40\text{ ms}$, $S_{MW}(40) = 0.20 \times e^{-40/20} \approx 0.027$, while $S_{IEW}(40) = 0.80 \times e^{-40/100} \approx 0.536$. The relative contribution is $\frac{0.027}{0.027 + 0.536} \approx 4.8\%$.
2. **Rapid signal loss at short $TE$:** When $T_{2,MW} = 10\text{ ms}$, over $63\%$ of the myelin water signal has already decayed by $TE = 10\text{ ms}$ ($e^{-1} \approx 0.37$), and almost $95\%$ is gone by $TE = 30\text{ ms}$. Without early echoes ($TE_1 \le 10\text{ ms}$), the short-$T_2$ component cannot be reliably separated from noise.
3. **Slower decay at late $TE$:** Because myelin water has already decayed by $TE = 100\text{ ms}$, the tail of the curve is governed almost entirely by $T_{2,IEW}$. Increasing $T_{2,IEW}$ elevates the total signal at long echo times without altering the rapid initial drop caused by myelin water.
::::

:::{note} Experimental note
This simulation assumes noise-free measurements and ideal $180^\circ$ refocusing pulses. In real multi-spin echo acquisitions, thermal noise and stimulated echoes require regularized fitting methods such as **NNLS** with **Extended Phase Graph (EPG)** correction (as implemented in **qMRLab**).
:::
