On abandonne les boucles for, on les remplace par des itérateurs.
> ```  javascript
> a = [1,2,3];
> for (let i = 0; i < 3; i++)
>  a[i] = a[i]* 2;
> -----
>  values = values.map(value => val * 2);
>  ```

Charger une liste d'amis : https://monsite/friends

``` javascript
let friends[].map(friend => {username: username})
-----
// Charger les amis dont le profil est public.
friends.map[].filter(friend => friend.publicProfile) // publicProfile booléen
```

Gestion des variables en JS vs ES6 :
``` javascript
function main() {
  let a = 5;
  for(var i = 0; i < a; i++) {
  }
  i++; // OK
}
-----
function main() {
  let a = 5;
  for(let i = 0; i < a; i++) {
  }
  i++; // Erreur
}
```

**Promise** :

``` javascript
function req(url) {
  new Promise((resolve, reject) {
    if(statusCode = 200) resolve();
    else reject();
  });
}
-----
let r = await req(url);
console.log("fini");
-----
req(url).then => (val => {
    let("fini");
  }) catch (err => {
    let("erreur");
});
```

**Fonctions nommées** :

``` javascript
function myFunc(a, func) {
};
-----
var myFunc(a = function() {
};
-----
var myFunc = () => {};
```
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTE2MDczNDc4NTAsMTEzMzAwODAwMiwtMj
AxODIzNjEwMSwtNzA4ODA3MDI5XX0=
-->