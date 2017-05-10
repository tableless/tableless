---
title: Vídeos mais acessíveis com HTML5 – parte I
author: Talita Pagani
type: post
date: 2011-02-15
excerpt: DFXP é a mais recente especificação do W3C baseada em XML para trabalhar com legendas em vídeos do HTML5.
url: /videos-mais-acessiveis-com-html5-parte-i/
tweetbackscheck:
  - 1356439911
shorturls:
  - 'a:3:{s:9:"permalink";s:64:"http://tableless.com.br/videos-mais-acessiveis-com-html5-parte-i";s:7:"tinyurl";s:26:"http://tinyurl.com/3qjxavk";s:4:"isgd";s:19:"http://is.gd/eqXnZc";}'
twittercomments:
  - 'a:1:{i:152060798972342272;s:7:"retweet";}'
tweetcount:
  - 1
dsq_thread_id: 503040005
categories:
  - Acessibilidade
  - HTML5
  - Tecnologia e Tendências
tags:
  - acessibilidade
  - dfxp
  - html5
  - video

---
Até o HTML 4 e XHTML 1.1, a acessibilidade de conteúdo era restrita a elementos basicamente textuais e imagens, mas os documentos de hipertexto são compostos de vários elementos de hipermídia, como áudio e vídeo que, na maioria dos casos, não possuíam seu conteúdo acessível a softwares leitores de tela.

Sabemos que o HTML5 tem potenciais recursos de acessibilidade através de elementos mais semânticos e o W3C tem trabalhado em estender a acessibilidade a recursos de áudio e vídeo.

A tag `video` já possui suporte a vários tipos de legenda, desde soluções simples como o conhecido formato SRT até outros formatos mais robustos e complexos. O W3C formou um grupo de trabalho para o desenvolvimento de padrões de legenda que visam atender as características de acessibilidade e portabilidade: <a title="Timed Text Working Group" href="http://www.w3.org/AudioVideo/TT/" target="_blank">Timed Text Working Group (TT WG)</a>.

Uma das mais recentes recomendações do W3C que é a base dos trabalhos do TT WG é o _Timed Text Markup Language_ (TTML) v.1.0 e foi publicada oficialmente como recomendação em 18 de novembro de 2010. A TTML é uma linguagem de marcação baseada em XML que permite a representação de uma informação textual associada a uma informação de tempo.

A TTML é a linguagem utilizada pelo _Distribution Format Exchange Profile_ (DFXP), uma especificação de tipo de conteúdo de texto cronometrado proposta para substituir antigos formatos de legenda. O DFXP faz parte das especificações de _Timed Text Authoring Format_ (TT AF).

O DFXP oferece mais ferramentas e possibilidades criativas para a apresentação de legendas. É possível criar e aplicar estilos aos textos apresentados, utilizar elementos já conhecidos do HTML (como <br />), modificar alinhamento e trabalhar com múltiplas regiões (_regions_) de apresentação de texto. Por padrão, o layout do DFXP possui as _regions default_ (área localizada abaixo do vídeo) __ e _overlay_ (área que ocupa o espaço do vídeo). Estas _regions_ são customizáveis, você pode formatar plano de fundo, transparência, fonte, etc. E também é possível criar novas _regions_ e posicioná-las onde desejar na cena.

Nas tags que definem os textos, você define os intervalos de tempo e associa cada frase ou um conjunto de frases a uma _region ****_(no próximo artigo veremos a estrutura completa de um arquivo DFXP).

Mas qual a utilidade de múltiplas regiões de legenda? Você pode utilizar a _region_ _overlay_ para apresentar um texto de abertura do vídeo ou utilizar _regions_ personalizadas para descrever ações/sons de uma cena, por exemplo.

E a questão fundamental de acessibilidade: as legendas são associadas, não embutidas no vídeo e, portanto, possibilita que o conteúdo seja escaneado por softwares leitores de tela e por outros mecanismos de varredura (mecanismo de busca, por exemplo). São aspectos hipotéticos que precisam ser avaliados, mas uma das intenções do TT WG é justamente desenvolver especificações para mídias acessíveis de acordo com as diretrizes de acessibilidade do W3C. As restrições sintáticas e semânticas da TTML baseada em XML favorecem a acessibilidade de conteúdo por estarem em conformidade com uma padronização.

Para ilustrar melhor o que foi apresentado neste artigo, dêem uma olhada no exemplo disponibilizado pelo W3C/TT WG: <a title="Demo - This is Coffee" href="http://www.w3.org/2009/02/ThisIsCoffee.html" target="_blank">This is Coffee</a>. É necessário visualizar em um navegador que tenha suporte à tag `video` do HTML5, a API de mídia e os codecs Ogg ou MPEG-4. Este demo mostra o uso de múltiplas _regions_ e efeitos textuais. Aproveite e teste a seleção e cópia de texto da legenda.

No próximo artigo veremos como é estruturado um documento DFXP e revisitar este demo.

## Para saber mais

<a title="Timed Text Authoring Format - Distributed Format Exchange Profile" href="http://www.w3.org/TR/ttaf1-dfxp/" target="_blank">Documentação do W3C para a TTML e o TTAF-DFXP</a>