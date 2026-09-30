---
title: 'Part 3: Rotation of the head of the patient'
kernelspec:
  name: base
  display_name: Python 3
---

## Goal

Assume a Cartesian acquisition scheme. At some point during the acquisition (± 5 lines near the center, your 
choice), imagine the patient rotated their head suddenly by 20 degrees and then stayed still. Manipulate the
k-space (and if needed, image space) data to simulate this.

## Head rotation

Interactive [](Rotation) shows the impact of a sudden head rotation during Cartesian k-space acquisition. You can increase or decrease the rotation angle and see how the reconstructed image changes. The red line indicates the boundary between k-space data acquired before and after the simulated head movement.

:::{figure} #figRotation 
:label: Rotation 
Interactive visualization of head rotation during Cartesian k-space acquisition
:::

## Interpretation

In Cartesian MRI, each k-space line is acquired at a different time. Therefore, if the patient suddenly rotates during the acquisition, the k-space data acquired before and after the movement correspond to different head positions. In this simulation, the k-space acquired after the movement is replaced by the Fourier transform of the rotated image.

A rotation of the image by an angle $\theta$ produces a corresponding rotation in k-space. If the original image is $I(x,y)$ and the rotated image is $I_\theta(x,y)$, the Fourier transform can be expressed as

$$
I_\theta(x,y) = I(R_{-\theta}[x,y]),
$$

where $R_\theta$ is the rotation matrix

$$
R_\theta =
\begin{pmatrix}
\cos\theta & -\sin\theta\\
\sin\theta & \cos\theta
\end{pmatrix}.
$$

The Fourier transform of the rotated image is therefore also rotated:

$$
K_\theta(k_x,k_y) =
K(R_{-\theta}[k_x,k_y]).
$$

In the simulation, only part of k-space is replaced by the rotated data, while the other part remains unchanged. This creates an inconsistency between the different k-space lines:

$$
K_{\mathrm{motion}} =
\begin{cases}
K(k_x,k_y), & \text{before the movement}\\
K_\theta(k_x,k_y), & \text{after the movement}.
\end{cases}
$$

The inverse Fourier transform of this inconsistent k-space produces motion artifacts in the reconstructed image. As the rotation angle increases, the difference between the two parts of k-space becomes larger, resulting in increasingly visible artifacts and image distortion.
