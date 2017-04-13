---
title: Ícones – SVG Sprites com CSS na prática
author: rogerio dias moreira
type: post
date: 2015-05-29
excerpt: Criando um sprites usando ícones SVG.
url: /icones-svg-sprites-com-css-na-pratica/
categories:
  - CSS
  - HTML
tags:
  - CSS
  - svg
  - svg sprites
  - wai-aria

---
O uso de ícones com SVG pode ser usado como uma alternativa mais poderosa, semântica e leve em relação a tradicional técnica de Icon Font.

O artigo abaixo abordará de forma prática o uso de ícones SVG com o uso das seguintes técnicas: SVG (defs, symbol), HTML + CSS + SVG (use). Como diziao Chapolin: &#8220;Sigam-me os bons!&#8221;

## Obtendo arquivos SVG

O site [FlatIcon][1] contém alguns ícones gratuitos que podem ser baixados no formato SVG. Para este exemplo serão usados os dois arquivos SVG abaixo para compor o sprite:

  * [http://www.flaticon.com/free-icon/save-disk_13842][2]
  * [http://www.flaticon.com/free-icon/download-arrow_64090][3]

A figura abaixo mostra o código fonte das duas imagens:

[<img class="alignnone size-full wp-image-49046" src="http://tableless.com.br/uploads/2015/05/figura_exemplo_svg_fonte1.png" alt="figura_exemplo_svg_fonte1" width="1295" height="744" />][4]

Percebam que existe muito &#8216;lixo&#8217; nos arquivos gerados pela ferramenta do site mas o que realmente importa é o grupo (&#8216;<g>&#8217;) que contém os polígonos juntamente com a informação de viewBox que está destacada.

## Montando arquivo svg contendo sprites

Usaremos uma técnica de SVG Symbol, juntamente com o elemento defs, para construir um arquivo SVG contendo sprites de imagens. Quando criamos um elemento `<symbol />` podemos reusá-lo mais tarde através do elemento `<use />`. O MDN tem mais detalhes sobre esses elementos: [https://developer.mozilla.org/pt-BR/docs/Web/SVG/Element/symbol][5] e [https://developer.mozilla.org/en-US/docs/Web/SVG/Element/defs][6]

A figura abaixo mostra a montagem do arquivo de sprites dentro da seguinte estrutura: `<svg><defs><symbol /></defs></svg>`. Para cada elemento <symbol> devemos atribuir um id juntamente com a viewBox da imagem e transpor os polígonos para dentro do elemento.

[<img class="alignnone size-full wp-image-49051" src="http://tableless.com.br/uploads/2015/05/figura_svg_exemplo_fonte2.png" alt="figura_svg_exemplo_fonte2" width="1033" height="327" />][7] Note que foi retirada a estilização (style) do SVG para que a mesma seja feita via CSS.

## Usando ícones SVG dentro da página HTML

Para o uso das imagens dentro do html foi utilizado o elemento <svg> juntamente com o elemento <use> para referenciar o sprite (symbol) contido no arquivo. O atributo role=&#8217;button&#8217; foi utilizado obedecendo a especificação WAI-ARIA para acessibilidade, onde foi utilizado o atributo title para uma pequena descrição do que o button irá fazer.

O tamanho da imagem, juntamente com a cor de preenchimento, foi definida via CSS, sendo que podemos explorar efeitos simples como mudança de cor num evento mouse over, até efeitos complexos através de animações.

[<img class="alignnone size-full wp-image-49053" src="http://tableless.com.br/uploads/2015/05/figura_svg_exemplo_fonte3.png" alt="figura_svg_exemplo_fonte3" width="820" height="538" />][8]

## Resultado final

Este exemplo foi testado com Chrome e Firefox. O Internet Explorer não suporta nativamente (tinha que ser&#8230;) o uso do elemento <use> para arquivos externos(veja [http://caniuse.com/#feat=svg][9]), sendo necessário o uso de polyfill (veja [https://github.com/jonathantneal/svg4everybody][10]).

Para quem quiser se aprofundar neste assunto não deixem de ler o seguinte artigo: <http://sarasoueidan.com/blog/structuring-grouping-referencing-in-svg/>

A figura abaixo mostra o resultado final.

[<img class="alignnone size-full wp-image-49055" src="http://tableless.com.br/uploads/2015/05/figura_svg_exemplo_fonte4.png" alt="figura_svg_exemplo_fonte4" width="1292" height="447" />][11]

 [1]: http://www.flaticon.com/ "flaticon"
 [2]: http://www.flaticon.com/free-icon/save-disk_13842 "svg"
 [3]: http://www.flaticon.com/free-icon/download-arrow_64090 "svg"
 [4]: http://tableless.com.br/uploads/2015/05/figura_exemplo_svg_fonte1.png
 [5]: https://developer.mozilla.org/pt-BR/docs/Web/SVG/Element/symbol "svg symbol"
 [6]: https://developer.mozilla.org/en-US/docs/Web/SVG/Element/defs "svg defs"
 [7]: http://tableless.com.br/uploads/2015/05/figura_svg_exemplo_fonte2.png
 [8]: http://tableless.com.br/uploads/2015/05/figura_svg_exemplo_fonte3.png
 [9]: http://caniuse.com/#feat=svg "caniuse"
 [10]: https://github.com/jonathantneal/svg4everybody "polyfill ie"
 [11]: http://tableless.com.br/uploads/2015/05/figura_svg_exemplo_fonte4.png