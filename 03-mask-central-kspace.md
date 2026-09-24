---
title: 'Part 1: Mask the central region of k-space'
kernelspec:
  name: base
  display_name: Python 3
---

## Goal

Mask the central region of k-space (e.g. using ½ of the number of voxels in both dimensions). Display the resulting k-space and magnitude of the image.

## Simple mask on central region

figure interactive avec un slider pour choisir la taille de la zone à masquer OK

Ajouter une légende + explication de la figure

Choses à corriger pour que ce soit parfait!:
- échelle de couleur?
- figure plus haute (là elle est toute ratatinée)
- colorbar sur le côté: plusieurs chiffres s'affichent, et ça change quand on glisse le slider
- si possible, modifier le fond pour qu'il soit uniforme (ou alors changer les Nan dans le code en une valeur fixe (style du noir ou du blanc))


:::{include} part1.ipynb
:::

:::{figure} #figMaskCenter
:label: MaskCenter
:::
