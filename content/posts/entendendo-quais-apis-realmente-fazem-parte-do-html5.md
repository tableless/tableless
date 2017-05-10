---
title: Entendendo quais APIs (realmente) fazem parte do HTML5
author: Talita Pagani
type: post
date: 2012-05-02
excerpt: Sabemos que o HTML5 não se trata apenas de marcação, mas também de um conjunto de novas funcionalidades encapsuladas em APIs que podem ser acessadas via JavaScript. Porém, algumas destas APIs não fazem parte do núcleo do HTML5.
url: /entendendo-quais-apis-realmente-fazem-parte-do-html5/
tweetbackscheck:
  - 1356393277
shorturls:
  - 'a:3:{s:9:"permalink";s:31:"http://tableless.com.br/?p=5981";s:4:"isgd";s:19:"http://is.gd/cQ4YMB";s:7:"tinyurl";s:26:"http://tinyurl.com/bs96pda";}'
twittercomments:
  - 'a:0:{}'
dsq_thread_id: 672754554
categories:
  - HTML5
  - JavaScript
tags:
  - api
  - desenvolvimento web
  - diferenças
  - html5
  - JavaScript
  - padroes web
  - w3c

---
Com o HTML5 ganhando força no mercado de desenvolvimento web, maior tem sido o interesse dos desenvolvedores em compreender seus recursos, novas APIs e tecnologias adjacentes. E é aí que acontece uma grande confusão.

Sabemos que o HTML5 não se trata apenas de marcação, mas também de um conjunto de novas funcionalidades encapsuladas em APIs que podem ser acessadas via JavaScript.

Porém, há APIs em processo de padronização pelo W3C que não fazem parte da especificação do HTML5. Elas são especificações relacionadas não intrínsecas ao HTML5, ou seja, a utilização delas não está estritamente atrelada ao uso da linguagem. Algumas, inclusive, faziam parte do _core_ do HTML5, mas hoje estão dissociadas e contam com uma especificação separada, como é o caso do [Web Storage][1].

As APIs próprias do HTML5 são mais específicas às funcionalidades que atuam no escopo da página e da manipulação de elementos. Elas se relacionam em grande parte com o [DOM][2]. Já as outras APIs geralmente trabalham com funcionalidades um pouco mais complexas, como armazenamento de dados e manipulação de arquivos, por exemplo.

Algumas das novas APIs que estão contidas na especificação do HTML5 são:

  * Canvas
  * Validação de formulários
  * Controles de áudio e vídeo
  * Application cache / offline applications
  * Funcionalidade de markup editável (contenteditable)
  * Drag and drop
  * Novas funcionalidades para manipulação do histórico do navegador

Algumas das novas APIs que são desenvolvidas em conjunto pelo WHATWG e W3C e trabalham muito bem com HTML5 mas que não são (mais) exclusivas dele:

  * Web Storage (localStorage e sessionStorage)
  * Web messaging
  * Microdata
  * Web Workers
  * Web Sockets

E algumas especificações relacionadas, que não são desenvolvidas pelo WHATWG e possuem especificações publicadas separamente pelo W3C:

  * Geolocation
  * File API
  * Indexed DB
  * File Writer
  * Notifications

O gráfico abaixo, desenvolvido por Sergey Mavrody fornece uma boa visão deste contexto e do relacionamento entre as novas APIs e o HTML, além de mostrar o status de desenvolvimento de cada uma destas especificações. Note que o Web Storage ainda está incluído junto à especificação do HTML5, mas isto já mudou.

<div id="attachment_5982" style="width: 650px" class="wp-caption aligncenter">
  <a href="http://tableless.com.br/uploads/2012/04/800px-HTML5-APIs-and-related-technologies-by-Sergey-Mavrody.png"><img class=" wp-image-5982 " src="http://tableless.com.br/uploads/2012/04/800px-HTML5-APIs-and-related-technologies-by-Sergey-Mavrody.png" alt="HTML5 e as APIs relacionadas" width="640" height="434" srcset="uploads/2012/04/800px-HTML5-APIs-and-related-technologies-by-Sergey-Mavrody.png 800w, uploads/2012/04/800px-HTML5-APIs-and-related-technologies-by-Sergey-Mavrody-300x203.png 300w" sizes="(max-width: 640px) 100vw, 640px" /></a>
  
  <p class="wp-caption-text">
    HTML5 e as APIs relacionadas por Sergey Mavrody
  </p>
</div>

Portanto, muitas vezes quando falamos das novas possibilidades do HTML5, na verdade estamos nos referindo à toda uma nova geração de tecnologias para a web.

O que podemos concluir disso tudo é que o HTML5, sozinho, não faz uma web melhor. Porém, ele ajudou a movimentar o mercado rumo ao desenvolvimento de novas tecnologias. Saímos da zona de conforto que já estávamos há alguns anos. O cenário que temos agora é de uma série de tecnologias web que, trabalhando em conjunto, fazem uma web melhor, para as pessoas e para os desenvolvedores 😉

### Referências:

[Especificação do HTML pelo WHATWG][3]
  
[W3C &#8211; HTML5 differences from HTML4][4]
  
[HTML5 &#8211; Wikipedia][5]

 [1]: http://www.w3.org/TR/webstorage/
 [2]: http://tableless.com.br/tenha-o-dom/
 [3]: http://www.whatwg.org/specs/web-apps/current-work/multipage/introduction.html
 [4]: http://dev.w3.org/html5/html4-differences/#apis
 [5]: http://en.wikipedia.org/wiki/HTML5