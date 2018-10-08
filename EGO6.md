> Généré depuis [StackEdit](https://stackedit.io/). Si ce fichier est sur GitHub, vous êtes en train de lire un backup du document original, qui est accessible [ici](https://frama.link/aden-iutsd) (avec de belles formules à la place des entrées Latex).
>
> Une authentification est demandée. 
> > Compte lecture seule :
> > Identifiant : **reader**
> > Mot de passe : **reader**

# Cours

> ## Vidéo : Quels sont les enjeux et les contraintes des DSI ?
>
> Livrer plus vite de la valeur au sein de l'entreprise à un coût réduit pour tenir la concurrence en s'efforçant de conserver ses meilleurs éléments.
>
> ⇒ Généralement en tant que fonction support (transparent aux yeux du client).
>
> ⇒ Nécessité pour un responsable d'avoir des compétences en GRH.
> 
> Proposer de nouveaux services tout en maintenant le SI (support+ innovation).
> ⇒ Nouveaux modes de fonctionnement.

## Interactions avec les autres services

La DSI est généralement une fonction support à part entière rattachée à la direction générale.

La DSI travaille avec l'utilisateur final et le produit qu'elle va créer va être le support de sa fonction métier. Elle est sollicitée par d'éventuels porteurs de l'idée d'une nouvelle application (direction comme utilisateur final). Les besoins sont apportés par les partenaires de la conception, dont le MOA (qui validera ou non l'application). Les responsables des services concernés vont faire figure de relais dans le cas des éventuels problèmes informatiques. Le responsable de l'usage stratégique de l'informatique établit dans quelle mesure des solutions informatiques peuvent être trouvées.

La DSI doit proposer une solution qui fait consensus entre les différents services qui ont des attentes parfois opposées. Elle doit savoir imposer ses solutions (et les changements qu'elles impliquent) aux usagers, ce qui nécessite un apprentissage, et ce bien que dans certains cas, les promesses de productivité / confort qu'elle fait ne sont pas toujours tenues. Elle doit pour cela employer un vocabulaire adapté.

La DSI a pour objectifs de diminuer les coûts, d'assouplir les processus et d'apporter une valeur ajoutée aux clients de ceux-ci.

## Missions de la DSI

La DSI établit et traduit les stratégies SI de la structure. Les décisions de la	DSI doivent être alignées avec celles de la DG. Pour cela :

 * La DSI doit avoir compris et intégré les objectifs généraux,
 * La DG doit avoir pris en compte les opportunités & contraintes des SI.

Pour établir la stratégie SI, il est impératif de connaître l'environnement et notamment :
 * la technologie qui sera utilisée,
 * ses coûts,
 * les risques liés à la stratégie choisie.

Les responsables SI définissent et suivent la mise en oeuvre des projets informatiques de l'entreprise.

Ils maîtrisent les risques :
 * financiers,
 * techniques / technologiques,
 * organisationnels,
 * liés aux délais.

Leur rôle est d'employer des moyens adéquats aux besoins des équipes. Pour cela, ils peuvent choisir d'internaliser ou d'externaliser les services.

Le chef de projet est en charge de l'animation des projets / des relations avec les équipes concernées. Il est en relation avec le MOA et doit avoir des compétences en termes de relations humaines. Il a également à charge une équipe et doit savoir gérer le personnel qui est sous sa responsabilité (tant en termes de relations humaines que de formation).

La DSI doit également pouvoir fournir des indicateurs de performance liés aux différents services (contrôle de gestion : quels coûts affectés à quel produit + mesure de la rentabilité). Ces indicateurs permettent de contrôler l'avancée des résultats et l'atteinte des objectifs stratégiques. Ils peuvent être :
 * financiers,
 * liés à la qualité,
 * liés à la gestion de projet (temps / coûts / standards qualité).

La DSI est une fonction multifonction. Elle doit acquérir des compétences métiers. Elle est souvent l'intermédiaire entre la DG et les autres services dans les applications métiers qu'elle développe :
 * CRM - commercial
 * SCM - logistique
 * ...

La direction informatique s'oriente de plus en plus vers des doubles profils (informatique/gestion, informatique/marketing...).

Les choix de la DSI se caractérisent par :
* informatique propriétaire (production interne) / sous-traitance partielle / l'externalisation complète,
 * un bon ratio qualité / budget dans ses prestataires,
 * le niveau d'accompagnement des projets externalisés.

Les cadres SI peuvent s'orienter vers :
 * des postes de direction (générale ou dans les autres domaines),
 * du consulting (accompagnement des autres structures vers des solutions informatiques),
 * la création ou la reprise de structures afin d'y apporter
	 * de nouvelles solutions,
	 * une expertise dans un domaine précis.

## Internalisation / Externalisation

Degrés d'externalisation (CF 29++)

### Infrastructure As A Service (IaaS)

### Platform As A Service (PaaS)

### Software As A Service (SaaS)

### Externalisation - avantages

Les activités à faible valeur ajoutée sont déléguées. On ne conserve en interne que le cœur de métier. On garde l'accès à des compétences rares. L'externalisation permet des réductions de coûts (optimisation du prestataire) côté de et une grande flexibilité et réactivité.

### Externalisation - limites & risques

 * Perte de contrôle de l'infrastructure, des logiciels et des données,
 * Réglementation spécifiques des données en fonction du pays dont dépend le prestataire.

⇒ Nécessite de pouvoir négocier, interrompre ou modifier le contrat conclu avec le prestataire.

## Métiers de l'informatique

> Vidéo : **qualités & compétences** | **variété des missions** | **inconvénients & contraintes** des métiers de l'informatique

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
