---
title: Mudanças no IE7
author: Diego Eis
type: post
date: 2006-09-29
url: /mudancas-no-ie7/
tweetbackscheck:
  - 1356453935
shorturls:
  - 'a:3:{s:9:"permalink";s:39:"http://tableless.com.br/mudancas-no-ie7";s:7:"tinyurl";s:26:"http://tinyurl.com/3my4sjw";s:4:"isgd";s:19:"http://is.gd/zoMYse";}'
twittercomments:
  - 'a:0:{}'
dsq_thread_id: 503036071
categories:
  - Browsers
  - Geral
tags:
  - cotidiano

---
O Internet Explorer 7 está vindo quase que como uma promessa a muito tempo esperada. Até hoje tentei evitar de falar sobre o IE7 porque ele era apenas uma versão beta e eu gostaria de esperar para conferir o que iria realmente acontecer com este browser.

Por ser um browser muito antigo, o IE tem uma série de bugs que até hoje fazem os desenvolvedores perderem alguns fios de cabelos no desenvolvimento de algum projeto. CSS é uma ferramenta que deve ser usada sem moderação, sem barreira alguma, mas infelizmente o IE diminui toda a utilidade de muitas das propriedades úteis que existem no CSS.
  
O IE7 ganhará algumas atualizações que pretendem transformar nossa vida para melhor (!). [Neste post][1] feito pelo Markus Mielke para o IEBlog mostra uma lista enorme de pontos que foram/serão corrigidos no IE7.

Todos os bugs listados no [positioniseverything.net][2] foram corrigidos.
  
Foram corrigidos um número muito grande de bugs de renderização e suporte de CSS. Por exemplo, uma coisa simples que não funciona no IE6 e que vai passar a funcionar no IE7 é o position: fixed;.

Alguns exemplos:

  * O Overflow funcionará corretamente. Agora quando você dizer que um elemento deve ter 100px de altura e seu texto ultrapassar isso, o IE7 respeitará essa altura e o texto irá transbordar para fora do elemento. Como deve ser.
  * Agora poderemos formatar os selects como quisermos.
  * Quando você coloca uma borda pontilhada de 1px em um elemento, o IE6 em vez de pontilhar a borda, ele traceja. Isso foi resolvido com o IE7. Agora vão aparecer pontinhos em vez de traços.
  * O Prologo XML (< ?xml>) não irá mais deixar o browser em quirks mode. No IE6, se você coloca o XML Prologo em seu documento, o browser passa a funcionar em [Quirks Mode][3].
  * Você poderá usar a pseudo-classe :hover não apenas para elementos .
  * Agora o background-attachment: fixed; funciona.
  * Min/max width/height agora são suportados.
  * Bordas transparentes também foram habilitadas agora.
  * E uma das melhores notícias, o IE7 suportará PNG com canais alpha!  🙂

E um monte de outras coisas.

Acho que o IE7 não será um problemão como andam esperando. Ainda não dá para ter certeza e nem podemos confiar que ele não terá outros bugs escondidos.
  
A única coisa que me preocupa mesmo é que apenas Windows Originais terão a atualização para o IE7&#8230; Já sabemos como funciona a coisa aqui no Brasil. Talvez apenas umas poucas pessoas terão o IE7. Melhor que nenhum.

Mais:

  * [Details on our CSS changes for IE7][1]
  * <http://www.positioniseverything.net/explorer.html>
  * [Quirks Mode][3]

 [1]: http://blogs.msdn.com/ie/archive/2006/08/22/712830.aspx
 [2]: http://www.positioniseverything.net/explorer.html
 [3]: http://en.wikipedia.org/wiki/Quirks_mode