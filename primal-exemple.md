---
title: "Optimisation linéaire : Exemple de problème primal"
author: Louis GERARD
date: 2 octobre 2018

html:
  embed_local_images: true
  embed_svg: true
  offline: false
  toc: undefined

export_on_save:
  html: true
---

# Optimisation linéaire

[Retour](index.html)
[Cours sur les problèmes primaux](primal.html)

## Problème primal : Exemple

### Enoncé
On considère le cas d’un fabricant d’automobiles qui propose deux modèles à la vente, des grosses voitures et des petites voitures. Les voitures de ce fabriquant sont tellement à la mode qu’il est certain de vendre tout ce qu’il parvient à produire, au moins au prix catalogue actuel de 16000 euros pour les grosses voitures, et 10000 euros pour les petites voitures. Son problème vient de l’approvisionnement limité en deux matières premières, le caoutchouc et l’acier. La construction d’une petite voiture nécessite l’emploi d’une unité de caoutchouc et d’une unité d’acier, tandis que celle d’une grosse voiture nécessite une unité de caoutchouc mais deux unités d’acier. Sachant que son stock de caoutchouc est de 400 unités et son stock d’acier de 600 unités, combien doit-il produire de petites et de grosses voitures au moyen de ces stocks afin de maximiser son chiffre d’affaire ? Nous appellerons x le nombre de grosses voitures produites, y le nombre de petites voitures produites, et z le chiffre d’affaire résultant.

Le problème se traduit alors sous la forme :

$max\ 16000x_1 + 10000x_2\ s.t.$
$x_1 + x_2 \le 400$
$2x_1  + x_2 \le 600$
$x_1 \ge 0, x_2 \ge 0$

Pour ce problème de maximisation, on a :
$x = \{x_1, x_2\}$
$z = \{16000, 10000\}$
$A = \begin{bmatrix}
   1 & 1 \\
   2 & 1
\end{bmatrix}$
$b = \{400, 600\}$

On peut le résoudre graphiquement comme cela :
![résolution graphique](graphique.jpg)

On devrait donc trouver une solution $x_1 = 200, x_2 = 200$



$B = \begin{bmatrix}
  1 & 1 & -1 & 0 \\
  2 & 1 & 0 & -1
\end{bmatrix}$

### Itération 1
variable entrante : $x_1$

$\frac{b}{B_1} = \begin{bmatrix}
  400/1 \\
  600/2
\end{bmatrix} = \begin{bmatrix}
  400 \\
  300
\end{bmatrix}$

$B = \begin{bmatrix}
  1-1 \times 1 & 1 - 1/2 \times 1 & -1 - 1 \times 0 & 0 - 1 \times (-1/2) \\
  2/2 & 1/2 & 0 & -1/2
\end{bmatrix} = \begin{bmatrix}
  0 & 1/2 & -1 & 1/2 \\
  1 & 1/2 & 0 & -1/2
\end{bmatrix}$

$b = \begin{bmatrix}
  400 - 1 \times 300 \\
  600 / 2
\end{bmatrix} = \begin{bmatrix}
  100 \\
  300
\end{bmatrix}$

$z = \begin{bmatrix}
  16000 - 16000 \times 1 \\
  10000 - 16000 \times 1/2
\end{bmatrix} = \begin{bmatrix}
  0 \\
  2000
\end{bmatrix}$

### Itération 2
variable entrante : $x_2$

$\frac{b}{B_1} = \begin{bmatrix}
  100 / (1/2) \\
  300 / (1/2)
\end{bmatrix} = \begin{bmatrix}
  200 \\
  600
\end{bmatrix}$

$B = \begin{bmatrix}
  0 & 1 & -2 & 1 \\
  1 & 0 & -1/2 & -1
\end{bmatrix}$

$b = \begin{bmatrix}
  100/(1/2) \\
  300 - (1/2) \times 200
\end{bmatrix}= \begin{bmatrix}
  200 \\
  200
\end{bmatrix}$

$z = \begin{bmatrix}
  0 - 2000 \times 0\\
  2000 - 2000 \times 1
\end{bmatrix} = \begin{bmatrix}
  0 \\
  0
\end{bmatrix}$

On a une solution optimale
