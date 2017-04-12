---
title: Não se preocupe tanto com o Time To First Byte
author: Diego Eis
type: post
date: 2016-04-11
url: /nao-se-preocupe-tanto-com-o-time-to-first-byte/
categories:
  - Browsers
  - Código
  - Técnicas e Práticas
tags:
  - browser
  - performance
  - servidores

---
O pessoal da [CloudFlare fez um teste muito interessante][1], provando que a medida TTFB (Time To First Byte) não é tão precisa para provarmos que a resposta do servidor de um site é rápida.

O que eles fizeram: em um servidor de teste eles criaram um delay de resposta HTTP para entender o que realmente é medido. A resposta foi que o TTFB não é uma medida tão útil assim. Quando um browser faz o request de uma página no servidor, ele envia alguns headers para especificar algumas coisas como os formatos de respostas aceitos. O servidor responde dizendo que a página está disponível e envia mais alguns headers contendo informações sobre a página, depois, finalmente, envia o conteúdo da página.

No teste da CloudFlare o servidor se comportou um pouco diferente. Quando ele recebe o request, ele enviou a primeira letra do termo **HTTP/1.1 200 OK** (ou seja, a letra H) e depois esperou por 10 segundos antes de enviar o resto dos headers e a página em si. O [código que eles usaram foi escrito em GO][2].

Se você fizer um teste no WebPageTest com a página do servidor de teste do TTFB, o WebPageTest vai reportar o tempo do TTFB que o **H** legou para chegar no servidor e não o tempo que a página em si foi enviada.

Medir o TTFB (Time To First Byte) remotamente, significa que você também está medindo a latência, o que obscurece o que o TTFB realmente tenta medir: quão rápido é o servidor para responder a um request.

No artigo deles há uma descrição bem completa sobre toda essa história. O que me tira um pouco do peso, porque o WebPageTest avisou que o TTFB do Tableless é de 6 segundos. Nenhuma desculpa para não diminuir isso, mas vale pensar no que é mais importante. 😉

[Confira o artigo na íntegra][1].

 [1]: https://blog.cloudflare.com/ttfb-time-to-first-byte-considered-meaningles/
 [2]: https://github.com/jgrahamc/ttfb