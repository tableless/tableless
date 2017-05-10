---
title: Parallax simples com JQuery e CSS
author: Diego Eis
type: post
date: 2013-01-14
excerpt: Faça o efeito parallax com 3 passos simples.
url: /parallax-simples-com-jquery-e-css/
tweetbackscheck:
  - 1356325721
shorturls:
  - 'a:3:{s:9:"permalink";s:31:"http://tableless.com.br/?p=7592";s:7:"tinyurl";s:26:"http://tinyurl.com/cjtr2qg";s:4:"isgd";s:19:"http://is.gd/N0NxVG";}'
twittercomments:
  - 'a:0:{}'
dsq_thread_id: 1024953901
categories:
  - JavaScript
  - JQuery
  - O Básico
  - Técnicas e Práticas
tags:
  - JavaScript
  - JQuery
  - parallax

---
> Parallax é a diferença na posição de objetos vistos em diferentes faixas de visão, medido pelo ângulo de inclinação entre as faixas. Com isso, objetos próximos têm uma maior Parallax que objetos mais distantes, quando observado de posições diferentes. Dessa forma, podemos dizer que o Parallax é o que nos dá a noção de profundidade em nosso campo de visão &#8211; _[UX Design][1]_

Parallax é algo que virou moda. É um efeito muito interessante quando bem utilizado e pode ser bastante explorado se você for criativo. Não é difícil de fazer este efeito utilizando CSS e Javascript. A coisa toda é muito simples. Vamos mostrar abaixo uma técnica que é bastante divulgada por aí. Tentei evitar firulas. O importante é que você entenda o cálculo, que é a essencia dessa técnica.

## Passo 1: HTML

Inicialmente vamos criar dois elementos. Estes elementos terão backgrounds diferentes para e vamos atribuir uma classe bgParallax para identificar que eles terão o movimento do background alterado. Muitos artigos por aí colocam um data-type=&#8221;background&#8221; ou algo do gênero.

Também vamos inserir um atributo data-speed, que é o que vai definir a velocidade com que o background vai se mover em relação aos outros elementos. O HTML fica assim:

<pre class="lang-html">&lt;div id="quemsomos" class="bgParallax" data-speed="15"&gt;
     &lt;article&gt;
     	&lt;h1&gt;That show's called a pilot.&lt;/h1&gt;
     	&lt;p&gt;Well, the way they make shows is, they make one show. That show's called a pilot. Then they show that show to the people who make shows, and on the strength of that one show they decide if they're going to make more shows. Some pilots get picked and become television programs. Some don't, become nothing. She starred in one of the ones that became nothing. &lt;/p&gt;
     &lt;/article&gt;
&lt;/div&gt;
&lt;div id="missao" class="bgParallax" data-speed="10"&gt;
     &lt;article&gt;
     	&lt;h1&gt;Water&lt;/h1&gt;
     &lt;p&gt;You think water moves fast? You should see ice. It moves like it has a mind. Like it knows it killed the world once and got a taste for murder. After the avalanche, it took us a week to climb out. Now, I don't know exactly when we turned on each other, but I know that seven of us survived the slide... and only five made it out. Now we took an oath, that I'm breaking now. We said we'd say it was the snow that killed the other two, but it wasn't. Nature is lethal but it doesn't hold a candle to man. &lt;/p&gt;
     &lt;/article&gt;
&lt;/div&gt;
</pre>

## Passo 2: CSS

Eu coloquei algum CSS e defini um background para cada um dos divs. Defini uma altura, defini background, font, cor e etc. Veja abaixo o código CSS:

<pre class="lang-css">* {margin:0; padding: 0;}
html, body {height:100%;}

/** formata elementos que tem backgrounds parallax **/
.bgParallax {
	font-family: 'Elsie', cursive;
	color:#FFF;
	margin: 0 auto;
	width: 100%;
	max-width: 1920px;
	position: relative;
	min-height: 100%;
	text-shadow:0 0 10px rgba(0,0,0,0.7);

	background-position: 50% 0;
	background-repeat: repeat;
	background-attachment: fixed;
}

/* Define backgrounds dos divs */
#quemsomos {background-image: url(bg2.jpg);}
#missao {
	background-image: url(bg1.jpg);
	-webkit-box-shadow:-20px 0 20px 5px rgba(0,0,0,0.7);
	-moz-box-shadow:-20px 0 20px 5px rgba(0,0,0,0.7);
	-ms-box-shadow:-20px 0 20px 5px rgba(0,0,0,0.7);
	-o-box-shadow:-20px 0 20px 5px rgba(0,0,0,0.7);
	box-shadow:-20px 0 20px 5px rgba(0,0,0,0.7);
}

/** Formata o article que vai o texto **/
.bgParallax article {
  width: 70%;
  text-align: center;
  margin:0 auto;
  padding:20% 0 0;
}

/** formata texto **/
article h1 {font-size:40px;}
article p {line-height: 30px; font-size:20px; margin-top:15px;}
article p a {color:#FFF; text-decoration:none; font-size:30px;}

</pre>

Nesse ponto eu apenas coloquei o CSS para formatar o visual dos DIVs. Como o background está **fixed** PARECE mas ainda não está com efeito parallax. Esse truque de colocar FIXED é velho, dá até um efeito bacana. Costumamos chamar de PARALLAX FAKE.

Agora vamos ao JQuery.

## Passo 3: JQuery

Primeiro identificamos os elementos que o efeito será aplicado. Nesse caso são todos os elementos com a classe **bgParallax**.

<pre class="lang-javascript">$(document).ready(function(){

   $('div.bgParallax').each(function(){
    	var $obj = $(this);
   });	
});
</pre>

Já que identificamos cada um dos elementos que terão o efeito, temos que identificar quando o usuário rola a página. Para isso iremos usar a função **scroll()** do JQuery. E aqui você precisa de muita atenção: a velocidade do scroll dos backgrounds é diferente da velocidade do scroll da página. É isso que causa o [efeito de Parallax][2]. É por isso que colocamos o atributo data-speed. Iremos utilizar aquele valor para definir quão rápido será a rolagem do background. Primeiro, precisamos definir a relação da rolagem: digamos que seja de 50px. Ou seja, a cada 50px o background vai rolar uma quantidade determinada de pixels. Esse valor é o 50px dividido pelo data-speed do objeto. Suponha que o data-speed seja de 10px. Logo, a cada 50px de rolagem da página o background rola 5px apenas. Sacou? Olha só o código:

<pre class="lang-javascript">var yPos = -($(window).scrollTop() / $obj.data('speed')); 
</pre>

Colocamos esse valor dentro de uma variável **yPos**. O valor é negativo por que o background tem que se mover para cima.
  
O **$(window).scrollTop()** pega o valor de quanto a página já rolou do topo, esse valor é dividido pelo **$obj.data(&#8216;speed&#8217;)**, que é o valor que colocamos no atributo **data-speed** de cada **div.bgParallax**.

Agora precisamos definir que esse valor seja o valor do TOP no background-position dos divs. Fazemos isso assim:

<pre class="lang-javascript">var bgpos = '50% '+ yPos + 'px';
</pre>

Aplicamos isso ao objeto assim:

<pre class="lang-javascript">$obj.css('background-position', bgpos );
</pre>

O código final fica assim:

<pre class="lang-javascript">$('div.bgParallax').each(function(){
	var $obj = $(this);

	$(window).scroll(function() {
		var yPos = -($(window).scrollTop() / $obj.data('speed')); 

		var bgpos = '50% '+ yPos + 'px';

		$obj.css('background-position', bgpos );

	}); 
});
</pre>

Veja o [exemplo completo aqui][3].

 [1]: http://www.uxdesign.blog.br/imersao/a-imersao-do-efeito-parallax/
 [2]: http://en.wikipedia.org/wiki/Parallax
 [3]: http://tableless.github.com/exemplos/parallax/parallax.html