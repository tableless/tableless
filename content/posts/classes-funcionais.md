---
title: Classes Funcionais
author: Diego Eis
type: post
date: 2012-11-28
excerpt: Crie classes que podem ser reutilizadas de acordo com a sua necessidade.
url: /classes-funcionais/
tweetbackscheck:
  - 1356393278
shorturls:
  - 'a:3:{s:9:"permalink";s:31:"http://tableless.com.br/?p=7422";s:7:"tinyurl";s:26:"http://tinyurl.com/cvdw2cn";s:4:"isgd";s:19:"http://is.gd/8yG9BG";}'
twittercomments:
  - 'a:0:{}'
dsq_thread_id: 948282002
categories:
  - CSS
  - HTML
  - Técnicas e Práticas
tags:
  - 2012
  - CSS

---
Normalmente, principalmente quando manipulamos elementos com javascript, precisamos modificar diversas vezes as características básicas dos objetos no HTML. Vira e mexe você precisa esconder, fazer aparecer, transformar em bloco ou linha, retirar margens, paddings e etc&#8230; você pode fazer isso com Javascript ou com uma simples linha de CSS.

<pre class="lang-html">&lt;div style="display:none;"&gt;&lt;/div&gt;
</pre>

Via JQuery seria algo como:

<pre class="lang-javascript">$('div').hide();
</pre>

O problema disso que é não escala. Se você precisa fazer isso em muitos elementos e muito frequentemente, você acaba sujando seu HTML ou acaba jogando um trabalho para o Javascript que na verdade não é dele. 

Esse tipo de cenário é normal por que você precisa reutilizar código o tempo inteiro, mas nem sempre esse pedaço de código vai ser inserido em lugares na estrutura do projeto para o qual ele foi pensado inicialmente. Aí você precisa adaptá-lo para que o objeto se encaixe naquele lugar de forma que você não precise criar outro elemento, com outra nomenclatura, com a mesma estrutura só para arrancar a margem, padding e etc&#8230;

A ideia é que você tenha uma biblioteca de classes reutilizáveis. Se você já leu sobre [OOCSS][1] você entende que a reutilização de código de forma controlada é ótimo para todo o projeto. Dessa forma é possível extender estruturas e controlar designs e layouts de forma mais uniforme e controlada. Eu costumo chamar isso de **classes funcionais**.

Essa classes tem uma única função: modificar uma determinada característica dos elementos.
  
Pode ser que um elemento por padrão contenha um float ou um position. Quando ele foi criado, essa propriedade deve ter sido inserida por conta do ambiente inicial na qual ele seria utilizado. Mas agora essa mesma estrutura será reutilizada em diversos momentos no projeto. Pode ser que o float atrapalhe e você tenha que tirá-lo. Aí você utiliza as classes funcionais para te dar essa força.

Essa combinação de classes é necessária por que você vai reutilizar código HTML durante todo o seu projeto. Um exemplo:



Normalmente são pequenas modificações ESTRUTURAIS. Uso muito pouco classes funcionais para modificar características visuais de layout, por exemplo cores, backgrounds e etc. Apenas em projetos que necessitam ter modificações de templates ou skins. No exemplo acima apenas retiramos a margin-bottom e o border-bottom do elemento.

Nós utilizamos aqui no trabalho um CSS que preparamos, bem básico, com algumas propriedades comuns que utilizamos todos os dias em projetos grandes e pequenos. Esse CSS cresceu de forma ordenada, onde fomos apenas inserindo mais código de acordo com nossa necessidade. Dê uma olhada no código e veja como você pode adequá-lo ao seu projeto: [exemplo do CSS contendo classes funcionais][2] que usamos aqui.

Um exemplo interessante: quando atribuímos display:none para algum elemento, esse elemento não é visto também pelos leitores de tela, ou seja, os leitores de tela simplesmente ignoram esses elementos. Então utilizar algo como um position:absolute com coordenadas negativas e etc para que esse elemento não apareça na tela, mas seja reconhecidos pelos leitores de tela. Como o exemplo abaixo:

<pre class="lang-css">.hideAccessible {
  position:absolute;
  top:-9999px; left:-9999px;
}
</pre>

Sugiro que pegue esse CSS e manipule para deixá-lo de acordo com o seu projeto. Acho que não vai mudar muitas coisas do que já existe, talvez o nome das classes, mas aí é questão de gosto. 😉

Em sites e sistemas onde você **acha** que vai reutilizar o HTML muitas vezes, mudando apenas o CSS para recriar novos layouts, esse método não é recomendável por motivos óbvios. Não existe maneira e nem é muito semântico você tentar posicionar absolutamente um elemento com classes que fazem o elemento ficar com float:right ou float:left. Isso é voltar aos primórdios onde misturávamos formatação com informação.
  
Eu nunca, em 11 anos, tive que reutilizar o mesmo HTML para um redesign ou reformatação da página mudando apenas o CSS. Nós sempre aproveitamos o momento para renovar o código HTML, melhorando a semântica e atualizando o código. Logo, você não vai passar por essa dúvida de usar ou não as classes funcionais em seus projetos.

 [1]: http://tableless.com.br/oocss-ou-css-do-jeito-certo/
 [2]: https://github.com/tableless/exemplos/blob/gh-pages/classesfuncionais.css