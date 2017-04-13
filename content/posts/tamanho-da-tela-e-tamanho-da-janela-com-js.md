---
title: Tamanho da tela e tamanho da janela com JavaScript
author: Diego Eis
type: post
date: 2015-02-09
excerpt: Um breve spike para comparar os valores do tamanho da tela e da janela em diversos dispositivos.
url: /tamanho-da-tela-e-tamanho-da-janela-com-js/
categories:
  - Adaptive Web Design (AWD)
  - JavaScript
  - Mobile
  - Responsive Web Design (RWD)
tags:
  - JavaScript
  - js
  - Mobile

---
Se você trabalha em um projeto que precisa ser em visto em todos os dispositivos, você precisará ir muito além das Media Queries. Um passo adiante será detectar o tamanho da tela do usuário e também o tamanho da janela usada pelo usuário.

Note que os dois são bem diferentes. Enquanto o usuário está um desktop, ele pode modificar o tamanho da janela do browser e consequentemente isso irá alterar o breakpoint da página. Se você faz um layout responsivo, ele verá o layout se adaptando enquanto faz o redimensionamento da página. Embora ele esteja modificando o tamanho da janela, o tamanho da tela (baseada PPI &#8211; Points Per Inch &#8211; da tela) dele não é modificada. 

Você pode usar as duas ocasiões para fazer mudanças no layout ou no funcionamento da página de acordo com o tamanho da janela ou o tamanho da tela. Abaixo, veja um código bem básico, onde você consegue recuperar esses valores:



Redimensionando a janela, os valores mudam e você conhece o tamanho da janela. Para que os valores da tela mudem, modifique a resolução do seu computador e faça um refresh na página. Perceba que aqui no Desktop, ele mostra a resolução que você colocou, que na verdade é uma emulação caso a tela tivesse uma quantidade de pontos por polegada menor do que ela realmente tem.

<img src="http://tableless.com.br/uploads/2015/02/desktop-width-height.png" alt="desktop-width-height" width="1188" height="762" class="alignnone size-full wp-image-46914" srcset="uploads/2015/02/desktop-width-height.png 1188w, uploads/2015/02/desktop-width-height-217x139.png 217w, uploads/2015/02/desktop-width-height-400x257.png 400w" sizes="(max-width: 1188px) 100vw, 1188px" />

Mas até aqui estamos testando isso em um Desktop. Quando testamos isso em um iPhone, que tem densidade de pixels diferente de desktops e toda aquela história, ele vai mostrar o valor real de PPI, que é o valor original da tela do iPhone, sem contar com o valor dobrado da tela retina. Nesse caso, em um iPhone 6, ficaria mais ou menos como a imagem abaixo:

<img src="http://tableless.com.br/uploads/2015/02/iphone-width-height.png" alt="iphone-width-height" width="675" height="1135" class="alignnone size-full wp-image-46912" srcset="uploads/2015/02/iphone-width-height.png 675w, uploads/2015/02/iphone-width-height-83x139.png 83w, uploads/2015/02/iphone-width-height-400x673.png 400w" sizes="(max-width: 675px) 100vw, 675px" />

E agora em um iPad Air:

<img src="http://tableless.com.br/uploads/2015/02/ipad-width-height.png" alt="ipad-width-height" width="880" height="1158" class="alignnone size-full wp-image-46913" srcset="uploads/2015/02/ipad-width-height.png 880w, uploads/2015/02/ipad-width-height-106x139.png 106w, uploads/2015/02/ipad-width-height-400x526.png 400w" sizes="(max-width: 880px) 100vw, 880px" />

Como as janelas dos browsers em mobiles são sempre maximizadas, muito dificilmente elas serão muito menores que o tamanho da tela do aparelho.

Tendo esses valores, você consegue pelo menos ter uma ideia do tamanho do dispositivo que o usuário tem usado. Pelo menos saber qual categoria ergonômica ele se encaixa e então fazer decisões de layout e funcionalidades mais adequadas ao projeto.

As Media Queries do CSS funcionando se baseando no tamanho da janela do browser e não no tamanho da tela. Isso é importante você saber.

Lembrando que aqui você não está detectando o dispositivo. Você não sabe se o cara está usando um iPhone ou um Motorola. Se ele está usando um iOS ou um Android. Mas, teoricamente, isso não precisa importar pra você, já que você faz websites se preocupando com o tamanho da tela e não qual o sistema operacional usado.

Sugiro que você faça testes aí veja essas alterações comparando com os diversos dispositivos. Faz bem para não confundir as bolas quando você precisar desenhar algo específico ou resolver bugs.