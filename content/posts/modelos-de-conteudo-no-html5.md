---
title: Modelos de conteúdo no HTML5
author: Diego Eis
type: post
date: 2010-07-20
excerpt: Sobre modelos de conteúdo no HTML5.
url: /modelos-de-conteudo-no-html5/
aktt_notify_twitter:
  - no
tweetbackscheck:
  - 1356449723
shorturls:
  - 'a:3:{s:9:"permalink";s:52:"http://tableless.com.br/modelos-de-conteudo-no-html5";s:7:"tinyurl";s:26:"http://tinyurl.com/3sd6vhb";s:4:"isgd";s:19:"http://is.gd/MFP3Ld";}'
twittercomments:
  - 'a:0:{}'
dsq_thread_id: 503039489
categories:
  - HTML5
  - Técnicas e Práticas
tags:
  - 2010
  - html5
  - padroes web
  - tableless

---
Este texto faz parte do [capítulo 4][1] da [apostila e guia de referência de HTML5][2].

Há pequenas regras básicas que nós já conhecemos e que estão no HTML desde o início. Estas regras definem onde os elementos podem ou não estar. Se eles podem ser filhos ou pais de outros elementos e quais os seus comportamentos.

Dentre todas as categorias de modelos de conteúdo, existem dois tipos de elementos: elementos de linha e de bloco.   
Os elementos de linha marcam, na sua maioria das vezes, texto. Alguns exemplos: **a**, **strong**, **em**, **img**, **input**, **abbr**, **span**.

Os elementos de blocos são como caixas, que dividem o conteúdo nas seções do layout.

Abaixo segue algumas premissas que você precisa relembrar e conhecer:

  * Os elementos de linha podem conter outros elementos de linha, dependendo da categoria que ele se encontra. Por exemplo: o elemento **a** não pode conter o elemento **label**.
  * Os elementos de linha nunca podem conter elementos de bloco.
  * Elementos de bloco sempre podem conter elementos de linha.
  * Elementos de bloco podem conter elementos de bloco, dependendo da categoria que ele se encontra. Por exemplo, um parágrafo não pode conter um DIV. Mas o contrário é possível.

Estes dois grandes grupos podem ser divididos em categorias. Estas categorias dizem qual modelo de conteúdo o elemento trabalha e como pode ser seu comportamento.

### Categorias

Cada elemento no HTML pode ou não fazer parte de um grupo de elementos com características similares. As categorias estão a seguir. Manteremos os nomes das categorias em inglês para que haja um melhor entendimento:

  * Metadata content
  * Flow content
  * Sectioning content
  * Heading content
  * Phrasing content
  * Embedded content
  * Interactive content

Abaixo segue como as categorias estão relacionadas de acordo com o WHATWG:



### Metadata content

Os elementos que compõe a categoria Metadata são:

  * base
  * command
  * link
  * meta
  * noscript
  * script
  * style
  * title

Este conteúdo vem antes da apresentação, formando uma relação com o documento e seu conteúdo com outros documentos que distribuem informação por outros meios.

### Flow content

A maioria dos elementos utilizados no body e aplicações são categorizados como Flow Content. São eles:

  * a
  * abbr
  * address
  * area (se for um decendente de um elemento de mapa)
  * article
  * aside
  * audio
  * b
  * bdo
  * blockquote
  * br
  * button
  * canvas
  * cite
  * code
  * command
  * datalist
  * del
  * details
  * dfn
  * div
  * dl
  * em
  * embed
  * fieldset
  * figure
  * footer
  * form
  * h1
  * h2
  * h3
  * h4
  * h5
  * h6
  * header
  * hgroup
  * hr
  * i
  * iframe
  * img
  * input
  * ins
  * kbd
  * keygen
  * label
  * link (Se o atributo **itemprop** for utilizado)
  * map
  * mark
  * math
  * menu
  * meta (Se o atributo **itemprop** for utilizado)
  * meter
  * nav
  * noscript
  * object
  * ol
  * output
  * p
  * pre
  * progress
  * q
  * ruby
  * samp
  * script
  * section
  * select
  * small
  * span
  * strong
  * style (Se o atributo **scoped** for utilizado)
  * sub
  * sup
  * svg
  * table
  * textarea
  * time
  * ul
  * var
  * video
  * wbr
  * Text

Por via de regra, elementos que seu modelo de conteúdo permitem inserir qualquer elemento que se encaixa no Flow Content, devem ter pelo menos um descendente de texto ou um elemento descendente que faça parte da categoria **embedded**.

 [1]: http://tableless.com.br/html5/?chapter=4
 [2]: http://tableless.com.br/html5/