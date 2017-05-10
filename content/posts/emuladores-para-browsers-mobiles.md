---
title: Emuladores para browsers mobiles
author: Diego Eis
type: post
date: 2010-03-23
excerpt: São diversos aparelhos com diversas versões de browsers. Qual escolher? Por onde nivelar o desenvolvimento? Qual browser é melhor?
url: /emuladores-para-browsers-mobiles/
aktt_notify_twitter:
  - no
tweetbackscheck:
  - 1356399114
shorturls:
  - 'a:3:{s:9:"permalink";s:56:"http://tableless.com.br/emuladores-para-browsers-mobiles";s:7:"tinyurl";s:26:"http://tinyurl.com/42ro6ht";s:4:"isgd";s:19:"http://is.gd/snt0Bb";}'
twittercomments:
  - 'a:36:{i:57813311714107392;s:7:"retweet";i:57813141677023232;s:7:"retweet";i:57811911261163520;s:7:"retweet";i:57804247877697536;s:7:"retweet";i:57801060542201856;s:7:"retweet";i:57798684355723264;s:7:"retweet";i:57796522863116290;s:7:"retweet";i:57796136878092288;s:7:"retweet";i:57795710363516928;s:7:"retweet";i:57795111936987136;s:7:"retweet";i:57794104158994432;s:7:"retweet";i:57793647659323392;s:7:"retweet";i:57791666333036544;s:7:"retweet";i:57791092699037696;s:7:"retweet";i:126648264283013120;s:7:"retweet";i:127189029191036928;s:7:"retweet";i:126865771518373888;s:7:"retweet";i:126685948250554370;s:7:"retweet";i:126659840633356289;s:7:"retweet";i:126652069070372864;s:7:"retweet";i:126651491271458816;s:7:"retweet";i:126647706260226049;s:7:"retweet";i:126647547291901953;s:7:"retweet";i:126647208606044160;s:7:"retweet";i:126646181253234688;s:7:"retweet";i:126645705065512960;s:7:"retweet";i:126644027071270913;s:7:"retweet";i:126643812226445312;s:7:"retweet";i:126641930674245632;s:7:"retweet";i:126641653900509184;s:7:"retweet";i:126641634568978432;s:7:"retweet";i:126641313759248385;s:7:"retweet";i:268718079310188546;s:7:"retweet";i:268713093067075584;s:7:"retweet";i:268703954362302467;s:7:"retweet";i:268703802000035841;s:7:"retweet";}'
tweetcount:
  - 142
dsq_thread_id: 503023709
categories:
  - Artigos
  - Mobile
  - O Básico
  - Técnicas e Práticas
  - Tecnologia e Tendências
tags:
  - 2010
  - desenvolvimento web
  - internetmovel
  - mobilidade
  - Na Prática

---
Criar sites para mobiles hoje não é bicho de sete cabeças, mas também não é tarefa fácil. Quando fazemos sites para desktops, temos tudo o que precisamos para testar ao nosso alcance. Se você usa Mac ou Linux, pode usar um virtualizador para ter o IE, se você usa Windows, tem todos os browsers que necessita para testes. Você pode ver o resultado em diferentes resoluções, tamanho de fontes e etc. No mundo dos Mobiles isso muda um pouco. Cada aparelho é diferente do outro. Enquanto nos desktops temos apenas 3 fabricantes de sistemas operacionais, no mundo mobile, cada fabricante usa a sua versão do sistema. A sorte é que para nós que desenvolvemos sites, o que nos importa é qual browser o usuário vai utilizar para acessar a web.

Hoje, temos os seguintes browsers e motores de renderização para se preocupar:

Webkit
:   Devices com Android instalado ou iPhones e iPod Touch (com Mobile Safari).

Opera Mobile e Opera Mini
:   O Opera é um dos browsers mais &#8220;perfeitos&#8221; que existem para mobiles. Ele tem um bom suporte aos Padrões e é quase tão atualizado como Mobile Safari.

Blackberry
:   O browser utilizado nos Blackberrys são muito bons. Bem melhores que o Internet Explorer, mas piores que o Opera ou Mobile Safari. Digo que eles estão no meio do caminho. Falta ainda suporte a metatags inteligentes, mas já conhecem um bocado de CSS.

Browsers S60 da Nokia
:   São baseados em Webkit também, como o browser do iPhone e do Android, mas geralmente a versão do webkit é antiga, o que atrapalha um pouco se você quiser fazer algumas coisas mais elaboradas, por exemplo, utilizar [media queries][1] ou metatags que nos ajudam a controlar o visual nos aparelhos, como a de Metatag de Viewport. 

Internet Explorer Mobile
:   Esse sim é uma dor de cabeça. Ele não tem bom suporte a CSS e tem bus quando usamos [media types][2]. Sem contar que é bastante lerdo e não tem uma séries features que os outros browsers tem, como o Opera. Mesmo assim, há um grupo enorme de aparelhos que vem com Windows Mobile e consequentemente, os usuários mais desavisados utilizam o Internet Explorer Mobile como browser. Felizmente, há uma parte desse grupo que conhece o Opera.
  
    Contudo, com o lançamento do Windows Phone 7 isso tende a mudar um pouco. O Windows Phone 7 utiliza um browser com características e suporte aos padrões referentes a alguma versão do Internet Explorer 7 e 8. 

Para facilitar o desenvolvimento para mobiles, eu nivelo a produção desta forma. Por ordem de prioridade:

  * Webkit
  * Opera Mobile e Opera Mini
  * Outros browsers comò do Blackberry, S60 e etc.

De longe o Webkit é hoje o melhor engine para browsers mobiles. Ele é rápido e suporta grande parte das especificações de HTML, CSS e Javascript. Além de estar presente em dispositivos como iPhone, Android e alguns smartphones da Nokia.

Mesmo assim, é preciso testar os sistemas nestes browsers. Você faz isso de duas formas: compra uma dezena de celulares diferentes uns dos outros e testa o produto em cada um deles. Ou por meio de emuladores. O problema de testar com emuladores é que nem todos tem versões para vários sistemas operacionais. O simulador de iPhone só tem para Mac. O de Android tem para Mac e para Windows. O de Blackberry e os da Nokia só tem para Windows. Dificulta bastante a produtividade, mesmo assim, é melhor que ter todos os aparelhos. 😉

Para obter os simuladores, veja abaixo:

iPhone/iPod Touch
:   O mais fiel de todos os emuladores de mobiles que já vi. Tudo o que você vê na tela, é exatamente o que verá no aparelho. O problema é que só funciona no Mac. Os emuladores alternativos para windows ou outros sistemas não são fiéis. [iPhone SDK][3].

Opera Mobile e Opera Mini
:   Fizeram uma atualização geral estes últimos tempos. A vantagem é que ele funciona on-line. Nada de fazer download. [Emulador Opera][4].

Blackberry
:   Só funciona em Windows. A vantagem é que dá para escolher versões anteriores. Mesmo assim, sugiro que sempre nivele pela última versão. [Emulador de Blackberry][5].

Browsers da Nokia
:   Também só para Windows. Mas costumam ser fiéis com o que vemos nos aparelhos. [Nokia Browser Emulator][6].

Android
:   Funciona em Macs e Windows. Mas são complicados de usar. Nada que alguns minutos lendo tutoriais e artigos pela internet não resolvam. A grande vantagem é que você consegue customizar o aparelho onde você vai testar o website. [Emulador Android][7].

Se você tem um aparelho com Android, Windows Mobile ou NokiaS60, aconselho também baixar o [Skyfire][8]. Um browser muito bom que apareceu para tentar dominar parte do mercado de browsers para mobiles. Ele ataca o mesmo mercado que o Opera está atuando. Tem um bom suporte a Padrões. Vale a pena conferir.

A grande graça de fazer sites para mobiles, é que a grande maioria dos dispositivos realmente confortáveis para acessar a web, e que são os dispositivos que a maioria dos usuários compram porque querem navegar, tem um bom suporte a Padrões Web. Ter conforto para navegar nestes aparelhos é ponto crucial, por isso os fabricantes de sistemas e browsers tentam sempre manter os browsers atualizados com os Padrões.

 [1]: http://tableless.com.br/introducao-sobre-media-queries
 [2]: http://tableless.com.br/sites-para-dispositivos-moveis-mediatype
 [3]: http://developer.apple.com/iphone/index.action
 [4]: http://www.opera.com/mobile/demo/
 [5]: https://www.blackberry.com/Downloads/entry.do?code=060AD92489947D410D897474079C1477
 [6]: http://www.forum.nokia.com/info/sw.nokia.com/id/db2c69a2-4066-46ff-81c4-caac8872a7c5/NMB40_install.zip.html
 [7]: http://developer.android.com/guide/developing/tools/emulator.html
 [8]: http://www.skyfire.com/