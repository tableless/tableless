---
title: Font icons – Utilizando ícones em formato de font
author: Diego Eis
type: post
date: 2012-08-20
excerpt: Aprenda a usar font para fazer elementos com ícones.
url: /utilizando-icones-formato-font/
tweetbackscheck:
  - 1356387705
shorturls:
  - 'a:3:{s:9:"permalink";s:31:"http://tableless.com.br/?p=6471";s:7:"tinyurl";s:26:"http://tinyurl.com/cfp7vlz";s:4:"isgd";s:19:"http://is.gd/Bd96Io";}'
twittercomments:
  - 'a:0:{}'
dsq_thread_id: 811911850
categories:
  - CSS
  - HTML
  - Técnicas e Práticas
tags:
  - 2012
  - font
  - icons

---
Você já deve ter desenvolvido um sistema onde o designer utilizou muitos ícones em botões, links e etc&#8230; A primeira coisa que pensamos em fazer são [sprites][1] com todos estes ícones. O problema é que dependendo da sua necessidade, criar Sprites para todos os ícones pode se tornar algo realmente trabalhoso. Ainda mais quando estes ícones são utilizados em várias cores e tamanhos. Utilizar ícones em imagens separadas dá tanto trabalho quanto.

Mesmo assim, até hoje utilizávamos esses métodos sem alguma outra solução interessante que nos desse a possibilidade de utilizar ícones em qualquer tipo de elemento, com facilidade de mudança de cores e principalmente de tamanho. Foi aí que depois do advento do [css font-face][2], alguém teve a grande ideia de fazer uma família de font em formato de ícones.

### Soluções atuais

Normalmente o pessoal utiliza o ícone como background do elemento. Essa é a solução mais comum e até agora a mais fácil. Muito melhor e mais correto inserir uma imagem de ícone no background do elemento do que colocar a imagem diretamente no código HTML.

Mas pense em larga escala. Pense em ter vários ícones sendo colocados em vários elementos. A coisa complica bastante por que você precisa ter uma maneira de controlar todos eles.

Alguns desenvolvedores faziam uma solução simples com jQuery. O HTML era o mesmo que o exemplo abaixo, algo como:

<pre class="lang-html">&lt;a href="#" class="ico ico-search"&gt;Buscar&lt;/a&gt;
</pre>

Via jQuery o desenvolvedor pega todos os elementos que tem a classe **ico** e adiciona um **span** ou qualquer outro elemento no começo do objeto em questão para adicionar o ícone.

Outra solução mais inteligente que a de cima é inserir os ícones via background. O HTML continua igual ao do exemplo acima, mas sem a necessidade de inserir um SPAN via Javascript. Todos os elementos que terão ícone recebem a classe ICO, que carrega os estilos comuns como background-repeat, background-position, width, height e etc&#8230; Em conjunto com essa classe comum, eles carrega uma outra classe que irá especificar o ícone. No caso do exempo acima, a classe ICO-SEARCH irá colocar uma imagem de ícone de lupa.

Essas soluções são interessantes, mas não são o ideal.

### Solução moderna

Com a saída do IE6/7 nós podemos utilizar algumas facilidades dos seletores do CSS. Tendo o HTML abaixo, como exemplo:

<pre class="lang-html">&lt;a href="#" class="ico-search"&gt;Buscar&lt;/a&gt;
</pre>

O CSS ficaria assim:

<pre class="lang-css">[class^="ico-"]:before {
  content: " ";
  width:10px; height:10px;
  display:inline-block;
  vertical-align:middle;
}
</pre>

Isso cria um pseudo-elemento ANTES (:before) de qualquer objeto que tenha no atributo **class** um valor que inicia com **ico-**&#8230;
  
Pronto, o elemento criado dinamicamente com JQuery agora é feito pelo CSS com o atributo **content**. 

O atributo content serve para inserirmos um pedaço de conteúdo nos elementos dinamicamente via CSS. Essa propriedade trabalha em conjunto com os pseudo-elementos :before e :after. [Entenda mais sobre a propriedade content e os pseudo-elementos :before e :after aqui][3].

Perceba que o valor do atributo **content** está vazio. Ali dentro iremos colocar o caractere que representa o ícone que queremos utilizar.

Hoje existem muitas coleções de font-icons que você pode utilizar de graça. Existem dois sites sensacionais onde você pode personalizar suas fonts: [Fontello][4] e [IcoMoon][5]. Eu já usei os dois, mas gostei mais do IcoMoon.

Quando você faz um pacote no Fontello ou no IcoMoon eles já te dão o código prontinho, basta importar no seu projeto. O código que eles utilizam é algo assim:

<pre class="lang-css">/** ICONS **/
@font-face {
  font-family: 'NomeDaFonte';
  src: url('NomeDaFonte.eot');
  src: url('NomeDaFonte?#iefix') format('embedded-opentype'),
    url('NomeDaFonte.svg#Locaweb-Icons') format('svg'),
    url('NomeDaFonte.ttf') format('truetype');
  font-weight: normal;
  font-style: normal;
}

[class^="ico-"]:before {
  content: " ";
  width:10px; height:10px;
  display:inline-block;
  vertical-align:middle;
  font-family: icomoon;
}

.icon-home:before { content: '\2302'; } /* '⌂' */
.icon-export:before { content: '\e715'; } /* '' */
.icon-folder-open:before { content: '📂'; } /* '\1f4c2' */
.icon-search:before { content: '🔍'; } /* '\1f50d' */
.icon-link:before { content: '🔗'; } /* '\1f517' */

</pre>

O primeiro bloco de código importa a fonte que será usada. O segundo bloco nós já explicamos anteriormente, ele define um elemento vazio no início do objeto que receberá a fonte. E terceiro bloco define quais os ícones em suas respectivas classes. Coisa linda.

A vantagem de usar fonts para essa tarefa é que como os ícones são fonts, temos total liberdade de aumentar ou diminuir as fonts, mudar de cor e etc&#8230; Não precisamos nos preocupar em gerenciar diversos stripes de imagens, de todos os tamanhos e cores, sem contar que usando fonts, os ícones já são pré-preparados para aparelhos com alta densidade de pixels.

Veja [um exemplo direto do IcoMoon][6] [aqui no nosso GitHub][7].
  
O [CSS-Tricks também fez um exemplo com um monte de firulas][8].

 [1]: http://tableless.com.br/css-sprites/ "CSS Sprites"
 [2]: http://tableless.com.br/font-face-fonts-externas-na-web/
 [3]: http://bit.ly/Ob6o1I
 [4]: http://fontello.com
 [5]: http://keyamoon.com/icomoon/app/
 [6]: http://tableless.github.com/exemplos/font-icons/
 [7]: https://github.com/tableless
 [8]: http://css-tricks.com/examples/IconFont/