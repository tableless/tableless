---
title: Como perder peso (no browser)
author: Zeno Rocha
type: post
date: 2013-08-23
excerpt: Nós desenvolvedores falamos tanto das novidades do HTML5, CSS3, EcmaScript 6 que acabamos esquecendo de falar de outras coisas também muito importantes, mas que não são tão novidade assim, como performance.
url: /como-perder-peso-no-browser/
dsq_thread_id: 1130382499
categories:
  - Código
tags:
  - 2013
  - boas praticas
  - CSS
  - html
  - JavaScript
  - performance

---
Nós desenvolvedores falamos tanto das novidades do HTML5, CSS3, EcmaScript 6 que acabamos esquecendo de falar de outras coisas também muito importantes, mas que não são tão novidade assim, como performance.

Depois de muito esforço, finalmente lançamos um guia definitivo sobre o assunto chamado [browserdiet.com][1] e vim compartilhar um pouco da experiência de ter liderado esse projeto irado.

## Motivação

O ano de 2012 foi um ano bem diferente pra mim, passei 1/3 dele viajando e me deparei com muita conexão ruim em hotel e aeroporto. Isso me deixava muito irritado. E é claro que eu sempre xingava o hotel/aeroporto, até perceber que a culpa na verdade é nossa.

Nós desenvolvedores somos egoístas. Passamos o dia todo no escritório com uma alta velocidade de conexão e esquecemos que existem outras pessoas no mundo enfrentando velocidades bem diferentes daquela.

## O Início

Comecei a estudar mais sobre performance para escrever [minha monografia][2] e me deparei com o seguinte cenário. Em inglês, excelentes referências como os livros [High Performance Websites][3] e [Even Faster Web Sites][4], ambos do [Steve Souders][5]. Além, é claro, dos guias da [Yahoo!][6] e [Google][7]. Já em português, uma dezena de blogposts soltos por aí.

Pensei: &#8220;E se eu fizesse um guia foda de performance voltado pra comunidade?&#8221; Mas não fazia sentido fazer aquilo sozinho, então de pouquinho em pouquinho fui conversando com uns amigos.

## Concepção

Uma coisa estava muito clara pra mim, queria fazer um projeto divertido.

Convenci primeiro a designer [Briza Bueno][8] _(Americanas.com)_ a me ajudar. Ela elaborou uma identidade muito mais divertida do que aqueles guias chatos que existem hoje. Isso tudo com base nas ilustrações do [Scott Johnson][9], a quem eu pedi autorização para utilizar as imagens.

Depois chegou a hora de elaborar a estrutura desse site, nessa parte o [Iraê Lambert][10] _(Yahoo!)_ me deu uma mão escrevendo um static generator em Python. Só que eu não dominava aquele código e as barreiras que eu encontrava por não saber manipular aquilo foram me afastando do projeto, ao mesmo tempo em que outras ideias iam surgindo.

Resultado: o projeto ficou parado por 1 ano até que eu decidi retomar reescrevendo todo código usando um outro static generator em Node.JS chamado [DocPad][11]. Como todo projeto open source, se você quiser fazer algo que tenha a colaboração das pessoas precisa eliminar o maior número de barreiras possíveis. Por isso, inspirado no [HTML5 Please][12], decidi que todas as dicas seriam escritas no formato mais simples do planeta, em [Markdown][13].

## Conteúdo

Design e implementação estavam prontos, só faltava o que realmente importa, o conteúdo. Convidei então grandes amigos que enfrentam muitos desafios de performance no seu dia-a-dia, [Davidson Fellipe][14] _(Globo.com)_, [Giovanni Keppelen][15] _(Peixe Urbano)_ e [Jaydson Gomes][16] _(Terra)_. As categorias iniciais divididas entre nós foram HTML, CSS, JavaScript e jQuery.

Meu eterno dilema entre português e inglês também persistia nesse projeto. Cheguei a comprar o pequenino domínio [comoperderpesonobrowser.com.br][17], mas ele claramente não funcionaria para um conteúdo em inglês também. Por isso, optei por algo mais curto e universal.

## Revisão

Depois de muito aprimoramento resolvi convidar outros caras sinistros para revisarem, como o [Marcel Duran][18] _(Twitter)_, [Mike Taylor][19] _(Opera)_, [Renato Mangini][20] _(Google)_ e [Sérgio Lopes][21] _(Caelum)_. Todos ficaram animados e contribuiram insanamente. O legal foi que a discussão não ficou apenas na parte do conteúdo, questões relativas ao código do site foram extremamente debatidas como usar [CSS Sprites vs Lazy Load][22].

## Lançamento

Eu estava planejando lançar esse projeto no mínimo em Abril. Só que quando vi que os primeiros colaboradores (Briza, Davidson, Giovanni, e Jaydson) do projeto estariam presentes no [Rio.JS][23], mudei o tema da minha palestra e comecei a correr contra o tempo.

Felizmente deu tudo certo e lançamos o projeto!

O resultado final você pode conferir em: [browserdiet.com][1]. E o código fonte, como sempre, está [aberto no Github][24].

_PS: Os [slides também estão online][25] para quem quiser conferir._

## Conclusão?

Estou bem animado para ver como a comunidade vai receber e se beneficiar desse aglomerado de dicas iradas que preparamos.

E aí, vamos fazer uma web mais rápida?

## Reações

_iMasters &#8211; [Guia que conscientiza desenvolvedores sobre a importância da performance é lançado][26]_

<blockquote class="twitter-tweet">
  <p>
    love this new project: <a title="http://browserdiet.com" href="http://t.co/u8FWpD5mW0">browserdiet.com</a>
  </p>
  
  <p>
    — Stoyan Stefanov (@stoyanstefanov) <a href="https://twitter.com/stoyanstefanov/status/311258820800303104">March 11, 2013</a>
  </p>
</blockquote>

_Stoyan Stefanov, Engineer &#8211; Facebook_

<blockquote class="twitter-tweet">
  <p>
    How to lose weight in the browser — the definitive front-end performance guide: <a title="http://browserdiet.com/" href="http://t.co/YqRgmFvipm">browserdiet.com</a>
  </p>
  
  <p>
    — Mathias Bynens (@mathias) <a href="https://twitter.com/mathias/status/311193207327293440">March 11, 2013</a>
  </p>
</blockquote>

_Mathias Bynens, Web Developer &#8211; Freelance_

<blockquote class="twitter-tweet">
  <p>
    Some of Brazil&#8217;s brightest front-end devs created and just launched <a title="http://browserdiet.com/" href="http://t.co/8FNPhsjzQx">browserdiet.com</a>. Check it out!
  </p>
  
  <p>
    — Mike Taylor (@miketaylr) <a href="https://twitter.com/miketaylr/status/311253455647952897">March 11, 2013</a>
  </p>
</blockquote>

_Mike Taylor, Web Opener &#8211; Opera_

 [1]: http://browserdiet.com
 [2]: http://zenorocha.com/monografia/
 [3]: http://www.amazon.com/High-Performance-Web-Sites-Essential/dp/0596529309
 [4]: http://www.amazon.com/Even-Faster-Web-Sites-Performance/dp/0596522304/ref=sr_1_1
 [5]: http://stevesouders.com/
 [6]: http://developer.yahoo.com/performance/rules.html
 [7]: https://developers.google.com/speed/docs/best-practices/rules_intro
 [8]: http://www.brizabueno.com/
 [9]: http://myextralife.com/56geeks/
 [10]: http://irae.pro.br
 [11]: http://docpad.org
 [12]: http://html5please.com/
 [13]: http://pt.wikipedia.org/wiki/Markdown
 [14]: https://github.com/davidsonfellipe
 [15]: https://github.com/keppelen
 [16]: https://github.com/jaydson
 [17]: http://comoperderpesonobrowser.com.br
 [18]: https://github.com/marcelduran
 [19]: https://github.com/miketaylr
 [20]: https://github.com/mangini
 [21]: https://github.com/sergiolopes
 [22]: https://github.com/zenorocha/browser-diet/issues/40
 [23]: http://riojs.org
 [24]: https://github.com/zenorocha/browser-diet
 [25]: https://speakerdeck.com/zenorocha/como-perder-peso-no-browser/
 [26]: http://imasters.com.br/noticia/guia-que-conscientiza-desenvolvedores-sobre-a-importancia-da-performance-e-lancado/