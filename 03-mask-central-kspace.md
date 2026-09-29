---
title: 'Part 1: Mask the central region of k-space'
kernelspec:
  name: base
  display_name: Python 3
---

## Goal

Mask the central region of k-space (e.g. using ½ of the number of voxels in both dimensions). Display the resulting k-space and magnitude of the image.

## Simple mask on central region

Interactive  [](#figMaskCenter) shows how progressively removing the central region of k-space affects the reconstructed image. You can increase or decrease the mask size (the number of pixels along the square side) and see how the reconstructed image changes. As the masked region size increases, the image progressively loses low-spatial-frequency information, which contains the image structure. Consequently, the reconstructed image becomes more and more dominated by high-frequency information, keeping edges and fine details of the image while reducing the overall contrast.

This demonstrates that the central region of k-space contains important information about image contrast and general structure, whereas the outer regions contribute more to fine details.



:::{include} part1.ipynb
:::

:::{figure} #figMaskCenter
:label: MaskCenter
Interactive visualization of central k-space masking and image reconstruction
:::
