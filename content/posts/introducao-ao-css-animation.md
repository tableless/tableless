---
title: Introdução ao CSS Animation
author: Diego Eis
type: post
date: 2009-06-29
excerpt: CSS Animation manipula características dos elementos, transformando-os modificando por meio de transições os valores das propriedades definidas dos elementos.
url: /introducao-ao-css-animation/
aktt_notify_twitter:
  - no
tweetbackscheck:
  - 1356403254
shorturls:
  - 'a:3:{s:9:"permalink";s:51:"http://tableless.com.br/introducao-ao-css-animation";s:7:"tinyurl";s:26:"http://tinyurl.com/3wwcs4u";s:4:"isgd";s:19:"http://is.gd/Ol3KR4";}'
twittercomments:
  - 'a:14:{i:121307609633538048;s:7:"retweet";i:121066772743979009;s:7:"retweet";i:120968515921518593;s:7:"retweet";i:120958920310259713;s:7:"retweet";i:120951829306671104;s:7:"retweet";i:120951379559849984;s:7:"retweet";i:120863459939323904;s:7:"retweet";i:120862151899480065;s:7:"retweet";i:120861757093838848;s:7:"retweet";i:120861752945676288;s:7:"retweet";i:120861556425752576;s:7:"retweet";i:120861443062104065;s:7:"retweet";i:174587167174176771;s:7:"retweet";i:174568866054275073;s:7:"retweet";}'
tweetcount:
  - 64
dsq_thread_id: 503026302
categories:
  - CSS
  - Técnicas e Práticas
  - Tecnologia e Tendências
tags:
  - aprenda
  - CSS
  - Na Prática
  - tecnicascss
  - xhtml

---
Tudo o que eu falarei aqui sobre **CSS Animation** e **CSS Transforms** só podem ser testados no Safari ou em qualquer outro browser que utilize as últimas versões do Webkit. Há algumas aplicações que modificam muito o Webkit para usá-lo, pode ser que nestes, não funcione direito. Mesmo assim, infelizmente, o [Webkit][1] (por enquanto) é o único motor que suporta esse tipo de característica. 

**CSS Animation** permite que modifiquemos propriedades do CSS e tenhamos o resultado ali, na hora.
  
Para isso, usaremos uma propriedade chamada **transition**. Essa propriedade é divida em 3 propriedades: **transition-property** que é a propriedade que deverá ser animada, **transition-duration** é quanto tempo a transição irá durar, e **transition-timing-function** é o tipo de transição.

Imagine o seguinte código:

[cc lang=&#8221;css&#8221;]
  
div {
     
border: 10px solid black;
     
width: 300px;
     
height:300px;
     
background:gray;
  
}

div:hover {
     
background:red;
  
}
  
[/cc]

O código acima faz com que quando o usuário passe o mouse em cima do DIV, o background mude de cor. 

Vamos adicionar a propriedade transition agora. Note o código abaixo:
  
[cc lang=&#8221;css&#8221;]
  
div {
     
border: 10px solid black;
     
width: 300px;
     
height:300px;
     
background:gray;

-webkit-transition: background 1s linear;

}

div:hover {
     
background:red;
  
}
  
[/cc]

O CSS Animation entrará em ação com a propriedade **transition**.
  
Note que a propriedade tem o prefixo do Webkit, indicando que isso só funciona em browsers com este motor. 

A propriedade **transition** tem 3 valores: o primeiro valor é a propriedade que você quer alterar. O segundo valor é o tempo que essa animação durará. O terceiro valor é tipo de transição.

Você pode fazer várias transições em, separando os valores por _vírgulas_. Veja o exemplo:

[cc lang=&#8221;css&#8221;]
  
div {
     
border: 10px solid black;
     
width: 300px;
     
height:300px;
     
background:gray;

-webkit-transition: background 1s linear, width 1s linear;

}

div:hover {
     
background:red;
     
width: 400px;
  
}
  
[/cc]

Neste caso, iremos animar a largura do DIV e ao mesmo tempo, mudaremos a cor de background.

[Exemplo de CSS Animation][2]

#### CSS Transform

Tudo isso fica mais interessante se utilizarmos algumas propriedades do CSS Transform.
  
O CSS Transform é uma das características do CSS que tranformam a forma original dos elementos do HTML. Por exemplo, inclinação. Veja abaixo:

[cc lang=&#8221;css&#8221;]
  
div {
     
border: 10px solid black;
     
width: 300px;
     
height:300px;
     
background:gray;
     
-webkit-transition: background 1s linear, width 1s linear;

-webkit-transform: rotate(3deg);

}
  
[/cc]

No código acima, utilizei a propriedade **transform** com o valor **rotate**. Este valor rotaciona o elemento em sentido horário para um determinado grau. No caso acima, ele está inclinando o elemento com o valor de 3 graus.

Podemos fazer uma animação interessante utilizando o **transform: rotate**. Teste o código CSS abaixo:

[cc lang=&#8221;css&#8221;]
  
div {
     
border: 10px solid black;
     
width: 300px;
     
height:300px;
     
background:gray;
     
-webkit-transform: rotate(0deg);
     
-webkit-transition: background 1s linear, width 0.5s linear, -webkit-transform 1s linear;
  
}

div:hover {
     
background: red;
     
width: 400px;
     
-webkit-transform: rotate(360deg);
  
}
  
[/cc]

O código acima fará com que o elemento gire 360 graus.

#### Testei no iPhone

Fiz um teste rápido no iPhone. No iPhone, a função de HOVER é acionada quando o elemento é clicado. As animações funcionam perfeitamente, com exceção do giro de 360 graus que pára no meio e o elemento volta a posição normal.

Quem tiver algum celular Nokia com browser baseado em Webkit, faça uns testes e comenta com a galera os resultados.

#### Ainda é um rascunho no W3C

Tudo isso ainda é um [rascunho lá no W3C][3]. Mas a Apple já propôs sua idéia de como poderia ser o funcionamento do CSS Transformations aqui:
  
[Apple&#8217;s Proposal for CSS Transformations][4].

O interessante é que os browsers hoje em dia estão andando com as próprias pernas. Na verdade não apenas os browsers, mas todos os desenvolvedores. Ninguém está esperando o W3C para implementar e inventar coisas. Todos estão ajudando a pensar como pode ser o desenvolvimento web de amanhã. O trabalho do W3C está se resumindo em estudar, incluir e modificar as idéias da comunidade e de suas equipes &#8211; que por sinal, estão em mais espertas e rápidas agora. 

A documentação do rascunho do W3C está disponível aqui:
  
[http://www.w3.org/TR/css3-animations/][5]

Há bastante coisa para se ler aqui:

  * [Webkit Blog: CSS Animation][6]
  * [Webkit Blog: CSS Transforms][7]
  * [CSS: Transition Timing Functions][8]

 [1]: http://webkit.org/
 [2]: http://tableless.com.br/uploads/2009/06/cssanimation.html "Exemplo de CSS Animation"
 [3]: http://www.w3.org/TR/css3-animations/#introduction
 [4]: http://www.nabble.com/Apple%27s-Proposal-for-CSS-Transformations-to13615345.html
 [5]: http://www.w3.org/TR/css3-animations/ "Documentação do W3C para CSS Animation"
 [6]: http://webkit.org/blog/138/css-animation/
 [7]: http://webkit.org/blog/130/css-transforms/
 [8]: http://www.the-art-of-web.com/css/timing-function/