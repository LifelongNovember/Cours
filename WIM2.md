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
<h1 id="php---session_set_save_handler---version-fonctionnelle">PHP :  <code>session_set_save_handler</code> - version fonctionnelle</h1>
<h2 id="open">open</h2>
<pre class=" language-php"><code class="prism  language-php"><span class="token function">open</span><span class="token punctuation">(</span>string <span class="token variable">$savePath</span><span class="token punctuation">,</span> string <span class="token variable">$sessionName</span><span class="token punctuation">)</span>
</code></pre>
<p>Initialise le stockage des sessions.</p>
<h2 id="close">close</h2>
<pre class=" language-php"><code class="prism  language-php"><span class="token function">close</span><span class="token punctuation">(</span><span class="token punctuation">)</span>
</code></pre>
<p>Permet la fermeture de la session dans les cas où c’est nécessaire (libération de l’espace mémoire).</p>
<p>⇒ Avec PDO :</p>
<pre class=" language-php"><code class="prism  language-php"><span class="token variable">$pdo</span> <span class="token operator">=</span> <span class="token keyword">null</span><span class="token punctuation">;</span>
</code></pre>
<h2 id="read">read</h2>
<pre class=" language-php"><code class="prism  language-php"><span class="token function">read</span><span class="token punctuation">(</span>string <span class="token variable">$sessionId</span><span class="token punctuation">)</span>
</code></pre>
<p>Retourne les données de la session spécifiée sous un format linéarisé (tableau).</p>
<h2 id="write">write</h2>
<pre class=" language-php"><code class="prism  language-php"><span class="token function">write</span><span class="token punctuation">(</span>string <span class="token variable">$sessionId</span><span class="token punctuation">,</span> string <span class="token variable">$data</span><span class="token punctuation">)</span>
</code></pre>
<p>Sérialise et injecte les données dans la session spécifiée.</p>
<h2 id="destroy">destroy</h2>
<pre class=" language-php"><code class="prism  language-php"><span class="token function">destroy</span><span class="token punctuation">(</span><span class="token variable">$sessionId</span><span class="token punctuation">)</span>
</code></pre>
<h2 id="gc">gc</h2>
<pre class=" language-php"><code class="prism  language-php"><span class="token function">gc</span><span class="token punctuation">(</span><span class="token variable">$lifetime</span><span class="token punctuation">)</span>
</code></pre>
<p>Détruit périodiquement les données temporaires.</p>
<p>⇒ Elle est appelée directement par PHP en fonction du <code>lifetime</code> spécifié.</p>
<h1 id="php---session_set_save_handler---version-objet">PHP :  <code>session_set_save_handler</code> - version objet</h1>
<pre class=" language-php"><code class="prism  language-php">bool <span class="token function">session_set_save_handler</span><span class="token punctuation">(</span>SessionHandlerInterface <span class="token variable">$sessionhandler</span> <span class="token punctuation">[</span><span class="token punctuation">,</span> bool <span class="token variable">$register_showdown</span> <span class="token operator">=</span> <span class="token boolean">true</span> <span class="token punctuation">]</span><span class="token punctuation">)</span>
</code></pre>
<p>L’objet <code>sessionhandler</code>doit implémenter les méthodes correspondant aux fonctions mentionnées ci-dessus.</p>
<blockquote>
<p>CF <a href="http://php.net">php.net</a> &gt; SessionHandlerInterface</p>
</blockquote>
<h1 id="drupal-7--session-handler">Drupal 7 : Session handler</h1>
<p>Drupal 7 gère les sessions en base de données.</p>
<h2 id="open-1">open</h2>
<pre class=" language-php"><code class="prism  language-php"><span class="token keyword">function</span> <span class="token function">_drupal_session_open</span><span class="token punctuation">(</span><span class="token punctuation">)</span> <span class="token punctuation">{</span>
	<span class="token keyword">return</span> <span class="token constant">TRUE</span><span class="token punctuation">.</span>
<span class="token punctuation">}</span>
</code></pre>
<blockquote>
<p>La base de données est déjà préparée.</p>
</blockquote>
<h2 id="close-1">close</h2>
<pre class=" language-php"><code class="prism  language-php"><span class="token keyword">function</span> <span class="token function">_drupal_session_close</span><span class="token punctuation">(</span><span class="token punctuation">)</span> <span class="token punctuation">{</span>
	<span class="token keyword">return</span> <span class="token constant">TRUE</span><span class="token punctuation">;</span>
<span class="token punctuation">}</span>
</code></pre>
<blockquote>
<p>La cloture de l’accès à la base de données est automatique.</p>
</blockquote>
<h2 id="read-1">read</h2>
<pre class=" language-php"><code class="prism  language-php"><span class="token keyword">function</span> <span class="token function">_drupal_session_read</span><span class="token punctuation">(</span><span class="token variable">$sid</span><span class="token punctuation">)</span> <span class="token punctuation">{</span>
	<span class="token keyword">global</span> <span class="token variable">$user</span><span class="token punctuation">,</span> <span class="token variable">$is_https</span><span class="token punctuation">;</span>
	<span class="token function">drupal_register_shutdown_function</span><span class="token punctuation">(</span><span class="token string">'session_write_close'</span><span class="token punctuation">)</span><span class="token punctuation">;</span>
	<span class="token comment">///</span>
	<span class="token variable">$user</span> <span class="token operator">=</span> <span class="token function">db_query</span><span class="token punctuation">(</span><span class="token string">"SELECT u.*, s.* FROM {users} u INNER JOIN {sessions} s ON u.uid = s.uid WHERE s.sid = :sid"</span><span class="token punctuation">,</span> <span class="token keyword">array</span><span class="token punctuation">(</span><span class="token string">':sid'</span> <span class="token operator">=</span><span class="token operator">&gt;</span> <span class="token variable">$sid</span><span class="token punctuation">)</span><span class="token punctuation">)</span><span class="token operator">-</span><span class="token operator">&gt;</span><span class="token function">fetchObject</span><span class="token punctuation">(</span><span class="token punctuation">)</span><span class="token punctuation">;</span>
	<span class="token comment">///</span>
	<span class="token keyword">return</span> <span class="token variable">$user</span><span class="token operator">-</span><span class="token operator">&gt;</span><span class="token property">session</span><span class="token punctuation">;</span><span class="token punctuation">.</span>
<span class="token punctuation">}</span>
</code></pre>
<h2 id="write-1">write</h2>
<pre class=" language-php"><code class="prism  language-php"><span class="token keyword">function</span> <span class="token function">_drupal_session_write</span><span class="token punctuation">(</span><span class="token variable">$sid</span><span class="token punctuation">,</span> <span class="token variable">$value</span><span class="token punctuation">)</span> <span class="token punctuation">{</span>
	<span class="token keyword">global</span> <span class="token variable">$user</span><span class="token punctuation">,</span> <span class="token variable">$is_https</span><span class="token punctuation">;</span>
	<span class="token comment">///</span>
	<span class="token variable">$fields</span> <span class="token operator">=</span> <span class="token keyword">array</span><span class="token punctuation">(</span>
		<span class="token string">'uid'</span> <span class="token operator">=</span><span class="token operator">&gt;</span> <span class="token variable">$user</span><span class="token operator">-</span><span class="token operator">&gt;</span><span class="token property">uid</span><span class="token punctuation">,</span>
		<span class="token string">'cache'</span> <span class="token operator">=</span><span class="token operator">&gt;</span> <span class="token function">isset</span><span class="token punctuation">(</span><span class="token variable">$user</span><span class="token operator">-</span><span class="token operator">&gt;</span><span class="token property">cache</span><span class="token punctuation">)</span> <span class="token operator">?</span> <span class="token variable">$user</span><span class="token operator">-</span><span class="token operator">&gt;</span><span class="token property">cache</span> <span class="token punctuation">:</span> <span class="token number">0</span><span class="token punctuation">,</span>
		<span class="token string">'hostname'</span> <span class="token operator">=</span><span class="token operator">&gt;</span> <span class="token function">ip_address</span><span class="token punctuation">(</span><span class="token punctuation">)</span><span class="token punctuation">;</span>
		<span class="token string">'session'</span> <span class="token operator">=</span><span class="token operator">&gt;</span> <span class="token variable">$value</span><span class="token punctuation">,</span>
		<span class="token string">'timestamp'</span> <span class="token operator">=</span><span class="token operator">&gt;</span> <span class="token constant">REQUEST_TIME</span><span class="token punctuation">,</span>
	<span class="token punctuation">)</span><span class="token punctuation">;</span>
	<span class="token comment">///</span>
	<span class="token variable">$key</span> <span class="token operator">=</span> <span class="token keyword">array</span><span class="token punctuation">(</span><span class="token string">'sid'</span> <span class="token operator">=</span><span class="token operator">&gt;</span> <span class="token variable">$sid</span><span class="token punctuation">,</span> <span class="token string">'ssid'</span> <span class="token operator">=</span><span class="token operator">&gt;</span> <span class="token string">''</span><span class="token punctuation">)</span><span class="token punctuation">;</span>
	<span class="token comment">///</span>
	<span class="token function">db_merge</span><span class="token punctuation">(</span><span class="token string">'sessions'</span><span class="token punctuation">)</span>
		<span class="token operator">-</span><span class="token operator">&gt;</span><span class="token function">key</span><span class="token punctuation">(</span><span class="token variable">$key</span><span class="token punctuation">)</span>
		<span class="token operator">-</span><span class="token operator">&gt;</span><span class="token function">fields</span><span class="token punctuation">(</span><span class="token variable">$fields</span><span class="token punctuation">)</span>
		<span class="token operator">-</span><span class="token operator">&gt;</span><span class="token function">execute</span><span class="token punctuation">(</span><span class="token punctuation">)</span><span class="token punctuation">;</span>
	<span class="token comment">///</span>
<span class="token punctuation">}</span>
</code></pre>
<h2 id="destroy-1">destroy</h2>
<pre class=" language-php"><code class="prism  language-php"><span class="token keyword">function</span> <span class="token function">_drupal_session_destroy</span><span class="token punctuation">(</span><span class="token variable">$sid</span><span class="token punctuation">)</span> <span class="token punctuation">{</span>
	<span class="token keyword">global</span> <span class="token variable">$user</span><span class="token punctuation">,</span> <span class="token variable">$is_https</span><span class="token punctuation">;</span>
	<span class="token function">db_delete</span><span class="token punctuation">(</span><span class="token string">'sessions'</span><span class="token punctuation">)</span>
		<span class="token operator">-</span><span class="token operator">&gt;</span><span class="token function">condition</span><span class="token punctuation">(</span><span class="token variable">$is_https</span> <span class="token operator">?</span><span class="token string">'ssid'</span> <span class="token punctuation">:</span> <span class="token string">'sid'</span><span class="token punctuation">,</span> <span class="token variable">$sid</span><span class="token punctuation">)</span>
		<span class="token operator">-</span><span class="token operator">&gt;</span><span class="token function">execute</span><span class="token punctuation">(</span><span class="token punctuation">)</span><span class="token punctuation">;</span>
	<span class="token comment">///</span>
<span class="token punctuation">}</span>
</code></pre>
<h2 id="gc-1">gc</h2>
<pre class=" language-php"><code class="prism  language-php"><span class="token keyword">function</span> <span class="token function">_drupal_session_garbage_collection</span><span class="token punctuation">(</span><span class="token variable">$lifetime</span><span class="token punctuation">)</span> <span class="token punctuation">{</span>
	<span class="token function">db_delete</span><span class="token punctuation">(</span><span class="token string">'sessions'</span><span class="token punctuation">)</span>
		<span class="token operator">-</span><span class="token operator">&gt;</span><span class="token function">condition</span><span class="token punctuation">(</span><span class="token string">'timestamp'</span><span class="token punctuation">,</span> <span class="token constant">REQUEST_TIME</span> <span class="token operator">-</span> <span class="token variable">$lifetime</span><span class="token punctuation">,</span> <span class="token string">'&lt;'</span><span class="token punctuation">)</span>
		<span class="token operator">-</span><span class="token operator">&gt;</span><span class="token function">execute</span><span class="token punctuation">(</span><span class="token punctuation">)</span><span class="token punctuation">;</span>
	<span class="token keyword">return</span> <span class="token constant">TRUE</span><span class="token punctuation">;</span>
<span class="token punctuation">}</span>
</code></pre>
<h2 id="lien-drupal-7--php">Lien Drupal 7 / PHP</h2>
<pre class=" language-php"><code class="prism  language-php"><span class="token keyword">function</span> <span class="token function">drupal_session_initialize</span><span class="token punctuation">(</span><span class="token punctuation">)</span> <span class="token punctuation">{</span>
	<span class="token function">session_set_handler</span><span class="token punctuation">(</span>
		<span class="token string">'_drupal_session_open'</span><span class="token punctuation">,</span>
		<span class="token string">'_drupal_session_close'</span><span class="token punctuation">,</span>
		<span class="token string">'_drupal_session_read'</span><span class="token punctuation">,</span>
		<span class="token string">'_drupal_session_write'</span><span class="token punctuation">,</span>
		<span class="token string">'_drupal_session_destroy'</span><span class="token punctuation">,</span>
		<span class="token string">'_drupal_session_garbage_collection'</span>
	<span class="token punctuation">)</span><span class="token punctuation">;</span>
 <span class="token punctuation">}</span>
</code></pre>
<h1 id="authentification-des-utilisateurs">Authentification des utilisateurs</h1>

