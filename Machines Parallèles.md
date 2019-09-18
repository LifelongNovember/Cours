# Cours

La mémoire d'un processus est partagée avec ses threads.
**Data race** : Concurrence d'accès à une même donnée par plusieurs threads (résultat différent selon l'ordre dans lequel s'exécutent les agents).
**Mutex** : Permet de verrouiller l'exécution d'un thread de sorte à ce qu'une seule routine n'y accède à la fois.
**Multitâches** : Outil dont dispose un processeur pour traiter plusieurs tâches en même temps. Chaque tâche est assignée à un temps de traitement appelé **quantum**.

**Processus** : 
 * Lourd à lancer,
 * Copie toute la mémoire,
 * Pas de mémoire partagée.

**Thread** :
 * Plus rapide à lancer,
 *  Mémoire partagée,
 * Communication directe (data race).

$$ \text {nb = 1} \quad \begin{array}{|c|c}
\text{\bf Thread 1} & \text{\bf Thread 2} \\
\text{get nb} & \\
 & \text{get nb} \\ 
\text{nb++} \rightarrow \text{nb} = 2 & \\
& \text{nb++} \rightarrow \text{nb} = 2 \\
\text{set nb} & \\
& \
\end{array}$$
<!--stackedit_data:
eyJoaXN0b3J5IjpbMTE3OTE5ODM4MCwxMDM1OTY4MjgzLC0xOT
MzMTY5NDg4XX0=
-->