---
title: Introdução sobre Media Queries
author: Diego Eis
type: post
date: 2009-07-06
excerpt: Media Queries é a utilização de Media Types com uma ou mais expressões envolvendo características de uma media para definir formatações para diversos dispositivos. O browser ou a aplicação lê as expressões definidas na query, caso o dispositivo se encaixe nestas requisições, o CSS será aplicado.
url: /introducao-sobre-media-queries/
aktt_notify_twitter:
  - no
tweetbackscheck:
  - 1356397672
shorturls:
  - 'a:3:{s:9:"permalink";s:54:"http://tableless.com.br/introducao-sobre-media-queries";s:7:"tinyurl";s:26:"http://tinyurl.com/4xzfx8x";s:4:"isgd";s:19:"http://is.gd/zKPYui";}'
twittercomments:
  - 'a:0:{}'
dsq_thread_id: 503033160
categories:
  - CSS
  - O Básico
  - Técnicas e Práticas
tags:
  - CSS
  - CSS3
  - iphone
  - media queries
  - Media Types
  - Na Prática
  - safari
  - tecnicascss

---
Eu não posso explicar sobre Media Queries sem um pouco do contexto das Media Types, que foram a primeira versão de um esforço para direcionar a formatação CSS para determinados tipos de meios de acesso.

O HTML foi criado para ser portável, ou seja, ele deve ser lido e interpretado por qualquer tipo de dispositivo. Cada dispositivo exibe HTML de uma determinada maneira. Logo, a forma com que você formata o layout precisa ser diferente para cada dispositivo. Por exemplo, se você visita um site por um desktop, a experiência será totalmente diferente caso você visite o mesmo site por um dispositivo móvel. São dispositivos diferentes, com formas totalmente diferentes de navegação e uso. 

Mas o exemplo acima é muito comum. Existem outras outros cenários que precisamos prever para controlar a formatação do site, como por exemplo, quando o usuário imprimir sua página. Quando alguém imprimi a página de um artigo no site do UOL, Terra ou qualquer site de conteúdo, vários elementos não precisam ser impressos, começando pelo menu, barra lateral, rodapé e etc. O texto poderia ser melhor formatado para que a leitura em papel fosse mais confortável. Essa diferença entre dispositivos é controlada pelas %%media types%%. Veja uma lista do que pode ser controlado abaixo:

  * **all** este valor é usado para que o código CSS seja aplicado para todos os dispositivos.
  * **braille** para dispositivos táteis.
  * **embossed** para dispositivos que imprimem em Braille.
  * **handheld** para dispositivos de mão, celulares e outros dispositivos deste perfil. Normalmente com telas pequenas e banda limitada.
  * **print** para impressão em papel.
  * **projection** para apresentações, como PowerPoint. Este valor foi inventado pelo pessoal da Opera. MUITO útil.
  * **screen** para dispositivos com telas coloridas e alta resolução.
  * **speech** para sintetizadores de voz. O CSS 2 tem uma especificação de CSS chamada Aural (http://www.w3.org/TR/CSS2/aural.html) que podemos “formatar” a voz de leitores de tela e outros sintetizadores.
  * **tty** para dispositivos que utilizam uma grade fixa para exibição de caracteres, como teletypes, terminais, dispositivos portáteis com display limitado.
  * **tv** para dispositivos como televisores, ou seja, com baixa resolução, com boa quantidade de cores e scroll limitado.

A aplicação é muito simples: basta adicionar a linha comum de %%link%% para seu CSS, inserindo um atributo %%media%% e adicionando o valor desejado:

<pre class="lang-html">&lt;link rel="stylesheet" href="estilo.css" type="text/css" media="handheld"&gt;
</pre>

Note que neste exemplo estou chamando um arquivo CSS, que será destinado para funcionar em dispositivos de media \*\*HANDHELD\*\*: aparelhos móveis, celulares com tela pequena e aparelhos similares (já usou PalmTop?). Logo, esse CSS não será aplicado quando o usuário visitar o site utilizando um desktop. Para tanto, teríamos que utilizar media SCREEN:

<pre class="lang-html">&lt;link rel="stylesheet" href="estilo.css" type="text/css" media="screen"&gt;
</pre>

## O problema

Você já notou que todo dia surgem novos dispositivos, com diversos tamanhos e hardwares parecidos com os desktops. Qualquer celular meia boca hoje tem a configuração mais parruda que muitos computadores por aí. Principalmente a configuração da tela, onde as fabricantes tem dado mais atenção nos últimos anos. Logo, não tem motivo para prepararmos um layout e um CSS com media type HANDHELD para o iPhone, já que ele não se encaixa nessa categoria. Entretanto, o iPhone também não é nem de longe um desktop. Aí existe o problema: a media type screen se encaixaria para direcionarmos o a formatação para o iPhone e companhia, mas a especificação é clara quando diz que a media type screen é para desktops e computadores. Como fazer agora?

## A solução: Media Queries

As Media Queries definem condições para que o CSS seja utilizado em cenários específicos. Se essas condições forem aprovadas, ou seja, se o dispositivo de adequar a todas as condições estabelecidas na sua Media Querie, o CSS será aplicado.

<pre class="lang-html">&lt;link rel="stylesheet" href="estilo.css" media="screen and (max-width: 480px)"&gt;
</pre>

Acima especificamos que o arquivo \*\*estilo.css\*\*, será aplicado em dispositivos que se enquadram na condição de \*\*screen\*\* (ou seja, que tem uma tela com alta capacidade de cores) e com uma largura máxima de 480px.

Há uma lista de características que você pode utilizar aqui para selecionar os dispositivos que você quiser:

  * width
  * height
  * device-width
  * device-height
  * orientation
  * aspect-ratio
  * device-aspect-ratio
  * color
  * color-index
  * monochrome
  * resolution
  * scan
  * grid

Geralmente usamos as Media Queries dentro código CSS, que é bem mais organizado. Você linka seu CSS normalmente no HEAD do seu documento:

<pre class="lang-html">&lt;link rel="stylesheet" href="estilo.css"&gt;
</pre>

E dentro do código CSS, você vai separar os famosos \*\*breakpoints\*\*, que são as condições da largura das telas do dispositivos, que definem quando cada bloco de CSS será utilizado. Veja o código abaixo:

<pre class="lang-css">/* Código geral, que será herdado por qualquer dispositivos.
   nesse caso, seria o código usado no desktop, na maioria das   vezes. 
   Se você já conhecer a ideia do Mobile First, esse primeiro código será destinado para mobiles.
*/
a {color: blue;}

/* 
 Pra dispositivos que tem uma largura mínima de 768 pixels. Tablets, por exemplo.
*/
@media screen and (min-width: 768px) {
  a {color: yellow;}
}

/* 
 Com uma largura mínima de 992 pixels. Monitores por exemplo.
*/
@media screen and (min-width: 992px) {
  a {color: green;}
}

/* 
 Dispositivos com largura mínima de 1200 pixels. Por exemplo TVs.
*/
@media screen and (min-width: 1200px) {
  a {color: black;}
}
</pre>

E assim você vai escrevendo seu CSS e manipulando a formatação do layout de acordo com dispositivo desejado.