> Généré depuis [StackEdit](https://stackedit.io/). Si ce fichier est sur GitHub, vous êtes en train de lire un backup du document original, qui est accessible [ici](https://frama.link/aden-iutsd) (avec de belles formules à la place des entrées Latex).
>
> Une authentification est demandée. 
> > Compte lecture seule :
> > Identifiant : **reader**
> > Mot de passe : **reader**

# Cours
## Patrons de conception
Ref : Design Patterns (Tête la première)

### Patrons de construction
Création et configuration d'objets

#### Singleton
Utilisé lors de l'utilisation de classes instanciées de manière unique.
``` java
private class Singleton {

	private static Singleton instance;
	private Singleton()
	{
		///
	}
	public static Singleton getInstance() {
		if(instance == null)
			instance = new Singleton();
		return instance;
	}
}
```
Compliqué à mettre en place dans le cas du multi-threading
```java
public static synchronized Singleton getInstance()
```
Coûteux lors de l'execution
``` java
private class Singleton {

	private static Singleton instance = new Singleton();
	private Singleton()
	{
		///
	}
	public static Singleton getInstance() {
		return instance;
	}
}
```

``` java
private class Singleton {

	private volatile static Singleton instance;
	private Singleton()
	{
		///
	}
	public static synchronized Singleton getInstance() {
		if(instance == null) {
			synchronized (Singleton.class) {
				if(instance == null)
				instance = new Singleton();
			}
		}
		return instance;
	}
}
```

#### Factory Method / Abstract Factory

En fonction du type d'objet dont on a besoin, on peut être amené à multiplier les appels à instancier des classes concrètes.

Une classe de fabrique permet de factoriser les instanciations et de créer les objets en fonction du type fourni  (fabrique paramétrée).

Les classes de fabrique se succèdent mais il est possible de faire les opérations dans une classe abstraite (avec une méthode abstraite) qu'implémentent toutes les classes de fabrique.

![](https://www.plantuml.com/plantuml/svg/fPEn3e8m48Ptde8mwS10PqBWI5nz0PU2PrA3DRR7fBwxLMXYgP8IklNk_x_s_hIb9gweltHHr7PSwpZ9So49rOctM1G7kUED4hSUgqQJue8mYUzHR5Qj4DM-EIDLc-sa0gRoj4HBgA-oLKYOhGMmfO2w4oZftuG3OHolIgniA6VkbWL1m8M02m43yJD9qqSH4BxdPC7E8GKZNwkU1XOg1V_ssSTbevxfWjzbNrusrpM1ZoVypcewpuXS88OGCbXn2FdzX4gKH_CpNm00)

⇒ L'utilisateur n'est plus responsable de la création des objets.
⇒ À la place, il manipule des familles d'objets par le biais de la fabrique abstraite.

### Patrons de structuration

#### Adaptateur

L'adaptateur permet à un système et à une interface incompatibles de communiquer.

``` java
Reader isr = new InputStreamReader(new FileInputStream(file));
while((int c = isr.read() != -1)
	System.out.println(c);
isr.close();
```

#### Façade

La façade permet l'utilisation d'un système complexe à partir d'une interface unique.

#### Décorateur

Le décorateur permet la superposition de composants de même type. Les interfaces permettent de spécifier les composants (leur ajouter de nouvelles fonctionnalités...) pour construire l'objet final.

![](https://www.plantuml.com/plantuml/svg/dP913i8W44NtSmhIbIvw0q9QwZ7SZ9J4HG43qvLwTud1QW2jwImdUIz_VgOBX9vcCm6e2KDW3UTu2kHHaH17EpXpSG4jDUmAB0v7mOocinjrlzldAnbNzvTgOGTdbTUK31bT8xCG1wsSHzAptv3Y3QSOVN8iyPZwDrVXabjSHIzjUnFVYuSVRQoGbTjhn8UnHEGgyZmHeDDsZ8_q0000)

#### Composite

Une structure composite permet d'appliquer les mêmes opérations aux composés et aux composants.
Une structure composite permet de représenter des hiérarchies composant / composé.



# TD 1
**Révisions - Diagrammes de classe, Diagrammes de séquence**

## I - Premiers exercices (plus ou moins) simples

> ### 1. Une classe contient des élèves.
> 
> ![](https://www.plantuml.com/plantuml/svg/SoWkIImgAStDuU9ApaaiBbPm1f6fKCxXpfp3AyfIkRWWeWfAXaeAkhfs2afQIZ0v1Ik5vFoyaipKl18kBeVKl1IWMG00)

> ### 2. Les modems et les claviers sont des périphériques d'entrée.
> 
> ![](https://www.plantuml.com/plantuml/svg/SoWkIImgAStDuU9ApaaiBbO8EBooABCW0qGMbgP21NtpKr9peMpddCIopDGYBYwme8AkReqTkYQe4gnoN0wfUIb0-m00)

> ### 3. Une bibliothèque possède des exemplaires ; ces exemplaires peuvent être soit des livres soit des cds.
>  
>  ![](https://www.plantuml.com/plantuml/svg/SoWkIImgAStDuU9ApaaiBbPmoapAoSmloJYyeh0q5IhcMf6QMv2Jc5a44_39B8EpdLsuk50qAIWPAYdewjefA1aewEafQ2aXwLUmKYZ8Bou-l28bbSlP1QYgnWxPTB2v6A9S3gbvAK0d0W00)

> ### 4. Un répertoire contient plusieurs éléments, chacun de ces éléments peut être un fichier ou un autre répertoire.
>  
>  ![](https://www.plantuml.com/plantuml/svg/SoWkIImgAStDuU9ApaaiBbO8Ehoo8BMe93-pA1KgShWpv_3AtDIy4YZVBJCv8pErY8iBIQc2ag6IWgwk7P1MqDDJq5A2gLAmKaZEpol916b7Lg-hMsE7P39CDPembqDgNWhGSG00)

## II - Classes `Telecommande` et `Lampe`
Classes : 
* `Lampe`
* `Telecommande`

`Lampe` :
* Attribut `nom` permettant d'identifier la lampe
* Attribut `allume` de type `boolean` valant `true` si la lampe est allumée
* Constructeur d'une lampe éteinte à partir de son nom

`Telecommande` :
* Attribut `lampes` de type liste de `Lampe`
* Constructeur vide
* Méthode `ajouterLampe` ajoutant une `Lampe`passée en paramètre dans la liste des lampes contrôlées
* Méthode `activerLampe` activant la `Lampe` dont l'indice est passé en paramètre
* Méthode `desactiverLampe` désactivant la `Lampe` dont l'indice est passé en paramètre
* Méthode `activerTout` activant toutes les lampes contrôlées par la `Telecommande`

![](https://www.plantuml.com/plantuml/svg/VL4z3y8W5Dpv5IzCrQIDhXrCVu2RtOm3bXU3uSF0eulnlrifH5na0UxkvUvW22GyHQCPcxG80Ox2F12U39Pr8g_i3QmpwNfrJgEm8BIE1g47yX4JauQQhtoJqDafcSM-gI0aL5Pwp5WU8xSU5lHLmeoeSNB622jBfcHrle3-x251jQhs4NSN2VqQRksbQteYDHTQMG9LaHB3NpwJu-BmhyPF0Rw3heCzXxOz0D_o_DOz50LZ0rgvVCOR)

## III - Classe `Reader`

Classes :
* `Reader`: abstraite
* `FileReader` :`Reader`
* `BufferedReader` : `Reader` contenant un autre `Reader`


``Reader`` :
* Méthode `read`

`BufferedReader` :
``` java
Reader f = new FileReader(name);
BufferedReader bf = new BufferedReader(f);
```

![](https://www.plantuml.com/plantuml/svg/SoWkIImgAStDuU9ApaaiBbPGih59J2ekAKfCBh6pYyaBIarCIIrIKgZcKW02cqGxXRByp1I58g2mXYPNBKoNMsPEAaGfL2LMLKwbQMcfHQafA2fH1JKWb2OsGv0iqTMjiSFXL2uqMqXIYbCbbqDgNWemc000)

## IV - Bibliothèque - ajout des méthodes

Classe `Bibliotheque` (cf I.3) : Implémenter la description de l'ensemble des éléments de la bibliothèque

![](https://www.plantuml.com/plantuml/svg/XP0z3i8m34RtdCBA14WPM54LLVniRAmiQR2AfJGfYOkGWFjm3ov6fLA93hIUFBpFVdQUs4HkAYU4TIObM5FXAF3v_Req27S1RHquaY-1GzVCvkBPupBBJ94u6ijQ7_tkXbNj34MKtsncT9ylaRUORAIQAVZVAPljSDD_Sa_NYDFmy0gvbA2K1hcGOy8hiC4peMVH2Ydrq2Eqw4ocA96ZFxNl_G00)

```java
class Bibliothèque {
	Exemplaire[] exemplaires;
	String toString() {
		String r;
		for(int i = 0; i < exemplaires[]; i++) {
			r += exemplaires[i].getDescription();
		}
		return r;
	}
}
```

## V - Emploi du temps I

* Un `EmploiDuTemps` contient des `Creneau`
* Chaque `Creneau`est associé à une `Matiere`, un `GroupeEtudiant` et une `Salle`. Il est caractérisé par une `Date`
* L'université est constituée de `Personne` pouvant être `Etudiant`ou `Enseignant`
* Les `Etudiant` appartiennent à un `GroupeEtudiant`
* Un `Enseignant` participe à une ou plusieurs `Matiere`

![](https://www.plantuml.com/plantuml/svg/RP5D2i8m48NtESNGfP2YMnUbOCML8EW5GZj889sK_ApKknjicgHg5adcvMFU6z9Q9uppesAiLy9QE8wJqhBpDnmd6xM3GKBXuS4Wh4uuX25ix1NVhq8fZFUpS1BDKfsCzXCUdH-a8BTOV9LaKTuf2nSqLXCXOwimKEqguBo1QWjr3PigvTf3hodOXWwBbDXmVkBDK8yczFq7nTmbjWvVqD4-lHJ-UPXVFblWJ669S_viykYfzrfcBT8GVkiD)

## VI - Diagrammes de séquence - Exercices simples 

> ### 1. Un objet `r` de la classe `UnRectangle` demande à son coin de se translater selon la direction (10,10).
> ![](https://www.plantuml.com/plantuml/svg/SoWkIImgAStDuU9IAbAmKWZD2qfDBadCIyz9LLBGjLDGIixFp0EB1m0P9Kf0Pd5gI55YNd5EOabgaOQXWOwXWIPGCxewNP1cT1EvkBWSKlDIWDO10000)

> ### 2. Le programme principal demande à la classe `Maths` de `calculerPi(int n)` à 5 décimales près.
> ![](https://www.plantuml.com/plantuml/svg/SoWkIImgAStDuU9I2YZAp4lEB4ZCILLIqBLJKCfDBCaeLh1Iy0NHIa16Sc9EScbEQb50feQf9b03cWAG7cGph1ICzGnD34qjkRYu75BpKe2s0000)

## VII - Calcul du poids d'une voiture

Le poids d'une voiture est égal à la somme du poids de son moteur et du poids de sa carrosserie.

![](https://www.plantuml.com/plantuml/svg/SoWkIImgAStDuU9ApaaiBbO8oyyiAIrALQZcKW02xPJyqgISL8Nqr9A0_CoKOgYiXYPNBLIzRtv9QcaH3kKGIIJLpeb5-SN5gKMPk2m0AW0hvuAvGybGIK7N3an1hR9IqCq5ix2fGR80g2uPnEFYSaZDIm5w4G00)

![](https://www.plantuml.com/plantuml/svg/SoWkIImgAStDuUBAJSpCKz2rKr0gKx1I2ClFB2ajIbK2CjDJImBoCrEAeK8QcboeAa1QSe42llabgQL5o3eW8Y0DoFAwMEmeCCHYQ39Gm3cnAB-uEBKe4yKfG56GgUWAi9fiX6uoK17Ogo1R5RH12hWSKlDIW6400000)

## VII - Retrait d'argent

![](https://www.plantuml.com/plantuml/svg/RP0x3i8m38RtdCBgnACTM3EW2de2E47QkX0fTI1n1eIuEsdfGwtmv3Y_Ftr9xbav3gqHeZBAUoYqPwVBm1WSl0N4sWDwhrxeBiXEQTu4ZqvUOunkARIMM15BJPn2PMlikgqihJMeI7n6y4dHC-0PAJ8CJcWL-1vdkj7ebk2PTRRjWt56_Su38fiC2XjAWwDoqs35OPOcs_vpNfWk7f_i4iYEa1oIjRk4hEmdOdNHPRkLk3auncZLTrx4of7g-DTV)

`Distributeur`:
* Relié à une `BanqueCentrale`
* `essayerRetrait` retourne `true` si le retrait a pu être effectué

`BanqueCentrale` :
* Peut `authentifier` un utilisateur (retourne le `Compte` qui lui est associé si son code est correct, `null` sinon)

`Compte` :
* Permet d'`effectuerRetrait` au montant demandé sur le compte de l'utilisateur

> ### Retrait de 100€ avec un code correct
> ![](https://www.plantuml.com/plantuml/svg/TP312i8m38RlVOhIauB2P0V1Wmpd4uWlq6qf5jPkfid1jpURWXxQ7Wef-RylJPF88d4ObGhMHxq_QpFeaxxwHEWx9c0qKaDAzWLu0qBhQMFk4qrcfmzL9LTT7xSg4rjWNI_F5nkV32r4IO-my2pJGqhlFE2FzW5b8wN1-f9uWRHJc6drWNFG4sT_8Ch_vfA9aA4WMrVtxP3JG1nafMy0)

> ### Retrait avec un code incorrect
> ![](https://www.plantuml.com/plantuml/svg/TO_12i9034Jl-nLXJmeLrciFKjGl47yWjIa6jblC9WV_tbJ4Kpkt2SoRJ5SLHMtA8Kp81GudY0EqSEMgmhqfcKJtL2k-IMwaWgoxU9zrZWqSKseWkVPX9RR0-eUVprXUHXSgdiwqyD3qwPP79ldJVg3LoDPZnNBUwFuEQc74N2cuEYg3B_q0)

# TD 3

## I - RegisterWindows

![](https://www.plantuml.com/plantuml/svg/SoWkIImgAStDuU9ApaaiBbO8IatFB2v9BGhFp4l9BozMgEPI009qqSmyeBwyv5ImP719KMPUka9UVYusjHeGQKsivgIdbdX2ZTBGvAhbSaZDIm4w1W00)

```java
class RegisterWindows {
public class RegisterWindows {
	private static RegisterWindows instance;
	private static String nom;
	private RegisterWindows(String noms) {
		RegisterWindowthis.nom = noms;
	}
	static public RegisterWindows getInstance(String nom) {
		if(instance == null)
			instance = new RegisterWindows(nom);
		return instance;
	}
	public String getNom() {
		return nom;
	}
}
```

## II - Connexions

![](https://www.plantuml.com/plantuml/svg/dPB12y8W5CRlxwyGJnNjq7KC6HLq2I9sxM9Emd0QwY2e_lTicskCZKMUzF5zxti_DRME6bSM4e19QYt2IKBFrXdA724dbUtMMumUWFnAA47CS6usMYb-5rhDIYUaiCiYlytZjbg9wLMNRbhwQc8_EGSVAdaJzbDGrvqTz_zOUxoj843NxZXpHgXBLV6DmZ4qQLr-Y7wffWBe44RHamnUD0IGSSNW--0LHf4tBF0uJyp2ra9tti6ihmrw85FobAlSVwSt)
	
# TD 4

## I - Pizzas

![](https://www.plantuml.com/plantuml/svg/hPJ1JiCm44Jl_WghN42eVn155KMHoe7cW3XnsJhRP2N7Jcq7eGB_JXhQOgh6aLhda4Dsz3oEPpop3enhQycOa60jdoG9hAmp85oQlgcSjbkOy4_6k-UU9v1oMAz9LFY8LXXg76brU-UD1KZHIZIveOzky3q0NgZIO46et85-m_l5U7FzMlFTcpOj7eq7G4EGJBV686P6rr1UHSh1OKRg8iRkwu7peBk9S_XAe0eS-6qN-7kfj8f7Uu9w5PFt_m0Y09TKgfW6vnNKJS-q4KrAUaVxhCbW56gWVjFfLtg-zupzDIcWEcbAG7biGa1pal9pIiyzwyCx9jfdSamMse6lsoTeJEO7OnJfd_UO-FTIcA4gkflx1m00)

``` java
public class Fromage {
	private Pizza p;
	public double calculerPrix() {
		return p.calculerPrix() + 1.20;
	}
	public String afficheDescription() {
		return p.afficheDescription() + "+ fromage";
	}
}
```

## II - Salle de conférences

![](https://www.plantuml.com/plantuml/svg/SoWkIImgAStDuGA2v9p4ucA5uCISd5Jd_BmqP3wKxL-KafcNM99QMWGL2CjCISqlAChFIar64WskB2v9pKrrB4t9pEVYWXkee6IefA2hQmUc8SPYazFJqr92jWcd6dJBSIf4TOz3QbuAqCS0)

```java
public class SalleConf {
	
	Ordinateur o = new Ordinateur();
	Salle s = new Salle();
	
	public SalleConf() {}
	
	public void entrer() {
		o.allume();
		s.allumerLumiere();
	}
	
	public void sortir() {
		o.eteindre();
		s.eteindreLumiere();
	}
```

## III - Document XML

![](https://www.plantuml.com/plantuml/svg/SoWkIImgAStDuGA2v9p4uc85fyISpE9KBWKWW8eesTWa9XMN52KcbzZPnUGvv-SMv1SdvfKeGUL3KYjAkBWW-XHqImjqxHIKj9JmQ4DIMcE7Hnt8OCAgk1nIyrA0NW00)

> A COMPLETER

# TP 2

## I - Simulation d'intersection de routes

![](https://www.plantuml.com/plantuml/svg/bPFFJiCm3CRlVWfBN5gDyW0xJ9EGk24XWNfFKxD5Akrmd0aq-kwaJHksb0dHK-llyyz_acwjA1RtrW18joFP4-C9TAEinVl6K2jWMY5-LPhmGLLitXsLj3VQDUITw9yLdbHbXPMM7ZKJyMp8yZNExz33x8gW9qFIjH7phzooC-AOakGGJ7BxvMp920KUZP2rjCQwSvNFkeW-gez4aC-3zpuBctOtXcuYCWl6so3cKtk-VXbWGtDdh55wyRWXVWPSeTAQ6cBYYUZrOsVgFzGUfX6JvORFBFynf1kConjN1kcY2tSelZQBIm39OLwpXTk4nLsnIS_mLotW8AaUSPVLhZOp42VIOfv1cpk0BRMr_ms-0G00)


