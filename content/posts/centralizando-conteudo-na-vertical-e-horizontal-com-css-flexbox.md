---
title: 'Centralizando conteúdo na vertical e horizontal  com CSS Flexbox'
author: Diego Eis
type: post
date: 2015-10-07
excerpt: Centralize conteúdo e elementos na vertical e horizontal usando Flexbox do CSS.
url: /centralizando-conteudo-na-vertical-e-horizontal-com-css-flexbox/
categories:
  - CSS
  - Técnicas e Práticas
tags:
  - CSS
  - flexbox

---
Centralizar as coisas com CSS não é algo trivial. Na verdade, centralizar na horizontal é até fácil. Mas centralizar elementos na vertical já beira o impossível. Existem as maneiras antigas, [com position por exemplo][1], mas que não passam de gambiarras. Dá para fazer com `display: table;` emulando uma tabela. Mas também não é a melhor das soluções.

Como eu estou usando cada vez mais Flexbox, acho que já é uma boa hora de usarmos essa alegria em produção. Logo, segue aí a dica de como centralizar conteúdo na vertical e na horizontal usando só CSS com Flexbox.



Nosso HTML:

<pre class="lang-html">&lt;body&gt;
  &lt;div class="wrapper"&gt;
    &lt;div&gt;
      Tão simples quanto isso.
    &lt;/div&gt;
  &lt;/div&gt;
&lt;/body&gt;
</pre>

Nosso CSS:

<pre class="lang-css">html, body {
  height: 100%;
  min-height: 100%;
}

body {
  font: 15px arial;
  color: rgba(0, 0, 0, .7);
}

.wrapper {
  height: 100%;
  min-height: 100%;
  display: -webkit-flex;
  display: flex;
  -webkit-align-items: center;
  align-items: center;
  -webkit-justify-content: center;
  justify-content: center;
}

.wrapper div {
  padding: 40px;
  border: 1px solid rgba(0, 0, 0, .3)
}
</pre>

Rapidamente: estamos fazendo com que o HTML e o Body tenham uma altura de 100%, para que o nosso `.wrapper` consiga ocupar todo o espaço vertical da tela. Assim podemos posicionar nosso `div` no centro.

No `.wrapper` definimos a propriedade `display: flex;` que avisa o navegador que os elementos filhos diretos do `.wrapper` deverão agir como flexbox. A propriedade `align-items` centraliza os elementos flex na vertical. A propriedade `justify-content` centraliza os elementos na horizontal.
  
Perceba que usei o prefixo `-webkit-` por causa do Safari.

Olha só como está o status no CanIUse.

<img src="http://tableless.com.br/uploads/2015/10/Screen-Shot-2015-10-07-at-2.50.22-PM.png" alt="Flexbox no Can I Use" width="1254" height="313" class="alignnone size-full wp-image-51607" />

 [1]: http://tableless.com.br/centralizando-um-objeto-na-horizontal-e-vertical-com-css/