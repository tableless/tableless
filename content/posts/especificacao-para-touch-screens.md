---
title: Especificação para touch screens
author: Diego Eis
type: post
date: 2011-06-22
excerpt: Interações em interfaces touch são diferentes das interfaces baseadas com mouse. Hoje temos pleno controle das ações baseadas com mouse, mas este controle não pode ser expandido para as interfaces touch. As ações e as forma de comportamento do usuário são diferentes.
url: /especificacao-para-touch-screens/
tweetbackscheck:
  - 1356391427
shorturls:
  - 'a:3:{s:9:"permalink";s:56:"http://tableless.com.br/especificacao-para-touch-screens";s:7:"tinyurl";s:26:"http://tinyurl.com/3uqkomg";s:4:"isgd";s:19:"http://is.gd/eVQT1p";}'
twittercomments:
  - 'a:29:{i:126272505781555203;s:7:"retweet";i:126004282158878720;s:7:"retweet";i:125993918478303233;s:7:"retweet";i:125993502457864192;s:7:"retweet";i:164742954123132930;s:7:"retweet";i:164739646620835840;s:7:"retweet";i:184333298284244994;s:7:"retweet";i:200555587027738625;s:7:"retweet";i:200267957933318146;s:7:"retweet";i:204989362314821632;s:7:"retweet";i:204976737002598400;s:7:"retweet";i:204968681162276865;s:7:"retweet";i:204968341297823745;s:7:"retweet";i:204968330241654784;s:7:"retweet";i:204967937495408641;s:7:"retweet";i:218750502446440452;s:7:"retweet";i:218740519315054593;s:7:"retweet";i:218739630785302528;s:7:"retweet";i:237942847175806976;s:7:"retweet";i:235769811542609921;s:7:"retweet";i:235769237673750529;s:7:"retweet";i:250272917135425536;s:7:"retweet";i:255700479366029312;s:7:"retweet";i:255700375867375617;s:7:"retweet";i:263317060619206657;s:7:"retweet";i:263315085672448000;s:7:"retweet";i:263310844518080512;s:7:"retweet";i:271647463423762434;s:7:"retweet";i:271644654305435648;s:7:"retweet";}'
tweetcount:
  - 52
dsq_thread_id: 503040338
categories:
  - Browsers
  - HTML
  - Mercado e Comportamento
  - Mobile
  - Tecnologia e Tendências
tags:
  - 2011
  - cotidiano
  - desenvolvimento web
  - html5
  - interface mobiles
  - internet
  - internetmovel
  - mobiles
  - mobilidade

---
Até alguns anos atrás nós acessávamos a internet apenas utilizando computadores e celulares. Hoje existem aparelhos de diversos tipos. Temos até dispositivos como o [Surface][1], ainda que seu uso seja mais restrito e específico. Mas não demora muito que outros dispositivos surjam e preencham alguma lacuna escondida. O importante é entender que cada aparelho tem sua forma de interação.

Hoje, as interfaces touch estão maduras e estáveis, que chegam a inspirar as interfaces dos sistemas desktops. Vide o que aconteceu com o OS X Lion e com o Windows 8. As principais ideias foram retiradas de suas respectivas interfaces mobiles: o Windows do Windows Phone e o Lion do OS X para iPad.
  
As interfaces mobiles e as interfaces desktop ficarão mais homogêneas com o passar do tempo, se assemelhando cada vez mais, contudo, as interações são totalmente diferentes. As interfaces criadas para cada dispositivo nos ajudam a distinguir os ambientes e também a forma com que o usuário interage.

Estamos acostumados com a experiência de interação com a ajuda do mouse. Isso foi desde os primórdios e provavelmente ainda será por bastante tempo. Nós desenhamos interfaces para ações baseadas no mouse ou qualquer aparelho que controle a setinha da sua tela. Criar interfaces touch é algo relativamente novo. Nós trouxemos ideias da interação com mouse para os dispositivos touch, mas grande parte das interações precisaram ser reinventadas porque o modo, o ato, a forma de interagir com a informação é diferente. Na interface touch você não &#8220;coloca o mouse&#8221; em cima do elemento. Você não utiliza teclas de atalho para executar ações. Normalmente as ações importantes estão expostas na interface, facilitando o acesso rápido. Isso é muito importante porque nos ensina criar interfaces mais intuitivas, com a curva de aprendizado menor.
  
Há também o outro lado da moeda, onde detalhes das interfaces touch não podem ser portadas para interfaces baseadas em mouse. Lembre agora na forma de como você gira uma imagem em um dispositivo touch e como você gira essa mesma imagem utilizando um mouse. A interface muda, o seu comportamento muda. 

Sabendo dessas limitações você deve entender que não podemos simplesmente portar o visual de um determinado site para um dispositivo touch. Você pode dizer que &#8220;hoje fazemos isso e até agora está funcionando muito bem&#8221;. Mas pense melhor&#8230; a grande maioria dos sites que você visita hoje no iPad ou qualquer outro tablet, por exemplo, são sites onde a sua interação é limitada. O que você faz em um site hoje em dia? Clica nos links e lê. Salvo às vezes quando você visita um site mais &#8220;animadinho&#8221; com mais ações para entreter o usuário. Mas e se você faz um site onde é preciso rotacionar uma imagem ou fazer um ZOOM? Você precisará manter as mesmas ações nos dois cenários. E como antigamente, para manter o cenário das interfaces touch você precisa da ajuda de muito script.

Ambas as versões tem suas limitações e um legado de compatibilidade com seu sistema base que precisam manter.

A ideia de criar uma especificação destinada para as interfaces touch é que tenhamos controle sobre as ações do usuário, da mesma forma que temos nos desktops. Para isso eles estão [mapeando uma série de eventos que específicos das interfaces touch][2]. Assim podemos definir ações baseadas nessas interfaces. Estão participando da escrita desta especificação Doug Schepers do W3C, Sangwhan Moon da Opera Software ASA e Matt Brubeck da Mozilla. 

Se você parar para ler a específicação, vai entender que poderemos controlar quando o usuário interage encostando o dedo na tela, movendo o dedo e também ao retirá-lo. Você poderá controlar a área de toque. Se o elemento for pequeno, por exemplo, você poderá aumentar essa área de toque para que o usuário não tenha dificuldades. Poderá acionar eventos no momento que o usuário rotacionar os elementos. Se você está fazendo um WebApp poderá acionar um menu contextual personalizado quando o usuário fizer um &#8220;tap&#8221; com dois dedos. O usuário vira basicamente um proctologista. 😉

A especificação ainda é um rascunho mas já está mostrando que as possibilidades são imensas. Eu vivo me perguntando até onde irá o HTML, CSS e Javascript com essas novas mudanças. Será que vão continuar fáceis como são hoje ou tudo vai ficar complicado? Será que serão eles que farão todo o trabalho ou novas linguagens serão criadas para lidar com essas novidades? Who knows? Eu tenho um palpite, mas é assunto para outra hora.

 [1]: http://www.microsoft.com/surface/
 [2]: http://bit.ly/mMP5jy