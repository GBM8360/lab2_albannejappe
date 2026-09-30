---
title: Lab 2 MyST Book
description: MRI K-Space Manipulations
---

# MRI K-Space Manipulations

## Introduction

Magnetic Resonance Imaging (MRI) data are acquired in the spatial-frequency domain, commonly referred to as **k-space**. The acquired k-space data are transformed into an image using the inverse Fourier transform (IFT).

The objective of this project is to explore how modifications of k-space affect the reconstructed MRI image. Three different situations are investigated: masking the central region of k-space, reducing the sampling density, and simulating patient motion during Cartesian acquisition.

The experiments are implemented using interactive visualizations, allowing the effects of different parameters to be explored directly.

## Project objectives

This project investigates three fundamental aspects of MRI reconstruction:

1. **Central k-space masking**  
   Explore the effect of removing low-spatial-frequency information on image contrast and anatomical structures.

2. **K-space downsampling**  
   Investigate how reducing the sampling density affects the field of view, spatial resolution, and aliasing, as well as the effect of zero-filling.

3. **Motion during acquisition**  
   Simulate a sudden head rotation during Cartesian k-space acquisition and observe the resulting motion artifacts.


## Interactive exploration

Each section contains an interactive visualization that allows the effect of different parameters to be explored. These visualizations complement the static results by making it possible to observe how changes in k-space progressively affect the reconstructed image.

## Organization

The project is divided into three parts:

```{tableofcontents}
