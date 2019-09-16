J'essaye de trouver le fichier compilé dans le Makefile sans succès.
J'ouvre un IDE et lance une session de debug sans trouver les lignes de code pertinentes.
À l'aide de l'IDE, je trouve que "G N U P L O T" est défini dans une variable globale PROGRAM dans show.c
Cette variable globale est mentionnée dans la fonction show_all sur ce même fichier, elle semble afficher le message de démarrage de la CLI.
J'ajoute une variable globale BOOTMSG dans laquelle je stocke la chaîne "Démarrage de gnuplot..." et la mentionne

<!--stackedit_data:
eyJoaXN0b3J5IjpbLTE4MzYxMTE1NzQsMTA0ODI4MjczMSwtMj
A4ODc0NjYxMl19
-->