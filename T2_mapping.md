---
title: T2 Mapping
---

# T2 Mapping

## Introduction

T2 Mapping is a quantitative Magnetic Resonance Imaging (MRI) technique used to estimate the transverse relaxation time (T2) of biological tissues.

Unlike conventional T2-weighted MRI, which provides qualitative image contrast, T2 Mapping produces quantitative maps in which each voxel is associated with an estimated T2 value.

These quantitative measurements can provide additional information about tissue composition and microstructure.

## 1. Physical principles of T2 relaxation

T2 relaxation, also known as transverse relaxation, describes the loss of phase coherence between the spins of hydrogen nuclei after the application of an RF excitation pulse.

This process leads to a progressive decrease in the transverse magnetization and, consequently, in the measured MRI signal.

For a mono-exponential model, the signal decay can be described by:

$$
S(TE) = S_0 e^{-TE/T_2}
$$

where:

- $S(TE)$ is the measured signal at echo time $TE$.
- $S_0$ is the initial signal amplitude.
- $T_2$ is the transverse relaxation time.
- $TE$ is the echo time.

The T2 relaxation time characterizes how quickly the transverse MRI signal decays.

## 2. T2 Mapping

T2 Mapping consists of acquiring several images at different echo times and fitting a mathematical model to the measured signal in each voxel.

The estimated T2 values are then combined to generate a quantitative T2 map.

This approach provides information that cannot be obtained directly from a single conventional T2-weighted image.

## 3. Multi-exponential T2 Mapping

Biological tissues contain different water environments, which may exhibit different T2 relaxation times.

Consequently, their MRI signal decay may not be accurately described by a single exponential function.

A multi-exponential model can be used to represent the contributions of different water compartments:

$$
S(TE) = \sum_{i=1}^{N} A_i e^{-TE/T_{2,i}}
$$

where:

- $N$ is the number of water compartments.
- $A_i$ is the initial signal amplitude of compartment $i$.
- $T_{2,i}$ is its corresponding T2 relaxation time.

In the context of brain imaging, two important water compartments are commonly considered:

- **Myelin water (MW):** Water trapped between the myelin bilayers, characterized by a relatively short T2 relaxation time.
- **Intra- and extracellular water (IEW):** Water located inside and outside cells, characterized by a longer T2 relaxation time.

The distinction between these compartments provides the basis for Myelin Water Fraction imaging.

## 4. Applications of Multi-exponential T2 Mapping

### 4.1 Myelin Water Fraction Imaging

Myelin Water Fraction (MWF) imaging is an application of multi-exponential T2 Mapping that aims to estimate the fraction of the MRI signal associated with myelin water.

Myelin is an essential component of the central nervous system, where it surrounds axons and contributes to efficient nerve signal transmission.

Changes in myelin content are associated with several neurological conditions, including multiple sclerosis.

MWF has therefore been investigated as a potential quantitative biomarker of myelin integrity.

The conventional initial-amplitude definition of MWF is:

$$
MWF = \frac{A_{MW}}{A_{MW}+A_{IEW}} \times 100
$$

where $A_{MW}$ and $A_{IEW}$ represent the initial signal amplitudes of the myelin water and intra- and extracellular water compartments, respectively.

Since myelin water has a shorter T2 relaxation time, its signal decays faster than the signal from the IEW compartment.

This difference in relaxation times allows the two water contributions to be distinguished through multi-exponential fitting.

### 4.2 Other applications

Multi-exponential T2 Mapping and related quantitative MRI techniques can also be used to investigate tissue microstructure and water compartment properties.

Other applications include the study of T2* relaxation and quantitative susceptibility mapping (QSM).

### 4.3 Benefits and limitations

Quantitative T2 Mapping provides information about tissue properties that is not directly available from conventional MRI contrast images.

However, multi-exponential fitting can be challenging because different water compartments may have overlapping relaxation times.

The estimated parameters can also be affected by noise, acquisition settings, model assumptions and fitting methods.

MWF should therefore be interpreted as an indirect measure of myelin-associated water rather than a direct measurement of myelin content.

## 5. Interactive activities: Myelin Water Fraction

The following activities explore the principles of MWF imaging through simplified simulations and visualizations.

They are designed to complement the theoretical concepts introduced above.

:::{seealso}
Explore the interactive activities:

- {doc}`mwf_interactive`: Understand how MWF and T2 relaxation times influence signal decay.
- {doc}`mwf_maps`: Explore the spatial distribution of MWF values using simulated maps.
- {doc}`healthy_demyelinated`: Compare simplified healthy and demyelinated tissue models.
:::
