---
title: Novas features no Safari
author: Diego Eis
type: post
date: 2016-04-01
excerpt: O que mudou no Safari no iOS 9.3 e o El Capitan 10.11.
url: /novas-features-no-safari/
titulo_personalizado:
  - 'Veja o que mudou no <strong>Safari</strong>'
categories:
  - Browsers
  - Notícias
tags:
  - browser
  - safari

---
Na última semana, uma nova versão do Safari foi publicada com o release do iOS 9.3 e o El Capitan 10.11. As versões iOS 9.3 e Safari 9.1 para o OS X são atualizações importantes que imcorporam várias novas funcionalidades do WebKit. Estas são as features consideradas prontas para serem usadas pelos Devs.

## Elemento Picture

O elemento `<picture>` é um container usado para agrupar diferentes versões de uma mesma imagem usando o elemento `<source>`. Ela é interessante por que oferece um fallback para que o browser possa escolher qual a imagem correta dependendo das capacidades do dispositivo, como densidade de pixels e tamanho de tela. Isso possibilita usar formatos de imagens baseados no conceito de graceful degradation. A habilidade de especificar media queries como atributos no elemento `source` permite a manipulação de imagens nos breakpoints de sites responsivos.

Se quiser saber mais sobre o elemento `picture`, dê uma olhada na [especificação HTML 5.1][1].

## Variáveis no CSS

Variáveis no CSS, formalmente conhecidas como CSS Custom Properties, permite que os devs reduzam a duplicação e a complexidade de código, tornando mais fácil a manutenção de CSS. 

Leia mais sobre variáveis no CSS [aqui][2] e [aqui][3].

## Font Feature Properties

O **Font Feature Properties** permite usar estilos especiais de textos e efeitos disponíveis em fontes como ligaduras e small-caps. Esses efeitos não são simulações feitas pelo browser, mas os estilos são desenhados pelo author. Existem fonts que você pode usar ligaduras ou não. Se essa opção estiver disponível na familia da font, você poderá optar por usar.

<img src="http://tableless.com.br/uploads/2016/04/IMG_0252.jpeg" alt="IMG_0252" width="2178" height="739" class="alignnone size-full wp-image-53572" />

<img src="http://tableless.com.br/uploads/2016/04/Screen-Shot-2016-04-01-at-3.01.27-PM.png" alt="Screen Shot 2016-04-01 at 3.01.27 PM" width="382" height="200" class="alignnone size-full wp-image-53573" />

Você pode [ler mais sobre isso aqui][4].

## Propriedade Will Change

A propriedade **will-change** permite que você adiante para o browser quais propriedades irão ser modificadas em um elemento. Essa dica dada para os browsers, os ajuda a fazer otimizações nesses efeitos antes que eles aconteçam, melhorando um bocado a performance.

## Entre outras

Houveram outras mudanças no Safari ligadas ao browser em si. Por exemplo: eles retiraram (aleluia!) aquele delay de 350 milisegundos ao fazer o tap em elementos. Além de atualizações no Web Inspector etc&#8230; Veja todas as mudanças aqui: <https://webkit.org/blog/6008/new-web-features-in-safari/>

 [1]: http://w3c.github.io/html/semantics-embedded-content.html#the-picture-element
 [2]: http://tableless.com.br/como-usar-variaveis-no-css-de-forma-nativa/
 [3]: https://webkit.org/blog/5989/css-variables-in-webkit/
 [4]: https://webkit.org/blog/5735/css-font-features/