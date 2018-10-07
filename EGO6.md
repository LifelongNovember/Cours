---


---

<blockquote>
<p>Généré depuis <a href="https://stackedit.io/">StackEdit</a>. Si ce fichier est sur GitHub, vous êtes en train de lire un backup du document original, qui est accessible <a href="https://frama.link/aden-iutsd">ici</a> (avec de belles formules à la place des entrées Latex).</p>
<p>Une authentification est demandée.</p>
<blockquote>
<p>Compte lecture seule :<br>
Identifiant : <strong>reader</strong><br>
Mot de passe : <strong>reader</strong></p>
</blockquote>
</blockquote>
<h1 id="tp">TP</h1>
<h2 id="processus--erp">Processus &amp; ERP</h2>
<h3 id="i----les-processus">I -  Les processus</h3>
<blockquote>
<h4 id="retrouver-les-3-types-de-processus">Retrouver les 3 types de processus</h4>
</blockquote>
<ul>
<li>Processus métier</li>
<li>Processus support</li>
<li>Processus de direction</li>
</ul>
<blockquote>
<h4 id="de-quels-processus-sont-clients-les-adhérents-les-agents-des-médiathèques-et-lagglomération-">De quels processus sont clients les adhérents, les agents des médiathèques et l’agglomération ?</h4>
</blockquote>
<ul>
<li>Agent des médiathèques : Processus support</li>
<li>Adhérent : Processus métier</li>
<li>Agglomération : Processus de direction</li>
</ul>
<blockquote>
<h4 id="la-cartographie-comporte-2-erreurs-de-placement-de-processus.-corrigez-ces-erreurs.">La cartographie comporte 2 erreurs de placement de processus. Corrigez ces erreurs.</h4>
</blockquote>
<ul>
<li>Gestion des inscriptions : Processus métier</li>
<li>Gestion des équipements : Processus support</li>
</ul>
<h3 id="ii----larchitecture-des-pgi">II -  L’architecture des PGI</h3>
<blockquote>
<h4 id="identifiez-le-rôle-des-3-couches-d’un-pgi.-quel-lien-y-a-t-il-entre-elles-">Identifiez le rôle des 3 couches d’un PGI. Quel lien y a-t-il entre elles ?</h4>
</blockquote>
<ol>
<li>Interface client : envoie les données au PGI</li>
<li>PGI :  Traitement des données envoyées par l’interface client puis stockage dans le SGBD</li>
<li>SGBD : Stockage et accès aux données à la demande du PGI</li>
</ol>
<blockquote>
<h4 id="d’après-vous-quel-est-l’intérêt-d’une-organisation-en-3-couches-">D’après vous quel est l’intérêt d’une organisation en 3 couches ?</h4>
</blockquote>
<ul>
<li>Couches connectées mais indépendantes (facilité à maintenir le système) ;</li>
<li>Possibilité d’utiliser des solutions déjà prêtes.</li>
</ul>
<h2 id="erp-open-source">ERP Open Source</h2>
<h3 id="i-–-généralités">I – Généralités</h3>
<blockquote>
<h4 id="quel-est-l’intérêt-d’avoir-un-erp-en-open-source-">Quel est l’intérêt d’avoir un ERP en open source ?</h4>
</blockquote>
<p>Permet de faire interface avec des outils existants dans la structure, d’adapter l’outil aux besoins de la structure.<br>
Il est constamment actualisé par la communauté de manière gratuite.</p>
<blockquote>
<h4 id="en-quoi-cet-erp-est-il-adaptable--voir-l’onglet-app-builder">En quoi cet ERP est-il adaptable ? Voir l’onglet App builder</h4>
</blockquote>
<p>Création de modules qui s’adaptent aux besoins de l’entreprise sans grandes connaissances informatiques.</p>
<blockquote>
<h4 id="quel-prix-quel-coût-pour-l’utilisation-de-cet-erp-">Quel prix, quel coût pour l’utilisation de cet ERP ?</h4>
</blockquote>
<p>Évolutif en fonction du nombre d’utilisateurs, des besoins, etc.</p>
<h3 id="ii---la-chaîne-d’approvisionnement-–-stocks-et-achats">II - La chaîne d’approvisionnement – Stocks et achats</h3>
<blockquote>
<h4 id="en-quoi-ces-modules-sont-ils-des-outils-opérationnels-d’aide-à-la-gestion-et-d’aide-à-la-décision-">En quoi ces modules sont-ils des outils opérationnels, d’aide à la gestion et d’aide à la décision ?</h4>
</blockquote>
<ul>
<li>Opérationnel : Inventaire, logistique, niveau du stock, édition de bons…</li>
<li>Gestion : Commandes automatisées, échéancier, estimation évolutive de la valeur du stock…</li>
<li>Décision : Analyse des besoins, propositions d’achats…</li>
</ul>
<blockquote>
<h4 id="en-quoi-cet-erp-utilise-t-il-les-principes-d’un-extranet-">En quoi cet ERP utilise-t-il les principes d’un extranet ?</h4>
</blockquote>
<p>Portail dédiés aux fournisseurs, mise en concurrence, gestion des appels d’offre…</p>
<h3 id="iii-–-la-gestion-financière-–-facturation-et-comptabilité">III – La gestion financière – Facturation et comptabilité</h3>
<blockquote>
<h4 id="quels-liens-avec-le-crm-">Quels liens avec le CRM ?</h4>
</blockquote>
<p>Gestion des ventes (validation des devis, calculs), facturation, avoirs…</p>
<blockquote>
<h4 id="en-quoi-la-facturation-facilite-t-elle-le-travail-des-vendeurs-">En quoi la facturation facilite-t-elle le travail des vendeurs ?</h4>
</blockquote>
<p>Génération des factures, gestion du suivi des clients, des contacts, des remises, des paiements, …</p>
<blockquote>
<h4 id="que-signifie-«-écritures-comptables-»--à-«-écritures-analytiques-»-">Que signifie « écritures comptables » / à « écritures analytiques » ?</h4>
</blockquote>
<h3 id="iv-–-rh-–-employés">IV – RH – Employés</h3>
<blockquote>
<h4 id="en-quoi-cet-erp-utilise-t-elle-la-ged-">En quoi cet ERP utilise-t-elle la GED ?</h4>
</blockquote>
<p>Instruments de numérisation et d’archivage de documents papier (pièces d’identité, certificats médicaux, etc) utiles au module RH.</p>
<blockquote>
<h4 id="en-quoi-ce-module-est-utile--au-recrutement--au-quotidien-de-l’entreprise-">En quoi ce module est utile : au recrutement / au quotidien de l’entreprise ?</h4>
</blockquote>
<blockquote>
<h4 id="quels-liens-avec-les-autres-modules-">Quels liens avec les autres modules ?</h4>
</blockquote>
<h3 id="v-–-industries">V – Industries</h3>
<blockquote>
<h4 id="en-quoi-cet-erp-semble-adapté-ou-pas-tant-aux-entreprises-de-services-qu’aux-activités-industrielles-ou-à-la-distribution-">En quoi cet ERP semble adapté (ou pas) tant aux entreprises de services, qu’aux activités industrielles ou à la distribution ?</h4>
</blockquote>

