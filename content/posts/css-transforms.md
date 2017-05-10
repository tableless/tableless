---
title: CSS Transforms
author: Diego Eis
type: post
date: 2011-01-10
excerpt: '"CSS 2D Transforms allow elements rendered by CSS to be trans- formed in two-dimensional space." É aqui que a graça do CSS 3 começa.'
url: /css-transforms/
tweetbackscheck:
  - 1356458876
shorturls:
  - 'a:3:{s:9:"permalink";s:38:"http://tableless.com.br/css-transforms";s:7:"tinyurl";s:26:"http://tinyurl.com/3rmns5y";s:4:"isgd";s:19:"http://is.gd/xhdT5U";}'
twittercomments:
  - 'a:5:{i:26963440056668160;s:7:"retweet";i:50610432746065920;s:6:"137347";i:144961097227714560;s:7:"retweet";i:156883648010915840;s:7:"retweet";i:169918207606525952;s:7:"retweet";}'
tweetcount:
  - 5
dsq_thread_id: 503039883
categories:
  - CSS
  - HTML
  - Técnicas e Práticas
tags:
  - 2011
  - animation
  - CSS3
  - cssanimation
  - csstransforms
  - tableless
  - web standards

---
O W3C descreve CSS Transform assim:

> CSS 2D Transforms allow elements rendered by CSS to be trans- formed in two-dimensional space.

Há dois tipos de CSS Transforms: no formato 2D e 3D. Veremos aqui apenas o formato 2D que é o que tem mais suporte entre os browsers. Testaremos com Firefox 4, Safari 5 e Opera 10.5. Perceba que o código estará com o prefixo de cada browser para que não haja problemas em browsers que não reconheçam as propriedades que iremos aplicar.

Temos abaixo um exemplo com 3 imagens. O código HTML é o seguinte:

<pre class="lang-html">&lt;ul&gt;
	&lt;li&gt;&lt;img src="http://tableless.github.com/exemplos/csstransforms/images/img1.png" alt="" /&gt;&lt;/li&gt;
	&lt;li&gt;&lt;img src="http://tableless.github.com/exemplos/csstransforms/images/img2.png" alt="" /&gt;&lt;/li&gt;
	&lt;li&gt;&lt;img src="http://tableless.github.com/exemplos/csstransforms/images/img3.png" alt="" /&gt;&lt;/li&gt;
&lt;/ul&gt;
</pre>

Apliquei o código CSS abaixo para que fique mais apresentável:

<pre class="lang-css">body {
	background:#EFEFEF;
}
ul {
	width:900px;
	margin:100px auto 0;
}
ul li {
	display:inline-block;
	list-style:none;
}

ul li img {
	vertical-align:middle;
	border:15px solid #FFF;
}
</pre>

A propriedade transform irá modificar a forma do elemento. Abaixo vamos conhecer alguns dos valores que iremos aplicar.

**scale**
  
O valor scale modificará a dimensão do elemento. Ele aumentará proporcionalmente o tamanho do elemento levando em consideração o tamanho original do elemento.

**skew**
  
Skew modificará os angulos dos elementos.

**translation**
  
O translation moverá o elemento no eixo X e Y. O interessante é que você não precisa se preocupar com floats, positions, margins e etc. Se você aplica o translation, ele moverá o objeto e pronto.

**rotate**
  
O rotate rotaciona o elemento levando em consideração seu ângulo, especialmente quando o ângulo é personalisado com o transform-origin.

### Como funciona

#### Scale

Adicionando o código abaixo, ao passarmos o mouse em cima das imagens, sua escala aumentará. Para entender o valor de referência da escala: 1 é o tamanho original do elemento. 2 é o dobro deste tamanho. Neste nosso exemplo diminui pela metade o tamanho da imagem ao passar o mouse aumentei em em 30% o

<pre class="lang-css">ul li img {
	-webkit-transform:scale(0.5); /* prefixo para browsers webkit */
	-moz-transform:scale(0.5); /* prefixo para browsers gecko */
	-o-transform:scale(0.5); /* prefixo para opera */
	transform:scale(0.5);
}

ul li img:hover {
	-webkit-transform:scale(1.3); /* prefixo para browsers webkit */
	-moz-transform:scale(1.3); /* prefixo para browsers gecko */
	-o-transform:scale(1.3); /* prefixo para opera */
	transform:scale(1.3);
}
</pre>

[Veja este exemplo][1]

#### Skew

Para testar, vamos adicionar o valor skew. Aqui não estaremos fazendo bom uso do skew, mas há exemplos bem interessantes na internet como [este][2]. 

<pre class="lang-css">ul li img {
	-webkit-transform:scale(0.5); /* prefixo para browsers webkit */
	-moz-transform:scale(0.5); /* prefixo para browsers gecko */
	-o-transform:scale(0.5); /* prefixo para opera */
	transform:scale(0.5);
}

ul li img:hover {
	-webkit-transform:scale(1.3) skew(30deg); /* prefixo para browsers webkit */
	-moz-transform:scale(1.3) skew(30deg); /* prefixo para browsers gecko */
	-o-transform:scale(1.3) skew(30deg); /* prefixo para opera */
	transform:scale(1.3) skew(30deg);
}
</pre>

Agora, no hover da imagem mudamos em 30 graus o ângulo. Veja [um exemplo][3].

#### Translate

Substituindo o skew pelo translate, modificaremos a posição do elemento. Veja abaixo:

<pre class="lang-css">ul li img {
	-webkit-transform:scale(0.5); /* prefixo para browsers webkit */
	-moz-transform:scale(0.5); /* prefixo para browsers gecko */
	-o-transform:scale(0.5); /* prefixo para opera */
	transform:scale(0.5);
}

ul li img:hover {
	-webkit-transform:scale(1.3) translate(80px, 80px); /* prefixo para browsers webkit */
	-moz-transform:scale(1.3) translate(80px, 80px); /* prefixo para browsers gecko */
	-o-transform:scale(1.3) translate(80px, 80px); /* prefixo para opera */
	transform:scale(1.3) translate(80px, 80px);
}
</pre>

[Veja o exemplo][4].

#### Rotate

E por fim, o efeito que eu acho mais legal é o rotate.
  
Com o código abaixo, rotacionamos o elemento em 180 graus.

<pre class="lang-css">ul li img {
	-webkit-transform:scale(0.5);
	-moz-transform:scale(0.5);
	-o-transform:scale(0.5);
	transform:scale(0.5);
}

ul li img:hover {
	-webkit-transform:scale(1.3) rotate(180deg);
	-moz-transform:scale(1.3) rotate(180deg);
	-o-transform:scale(1.3) rotate(180deg);
	transform:scale(0.5) rotate(180deg);
}
</pre>

[veja o exemplo][5].

#### Com animação

Aplicando animação via CSS, o [exemplo fica mais interessante][6].

 [1]: http://tableless.github.com/exemplos/csstransforms/exemplo1.html
 [2]: http://www.paulrhayes.com/experiments/cube/multiCubes.html
 [3]: http://tableless.github.com/exemplos/csstransforms/exemplo2.html
 [4]: http://tableless.github.com/exemplos/csstransforms/exemplo3.html
 [5]: http://tableless.github.com/exemplos/csstransforms/exemplo4.html
 [6]: http://tableless.github.com/exemplos/csstransforms/