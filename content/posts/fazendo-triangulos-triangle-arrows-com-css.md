---
title: Como fazer triângulos (setas ou arrows) com CSS
author: Diego Eis
type: post
date: 2014-04-18
excerpt: Como fazer triângulos (arrows) usando apenas com CSS.
url: /fazendo-triangulos-triangle-arrows-com-css/
dsq_thread_id: 2620565847
categories:
  - CSS
  - Técnicas e Práticas
tags:
  - CSS
  - tecnicas css
  - tecnicascss

---
Muitas vezes usamos triângulos em links, botões ou qualquer outro elemento que precise de alguma indicação de clique. Esses triângulos, por serem muito simples, é bem possível criarmos inteiramente usando CSS. Esse truque vale muito a pena para evitar que o browser tenha que baixar pequenas imagens, quem mesmo tendo um peso bem leve, elas atrapalham a performance do carregamento do site.

Para esse truque você usará os [pseudo elementos :after ou :before][1].

Abaixo, segue o código:

<pre class="lang-html">&lt;a href="#" class="seta-cima"&gt;Seta para cima&lt;/a&gt;
&lt;span class="seta-baixo"&gt;Seta para baixo&lt;/span&gt;
&lt;i class="seta-esquerda"&gt;Seta para esquerda&lt;/i&gt;
&lt;div class="seta-direita"&gt;Seta para direita&lt;/div&gt;
</pre>

<pre class="lang-css">/**
*** Seta para ESQUERDA
**/
.seta-esquerda:before {
  content: "";
  display: inline-block;
  vertical-align: middle;
  margin-right: 10px;
  width: 0; 
  height: 0; 

  border-top: 5px solid transparent;
  border-bottom: 5px solid transparent; 
  border-right: 5px solid blue; 
}

/**
*** Seta para DIREITA
**/
.seta-direita:before {
  content: "";
  display: inline-block;
  vertical-align: middle;
  margin-right: 10px;
  width: 0; 
  height: 0; 

  border-top: 5px solid transparent;
  border-bottom: 5px solid transparent;
  border-left: 5px solid green;
}

/**
*** Seta para CIMA
**/
.seta-cima:before {
  content: "";
  display: inline-block;
  vertical-align: middle;
  margin-right: 10px;
  width: 0; 
  height: 0; 

  border-left: 5px solid transparent;
  border-right: 5px solid transparent;
  border-bottom: 5px solid black;
}

/**
*** Seta para BAIXO
**/
.seta-baixo:before {
  content: "";
  display: inline-block;
  vertical-align: middle;
  margin-right: 10px;
  width: 0; 
  height: 0; 

  border-left: 5px solid transparent;
  border-right: 5px solid transparent;
  border-top: 5px solid #f00;
}
</pre>



Perceba que o que define o tamanho da seta é o tamanho das bordas. A cor também é definida pela borda. Eu usei em um pseudo-elemento, mas você pode muito bem fazer em um span ou qualquer outro elemento vazio. Eu ainda assim sugiro fazer em um pseudo-elemento para evitar elementos inúteis.

 [1]: http://tableless.com.br/como-usar-before-after/