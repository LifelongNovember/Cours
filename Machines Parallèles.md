# Cours

La mémoire d'un processus est partagée avec ses threads.
**Data race** : Concurrence d'accès à une même donnée par plusieurs threads (résultat différent selon l'ordre dans lequel s'exécutent les agents).
**Mutex** : Permet de verrouiller l'exécution d'un thread.
**Multitâches** : Outil dont dispose un processeur pour traiter plusieurs tâches en même temps. Chaque tâche est assignée à un temps de traitement appelé **quantum**.

**Processus** : 
 * Lourd à lancer,
 * Copie toute la mémoire,
 * Pas de mémoire partagée.

**Thread** :
 * Plus rapide à lancer,
 *  Mémoire partagée,
 * Communication directe (data race).

**Routine** :
 * 
<!--stackedit_data:
eyJoaXN0b3J5IjpbNDI0Mzk0MzU3LDEwMzU5NjgyODMsLTE5Mz
MxNjk0ODhdfQ==
-->