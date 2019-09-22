$$ \text{\Large \sf  Compréhension de programmes} $$ $$ \text{\large \sf  Atelir} $$

## Message d'accueil & prompt

J'essaye de trouver le fichier compilé dans le Makefile sans succès.
J'ouvre un IDE et lance une session de debug sans trouver les lignes de code pertinentes.
À l'aide de l'IDE, je trouve que "G N U P L O T" est défini dans une variable globale **PROGRAM** dans show.c
Cette variable globale est mentionnée dans la fonction **show_all** du même fichier, elle semble afficher le message de démarrage de la CLI.
J'ajoute une variable globale **BOOTMSG** dans laquelle je stocke la chaîne "Démarrage de gnuplot..." et la mentionne dans la fonction **show_all**.
J'identifie la variable **gnuplot_date** et trouve son implémentation dans version.c. Je change sa valeur.
J'ai quelques difficultés à reconstituer le fprintf de la fonction show_all pour qu'elle prenne en compte mes ajouts, mais en prenant un peu de temps pour tout remettre à sa place, l'en-tête désiré s'affiche correctement.
Je trouve ensuite la variable **PROMPT** dans le fichier command.c et change sa valeur.

## Message « Chargement de <fichier\> »

J'essaye d'insérer un fprintf de *argv dans RECOVER_FROM_ERROR_IN_DASH (du fichier plot.c) pour afficher le fichier entré, mais sans succès.
Je passe plusieurs heures à chercher là où le message pourrait aller sans réussir à générer de nouveaux inputs avant de m'apercevoir que je travaillais sur une copie locale du fichier (qui n'était donc pas incluse dans la compilation).
J'essaye d'afficher le contenu d'argv dans plot.c, mais je me rends compte plus tard qu'il s'agît en fait des arguments de lancement de gnuplot depuis le terminal (du binaire de gnuplot lui-même donc, pas des commandes du prompt).
Je trouve finalement la fonction **loadpath_fopen** du fichier misc.c, qui prend pour paramètre une chaîne "filename", que j'utilise pour afficher le message de chargement du fichier, qui produit le résultat attendu.
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTE3Mjg0NjI3MzUsODE3NDY3NzY1LDcwOT
Y1MDAzMiwtMTY1Mzg1MzU0NCwxMDQ4MjgyNzMxLC0yMDg4NzQ2
NjEyXX0=
-->