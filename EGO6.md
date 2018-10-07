> Généré depuis [StackEdit](https://stackedit.io/). Si ce fichier est sur GitHub, vous êtes en train de lire un backup du document original, qui est accessible [ici](https://frama.link/aden-iutsd) (avec de belles formules à la place des entrées Latex).
>
> Une authentification est demandée. 
> > Compte lecture seule :
> > Identifiant : **reader**
> > Mot de passe : **reader**

# TP

## Processus & ERP

### I -  Les processus

> #### Retrouver les 3 types de processus

* Processus métier
* Processus support
* Processus de direction

> #### De quels processus sont clients les adhérents, les agents des médiathèques et l'agglomération ?

* Agent des médiathèques : Processus support
* Adhérent : Processus métier
* Agglomération : Processus de direction

> #### La cartographie comporte 2 erreurs de placement de processus. Corrigez ces erreurs.

* Gestion des inscriptions : Processus métier
* Gestion des équipements : Processus support

### II -  L'architecture des PGI

> #### Identifiez le rôle des 3 couches d’un PGI. Quel lien y a-t-il entre elles ?

 1. Interface client : envoie les données au PGI
 2. PGI :  Traitement des données envoyées par l'interface client puis stockage dans le SGBD
 3. SGBD : Stockage et accès aux données à la demande du PGI

> #### D’après vous quel est l’intérêt d’une organisation en 3 couches ?

 * Couches connectées mais indépendantes (facilité à maintenir le système) ;
 * Possibilité d'utiliser des solutions déjà prêtes.

## ERP Open Source

### I – Généralités

> #### Quel est l’intérêt d’avoir un ERP en open source ?

Permet de faire interface avec des outils existants dans la structure, d'adapter l'outil aux besoins de la structure.
Il est constamment actualisé par la communauté de manière gratuite.

> #### En quoi cet ERP est-il adaptable ? Voir l’onglet App builder

Création de modules qui s'adaptent aux besoins de l'entreprise sans grandes connaissances informatiques.

> #### Quel prix, quel coût pour l’utilisation de cet ERP ?

Évolutif en fonction du nombre d'utilisateurs, des besoins, etc.

### II - La chaîne d’approvisionnement – Stocks et achats

> #### En quoi ces modules sont-ils des outils opérationnels, d’aide à la gestion et d’aide à la décision ?

 * Opérationnel : Inventaire, logistique, niveau du stock, édition de bons...
 * Gestion : Commandes automatisées, échéancier, estimation évolutive de la valeur du stock...
 * Décision : Analyse des besoins, propositions d'achats...

> #### En quoi cet ERP utilise-t-il les principes d’un extranet ?

Portail dédiés aux fournisseurs, mise en concurrence, gestion des appels d'offre...

### III – La gestion financière – Facturation et comptabilité

> #### Quels liens avec le CRM ?

Gestion des ventes (validation des devis, calculs), facturation, avoirs...

> #### En quoi la facturation facilite-t-elle le travail des vendeurs ?

Génération des factures, gestion du suivi des clients, des contacts, des remises, des paiements, ...

> #### Que signifie « écritures comptables » / à « écritures analytiques » ?



### IV – RH – Employés

> #### En quoi cet ERP utilise-t-elle la GED ?

Instruments de numérisation et d'archivage de documents papier (pièces d'identité, certificats médicaux, etc) utiles au module RH.

> #### En quoi ce module est utile : au recrutement / au quotidien de l’entreprise ?

> #### Quels liens avec les autres modules ?

### V – Industries

> #### En quoi cet ERP semble adapté (ou pas) tant aux entreprises de services, qu’aux activités industrielles ou à la distribution ?
