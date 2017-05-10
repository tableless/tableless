---
title: CSS 3 Columns
author: Diego Eis
type: post
date: 2009-07-14
excerpt: O CSS3 facilitará muitas coisas, uma das possibilidades é a criação automatica de colunas em blocos de textos. Para tanto, utilizamos as propriedades de columns do CSS3.
url: /css3-columns/
aktt_notify_twitter:
  - no
tweetbackscheck:
  - 1356398227
shorturls:
  - 'a:3:{s:9:"permalink";s:36:"http://tableless.com.br/css3-columns";s:7:"tinyurl";s:26:"http://tinyurl.com/3n52zh9";s:4:"isgd";s:19:"http://is.gd/FWnt9o";}'
twittercomments:
  - 'a:0:{}'
dsq_thread_id: 503039130
categories:
  - CSS
  - HTML
  - Técnicas e Práticas
tags:
  - 2009
  - CSS
  - CSS3
  - html
  - Na Prática
  - tecnicascss

---
Com o controle de colunas no CSS, podemos definir colunas de texto de forma automática. Até hoje não havia maneira de fazer isso de maneira inteligente com CSS e o grupo de propriedades `columns` pode fazer isso de maneira livre de gambiarras.

#### column-count

A propriedade `column-count` define a quantidade de colunas terá o bloco de textos.

<pre lang="css" line="1">/* Define a quantidade de colunas, a largura é definida uniformimente. */
-moz-column-count: 2;
-webkit-column-count: 2;
</pre>

#### column-width

Com a propriedade `column-width` definimos a largura destas colunas.

<pre lang="css" line="1">/* Define qual a largura mínima para as colunas. Se as colunas forem expremidas, fazendo com que a largura delas fique menor que este valor, elas se transformam em 1 coluna automaticamente */
-moz-column-width: 400px; 
-webkit-column-width: 400px; 
</pre>

Fiz alguns testes aqui e há uma diferença entre o Firefox 3.5 e o Safari 4 (Public Beta).
  
O `column-width` define a largura mínima das colunas. Na [documentação do W3C][1] é a seguinte: imagine que você tenha uma área disponível para as colunas de 100px. Ou seja, você tem um div com 100px de largura (width). E você define que as larguras destas colunas (`column-width`) sejam de 45px. Logo, haverá 10px de sobra, e as colunas irão automaticamente ter 50px de largura, preenchendo este espaço disponível. É esse o comportamento que o Firefox adota.

Já no Safari, acontece o seguinte: se você define um `column-width`, as colunas obedecem esse valor e não preenchem o espaço disponível, como acontece na explicação do W3C e como acontece também no Firefox. Dessa forma faz mais sentido para mim. 

Como a propriedade não está 100% aprovada ainda, há tempo para que isso seja modificado novamente. Talvez a mudança da nomenclatura da classe para `column-min-width` ou algo parecida venha a calhar, assim, ficamos com os dois resultados citados, que são bem úteis para nós de qualquer maneira.

#### column-gap

A propriedade `column-gap` cria um espaço entre as colunas, um gap.

<pre lang="css" line="1">/* Define o espaço entre as colunas. */
-moz-column-gap: 50px;
-webkit-column-gap: 50px;
</pre>

[Veja um exemplo destas propriedades aqui.][2].

Utilizamos aqui os prefixos -moz- e -webkit-, estas propriedades não funcionam oficialmente em nenhum browser. Mas já podem ser usados em browsers como Firefox e Safari. Fique à vontade para testar e comentar aqui os resultados!

 [1]: http://www.w3.org/TR/css3-multicol/#cw
 [2]: http://tableless.com.br/uploads/2009/07/css3-columns.html