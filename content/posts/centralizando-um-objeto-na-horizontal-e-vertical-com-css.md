---
title: Centralizando um objeto na Horizontal e Vertical com CSS
authors: Diego Eis
type: post
date: 2007-12-06
excerpt: Saiba como centralizar um objeto na horizontal e vertical apenas com CSS.
url: /centralizando-um-objeto-na-horizontal-e-vertical-com-css/
sponsor: organizze
dsq_thread_id: 503018562
categories:
  - Artigos
  - CSS
  - HTML
  - O Básico
  - Técnicas e Práticas
tags:
  - aprenda
  - centralizando elementos
  - centralizar
  - CSS
  - elementos
  - Na Prática
  - tableless
  - tecnicascss

---
[][1] 

### Objeto no centro da tela

Uma das dúvidas mais freqüentes é esta: Como fazer para que um objeto fique no centro da tela usando css?
  
A resposta está nos passos abaixo!

### Colocando a imagem:

Neste exemplo vamos usar uma imagem, mas você pode perfeitamente usar um div, o processo é o mesmo.
  
Coloque na imagem (ou no div) um nome de ID&#8230; Colocamos neste exemplo o ID com nome &#8220;centro&#8221;.

<pre class="lang-html">&lt;img src="imagem.gif" id="centro" /&gt;
</pre>

### Definindo as dimensões do objeto:

Agora, no css, defina as dimensões do objeto (imagem ou div).
  
Nossa imagem tem 100 x 100 px&#8217;s, então vamos definir no css que a largura será de 100px (width:100px;) e que a altura também será de 100px (height:100px;).

<pre class="lang-css">#centro {
width:100px;
height:100px;
}
</pre>

### Alinhando:

Estamos quase no final, você pode perceber que o objeto está um pouco desalinhado do centro. Vamos agora posicioná-lo&#8230; É aqui começa o truque.
  
Defina para nosso objeto, uma posição absoluta (position:absolute;), ele deverá ficar a 50% de distância do topo (top:50%;) e 50% de distância do lado esquerdo do documento (left:50%;).
  
O css não usa o centro do objeto como referência para o posicionamento, mas sim as extremidades, portanto, o que ficará no centro depois deste código, será o canto esquerdo superior do objeto.

<pre class="lang-css">#centro {
width:100px;
height:100px;
position:absolute;
top:50%;
left:50%;
}
</pre>

### O grande final:

Eis o truque para tirar a diferença, não é nada de outro mundo.
  
Você irá definir ao objeto duas margens negativas&#8230; a margem do topo (margin-top) e a margem da esquerda (margin-left). Na margem do topo, você simplesmente colocará um valor negativo, este valor será a metade da altura do objeto, neste caso, será -50px (margin-top:-50px;) e no lado esquerdo você fará a mesma coisa, mas o valor será a metade da largura do objeto, neste caso -50px (margin-left:-50px;).

<pre class="lang-css">#centro {
	width:100px;
	height:100px;
	position:absolute;
	top:50%;
	left:50%;
	margin-top:-50px;
	margin-left:-50px;
}
</pre>

 [1]: https://tableless.com.br/centralizando-conteudo-na-vertical-e-horizontal-com-css-flexbox/