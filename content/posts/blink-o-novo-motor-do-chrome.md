---
title: 'Blink: o novo motor do Chrome'
author: Diego Eis
type: post
date: 2013-04-04
excerpt: Google cria seu próprio motor de renderização baseado no WebKit.
url: /blink-o-novo-motor-do-chrome/
dsq_thread_id: 1185565870
categories:
  - Notícias
tags:
  - 2013
  - blink
  - Browsers
  - chrome
  - webkit

---
O [Chromium][1] (que é o projeto por trás do Chrome e do Chromium OS) utiliza uma arquitetura de múltiplos processos que é diferente do WebKit. Essa arquitetura mudou muito durante a existência do Chrome, dificultando a integração entre o browser e o WebKit. Por isso o pessoal do Google está apresentando hoje o Blink, seu novo motor de renderização baseado no WebKit.

> This was not an easy decision. We know that the introduction of a new rendering engine can have significant implications for the web.

O [Blink][2] é uma decisão da equipe do Chromium de fazer um fork do projeto do WebKit e criar seu novo motor de renderização, que também será open source.

Essa mudança de caminho não trará quase que nenhuma mudança para os desenvolvedores. Mas eles já adiataram que removerão algo em torno de 7.000 arquivos com mais de 4.5 milhões de linhas de código. &#8220;Over the long term a healthier codebase leads to more stability and fewer bugs.&#8221; [diz no post oficial][3].

> Throughout this transition, we’ll collaborate closely with other browser vendors to move the web forward and preserve the compatibility that made it a successful ecosystem. 

A boa notícia é que o Google é super comprometido com o projeto do WebKit. Tanto o Google quanto a Apple trabalharam juntos durante muito tempo para melhorar o WebKit para fazê-lo o que ele é hoje. Novidades virão com certeza. É só esperar.

 [1]: http://www.chromium.org/
 [2]: http://www.chromium.org/blink
 [3]: http://blog.chromium.org/2013/04/blink-rendering-engine-for-chromium.html