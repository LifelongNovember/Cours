# Cours

La mémoire d'un processus est partagée avec ses threads.
**Data race** : Concurrence d'accès à une même donnée par plusieurs threads (résultat différent selon l'ordre dans lequel s'exécutent les agents).
**Mutex** : Primitive d'exécution qui permet de réguler l'accès aux données de sorte à ce qu'une seule routine n'y accède à la fois.
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
& \text{set nb}
\end{array}$$
<!--stackedit_data:
eyJoaXN0b3J5IjpbMTE5NTA2MDg4OSwzNTQ5ODQzNzIsMTAzNT
k2ODI4MywtMTkzMzE2OTQ4OF19
-->