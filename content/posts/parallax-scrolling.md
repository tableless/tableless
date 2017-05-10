---
title: Parallax Scrolling
author: Dani Guerrato
type: post
date: 2012-12-03
excerpt: Entenda como funciona o efeito parallax.
url: /parallax-scrolling/
tweetbackscheck:
  - 1356469546
shorturls:
  - 'a:3:{s:9:"permalink";s:31:"http://tableless.com.br/?p=7446";s:7:"tinyurl";s:26:"http://tinyurl.com/crq62pr";s:4:"isgd";s:19:"http://is.gd/5T9p0x";}'
twittercomments:
  - 'a:0:{}'
dsq_thread_id: 956106242
categories:
  - Artigos
  - JavaScript
  - JQuery
tags:
  - JavaScript
  - paralaxe
  - parallax
  - stellar.js

---
Parallax Scrolling foi uma das grandes tendências do webdesign em 2012. Mesmo que você não conheça o termo é capaz de já ter visto o efeito por aí&#8230; Ele serve para dar a ilusão de profundidade de campo e pode ser utilizado para criar uma experiência de navegação bem diferentes do convencional. Neste artigo vamos entender da onde surgiu este termo, quais cuidados devemos tomar e é claro, como implementar o efeito de parallax scrolling através de javascript.

## O que afinal é parallax?

Segundo  a Wikipedia:

> Parallax é uma entidade cósmica que nutre e se alimenta do próprio medo que espalha nos seres vivos dos planetas que são tocados por sua energia amarela.

Opa, Parallax errado! Esta é o vilão da DC. O termo certo em português é &#8220;paralaxe&#8221;. Vamos a definição correta da nossa grande amiga [Wikipedia][1]:

> Paralaxe é a alteração aparente de um objeto contra um fundo devido ao movimento do observador.

Parece confuso? Existe uma experiência simples para ver este efeito no &#8220;mundo real&#8221;. Você pode testar agora mesmo. Levante seu dedo indicador e estique o braço. Agora feche um olho e preste atenção no fundo atrás do seu dedo. Depois, ainda com o braço parado, feche o olho que estava aberto e abra o outro. A impressão é que dá é que seu dedo &#8220;andou&#8221; em relação ao fundo, certo?

## O que isto tem a ver com desenvolvimento web?

Na verdade esta não é uma idéia muito nova. Utilizar camadas de imagens que se movem em velocidades diferentes é uma técnica que já foi muito utilizada no cinema e até em video games. Quem é um pouco mais velho certamente se lembra dos jogos 2D. As camadas de cenário em jogos como Super Mario, por exemplo, criavam a ilusão de profundidade de campo quando o personagem se movia pela tela. A idéia aqui é a mesma. Utilizar elementos gráficos como texto, imagens, background etc sobrepostos em camadas que se movem em diferentes velocidades de acordo com a rolagem do mouse na tela.

A febre se espalhou mesmo na internet com o site Nike Better World (A Smashing Magazine inclusive tem um [case][2] bem interessante sobre o projeto). Desde então o parallax foi utilizado em inúmeras situações e se tornou uma ótima ferramenta de storytelling, já que o efeito é ótimo para criar uma continuidade visual como no site [Ben, the bodyguard][3]. Ou até mesmo uma história em quadrinhos interativa de como a [Soul Reaper][4].

## Alguns cuidados necessários

OK. Uma vez tomada a decisão de utilizar o efeito, para aplica-lo na prática é necessário bastante planejamento e uma boa integração entre o designer e o desenvolvedor. É importante sentar junto para pensar quais elementos do layout devem se sobrepor, a qual velocidade, em que momento deverão &#8220;aparecer&#8221; e &#8220;sumir&#8221; da tela&#8230; Esta etapa é fundamental e se pulada pode levar a uma grande confusão visual digna dos idos tempos do Flash. E o que tinha a intenção de melhorar a experiência acaba atrapalhando&#8230; Por isto capriche no wireframe. Pode ser um documento detalhado ou um rabisco no verso de uma folha que só a sua equipe compreende, o importante é ter as informações do projeto pensadas antes de iniciar o desenvolvimento em si ao invés de ficar na tentativa e erro.

## Stellar

Existem diversos métodos de implementar o efeito parallax, a maior parte se baseia em jQuery. Neste artigo vou me focar no plugin [stellar.js][5] por sua fácil implementação, flexibilidade de uso  e compatibilidade com dispositivos móveis.

A primeira decisão a ser tomada é se a rolagem do site será horizontal ou vertical, já que ambas são permitidas pelo plugin. Para este artigo vamos exemplificar com elementos verticais.

#### Os Elementos Parallax

A velocidade natural de scroll dos elementos é 1. O que este plugin faz é altera-la através do parâmetro data-stellar-ratio.  Uma observação importante é que a posição dos elementos deve ser declarada no CSS como absolute, relative ou fixed.

Este exemplo duplica a velocidade de scroll da div.

<pre>&lt;div data-stellar-ratio="2"&gt;</pre>

Lembre-se de trocar o número &#8220;2&#8221; pela velocidade desejada. Você pode até utilizar números negativos para inverter a direção dos elementos.

#### Parallax Backgrounds

Este parâmetro altera a rolagem do fundo de acordo com a rolagem do mouse.

<pre><strong>&lt;div data-stellar-background-ratio="0.5"&gt;</strong></pre>

#### Offsets

Determina em qual posição o elemento vai voltar para a sua posição original. Isto pode ser aplicado de duas maneiras:

**Configura o Offset de todos os elementos:**

<pre>$.stellar({
  horizontalOffset: 40,
  verticalOffset: 150
});</pre>

**Apenas de um elemento:**

<pre>&lt;div data-stellar-ratio="2"
     data-stellar-horizontal-offset="40"
     data-stellar-vertical-offset="150"&gt;</pre>

**Offset Parents**

Por padrão o offset (momento em que o objeto &#8220;some&#8221; da tela) é sempre relativo ao elemento container. O elemento pai é sempre o item mais próximo com uma posição fixed ou absolute (como no CSS). Mas é possível &#8220;forçar&#8221; outro elemento a ser o parent

<pre><strong>&lt;div data-stellar-offset-parent="true"&gt;</strong></pre>

O parent também pode ter seus próprios Offset

<pre>&lt;div data-stellar-offset-parent="true"
     data-stellar-horizontal-offset="40"
     data-stellar-vertical-offset="150"&gt;</pre>

#### Scroll Positioning

Você consegue determinar o que exatamente significa &#8220;scroll&#8221;. Se é mudar de posição, CSS transform, etc É isto que permite o stellar funcionar no iOS. Exemplo utilizando CSS transforms:

<pre>$('#gallery').stellar({
  positionProperty: 'transform'
});</pre>

Para mais informações, não se esqueça de conferir a [documentação][6] do plugin e/ou o repositório no [Github][7].

## Uma dica importante

Aqui cabe um alerta. O paralax scrolling é mesmo um efeito bacana e é legal conhecer a técnica, mas é importante saber **quando** é o melhor momento para se utilizar. Antes de adicionar, não apenas este efeito especificamente como qualquer outro elemento visual, não se esqueça da pergunta &#8220;Por que eu quero fazer isto?&#8221;&#8230;. Principalmente no caso de efeitos e animações que podem influir negativamente na experiência do usuário trazendo poluição visual, aumento no tempo de carregamento de uma pagina, etc. E se a resposta for apenas &#8220;porque é bonitinho&#8221; é melhor pensar duas vezes antes de utilizar parallax scrolling. Como qualquer aspecto do design, é importante que o parallax seja utilizado não apenas como um efeito visual, mas como parte integrante do storytelling.

 [1]: http://pt.wikipedia.org/wiki/Paralaxe "Paralaxe"
 [2]: http://coding.smashingmagazine.com/2011/07/12/behind-the-scenes-of-nike-better-world/ "Behind the scenes of nike better world"
 [3]: http://benthebodyguard.com "Ben the bodyguard"
 [4]: http://www.soul-reaper.com "Soul Reaper"
 [5]: http://markdalgleish.com/projects/stellar.js/ "Stellar.js"
 [6]: http://markdalgleish.com/projects/stellar.js/docs/ "Documentação Stellar"
 [7]: https://github.com/markdalgleish/stellar.js "Github"