J'essaye de trouver le fichier compilé dans le Makefile sans succès.
J'ouvre un IDE et lance une session de debug sans trouver les lignes de code pertinentes.
À l'aide de l'IDE, je trouve que "G N U P L O T" est défini dans une variable globale PROGRAM dans show.c
Cette variable globale est mentionnée dans la fonction show_all sur ce même fichier, elle semble afficher le message de démarrage de la CLI.
J'ajoute une variable globale BOOTMSG dans laquelle je stocke la chaîne "Démarrage de gnuplot..." et la mentionne dans la fonction show_all.
J'identifie la variable gnuplot_date et trouve sa définition dans version.c. Je change sa valeur.
J'ai quelques difficultés à reconstituer le fprintf de la fonction show_all pour qu'elle prenne en compte mes ajouts, mais en prenant un peu de temps pour tout remettre à sa place, l'en-tête désiré s'affiche correctement.
Je trouve ensuite la variable PROMPT dans le fichier command.c et change sa valeur.
J'essaye d'insérer un fprintf de *argv dans RECOVER_FROM_ERROR_IN_DASH (du fichier plot.c) pour afficher le fichier entré, mais sans succès.
<!--stackedit_data:
eyJoaXN0b3J5IjpbNzA5NjUwMDMyLC0xNjUzODUzNTQ0LDEwND
gyODI3MzEsLTIwODg3NDY2MTJdfQ==
-->