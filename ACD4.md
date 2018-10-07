---


---

<blockquote>
<p>Généré depuis <a href="https://stackedit.io/">StackEdit</a>. Si ce fichier est un gist, vous êtes en train de lire un backup du document original, qui est accessible <a href="https://frama.link/aden-iutsd">ici</a> (avec de belles formules à la place des entrées Latex).</p>
<p>Une authentification est demandée.</p>
<blockquote>
<p>Compte lecture seule :<br>
Identifiant : <strong>reader</strong><br>
Mot de passe : <strong>reader</strong></p>
</blockquote>
</blockquote>
<h1 id="cours">Cours</h1>
<h2 id="patrons-de-conception">Patrons de conception</h2>
<p>Ref : Design Patterns (Tête la première)</p>
<h3 id="patrons-de-construction">Patrons de construction</h3>
<p>Création et configuration d’objets</p>
<h4 id="singleton">Singleton</h4>
<p>Utilisé lors de l’utilisation de classes instanciées de manière unique.</p>
<pre class=" language-java"><code class="prism  language-java"><span class="token keyword">private</span> <span class="token keyword">class</span> <span class="token class-name">Singleton</span> <span class="token punctuation">{</span>

	<span class="token keyword">private</span> <span class="token keyword">static</span> Singleton instance<span class="token punctuation">;</span>
	<span class="token keyword">private</span> <span class="token function">Singleton</span><span class="token punctuation">(</span><span class="token punctuation">)</span>
	<span class="token punctuation">{</span>
		<span class="token comment">///</span>
	<span class="token punctuation">}</span>
	<span class="token keyword">public</span> <span class="token keyword">static</span> Singleton <span class="token function">getInstance</span><span class="token punctuation">(</span><span class="token punctuation">)</span> <span class="token punctuation">{</span>
		<span class="token keyword">if</span><span class="token punctuation">(</span>instance <span class="token operator">==</span> null<span class="token punctuation">)</span>
			instance <span class="token operator">=</span> <span class="token keyword">new</span> <span class="token class-name">Singleton</span><span class="token punctuation">(</span><span class="token punctuation">)</span><span class="token punctuation">;</span>
		<span class="token keyword">return</span> instance<span class="token punctuation">;</span>
	<span class="token punctuation">}</span>
<span class="token punctuation">}</span>
</code></pre>
<p>Compliqué à mettre en place dans le cas du multi-threading</p>
<pre class=" language-java"><code class="prism  language-java"><span class="token keyword">public</span> <span class="token keyword">static</span> <span class="token keyword">synchronized</span> Singleton <span class="token function">getInstance</span><span class="token punctuation">(</span><span class="token punctuation">)</span>
</code></pre>
<p>Coûteux lors de l’execution</p>
<pre class=" language-java"><code class="prism  language-java"><span class="token keyword">private</span> <span class="token keyword">class</span> <span class="token class-name">Singleton</span> <span class="token punctuation">{</span>

	<span class="token keyword">private</span> <span class="token keyword">static</span> Singleton instance <span class="token operator">=</span> <span class="token keyword">new</span> <span class="token class-name">Singleton</span><span class="token punctuation">(</span><span class="token punctuation">)</span><span class="token punctuation">;</span>
	<span class="token keyword">private</span> <span class="token function">Singleton</span><span class="token punctuation">(</span><span class="token punctuation">)</span>
	<span class="token punctuation">{</span>
		<span class="token comment">///</span>
	<span class="token punctuation">}</span>
	<span class="token keyword">public</span> <span class="token keyword">static</span> Singleton <span class="token function">getInstance</span><span class="token punctuation">(</span><span class="token punctuation">)</span> <span class="token punctuation">{</span>
		<span class="token keyword">return</span> instance<span class="token punctuation">;</span>
	<span class="token punctuation">}</span>
<span class="token punctuation">}</span>
</code></pre>
<pre class=" language-java"><code class="prism  language-java"><span class="token keyword">private</span> <span class="token keyword">class</span> <span class="token class-name">Singleton</span> <span class="token punctuation">{</span>

	<span class="token keyword">private</span> <span class="token keyword">volatile</span> <span class="token keyword">static</span> Singleton instance<span class="token punctuation">;</span>
	<span class="token keyword">private</span> <span class="token function">Singleton</span><span class="token punctuation">(</span><span class="token punctuation">)</span>
	<span class="token punctuation">{</span>
		<span class="token comment">///</span>
	<span class="token punctuation">}</span>
	<span class="token keyword">public</span> <span class="token keyword">static</span> <span class="token keyword">synchronized</span> Singleton <span class="token function">getInstance</span><span class="token punctuation">(</span><span class="token punctuation">)</span> <span class="token punctuation">{</span>
		<span class="token keyword">if</span><span class="token punctuation">(</span>instance <span class="token operator">==</span> null<span class="token punctuation">)</span> <span class="token punctuation">{</span>
			<span class="token keyword">synchronized</span> <span class="token punctuation">(</span>Singleton<span class="token punctuation">.</span><span class="token keyword">class</span><span class="token punctuation">)</span> <span class="token punctuation">{</span>
				<span class="token keyword">if</span><span class="token punctuation">(</span>instance <span class="token operator">==</span> null<span class="token punctuation">)</span>
				instance <span class="token operator">=</span> <span class="token keyword">new</span> <span class="token class-name">Singleton</span><span class="token punctuation">(</span><span class="token punctuation">)</span><span class="token punctuation">;</span>
			<span class="token punctuation">}</span>
		<span class="token punctuation">}</span>
		<span class="token keyword">return</span> instance<span class="token punctuation">;</span>
	<span class="token punctuation">}</span>
<span class="token punctuation">}</span>
</code></pre>
<h4 id="factory-method--abstract-factory">Factory Method / Abstract Factory</h4>
<p>En fonction du type d’objet dont on a besoin, on peut être amené à multiplier les appels à instancier des classes concrètes.</p>
<p>Une classe de fabrique permet de factoriser les instanciations et de créer les objets en fonction du type fourni  (fabrique paramétrée).</p>
<p>Les classes de fabrique se succèdent mais il est possible de faire les opérations dans une classe abstraite (avec une méthode abstraite) qu’implémentent toutes les classes de fabrique.</p>
<p><img src="https://www.plantuml.com/plantuml/svg/fPEn3e8m48Ptde8mwS10PqBWI5nz0PU2PrA3DRR7fBwxLMXYgP8IklNk_x_s_hIb9gweltHHr7PSwpZ9So49rOctM1G7kUED4hSUgqQJue8mYUzHR5Qj4DM-EIDLc-sa0gRoj4HBgA-oLKYOhGMmfO2w4oZftuG3OHolIgniA6VkbWL1m8M02m43yJD9qqSH4BxdPC7E8GKZNwkU1XOg1V_ssSTbevxfWjzbNrusrpM1ZoVypcewpuXS88OGCbXn2FdzX4gKH_CpNm00" alt=""></p>
<p>⇒ L’utilisateur n’est plus responsable de la création des objets.<br>
⇒ À la place, il manipule des familles d’objets par le biais de la fabrique abstraite.</p>
<h3 id="patrons-de-structuration">Patrons de structuration</h3>
<h4 id="adaptateur">Adaptateur</h4>
<p>L’adaptateur permet à un système et à une interface incompatibles de communiquer.</p>
<pre class=" language-java"><code class="prism  language-java">Reader isr <span class="token operator">=</span> <span class="token keyword">new</span> <span class="token class-name">InputStreamReader</span><span class="token punctuation">(</span><span class="token keyword">new</span> <span class="token class-name">FileInputStream</span><span class="token punctuation">(</span>file<span class="token punctuation">)</span><span class="token punctuation">)</span><span class="token punctuation">;</span>
<span class="token keyword">while</span><span class="token punctuation">(</span><span class="token punctuation">(</span><span class="token keyword">int</span> c <span class="token operator">=</span> isr<span class="token punctuation">.</span><span class="token function">read</span><span class="token punctuation">(</span><span class="token punctuation">)</span> <span class="token operator">!=</span> <span class="token operator">-</span><span class="token number">1</span><span class="token punctuation">)</span>
	System<span class="token punctuation">.</span>out<span class="token punctuation">.</span><span class="token function">println</span><span class="token punctuation">(</span>c<span class="token punctuation">)</span><span class="token punctuation">;</span>
isr<span class="token punctuation">.</span><span class="token function">close</span><span class="token punctuation">(</span><span class="token punctuation">)</span><span class="token punctuation">;</span>
</code></pre>
<h4 id="façade">Façade</h4>
<p>La façade permet l’utilisation d’un système complexe à partir d’une interface unique.</p>
<h4 id="décorateur">Décorateur</h4>
<p>Le décorateur permet la superposition de composants de même type. Les interfaces permettent de spécifier les composants (leur ajouter de nouvelles fonctionnalités…) pour construire l’objet final.</p>
<p><img src="https://www.plantuml.com/plantuml/svg/dP913i8W44NtSmhIbIvw0q9QwZ7SZ9J4HG43qvLwTud1QW2jwImdUIz_VgOBX9vcCm6e2KDW3UTu2kHHaH17EpXpSG4jDUmAB0v7mOocinjrlzldAnbNzvTgOGTdbTUK31bT8xCG1wsSHzAptv3Y3QSOVN8iyPZwDrVXabjSHIzjUnFVYuSVRQoGbTjhn8UnHEGgyZmHeDDsZ8_q0000" alt=""></p>
<h4 id="composite">Composite</h4>
<p>Une structure composite permet d’appliquer les mêmes opérations aux composés et aux composants.<br>
Une structure composite permet de représenter des hiérarchies composant / composé.</p>
<h1 id="td-1">TD 1</h1>
<p><strong>Révisions - Diagrammes de classe, Diagrammes de séquence</strong></p>
<h2 id="i---premiers-exercices-plus-ou-moins-simples">I - Premiers exercices (plus ou moins) simples</h2>
<blockquote>
<h3 id="une-classe-contient-des-élèves.">1. Une classe contient des élèves.</h3>
<p><img src="https://www.plantuml.com/plantuml/svg/SoWkIImgAStDuU9ApaaiBbPm1f6fKCxXpfp3AyfIkRWWeWfAXaeAkhfs2afQIZ0v1Ik5vFoyaipKl18kBeVKl1IWMG00" alt=""></p>
</blockquote>
<blockquote>
<h3 id="les-modems-et-les-claviers-sont-des-périphériques-dentrée.">2. Les modems et les claviers sont des périphériques d’entrée.</h3>
<p><img src="https://www.plantuml.com/plantuml/svg/SoWkIImgAStDuU9ApaaiBbO8EBooABCW0qGMbgP21NtpKr9peMpddCIopDGYBYwme8AkReqTkYQe4gnoN0wfUIb0-m00" alt=""></p>
</blockquote>
<blockquote>
<h3 id="une-bibliothèque-possède-des-exemplaires--ces-exemplaires-peuvent-être-soit-des-livres-soit-des-cds.">3. Une bibliothèque possède des exemplaires ; ces exemplaires peuvent être soit des livres soit des cds.</h3>
<p><img src="https://www.plantuml.com/plantuml/svg/SoWkIImgAStDuU9ApaaiBbPmoapAoSmloJYyeh0q5IhcMf6QMv2Jc5a44_39B8EpdLsuk50qAIWPAYdewjefA1aewEafQ2aXwLUmKYZ8Bou-l28bbSlP1QYgnWxPTB2v6A9S3gbvAK0d0W00" alt=""></p>
</blockquote>
<blockquote>
<h3 id="un-répertoire-contient-plusieurs-éléments-chacun-de-ces-éléments-peut-être-un-fichier-ou-un-autre-répertoire.">4. Un répertoire contient plusieurs éléments, chacun de ces éléments peut être un fichier ou un autre répertoire.</h3>
<p><img src="https://www.plantuml.com/plantuml/svg/SoWkIImgAStDuU9ApaaiBbO8Ehoo8BMe93-pA1KgShWpv_3AtDIy4YZVBJCv8pErY8iBIQc2ag6IWgwk7P1MqDDJq5A2gLAmKaZEpol916b7Lg-hMsE7P39CDPembqDgNWhGSG00" alt=""></p>
</blockquote>
<h2 id="ii---classes-telecommande-et-lampe">II - Classes <code>Telecommande</code> et <code>Lampe</code></h2>
<p>Classes :</p>
<ul>
<li><code>Lampe</code></li>
<li><code>Telecommande</code></li>
</ul>
<p><code>Lampe</code> :</p>
<ul>
<li>Attribut <code>nom</code> permettant d’identifier la lampe</li>
<li>Attribut <code>allume</code> de type <code>boolean</code> valant <code>true</code> si la lampe est allumée</li>
<li>Constructeur d’une lampe éteinte à partir de son nom</li>
</ul>
<p><code>Telecommande</code> :</p>
<ul>
<li>Attribut <code>lampes</code> de type liste de <code>Lampe</code></li>
<li>Constructeur vide</li>
<li>Méthode <code>ajouterLampe</code> ajoutant une <code>Lampe</code>passée en paramètre dans la liste des lampes contrôlées</li>
<li>Méthode <code>activerLampe</code> activant la <code>Lampe</code> dont l’indice est passé en paramètre</li>
<li>Méthode <code>desactiverLampe</code> désactivant la <code>Lampe</code> dont l’indice est passé en paramètre</li>
<li>Méthode <code>activerTout</code> activant toutes les lampes contrôlées par la <code>Telecommande</code></li>
</ul>
<p><img src="https://www.plantuml.com/plantuml/svg/VL4z3y8W5Dpv5IzCrQIDhXrCVu2RtOm3bXU3uSF0eulnlrifH5na0UxkvUvW22GyHQCPcxG80Ox2F12U39Pr8g_i3QmpwNfrJgEm8BIE1g47yX4JauQQhtoJqDafcSM-gI0aL5Pwp5WU8xSU5lHLmeoeSNB622jBfcHrle3-x251jQhs4NSN2VqQRksbQteYDHTQMG9LaHB3NpwJu-BmhyPF0Rw3heCzXxOz0D_o_DOz50LZ0rgvVCOR" alt=""></p>
<h2 id="iii---classe-reader">III - Classe <code>Reader</code></h2>
<p>Classes :</p>
<ul>
<li><code>Reader</code>: abstraite</li>
<li><code>FileReader</code> :<code>Reader</code></li>
<li><code>BufferedReader</code> : <code>Reader</code> contenant un autre <code>Reader</code></li>
</ul>
<p><code>Reader</code> :</p>
<ul>
<li>Méthode <code>read</code></li>
</ul>
<p><code>BufferedReader</code> :</p>
<pre class=" language-java"><code class="prism  language-java">Reader f <span class="token operator">=</span> <span class="token keyword">new</span> <span class="token class-name">FileReader</span><span class="token punctuation">(</span>name<span class="token punctuation">)</span><span class="token punctuation">;</span>
BufferedReader bf <span class="token operator">=</span> <span class="token keyword">new</span> <span class="token class-name">BufferedReader</span><span class="token punctuation">(</span>f<span class="token punctuation">)</span><span class="token punctuation">;</span>
</code></pre>
<p><img src="https://www.plantuml.com/plantuml/svg/SoWkIImgAStDuU9ApaaiBbPGih59J2ekAKfCBh6pYyaBIarCIIrIKgZcKW02cqGxXRByp1I58g2mXYPNBKoNMsPEAaGfL2LMLKwbQMcfHQafA2fH1JKWb2OsGv0iqTMjiSFXL2uqMqXIYbCbbqDgNWemc000" alt=""></p>
<h2 id="iv---bibliothèque---ajout-des-méthodes">IV - Bibliothèque - ajout des méthodes</h2>
<p>Classe <code>Bibliotheque</code> (cf I.3) : Implémenter la description de l’ensemble des éléments de la bibliothèque</p>
<p><img src="https://www.plantuml.com/plantuml/svg/XP0z3i8m34RtdCBA14WPM54LLVniRAmiQR2AfJGfYOkGWFjm3ov6fLA93hIUFBpFVdQUs4HkAYU4TIObM5FXAF3v_Req27S1RHquaY-1GzVCvkBPupBBJ94u6ijQ7_tkXbNj34MKtsncT9ylaRUORAIQAVZVAPljSDD_Sa_NYDFmy0gvbA2K1hcGOy8hiC4peMVH2Ydrq2Eqw4ocA96ZFxNl_G00" alt=""></p>
<pre class=" language-java"><code class="prism  language-java"><span class="token keyword">class</span> <span class="token class-name">Biblioth</span>èque <span class="token punctuation">{</span>
	Exemplaire<span class="token punctuation">[</span><span class="token punctuation">]</span> exemplaires<span class="token punctuation">;</span>
	String <span class="token function">toString</span><span class="token punctuation">(</span><span class="token punctuation">)</span> <span class="token punctuation">{</span>
		String r<span class="token punctuation">;</span>
		<span class="token keyword">for</span><span class="token punctuation">(</span><span class="token keyword">int</span> i <span class="token operator">=</span> <span class="token number">0</span><span class="token punctuation">;</span> i <span class="token operator">&lt;</span> exemplaires<span class="token punctuation">[</span><span class="token punctuation">]</span><span class="token punctuation">;</span> i<span class="token operator">++</span><span class="token punctuation">)</span> <span class="token punctuation">{</span>
			r <span class="token operator">+=</span> exemplaires<span class="token punctuation">[</span>i<span class="token punctuation">]</span><span class="token punctuation">.</span><span class="token function">getDescription</span><span class="token punctuation">(</span><span class="token punctuation">)</span><span class="token punctuation">;</span>
		<span class="token punctuation">}</span>
		<span class="token keyword">return</span> r<span class="token punctuation">;</span>
	<span class="token punctuation">}</span>
<span class="token punctuation">}</span>
</code></pre>
<h2 id="v---emploi-du-temps-i">V - Emploi du temps I</h2>
<ul>
<li>Un <code>EmploiDuTemps</code> contient des <code>Creneau</code></li>
<li>Chaque <code>Creneau</code>est associé à une <code>Matiere</code>, un <code>GroupeEtudiant</code> et une <code>Salle</code>. Il est caractérisé par une <code>Date</code></li>
<li>L’université est constituée de <code>Personne</code> pouvant être <code>Etudiant</code>ou <code>Enseignant</code></li>
<li>Les <code>Etudiant</code> appartiennent à un <code>GroupeEtudiant</code></li>
<li>Un <code>Enseignant</code> participe à une ou plusieurs <code>Matiere</code></li>
</ul>
<p><img src="https://www.plantuml.com/plantuml/svg/RP5D2i8m48NtESNGfP2YMnUbOCML8EW5GZj889sK_ApKknjicgHg5adcvMFU6z9Q9uppesAiLy9QE8wJqhBpDnmd6xM3GKBXuS4Wh4uuX25ix1NVhq8fZFUpS1BDKfsCzXCUdH-a8BTOV9LaKTuf2nSqLXCXOwimKEqguBo1QWjr3PigvTf3hodOXWwBbDXmVkBDK8yczFq7nTmbjWvVqD4-lHJ-UPXVFblWJ669S_viykYfzrfcBT8GVkiD" alt=""></p>
<h2 id="vi---diagrammes-de-séquence---exercices-simples">VI - Diagrammes de séquence - Exercices simples</h2>
<blockquote>
<h3 id="un-objet-r-de-la-classe-unrectangle-demande-à-son-coin-de-se-translater-selon-la-direction-1010.">1. Un objet <code>r</code> de la classe <code>UnRectangle</code> demande à son coin de se translater selon la direction (10,10).</h3>
<p><img src="https://www.plantuml.com/plantuml/svg/SoWkIImgAStDuU9IAbAmKWZD2qfDBadCIyz9LLBGjLDGIixFp0EB1m0P9Kf0Pd5gI55YNd5EOabgaOQXWOwXWIPGCxewNP1cT1EvkBWSKlDIWDO10000" alt=""></p>
</blockquote>
<blockquote>
<h3 id="le-programme-principal-demande-à-la-classe-maths-de-calculerpiint-n-à-5-décimales-près.">2. Le programme principal demande à la classe <code>Maths</code> de <code>calculerPi(int n)</code> à 5 décimales près.</h3>
<p><img src="https://www.plantuml.com/plantuml/svg/SoWkIImgAStDuU9I2YZAp4lEB4ZCILLIqBLJKCfDBCaeLh1Iy0NHIa16Sc9EScbEQb50feQf9b03cWAG7cGph1ICzGnD34qjkRYu75BpKe2s0000" alt=""></p>
</blockquote>
<h2 id="vii---calcul-du-poids-dune-voiture">VII - Calcul du poids d’une voiture</h2>
<p>Le poids d’une voiture est égal à la somme du poids de son moteur et du poids de sa carrosserie.</p>
<p><img src="https://www.plantuml.com/plantuml/svg/SoWkIImgAStDuU9ApaaiBbO8oyyiAIrALQZcKW02xPJyqgISL8Nqr9A0_CoKOgYiXYPNBLIzRtv9QcaH3kKGIIJLpeb5-SN5gKMPk2m0AW0hvuAvGybGIK7N3an1hR9IqCq5ix2fGR80g2uPnEFYSaZDIm5w4G00" alt=""></p>
<p><img src="https://www.plantuml.com/plantuml/svg/SoWkIImgAStDuUBAJSpCKz2rKr0gKx1I2ClFB2ajIbK2CjDJImBoCrEAeK8QcboeAa1QSe42llabgQL5o3eW8Y0DoFAwMEmeCCHYQ39Gm3cnAB-uEBKe4yKfG56GgUWAi9fiX6uoK17Ogo1R5RH12hWSKlDIW6400000" alt=""></p>
<h2 id="vii---retrait-dargent">VII - Retrait d’argent</h2>
<p><img src="https://www.plantuml.com/plantuml/svg/RP0x3i8m38RtdCBgnACTM3EW2de2E47QkX0fTI1n1eIuEsdfGwtmv3Y_Ftr9xbav3gqHeZBAUoYqPwVBm1WSl0N4sWDwhrxeBiXEQTu4ZqvUOunkARIMM15BJPn2PMlikgqihJMeI7n6y4dHC-0PAJ8CJcWL-1vdkj7ebk2PTRRjWt56_Su38fiC2XjAWwDoqs35OPOcs_vpNfWk7f_i4iYEa1oIjRk4hEmdOdNHPRkLk3auncZLTrx4of7g-DTV" alt=""></p>
<p><code>Distributeur</code>:</p>
<ul>
<li>Relié à une <code>BanqueCentrale</code></li>
<li><code>essayerRetrait</code> retourne <code>true</code> si le retrait a pu être effectué</li>
</ul>
<p><code>BanqueCentrale</code> :</p>
<ul>
<li>Peut <code>authentifier</code> un utilisateur (retourne le <code>Compte</code> qui lui est associé si son code est correct, <code>null</code> sinon)</li>
</ul>
<p><code>Compte</code> :</p>
<ul>
<li>Permet d’<code>effectuerRetrait</code> au montant demandé sur le compte de l’utilisateur</li>
</ul>
<blockquote>
<h3 id="retrait-de-100€-avec-un-code-correct">Retrait de 100€ avec un code correct</h3>
<p><img src="https://www.plantuml.com/plantuml/svg/TP312i8m38RlVOhIauB2P0V1Wmpd4uWlq6qf5jPkfid1jpURWXxQ7Wef-RylJPF88d4ObGhMHxq_QpFeaxxwHEWx9c0qKaDAzWLu0qBhQMFk4qrcfmzL9LTT7xSg4rjWNI_F5nkV32r4IO-my2pJGqhlFE2FzW5b8wN1-f9uWRHJc6drWNFG4sT_8Ch_vfA9aA4WMrVtxP3JG1nafMy0" alt=""></p>
</blockquote>
<blockquote>
<h3 id="retrait-avec-un-code-incorrect">Retrait avec un code incorrect</h3>
<p><img src="https://www.plantuml.com/plantuml/svg/TO_12i9034Jl-nLXJmeLrciFKjGl47yWjIa6jblC9WV_tbJ4Kpkt2SoRJ5SLHMtA8Kp81GudY0EqSEMgmhqfcKJtL2k-IMwaWgoxU9zrZWqSKseWkVPX9RR0-eUVprXUHXSgdiwqyD3qwPP79ldJVg3LoDPZnNBUwFuEQc74N2cuEYg3B_q0" alt=""></p>
</blockquote>
<h1 id="td-3">TD 3</h1>
<h2 id="i---registerwindows">I - RegisterWindows</h2>
<p><img src="https://www.plantuml.com/plantuml/svg/SoWkIImgAStDuU9ApaaiBbO8IatFB2v9BGhFp4l9BozMgEPI009qqSmyeBwyv5ImP719KMPUka9UVYusjHeGQKsivgIdbdX2ZTBGvAhbSaZDIm4w1W00" alt=""></p>
<pre class=" language-java"><code class="prism  language-java"><span class="token keyword">class</span> <span class="token class-name">RegisterWindows</span> <span class="token punctuation">{</span>
<span class="token keyword">public</span> <span class="token keyword">class</span> <span class="token class-name">RegisterWindows</span> <span class="token punctuation">{</span>
	<span class="token keyword">private</span> <span class="token keyword">static</span> RegisterWindows instance<span class="token punctuation">;</span>
	<span class="token keyword">private</span> <span class="token keyword">static</span> String nom<span class="token punctuation">;</span>
	<span class="token keyword">private</span> <span class="token function">RegisterWindows</span><span class="token punctuation">(</span>String noms<span class="token punctuation">)</span> <span class="token punctuation">{</span>
		RegisterWindowthis<span class="token punctuation">.</span>nom <span class="token operator">=</span> noms<span class="token punctuation">;</span>
	<span class="token punctuation">}</span>
	<span class="token keyword">static</span> <span class="token keyword">public</span> RegisterWindows <span class="token function">getInstance</span><span class="token punctuation">(</span>String nom<span class="token punctuation">)</span> <span class="token punctuation">{</span>
		<span class="token keyword">if</span><span class="token punctuation">(</span>instance <span class="token operator">==</span> null<span class="token punctuation">)</span>
			instance <span class="token operator">=</span> <span class="token keyword">new</span> <span class="token class-name">RegisterWindows</span><span class="token punctuation">(</span>nom<span class="token punctuation">)</span><span class="token punctuation">;</span>
		<span class="token keyword">return</span> instance<span class="token punctuation">;</span>
	<span class="token punctuation">}</span>
	<span class="token keyword">public</span> String <span class="token function">getNom</span><span class="token punctuation">(</span><span class="token punctuation">)</span> <span class="token punctuation">{</span>
		<span class="token keyword">return</span> nom<span class="token punctuation">;</span>
	<span class="token punctuation">}</span>
<span class="token punctuation">}</span>
</code></pre>
<h2 id="ii---connexions">II - Connexions</h2>
<p><img src="https://www.plantuml.com/plantuml/svg/dPB12y8W5CRlxwyGJnNjq7KC6HLq2I9sxM9Emd0QwY2e_lTicskCZKMUzF5zxti_DRME6bSM4e19QYt2IKBFrXdA724dbUtMMumUWFnAA47CS6usMYb-5rhDIYUaiCiYlytZjbg9wLMNRbhwQc8_EGSVAdaJzbDGrvqTz_zOUxoj843NxZXpHgXBLV6DmZ4qQLr-Y7wffWBe44RHamnUD0IGSSNW--0LHf4tBF0uJyp2ra9tti6ihmrw85FobAlSVwSt" alt=""></p>
<h1 id="td-4">TD 4</h1>
<h2 id="i---pizzas">I - Pizzas</h2>
<p><img src="https://www.plantuml.com/plantuml/svg/hPJ1JiCm44Jl_WghN42eVn155KMHoe7cW3XnsJhRP2N7Jcq7eGB_JXhQOgh6aLhda4Dsz3oEPpop3enhQycOa60jdoG9hAmp85oQlgcSjbkOy4_6k-UU9v1oMAz9LFY8LXXg76brU-UD1KZHIZIveOzky3q0NgZIO46et85-m_l5U7FzMlFTcpOj7eq7G4EGJBV686P6rr1UHSh1OKRg8iRkwu7peBk9S_XAe0eS-6qN-7kfj8f7Uu9w5PFt_m0Y09TKgfW6vnNKJS-q4KrAUaVxhCbW56gWVjFfLtg-zupzDIcWEcbAG7biGa1pal9pIiyzwyCx9jfdSamMse6lsoTeJEO7OnJfd_UO-FTIcA4gkflx1m00" alt=""></p>
<pre class=" language-java"><code class="prism  language-java"><span class="token keyword">public</span> <span class="token keyword">class</span> <span class="token class-name">Fromage</span> <span class="token punctuation">{</span>
	<span class="token keyword">private</span> Pizza p<span class="token punctuation">;</span>
	<span class="token keyword">public</span> <span class="token keyword">double</span> <span class="token function">calculerPrix</span><span class="token punctuation">(</span><span class="token punctuation">)</span> <span class="token punctuation">{</span>
		<span class="token keyword">return</span> p<span class="token punctuation">.</span><span class="token function">calculerPrix</span><span class="token punctuation">(</span><span class="token punctuation">)</span> <span class="token operator">+</span> <span class="token number">1.20</span><span class="token punctuation">;</span>
	<span class="token punctuation">}</span>
	<span class="token keyword">public</span> String <span class="token function">afficheDescription</span><span class="token punctuation">(</span><span class="token punctuation">)</span> <span class="token punctuation">{</span>
		<span class="token keyword">return</span> p<span class="token punctuation">.</span><span class="token function">afficheDescription</span><span class="token punctuation">(</span><span class="token punctuation">)</span> <span class="token operator">+</span> <span class="token string">"+ fromage"</span><span class="token punctuation">;</span>
	<span class="token punctuation">}</span>
<span class="token punctuation">}</span>
</code></pre>
<h2 id="ii---salle-de-conférences">II - Salle de conférences</h2>
<p><img src="https://www.plantuml.com/plantuml/svg/SoWkIImgAStDuGA2v9p4ucA5uCISd5Jd_BmqP3wKxL-KafcNM99QMWGL2CjCISqlAChFIar64WskB2v9pKrrB4t9pEVYWXkee6IefA2hQmUc8SPYazFJqr92jWcd6dJBSIf4TOz3QbuAqCS0" alt=""></p>
<pre class=" language-java"><code class="prism  language-java"><span class="token keyword">public</span> <span class="token keyword">class</span> <span class="token class-name">SalleConf</span> <span class="token punctuation">{</span>
	
	Ordinateur o <span class="token operator">=</span> <span class="token keyword">new</span> <span class="token class-name">Ordinateur</span><span class="token punctuation">(</span><span class="token punctuation">)</span><span class="token punctuation">;</span>
	Salle s <span class="token operator">=</span> <span class="token keyword">new</span> <span class="token class-name">Salle</span><span class="token punctuation">(</span><span class="token punctuation">)</span><span class="token punctuation">;</span>
	
	<span class="token keyword">public</span> <span class="token function">SalleConf</span><span class="token punctuation">(</span><span class="token punctuation">)</span> <span class="token punctuation">{</span><span class="token punctuation">}</span>
	
	<span class="token keyword">public</span> <span class="token keyword">void</span> <span class="token function">entrer</span><span class="token punctuation">(</span><span class="token punctuation">)</span> <span class="token punctuation">{</span>
		o<span class="token punctuation">.</span><span class="token function">allume</span><span class="token punctuation">(</span><span class="token punctuation">)</span><span class="token punctuation">;</span>
		s<span class="token punctuation">.</span><span class="token function">allumerLumiere</span><span class="token punctuation">(</span><span class="token punctuation">)</span><span class="token punctuation">;</span>
	<span class="token punctuation">}</span>
	
	<span class="token keyword">public</span> <span class="token keyword">void</span> <span class="token function">sortir</span><span class="token punctuation">(</span><span class="token punctuation">)</span> <span class="token punctuation">{</span>
		o<span class="token punctuation">.</span><span class="token function">eteindre</span><span class="token punctuation">(</span><span class="token punctuation">)</span><span class="token punctuation">;</span>
		s<span class="token punctuation">.</span><span class="token function">eteindreLumiere</span><span class="token punctuation">(</span><span class="token punctuation">)</span><span class="token punctuation">;</span>
	<span class="token punctuation">}</span>
</code></pre>
<h2 id="iii---document-xml">III - Document XML</h2>
<p><img src="https://www.plantuml.com/plantuml/svg/SoWkIImgAStDuGA2v9p4uc85fyISpE9KBWKWW8eesTWa9XMN52KcbzZPnUGvv-SMv1SdvfKeGUL3KYjAkBWW-XHqImjqxHIKj9JmQ4DIMcE7Hnt8OCAgk1nIyrA0NW00" alt=""></p>
<blockquote>
<p>A COMPLETER</p>
</blockquote>
<h1 id="tp-2">TP 2</h1>
<h2 id="i---simulation-dintersection-de-routes">I - Simulation d’intersection de routes</h2>
<p><img src="https://www.plantuml.com/plantuml/svg/bPFFJiCm3CRlVWfBN5gDyW0xJ9EGk24XWNfFKxD5Akrmd0aq-kwaJHksb0dHK-llyyz_acwjA1RtrW18joFP4-C9TAEinVl6K2jWMY5-LPhmGLLitXsLj3VQDUITw9yLdbHbXPMM7ZKJyMp8yZNExz33x8gW9qFIjH7phzooC-AOakGGJ7BxvMp920KUZP2rjCQwSvNFkeW-gez4aC-3zpuBctOtXcuYCWl6so3cKtk-VXbWGtDdh55wyRWXVWPSeTAQ6cBYYUZrOsVgFzGUfX6JvORFBFynf1kConjN1kcY2tSelZQBIm39OLwpXTk4nLsnIS_mLotW8AaUSPVLhZOp42VIOfv1cpk0BRMr_ms-0G00" alt=""></p>

