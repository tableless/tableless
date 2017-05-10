---
title: Elementos de interface utilizando apenas CSS3
author: Davi Ferreira
type: post
date: 2013-05-09
excerpt: Você sabia que já é possível criar interfaces ricas sem escrever código JavaScript? Nesse artigo você confere algumas implementações de elementos de interfaces ricas que utilizam apenas CSS3.
url: /elementos-de-interface-utilizando-apenas-css3/
dsq_thread_id: 1272770615
categories:
  - CSS3
tags:
  - 2013
  - animacao css
  - css2
  - CSS3
  - elementos de interface
  - html
  - interface
  - JavaScript

---
Se por um lado está na hora de você [parar de usar jQuery para tudo e investir mais em códigos JavaScript][1], por outro já é possível criar elementos animados e interativos utilizando apenas CSS3.

É claro que você vai precisar abrir mão de efeitos em navegadores antigos (ou, na maioria dos casos, da implementação inteira). É claro também que as implementações são até certo ponto limitadas em comparação a plugins e bibliotecas JavaScript, mas dão um show em performance e otimização.

Botões, galerias/slides, tabs e até mesmo o famoso efeito de lightbox já podem ser implementados sem nenhuma linha de JavaScript. Confira alguns exemplos.

## Galeria

[<img src="http://tableless.com.br/uploads/2013/05/gallery-css.jpg" alt="gallery-css" width="660" height="342" class="alignnone size-full wp-image-37344" srcset="uploads/2013/05/gallery-css.jpg 660w, uploads/2013/05/gallery-css-324x168.jpg 324w, uploads/2013/05/gallery-css-588x304.jpg 588w, uploads/2013/05/gallery-css-598x310.jpg 598w" sizes="(max-width: 660px) 100vw, 660px" />][2]

[http://benschwarz.github.io/gallery-css/][2]

Ben Schwarz caprichou e lançou recentemente uma galeria utilizando apenas CSS3. A galeria permite controles personalizados e vem com uma animação para autoplay. 

Os slides podem conter qualquer conteúdo em HTML e o grande segredo por trás dessa galeria é o uso de âncoras (#) aliado a elementos com position:absolute e o pseudo-atributo [:target][3].

O pseudo atributo target é aplicado em elementos referenciados por uma âncora. Por exemplo, sua página tem um elemento section com o id &#8220;section-1&#8221; e um link para a âncora #section-1. Quando o usuário clicar nesse link, o CSS definido na regra section:target será aplicado no elemento #section-1.

## Lightbox

[<img src="http://tableless.com.br/uploads/2013/05/lightbox-css.jpg" alt="lightbox-css" width="660" height="342" class="alignnone size-full wp-image-37345" srcset="uploads/2013/05/lightbox-css.jpg 660w, uploads/2013/05/lightbox-css-324x168.jpg 324w, uploads/2013/05/lightbox-css-588x304.jpg 588w, uploads/2013/05/lightbox-css-598x310.jpg 598w" sizes="(max-width: 660px) 100vw, 660px" />][4]

[http://tympanus.net/codrops/2011/12/26/css3-lightbox/][4]

O efeito Lightbox é um dos grandes responsáveis pela popularização do JavaScript e suas bibliotecas. Hoje já existem centenas de clones do original, com diferentes configurações e a versão CSS supera muitas dessas implementações em JavaScript.

## Menu Dropdown

[<img src="http://tableless.com.br/uploads/2013/05/dropdown-css.jpg" alt="dropdown-css" width="660" height="342" class="alignnone size-full wp-image-37343" srcset="uploads/2013/05/dropdown-css.jpg 660w, uploads/2013/05/dropdown-css-324x168.jpg 324w, uploads/2013/05/dropdown-css-588x304.jpg 588w, uploads/2013/05/dropdown-css-598x310.jpg 598w" sizes="(max-width: 660px) 100vw, 660px" />][5]

[http://line25.com/tutorials/how-to-create-a-pure-css-dropdown-menu][5]

Outro elemento bastante popular em JavaScript é o menu dropdown. Sua versão CSS usa apenas o atributo :hover dos links para exibir e esconder os múltiplos níveis de submenus.

Ainda dá para usar algum tipo de transition ou animation para deixar o menu mais atraente. Quem se habilita? 🙂

## Abas

[<img src="http://tableless.com.br/uploads/2013/05/tabs-css.jpg" alt="tabs-css" width="660" height="342" class="alignnone size-full wp-image-37346" srcset="uploads/2013/05/tabs-css.jpg 660w, uploads/2013/05/tabs-css-324x168.jpg 324w, uploads/2013/05/tabs-css-588x304.jpg 588w, uploads/2013/05/tabs-css-598x310.jpg 598w" sizes="(max-width: 660px) 100vw, 660px" />][6]

[http://www.sitepoint.com/css3-tabs-using-target-selector/][6]

E que tal uma interface separada por abas sem usar JavaScript? É isso que este tutorial do Sitepoint oferece, mais uma vez fazendo uso do atributo target.

## Tooltip

[<img src="http://tableless.com.br/uploads/2013/05/tooltip-css.jpg" alt="tooltip-css" width="660" height="342" class="alignnone size-full wp-image-37347" srcset="uploads/2013/05/tooltip-css.jpg 660w, uploads/2013/05/tooltip-css-324x168.jpg 324w, uploads/2013/05/tooltip-css-588x304.jpg 588w, uploads/2013/05/tooltip-css-598x310.jpg 598w" sizes="(max-width: 660px) 100vw, 660px" />][7]

[http://kushagragour.in/lab/hint/][7]

Tooltips possuem dezenas de implementações utilizando JavaScript. Sua versão CSS3 usa e abusa dos pseudo atributos [:after e :before][8]. 

Uma nota importante: as transições nos atributos after e before só foram implementadas recentemente no Chrome (versão 26). Nada que impeça a tooltip de funcionar &#8211; ela apenas será renderizada sem animações.

## Botões

[<img src="http://tableless.com.br/uploads/2013/05/buttons-css.jpg" alt="buttons-css" width="660" height="342" class="alignnone size-full wp-image-37342" srcset="uploads/2013/05/buttons-css.jpg 660w, uploads/2013/05/buttons-css-324x168.jpg 324w, uploads/2013/05/buttons-css-588x304.jpg 588w, uploads/2013/05/buttons-css-598x310.jpg 598w" sizes="(max-width: 660px) 100vw, 660px" />][9]

[http://hellohappy.org/css3-buttons/][9]

Não é só JavaScript que pode ser cortado &#8211; também podemos parar de utilizar sprites para botões. Hoje em dia já é possível criar botões consistentes e interativos utilizando apenas CSS3.

O designer Chad Mazzola mantém um repositório de botões &#8220;que utilizam o markup mais simples possível&#8221;. Este é um bom ponto de partida, mas os exemplos de botões utilizando apenas CSS são os mais fáceis de encontrar.

## Evento de clique

[http://www.ryancollins.me/?p=1041][10]

Esse último exemplo não é bem um elemento, mas sim uma aplicação do evento de clique utilizando o atributo active de um elemento. Com poucas linhas de código é possível exibir/esconder um menu ao clicar em um botão.

E você, já deixou de fazer alguma coisa em JavaScript para implementar utilizando apenas CSS? Diz aí nos comentários!

 [1]: http://tableless.com.br/criando-um-plugin-javascript-sem-jquery/
 [2]: http://benschwarz.github.io/gallery-css/ "http://benschwarz.github.io/gallery-css/"
 [3]: http://www.w3.org/TR/css3-selectors/#target-pseudo "http://www.w3.org/TR/css3-selectors/#target-pseudo"
 [4]: http://tympanus.net/codrops/2011/12/26/css3-lightbox/ "http://tympanus.net/codrops/2011/12/26/css3-lightbox/"
 [5]: http://line25.com/tutorials/how-to-create-a-pure-css-dropdown-menu "http://line25.com/tutorials/how-to-create-a-pure-css-dropdown-menu"
 [6]: http://www.sitepoint.com/css3-tabs-using-target-selector/ "http://www.sitepoint.com/css3-tabs-using-target-selector/"
 [7]: http://kushagragour.in/lab/hint/ "http://kushagragour.in/lab/hint/"
 [8]: http://www.w3.org/TR/css3-selectors/#gen-content
 [9]: http://hellohappy.org/css3-buttons/ "http://hellohappy.org/css3-buttons/"
 [10]: http://www.ryancollins.me/?p=1041 "http://www.ryancollins.me/?p=1041"