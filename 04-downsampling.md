---
title: 'Part 2: Downsample the k-space by half'
kernelspec:
  name: base
  display_name: Python 3
---

## Goal
Downsample the k-space by half in one direction (e.g., use any tool or method you want). Display the resulting k-space and magnitude of the image.

## Downsampling

Interactive [](#DownsamplingX) and [](#DownsamplingY) show k-space undersampling in the two spatial directions. To do so, every other line in k-space has been deleted. Therefore, this decreases the spatial resolution in the corresponding direction. Also, as the matrix size has been reduced, aliasing appears in the direction in which the k-space has been downsampled.

:::{figure} #figDownsamplingX
:label: DownsamplingX
Interactive visualization of k-space undersampling in the X direction
:::

:::{figure} #figDownsamplingY
:label: DownsamplingY
Interactive visualization of k-space undersampling in the Y direction
:::

## Zero-filling

Interactive [](#ZeroFillX) and [](#ZeroFillY) show zero-filling in the two spatial directions. This time, k-space values have been replaced by 0 in one half. Thus, the matrix size is the same as before (contrary to downsampling, which reduces its size by half) and the image appears quite the same, only smoother in the opposite direction.

Even though the goal was only to do the downsampling, you can also see zero-filling because during lab 1, I did zero-filling instead of downsampling. This lab allowed me to understand the difference in the concepts but also their difference in the reconstructed image.

:::{figure} #figZeroFillX
:label: ZeroFillX
Interactive visualization of zero-filling in the X direction
:::

:::{figure} #figZeroFillY
:label: ZeroFillY
Interactive visualization of zero-filling in the Y direction
:::

## Interpretation

For a Cartesian acquisition, the FOV is related to the number of acquired voxels and the voxel size by

$$
FOV = N_{\mathrm{vox}} \times \Delta x
$$

where $N_{\mathrm{vox}}$ is the number of voxels and $\Delta x$ is the spatial resolution. The FOV is also related to the sampling interval in k-space:

$$
FOV = \frac{1}{\Delta k}
$$

When k-space is undersampled by a factor of two in one direction, the number of acquired samples is reduced by half. If the sampling interval $\Delta k$ is increased, the FOV becomes smaller:

$$
\Delta k' = 2\Delta k
$$

and therefore

$$
FOV' = \frac{1}{\Delta k'} = \frac{FOV}{2}.
$$

The smaller FOV means that the reconstructed image covers a smaller spatial region. If the object extends beyond this reduced FOV, spatial locations outside the FOV are mapped back into the image, producing aliasing.

Moreover, the spatial resolution is related to the extent of k-space that is sampled:

$$
\Delta x = \frac{FOV}{N_{\mathrm{vox}}}
$$

Thus, reducing the number of acquired samples does not necessarily mean that the voxel size is simply reduced. In this experiment, the reduced sampling density primarily decreases the FOV and introduces aliasing because the object is larger than the new FOV.

Zero-filling produces a different effect. Adding zeros to k-space increases the reconstructed matrix size without adding new spatial-frequency information. Therefore, it can make the image appear smoother or provide a denser pixel grid, but it does not recover the information lost during undersampling.

