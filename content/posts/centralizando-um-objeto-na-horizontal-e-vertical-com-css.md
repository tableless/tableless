---
title: Centralizando um objeto na Horizontal e Vertical com CSS
author: Diego Eis
type: post
date: 2007-12-06
excerpt: Saiba como centralizar um objeto na horizontal e vertical apenas com CSS.
url: /centralizando-um-objeto-na-horizontal-e-vertical-com-css/
aktt_notify_twitter:
  - no
tweetbackscheck:
  - 1356391819
shorturls:
  - 'a:3:{s:9:"permalink";s:80:"http://tableless.com.br/centralizando-um-objeto-na-horizontal-e-vertical-com-css";s:7:"tinyurl";s:26:"http://tinyurl.com/3epkhp5";s:4:"isgd";s:19:"http://is.gd/ow7ixO";}'
twittercomments:
  - 'a:52:{i:37496370067673088;s:6:"137044";i:37510815913349121;s:7:"retweet";i:37510814399209472;s:7:"retweet";i:37510812255916032;s:7:"retweet";i:37510810490114048;s:7:"retweet";i:37510809047269376;s:7:"retweet";i:37510807629594624;s:7:"retweet";i:37510806081896449;s:7:"retweet";i:37510799484256256;s:7:"retweet";i:37510798095941633;s:7:"retweet";i:37510795994599424;s:7:"retweet";i:37510794337845250;s:7:"retweet";i:37510792005812224;s:7:"retweet";i:37510790105800704;s:7:"retweet";i:37510788440653824;s:7:"retweet";i:37510786758742016;s:7:"retweet";i:37510784963575809;s:7:"retweet";i:37510783394910209;s:7:"retweet";i:37510781809467392;s:7:"retweet";i:37510776663056384;s:7:"retweet";i:37510775220207616;s:7:"retweet";i:37510773664124928;s:7:"retweet";i:37510771403395072;s:7:"retweet";i:37510769792782336;s:7:"retweet";i:37510766982602752;s:7:"retweet";i:37510764319211521;s:7:"retweet";i:37510762842816512;s:7:"retweet";i:37510760401735680;s:7:"retweet";i:37510758514294784;s:7:"retweet";i:37510757092429825;s:7:"retweet";i:37510755427291136;s:7:"retweet";i:37510753460162560;s:7:"retweet";i:37510751803412480;s:7:"retweet";i:37510749836279809;s:7:"retweet";i:37510748364083200;s:7:"retweet";i:37510746849935360;s:7:"retweet";i:37510745428070400;s:7:"retweet";i:37510743733567489;s:7:"retweet";i:37510741086969856;s:7:"retweet";i:37510739438600192;s:7:"retweet";i:37510737945432064;s:7:"retweet";i:37510736158662656;s:7:"retweet";i:37510734531268608;s:7:"retweet";i:37510729795903488;s:7:"retweet";i:37510721587650560;s:7:"retweet";i:37510719922507776;s:7:"retweet";i:37510718420942848;s:7:"retweet";i:37510716592234498;s:7:"retweet";i:37510715212300289;s:7:"retweet";i:37510707662553088;s:7:"retweet";i:37510705544433664;s:7:"retweet";i:37510704093200384;s:7:"retweet";}'
tweetcount:
  - 52
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

 [1]: http://tableless.com.br/centralizando-conteudo-na-vertical-e-horizontal-com-css-flexbox/