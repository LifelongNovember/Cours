> Généré depuis [StackEdit](https://stackedit.io/). Si ce fichier est sur GitHub, vous êtes en train de lire un backup du document original, qui est accessible [ici](https://frama.link/aden-iutsd) (avec de belles formules à la place des entrées Latex).
>
> Une authentification est demandée. 
> > Compte lecture seule :
> > Identifiant : **reader**
> > Mot de passe : **reader**

# Introduction à Angular

L'idée est de rapprocher HTML et JS en créant de nouvelles balises et des attributs spéciaux. Afin d'anticiper l'innovation tout en fournissant des applications compatibles, **TypeScript** a été créé afin d'anticiper l'innovation et éventuellement se traduire en JS, selon les spécifications **ES2015**. Comme **TypeScript** est transpilé, les instructions JS sont recréées et interprétées par les navigateurs plus anciens.

**TypeScript** est **fortement typé**, ce qui permet l'utilisation d'IDE plus évolués et une structure de données plus spécifique.

L'utilisation des nouvelles balises et de leurs attributs permet d'économiser énormément de lignes de codes en langage basique.

Les **décorateurs** permettent d'annoter les classes afin de leur ajouter des fonctionnalités ou des données sans les modifier. Les **injections de dépendances** permettent d'instancier les objets et de leur attribuer des méthodes que le client n'a pas besoin de connaître pour faire fonctionner leur programme.

## TypeScript

### Types de base

`let` permet de créer des variables locales (préférées aux variables globales).

```javascript
let firstName: string = "John";
let lastName = 'Smith';
let height: number = 6;
let isDone: boolean = false;
```

```javascript
var numbers:number[] = [1, 2, 3];
var name:Array<string> = ['Alice', 'Helen', 'Claire'];
```

`any` est le supertype de tous les autres types. Si le type d'une variable n'est pas spécifié, celle-ci sera de type `any`.

```javascript
var w: any;
var y;
```

### Interfaces

```javascript
interface IVehicle {
	wheels: number;
	engine: string;
	drive();
}
```

### Décorateurs

Un décorateur s'utilise sous la forme `@decoratorName`. Il permet de spécifier les classes qui seront créées.

(CF 7)

### Architecture 

Angular est composé de **composants**. Afin de traiter des données, ils vont utiliser des **services** en fonction des **directives** qui leur sont injectées (généralement en attribut).

#### Modules

Beaucoup de fonctionnalités ont déjà été écrites et peuvent être importées par le biais des **modules**.

```javascript
import { Module } from '@angular/misc';
///
@MonModule({
	// Modules & fonctions importées
	imports: [
		Module, 
		/// 
	],
	// Composant utilisé
	declarations: [
		AppComponant
	],
	// Composant raçine
	bootstrap: [AppComponent]
})
export class MyApp{ }
```

#### Composants

Un composant est une partie de l'interface utilisateur (appelée **vue**). Il s'agît d'une classe décorée afin d'inclure des métadonnées.

```javascript
import { Component } from '@angular/core';
@Composant({
	selector: 'mean-app',
	template: '<h1>Lorem ipsum</h1>'
})
export class AppComponent { }
```

⇒ Permet de créer une balise `<mean-app>` dans le code HTML qui sera remplacée par `<h1>Lorem ipsum</h1>`.

#### Templates

Les **templates** permettent de rendre la vue du composant.

```javascript
import { Component } from '@angular/core';

@Component({
	selector: 'mean-app',
	templateUrl: 'app.template.html'
})
export class AppComponent {}
```

### Liaison de données (data binding)

Angular permet la liaison de données sophistiquées.

#### Interpolation binding

L'interpolation lie une valeur d'une propriété de classe avec un placeholder du template renseigné entre doubles accolades.

```javascript
import { Component } from '@angular/core';

@Component({
	selector: 'mean-app',
	template: `<h1>{{title}}</h1>`
})
export class AppComponent {
	title = 'Mon Application';
}
```

⇒ Facilite énormément la mise en place d'une structure MVC.

#### Property binding

L'élément entre crochets va conditionner le comportement d'un élément HTML.

```javascript
import { Component } from '@angular/core';

@Component({
	selector: 'mean-app',
	template: `<button [disabled]="isButtonDisabled">My Button</button>`
})
export class AppComponent {
	isButtonDisabled = true;
}
```

/!\ Différent de `<button disabled="{{isButtonDisabled}}">My Button</button>` (CF 13)

#### Event binding

Un nom d'événement peut être renseigné entre parenthèses, son comportement est défini dans la classe.

```javascript
import { Component } from '@angular/core';

@Component({
	selector: 'mean-app',
	template: `<button (click)="showMessage()">Show Message</button>`
})
export class AppComponent {
	showMessage() {
		alert('This is a message!')
	}
}
```
#### Liaison bidirectionnelle

```javascript
import { Component } from '@angular/core';

@Component({
	selector: 'mean-app',
	template: `<h1>Hello {{name}}</h1><br><input [(ngModel)]="name">`
})
export class AppComponent {
	name = ''
}
```

Une modification dans la valeur de `name` est répercutée dans l'attribut de l'`input` et réciproquement.
 
 ⇒ `ngModel` est une **directive**.


