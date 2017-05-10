---
title: CSS Transition e CSS Animation
author: Raphael Fabeni
type: post
date: 2013-04-19
excerpt: Um guia rápido pra você entender e começar a usar essas duas propriedades do CSS3.
url: /transition-e-animation/
dsq_thread_id: 1212379971
titulo_personalizado:
  - 'Entendendo de fato as <strong>animações no CSS</strong>'
categories:
  - CSS
  - CSS3
  - HTML
tags:
  - CSS
  - CSS3
  - padroes web
  - tecnicascss
  - tutorial

---
## Transition. Prazer!

<blockquote cite="http://www.w3schools.com/css3/css3_transitions.asp">
  <p>
    &#8220;Com CSS3, podemos adicionar um efeito quando o navegador troca de um estilo para outro, sem usar animações em Flash ou JavaScript.&#8221; &#8211; w3schools
  </p>
</blockquote>

Mostrar um feedback ao usuário quando ele passar o mouse sobre um link (_:hover_) ou quando ele der foco em um campo input (_:focus_) são boas práticas. Há muitos jeitos de fazermos isso: mudando a cor do texto, tirando o _underline da palavra_, alterando a borda do _input_ que recebeu o foco ou até alterando a cor de _background_ do elemento. ([Esse][1] artigo da _Smashing Magazine_ trata muito bem a questão da estilização de links).

Normalmente fazemos isso alterando o valor de uma propriedade _CSS_ no estado _:hover_ ou _:focus_ do elemento. Quando fazemos isso, o resultado é instantâneo. Melhor dizendo, a alteração ocorre imediatamente ao usuário fazer a ação (seja passar o mouse sobre o elemento ou este ganhar foco). A alteração ocorre de forma brusca, do valor antigo da propriedade para o novo valor. Por exemplo, quando temos um elemento com borda colorida, e utilizamos o estado _:hover_ para alterarmos a cor da borda, essa transição entre uma cor e outra acontece imediatamente assim que você passa o mouse em cima do elemento.

<pre class="lang-css">div { 
   display: block;
   background-color: #666;
   width: 100px;
   height: 40px;
   border: solid 5px red;
}

div:hover { border: solid 5px black; }</pre>

É aí que entra a **transition** do _CSS3_. Ela analisa a mudança de valor entre a propriedade e faz com que essa transição, ao invés de ocorrer de forma brusca, ocorra suavemente em um tempo determinado.

<blockquote cite="http://www.w3.org/TR/css3-transitions/">
  <p>
    &#8220;CSS transitions permite que as mudanças nos valores das propriedades CSS ocorram suavemente sobre uma duração especificada.&#8221; &#8211; w3c
  </p>
</blockquote>

Nesse [exemplo][2], passe o mouse sobre o logo do Tableless abaixo e veja um exemplo da propriedade _transition_ em conjunto com a propriedade _transform_.

### Tá legal, entendi. Mas como faz?

A propriedade transition possui quatro propriedades para você configurar:

  * _transition-property_*,
  * _transition-duration_*,
  * _transition-timing-function_
  * e _transition-delay_.

<small>* propriedades obrigatórias na declaração. As demais caso omitidas, assumem seu valor <i>default</i>.</small> **transition-property**: Nome da propriedade _CSS_ sobre a qual o efeito da transição vai ser aplicado. É obrigatória na declaração pois caso seja omitida, não existirá uma propriedade para se aplicar o efeito da transição. É possível ainda aplicar uma mesma transição para todas as propriedades _CSS_ do elemento, basta colocar o valor _all_. [Aqui][3] você encontra uma tabela com todas as propriedades que suportam _transition_.

<pre class="lang-css">transition-property: border-color;</pre>

**transition-duration**: Duração do efeito em segundos (o padrão é 0). Também é obrigatória na declaração pois, se omitida, assume seu valor _default_ que é zero e a transição não vai ter efeito.

<pre class="lang-css">transition-duration: 1s;</pre>

**transition-timing-function**: Forma como a transição progride no tempo (o padrão é _ease_). Falando de um jeito mais fácil, é como se comporta o ritmo da transição durante o efeito. Pode ser usado de duas maneiras: uma é utilizando alguns valores já pré-definidos que são:

_linear_, _ease_, _ease-in_, _ease-out_ e _ease-in-out_;

<pre class="lang-css">transition-timing-function: linear;</pre>

&#8230;e a outra é definindo uma função customizada, especificando quatro coordenadas para definir a _cubic bezier curve_:

<pre class="lang-css">transition-timing-function: cubic-bezier(0.005, 0.625, 0.365, 0.0840);</pre>

Esse [site][4] ajuda e muito. Tanto para entender o funcionamento da cubic bezier, quanto para customizar a sua própria transição.

**transition-delay**: Define a partir de quanto tempo (em segundos) o efeito da transição vai se iniciar (o padrão é 0).

<pre class="lang-css">transition-delay: 0.1s;</pre>

**Passe** o mouse sobre o retângulo cinza no exemplo abaixo para ver a _transition_ em ação:

*Nos exemplos a seguir, para facilitar a leitura, não utilizei prefixos. Mas, recomendo que dêem uma olhada no [Can I Use][5] para usar os prefixos correspondentes para cada browser.

<pre class="codepen"></pre>

No exemplo acima, a propriedade que recebeu o efeito da _transição_ é a _border-color_, a _duração_ do efeito é de _1 segundo_, o _efeito_ (ou ritmo) é _linear_ e o _delay_ para a transição se iniciar é de _0.1 segundo_.

### Escrevendo menos&#8230;

É possível encurtar a sintaxe em um shortcode bem simples. Basta declarar a propriedade _transition_ que ela agrupa as quatro propriedades específicas que vimos acima. As palavras mágicas e a ordem são as seguintes:

<pre class="lang-css">div { transition: |property| |duration| |timing-function| |delay|; }</pre>

O exemplo visto acima ficaria dessa maneira:

<pre class="lang-css">div { transition: border-color 1s linear 0.1s; }</pre>

Um outro exemplo, agora adicionando o efeito da transição na _opacidade_:

<pre class="codepen"></pre>

No exemplo acima, se olharmos a aba do _CSS_ identificamos a seguinte chamada:

<pre class="lang-css">div &gt; a {
   display: block;
   transition: opacity 0.5s;
}</pre>

Podemos notar que as propriedades _timing-function_ e _delay_ foram omitidas. Com isso, elas assumem seus valores _default_ que são _ease_ e __ respectivamente.

### E mais de uma propriedade.. tem como?

É possível aplicar transições diferentes para mais de uma propriedade em um mesmo elemento. Para isso é só você separar cada bloco de declaração de efeito com vírgulas:

<pre class="lang-css">div { transition: opacity 0.5s, padding 0.25s; }</pre>

No código acima definimos duas transições:

  * a primeira com o efeito da transição aplicado na opacidade, que já havia sido configurada no exemplo anterior;
  * a segunda que define que a propriedade a receber o efeito da transição é o _padding_, a _duração_ vai ser de _0.25 segundos_, o _ritmo_ como está omitido assume seu valor _default_ que é _ease_ e o _delay_, como também está omitido, assume seu valor _default_ que é __.

<pre class="codepen"></pre>

É possível ainda definir uma transição padrão para todas as propriedades de um elemento:

<pre class="lang-css">div { transition: all 1s linear; }</pre>

No caso, definimos o valor _all_ para a _property_, o que significa que **todas** as transições do elemento terão a _duração_ de _1 segundo_, o _ritmo_ será _linear_ e o _delay_ será __.

### Suporte

  * **IE** 10
  * **FF** 1
  * **Chrome** 4
  * **Safari** 3.1
  * **Opera** 10.5

<small>Fonte: <a href="http://caniuse.com/css-transitions">Can I Use</a></small>

## Animation

<blockquote cite="http://www.w3schools.com/css3/css3_animations.asp">
  <p>
    &#8220;Com CSS3, conseguimos criar animações que podem substituir imagens animadas, animações em Flash e JavaScript em muitas páginas web&#8221; &#8211; w3schools
  </p>
</blockquote>

### A regra dos keyframes

Indo direto ao ponto: É aonde as animações são criadas.

Um keyframe descreve como o elemento que vai ser animado, deve ser renderizado em uma determinada **fase**, durante a sequência da animação.

Ou seja, cada keyframe contém uma ou mais propriedades CSS que vão ser aplicadas no elemento que será ser animado e, a animação se encarrega de mudar de um keyframe para outro, aplicando a transição entre as mudanças de CSS.

A sintaxe para a criação de keyframes é a seguinte:

<pre class="lang-css">@keyframes nomedaanimacao {
   seletores-keyframe { estilo css para esse determinado keyframe; }
}</pre>

Existem duas maneiras para se criar nossos amigos keyframes:

<pre class="lang-css">@keyframes animacao {
   from {
      width: 100px; 
      background: black;
   }
   to { 
     background: yellow;
      width: 200px;
   }
}</pre>

É a forma mais básica, onde definimos um início e um fim para a animação. No exemplo acima, _from_ é equivalente ao início da animação (_0%_) e _to_ é equivalente ao final da animação (_100%_).

<pre class="lang-css">@keyframes animacaoBolada {
   0%   { 
      background: black;
      width: 100px;
   }
   25%  { background: green; }
   50%  { background: blue; }
   75%  { background: red; }
   100% { 
      background: yellow;
      width: 200px;
   }
}</pre>

Já essa é a maneira que temos maior controle da animação. Para isso, utilizamos porcentagem para definir os _keyframes_. No código acima, a animação possui 5 passos e, a **porcentagem é relativa à duração da animação** que vai ser definida posteriormente.

Com a animação criada nos _keyframes_, precisamos vinculá-la a algum seletor, **caso contrário a animação não terá nenhum efeito**. Para fazer isso, temos que declarar pelo menos duas propriedades que são obrigatórias:

  * o nome da animação (igual ao especificado nos _keyframes_);
  * a duração da animação (se não for declarada, a animação não se inicia pois o valor padrão é 0).

Confira no [exemplo][6] as animações com os dois modelos de _keyframes_ citados acima:

Mas a _animation_ do CSS3 possui mais propriedades. Vamos conhecer as outras&#8230;.

### As propriedades

**animation-name**: Nome da animação especificada nos _@keyframes_;

<pre class="lang-css">animation-name: animacaoBolada;</pre>

**animation-duration**: Quanto tempo, em segundos ou milisegundos, durará um ciclo da animação (o padrão é 0).

<pre class="lang-css">animation-duration: 5s;</pre>

**animation-timing-function**: Forma como a animação progride no tempo (o padrão é _ease_). Do mesmo modo que a propriedade _transition_, pode ser usada de duas maneiras: uma é utilizando alguns valores já pré-definidos que são:

_linear_, _ease_, _ease-in_, _ease-out_ e _ease-in-out_;

<pre class="lang-css">animation-timing-function: ease;</pre>

&#8230; e a outra é definindo uma função customizada, especificando quatro coordenadas para definir a _cubic bezier curve_:

<pre class="lang-css">animation-timing-function: cubic-bezier(0.005, 0.0625, 0.365, 0.0840);</pre>

**animation-delay**: Define a partir de quanto tempo a animação vai se iniciar (o padrão é 0).

<pre class="lang-css">animation-delay: 0.2s;</pre>

**animation-iteration-count**: Determina o número de vezes que a animação vai se repetir (o padrão é 1). Podemos deixar a animação repetindo infinitamente, basta especificar o valor _infinite_.

<pre class="lang-css">animation-iteration-count: infinite;</pre>

**animation-direction**: Especifica se ao final da animação, ela deve reiniciar seu fluxo normalmente (_normal_), que é o padrão, ou voltar no sentido inverso (_reverse_).

<pre class="lang-css">animation-direction: reverse;</pre>

**animation-play-state**: Define se a animação está rodando (_running_), que é o padrão, ou pausada (_paused_).

<pre class="lang-css">animation-play-state: running;</pre>

### Montando o bolo&#8230;

<pre class="lang-css">div {
   animation-name: animacaoBolada;
   animation-duration: 5s;
   animation-timing-function: ease;
   animation-delay: 1s;
   animation-iteration-count: infinite;
   animation-direction: alternate;
   animation-play-state: running;
}</pre>

### Escrevendo menos&#8230;

Da mesma forma que a propriedade _transition_, também é possível encurtar a sintaxe em um _shortcode_. Basta declarar a propriedade _animation_ que ela agrupa todas as propriedades que vimos acima. As palavras mágicas e a ordem são as seguintes:

<pre class="lang-css">div {
   |name| |duration| |timing-function| |delay| |iteration-count| |direction| |play-state|;
}</pre>

O _bolo_ acima ficaria dessa maneira:

<pre class="lang-css">div { animation: animacaoBolada 5s ease 1s infinite alternate; }</pre>

Mais dois exemplos ([1][7] e [2][8]) em conjunto com a propriedade _transform_.

### Suporte

  * **IE** 10
  * **FF** 5
  * **Chrome** 4
  * **Safari** 4
  * **Opera** 12

<small>Fonte: <a href="http://caniuse.com/css-animation">Can I Use</a></small>

 [1]: http://www.smashingmagazine.com/2010/02/13/the-definitive-guide-to-styling-web-links/
 [2]: http://codepen.io/raphaelfabeni/full/Fkbej
 [3]: http://www.w3.org/TR/css3-transitions/#animatable-properties-
 [4]: http://matthewlein.com/ceaser/
 [5]: http://caniuse.com/css-transitions
 [6]: http://cdpn.io/eCGhx
 [7]: http://cdpn.io/qHkgJ
 [8]: http://cdpn.io/csubG