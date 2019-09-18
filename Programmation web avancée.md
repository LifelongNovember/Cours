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
new Promise() let req = XMLHTTPRequest(val,..., callback)
```
<!--stackedit_data:
eyJoaXN0b3J5IjpbMjU0MTA2OTkwLC0yMDE4MjM2MTAxLC03MD
g4MDcwMjldfQ==
-->