> Généré depuis [StackEdit](https://stackedit.io/). Si ce fichier est sur GitHub, vous êtes en train de lire un backup du document original, qui est accessible [ici](https://frama.link/aden-iutsd) (avec de belles formules à la place des entrées Latex).
>
> Une authentification est demandée. 
> > Compte lecture seule :
> > Identifiant : **reader**
> > Mot de passe : **reader** aa


# PHP :  `session_set_save_handler` - version fonctionnelle

## open

``` php
open(string $savePath, string $sessionName)
```

Initialise le stockage des sessions.



## close

```php
close()
```

Permet la fermeture de la session dans les cas où c'est nécessaire (libération de l'espace mémoire).

⇒ Avec PDO : 
```php 
$pdo = null;
```

## read

```php
read(string $sessionId)
```

Retourne les données de la session spécifiée sous un format linéarisé (tableau).

## write

```php
write(string $sessionId, string $data)
```

Sérialise et injecte les données dans la session spécifiée.

## destroy

```php
destroy($sessionId)
```

## gc

```php
gc($lifetime)
```

Détruit périodiquement les données temporaires.

⇒ Elle est appelée directement par PHP en fonction du `lifetime` spécifié.

# PHP :  `session_set_save_handler` - version objet

```php
bool session_set_save_handler(SessionHandlerInterface $sessionhandler [, bool $register_showdown = true ])
```

L'objet `sessionhandler`doit implémenter les méthodes correspondant aux fonctions mentionnées ci-dessus.

> CF php.net > SessionHandlerInterface

# Drupal 7 : Session handler

Drupal 7 gère les sessions en base de données.

## open

```php
function _drupal_session_open() {
	return TRUE;
}
```
> La base de données est déjà préparée.

## close

```php
function _drupal_session_close() {
	return TRUE;
}
```
> La cloture de l'accès à la base de données est automatique.

## read

```php
function _drupal_session_read($sid) {
	global $user, $is_https;
	drupal_register_shutdown_function('session_write_close');
	///
	$user = db_query("SELECT u.*, s.* FROM {users} u INNER JOIN {sessions} s ON u.uid = s.uid WHERE s.sid = :sid", array(':sid' => $sid))->fetchObject();
	///
	return $user->session;
}
```
## write

```php
function _drupal_session_write($sid, $value) {
	global $user, $is_https;
	///
	$fields = array(
		'uid' => $user->uid,
		'cache' => isset($user->cache) ? $user->cache : 0,
		'hostname' => ip_address(),
		'session' => $value,
		'timestamp' => REQUEST_TIME,
	);
	///
	$key = array('sid' => $sid, 'ssid' => '');
	///
	db_merge('sessions')
		->key($key)
		->fields($fields)
		->execute();
	///
}
```

## destroy

```php
function _drupal_session_destroy($sid) {
	global $user, $is_https;
	db_delete('sessions')
		->condition($is_https ?'ssid' : 'sid', $sid)
		->execute();
	///
}
```

## gc

```php
function _drupal_session_garbage_collection($lifetime) {
	db_delete('sessions')
		->condition('timestamp', REQUEST_TIME - $lifetime, '<')
		->execute();
	return TRUE;
}
```

## Lien Drupal 7 / PHP

```php
function drupal_session_initialize() {
	session_set_handler(
		'_drupal_session_open',
		'_drupal_session_close',
		'_drupal_session_read',
		'_drupal_session_write',
		'_drupal_session_destroy',
		'_drupal_session_garbage_collection'
	);
 }
```

# Authentification des utilisateurs


<!--stackedit_data:
eyJoaXN0b3J5IjpbLTExOTUwMjU3NTVdfQ==
-->