---
title: Conheça o Vue.js, um framework javascript para criação de componentes web reativos
author: Daniel Schmitz
type: post
date: 2016-08-08
url: /conheca-o-vue-js-um-framework-javascript-para-criacao-de-componentes-web-reativos/
categories:
  - JavaScript

---
Venho acompanhando a evolução de diversos frameworks &#8220;frontend&#8221; ao longo dos últimos anos, e sendo um entusiasta ao estudá-los e criar conteúdo sobre eles. Talvez o primeiro framework que tenhamos mais destaque (após a geração jQuery) foi o AngularJS, que está forte até hoje, mas já possui o seu sucessor, o Angular 2 (atualmente na versão beta). Também temos o React e o Aurelia nesse jogo, e além de todos estes, temos o framework que iremos abordar neste artigo, o Vue.js (pronuncia-se view).

O Vue.js destaca-se pela sua simplicidade em executar as mesmas tarefas dos outros frameworks. Nele você possui os mesmos conceitos que um framework reativo possui, como data bind, two way, events, criação de componentes, entre outros. Mas então, porque ter mais um framework com os mesmos processos? O resultado é a simplicidade que temos ao trabalhar com Vue.js, que veremos ao longo deste artigo.

Neste artigo usaremos o [JSFiddle][1] como ferramenta para compreender os processos básicos do Vue, então não será necessário, a princípio, instalar nada no seu sistema. Abra o jsfiddle em outra aba do seu navegador e acesse o menu JavaScript, conforme a imagem a seguir, escolha o framework Vue 1.0 para ser carregado:

<img src="http://tableless.com.br/uploads/2016/06/2016-06-28-12_23_29-Create-a-new-fiddle-JSFiddle.png" alt="JSFiddle+Vue" width="625" height="623" class="aligncenter size-full wp-image-54927" />

## Estrutura inicial

Pelo jsfiddle, o Vue pode ser usado usando as áreas HTML e JavaScript. Na parte JavaScript, o código básico para utilizar o Vue é instanciar a própria classe Vue, repassando inicialmente o parâmetro `el`, que determina em qual elemento html o Vue irá observar.

Basicamente, temos:

HTML

<pre class="lang-htm">&lt;div id="app"&gt;

&lt;/div&gt;
</pre>

e o Javascript:

<pre class="lang-javascript">new Vue({
  el: '#app'
})
</pre>

## Data Bind

O databind permite ligar um elemento do HTML à uma variável do JS. Neste ponto, para atualizar a variável na página não é necessário percorrer a DOM do elemento HTML e alterar o seu valor. Basta alterar o valor da variável JavaScript, que o Vue irá cuidar da atualização no elemento HTML. Chamamos este comportamento de design reativo, ou seja, o design da página reflete a configuração das variáveis.

Vamos então criar um pequeno Hello World, veja:

HTML

<pre class="lang-html">&lt;div id="app"&gt;
 {{msg}}
&lt;/div&gt;
</pre>

e JavaScript:

<pre class="lang-javascript">new Vue({
  el: '#app',
  data: {
    msg: 'Hello World!'
  }
})
</pre>

A configuração no fiddle fica semelhante a figura a seguir:

<img src="http://tableless.com.br/uploads/2016/06/2016-06-28-14_43_35-Create-a-new-fiddle-JSFiddle.png" alt="2016-06-28 14_43_35-Create a new fiddle - JSFiddle" width="665" height="360" class="aligncenter size-full wp-image-54937" />

Clique no botão **Run** para executar o código. A resposta é exibida na caixa da direta. Neste caso, a mensagem Hello World será exibida.

**Two-Way databing**

O termo Two Way significa que uma variável pode estar ligada a um elemento e este elemento pode alterar a variável, como uma via dupla. No próximo exemplo, vamos criar uma caixa de texto onde você poderá digitar o seu nome, veja:

HTML

<pre class="html" title="html">&lt;div id="app"&gt;
 {{msg}}, {{nome}}
  &lt;br/&gt;
  &lt;input type="text" v-model="nome"&gt;
&lt;/div&gt;
</pre>

e

Javascript

<pre class="lang-javascript">new Vue({
  el: '#app',
  data: {
    msg: 'Hello World',
    nome: 'Fulano'
  }
})
</pre>

O que temos agora é uma nova variável chamada &#8220;nome&#8221;, que esta ligada ao {{nome}} e também ao v-model do input. Quando alteramoso valor do input, a variável nome é alterada também, e a o nome aparece após o Hello World, conforme a figura a seguir:

<img src="http://tableless.com.br/uploads/2016/06/2016-06-28-15_12_15-Create-a-new-fiddle-JSFiddle.png" alt="2016-06-28 15_12_15-Create a new fiddle - JSFiddle" width="591" height="330" class="aligncenter size-full wp-image-54939" />

**Criando uma lista**

É possível iterar entre elementos de um Array no javascript e criar uma lista de elementos em html, conforme o exemplo a seguir:

HTML

<pre class="html" title="html">&lt;div id="app"&gt;
  &lt;ul&gt;
    &lt;li v-for="fruit in fruits"&gt;
      {{ fruit.name }}
    &lt;/li&gt;
  &lt;/ul&gt;
&lt;/div&gt;
</pre>

e

Javascript

<pre class="lang-javascript">new Vue({
  el: '#app',
  data: {
    fruits: [
      { name: 'banana' },
      { name: 'apple' },
      { name: 'orange' }
    ]
  }
})
</pre>

Neste exemplo, a variável `fruits` é um array de objetos, que contém a propriedade `name`. No Html, usamos o elemento `v-for` para realizar um loop no `&lt;li&gt;` repetindo este item para cada elemento do array. A resposta do código é exibida a seguir:

<img src="http://tableless.com.br/uploads/2016/06/2016-06-28-15_20_33-Create-a-new-fiddle-JSFiddle.png" alt="2016-06-28 15_20_33-Create a new fiddle - JSFiddle" width="441" height="365" class="aligncenter size-full wp-image-54942" />

 **Para saber mais** 

Demos um ponta pé inicial exibindo algumas funcionalidades deste framework, mas é claro ainda existe muitos outros pontos , e iremos a seguir exibir algumas urls para que você possa dar prosseguimento ao seus estudos. Fique a vontade também em perguntar.

  * [Venho acompanhando a evolução de diversos frameworks &#8220;frontend&#8221; ao longo dos últimos anos, e sendo um entusiasta ao estudá-los e criar conteúdo sobre eles. Talvez o primeiro framework que tenhamos mais destaque (após a geração jQuery) foi o AngularJS, que está forte até hoje, mas já possui o seu sucessor, o Angular 2 (atualmente na versão beta). Também temos o React e o Aurelia nesse jogo, e além de todos estes, temos o framework que iremos abordar neste artigo, o Vue.js (pronuncia-se view).

O Vue.js destaca-se pela sua simplicidade em executar as mesmas tarefas dos outros frameworks. Nele você possui os mesmos conceitos que um framework reativo possui, como data bind, two way, events, criação de componentes, entre outros. Mas então, porque ter mais um framework com os mesmos processos? O resultado é a simplicidade que temos ao trabalhar com Vue.js, que veremos ao longo deste artigo.

Neste artigo usaremos o [JSFiddle][1] como ferramenta para compreender os processos básicos do Vue, então não será necessário, a princípio, instalar nada no seu sistema. Abra o jsfiddle em outra aba do seu navegador e acesse o menu JavaScript, conforme a imagem a seguir, escolha o framework Vue 1.0 para ser carregado:

<img src="http://tableless.com.br/uploads/2016/06/2016-06-28-12_23_29-Create-a-new-fiddle-JSFiddle.png" alt="JSFiddle+Vue" width="625" height="623" class="aligncenter size-full wp-image-54927" />

## Estrutura inicial

Pelo jsfiddle, o Vue pode ser usado usando as áreas HTML e JavaScript. Na parte JavaScript, o código básico para utilizar o Vue é instanciar a própria classe Vue, repassando inicialmente o parâmetro `el`, que determina em qual elemento html o Vue irá observar.

Basicamente, temos:

HTML

<pre class="lang-htm">&lt;div id="app"&gt;

&lt;/div&gt;
</pre>

e o Javascript:

<pre class="lang-javascript">new Vue({
  el: '#app'
})
</pre>

## Data Bind

O databind permite ligar um elemento do HTML à uma variável do JS. Neste ponto, para atualizar a variável na página não é necessário percorrer a DOM do elemento HTML e alterar o seu valor. Basta alterar o valor da variável JavaScript, que o Vue irá cuidar da atualização no elemento HTML. Chamamos este comportamento de design reativo, ou seja, o design da página reflete a configuração das variáveis.

Vamos então criar um pequeno Hello World, veja:

HTML

<pre class="lang-html">&lt;div id="app"&gt;
 {{msg}}
&lt;/div&gt;
</pre>

e JavaScript:

<pre class="lang-javascript">new Vue({
  el: '#app',
  data: {
    msg: 'Hello World!'
  }
})
</pre>

A configuração no fiddle fica semelhante a figura a seguir:

<img src="http://tableless.com.br/uploads/2016/06/2016-06-28-14_43_35-Create-a-new-fiddle-JSFiddle.png" alt="2016-06-28 14_43_35-Create a new fiddle - JSFiddle" width="665" height="360" class="aligncenter size-full wp-image-54937" />

Clique no botão **Run** para executar o código. A resposta é exibida na caixa da direta. Neste caso, a mensagem Hello World será exibida.

**Two-Way databing**

O termo Two Way significa que uma variável pode estar ligada a um elemento e este elemento pode alterar a variável, como uma via dupla. No próximo exemplo, vamos criar uma caixa de texto onde você poderá digitar o seu nome, veja:

HTML

<pre class="html" title="html">&lt;div id="app"&gt;
 {{msg}}, {{nome}}
  &lt;br/&gt;
  &lt;input type="text" v-model="nome"&gt;
&lt;/div&gt;
</pre>

e

Javascript

<pre class="lang-javascript">new Vue({
  el: '#app',
  data: {
    msg: 'Hello World',
    nome: 'Fulano'
  }
})
</pre>

O que temos agora é uma nova variável chamada &#8220;nome&#8221;, que esta ligada ao {{nome}} e também ao v-model do input. Quando alteramoso valor do input, a variável nome é alterada também, e a o nome aparece após o Hello World, conforme a figura a seguir:

<img src="http://tableless.com.br/uploads/2016/06/2016-06-28-15_12_15-Create-a-new-fiddle-JSFiddle.png" alt="2016-06-28 15_12_15-Create a new fiddle - JSFiddle" width="591" height="330" class="aligncenter size-full wp-image-54939" />

**Criando uma lista**

É possível iterar entre elementos de um Array no javascript e criar uma lista de elementos em html, conforme o exemplo a seguir:

HTML

<pre class="html" title="html">&lt;div id="app"&gt;
  &lt;ul&gt;
    &lt;li v-for="fruit in fruits"&gt;
      {{ fruit.name }}
    &lt;/li&gt;
  &lt;/ul&gt;
&lt;/div&gt;
</pre>

e

Javascript

<pre class="lang-javascript">new Vue({
  el: '#app',
  data: {
    fruits: [
      { name: 'banana' },
      { name: 'apple' },
      { name: 'orange' }
    ]
  }
})
</pre>

Neste exemplo, a variável `fruits` é um array de objetos, que contém a propriedade `name`. No Html, usamos o elemento `v-for` para realizar um loop no `&lt;li&gt;` repetindo este item para cada elemento do array. A resposta do código é exibida a seguir:

<img src="http://tableless.com.br/uploads/2016/06/2016-06-28-15_20_33-Create-a-new-fiddle-JSFiddle.png" alt="2016-06-28 15_20_33-Create a new fiddle - JSFiddle" width="441" height="365" class="aligncenter size-full wp-image-54942" />

 **Para saber mais** 

Demos um ponta pé inicial exibindo algumas funcionalidades deste framework, mas é claro ainda existe muitos outros pontos , e iremos a seguir exibir algumas urls para que você possa dar prosseguimento ao seus estudos. Fique a vontade também em perguntar.

  *][2] 
  * [Guia traduzido para o português][3] 
  *  1º hangout sobre Vue e Vuex </li> 
    
      * [www.vuejs-brasil.com.br][4] &#8211; Blog sobre Vue com conteúdo em português
      * [vuejs-brasil.slack.com][5] &#8211; Comunidade Vue Brasil no Slack
      * [telegram.me/vuejsbrasil][6] &#8211; Comunidade Vue Brasil no Telegram
      * [telegram.me/danielschmitz][7]&#8211; Converse diretamente comigo pelo Telegram</ul>

 [1]: https://jsfiddle.net/
 [2]: http://vuejs.org/guide/installation.html
 [3]: http://vuejs-br.github.io/vuejs.org/guide/
 [4]: http://www.vuejs-brasil.com.br
 [5]: http://vuejs-brasil.slack.com
 [6]: https://telegram.me/vuejsbrasil
 [7]: https://telegram.me/danielschmitz