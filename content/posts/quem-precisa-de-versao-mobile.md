---
title: Quem precisa de versão mobile?
author: Elcio Ferreira
type: post
date: 2007-12-12
url: /quem-precisa-de-versao-mobile/
tweetbackscheck:
  - 1356171168
shorturls:
  - 'a:3:{s:9:"permalink";s:53:"http://tableless.com.br/quem-precisa-de-versao-mobile";s:7:"tinyurl";s:26:"http://tinyurl.com/3ckmjlc";s:4:"isgd";s:19:"http://is.gd/UzbjYf";}'
twittercomments:
  - 'a:0:{}'
dsq_thread_id: 503037817
categories:
  - Artigos
  - Browsers
  - Mobile
  - Tecnologia e Tendências
tags:
  - 2007
  - acessibilidade
  - Browsers
  - internetmovel
  - konqueror
  - mobilidade
  - Na Prática
  - padroes web

---
Parece ser um erro comum dos novatos criar versões diferentes do mesmo site.

O ano era 1997. Eu e e todo mundo que eu conhecia usávamos Netscape Navigator. Foi o ano em que, pela primeira vez, fiz um site sozinho. Tudo, atendi o cliente, preparei textos, fotos, fiz o layout, se é que se pode chamar aquilo de layout, criei uma conta no [Geocities][1] e publiquei. Em seguida entrei no [Yahoo!][2] e cadastrei o site, para que aparecesse nas buscas.

Depois de alguns dias recebi um e-mail do Yahoo! dizendo que o site não poderia ser publicado no diretório porque não funcionava no Internet Explorer. <!--more--> Sim, cavalheiros, era política do Yahoo! só publicar em seu diretório sites que funcionassem bem nos dois navegadores. Como eu resolvi? Criei duas versões do site, uma para cada navegador, e um Javascript que selecionava a versão de acordo com o navegador do usuário.

Mas eu não fiquei satisfeito. Fazer duas versões do site dava um bocado de trabalho. Manter as duas versões dava mais trabalho ainda. E se houvesse mais um navegador relevante? Eu não queria ter três ou quatro versões de cada site que desenvolvesse. Parece que muito mais gente tinha o mesmo sentimento que eu. Gente muito mais talentosa e importante do que eu. Gente como o pessoal que criou o [projeto Web Standards][3].

Você não imagina como eu fiquei feliz quando, no final do século passado, ao estudar os Padrões Web, percebi que não precisava de duas versões de cada site. Eu hoje uso [Opera][4], [Firefox][5] e [Konqueror][6]. E esporadicamente, [Flock][7], [Safari][8], [Epiphany][9] e [Galeon][10]. E ainda preciso testar meus sites no Internet Explorer. Esta é uma das grandes vantagens dos padrões, seu site, uma única versão, funcionando em todo lugar.

Bom, talvez eu me preocupe com navegadores demais. Quem sabe é alguma paranóia minha. Talvez para você seja importante apenas que o site funcione no IE e no Firefox. Mas geralmente não dá nenhum trabalho fazê-lo funcionar nesses navegadores todos. Agora, dê uma olhada no [mundo da mobilidade][11]. Você vai construir uma versão para cada navegador? Que tal se simplesmente não construísse versão nenhuma?

Ora, os padrões web surgiram justamente para isso, para que seu site, a única versão, funcione em qualquer lugar. Naturalmente, há sites e aplicações online, por exemplo aquelas cuja experiência de uso depende fortemente de Ajax, que realmente merecem uma versão em HTML simples, acessível via dispositivos móveis e outros dispositivos e cenários de uso. Mas a maioria, a esmagadora maioria dos sites **não precisa** de uma versão mobile. Basta que o site seja bem feito, vai funcionar no mobile.

Existe porém um mito sendo difundido por aí de que as pessoas precisam de uma versão mobile de seus sites. Há uma febre de versão mobile por aí! Então, vamos deixar claro quais são as opções que temos em relação à acessibilidade de um site em dispositivos móveis:

  1. **Ter um site que simplesmente funcione**: um site bem feito, nos padrões web, vai funcionar bem no celular. É a estratégia mais simples, mais barata, e os resultados são fantásticos!
  2. **Ter um CSS para dispositivos móveis**: essa é a melhor estratégia. Você continua tendo uma única versão do site para manter. Mas oferece um layout trabalhado especialmente para dispositivos móveis que suportem bem CSS. Ou seja, dá só um pouquinho de trabalho em relação à primeira estratégia, oferece os mesmos resultados para navegadores sem CSS, e dão um conforto a mais para usuários de bons navegadores mobile.
  3. **Ter uma versão do site específica para mobile**: vai te dar um trabalho desgraçado. Mas, ás vezes, simplesmente não tem jeito. É o caso de aplicações como o [Twitter][12] e o [Google Reader][13]. Aplicações Ajax, sites que dependem de um plugin específico ou aqueles cuja quantidade de conteúdo torna o uso muito desconfortável no mobile são potenciais candidatos a uma segunda versão. Uma abordagem semelhante é aquela que oferece uma versão &#8220;HTML simples&#8221;, que vai funcionar no mobile, no leitor de telas e etc.
  4. **Não se importar**: é a estratégia de boa parte dos sites hoje. Não é irônico perceber que sites de operadoras de telefonia móvel não funcionam em seus próprios celulares?

Se você não tiver nenhum motivo muito bom para fazer diferente, fique num dos dois primeiros níveis. Você vai ter muito menos trabalho, e todo mundo vai poder acessar seu site. Da próxima vez que pensar em acessibilidade para dispositivos móveis, lembre-se: muito provavelmente você não precisa de uma versão mobile.

Os mesmos quatro níveis podem ser aplicados a praticamente qualquer cenário de uso. Por exemplo, impressão ou leitores de tela. Você pode fazer um site nos padrões e isso vai funcionar de maneira razoável. Pode escrever CSS ou pequenas adições em seu HTML para melhorar a experiência nesses cenários de uso. Pode, se não tiver outro jeito mesmo, fazer a indesejável segunda versão. Ou pode ignorar seus usuários.

 [1]: http://geocities.yahoo.com/
 [2]: http://www.yahoo.com
 [3]: http://www.webstandards.org/
 [4]: http://www.opera.com
 [5]: http://www.mozilla.com/firefox/
 [6]: http://www.konqueror.org/
 [7]: http://www.flock.com/
 [8]: http://www.apple.com/safari/
 [9]: http://www.gnome.org/projects/epiphany/
 [10]: http://galeon.sourceforge.net/
 [11]: http://en.wikipedia.org/wiki/Microbrowser#Default_browsers_used_by_major_mobile_phone_and_PDA_vendors
 [12]: http://twitter.com/
 [13]: http://www.google.com/reader/