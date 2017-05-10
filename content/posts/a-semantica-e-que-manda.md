---
title: A Semântica é que manda
author: Diego Eis
type: post
date: 2006-04-06
url: /a-semantica-e-que-manda/
tweetbackscheck:
  - 1356439579
shorturls:
  - 'a:3:{s:9:"permalink";s:47:"http://tableless.com.br/a-semantica-e-que-manda";s:7:"tinyurl";s:26:"http://tinyurl.com/42m5fl8";s:4:"isgd";s:19:"http://is.gd/GMaZgS";}'
twittercomments:
  - 'a:0:{}'
dsq_thread_id: 503035137
categories:
  - Artigos
  - Geral
tags:
  - acessibilidade
  - cotidiano
  - Técnicas e Práticas

---
Um leitor do Tableless enviou um artigo muito interessante: [Divless][1].

Muitos desenvolvedores que começam a abordar os padrões tem muita dificuldade porque não prestam atenção em uma coisinha simples: semântica.
  
Já cansei de falar em curso, em artigos, podcasts e tudo mais&#8230; Semântica é a alma do negócio. Semântica é a chave do desenvolvimento com padrões web. Se você entende semântica, você tem meio caminho andado.

Todo mundo já sabe que cada tag, tem uma função semântica. Se você quer definir um título as tags apropriadas serão H1, H2, H3&#8230; Se você quiser fazer um parágrafo, usa-se P. Simples assim.
  
A tag DIV serve para dividir o layout em seções. O layout geralmente é dividido em partes como o cabeçalho, o menu, a coluna da esquerda, a coluna do meio, o rodapé etc. Para separar ou demarcar estas seções a tag semanticamente correta é a DIV. Nada de tabelas, nada de span, nada de p ou qualquer outra tag. O DIV foi designado para fazer este trabalho. Usar qualquer outra tag para fazer isto é errado.

Sem contar que criar um código semanticamente correto vai te ajudar bastante na hora de implementar o CSS. Você vai ter mais variedade de tags. Vai conseguir identificar melhor as partes do layout. Imagine se o layout fosse feito com listas. Você teria que colocar classe ou ids em todos os objetos para poder identificá-los para manipulá-los com CSS. Iria se tornar uma coisa totalmente contraproducente.

No artigo do camarada, ele fez alguns exemplos de layout usando apenas listas. Bom, nada mais fácil&#8230; Se você quiser você pode fazer layouts usando apenas a tag B ou qualquer outra tag que quiser. O CSS lhe permite manipular as características dos objetos, mas o CSS não muda a função semântica do elemento.

O que você acha?

<small>Nunca é demais voltar nestes assuntos para fixar melhor na memória. Já dizia o velho sentado: A repetição faz a gravação. </small>

 [1]: http://somerandomdude.net/projects/webdev/divless/