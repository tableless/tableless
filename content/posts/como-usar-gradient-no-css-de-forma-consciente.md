---
title: Como usar linear-gradient em CSS de forma consciente?
author: Bernard De Luna
type: post
date: 2013-03-20
excerpt: Não há mais motivo para você usar nenhum gerador automático de gradiente depois desse GUIA DEFINITIVO DE COMO USAR LINEAR-GRADIENT. Vem comigo e vamos codar.
url: /como-usar-gradient-no-css-de-forma-consciente/
dsq_thread_id: 1152407042
categories:
  - CSS3
  - Geral
  - HTML
tags:
  - background-image
  - bernard de luna
  - degrade css
  - linear-gradient
  - old radio
  - rgba

---
Vejo em diversos grupos, fóruns e blogs as pessoas recomendando diversos sites que geram automaticamente o seu linear-gradient em CSS, Eu nos últimos meses tenho criticado um pouco a recomendação dessas tecnologias, pois já está mais do que na hora de aprendermos e utilizarmos esses atributos de forma criativa.

## Desculpa Bernard, mas do que você está falando?

Olá tudo bem? Meu nome é Bernard De Luna, você está no Tableless, até aí tudo bem? Brincadeira, deixa eu contextualizá-lo primeiro:

`linear-gradient` é uma funcionalidade das CSS3 para criar degrades entre 2 ou mais cores em linha. Farei um pequeno exemplo para perceberem como é fácil fazer um gradiente sem utilizar editor:

OBS: Por questão de compatibilidade de browsers, vale a pena vocês consultarem o <a href="http://caniuse.com/#search=linear" title="http://caniuse.com/#search=linear" target="_blank">http://caniuse.com/#search=linear</a> para usar prefixos como -webkit, -moz, -ms, -o, etc., **para esses exemplos não utilizarei prefixos**. Outro ponto importante é que na nova especificação, o &#8220;top&#8221; virou &#8220;to bottom&#8221;, porém essa mudança só existe no valor sem prefixo, as escritas com prefixo ainda usam a direção top, right, bottom, left como padrões.

## linear-gradient nível básico

O gradiente é renderizado como uma imagem de fundo, então podemos chamá-lo assim. Dentro do ( ) temos que definir o ângulo do degrade e depois em vírgulas os canais de cores.

<pre class="lang-css">background-image: linear-gradient(to bottom, white, purple);</pre>

<div class="exemplo e1">
</div>

Mudando o ângulo do degrade

<pre class="lang-css">background-image: linear-gradient(to right, white, purple);</pre>

<div class="exemplo e2">
</div>

<pre class="lang-html">background-image: linear-gradient(45deg, white, purple);</pre>

<div class="exemplo e3">
</div>

Podemos colocar mais vírgulas e inserir mais canais de cores para o degrade, até agora tudo muito simples né?

<pre class="lang-css">background-image: linear-gradient(to right, white, purple, yellow);</pre>

<div class="exemplo e4">
</div>

O problema das explicações sobre gradient é que são todas feias e não usuais, o que dificulta algumas pessoas se sentirem confiantes em criá-las, por isso, vamos criar um degrade bacana para um botão.

<pre class="lang-css">background-image: linear-gradient(to bottom, #cf2b4f, #980021);</pre>

<div class="exemplo e5">
</div>

Eu prefiro degrades mais suaves, por isso, vamos aprender outra coisa importante no `linear-gradient`, que é onde a cor vai parar. Então vamos dizer que o vermelho mais escuro não finalizará no padrão (não informado) de 100%, vamos fazê-lo parar um pouco depois, suavizando um pouco mais o gradiente.

<pre class="lang-css">background-image: linear-gradient(to bottom, #980021 130%);</pre>

<div class="exemplo e6">
</div>

Viram que ficou mais bonito? Para ficar ainda mais visual, colocarei alguns estilos simples para perceberem que somados fazem nosso elemento ficar bastante sexy!

<pre class="lang-css">height:auto;
padding: 40px 0;
color:#fff;
font-size:20px;
text-align:center;
border-radius:4px;
border:1px solid #980021;
box-shadow: inset 0 2px 3px 0 rgba(255,255,255,.3), inset 0 -3px 6px 0 rgba(0,0,0,.2), 0 3px 2px 0 rgba(0,0,0,.2);
background-image: linear-gradient(to bottom, #cf2b4f, #980021 130%);
</pre>

<div class="exemplo e7">
  olha como eu sou sexy!
</div>

**Como esse post é apenas sobre degrade, vamos voltar para o assunto 🙂**

Em alguns casos, você não precisa definir as cores precisamente do seu degradee, passando a usar transparência para isso. Por exemplo, você pode utilizar o `background-color` para definir a cor de fundo, e depois utilizar um degrade que vai do transparente para o preto com 30% de transparência, vejamos:

<pre class="lang-css">background-color:#4fd8e8;
background-image: linear-gradient(to bottom, transparent, rgba(0,0,0,.3));</pre>

<div class="exemplo e8">
</div>

O novo rgba é interessantíssimo para fazer diversas coisas no CSS, como por exemplo fazer um elemento estilo GLASS. Há muitos anos atrás, lá pelos 2006 &#8211; 2007, o estilo visual de vidro estava tomando todas as interfaces, um dia identifiquei um padrão para criar botões de vidro com facilidade. A técnica era tão fácil que até hoje eu lembro dela, basta você começar com uma cor CLARA que vai para uma cor MUITO CLARA, **colado a essa cor** MUITO CLARA você tem a mesma cor NORMAL, e finaliza com a cor UM POUCO CLARA, apenas essas 4 variações da mesma cor, ou da luz, não acredita? Veja só.

<pre class="lang-css">background-color:#4fd8e8;
background-image: linear-gradient(to bottom, rgba(255,255,255,.1), rgba(255,255,255,.4), rgba(255,255,255,0), rgba(255,255,255,.4));</pre>

<div class="exemplo e9">
</div>

Sei que essa hora você está rindo de mim dizendo que não ficou nem parecido com glass, que ficou horrível, que eu sou loiro e burro. Eu sei, mas lembra que eu falei que a cor precisava ser colada(coloquei até em negrito porque eu sabia que você não repararia)? Vamos ajustar o **&#8220;color stop&#8221;** do degrade, em outras palavras, vamos ajustar onde cada cor vai parar.

<pre class="lang-css">background-color:#4fd8e8;
background-image: linear-gradient(to bottom, rgba(255,255,255,.1), rgba(255,255,255,.4) 49%, rgba(255,255,255,0) 50%, rgba(255,255,255,.4));</pre>

<div class="exemplo e10">
</div>

Agora sim hein! Como diz Bart Simpsons &#8220;_Meninos loiros não são burros, eles são maus, como em Karate Kid ou II Guerra Mundial_&#8220;. O mais bacana é que como o degrade está sendo feito com camadas de transparência, você pode fazer qualquer efeito ou adaptação do efeito através da simples mudança de cor de fundo. Outro ponto muito importante é que o **CSS transition não funciona para o linear**, pois o mesmo é renderizado como IMAGEM, sendo assim, você consegue mudar apenas a cor de fundo e utilizar o CSS transition para tornar o movimento mais divertido. Veja só:

<pre class="lang-css">{
height:auto;
padding: 40px 0;
color:#fff;
font-size:20px;
text-align:center;
background-color:#4fd8e8;
background-image: linear-gradient(to bottom, rgba(255,255,255,.1), rgba(255,255,255,.4) 49%, rgba(255,255,255,0) 50%, rgba(255,255,255,.4));
transition: all .5s;
}
:hover { background-color:#0b8b9a; }</pre>

<div class="exemplo e11">
  HOVER ME!
</div>

## linear-gradient nível intermediário

Agora que você já entendeu como fazer degrades simples utilizando o `linear-gradient`, vamos brincar um pouco mais? Quando eu criei o <a title="https://developer.mozilla.org/en-US/demos/detail/old-radio/launch" href="https://developer.mozilla.org/en-US/demos/detail/old-radio/launch" target="_blank">Old Radio</a> sem utilizar nenhuma imagem eu tive 3 itens para trabalhar a realidade apenas com CSS: a retina display, a textura de madeira e as estações do rádio, vamos aprender a fazer as três coisas?

### Retina Display

Essa técnica foi bem simples, mas o resultado ficou muito bom, única coisa que precisamos é utilizar a transparência do RGBA mostrada anteriormente e um ângulo diferente para dar o efeito, no Old Radio eu usei -88deg, mas aqui colocarei -78deg para ficar mais visível, veja só:

<pre class="lang-css">background-color:#312d28;
background-image:linear-gradient(-87deg, rgba(255,255,255,0.1) 0%,rgba(255,255,255,0.08) 49%,rgba(255,255,255,0.03) 50%,rgba(0,0,0,0) 51%,rgba(0,0,0,0.4) 100%);</pre>

<div class="exemplo e12">
</div>

### Textura de Madeira

Fiquei bons minutos olhando para a textura de madeira sem saber como a faria em CSS, até mesmo se seria possível, até que fiz um teste utilizando o RGBA em cima da cor marrom e rapidamente vi que poderia criar uma técnica bem divertida para transformar uma cor marrom em uma textura de madeira. A técnica é utilizar 2 únicas cores, sendo uma transparente e outra com 10% de transparência, veja bem como foi feita:

<pre class="lang-css">background-color:#5f3c24;
background-image:linear-gradient(to bottom, transparent, rgba(0,0,0,.1));</pre>

<div class="exemplo e13">
</div>

Agora digo que cada cor para depois de 1px, como a altura do elemento é maior que 2px (só temos duas cores), a última cor persistirá até o final do elemento.

<pre class="lang-css">background-color:#5f3c24;
background-image:linear-gradient(to bottom, transparent 1px, rgba(0,0,0,.1) 1px);</pre>

<div class="exemplo e14">
</div>

Para finalizar, eu utilizo um atributo novo bem importante que é o `background-size` onde eu digo que a altura do meu degrade é de 2px, como o padrão do fundo é repetir, as linhas começam a se repetir, fazendo uma textura bem suave de madeira.

<pre class="lang-css">background-color:#5f3c24;
background-image:linear-gradient(to bottom, transparent 1px, rgba(0,0,0,.1) 1px);
background-size: auto 2px;</pre>

<div class="exemplo e15">
</div>

Prontinho! Temos uma textura de madeira apenas com gradiente, caso você não esteja conseguindo ver a diferença, dê um zoom no browser e veja a belezura 🙂 Então vamos ao último e mais difícil das 3 coisas do Old Radio, as estações de rádio.

### Estações de rádio

Criar as estações de rádio apenas com uma tag e apenas no CSS parecia ser algo impossível, mas nada que um estudo não pudesse me mostrar novamente que tudo é possível com CSS, é apenas combinar o gradiente com repetição, posição e tamanho do background. Inicialmente vamos criar várias palhetas utilizando a mesma técnica do exercício anterior:

<pre class="lang-css">background-color:#312d28;
background-image: linear-gradient(to right, rgba(255,255,255,.3) 1px, transparent 1px);
background-size: 5px 5px;</pre>

<div class="exemplo e16">
</div>

Só que nós não queremos que o nosso fundo vá até o final, repare que colocamos o `background-size: 5px 5px`, mas de que adianta isso se não mexermos no `background-repeat`? Então vamos definir que o nosso fundo só vai se repetir horizontalmente. Para o exercício ficar mais visível vou aumentar um pouco o tamanho das palhetas ok?

<pre class="lang-css">background-color:#312d28;
background-image: linear-gradient(to right, rgba(255,255,255,.3) 1px, transparent 1px);
background-size: 10px 10px;
background-repeat: repeat-x;</pre>

<div class="exemplo e17">
</div>

Agora vem uma coisa bem legal! O CSS3 permite múltiplos backgrounds, ou seja, vamos agora fazer a mesma técnica para essas palhetas pequenas, com apenas duas diferenças, ela vai ser um branco mais forte e estará com o `backgrond-size` diferente. OBS: Quando você tem mais de uma imagem de fundo, você pode controlar cada propriedade do background usando vírgulas, sendo a primeira informação para o primeiro fundo, a segunda para o segundo e assim vai, se houver uma só, ela valerá para todos.

<pre class="lang-css">background-color:#312d28;
background-image: linear-gradient(to right, rgba(255,255,255,1) 1px, transparent 1px), linear-gradient(to right, rgba(255,255,255,.3) 1px, transparent 1px);
background-size: 50px 50px, 10px 30px;
background-repeat: repeat-x;</pre>

<div class="exemplo e18">
</div>

Irado hein!!! Só que isso é uma régua meu camarada e não uma estação de rádio. Para parecer definitivamente uma estação de rádio precisaremos alinhar o fundo pela parte de baixo, e isso é simples e antigo no css, chama-se `background-position`.

<pre class="lang-css">background-color:#312d28;
background-image: linear-gradient(to right, rgba(255,255,255,1) 1px, transparent 1px), linear-gradient(to right, rgba(255,255,255,.3) 1px, transparent 1px);
background-size: 50px 50px, 10px 30px;
background-repeat: repeat-x;
background-position: 0 bottom;</pre>

<div class="exemplo e19">
</div>

Agora sim! Parabéns, você criou uma estação de rádio apenas usando CSS! Can you feel it?

## Concluindo&#8230;

Os atributos não são muito complicados de serem utilizados, a percepção é que faz toda a diferença para uma aplicação criativa. Agora é você criar experimentos com essas etapas que foram mostradas aqui e ficar O MOOOOONNNSTRROOO do linear-gradient! Quem sabe depois não vem um apenas sobre radial-gradient? 

Aproveite que chegou até aqui e me conte o que achou 🙂 Você já sabia fazer essas coisas com facilidade usando linear-gradient? Deixe seu comentário 

OBS1: Com a nova especificação do valor linear-gradient, o ângulo 0 deixou de ser top e passou a ser right, sendo valores positivos para seguir na direção do relógio e negativo para o contrário. (chamada de atenção pelo grande Sergio Lopes) *já corrigido.
  
OBS2: Chamei no começo do artigo linear-gradient de propriedade o que é errado, já que ele é um valor. (chamada de atenção pelo amigo Maujor) *já corrigido.