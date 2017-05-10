---
title: Versionamento inteligente para mobiles
author: Diego Eis
type: post
date: 2010-01-20
excerpt: Filtrar mobiles pelo tipo de aparelho é muito comum. A moda é versionar o site para iPhone. Mas há outros aparelhos com a mesma capacidade de renderização que podem se beneficiar.
url: /versionamento-inteligente-para-mobiles/
aktt_notify_twitter:
  - no
tweetbackscheck:
  - 1356453509
shorturls:
  - 'a:3:{s:9:"permalink";s:62:"http://tableless.com.br/versionamento-inteligente-para-mobiles";s:7:"tinyurl";s:26:"http://tinyurl.com/3nn6jq9";s:4:"isgd";s:19:"http://is.gd/sSiR0n";}'
twittercomments:
  - 'a:3:{i:47756324984983552;s:6:"137244";i:130255212161146881;s:7:"retweet";i:129968334593732608;s:7:"retweet";}'
tweetcount:
  - 4
dsq_thread_id: 503039310
categories:
  - Browsers
  - CSS
  - Geral
  - Mobile
  - Técnicas e Práticas
  - Tecnologia e Tendências
tags:
  - acessibilidade
  - android
  - CSS
  - dispositivos moveis
  - google
  - html
  - iphone
  - media queries
  - Na Prática

---
O iPhone fez a festa dele. Todo mundo gostou do que viu e usou. Acontece que não só de iPhone vive o homem, e há pessoas por aí que não gostam do aparelho por motivos diversos. Há mercado para todos e por isso é natural que apareçam outros aparelhos com novos sistemas. Acontece que o lançamento do iPhone criou uma moda de [criar versões dos sites específicas para ele][1]. No começo isso foi ótimo. Mas agora, isso priva diversos celulares similares ao iPhone de terem uma boa experiência de navegação. É o caso de usuários de Android.

O Android é o novo sistema operacional para mobiles do Google. Até para um AppleBoy, como eu, o sistema é interessante. Tem a interface bem acabada, app&#8217;s amigáveis e etc. Ele faz muito bem o papel dele. O Engine de renderização do browser dele é WebKit. O mesmo engine que o Safari Mobile utiliza. E não estou falando de versões antigas do Webkit como alguns outros celulares utilizam. O Android utiliza as versões mais atuais do Webkit, com suporte extenso a CSS e HTML. Portanto, um site que teoricamente foi feito apenas para iPhone, pode ser visualizado da mesma maneira pelos usuários de Android.

Aí entra outra questão: provavelmente você deve ter pensado que seria apenas fazer um script de detecção de browser, capturando as visitas de Safari Mobile e Android e pronto. É aí que você se engana. Já há vários outros aparelhos que estão utilizando engines parecidas e que podem renderizar sua &#8220;versão de iphone&#8221;. Exatamente por isso, que você precisa fazer um filtro por características e não por browser. Fazemos isso utilizando [Media Queries][2]. 

As Media Queries permitem fazer um pequeno filtro, onde definimos as características do dispositivo que acessará a página. Com isso, podemos definir um CSS específico para aquele grupo de dispositivos que se encaixaram no seu filtro. Veja um exemplo abaixo:

<pre lang="css" line="1"><link rel="stylesheet" href="style.css" type="text/css" media="screen and (min-width:481px)" />

<link rel="stylesheet" href="mob.css" type="text/css" media="screen and (max-width:480px)" />
</pre>

A media que fiz é muito simples de ser entendida. A primeira linha engloba dispositivos que tem tela colorida, com uma resolução de largura mínima de 481px, isso inclui seu monitor, notebook e etc. A outra linha engloba dispositivos com uma largura máxima de 480px, ou seja, iPhones, Androids e dispositivos que seguem esse mesmo esquema de resolução e etc.

Dessa forma, você filtra os dispositivos e não os browsers dos aparelhos. Isso previne que algum celular, tão bom quanto o iPhone e o Android fiquem de fora de ter uma boa experiência de uso. Quer fazer um teste interessante? Se você estiver utilizando um browser que aceita media queries, redimensione a janela para uma largura menor que 480px. Você verá o Tableless chaveando os estilos automaticamente. Perceba que alguns elementos são reformatados e outros retirados do layout. 

O filtro ainda não está completo porque não estamos contemplando os aparelhos que não aceitam meda queries, mas são mobiles. Para isso, usaríamos os [Media Types][3], com valor de **handheld**. Embora celulares que aceitem os Media Types não tenham um bom suporte de CSS, podemos fazer pelo menos uma formatação de texto, cor e background. Celulares que utilizam Opera Mini, terão uma ótima experiência.

É sempre aquela mesma velha idéia: dar a melhor experiência para todos os meios de acesso. Sempre.

 [1]: http://tableless.com.br/porque-so-para-o-iphone
 [2]: http://tableless.com.br/introducao-sobre-media-queries
 [3]: http://tableless.com.br/o-que-sao-media-types