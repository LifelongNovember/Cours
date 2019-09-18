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

``` c
bool isLocked = false
if(isLocked == false) {
  isLocked = true
}
else {
  while(isLocked) {
    thread.sleep() / thread.yield()
  }
}
isLocked = true
...
```

**État de famine** : Point à partir duquel le système limite les performances globales à force d'attendre l'accès aux données.
**Deadlock** : Interblocage entre deux threads.


$$ \begin{array}{c|c}
\text{\bf Thread 1} & \text{\bf Thread 2} \\
\hline \\
\text{M1.lock()} & \text{M2.lock()} \\ \\
\text{wait M2} & \text{wait M1}
\end{array}$$

**Inversion des priorités** : Lorsque des threads ont des fonctions différentes d'importance plus ou moins grande, les mutex ne sont pas capables de gérer les priorités
<!--stackedit_data:
eyJoaXN0b3J5IjpbMTc4ODIwNjI4MSwtMTM3ODY5MjUxNiwzNT
Q5ODQzNzIsMTAzNTk2ODI4MywtMTkzMzE2OTQ4OF19
-->