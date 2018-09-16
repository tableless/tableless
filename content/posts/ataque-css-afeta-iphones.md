+++
authors = "Diego Eis"
categories = ["noticias"]
date = "2018-09-16T08:08:00+00:00"
publishdate = "2018-09-16T08:08:00+00:00"
excerpt = "O código explora uma falha no WebKit."
image = "https://i.imgur.com/zRbPV9d.jpg"
tags = ["css"]
title = "Um simples código de HTML e CSS crasheia aparelhos da Apple"
type = "post"
+++

Com algumas linhas de código você pode fazer crash e restartar um iPhone.
Um cara chamado Sabri Haddouche twittou uma página para provar um conceito que com apenas 15 linhas de código, que se visitado com o Safari, poderá crashear e restartar iPhones ou iPads.

O código explora uma falha no WebKit, que é o motor de renderização usado pela Apple. Ele explicou que se você inserir no HTML uma série de elementos encadeados (um div dentro do outro, por exemplo), e aplicar a propriedade de backdrop do CSS, o dispositivo vai precisar toda potencia do celular para conseguir aplicar o efeito e isso pode causar um kernel panic, que faz com que o celular reinicie.

Tecnicamente isso pode acontecer com qualquer aparelho, inclusive PCs, o ponto é que cada aparelho tem seu poder de processamento. Contudo, a falha do WebKit facilita "bagunçar" a forma com que o WebKit lida com o efeito e consequentemente faz com que o aparelho fique maluco.

<blockquote class="twitter-tweet" data-lang="en"><p lang="en" dir="ltr">How to force restart any iOS device with just CSS? 💣<br><br>Source: <a href="https://t.co/Ib6dBDUOhn">https://t.co/Ib6dBDUOhn</a><br><br>IF YOU WANT TO TRY (DON’T BLAME ME IF YOU CLICK) : <a href="https://t.co/4Ql8uDYvY3">https://t.co/4Ql8uDYvY3</a></p>&mdash; Sabri (@pwnsdx) <a href="https://twitter.com/pwnsdx/status/1040944750973595649?ref_src=twsrc%5Etfw">September 15, 2018</a></blockquote>
<script async src="https://platform.twitter.com/widgets.js" charset="utf-8"></script>

Ele liberou o código no GitHub:

<script src="https://gist.github.com/pwnsdx/ce64de2760996a6c432f06d612e33aea.js"></script>

O ponto interessante é que QUALQUER COISA que renderize HTML no iOS pode ser afetado. Então, se alguém enviar [esse link](https://cdn.rawgit.com/pwnsdx/ce64de2760996a6c432f06d612e33aea/raw/23f2faa0aadb4babbfd228c8bb32a26a8c51c741/safari-ripper.html) para qualquer pessoa com iOS, e essa pessoa abrir via WebView de Apps com o WhatsApp, o iPhone vai pro beleléu.

Parece que até os Apple Watchs podem se dar mal nessa:

<blockquote class="twitter-tweet" data-conversation="none" data-lang="en"><p lang="en" dir="ltr">Also looks like watchOS 5 is susceptible. <a href="https://t.co/Mam8uTyuye">pic.twitter.com/Mam8uTyuye</a></p>&mdash; Robert Petersen (@Sonikku_a2) <a href="https://twitter.com/Sonikku_a2/status/1041111748290338816?ref_src=twsrc%5Etfw">September 15, 2018</a></blockquote>
<script async src="https://platform.twitter.com/widgets.js" charset="utf-8"></script>

Fonte: [TechCrunch](https://techcrunch.com/2018/09/15/a-new-css-based-web-attack-will-crash-and-restart-your-iphone/)
