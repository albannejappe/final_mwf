---
title: Healthy and Demyelinated Tissue
kernelspec:
  name: python3
  display_name: Python 3
---

# Healthy and Demyelinated Tissue

## Learning objectives

Myelin Water Fraction (MWF) imaging is widely investigated as a quantitative biomarker of myelin integrity in neurological disorders such as **multiple sclerosis (MS)**, leukodystrophies, and spinal cord injury.

In this activity, you will:
- Compare the multi-exponential $T_2$ decay curves and $T_2$ distributions of healthy white matter versus demyelinated tissue.
- Understand how myelin loss and accompanying inflammation/edema alter the two water compartments.

---

## Comparing healthy and pathological white matter

In healthy white matter, densely packed myelin sheaths trap a substantial fraction of water ($MWF \approx 15\text{–}20\%$), producing a distinct short-$T_2$ peak ($T_2 < 40\text{ ms}$).

During **demyelination**:
- Breakdown of myelin bilayers reduces the myelin water compartment ($A_{MW}$ decreases), shrinking the short-$T_2$ peak.
- Accompanying **edema, inflammation, or axonal loss** often expands the intra-/extracellular water space ($A_{IEW}$ increases) and shifts $T_{2,IEW}$ toward longer relaxation times.

| Tissue condition | Typical MWF (%) | $T_{2,MW}$ (ms) | $T_{2,IEW}$ (ms) | Primary biophysical mechanism |
| :--- | :---: | :---: | :---: | :--- |
| **Healthy white matter** | $15\text{–}20\%$ | $\approx 20\text{ ms}$ | $\approx 80\text{ ms}$ | Intact myelin bilayers |
| **Normal-appearing WM (MS)** | $12\text{–}16\%$ | $\approx 20\text{ ms}$ | $80\text{–}90\text{ ms}$ | Subtle diffuse myelin loss |
| **Acute / chronic MS lesion** | $2\text{–}8\%$ | $\approx 20\text{ ms}$ | $95\text{–}130\text{ ms}$ | Severe demyelination + edema |

---

## Interactive simulation

Use the slider below to adjust the **MWF of the demyelinated tissue** (from $2\%$ to $20\%$) while comparing it against a healthy white matter reference ($MWF = 20\%$):

- **Left plot:** Normalized signal decay $S(TE)$ over echo time.
- **Right plot:** Underlying $T_2$ distribution showing the myelin water peak ($T_2 < 40\text{ ms}$) and the intra-/extracellular water peak ($T_2 > 40\text{ ms}$).

:::{include} notebooks/healthy_demyelinated.ipynb
:::

---

## Self-assessment exercise

Consider the following questions while exploring the simulation:

1. **Initial signal contribution:** How does a decrease in MWF (from $20\%$ down to $5\%$) affect the area under the short-$T_2$ peak ($T_2 < 40\text{ ms}$) and the initial rapid drop of the signal curve?
2. **Evolution over echo time ($TE$):** How does the difference between the healthy and demyelinated signal curves evolve from early echo times ($TE < 40\text{ ms}$) to late echo times ($TE > 120\text{ ms}$)?
3. **Clinical specificity:** Why is MWF more specific to myelin loss than a standard mono-exponential $T_2$ measurement?

::::{dropdown} Show solutions
:color: success
:icon: check-circle

1. **Reduced short-$T_2$ peak and flatter initial decay:** Lowering MWF from $20\%$ to $5\%$ shrinks the short-$T_2$ peak by a factor of 4. Because less water undergoes rapid relaxation ($T_{2,MW} = 20\text{ ms}$), the steep initial drop at early echo times ($TE < 40\text{ ms}$) becomes noticeably flatter.
2. **Crossover between early and late echoes:** At very early echoes ($TE \approx 10\text{–}40\text{ ms}$), the demyelinated curve initially stays slightly higher if $T_{2,IEW}$ is prolonged by edema, or diverges depending on total water content. At late echoes ($TE > 120\text{ ms}$), myelin water has completely decayed in both tissues, so the separation between the two curves is driven solely by the difference in $T_{2,IEW}$ ($80\text{ ms}$ vs. $105\text{ ms}$).
3. **Separating myelin from water content/edema:** A mono-exponential $T_2$ fit averages all water compartments together and cannot distinguish whether an elevated $T_2$ comes from demyelination or from inflammation/edema. Multi-exponential MWF isolates the short-$T_2$ water trapped within myelin sheaths, providing a more direct indicator of myelin integrity.
::::

:::{important}
This is a simplified educational model. While a decrease in MWF is strongly associated with demyelination, MWF remains an indirect marker of myelin water and can also be influenced by iron deposition, axonal density, and inter-compartmental water exchange.
:::
