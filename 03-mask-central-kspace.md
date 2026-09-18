---
title: 'Part 1: Mask the central region of k-space'
kernelspec:
  name: base
  display_name: Python 3
---

## Goal

Mask the central region of k-space (e.g. using ½ of the number of voxels in both dimensions). Display the resulting k-space and magnitude of the image.

## Simple mask on central region

Pour le code: ne pas tout refaire mes codes en python, on peut importer les figures en .mat et grâce à SciPy les insérer dans le notebook, et utiliser save dans matlab pour exporter les image en .mat

figure interactive avec un slider pour choisir la taille de la zone à masquer

:::{include} part1.ipynb
:::

:::{figure} notebooks/mask-center.ipynb#figMaskCenter
:label: MaskCenter
:::
