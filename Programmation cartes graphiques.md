
# Cours

> M. Ammi (ammi@limsi.fr)

## Pipeline Graphique

Entrée : Modèle géométrique, d'illumination, de caméra et de fenêtre.
Sortie : Couleur et intensité de l'affichage.

### Transformations de modélisation

Projections et rotations qui permettent de positionner des objets dans la scène.
⇒ Repère objet

### Illumination (Shading)

Interaction de diffusion de la lumière avec un objet en fonction des propriétés de celui-ci.

### Transformations d'affichage

Représentation des objets dans le référentiel de la caméra au moyen de projections (changement de référentiel).
⇒ Repère scène

### Clipping

Élimination de tout ce qui n'est pas visible / utile par la caméra (trop loin, derrière, etc) du calcul d'affichage.
⇒ Repère caméra

### Transformations écran (Projection)

Passage de la 3D à la 2D — Introduction de la perspective, de la stéréoscopie, des ombres portées et des textures.
⇒ Repère caméra normalisé (NDC)

### Pixellisation (Rasterization)

Dessin des primitives en 2D (activation des suites de pixels).
⇒ Espace écran

### Visibilité / Affichage

Élimination des faces cachées.

## Implémentation

Le hardware s'est progressivement introduit dans la pipeline (absent dans un premier temps, puis limité à l'affichage à la pixellisation et à l'affichage, avant de se généraliser), est devenu configurable puis programmable.

## Concepts mathématiques

### Entités & opérations

**Scalaire** : grandeur définie par un nombre et une unité.
**Vecteur** : entité mathématique définie par n valeurs numériques extraites d'un même ensemble (par exemple $\mathbb N, \mathbb Z, \mathbb R, \mathbb C$).
Dans un repère, les vecteurs sont placés dans une base.
Signe du produit scalaire : 
 - $\vec A \cdot \vec B \gt 0 : \ -90° \lt \theta \lt 90°$
 -  $\vec A  \vec B = 0 : \ \pm 90°$
 - $\vec A \cdot \vec B \lt 0 : \ -180° \lt \theta \lt -90° \text{ ou } 90° \lt \theta \lt 180°$

Produit vectoriel :
$$ \vec A \cdot \vec B = \left |
\begin{matrix}
\vec i & \vec j & \vec k \\
A_x & A_y & A_z \\ 
B_x & B_y & B_z
\end{matrix} \right | = + \vec i \left |
\begin{matrix}
\vec A_y & \vec A_z \\
\vec B_y & \vec B_z
\end{matrix} \right | - \vec j \left | \begin{matrix}
\vec A_x & \vec A_z \\
\vec B_x & \vec B_z
\end{matrix} \right | + \vec k \left |
\begin{matrix}
\vec A_x & \vec A_y \\
\vec B_x & \vec B_y
\end{matrix} \right |
$$
Règle de la main droite :
![](https://raw.githubusercontent.com/LifelongNovember/Cours/master/img/main%20droite.png)
### Transformations

#### Rigide / Euclidienne

⇒ Translation (3 DDL) + Rotation (3 DDL) = 6 degrés de liberté

#### Similitude

⇒ Translation + Rotation + Homothétie (3 DDL) : 9 degrés de liberté

#### Transformation Affine

⇒ Translation + Rotation + Homothétie + Réflexion (3DDL) : 12 degrés de liberté

#### Transformation Projective ou Homographie

⇒ Translation + Rotation + Homothétie + Réflexion + Projection (3DDL) : 15 degrés de liberté

# TD

## TD0

### Exercice 1
<div align="center"><img src="https://raw.githubusercontent.com/LifelongNovember/Cours/master/img/cg_exo1.png" width=500px /></div>


Équation du plan : $ax + by + cz + d = 0$
Vecteur orthogonal : $\vec v \cdot \vec d = 0$
$$
\begin{aligned}\vec v = \begin{pmatrix} x \\ y \\ z \end{pmatrix} - \vec p = \begin{pmatrix} x - p_x \\ y - p_y \\ z - p_z \end{pmatrix} &\iff
\vec v \cdot \vec d = \begin{pmatrix} x - p_x \\ y - p_y \\ z - p_z \end{pmatrix} \cdot \begin{pmatrix} d_x \\ d_y \\d_z \end{pmatrix} \\ \\
& \iff (x - p_x) d_x + (y - p_y) d_y + (z - p_z) d_z = 0 \\ \\
& \iff{d_x \over a} x + {d_y \over b} y + {d_z \over c}z - {(p_x d_x + p_y d_y + p_z d_z) \over d} = 0
\end{aligned}
$$

### Exercice 2

Le vecteur normal à l'une des faces doit être orthogonal à au moins deux des arêtes de l'autre face pour que les deux faces soient parallèles.

<div align="center"><img src="https://raw.githubusercontent.com/LifelongNovember/Cours/master/img/faces%20triangulaires.png" width=200px/></div>

# Cours

> M. Ammi (ammi@limsi.fr)

## Pipeline Graphique

Entrée : Modèle géométrique, d'illumination, de caméra et de fenêtre.
Sortie : Couleur et intensité de l'affichage.

### Transformations de modélisation

Projections et rotations qui permettent de positionner des objets dans la scène.
⇒ Repère objet

### Illumination (Shading)

Interaction de diffusion de la lumière avec un objet en fonction des propriétés de celui-ci.

### Transformations d'affichage

Représentation des objets dans le référentiel de la caméra au moyen de projections (changement de référentiel).
⇒ Repère scène

### Clipping

Élimination de tout ce qui n'est pas visible / utile par la caméra (trop loin, derrière, etc) du calcul d'affichage.
⇒ Repère caméra

### Transformations écran (Projection)

Passage de la 3D à la 2D — Introduction de la perspective, de la stéréoscopie, des ombres portées et des textures.
⇒ Repère caméra normalisé (NDC)

### Pixellisation (Rasterization)

Dessin des primitives en 2D (activation des suites de pixels).
⇒ Espace écran

### Visibilité / Affichage

Élimination des faces cachées.

## Implémentation

Le hardware s'est progressivement introduit dans la pipeline (absent dans un premier temps, puis limité à l'affichage à la pixellisation et à l'affichage, avant de se généraliser), est devenu configurable puis programmable.

## Concepts mathématiques

### Entités & opérations

**Scalaire** : grandeur définie par un nombre et une unité.
**Vecteur** : entité mathématique définie par n valeurs numériques extraites d'un même ensemble (par exemple $\mathbb N, \mathbb Z, \mathbb R, \mathbb C$).
Dans un repère, les vecteurs sont placés dans une base.
Signe du produit scalaire : 
 - $\vec A \cdot \vec B \gt 0 : \ -90° \lt \theta \lt 90°$
 -  $\vec A  \vec B = 0 : \ \pm 90°$
 - $\vec A \cdot \vec B \lt 0 : \ -180° \lt \theta \lt -90° \text{ ou } 90° \lt \theta \lt 180°$

Produit vectoriel :
$$ \vec A \cdot \vec B = \left |
\begin{matrix}
\vec i & \vec j & \vec k \\
A_x & A_y & A_z \\ 
B_x & B_y & B_z
\end{matrix} \right | = + \vec i \left |
\begin{matrix}
\vec A_y & \vec A_z \\
\vec B_y & \vec B_z
\end{matrix} \right | - \vec j \left | \begin{matrix}
\vec A_x & \vec A_z \\
\vec B_x & \vec B_z
\end{matrix} \right | + \vec k \left |
\begin{matrix}
\vec A_x & \vec A_y \\
\vec B_x & \vec B_y
\end{matrix} \right |
$$
Règle de la main droite :
![](https://raw.githubusercontent.com/LifelongNovember/Cours/master/img/main%20droite.png)
### Transformations

#### Rigide / Euclidienne

⇒ Translation (3 DDL) + Rotation (3 DDL) = 6 degrés de liberté

#### Similitude

⇒ Translation + Rotation + Homothétie (3 DDL) : 9 degrés de liberté

#### Transformation Affine

⇒ Translation + Rotation + Homothétie + Réflexion (3DDL) : 12 degrés de liberté

#### Transformation Projective ou Homographie

⇒ Translation + Rotation + Homothétie + Réflexion + Projection (3DDL) : 15 degrés de liberté

# TD

## TD0

### Exercice 1
<div align="center"><img src="https://raw.githubusercontent.com/LifelongNovember/Cours/master/img/cg_exo1.png" width=500px /></div>


Équation du plan : $ax + by + cz + d = 0$
Vecteur orthogonal : $\vec v \cdot \vec d = 0$
$$
\begin{aligned}\vec v = \begin{pmatrix} x \\ y \\ z \end{pmatrix} - \vec p = \begin{pmatrix} x - p_x \\ y - p_y \\ z - p_z \end{pmatrix} &\iff
\vec v \cdot \vec d = \begin{pmatrix} x - p_x \\ y - p_y \\ z - p_z \end{pmatrix} \cdot \begin{pmatrix} d_x \\ d_y \\d_z \end{pmatrix} \\ \\
& \iff (x - p_x) d_x + (y - p_y) d_y + (z - p_z) d_z = 0 \\ \\
& \iff{d_x \over a} x + {d_y \over b} y + {d_z \over c}z - {(p_x d_x + p_y d_y + p_z d_z) \over d} = 0
\end{aligned}
$$

### Exercice 2

Le vecteur normal à l'une des faces doit être orthogonal à au moins deux des arêtes de l'autre face pour que les deux faces soient parallèles.

<div align="center"><img src="https://raw.githubusercontent.com/LifelongNovember/Cours/master/img/faces%20triangulaires.png" width=200px/></div>


<!--stackedit_data:
eyJoaXN0b3J5IjpbLTIwNzI0ODAzNTgsMTEzODY2MjcyOF19
-->