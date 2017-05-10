---
title: 'Coisas úteis que não funcionam no IE #2 – Altura e Largura mínima e máxima'
author: Diego Eis
type: post
date: 2006-09-28
url: /coisas-uteis-que-nao-funcionam-no-ie-2-altura-e-largura-minima-e-maxima/
tweetbackscheck:
  - 1356463700
shorturls:
  - 'a:3:{s:9:"permalink";s:95:"http://tableless.com.br/coisas-uteis-que-nao-funcionam-no-ie-2-altura-e-largura-minima-e-maxima";s:7:"tinyurl";s:26:"http://tinyurl.com/3q4f62l";s:4:"isgd";s:19:"http://is.gd/eOyvRb";}'
twittercomments:
  - 'a:0:{}'
dsq_thread_id: 503036054
categories:
  - Artigos
  - Geral
  - Tecnologia e Tendências
tags:
  - Técnicas e Práticas

---
Existe quatro propriedades interessantes no CSS que nos permitem definir uma largura e uma altura mínima e máxima para os elementos. Essas propriedades são: min-width, max-width, min-height e max-height.

Vamos supor que você faça um site fluído, mas que se o usuário estiver usando uma resolução muito grande, o layout não vá até o final da janela, para não deixar o layout tão feio. Tipo, se o layout ficasse bom até a resolução de 1152, mas não ficasse tão bom numa resolução de 1280. Mas que se o usuário redimensionasse a janela ou usasse uma resolução menor, o layout também se adequaria perfeitamente.

Logo, para o layout manter sua aparência, seria perfeito se você pudesse definir uma largura máxima cujo o layout não passaria. Para tanto, você usa a propriedade max-width. O valor da propriedade seria a largura máxima que você gostaria que o layout chegasse.

`div#geral {max-width: 1150px;}`

O mesmo método de utilização é aplicado para as outras propriedades.

Infelizmente, essas propriedades &#8211; que salvariam nossa vida &#8211; não funcionam no Internet Explorer. E quem sabe se via funcionar nos próximos IEs. Aguardemos.

Leia também o primeiro artigo da série: [Coisas úties que não funcionam no IE #1 &#8211; Seletor Inteligente][1]

 [1]: http://tableless.com.br/coisas-uteis-que-nao-funcionam-no-ie-1-seletor-inteligente