# L'intelligence artificielle (augmentée)

> **Vincent Perrin** - Watson AI Technical Leader, IBM Watson *@vperrin*

On préfère parler d'intelligence augmentée. Une machine n'est pas encore capable de traiter l'ensemble des tâches comme un humain pourrait le faire.

## Intelligence artificielle

> Ensemble des théories et des techniques développant des programmes informatiques complexes capables de simuler certains traits de l’intelligence humaine.

> /* the end of code */
> Sur les 50 / 80 dernières années, l'ère de la programmation s'est développée : des spécifications étaient décrites dans un CDC, puis implémentées par un service informatique.
> Si les spécifications changent, le programme doit changer aussi.
> Aujourd'hui, les solutions doivent s'adapter d'elles-mêmes. Le savoir-faire est partagé avec la solution.
> > Implique de nouveaux métiers, avec des paradigmes différents

## Historique

Depuis les années 50 : Artificial Intelligence (résolution de problèmes, échecs, jeux...)
Depuis les années 80 : Machine Learning
Depuis les années 2010 : Deep learning

1997 : Victoire de Deep Blues vs. Kasparov (échecs)
Interviewé, Kasparov a dit que le système apprenait son style de jeu au fil des parties (alors que l'algorithme fonctionnait par force brute).

2011 : Watson vs Jeopardy (deviner la question d'une réponse)
La machine a battu le gagnant du plus de parties et le gagnant du plus d'argent. Dans le jeu, le participant devait miser de l'argent sur sa réponse. La machine devait donc estimer sa réponse.
"La machine à voyager dans le temps qui est apparue le jour suivant de l'assassinant de JFK" ⇒ "Qu'est-ce que le TARDIS"

2017 : AlphaGo Zero vs itself (Go)
La machine s'est entraînée elle-même pendant 37 jours puis a battu le 3ème plus grand champion mondial.

> **Machine Learning** : type d'IA qui permet à des ordinateurs d'apprendre sans avoir été explicitement programmé $\in$ intelligence interficielle.
> La machine peut apprendre sans avoir été programmée à effectuer la tâche.
> Algorithmes SVM, Random Forest, K-Means... permettent de décrire le problème et comprendre la donnée

> **Deep Learning** : Capacité du système à découvrir et comprendre une donnée pour fournir un résultat.
> Il permet, entre-autres, d'essayer d'imiter un cerveau humain.
> > Similarité avec les réseaux de neurones et de synapses...
> > Vision, reconnaissance des images et des sons...
> 
> Chaque couche du réseau va être capable de détecter de l'information. Au fil des couches, l'information est décrite de plus en plus précisément.
> > Capacité de sous-titrer une image en fonction de ce qu'elle représente, de décrire pourquoi il l'interprète de cette façon et comment il l'a compris, de répondre à des questions au sujet de l'image.

## Approches d'apprentissage

* Apprentissage supervisé : travail sur la donnée (labellisation de la donnée) afin d'informer la solution d'intelligence artificielle.
⇒ Lié à une tâche
 * Apprentissage non-supervisé : travail à partir d'un lot de données brutes non-labellisées.
Vrai challenge pour les entreprises (pléthore de données mais peu de moyens de les traiter)
⇒ Lié aux données
 * Apprentissage par renforcement : essai/erreur, basé sur du feedback / des récompenses.
IA Fifa 2018 : lucarne parfaite au bout de 1000 essais
Challenges dans le but de gagner contre des équipes DOTA
⇒ Très puissante mais peu exploitée par manque de moyens pour monitorer les simulations.

## Cas d'usage les plus courants

 * Chatbot (questions/réponses) / Agent conversationnel (Chatbot + dialogue) ⇒ Support client d'une entreprise / à l'accueil d'un hôtel...
 * Assistance visuelle : détection de problèmes visibles sur un système permettant de proposer une marche à suivre pour réparer l'appareil à partir d'une image de l'objet.
 * Prédiction des pannes dans des datacenters à partir de capteurs sonores IoT / Détection des appareils les plus bruyants sur des chantiers en milieu urbain

L'IA imprègne tous les secteurs d'activité. (Crédit Mutuel : "100% des métiers de la vente seront en lien avec l'IA")
⇒ Analyse & réponse à des mails en détectant l'urgence et le problème.
⇒ Assistance (et non remplacement) du conseiller : suggestions en temps réel à des conseillers téléphoniques en écoutant l'appel. À 90%, la réponse est pertinente pour l'utilisateur.
⇒ Médecine : détection de cas cancéreux à partir de photos (85% de pertinence pour l'IA vs 75% pour le praticien) / compréhension d'IRM.
⇒ Éducation : plateforme d'apprentissage en partenariat avec le CNED afin d'adapter les cursus aux étudiants.
⇒ Agriculture : détection des plantations avec données GPS, taux d'humidité, localisation & dispersion des maladies...
⇒ Assistance sur des chantiers (pour un couvreur, calcul de la surface à remplacer), calcul du coût de réparation sur une voiture à partir d'une photo...

Ère d'internet : besoin d'un programme ⇒ fournir un schéma, un prototype
Ère de l'IA : besoin de réponses ⇒ fournir un bon jeu de données afin de créer une IA fiable

## Demain

IBM entraîne ses machines à débattre avec un humain.
> Vidéo - IBM Project Debater vs champion israélien des débats sur le sujet "Doit-on arrêter la surveillance de masse ?"

IA : Algorithme + Données + Puissance de calcul

La donnée existe en profusion, la puissance de calcul arrive à sa limite (le transfert de données mémoire au processeur est limité dans le temps).
⇒ Ordinateur quantique : puissance de calcul exponentielle

> AIs are only as good as the **data** we train them with.
⇒ Les IAs commencent à introduire des biais (sexime, racisme) dans leur fonctionnement.

> "L'intelligence artificielle est à notre cerveau, ce que le moteur à vapeur a été pour nos muscles" - Hannes Gasser

Il est d'ores et déjà possible de jouer avec certains services d'IA : http://bluemix.net

IBM recrute : stages@fr.ibm.com

# Table ronde / Débat

> **Vincent Perrin** - Watson AI Technical Leader, IBM Watson *@vperrin*
> **Armelle Brun** - Enseignante chercheuse sur l'IA, LORIA Nancy
> **José Levices** - Dirigeant société App Mobile, Sainte-Marguerite

> ## Peut-on se perfectionner au moyen de l'IA ?
> > Chaque action d'un service informatique sur Internet est stockée. Dans l'éducation, on travaille énormément sur des services en ligne. Ces informations sont collectées par l'IA pour comprendre l'étudiant (personnalité, forces/faiblesses) et émettre des suggestions afin qu'il puisse s'améliorer, en préservant sa vie privée.
> > Les IA ne remplacent pas les enseignants mais les assistent. 
> > Il existe beaucoup de défis liés à l'enseignement dans les concepts d'IA

> ## Quand doit-on attendre ces arrivées ? À quels niveaux ?
> > Elles sont déjà là, elles existent à tous niveaux, en formations classiques ou professionnelles. Cela implique d'équiper les établissements de matériel informatique.

> ## L'IA ne risque-t-elle pas de déshumaniser les rapports entre les personnes ? Quelle société cela va-t-il créer ?
> > En aidant les processus d'interaction, on peut rendre la communication plus bénéfique. Le progrès peut toujours être récupéré, mais le but ici est de faciliter le travail.
> > Des organismes sont en train de réfléchir à une éthique de l'IA. Il est nécessaire d'établir des principes éthiques afin que l'IA ne puisse pas devenir préjudiciable. L'IA peut être extrêmement spécialisée, mais n'a que peu de compétences transversales.
> > Il est nécessaire d'établir un taux de confiance qui doit être mis en lien avec la tâche à accomplir.
 
> ## À partir de combien de cas l'IA devient-elle fiable ?
> > Un enfant : ~ 3 photos de dinosaure nécessaires, une IA : plusieurs milliers de photos.
> > Les grandes sociétés du numérique ont beaucoup de données mais ne savent pas les interpréter. Il faut donc que l'IA apprenne d'elle-même en continu. Selon ce que l'on a à faire, le jeu de données doit être plus ou moins important. Les applications les plus intéressantes résident dans l'apprentissage assisté.

> ## Intelligence, apprentissage, neurones : dans quelle mesure les solutions d'apprentissage sont-elles bio-inspirées ?
> > Conception d'avions : on a essayé d'imiter des oiseaux, ça n'était pas une bonne idée.
> > Assimilation aux réseaux de neurones : on s'inspire du fonctionnement du cerveau humain mais on en reste loin, l'humain consomme peu d'énergie alors que la machine est très gourmande. La médecine n'est pas encore capable aujourd'hui d'expliquer comment fonctionnent les réseaux de neurones (notamment comment le renouvellement constant des neurones peut maintenir le fonctionnement).
> > Une IA est davantage similaire à un ensemble d'algorithmes dédiés à la résolution d'une tâche.

> ## L'IA nécessite du matériel. Comment peut-elle être mise en place dans tous les services ?
> > Différence entre une machine basique (frigo...) et un ordinateur. Ce dernier fonctionne en couches. Les installations demandent énormément de suivi (gestion électrique, refroidissement...). Ces complications impliquent la nécessite de trouver des solutions plus simples et plus fonctionnelles.

> ## En apprenant d'un être humain, n'est-on pas amené à trop le simplifier ?
> > C'est effectivement une problématique qui est surveillée. On cherche à satisfaire la personne tout en la considérant toujours comme complexe et unique et donc en continuant à l'explorer. Un élément intéressant est d'expliquer au client pourquoi le produit est avantageux pour lui.

> ## Aide à la décision : ne doit-ont pas avoir peur d'être manipulé par l'IA à son insu ?
> > Le RGPD impose au système d'être transparent, ils est nécessaire d'indiquer les processus qui mènent à l'assistance fournie. Dans une démarche "humaine", les biais existent également. Ici, ils sont plus explicites. Une démarche critique reste nécessaire quelle que soit la situation.
> >
> ### Le RGPD ne constitue pas vraiment une contrainte menaçante pour les grandes sociétés du numérique.
> > Le RGPD peut aussi se manifester comme un challenge : qu'est-ce que je collecte et pourquoi ?

> ## Quelques chiffres sur l'IA ? Une organisation ne risque-t-elle pas de phagocyter les autres ?
> > Les GAFA utilisent l'IA pour eux-mêmes alors que les autres organisations sont fournisseurs de services pour que leurs clients mettent en place de l'IA. Ces acteurs feront face à de la concentration (de par les moyens liés au matériel), mais ils persisteront et continuent d'émerger du fait de leur spécialisation.

> ## Quel conseil donner à de jeunes lycéens qui s'apprêtent à faire des études ?
> > Être curieux, avoir le désir d'apprendre à faire quelque-chose, mais également de comprendre les différences entre plusieurs technologies, pourquoi certaines prennent le pas sur d'autres. C'est ce qui permettra d'avoir un profil intéressant.
> > Une hygiène de vie à avoir : passer 1h dans la journée à apprendre quelque-chose de nouveau. Les technologies changent, il faut savoir s'adapter.
> > Cet apprentissage et cette curiosité ne doivent pas se limiter à l'informatique.
> > Ne pas avoir peur d'oublier ce que l'on croit.
