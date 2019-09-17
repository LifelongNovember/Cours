# Cours

## Normalisation

### Rappels

#### Première forme normale

> Une relation R est dite en première forme normale ssi tous ses attributs sont atomiques.

**Exemple** :

| Livre | Titre | Auteur | Prix |
|-------|-------|--------| -----|
|       |Germinal|Pascal|10-12|
|       |Optimisation|Ali|13-14|
|       |Bases de données | Georges|12

La relation Livre n'est pas en première forme normale (1NF) car l'attribut prix n'est pas atomique.
La relation Livre peut être normalisée pour respecter la 1NF de la manière suivante :
| Livre | Titre | Auteur | PrixMin | PrixMax
|-------|-------|--------| -----|---
|       |Germinal|Pascal|10|12
|       |Optimisation|Ali|13|14
|       |Bases de données | Georges|12 | 12

#### Deuxième forme normale

> Une relation R est 2NF ssi :
> * Elle est en 1NF
> * Aucun attribut non-clé ne dépend d'une partie de la clé. 

**Remarque** : Toute relation dont la clé est composée d(un seul attribut et qui respecte la 1NF est forcément 2NF.

**Exemple 1** : 
$R(A,B,C,D) : \text{une relation } \{A \rightarrow B, C \rightarrow D, F \rightarrow C, FD \rightarrow A \}$, ensemble de dépendances fonctionnelles valides sur $R$.

**Graphe des DF de R**

```mermaid
graph LR
A((A)) -->B((B))
F((F)) --> A
D((D)) --> A
C((C)) --> D
F --> C
```

Tout attribut n'appartenant à aucune des parties droites des dépendances fonctionnelles doit faire partie de la clé.
⇒ $F \in \text{clé}$
$$\begin{aligned} FD \rightarrow A   &(1) \\ F \rightarrow C &(2) \\ C \rightarrow D &(3) \\ F \rightarrow D &(4)\end{aligned}$$

$$\begin{aligned} (4) \text{ et } (1) \ &FF \rightarrow A \\ &F \rightarrow A \\ &F \rightarrow B \text{ par transitivité}\end{aligned}$$ $F$ est une clé candidate, elle est unique.
⇒ Clé atomique : $R$ 2NF.

**Exemple 2** :

$R(ABCD) : A \rightarrow B, C\rightarrow D.$
$(A) \rightarrow (B)$ : une partie de la clé ⇒ un attribut n'appartenant pas à la clé.
$(C) \rightarrow (D)$

Clé de $R$ :
$AC$ doivent faire partie de la clé.
$AC \rightarrow A, AC\rightarrow C, AC \rightarrow B, AC \rightarrow D$ : $AC$ est une clé unique.
$R$ n'est pas 2NF car $A \rightarrow B$ est de la forme $\text{partie de la clé } \rightarrow \text{ attribut} \notin \text{ clé}$.

CF (1)

Cette décomposition est sans perte de dépendances fonctionnelles ?
Oui : les deux DF initiales sont préservées.

| R | A | B | C | D
|-------|-------|--------| -----|---
|       |1|2|3|4
|  $\rightarrow$     |1|2|7|8
|       |9 | 10|3 | 4

$$ \\ $$
|R1|A|B|
--|--|--
|  | 1 | 2 |
|  | 9 | 10 |

$$ \\ $$
|R2|C|D|
--|--|--
|  | 3 | 4 |
|  | 7 | 8 |

$$  R1 (\times) R2 = R1 \times R2 $$ $$ \begin{aligned}R1 (\times) R2 &= R :\text{sans perte d'informations}  \\ &\neq R : \text {perte d'informations} \end{aligned} $$ $R1 (\times) R2 :$

|A|B|C|D|
|-|-|-|-|
|1|2|3|4|
|1|2|7|8|
|9|10|3|4|
|$\bf9$|$\bf10$|$\bf7$|$\bf8$|

Le tuple $(9,10,7,8) \notin R$.
$$ R1 (\times) R2 = R + (9, 10, 7, 8)$$

**Exemple 3**

$$ R(A,B,C,D) : AB \rightarrow C, DE \rightarrow C, B \rightarrow E, $$

```mermaid
graph LR
A((A)) -->C((C))
B((B)) --> C
B --> E((E))
E --> B
E --> C
D((D)) --> C
```

### Forme normale 4

### Forme normale 5

## Gestion des transactions

## Optimisation

## Techniques de stockage

## Administration
<!--stackedit_data:
eyJoaXN0b3J5IjpbMTI5ODc4NDUwOCw3NDg2MDAzMjRdfQ==
-->