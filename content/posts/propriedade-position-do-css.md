---
title: Propriedade Position do CSS
author: Diego Eis
type: post
date: 2009-05-12
excerpt: 'A propriedade position não serve para criar estruturas de layouts. Você o usará para coisas mais simples. Existem 3 tipos: relative, absolute e fixed. Entenda como eles funcionam e quais as suas relações.'
url: /propriedade-position-do-css/
aktt_notify_twitter:
  - yes
aktt_tweeted:
  - 1
tweetbackscheck:
  - 1356455180
shorturls:
  - 'a:3:{s:9:"permalink";s:51:"http://tableless.com.br/propriedade-position-do-css";s:7:"tinyurl";s:26:"http://tinyurl.com/3o5hlof";s:4:"isgd";s:19:"http://is.gd/RITXkO";}'
twittercomments:
  - 'a:0:{}'
dsq_thread_id: 503012963
categories:
  - CSS
  - HTML
  - O Básico
  - Técnicas e Práticas
tags:
  - 2009
  - aprenda
  - CSS
  - Na Prática
  - position
  - tableless

---
## Entendendo a propriedade Position

O Position é uma propriedade perigosa para iniciantes. Normalmente o desenvolvedor que acaba de conhecer essa propriedade, acha que ela é a resposta para todos os problemas de posicionamento e diagramação de layout. Pelo contrário. O Position não serve para diagramar a estrutura de layouts. Para isso, você utiliza a [propriedade float do css][1]. O Position vai servir para fazer coisas mais simples. 

### Coordenadas

Para posicionar seus elementos, você precisa inserir uma coordenada. Essas coordenadas são comandadas pelas propriedades: top, left, right ou bottom. Todos os valores de positions só trabalham com essas coordenadas. Obviamente, se você definir um left para o seu elemento, não faz sentido definir um right. A mesma coisa para o bottom e o top. Em código ficaria assim:

<pre class="lang-css">div {
  position: absolute;
  top: 150px;
  left: 150px;
}
</pre>

Nesse caso eu posicionei o elemento a 150 pixels do topo e 150px da esquerda. 

Existem 3 tipos de valores que usamos na **propriedade position**: _relative_, _absolute_ e _fixed_. 

### Position Fixed

O position: fixed; irá fixar a posição do elemento na coordenada que você definir. A medida que a página é rolada, o elemento continua fixo na posição que você definiu e o conteúdo da página rola normalmente. 

Geralmente é usado para fixar elementos como cabeçalhos ou sidebars.
  
[Veja um exemplo de position fixed][2] ou [esse exemplo][3].

### Position Relative

Todos os positions precisam de um ponto para iniciar o cálculo da coordenada para assim posicionar o elemento na tela. Ao contrário do que muitos acham, esse ponto não é o ponto central do elemento, o ponto base é o canto superior esquerdo do elemento. A partir deste canto, o browser irá calcular a coordenada que você definiu e irá posicionar o elemento no viewport.

O position relative posiciona o elemento em relação a si mesmo. Ou seja, o ponto zero será o canto superior esquerdo, e ele começará a contar a partir dali. 

[<img src="http://tableless.com.br/uploads/2009/05/position-relative.gif" alt="position-relative" title="position-relative" width="400" height="400" class="alignnone size-full wp-image-1408" srcset="uploads/2009/05/position-relative.gif 400w, uploads/2009/05/position-relative-150x150.gif 150w, uploads/2009/05/position-relative-300x300.gif 300w" sizes="(max-width: 400px) 100vw, 400px" />][4]

### Position Absolute

O Position Absolute é um tanto diferente do Relative. Enquanto o elemento com Position Relative utiliza seu próprio canto para referenciar sua posição, o elemento com Position Absolute se utiliza do ponto superior esquerdo de outros elementos. Estes elementos são os parentes dele do elemento com position absolute. Mais especificamente o pai.

[<img src="http://tableless.com.br/uploads/2009/05/position-absolute.gif" alt="position-absolute" title="position-absolute" width="500" height="500" class="alignnone size-full wp-image-1409" srcset="uploads/2009/05/position-absolute.gif 500w, uploads/2009/05/position-absolute-150x150.gif 150w, uploads/2009/05/position-absolute-300x300.gif 300w" sizes="(max-width: 500px) 100vw, 500px" />][5]

[Veja um exemplo em HTML.][6]

No caso, se o DIV pai não tivesse position definido, o div filho iria se referenciar pelo BODY mesmo. Se caso o div pai não tivesse position definido, e se ele também fosse envolvido por outro div com position, o div filho iria se referenciar por este terceiro div.
  
Logo, o div com position absolute referencia sua posição pelo div mais próximo que o envolve e que também tenha um position definido. Complicado, não é?

Uma ocasião bem simples onde usaríamos position é na home do Flickr. Onde temos aquela imagem bonita de capa e o nome do autor logo abaixo. Para posicionar o nome do autor lá no rodape do div, você utilizaria o Position. Veja a imagem de exemplo:

[<img src="http://tableless.com.br/uploads/2009/05/flickr-exemplo.jpg" alt="flickr-exemplo" title="flickr-exemplo" width="578" height="411" class="alignnone size-full wp-image-1414" srcset="uploads/2009/05/flickr-exemplo.jpg 578w, uploads/2009/05/flickr-exemplo-300x213.jpg 300w" sizes="(max-width: 578px) 100vw, 578px" />][7]

 [1]: http://tableless.com.br/propriedade-float-do-css
 [2]: http://tableless.com.br/uploads/2009/04/fixed.html
 [3]: http://tableless.github.io/exemplos/position-fixed.html
 [4]: http://tableless.com.br/uploads/2009/05/position-relative.gif
 [5]: http://tableless.com.br/uploads/2009/05/position-absolute.gif
 [6]: http://tableless.com.br/uploads/2009/05/position-absolute.html "Exemplo de com funciona o Position Absolute"
 [7]: http://tableless.com.br/uploads/2009/05/flickr-exemplo.jpg