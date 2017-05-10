---
title: Novo parser HTML5 – FF4
author: Diego Eis
type: post
date: 2011-03-28
excerpt: O Firefox 4 trouxe uma série de atualizações, uma das mais importantes é o novo parser de HTML5 que promete ser mais rápido e eficiente.
url: /parser-html5-firefox4/
tweetbackscheck:
  - 1356387878
shorturls:
  - 'a:3:{s:9:"permalink";s:45:"http://tableless.com.br/parser-html5-firefox4";s:7:"tinyurl";s:26:"http://tinyurl.com/3bn68dd";s:4:"isgd";s:19:"http://is.gd/QyN5zx";}'
twittercomments:
  - 'a:8:{i:149519283251183617;s:7:"retweet";i:148112785010728960;s:7:"retweet";i:148084287009337347;s:7:"retweet";i:148080926189031425;s:7:"retweet";i:159806608183009282;s:7:"retweet";i:159299086321848320;s:7:"retweet";i:159251208404598784;s:7:"retweet";i:159250146528473088;s:7:"retweet";}'
tweetcount:
  - 19
dsq_thread_id: 503028123
categories:
  - Browsers
  - Código
  - HTML
  - HTML5
  - Tecnologia e Tendências
tags:
  - 2011
  - Browsers
  - CSS3
  - desenvolvimento web
  - firefox
  - mozilla
  - Na Prática
  - navegadores
  - padroes web

---
O Firefox é o meu browser favorito embora não seja meu browser padrão atualmente. Durante muito tempo ele me segurava com suas extensions exclusivas. Os outros browsers demoraram para ter uma coleção aceitável de extensions que realmente competissem com as do Firefox.
  
Foi lançado na semana passada o <a href="http://getfirefox.com/" title="baixe agora" rel="external">Firefox 4.0</a> que trouxe uma série de mudanças interessantes. Uma das atualizações mais importantes foi o &#8220;redesign&#8221; do parser de HTML5.

### HTML5 parser

O parser do [Firefox 4][1] foi todo reescrito para melhorar a performance e eficiência da renderização de código client-side. O motor antigo &#8211; de 1998 &#8211; foi descontinuado e agora com esse novo parser temos a possibilidade de utilizar SVG e MathML diretamente nas páginas HTML5 sem a utilização de namespace de XML. Entre outros diversos [bugs que foram arrumados][2].

A esse novo parser foi escrito baseando-se na especificação do HTML5, que foi a primeira especificação que explica exatamente como os fabricantes de browsers devem ler e renderização o HTML. Estes detalhes técnicos não eram ditos nas versões anteriores das especificações do HTML. Basicamente o antigo HTML era ainda definido nos termos do antigo SGML. Isso implica na relação do código HTML e DOM. Isso quer dizer que o parseador consegue ler melhor a estrutura do nosso HTML e suas hierarquias. Claro, toda a performance do paseador é somente utilizada se o código for bem escrito e não tiver erros de sintaxe. A grande maioria dos sites na web ainda utilizam códigos mal escritos em HTML4. Leia mais sobre o [DOM][3].

Para os casos onde o HTML for mal escrito, como em sites antigos que foram criados para suprir necessidades de browsers como Netscape e IE, o parser faz uma mudança de interpretação fazendo com que o Firefox entenda esse código antigo e não quebre o site. Logo, não precisamos manter um legado com códigos antigos e abre portas para a criação de código novo, mesmo estando em ambientes onde ainda é necessário conviver com código antigo.

### MathML e SVG

Uma das vantagens desse novo parser é que ele permite que você sirva MathML e SVG diretamente na sua página sem ter que declarar a página inteira como XML/XHTML. Isso quer dizer que o código abaixo pode ser inserido normalmente em uma página HTML, sem qualquer namespace declarado.

Veja um exemplo de MathML:

<pre lang="html" line="1">&lt;math>
  &lt;mi>x&lt;/mi>
 
  &lt;mo>=&lt;/mo>
  &lt;mfrac>
    &lt;mrow>
      &lt;mo>&minus;&lt;/mo>
      &lt;mi>b&lt;/mi>
      &lt;mo>&PlusMinus;&lt;/mo>
      &lt;msqrt>
        &lt;msup>
 
          &lt;mi>b&lt;/mi>
          &lt;mn>2&lt;/mn>
        &lt;/msup>
        &lt;mo>&minus;&lt;/mo>
        &lt;mn>4&lt;/mn>
        &lt;mo>&InvisibleTimes;&lt;/mo>
        &lt;mi>a&lt;/mi>
 
        &lt;mo>&InvisibleTimes;&lt;/mo>
        &lt;mi>c&lt;/mi>
      &lt;/msqrt>
    &lt;/mrow>
    &lt;mrow>
      &lt;mn>2&lt;/mn>
      &lt;mo>&InvisibleTimes;&lt;/mo>
      &lt;mi>a&lt;/mi>
 
    &lt;/mrow>
  &lt;/mfrac>
&lt;/math>
</pre>

<a href="http://tableless.github.com/tableless/mathml.html" rel="external">Veja o exemplo online</a>.
  
Veja o <a href="https://github.com/tableless/exemplos/blob/gh-pages/mathml.html" rel="external">código no Github</a>.

Com o SVG é a mesma coisa, veja o código abaixo:

<pre lang="html" line="1">




<a href="http://tableless.com.br/">
    &lt;svg style="width:113px; height:113px; margin-left:30px">
&lt;polygon fill="#EA2125" points="113,91 113,0 0,0 0,113 91,113"/>
&lt;polygon opacity="0.5" fill="#010101" points="113,91 91,91 91,113"/>
&lt;path fill="#FFFFFF" d="M62.364,34.905v14.147l12.991-4.482l3.963,10.369l-13.003,5.447l8.165,11.593l-8.783,6.502L56.82,66.799
l-8.693,11.683l-9.225-6.502l8.261-12.036l-13.096-5.004l3.779-10.369l13.438,4.482V34.905H62.364z"/>
    &lt;/svg>
</a>


</pre>

Veja o código <a href="http://tableless.github.com/exemplos/logo-tableless-svg.html" rel="external">acima em ação</a> no <a href="https://github.com/tableless/exemplos/" rel="external">nosso GITHUB</a>.

Perceba que os códigos acima se parecem muito mais com um HTML do que com um XML. Perceba que não há nenhum namespace declarado. Isso é uma maravilha porque dá flexibilidade.

Pela explicação do [Mozilla Hacks][4], o algoritmo é dividido em duas partes principais: **tokenization** e **tree building** (mantive o termo original porque a tradução literal seria muito estranha). A tokenization (algo como **tokenização**. Viu, falei que seria estranho) seria o processo de ler o fluxo do código de tags, comentários e atributos de tags. A **tree building** seria o processo de pegar essas informações encontradas pela tokenização e construir a árvore de tags, o árvore do DOM. O fluxo de tags que você construiu.

#### Outras atualizações

O Firefox 4 trouxe outras atualizações que podemos falar mais pra frente aqui no Tableless. São atualizações que navegadores Webkit já tem suporte e também o Opera, como: [CSS Transitions][5], [Formulários em HTML5][6], [Audio Data API][7], [History API][8], HTML5 Video buffered property, e o tão aguardado JägerMonkey o novo engine de Javascript da Mozilla.

 [1]: http://getfirefox.com
 [2]: https://bugzilla.mozilla.org/buglist.cgi?status_whiteboard_type=substring&status_whiteboard=[fixed%20by%20the%20HTML5%20parser]&resolution=FIXED
 [3]: http://tableless.com.br/html5/?chapter=16
 [4]: http://hacks.mozilla.org/2010/05/firefox-4-the-html5-parser-inline-svg-speed-and-more/
 [5]: http://tableless.com.br/introducao-ao-css-animation
 [6]: http://tableless.com.br/html5/?chapter=8
 [7]: http://tableless.com.br/html5/?chapter=11
 [8]: http://tableless.com.br/html5/?chapter=21