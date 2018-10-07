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
<h1 id="introduction-à-angular">Introduction à Angular</h1>
<p>L’idée est de rapprocher HTML et JS en créant de nouvelles balises et des attributs spéciaux. Afin d’anticiper l’innovation tout en fournissant des applications compatibles, <strong>TypeScript</strong> a été créé afin d’anticiper l’innovation et éventuellement se traduire en JS, selon les spécifications <strong>ES2015</strong>. Comme <strong>TypeScript</strong> est transpilé, les instructions JS sont recréées et interprétées par les navigateurs plus anciens.</p>
<p><strong>TypeScript</strong> est <strong>fortement typé</strong>, ce qui permet l’utilisation d’IDE plus évolués et une structure de données plus spécifique.</p>
<p>L’utilisation des nouvelles balises et de leurs attributs permet d’économiser énormément de lignes de codes en langage basique.</p>
<p>Les <strong>décorateurs</strong> permettent d’annoter les classes afin de leur ajouter des fonctionnalités ou des données sans les modifier. Les <strong>injections de dépendances</strong> permettent d’instancier les objets et de leur attribuer des méthodes que le client n’a pas besoin de connaître pour faire fonctionner leur programme.</p>
<h2 id="typescript">TypeScript</h2>
<h3 id="types-de-base">Types de base</h3>
<p><code>let</code> permet de créer des variables locales (préférées aux variables globales).</p>
<pre class=" language-javascript"><code class="prism  language-javascript"><span class="token keyword">let</span> firstName<span class="token punctuation">:</span> string <span class="token operator">=</span> <span class="token string">"John"</span><span class="token punctuation">;</span>
<span class="token keyword">let</span> lastName <span class="token operator">=</span> <span class="token string">'Smith'</span><span class="token punctuation">;</span>
<span class="token keyword">let</span> height<span class="token punctuation">:</span> number <span class="token operator">=</span> <span class="token number">6</span><span class="token punctuation">;</span>
<span class="token keyword">let</span> isDone<span class="token punctuation">:</span> boolean <span class="token operator">=</span> <span class="token boolean">false</span><span class="token punctuation">;</span>
</code></pre>
<pre class=" language-javascript"><code class="prism  language-javascript"><span class="token keyword">var</span> numbers<span class="token punctuation">:</span>number<span class="token punctuation">[</span><span class="token punctuation">]</span> <span class="token operator">=</span> <span class="token punctuation">[</span><span class="token number">1</span><span class="token punctuation">,</span> <span class="token number">2</span><span class="token punctuation">,</span> <span class="token number">3</span><span class="token punctuation">]</span><span class="token punctuation">;</span>
<span class="token keyword">var</span> name<span class="token punctuation">:</span>Array<span class="token operator">&lt;</span>string<span class="token operator">&gt;</span> <span class="token operator">=</span> <span class="token punctuation">[</span><span class="token string">'Alice'</span><span class="token punctuation">,</span> <span class="token string">'Helen'</span><span class="token punctuation">,</span> <span class="token string">'Claire'</span><span class="token punctuation">]</span><span class="token punctuation">;</span>
</code></pre>
<p><code>any</code> est le supertype de tous les autres types. Si le type d’une variable n’est pas spécifié, celle-ci sera de type <code>any</code>.</p>
<pre class=" language-javascript"><code class="prism  language-javascript"><span class="token keyword">var</span> w<span class="token punctuation">:</span> any<span class="token punctuation">;</span>
<span class="token keyword">var</span> y<span class="token punctuation">;</span>
</code></pre>
<h3 id="interfaces">Interfaces</h3>
<pre class=" language-javascript"><code class="prism  language-javascript"><span class="token keyword">interface</span> <span class="token class-name">IVehicle</span> <span class="token punctuation">{</span>
	wheels<span class="token punctuation">:</span> number<span class="token punctuation">;</span>
	engine<span class="token punctuation">:</span> string<span class="token punctuation">;</span>
	<span class="token function">drive</span><span class="token punctuation">(</span><span class="token punctuation">)</span><span class="token punctuation">;</span>
<span class="token punctuation">}</span>
</code></pre>
<h3 id="décorateurs">Décorateurs</h3>
<p>Un décorateur s’utilise sous la forme <code>@decoratorName</code>. Il permet de spécifier les classes qui seront créées.</p>
<p>(CF 7)</p>
<h3 id="architecture">Architecture</h3>
<p>Angular est composé de <strong>composants</strong>. Afin de traiter des données, ils vont utiliser des <strong>services</strong> en fonction des <strong>directives</strong> qui leur sont injectées (généralement en attribut).</p>
<h4 id="modules">Modules</h4>
<p>Beaucoup de fonctionnalités ont déjà été écrites et peuvent être importées par le biais des <strong>modules</strong>.</p>
<pre class=" language-javascript"><code class="prism  language-javascript"><span class="token keyword">import</span> <span class="token punctuation">{</span> Module <span class="token punctuation">}</span> <span class="token keyword">from</span> <span class="token string">'@angular/misc'</span><span class="token punctuation">;</span>
<span class="token comment">///</span>
@<span class="token function">MonModule</span><span class="token punctuation">(</span><span class="token punctuation">{</span>
	<span class="token comment">// Modules &amp; fonctions importées</span>
	imports<span class="token punctuation">:</span> <span class="token punctuation">[</span>
		Module<span class="token punctuation">,</span> 
		<span class="token comment">/// </span>
	<span class="token punctuation">]</span><span class="token punctuation">,</span>
	<span class="token comment">// Composant utilisé</span>
	declarations<span class="token punctuation">:</span> <span class="token punctuation">[</span>
		AppComponant
	<span class="token punctuation">]</span><span class="token punctuation">,</span>
	<span class="token comment">// Composant raçine</span>
	bootstrap<span class="token punctuation">:</span> <span class="token punctuation">[</span>AppComponent<span class="token punctuation">]</span>
<span class="token punctuation">}</span><span class="token punctuation">)</span>
<span class="token keyword">export</span> <span class="token keyword">class</span> <span class="token class-name">MyApp</span><span class="token punctuation">{</span> <span class="token punctuation">}</span>
</code></pre>
<h4 id="composants">Composants</h4>
<p>Un composant est une partie de l’interface utilisateur (appelée <strong>vue</strong>). Il s’agît d’une classe décorée afin d’inclure des métadonnées.</p>
<pre class=" language-javascript"><code class="prism  language-javascript"><span class="token keyword">import</span> <span class="token punctuation">{</span> Component <span class="token punctuation">}</span> <span class="token keyword">from</span> <span class="token string">'@angular/core'</span><span class="token punctuation">;</span>
@<span class="token function">Composant</span><span class="token punctuation">(</span><span class="token punctuation">{</span>
	selector<span class="token punctuation">:</span> <span class="token string">'mean-app'</span><span class="token punctuation">,</span>
	template<span class="token punctuation">:</span> <span class="token string">'&lt;h1&gt;Lorem ipsum&lt;/h1&gt;'</span>
<span class="token punctuation">}</span><span class="token punctuation">)</span>
<span class="token keyword">export</span> <span class="token keyword">class</span> <span class="token class-name">AppComponent</span> <span class="token punctuation">{</span> <span class="token punctuation">}</span>
</code></pre>
<p>⇒ Permet de créer une balise <code>&lt;mean-app&gt;</code> dans le code HTML qui sera remplacée par <code>&lt;h1&gt;Lorem ipsum&lt;/h1&gt;</code>.</p>
<h4 id="templates">Templates</h4>
<p>Les <strong>templates</strong> permettent de rendre la vue du composant.</p>
<pre class=" language-javascript"><code class="prism  language-javascript"><span class="token keyword">import</span> <span class="token punctuation">{</span> Component <span class="token punctuation">}</span> <span class="token keyword">from</span> <span class="token string">'@angular/core'</span><span class="token punctuation">;</span>

@<span class="token function">Component</span><span class="token punctuation">(</span><span class="token punctuation">{</span>
	selector<span class="token punctuation">:</span> <span class="token string">'mean-app'</span><span class="token punctuation">,</span>
	templateUrl<span class="token punctuation">:</span> <span class="token string">'app.template.html'</span>
<span class="token punctuation">}</span><span class="token punctuation">)</span>
<span class="token keyword">export</span> <span class="token keyword">class</span> <span class="token class-name">AppComponent</span> <span class="token punctuation">{</span><span class="token punctuation">}</span>
</code></pre>
<h3 id="liaison-de-données-data-binding">Liaison de données (data binding)</h3>
<p>Angular permet la liaison de données sophistiquées.</p>
<h4 id="interpolation-binding">Interpolation binding</h4>
<p>L’interpolation lie une valeur d’une propriété de classe avec un placeholder du template renseigné entre doubles accolades.</p>
<pre class=" language-javascript"><code class="prism  language-javascript"><span class="token keyword">import</span> <span class="token punctuation">{</span> Component <span class="token punctuation">}</span> <span class="token keyword">from</span> <span class="token string">'@angular/core'</span><span class="token punctuation">;</span>

@<span class="token function">Component</span><span class="token punctuation">(</span><span class="token punctuation">{</span>
	selector<span class="token punctuation">:</span> <span class="token string">'mean-app'</span><span class="token punctuation">,</span>
	template<span class="token punctuation">:</span> <span class="token template-string"><span class="token string">`&lt;h1&gt;{{title}}&lt;/h1&gt;`</span></span>
<span class="token punctuation">}</span><span class="token punctuation">)</span>
<span class="token keyword">export</span> <span class="token keyword">class</span> <span class="token class-name">AppComponent</span> <span class="token punctuation">{</span>
	title <span class="token operator">=</span> <span class="token string">'Mon Application'</span><span class="token punctuation">;</span>
<span class="token punctuation">}</span>
</code></pre>
<p>⇒ Facilite énormément la mise en place d’une structure MVC.</p>
<h4 id="property-binding">Property binding</h4>
<p>L’élément entre crochets va conditionner le comportement d’un élément HTML.</p>
<pre class=" language-javascript"><code class="prism  language-javascript"><span class="token keyword">import</span> <span class="token punctuation">{</span> Component <span class="token punctuation">}</span> <span class="token keyword">from</span> <span class="token string">'@angular/core'</span><span class="token punctuation">;</span>

@<span class="token function">Component</span><span class="token punctuation">(</span><span class="token punctuation">{</span>
	selector<span class="token punctuation">:</span> <span class="token string">'mean-app'</span><span class="token punctuation">,</span>
	template<span class="token punctuation">:</span> <span class="token template-string"><span class="token string">`&lt;button [disabled]="isButtonDisabled"&gt;My Button&lt;/button&gt;`</span></span>
<span class="token punctuation">}</span><span class="token punctuation">)</span>
<span class="token keyword">export</span> <span class="token keyword">class</span> <span class="token class-name">AppComponent</span> <span class="token punctuation">{</span>
	isButtonDisabled <span class="token operator">=</span> <span class="token boolean">true</span><span class="token punctuation">;</span>
<span class="token punctuation">}</span>
</code></pre>
<p>/!\ Différent de <code>&lt;button disabled="{{isButtonDisabled}}"&gt;My Button&lt;/button&gt;</code> (CF 13)</p>
<h4 id="event-binding">Event binding</h4>
<p>Un nom d’événement peut être renseigné entre parenthèses, son comportement est défini dans la classe.</p>
<pre class=" language-javascript"><code class="prism  language-javascript"><span class="token keyword">import</span> <span class="token punctuation">{</span> Component <span class="token punctuation">}</span> <span class="token keyword">from</span> <span class="token string">'@angular/core'</span><span class="token punctuation">;</span>

@<span class="token function">Component</span><span class="token punctuation">(</span><span class="token punctuation">{</span>
	selector<span class="token punctuation">:</span> <span class="token string">'mean-app'</span><span class="token punctuation">,</span>
	template<span class="token punctuation">:</span> <span class="token template-string"><span class="token string">`&lt;button (click)="showMessage()"&gt;Show Message&lt;/button&gt;`</span></span>
<span class="token punctuation">}</span><span class="token punctuation">)</span>
<span class="token keyword">export</span> <span class="token keyword">class</span> <span class="token class-name">AppComponent</span> <span class="token punctuation">{</span>
	<span class="token function">showMessage</span><span class="token punctuation">(</span><span class="token punctuation">)</span> <span class="token punctuation">{</span>
		<span class="token function">alert</span><span class="token punctuation">(</span><span class="token string">'This is a message!'</span><span class="token punctuation">)</span>
	<span class="token punctuation">}</span>
<span class="token punctuation">}</span>
</code></pre>
<h4 id="liaison-bidirectionnelle">Liaison bidirectionnelle</h4>
<pre class=" language-javascript"><code class="prism  language-javascript"><span class="token keyword">import</span> <span class="token punctuation">{</span> Component <span class="token punctuation">}</span> <span class="token keyword">from</span> <span class="token string">'@angular/core'</span><span class="token punctuation">;</span>

@<span class="token function">Component</span><span class="token punctuation">(</span><span class="token punctuation">{</span>
	selector<span class="token punctuation">:</span> <span class="token string">'mean-app'</span><span class="token punctuation">,</span>
	template<span class="token punctuation">:</span> <span class="token template-string"><span class="token string">`&lt;h1&gt;Hello {{name}}&lt;/h1&gt;&lt;br&gt;&lt;input [(ngModel)]="name"&gt;`</span></span>
<span class="token punctuation">}</span><span class="token punctuation">)</span>
<span class="token keyword">export</span> <span class="token keyword">class</span> <span class="token class-name">AppComponent</span> <span class="token punctuation">{</span>
	name <span class="token operator">=</span> <span class="token string">''</span>
<span class="token punctuation">}</span>
</code></pre>
<p>Une modification dans la valeur de <code>name</code> est répercutée dans l’attribut de l’<code>input</code> et réciproquement.</p>
<p>⇒ <code>ngModel</code> est une <strong>directive</strong>.</p>

