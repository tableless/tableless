---
title: Criando um Menu Horizontal com CSS
author: Diego Eis
type: post
date: 2007-12-06
excerpt: Aprenda como criar um menu horizontal padrão com CSS.
url: /criando-um-menu-horizontal-com-css/
aktt_notify_twitter:
  - no
tweetbackscheck:
  - 1356458897
shorturls:
  - 'a:3:{s:9:"permalink";s:58:"http://tableless.com.br/criando-um-menu-horizontal-com-css";s:7:"tinyurl";s:26:"http://tinyurl.com/3lmognw";s:4:"isgd";s:19:"http://is.gd/BKWBBP";}'
twittercomments:
  - 'a:0:{}'
dsq_thread_id: 503014507
categories:
  - Artigos
  - CSS
  - O Básico
  - Técnicas e Práticas
tags:
  - aprenda
  - CSS
  - listas
  - menu horizontal
  - Na Prática
  - tecnicas css
  - tutorial

---
Se você não quiser ler, mas ver como fazer, [assista um vídeo][1]. Neste vídeo é mostrado [como fazer um menu horizontal com CSS][1]. E se quiser aprender mais, [visite o Campus Online e cadastre-se grátis][2] para ver vídeos sobre desenvolvimento web.

Quer fazer um **menu horizontal** que seja fácil de personalizar e de fazer manutenção?
  
Siga os passos abaixo e descubra como é fácil.

### Estrutura:

Primeiramente faça um elemento NAV (antigamente usaríamos a tag DIV) e atribua um ID. Neste exemplo nossa NAV se chamará &#8220;menu&#8221;. Dentro desta NAV, faça uma lista com as opções do menu.

<pre class="lang-html">&lt;nav id="menu"&gt;
	&lt;ul&gt;
		&lt;li&gt;&lt;a href="#"&gt;Home&lt;/a&gt;&lt;/li&gt;
		&lt;li&gt;&lt;a href="#"&gt;Produtos&lt;/a&gt;&lt;/li&gt;
		&lt;li&gt;&lt;a href="#"&gt;Missão&lt;/a&gt;&lt;/li&gt;
		&lt;li&gt;&lt;a href="#"&gt;Links&lt;/a&gt;&lt;/li&gt;
		&lt;li&gt;&lt;a href="#"&gt;Contato&lt;/a&gt;&lt;/li&gt;
	&lt;/ul&gt;
&lt;/nav&gt;
</pre>

Há também a possibilidade de utilizar o elemento **<menu>**, mas ainda está em rascunho no W3C.

### Começando a formatação:

Agora que já fizemos a estrutura do menu, vamos formatá-lo com CSS.

Primeiro, para podermos trabalhar melhor, vamos tirar o margin (margin:0px;), o padding (padding:0px;) e os Bullets das opções (list-style:none;) da tag UL. Queremos que o UL seja uma barra de navegação certo? Então vamos fazer ele flutuar à esquerda (float:left), depois damos a ele a largura de 100% (width:100%;), isso fará com que ele vire uma bloco. Veja o código css atribuído à tag UL:

<pre class="lang-css">#menu ul {
	padding:0px;
	margin:0px;
	background-color:#EDEDED;
	list-style:none;
}
</pre>

### Terceiro:

Para o nosso menu ficar horizontal, temos que fazer as suas opções ficarem uma ao lado da outra&#8230; para isso, basta atribuir um display:inline; para a tag LI&#8230; Isso fará todas as opções ficarem em uma linha horizontal:

<pre class="lang-css">#menu ul li { display: inline; }
</pre>

Pronto, as opções já estão na horizontal, mas ainda podemos melhorar adicionando um visual melhor para os links, melhorando a área do click.

### Deixando o menu na horizontal:

Ótimo. Estamos quase acabando nosso menu horizontal, agora falta pouco.
  
Precisamos apenas formatar os links do menu para que eles não fiquem tão próximos um do outro. No css, faça que todos os links que estão dentro da tag LI (#menu ul li a) tenham características de elementos de bloco, mas não quebrem linha, dessa forma conseguimos formatar características como largura, altura, margin, padding como se os links fossem blocos. Agora, dê um espaço entre a borda do menu e o texto, para isso use o padding (padding: 2px 10px;).

Você pode aproveitar para definir o &#8220;visual&#8221; que deverá ter o link: cor de fundo, letra, etc&#8230;

Veja o código css que escrevemos neste passo:

<pre class="lang-css">#menu ul li a {
	padding: 2px 10px;
	display: inline-block;

	/* visual do link */
	background-color:#EDEDED;
	color: #333;
	text-decoration: none;
	border-bottom:3px solid #EDEDED;
}
</pre>

### Vamos ver no que deu!

Para finalizar, vamos apenas definir o que deverá acontecer com o link quando o usuário passar o mouse. Este passo dispensa explicações.

<pre class="lang-css">#menu ul li a:hover {
	background-color:#D6D6D6;
	color: #6D6D6D;
	border-bottom:3px solid #EA0000;
}
</pre>

Essa é a forma resumida e simples sobre como fazemos todos os menus horizontais da face da terra.

 [1]: http://tableless.com.br/video-menu-horizontal-em-5-minutos
 [2]: http://campus.tableless.com.br/