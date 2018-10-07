> Généré depuis [StackEdit](https://stackedit.io/). Si ce fichier est sur GitHub, vous êtes en train de lire un backup du document original, qui est accessible [ici](https://frama.link/aden-iutsd) (avec de belles formules à la place des entrées Latex).
>
> Une authentification est demandée. 
> > Compte lecture seule :
> > Identifiant : **reader**
> > Mot de passe : **reader**

# Cours

## MinMax

⇒ Génération d'un arbre des possibilités, puis choix de la possibilité la plus intéressante (contexte : TicTacToe, Go...).

On assigne à chaque coup une valeur et on cherche la valeur la plus intéressante dans le cas d'un coup du programme et la moins intéressante dans le cas d'un coup de l'adversaire.

Lorsqu'il n'est pas possible d'estimer toutes les configurations de jeu, l'attribution des valeurs se fait selon des heuristiques établies par la connaissance du jeu.

## AlphaBeta

Si la valeur d'un fils Max est supérieure à la valeur courante d'un noeud Min, alors les frères du fils n'ont pas besoin d'être explorés.

![](https://upload.wikimedia.org/wikipedia/commons/thumb/9/91/AB_pruning.svg/1212px-AB_pruning.svg)

## Programmation Dynamique

À partir d'une méthode diviser-pour-régner, on résout les sous-problèmes et on stocke les résultats dans une table.
⇒ Utile pour des problèmes d'optimisation (maximisation, minimisation...).

> On dispose d'un sac de monnaie. On veut diviser le sac en deux sacs plus petits de sorte à ce que les sommes contenues dans chacun des sacs est la plus proche possible.
>> On étudie les pièces une à une en évaluant leurs combinaisons avec les pièces déjà étudiées de sorte à dégager les meilleures sommes.
>>
>> |  | 0 | 1 | ... | S/2 -1 | S/2
>> |--|---|---|---|---------|----------
>> |P1| X | | ...| |
>> |P2 = 1| X | X |... | |
>> | P3 = S/2-1 | X | X|... |X |X

# TD

## Exercice 1
```mermaid
 graph TD
 A("3") -->|g|B("3")
 A -->|c|C("2")
 A -->|d|D("1")
 B -->|g|E("3")
 B -->|c|F("4")
 B -->|d|G("5")
 C -->|g|H("7")
 C -->|c|I("2")
 C -->|d|J("9")
 D -->|g|K("1")
 D -->|c|L("5")
 D -->|d|M("8")
```

Meilleure action possible pour l'IA : g-g.

## Exercice 2

```mermaid
 graph TD
 A("N1 (1)") -->|"MAX"|B("N2 (1)")
 A -->C("N3 (1)")
 A -->D("N4 (0)")
 B -->|"min"|E("N21 (1)")
 B -->F("N22 (2)")
 C -->H("N31 (1)")
 C -->I("N32 (2)")
 C -->J("N33 (2)")
 D -->K("N41 (0)")
 D -->|"/"|L("N42 (1)")
 E -->|"MAX"|M("a (0)")
 E -->N("b (1)")
 F -->O("c (2)")
 F -->|"/"|P("d (0)")
 H -->Q("e (0)")
 H -->R("f (1)")
 I-->S("g (2)")
 I-->|"/"|T("h (0)")
 I-->|"/"|U("i (0)")
 J-->V("j (2)")
 J-->|"/"|W("k (0)")
 K-->X("l (0)")
 K-->Y("m (0)")
 K-->Z("n (0)")
 L-->A1("o (1)")
 L-->B1("p (0)")
```


## Exercice 3

``` mermaid
graph TD
C1("X -  -<br/>OOX<br/>XO -")-->|"IA<br/>+50"|C21("XX -<br/>OOX<br/>XO -<br/> (1)")
C1-->|+50|C22("X - X<br/>OOX<br/>XO -<br/> (2)")
C1-->|+50|C23("X - -<br/>OOX<br/>XOX<br/> (3)")

C21-->|"H<br/>-50"|C30("XXO<br/>OOX<br/>XO -")
C21-->|-50|C32("XX - <br/>OOX<br/>XOO")

C22-->|-100|C34("XOX<br/>OOX<br/>XO -")
C22-->|-50|C35("X - X<br/>OOX<br/>XOO")

C23-->|-100|C36("X O -<br/>OOX<br/>XOX")
C23-->|-50|C37("X - O<br/>OOX<br/>XOX")
```

Meilleure action de l'IA : (1)


