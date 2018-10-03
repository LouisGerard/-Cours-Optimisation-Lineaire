---
title: "Optimisation linéaire : Problème primal"
author: Louis GERARD
date: 2 octobre 2018
output: pdf_document
export_on_save:
  pandoc: true
wrap: preserve
---

# Optimisation linéaire
## Problème primal
### Enoncé du problème
minimisation :
$min\ zx\ s.t.$
$Ax \ge b$

maximisation :
$max\ zx\ s.t.$
$Ax \le b$

# Todo expliquer la notation matricielle

#### Exemple
On considère le cas d’un fabricant d’automobiles qui propose deux modèles à la vente, des grosses voitures et des petites voitures. Les voitures de ce fabriquant sont tellement à la mode qu’il est certain de vendre tout ce qu’il parvient à produire, au moins au prix catalogue actuel de 16000 euros pour les grosses voitures, et 10000 euros pour les petites voitures. Son problème vient de l’approvisionnement limité en deux matières premières, le caoutchouc et l’acier. La construction d’une petite voiture nécessite l’emploi d’une unité de caoutchouc et d’une unité d’acier, tandis que celle d’une grosse voiture nécessite une unité de caoutchouc mais deux unités d’acier. Sachant que son stock de caoutchouc est de 400 unités et son stock d’acier de 600 unités, combien doit-il produire de petites et de grosses voitures au moyen de ces stocks afin de maximiser son chiffre d’affaire ? Nous appellerons x le nombre de grosses voitures produites, y le nombre de petites voitures produites, et z le chiffre d’affaire résultant.

Le problème se traduit alors sous la forme :

$max\ 16000x_1 + 10000x_2\ s.t.$
$x_2 + x_1 \le 400$
$2x_2  + x_1 \le 600$
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

### Variables sortantes
On commence par créer autant de variables sortantes que l'on a de contraintes :
$x_s$
et leurs coefficients :
$B = [b^T; -A]$
Ces variables sont dans le système et sont égales à zéro. On va essayer de les sortir du système afin de les échanger avec les variables entrantes ($x$).

#### Exemple
Pour le même exemple :
$x_s = \{x_3, x_4\}$
$B = \begin{bmatrix}
  400 & -1 & -1 \\
  600 & -2 & -1
\end{bmatrix}$

### Choix de la variables entrante
Pour éviter les cycles, on va choisir $x_i$ comme variable entrante dans l'ordre des $i$

#### Exemple
Pour notre exemple, la première variable entrante sera $x_1$, puis $x_2$

### Choix de la variable sortante
On va voir quelle variable sortante est la plus contraignante pour la variable entrante.
On va donc choisir la variable sortante correspondant à la ligne de $B$:
- S'il s'agit d'un problème de minimisation :
  $max(-B\{1, x\})$
- S'il s'agit d'un problème de maximisation :
  $min(-B\{1, x\})$

#### Exemple
Il s'agit ici d'un problème de maximisation, on va donc prendre
$min(-B\{1, x\}) = $
$min(-\begin{bmatrix}
  400 & -1 & -1 \\
  600 & -2 & -1
\end{bmatrix} \{1, x_1, x_2\}) = $
$min(\begin{bmatrix}
  -400 & 1 & 1 \\
  -600 & 2 & 1
\end{bmatrix} \{1, 0, 0\}) = $
$min(\begin{bmatrix}
  -400 & 0 & 0 \\
  -600 & 0 & 0
\end{bmatrix}) = -600$
Il s'agit donc de la deuxième ligne, on va donc prendre la première variable sortante : $x_4$

### Echange de variables
On va maintenant pouvoir faire rentrer la variable entrante et sortir la variable sortante.
