---
title: Gradientes em CSS
author: Diego Eis
type: post
date: 2010-09-22
excerpt: Já é possível criar gradientes apenas utilizando CSS3. Sem imagens e com alguma compatibilidade com a maioria dos browsers do mercado. Vale a pena experimentar.
url: /gradientes-em-css/
aktt_notify_twitter:
  - yes
tweetbackscheck:
  - 1356466647
shorturls:
  - 'a:3:{s:9:"permalink";s:41:"http://tableless.com.br/gradientes-em-css";s:7:"tinyurl";s:26:"http://tinyurl.com/3gqncch";s:4:"isgd";s:19:"http://is.gd/leoN1w";}'
twittercomments:
  - 'a:0:{}'
dsq_thread_id: 503028815
categories:
  - CSS
  - Técnicas e Práticas
tags:
  - 2010
  - CSS
  - CSS3
  - padroes web
  - safari

---
Uma das vantagens do CSS3 é a economia de imagem. É normal utilizar imagens para tratar partes do layout que são exclusivamente visuais. Um exemplo é o uso de gradientes. Até agora a única maneira de produzir gradientes era com imagens. E dá um trabalhão caso você queira modificá-la ou caso você esteja produzindo um site baseado em themes. Com CSS3 você consegue produzir gradientes diretamente pelo código CSS. Isso dá possibilidades para manipulação via Javascript e outros frameworks. Sem contar que a manutenção é muito mais suave.

### Suporte de browser

Firefox, Safari, Chrome e IE5+ suportam gradientes. O Opera irá suportar um pouco mais pra frente. Parece que essa feature já está nos planos do browser. O problema é que a sintaxe utilizada é diferente para cada um deles. O que não deixa é exatamente um problemão, contanto que o resultado visual seja parecido ou igual.

### Sintaxe

O gradiente será feito no background. Você define a direção do gradiente, onde ele começará e terminará, e quais as cores que farão a transição.

<pre class="lang-css">/* Para Mozilla/Gecko (Firefox etc) */
background: -moz-linear-gradient(top, #666, #fff) repeat-X;

/* Para WebKit (Safari, Google Chrome etc) */
background: -webkit-gradient(linear, left top, left bottom, from(#666), to(#fff)) repeat-X;

/* Para IE 8 */
-ms-filter: "progid:DXImageTransform.Microsoft.gradient(startColorstr=#666, endColorstr=#FFFFFFFF)";

/* Para IE 5.5 - 7 */
filter: progid:DXImageTransform.Microsoft.gradient(startColorstr=#666, endColorstr=#FFFFFFFF);
</pre>

Estou torcendo para que os browsers resolvam logo essa questão da sintaxe.

Veja abaixo como fazemos um gradiente radial. Infelizmente não funcionará no IE.

<pre class="lang-css">/* Para Mozilla/Gecko (Firefox etc) */
background: -moz-radial-gradient(40% 40%, farthest-side, #666, #FFF) repeat-X;

/* Para WebKit (Safari, Google Chrome etc) */
background: -webkit-gradient(radial, 20% 20%, 20, 20% 20%, 60, from(#666), to(#FFF)) repeat-X;
</pre>

[Veja um exemplo.][1]

A [biblioteca de referência do Safari][2] tem alguns exemplos muito bons sobre o assunto. Contudo, acho a sintaxe do webkit mais difícil de ser entendida. Aqui tem um [simulador bacana para webkit][3].

Para gradientes simples e para ocasiões onde o Internet Explorer não seja requisitado, esse recurso é interessante. Se o IE for realmente uma pedra no seu caminho e você precisa fazer uma versão com imagens para ele, aconselho deixar essa técnica para lá e fazer uma versão com imagens para todos os browsers. Você vai ter o trabalho já de produzir as imagens, recortá-las e etc, não vale a pena manter dois tipos de códigos.

 [1]: http://tableless.com.br/uploads/2010/09/gradiente.html
 [2]: http://developer.apple.com/library/safari/#documentation/InternetWeb/Conceptual/SafariVisualEffectsProgGuide/Gradients/Gradients.html
 [3]: http://www.westciv.com/tools/gradients/index.html