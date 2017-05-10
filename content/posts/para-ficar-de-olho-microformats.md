---
title: 'Para ficar de olho: Microformats'
author: Elcio Ferreira
type: post
date: 2007-01-08
url: /para-ficar-de-olho-microformats/
aktt_tweeted:
  - 1
tweetbackscheck:
  - 1356440012
shorturls:
  - 'a:3:{s:9:"permalink";s:55:"http://tableless.com.br/para-ficar-de-olho-microformats";s:7:"tinyurl";s:26:"http://tinyurl.com/3baocqn";s:4:"isgd";s:19:"http://is.gd/HCMhgZ";}'
twittercomments:
  - 'a:0:{}'
dsq_thread_id: 503036522
categories:
  - Browsers
  - Tecnologia e Tendências
tags:
  - acessibilidade
  - Extensions

---
Veja este artigo da Read/Write Web: [Mozilla Does Microformats: Firefox 3 as Information Broker][1].

Enquanto isso, recebemos muitos e-mails de gente que ainda não entendeu o que são os tais microformats, ou, o que é muito mais comum, para que eles exatamente servem. Então vamos tentar elucidar, escolhendo um microformat como exemplo: [hCard][2], um dos mais populares, vai servir perfeitamente.<!--more-->

Quase todo mundo, ao criar um site, precisa colocar informações como nome, endereço, e-mail, telefone, etc. É algo comum, recorrente, e você mesmo já deve ter feito isso uma porção de vezes, para uma porção de gente. E talvez para cada cliente você pode ter escrito markup diferente para a mesma informação. E mesmo que você tenha um padrão, e que use o mesmo código XHTML para os &#8220;perfis&#8221;, &#8220;endereços&#8221;, &#8220;informações de contato&#8221; e &#8220;sobre&#8221; de todos os seus clientes, seu padrão é diferente do meu, que é diferente do de todo mundo mais.

A idéia dos microformats é nos dar um padrão. Não um padrão quando a Web Semântica estiver funcionando, se é que um dia vai estar. Mas um padrão hoje, para a construção da web semântica com letras minúsculas. Assim, ao invés de inventar seu próprio padrão para os profiles de seus clientes, você pode usar o padrão hCard. Na prática, o padrão consiste geralmente em uma série de nomes de classes para cada informação que você pode querer descrever, acompanhado às vezes das tags que você deve usar.

Então é fácil, ao invés de cada um de nós inventar seu próprio jeito de descrever as coisas, nós compartilhamos de um padrão comum. O mesmo padrão está sendo usado nos profiles do [Last.fm][3] e do [Flickr][4], nos resultados do [Yahoo Local][5], E daí, para que serve isso?

O truque é que, se eu e você usarmos o mesmo código para o mesmo tipo de informação, as aplicações desenvolvidas para entender meu site provavelmente vão entender o seu. E isso se torna muito atraente para quem desenvolve aplicações, principalmente se além de eu e você, o resto do mundo também estiver usando o mesmo padrão. É o caso do Firefox 3 que, segundo o artigo da Read/Write Web, vai entender os microformats em seu site e permitir ao usuário abrí-los com a aplicação padrão em sua máquina ou na web. Se você quer ter uma idéia de como isso funciona, experimente instalar a extensão [Operator][6] para o Firefox.

Você pode achar tudo meio sem graça ao navegar com isso e não encontrar muitos sites com o recurso. Isso me lembra o começo do RSS. Não sei se você se lembra disso, mas a gente tinha dificuldades em encontrar sites com RSS para assinar. O [Charles][7] criou inclusive um projeto, o [RSSficado][8], com ferramentas para a criação de RSS de sites que não se preocupavam em oferecer o recurso. O projeto foi seguido de diversos outros semelhantes, em diferentes linguagens e plataformas de programação. Eu fiz até uma [ferramenta semelhante em ASP][9] que na época chegou a me servir duzentos feeds.

Hoje o projeto RSSficado foi descontinuado. O Wiki está até meio largado, cheio de spam. Meu RSSficador, assim como uma porção de outros que conheci também cairam no esquecimento. Por quê? Porque todo site que se preze hoje se preocupa em oferecer RSS para os leitores. Se encontro algum site que não oferece o recurso, simplesmente deixo de lê-lo, porque o concorrente provavelmente tem conteúdo tão bm quanto, e com um feed para eu assinar.

Suponho que a mesma história vai se repetir com os microformats. Conforme os sites forem adotando os padrões de mark-up, a coisa inteira vai ficando mais útil, mais aplicações interessantes irão surgindo para usar os microformats, e mais vai parecer óbvio usá-los.

Segue então minha listinha de coisas que você pode fazer para tornar mais úteis seus sites e aplicações:

  1. **Use microformats**: essa é a parte mais fácil. Ao escrever datas para divulgar eventos, use [hCalendar][10], ao publicar suas informações pessoais ou comerciais, ou as de seus clientes, use [hCard][2], ao apontar para suas coordenadas geográficas, use [geo][11], ao escrever avaliações sobre um produto qualquer, use [hreview][12], e assim por diante. Dê uma olhada nos links, esses formatos são mesmo simples de se implementar.
  2. **Coloque seus clientes na dianteira**: mas não saia feito um fanfarrão tentando explicar para eles o que são os microformats e etc. A não ser que seus clientes sejam técnicos, contratando uma consultoria estratégica em padrões e o futuro da web, coloque microformats nos sites deles, onde for adequado, e não conte a eles. Essa coisa toda é técnica demais, e [o cara te contratou justamente porque ele não entende disso][13]. Seus clientes não-técnicos não ficam felizes porque o site deles foi escrito em XHTML válido e semântico, mas porque o site carrega rápido, os clientes com Mac e Linux pararam de reclamar e a nova posição no Google aumentou as vendas. Ele talvez nem saiba que o blog que você criou para ele tem RSS, e talvez nem saiba o que é RSS. Mas ele fica feliz porque as pessoas, que ele nem sabe que chegaram ao site porque assinaram o feed, lêem, comentam e até compram.
  3. **Use aplicações que trabalham com microformats**: de duas maneiras. Primeiro, instale em sua máquina ou se cadastre em aplicações online para uso pessoal. Por exemplo, instale a [Operator][6]. O segundo jeito legal de fazer isso é oferecer aos seus visitantes suporte a microformats através de aplicações online. Veja, por exemplo, [este artigo do Henrique][14], que aponta para esse [conversor online][15].
  4. **Divulgue os microformats**: bem, você entendeu, quanto mais gente estiver usando isso, mais útil será a coisa toda. Então faça sua parte.
  5. **Crie aplicações que suportem microformats**: se você vai criar um site de currículos para uma empresa de RH, que tal facilitar a vida do candidato, perguntando a URL do site dele e, se ele tiver hCard, importando os dados para o formulário de contato para que ele só precise preencher o que não está lá? Há demanda para geradores, importadores, exportadores e consumidores de microformats.
  6. **Escreva javascript que trabalhe com microformats**: se você escreve um script que trabalha com hCalendar, por exemplo, exibindo as informações de uma maneira especial, criando um link para um serviço online, ou fazendo qualquer outra coisa útil que sua criatividade puder produzir, ele poderá ser usado com facilidade por qualquer um que tenha hCalendar em seu site.
  7. **Crie novos microformats**: se você tem uma necessidade específica, e não há nenhum microformat que a contemple, escreva um e envie a proposta para o [microformats.org][16]. Quem sabe você não vai estar resolvendo o problema de muita gente, e ajudando a criar possibilidades para novas e interessantes aplicações que vão beneficiar todo mundo, inclusive seus clientes? Sinto falta, por exemplo, de microformats relacionados com e-commerce. Não achei nada sobre isso lá. Que tal um microformat com os dados sobre um produto num site de e-commerce, inclusive os dados sobre preço e pagamento? Imagine como seria mais simples a vida de quem faz sites de comparação de preços, programas de afiliados e afins.

**Update:** [para aqueles que pediram um exemplo][17].

 [1]: http://www.readwriteweb.com/archives/mozilla_does_microformats_firefox3.php
 [2]: http://microformats.org/wiki/hcard
 [3]: http://www.last.fm/
 [4]: http://flickr.com/
 [5]: http://local.yahoo.com/
 [6]: https://addons.mozilla.org/firefox/4106/
 [7]: http://charles.pilger.com.br/
 [8]: http://www.rssficado.com.br/
 [9]: http://elcio.com.br/rss/
 [10]: http://microformats.org/wiki/hcalendar
 [11]: http://microformats.org/wiki/geo
 [12]: http://microformats.org/wiki/hreview
 [13]: http://www.joelonsoftware.com/articles/fog0000000356.html
 [14]: http://www.revolucao.etc.br/archives/compartilhe-seu-hcard-com-icones-microformats/
 [15]: http://suda.co.uk/projects/X2V/
 [16]: http://www.microformats.org
 [17]: http://blog.elcio.com.br/microformats-aplicados/