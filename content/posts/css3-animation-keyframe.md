---
title: CSS3 – Animation e regra keyframe
author: Diego Eis
type: post
date: 2011-05-09
excerpt: Saiba como o CSS 3 possibilita a criação de efeitos de animações e transições.
url: /css3-animation-keyframe/
tweetbackscheck:
  - 1356400731
shorturls:
  - 'a:3:{s:9:"permalink";s:47:"http://tableless.com.br/css3-animation-keyframe";s:7:"tinyurl";s:26:"http://tinyurl.com/3nyycgl";s:4:"isgd";s:19:"http://is.gd/7HTawD";}'
twittercomments:
  - 'a:7:{i:153949422533885952;s:7:"retweet";i:153939853841661952;s:7:"retweet";i:153934310024544257;s:7:"retweet";i:169914590929498112;s:7:"retweet";i:174587167174176771;s:7:"retweet";i:174568866054275073;s:7:"retweet";i:174171765503823873;s:7:"retweet";}'
tweetcount:
  - 13
dsq_thread_id: 503040265
categories:
  - CSS
  - CSS3
  - HTML
  - Técnicas e Práticas
  - Tecnologia e Tendências
tags:
  - 2011
  - CSS
  - CSS3
  - desenvolvimento web
  - Na Prática
  - tecnicascss

---
A propriedade trasition trabalha de forma muito simples e flexível. Você praticamente diz para o browser qual o valor inicial e o valor final para que ele aplique a transição automaticamente, controlamos praticamente apenas o tempo de execução. Para termos mais controle sobre a animação temos a propriedade animation que trabalha juntamente com a rule keyframe. 

Basicamente você consegue controlar as características do objeto e suas diversas transformações definindo fases da animação. Observe o código abaixo e veja seu funcionamento:

<pre class="lang-css">@-webkit-keyframes rodar {
	from {
		-webkit-transform:rotate(0deg);
	}
	to {
		-webkit-transform:rotate(360deg);
	}
}
</pre>

O código acima define um valor inicial e um valor final. Agora vamos aplicar esse código a um elemento. Minha ideia é fazer um DIV girar. 😉

O código HTML até agora é este. Fiz apenas um div e defini este keyframe:

<pre class="lang-html">&lt;!DOCTYPE html&gt;

&lt;html lang=&rdquo;pt-br&rdquo;&gt;
&lt;head&gt;
	&lt;title&gt;&lt;/title&gt;
	&lt;meta charset=&rdquo;utf-8&rdquo;&gt;
	&lt;style&gt;
	@-webkit-keyframes rodaroda {
		from {
			-webkit-transform:rotate(0deg);
		}
		to {
			-webkit-transform:rotate(360deg);
		}
	}
	&lt;/style&gt;
&lt;/head&gt;
&lt;body&gt;

&lt;div&gt;&lt;/div&gt;

&lt;/body&gt;
&lt;/html&gt;
</pre>

Primeiro você define a função de animação, no caso é o nosso código que define um valor inicial de 0 graus e um valor final de 360 graus. Agora vamos definir as características deste DIV.

<pre class="lang-css">div {
	width:50px;
	height:50px;
	margin:30% auto 0;
	background:black;
}
</pre>

Nas primeiras linhas defini qual será o estilo do div. Ele terá uma largura e uma altura de 50px. A margin de 30% do topo garantirá um espaço entre o objeto e o topo do documento, e background preto.

A propriedade animation tem uma série de propriedades que podem ser resumidas em um shortcode bem simples. Veja a tabela logo a seguir para entender o que cada propriedade signifca:

animation-name
:   Especificamos o nome da função de animação

animation-duration
:   Define a duração da animação. O valor é declarado em segundos.

animation-timing-function
:   Descreve qual será a progressão da animação a cada ciclo de duração. Existem uma série de valores possíveis e que pode ser que o seu navegador ainda não suporte, mas são eles: ease, linear, ease-in, ease-out, ease-in-out, cubic-bezier(<number>, <number>, <number>, <number>) [, ease, linear, ease-in, ease-out, ease-in-out, cubic-bezier(<number>, <number>, <number>, <number>)]*. O valor padrão é ease.

animation-interation-count
:   Define o número de vezes que o ciclo deve acontecer. O padrão é um, ou seja, a animação acontece uma vez e pára. Pode ser também infinito definindo o valor infinite no valor.

animation-direction
:   Define se a animação irá acontecer ou não no sentido inverso em ciclos alternados. Ou seja, se a animação está acontecendo no sentido horário, ao acabar a animação, o browser faz a mesma animação no elemento, mas no sentido antihorário. Os valores são alternate ou normal.

animation-play-state
:   Define se a animação está acontecendo ou se está pausada. Você poderá por exemplo, via script, pausar a animação se ela estiver acontecendo. Os valores são running ou paused. 

animation-delay
:   Define quando a animação irá começar. Ou seja, você define um tempo para que a animação inicie. O valor 0, significa que a animação começará imediatamente.

Voltando para o nosso código, vamos aplicar algumas dessas propriedades:

<pre class="lang-css">div {
	width:50px;
	height:50px;
	margin:30% auto 0;
	background:black;

	-webkit-animation-name: rodaroda;
	-webkit-animation-duration: 0.5s;
	-webkit-animation-timing-function: linear;
	-webkit-animation-iteration-count: infinite;
	-webkit-animation-direction: alternate;
}
</pre>

Veja que na propriedade animation-name chamamos o mesmo nome que demos na nossa função de keyframe logo no começo da explicação. Depois definimos uma duração de ciclo de meio segundo. Definimos que o comportamento da animação será linear, e com a propriedade animation-iteration-count definimos que ele girará infinitamente. E por último definimos pelo animation-direction que a animação deverá ser alternada, ou seja, o DIV girará para um lado, e quando alcançar o final da animação, o browser deverá alternar essa animação.

Podemos melhorar esse código utilizando a versão shortcode, que é mais recomendado. Veja a ordem que devemos escrever as propriedades animation em forma de shortcode:

**animation**: animation-name, animation-duration, animation-timing-function, animation-delay, animation-iteration-count, animation-direction] , animation-name, animation-duration, animation-timing-function, animation-delay, animation-iteration-count, animation-direction

Aplicando isso ao nosso código:

<pre class="lang-css">div {
	width:50px;
	height:50px;
	margin:30% auto 0;
	background:black;

	-webkit-animation: rodaroda 0.5s linear infinite alternate;
}
</pre>

Pronto. Agora temos um elemento que gira sem parar, hora para direita hora para esquerda.

### Definindo ciclos

Nós definimos no keyframe do nosso último exemplo apenas um início e um fim. Mas e se quiséssemos que ao chegar na metade da animação o nosso elemento ficasse com o background vermelho? Ou que ele mudasse de tamanho, posição e etc? É aí onde podemos flexibilizar melhor nosso keyframe definindo as fases da animação. Por exemplo, podemos dizer para o elemento ter uma cor de background diferente quando a animação chegar aos 10% do ciclo, e assim por diante.

Veja o exemplo:

<pre class="lang-css">@-webkit-keyframes rodaroda {
	0% {
		-webkit-transform:rotate(0deg);
	}
	50% {
		background:red;
		-webkit-transform:rotate(180deg);
	}
	100% {
		-webkit-transform:rotate(360deg);
	}
}
</pre>

Definimos acima que o início da animação o elemento começará na posição normal, 0 graus.
  
Quando a animação chegar aos 50% do ciclo, o elemento deverá ter girado para 180 graus e o background dele deve ser vermelho. E quando a animação chegar a 100% o elemento deve ter girado ao todo 360 graus e o background, como não está sendo definido, volta ao valor padrão, no nosso caso black, que foi definido no CSS onde formatamos este DIV.

Logo nosso elemento girará pra sempre e ficará alternando a cor de fundo de preto para vermelho. Fiz um exemplo bem simples modificando apenas o background, mas você pode muito bem definir um position e modificar os valores de left e top para fazer o elemento se movimentar.
  
No exemplo também defini apenas 3 estágios (0%, 50% e 100%) você pode definir um maior número de estágios: 5%, 10%, 12%, 16% e etc&#8230; Adequando as fases da animação às suas necessidades.

Há exemplos muito interessantes na internet onde podemos ver todo o poder das animações feitas pela CSS. Veja o exemplo que fizemos aqui neste texto no endereço: <http://migre.me/4ubym>