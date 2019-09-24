https://raw.githubusercontent.com/LifelongNovember/Cours/master/img/transition.png# Langages : interprétation et compilation

> Pablo Rauzy pr@up8.edu pablo.rauzy.name/teaching/liec

**Interpréteur** : programme qui exécute directement les instructions du code source.
 * Lit et analyse une expression,
 * L'évalue si elle est valide
 * (CF diapo)

**Compilateur** : programme qui traduit un langage dans un autre langage plus bas niveau.
Le compilateur produit généralement un exécutable mais pas nécessairement. 
Le compilateur est *correct* si la sémantique du code produit est la même que celle du code source.

Il se divise en trois parties : 
 * **front end** : lecture du code source et transformation en langage intermédiaire.
 * **middle end** : fait plusieurs passes de traitement dans le langage intermédiaire.
 * **back end** : produit le code final à partir du langage intermédiaire.

**Lexer** :

![](https://raw.githubusercontent.com/LifelongNovember/Cours/master/img/transition.png)
![](https://www.plantuml.com/plantuml/svg/SoWkIImgAStDuUAArefLqDLDoI_FqxLJyCiliL9Gv09I2Z0XMrjdMrjKLVu5YKLM2XfS81gVEcUmEaqkPmBg78kBCzFph1HikI0iV6g3KtCphHIikK0qDdLGaH03AmKrhX03k81ZNWf814ZXqsLefL335M885_0l0WduOtKzJ8-HbK9qecvLB5U8aG867weeBB68AmmZ4C0aq6js2a030G00)
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTE3ODE3MzcwMTYsLTkyNTMxMzYyMSwxMz
UzODQ3NDI0LDEwODk3OTQyNTgsNTgwNDgwMzc2LDEwODk3OTQy
NTgsMTA4OTc5NDI1OCwtMjI0NDQ1NTMyLC0yMDY5MTk1MzYyLC
0xNzEzNTc2MjU2LDEwODc3MzcyNzYsLTE1MjgyMjk0NDUsLTIw
ODg3NDY2MTJdfQ==
-->