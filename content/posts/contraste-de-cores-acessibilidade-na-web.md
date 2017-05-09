---
title: Contraste de cores – Acessibilidade na web
author: Orivelton Cesar
type: post
date: 2017-02-01
url: /contraste-de-cores-acessibilidade-na-web/
categories:
  - Acessibilidade
  - CSS3
  - Semântica
  - UX
tags:
  - acessibilidade
  - contraste de cores
  - html5
  - JavaScript

---
Nesse post vou explicar uma das opções de como fazer um contraste de cores, existe diretrizes de acessibilidade da <a href="https://www.w3.org/Translations/WCAG20-pt-PT/" target="_blank">WCAG 2.0</a> que explica o nível aceitável de contraste de cores esperadas em um site, veja nesse <a href="https://www.w3.org/TR/WCAG20/#visual-audio-contrast" target="_blank">link</a>.

## Proposta

Criar um contraste de cores em três níveis (Branco, Preto e Azul) usando HTML5, CSS3, Javascript (Puro), Node e o Cookie do navegado para guarda o contraste escolhido.

<img class="alignnone size-full wp-image-56600" src="uploads/2016/12/html5-css-javascript-logos.png" alt="html5-css-javascript-logos" width="1267" height="287" />

## Como será feito

  * Em uma página teremos quatro links em que o usuário vai escolher (Preto, branco, azul ou sem contraste).
  * No evento de click vamos passar para o javascript um valor do atributo &#8216;data-contraste&#8217;.
  * Vai ser adicionar na tag &#8216;body&#8217; um &#8216;id&#8217; para o CSS fazer toda a mágica de trocar as cores da página.
  * Vai ser guardado no cookie a opção selecionada.

Veja como vai ficar;

<img class="alignnone wp-image-56620" src="uploads/2016/12/contraste-de-cores.gif" alt="contraste-de-cores" width="484" height="264" />

  * Então&#8230;

<img class="alignnone wp-image-56615" src="uploads/2016/12/ThomasCook_tagline.jpg" alt="ThomasCook_tagline_hori_cmyk" width="479" height="137" />

* * *

## HTML

O HTML para esse tipo de projeto é de extrema necessidade ser no mínimo validado pelo [W3C][1] e ter nível &#8220;AAA&#8221; em alguma ferramenta de análise de acessibilidade, no caso eu usei o [Accessmonitor][2], já usando a WCAG 2.0.

A atenção na contrução do HTML vai determinar se o usuário acessível vai ter uma boa experiência no seu site ou não.

* * *

<pre>&lt;!DOCTYPE html&gt;
&lt;html lang="pt-BR"&gt;
 &lt;head&gt;
 &lt;meta charset="utf-8"&gt;
 &lt;title&gt;Artigo contraste de cores&lt;/title&gt;
 &lt;link rel="stylesheet" href="css/style.css"&gt;
 &lt;/head&gt;
 &lt;body&gt;
 &lt;div class="row row-header"&gt;
 &lt;div class="container"&gt;
 &lt;nav&gt;
 &lt;ul&gt;
 &lt;li&gt;
 &lt;a href="#content" title="Ir para o Conteúdo"&gt;Ir para o Conteúdo&lt;/a&gt;
 &lt;/li&gt;
 &lt;li&gt;
 &lt;a href="#" title="Ir para o Topo"&gt;Ir para o Topo&lt;/a&gt;
 &lt;/li&gt;
 &lt;li&gt;
 &lt;a href="#footer" title="Ir para o Rodapé"&gt;Ir para o Rodapé&lt;/a&gt;
 &lt;/li&gt;
 &lt;li&gt;
 &lt;a href="#" data-contraste="0" title="Sem Contraste"&gt;Sem Contraste&lt;/a&gt;
 &lt;/li&gt;
 &lt;li&gt;
 &lt;a href="#" data-contraste="1" title="Contraste Branco"&gt;Contraste Branco&lt;/a&gt;
 &lt;/li&gt;
 &lt;li&gt;
 &lt;a href="#" data-contraste="2" title="Contraste Preto"&gt;Contraste Preto&lt;/a&gt;
 &lt;/li&gt;
 &lt;li&gt;
 &lt;a href="#" data-contraste="3" title="Contraste Azul"&gt;Contraste Azul&lt;/a&gt;
 &lt;/li&gt;
 &lt;/ul&gt;
 &lt;/nav&gt;
 &lt;/div&gt;
 &lt;!-- End - .container--&gt;
 &lt;/div&gt;
 &lt;!-- End - .row--&gt;
 &lt;div class="row row-top"&gt;
 &lt;div class="container"&gt;
 &lt;strong&gt;Front End Developer&lt;/strong&gt;
 &lt;/div&gt;
 &lt;/div&gt;
 &lt;div class="row row-banner"&gt;
 &lt;div class="container"&gt;
 &lt;h1&gt;Hi my names is &lt;span&gt;Orivelton&lt;/span&gt;&lt;/h1&gt;
 &lt;img src="img/avatar.png" alt="Avatar Front End" class="avatar"&gt;
 &lt;img src="img/avatar-preto.png" alt="Oculos do avatar" class="oculos"&gt;
 &lt;/div&gt;
 &lt;/div&gt;
 &lt;div class="row row-content"&gt;
 &lt;article class="container" id="content"&gt;
 &lt;div class="box"&gt;
 &lt;h2&gt;Html5&lt;/h2&gt;
 &lt;i&gt;★★★★★&lt;/i&gt;
 &lt;p&gt;
 Mussum Ipsum, cacilds vidis litro abertis. Manduma pindureta quium dia nois paga.
 Nec orci ornare consequat. Praesent lacinia ultrices consectetur. Sed non ipsum felis.
 Si num tem leite então bota uma pinga aí cumpadi! Atirei o pau no gatis, per gatis num morreus.
 &lt;/p&gt;
 &lt;/div&gt;
 &lt;div class="box"&gt;
 &lt;h2&gt;Css3&lt;/h2&gt;
 &lt;i&gt;★★★★★&lt;/i&gt;
 &lt;p&gt;
 Mussum Ipsum, cacilds vidis litro abertis. Manduma pindureta quium dia nois paga.
 Nec orci ornare consequat. Praesent lacinia ultrices consectetur. Sed non ipsum felis.
 Si num tem leite então bota uma pinga aí cumpadi! Atirei o pau no gatis, per gatis num morreus.
 &lt;/p&gt;
 &lt;/div&gt;
 &lt;div class="box"&gt;
 &lt;h2&gt;Javascript&lt;/h2&gt;
 &lt;i&gt;★★★★&lt;/i&gt;
 &lt;p&gt;
 Mussum Ipsum, cacilds vidis litro abertis. Manduma pindureta quium dia nois paga.
 Nec orci ornare consequat. Praesent lacinia ultrices consectetur. Sed non ipsum felis.
 Si num tem leite então bota uma pinga aí cumpadi! Atirei o pau no gatis, per gatis num morreus.
 &lt;/p&gt;
 &lt;/div&gt;
 &lt;div class="box"&gt;
 &lt;h2&gt;Typescript&lt;/h2&gt;
 &lt;i&gt;★★★★&lt;/i&gt;
 &lt;p&gt;
 Mussum Ipsum, cacilds vidis litro abertis. Manduma pindureta quium dia nois paga.
 Nec orci ornare consequat. Praesent lacinia ultrices consectetur. Sed non ipsum felis.
 Si num tem leite então bota uma pinga aí cumpadi! Atirei o pau no gatis, per gatis num morreus.
 &lt;/p&gt;
 &lt;/div&gt;
 &lt;/article&gt;
 &lt;/div&gt;
 &lt;footer id="footer"&gt;
 Copyright (c) 2016 Copyright Holder All Rights Reserved.
 &lt;/footer&gt;
 &lt;script type="text/javascript" src="js/contraste.js"&gt;&lt;/script&gt;
 &lt;/body&gt;
&lt;/html&gt;</pre>

Umas das recomendações da WCAG 2.0 é que o primeiro link do site leve para o conteúdo principal, com isso você já ganha uns pontinhos na ferramenta de análise de acessibilidade.

* * *

## CSS

O CSS é muito importante, se possível não usar CSS inline, a utilização de unidades relativas (EM, %,  REM) na escrita do CSS melhora a acessibilidade. Validar o CSS vai apontar erros que deixamos passar, para isso temos a ferramenta de análise da W3C o [CSS Validation Service][3]. Não vou postar aqui o CSS, mas logo abaixo vou deixar o link do projeto completo ;).

* * *

# Javascript

Nesse post resolvi usar javascript puro, pois se trata de uma aplicação simples e não haveria a necessidade de usar JQuery ou alguma lib ou Framework e também eu amo javascript puro, acho bem desafiador \0/.

Esse Javascript modularizei em três blocos.

### 1 &#8211; A escolha do contraste no click do link

<pre>//Selecionando os links de contraste
var linksContraste = document.querySelectorAll('nav a[data-contraste]');

//Function click passando o valor do data-contraste para a function contraste setar o Id no body
linksContraste.forEach(linksContraste =&gt; linksContraste.addEventListener('click', function() {
 var dataContraste = this.dataset.contraste; // pegando o data-contraste da tag 'a'
 contraste(dataContraste); // Chamando a function contraste com um parâmetro passado pelo data-contraste da tag 'a'
 }
));</pre>

### 2 &#8211; A Função de setar o contraste.

<pre>function contraste(dataContraste) {
 var setId;
 //Verificação de qual contraste foi selecionado
 if (dataContraste == 1) {
 setId = 'contrasteBranco';
 } else if (dataContraste == 2) {
 setId = 'contrastePreto';
 } else if (dataContraste == 3) {
 setId = 'contrasteAzul';
 } else {
 setId = '';
 }
 // setando o ID do contraste escolhido no body
 document.querySelector("body").setAttribute("id", setId);
 // Guardando o cookie do contraste
 document.cookie = "contraste=" + setId + "";
}</pre>

### 3 &#8211; A verificação do cookie gravado

<pre>// Verificação do cookie
var cookieContrasteBranco = document.cookie.indexOf('contrasteBranco');
var cookieContrastePreto = document.cookie.indexOf('contrastePreto');
var cookieContrasteAzul = document.cookie.indexOf('contrasteAzul');

//Verificando o cookie setado anteriormente
var cookieTrue = '';
if (cookieContrasteBranco != -1) {
 cookieTrue = 1;
} else if (cookieContrastePreto != -1) {
 cookieTrue = 2;
} else if (cookieContrasteAzul != -1) {
 cookieTrue = 3;
} else {
 cookieTrue = '';
}
//Chamando a function contraste com o valor do cookie guardado
contraste(cookieTrue);</pre>

* * *

## Node + Cookie

Node? sim, usaremos o Node para subir um servidor, pois não da pra guardar cookie sem um servidor, vamos precisar usar o Node, mas é super simples.

Não sabe usar? Não sabe o que é? tem um poste aqui muito bom que vai te dar o caminho das pedras, nesse [link][4].

No site [NPMJS ][5]temos um servidor em que iremos utilizar, abra seu Node e manda essa;

<pre>npm install http-server -g</pre>

Pronto, o resultado será esse;

<img class="alignnone size-full wp-image-56612" src="uploads/2016/12/Capture.png" alt="capture" width="636" height="48" />

Agora navegando com o Node até a pasta do seu projeto;

<pre>http-server</pre>

Ok, você já tem um servidor no ar, utilize um dos endereços http listados e abra no seu navegador de preferência (<del><em>Chrome</em></del>);

<pre><img class="alignnone wp-image-56613" src="uploads/2016/12/Capture-1.png" alt="capture" width="640" height="134" /></pre>

Já está tudo pronto, com o servidor no ar já podemos gravar no cookie a escolha do contraste selecionada pelo usuário, isso vai evitar que o usuário atualize a página e carregue a página sem o contraste escolhido.

já podemos verificar o cookie guardado depois do click no link

<img class="alignnone size-full wp-image-56617" src="uploads/2016/12/Capture-2.png" alt="capture" width="931" height="509" />

Com esse valor guardado no cookie o passo 3 vai funcionar perfeitamente, setando o contraste escolhido anteriormente ao recarregar a página.

* * *

Veja o projeto completo no [Nesse post vou explicar uma das opções de como fazer um contraste de cores, existe diretrizes de acessibilidade da <a href="https://www.w3.org/Translations/WCAG20-pt-PT/" target="_blank">WCAG 2.0</a> que explica o nível aceitável de contraste de cores esperadas em um site, veja nesse <a href="https://www.w3.org/TR/WCAG20/#visual-audio-contrast" target="_blank">link</a>.

## Proposta

Criar um contraste de cores em três níveis (Branco, Preto e Azul) usando HTML5, CSS3, Javascript (Puro), Node e o Cookie do navegado para guarda o contraste escolhido.

<img class="alignnone size-full wp-image-56600" src="uploads/2016/12/html5-css-javascript-logos.png" alt="html5-css-javascript-logos" width="1267" height="287" />

## Como será feito

  * Em uma página teremos quatro links em que o usuário vai escolher (Preto, branco, azul ou sem contraste).
  * No evento de click vamos passar para o javascript um valor do atributo &#8216;data-contraste&#8217;.
  * Vai ser adicionar na tag &#8216;body&#8217; um &#8216;id&#8217; para o CSS fazer toda a mágica de trocar as cores da página.
  * Vai ser guardado no cookie a opção selecionada.

Veja como vai ficar;

<img class="alignnone wp-image-56620" src="uploads/2016/12/contraste-de-cores.gif" alt="contraste-de-cores" width="484" height="264" />

  * Então&#8230;

<img class="alignnone wp-image-56615" src="uploads/2016/12/ThomasCook_tagline.jpg" alt="ThomasCook_tagline_hori_cmyk" width="479" height="137" />

* * *

## HTML

O HTML para esse tipo de projeto é de extrema necessidade ser no mínimo validado pelo [W3C][1] e ter nível &#8220;AAA&#8221; em alguma ferramenta de análise de acessibilidade, no caso eu usei o [Accessmonitor][2], já usando a WCAG 2.0.

A atenção na contrução do HTML vai determinar se o usuário acessível vai ter uma boa experiência no seu site ou não.

* * *

<pre>&lt;!DOCTYPE html&gt;
&lt;html lang="pt-BR"&gt;
 &lt;head&gt;
 &lt;meta charset="utf-8"&gt;
 &lt;title&gt;Artigo contraste de cores&lt;/title&gt;
 &lt;link rel="stylesheet" href="css/style.css"&gt;
 &lt;/head&gt;
 &lt;body&gt;
 &lt;div class="row row-header"&gt;
 &lt;div class="container"&gt;
 &lt;nav&gt;
 &lt;ul&gt;
 &lt;li&gt;
 &lt;a href="#content" title="Ir para o Conteúdo"&gt;Ir para o Conteúdo&lt;/a&gt;
 &lt;/li&gt;
 &lt;li&gt;
 &lt;a href="#" title="Ir para o Topo"&gt;Ir para o Topo&lt;/a&gt;
 &lt;/li&gt;
 &lt;li&gt;
 &lt;a href="#footer" title="Ir para o Rodapé"&gt;Ir para o Rodapé&lt;/a&gt;
 &lt;/li&gt;
 &lt;li&gt;
 &lt;a href="#" data-contraste="0" title="Sem Contraste"&gt;Sem Contraste&lt;/a&gt;
 &lt;/li&gt;
 &lt;li&gt;
 &lt;a href="#" data-contraste="1" title="Contraste Branco"&gt;Contraste Branco&lt;/a&gt;
 &lt;/li&gt;
 &lt;li&gt;
 &lt;a href="#" data-contraste="2" title="Contraste Preto"&gt;Contraste Preto&lt;/a&gt;
 &lt;/li&gt;
 &lt;li&gt;
 &lt;a href="#" data-contraste="3" title="Contraste Azul"&gt;Contraste Azul&lt;/a&gt;
 &lt;/li&gt;
 &lt;/ul&gt;
 &lt;/nav&gt;
 &lt;/div&gt;
 &lt;!-- End - .container--&gt;
 &lt;/div&gt;
 &lt;!-- End - .row--&gt;
 &lt;div class="row row-top"&gt;
 &lt;div class="container"&gt;
 &lt;strong&gt;Front End Developer&lt;/strong&gt;
 &lt;/div&gt;
 &lt;/div&gt;
 &lt;div class="row row-banner"&gt;
 &lt;div class="container"&gt;
 &lt;h1&gt;Hi my names is &lt;span&gt;Orivelton&lt;/span&gt;&lt;/h1&gt;
 &lt;img src="img/avatar.png" alt="Avatar Front End" class="avatar"&gt;
 &lt;img src="img/avatar-preto.png" alt="Oculos do avatar" class="oculos"&gt;
 &lt;/div&gt;
 &lt;/div&gt;
 &lt;div class="row row-content"&gt;
 &lt;article class="container" id="content"&gt;
 &lt;div class="box"&gt;
 &lt;h2&gt;Html5&lt;/h2&gt;
 &lt;i&gt;★★★★★&lt;/i&gt;
 &lt;p&gt;
 Mussum Ipsum, cacilds vidis litro abertis. Manduma pindureta quium dia nois paga.
 Nec orci ornare consequat. Praesent lacinia ultrices consectetur. Sed non ipsum felis.
 Si num tem leite então bota uma pinga aí cumpadi! Atirei o pau no gatis, per gatis num morreus.
 &lt;/p&gt;
 &lt;/div&gt;
 &lt;div class="box"&gt;
 &lt;h2&gt;Css3&lt;/h2&gt;
 &lt;i&gt;★★★★★&lt;/i&gt;
 &lt;p&gt;
 Mussum Ipsum, cacilds vidis litro abertis. Manduma pindureta quium dia nois paga.
 Nec orci ornare consequat. Praesent lacinia ultrices consectetur. Sed non ipsum felis.
 Si num tem leite então bota uma pinga aí cumpadi! Atirei o pau no gatis, per gatis num morreus.
 &lt;/p&gt;
 &lt;/div&gt;
 &lt;div class="box"&gt;
 &lt;h2&gt;Javascript&lt;/h2&gt;
 &lt;i&gt;★★★★&lt;/i&gt;
 &lt;p&gt;
 Mussum Ipsum, cacilds vidis litro abertis. Manduma pindureta quium dia nois paga.
 Nec orci ornare consequat. Praesent lacinia ultrices consectetur. Sed non ipsum felis.
 Si num tem leite então bota uma pinga aí cumpadi! Atirei o pau no gatis, per gatis num morreus.
 &lt;/p&gt;
 &lt;/div&gt;
 &lt;div class="box"&gt;
 &lt;h2&gt;Typescript&lt;/h2&gt;
 &lt;i&gt;★★★★&lt;/i&gt;
 &lt;p&gt;
 Mussum Ipsum, cacilds vidis litro abertis. Manduma pindureta quium dia nois paga.
 Nec orci ornare consequat. Praesent lacinia ultrices consectetur. Sed non ipsum felis.
 Si num tem leite então bota uma pinga aí cumpadi! Atirei o pau no gatis, per gatis num morreus.
 &lt;/p&gt;
 &lt;/div&gt;
 &lt;/article&gt;
 &lt;/div&gt;
 &lt;footer id="footer"&gt;
 Copyright (c) 2016 Copyright Holder All Rights Reserved.
 &lt;/footer&gt;
 &lt;script type="text/javascript" src="js/contraste.js"&gt;&lt;/script&gt;
 &lt;/body&gt;
&lt;/html&gt;</pre>

Umas das recomendações da WCAG 2.0 é que o primeiro link do site leve para o conteúdo principal, com isso você já ganha uns pontinhos na ferramenta de análise de acessibilidade.

* * *

## CSS

O CSS é muito importante, se possível não usar CSS inline, a utilização de unidades relativas (EM, %,  REM) na escrita do CSS melhora a acessibilidade. Validar o CSS vai apontar erros que deixamos passar, para isso temos a ferramenta de análise da W3C o [CSS Validation Service][3]. Não vou postar aqui o CSS, mas logo abaixo vou deixar o link do projeto completo ;).

* * *

# Javascript

Nesse post resolvi usar javascript puro, pois se trata de uma aplicação simples e não haveria a necessidade de usar JQuery ou alguma lib ou Framework e também eu amo javascript puro, acho bem desafiador \0/.

Esse Javascript modularizei em três blocos.

### 1 &#8211; A escolha do contraste no click do link

<pre>//Selecionando os links de contraste
var linksContraste = document.querySelectorAll('nav a[data-contraste]');

//Function click passando o valor do data-contraste para a function contraste setar o Id no body
linksContraste.forEach(linksContraste =&gt; linksContraste.addEventListener('click', function() {
 var dataContraste = this.dataset.contraste; // pegando o data-contraste da tag 'a'
 contraste(dataContraste); // Chamando a function contraste com um parâmetro passado pelo data-contraste da tag 'a'
 }
));</pre>

### 2 &#8211; A Função de setar o contraste.

<pre>function contraste(dataContraste) {
 var setId;
 //Verificação de qual contraste foi selecionado
 if (dataContraste == 1) {
 setId = 'contrasteBranco';
 } else if (dataContraste == 2) {
 setId = 'contrastePreto';
 } else if (dataContraste == 3) {
 setId = 'contrasteAzul';
 } else {
 setId = '';
 }
 // setando o ID do contraste escolhido no body
 document.querySelector("body").setAttribute("id", setId);
 // Guardando o cookie do contraste
 document.cookie = "contraste=" + setId + "";
}</pre>

### 3 &#8211; A verificação do cookie gravado

<pre>// Verificação do cookie
var cookieContrasteBranco = document.cookie.indexOf('contrasteBranco');
var cookieContrastePreto = document.cookie.indexOf('contrastePreto');
var cookieContrasteAzul = document.cookie.indexOf('contrasteAzul');

//Verificando o cookie setado anteriormente
var cookieTrue = '';
if (cookieContrasteBranco != -1) {
 cookieTrue = 1;
} else if (cookieContrastePreto != -1) {
 cookieTrue = 2;
} else if (cookieContrasteAzul != -1) {
 cookieTrue = 3;
} else {
 cookieTrue = '';
}
//Chamando a function contraste com o valor do cookie guardado
contraste(cookieTrue);</pre>

* * *

## Node + Cookie

Node? sim, usaremos o Node para subir um servidor, pois não da pra guardar cookie sem um servidor, vamos precisar usar o Node, mas é super simples.

Não sabe usar? Não sabe o que é? tem um poste aqui muito bom que vai te dar o caminho das pedras, nesse [link][4].

No site [NPMJS ][5]temos um servidor em que iremos utilizar, abra seu Node e manda essa;

<pre>npm install http-server -g</pre>

Pronto, o resultado será esse;

<img class="alignnone size-full wp-image-56612" src="uploads/2016/12/Capture.png" alt="capture" width="636" height="48" />

Agora navegando com o Node até a pasta do seu projeto;

<pre>http-server</pre>

Ok, você já tem um servidor no ar, utilize um dos endereços http listados e abra no seu navegador de preferência (<del><em>Chrome</em></del>);

<pre><img class="alignnone wp-image-56613" src="uploads/2016/12/Capture-1.png" alt="capture" width="640" height="134" /></pre>

Já está tudo pronto, com o servidor no ar já podemos gravar no cookie a escolha do contraste selecionada pelo usuário, isso vai evitar que o usuário atualize a página e carregue a página sem o contraste escolhido.

já podemos verificar o cookie guardado depois do click no link

<img class="alignnone size-full wp-image-56617" src="uploads/2016/12/Capture-2.png" alt="capture" width="931" height="509" />

Com esse valor guardado no cookie o passo 3 vai funcionar perfeitamente, setando o contraste escolhido anteriormente ao recarregar a página.

* * *

Veja o projeto completo no ][6] e no [github][7].

 [1]: https://validator.w3.org/
 [2]: http://www.acessibilidade.gov.pt/accessmonitor/
 [3]: https://jigsaw.w3.org/css-validator/
 [4]: https://tableless.com.br/o-que-nodejs-primeiros-passos-com-node-js/
 [5]: https://www.npmjs.com/package/http-server
 [6]: http://codepen.io/orivelton/pen/XNymQp
 [7]: https://github.com/orivelton10/contraste-de-cores