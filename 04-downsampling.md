---
title: 'Part 2: Downsample the k-space by half'
kernelspec:
  name: base
  display_name: Python 3
---

## Goal
Downsample the k-space by half in one direction (e.g., use any tool or method you want). Display the resulting k-space and magnitude of the image.

## Downsampling

Interactive [](#figDownsamplingX) and [](#figDownsamplingY) show k-space undersampling in the two spatial directions. To do so, every other line in k-space has been deleted. Therefore, this decreases the spatial resolution in the corresponding direction. Also, as the matrix size has been reduced, aliasing appears in the direction in which the k-space has been downsampled.
compare k-space undersampling and zero-filling in the two spatial directions. Undersampling reduces the number of acquired k-space samples, which decreases the spatial resolution in the corresponding direction. In contrast, zero-filling increases the matrix size by adding zeros without adding new information; it can make the reconstructed image appear smoother and provide a denser image grid, but it does not recover the spatial information lost during undersampling.

The effect is particularly clear when switching between the two directions: reducing the sampling density in one direction mainly affects the image resolution along that direction. This illustrates the relationship between k-space sampling, matrix size, field of view, and spatial resolution.


:::{figure} #figDownsamplingX
:label: DownsamplingX
Interactive visualization of k-space undersampling in the X direction
:::

:::{figure} #figDownsamplingY
:label: DownsamplingY
Interactive visualization of k-space undersampling in the Y direction
:::

## Zero-filling

Interactive [](#figZeroFillX) and [](#figZeroFillY) show zero-filling in the two spatial directions. This time, k-space values have been replaced by 0 in one half. Thus, the matrix size is the same as before (contrary to downsampling, which reduces its size by half) and the image appears quite the same, only smoother in the opposite direction.

Here, all the left part of the k-space is set to 0. It gives a blur effect on the resulting image in the horizontal direction.
Downsampling k-space by a factor of two in one direction increases the spacing between k-space samples, which
reduces the FOV by a factor of two in that direction. The maximum sampled spatial frequency is also reduced, leading
to a decrease in spatial resolution. Consequently, the reconstructed image has a smaller FOV and appears less detailed
in the downsampled direction

:::{figure} #figZeroFillX
:label: ZeroFillX
Interactive visualization of zero-filling in the X direction
:::

:::{figure} #figZeroFillY
:label: ZeroFillY
Interactive visualization of zero-filling in the Y direction
:::

## Interpretation

For a Cartesian acquisition, the field of view (FOV) is related to the number of acquired voxels and the voxel size by

$$
FOV = N_{\mathrm{vox}} \times \Delta x (1)
$$

where $N_{\mathrm{vox}}$ is the number of voxels and $\Delta x$ is the spatial resolution. The FOV is also related to the sampling interval in k-space:

$$
FOV = \frac{1}{\Delta k} (2)
$$

When k-space is undersampled by a factor of two in one direction, the number of acquired samples is reduced by half. If the sampling interval $\Delta k$ is increased accordingly, the FOV becomes smaller:

$$
\Delta k' = 2\Delta k
$$

and therefore

$$
FOV' = \frac{1}{\Delta k'} = \frac{FOV}{2}.
$$

The smaller FOV means that the reconstructed image covers a smaller spatial region. If the object extends beyond this reduced FOV, spatial locations outside the FOV are mapped back into the image, producing aliasing or wrap-around artifacts.

The spatial resolution is related to the extent of k-space that is sampled:

$$
\Delta x = \frac{FOV}{N_{\mathrm{vox}}}
$$

Thus, reducing the number of acquired samples does not necessarily mean that the voxel size is simply reduced. In this experiment, the reduced sampling density primarily decreases the FOV and introduces aliasing because the object is larger than the new FOV.

Zero-filling produces a different effect. Adding zeros to k-space increases the reconstructed matrix size without adding new spatial-frequency information. Therefore, it can make the image appear smoother or provide a denser pixel grid, but it does not recover the information lost during undersampling.

