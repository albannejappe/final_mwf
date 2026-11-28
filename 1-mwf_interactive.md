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

Myelin water fraction (MWF) imaging is one of the most common applications of multi-exponential $T_2$ mapping. Myelin is a lipid-rich substance that surrounds axons in the central nervous system and facilitates rapid nerve signal conduction. In neurological disorders such as multiple sclerosis, demyelination leads to a reduction in myelin content, making MWF a valuable quantitative biomarker for monitoring disease progression and treatment efficacy.

In multi-exponential $T_2$ mapping of white matter, the $T_2$ distribution typically exhibits two main components: a short-$T_2$ peak ($T_2 < 40\text{ ms}$) attributed to water trapped between the myelin bilayers, and an intermediate-$T_2$ peak ($T_2 \approx 60\text{–}120\text{ ms}$) corresponding to intra- and extracellular water.

The Myelin Water Fraction is defined as the ratio of the area under the short-$T_2$ peak (myelin water) to the total area under the $T_2$ distribution:

$$
MWF = \frac{\int_{T_{2,\min}}^{40\text{ ms}} S(T_2)\,dT_2}{\int_{T_{2,\min}}^{T_{2,\max}} S(T_2)\,dT_2}
$$
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
