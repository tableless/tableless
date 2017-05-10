---
title: 'SASS: Mixin ou Placeholder?'
author: Raphael Fabeni
type: post
date: 2014-03-16
excerpt: Você utiliza pré-processadores de CSS? Sabe a diferença entre um mixin e um placeholder? Entenda a diferença entre os dois e saiba quando utilizá-los.
url: /sass-mixin-ou-placeholder/
dsq_thread_id: 2429033279
categories:
  - Artigos
  - CSS
  - Pré-processadores
  - SASS
  - Traduções
tags:
  - CSS
  - CSS3
  - pré-processadores
  - SASS

---
Se é um tema que sempre vejo a respeito da utilização ou não, é sobre o uso de pré processadores CSS. Alguns _devs_ que costumo seguir e ler os artigos, e que pra mim são algumas das nossas referências, apontam as suas considerações sobre o tema. O Miller Medeiros, em um [post][1] mostra alguns pontos negativos na utilização de pré processadores. O Jean Carlos Emer em um outro [post][2] mostra as reais vantagens de se utilizar um pré-processador. O Diego Eis, em um outro [post][3] faz uma conclusão muito boa sobre a utilização ou não:

> Pré processadores podem ajudar como também podem maltratar bastante. Basta um escorregão para que seu projeto vire um inferno. &#8211; Diego Eis 

A utilização ou não de um pré processador fica a seu critério mas, se você já utiliza nos seus projetos ou está pensando em usar, você sabe o que são um **placeholder** e um **mixin**? Se sim, sabe qual a principal diferença entre eles e quando usar um ou outro? Navegando um dia pela internet, achei um [artigo][4] do [Hugo Giraudel][5], um dev front-end francês, no [SitePoint][6] que trata exatamente sobre esse assunto.

—

Quando comecei a trabalhar com SASS cerca de um ano e meio atrás, uma coisa que me levou tempo para entender foi a diferença entre _[incluir um mixin][7]_ e _[estender um placeholder][8]_. Na verdade, até mesmo a noção de _placeholder_ era uma espécie de magia negra vodu naquela época.

Se você estiver em uma situação semelhante, não se preocupe, porque eu vou tentar iluminar o caminho. Hoje vamos aprender para que exatamente serve um _mixin_, e quando usar um _placeholder do SASS_. Você vai entender que ambos tem diferentes finalidades e não devem ser confundidas.

_Nota: Enquanto pretendo falar sobre SASS, esse artigo pode ser aplicado a qualquer outro pré-processador CSS, seja Stylus, LESS, ou outro que você venha a usar. Essas tecnologias geralmente fazem a mesma coisa, portanto fique a vontade para adaptar o conteúdo deste artigo para a ferramenta de sua escolha_.

Primeiro devemos fazer um breve resumo sobre o que estamos falando quando nos referimos aos **placeholder e mixins do SASS**, então vamos fazer isso já.

## Entendendo o mixin

Um mixin é uma diretiva que permite que você defina várias regras com diversos argumentos. Pense nisso como uma função que irá retornar conteúdo CSS ao invés de um valor. Aqui está a definição de _mixin_ da [referência do SASS][9]:

<blockquote cite="http://sass-lang.com/documentation/file.SASS_REFERENCE.html#mixin-content">
  <p>
    Mixins permitem definir estilos que podem ser reutilizados em toda a folha de estilo, sem a necessidade de recorrer a classes não semânticas como <i>.float-left</i>. Mixins podem também conter regras completas de CSS e quaisquer outras coisas permitidas em um documento SASS. Eles podem até mesmo possuírem argumentos que lhe permitem produzir uma ampla variedade de estilos com poucos mixins.
  </p>
</blockquote>

Agora que cobrimos a terminologia, vamos dizer que você encontra algumas declarações que são repetidas várias vezes ao longo da sua folha de estilos. Você que está familiarizado com o conceito de DRY ([Don&#8217;t Repeat Yourself][10]), sabe que a repetição de código é ruim. Para corrigir isso, você pode escrever um mixin para todas aquelas declarações repetidas:

<pre class="lang-scss">@mixin center() {
    display: block;
    margin-left: auto;
    margin-right: auto;
}

.container {
    @include center();
    /* Outros estilos aqui... */
}

/* Outros estilos... */

.image-cover {
    @include center;
}
</pre>

_Nota: Se você não passar um argumento para um mixin, você pode omitir os parênteses. Na verdade, você pode até omiti-los na definição do `@mixin`_.

Com este mixin recém-criado, você não precisa repetir aquelas três linhas de código cada vez que precisar centralizar um elemento; você simplesmente inclui o mixin. Muito prático, não é?!

Algumas vezes você vai querer um mixin para construir o que você chamaria de _shorthand_ para algumas propriedades. Por exemplo, largura e altura. Você não está cansado de escrever as duas linhas várias e várias vezes? Especialmente quando ambas tem o mesmo valor? Bem, vamos lidar com isso usando um mixin!

<pre class="lang-scss">@mixin size($width, $height: $width) {
    width: $width;
    height: $height;
}
</pre>

Muito simples, não é? Note como deixamos o parâmetro `$height` ser opcional e, por padrão assumir o mesmo valor do parâmetro `$width` na assinatura do mixin. Agora, sempre que você precisar definir as dimensões para um elemento, você pode simplesmente fazer isso:

<pre class="lang-scss">.icon {
    @include size(32px);
}

.cover {
    @include size(100%, 10em);
}
</pre>

_Nota: Um outro bom exemplo de mixin seria [este aqui][11] que eu fiz para evitar de escrever as posições `top`, `left`, `right` e `bottom` toda vez que quiser utilizar um sistema de posicionamento diferente do estático._

## Conhecendo seu Placeholder

Placeholders são um tipo de coisa estranha. Eles são classes que não são retornadas quando o seu SCSS é compilado. Você deve então pensar: _&#8220;Qual é o sentido disso?&#8221;_. Na verdade, o ponto seria minímo senão fosse a expressão `@extend`. Mas vamos por partes. Essa é a forma que você escreve um placeholder:

<pre class="lang-scss">%center {
    display: block;
    margin-left: auto;
    margin-right: auto;
}
</pre>

_Nota do editor: Como um placeholder, um mixin é igualmente inútil, a menos que seja referenciado, assim essa seção não está dizendo que eles são diferentes nesse aspecto, mas apenas esclarecendo que mesmo que se pareça similar com um bloco de declaração CSS, não será gerado por conta própria._

Basicamente você escreve exatamente como uma classe `CSS` exceto pelo símbolo % ao invés do ponto. Além disso, segue as mesmas [regras de nomenclatura][12] das classes.

Agora, se você tentar compilar seu SCSS, você não vai ver esse pedaço de código no arquivo gerado. Como eu disse: **placeholders não são compilados**.

Então, por agora, esse placeholder é totalmente inútil. Você não consegue fazer qualquer uso dele a não ser que você veja o `@extend`. Um `@extend` tem como objetivo herdar as propriedades de um seletor CSS / SCSS placeholder. Aqui como usá-lo:

<pre class="lang-scss">.container {
  @extend %center;
}
</pre>

Ao fazer isso, o arquivo SASS vai pegar o conteúdo do placeholder `%center` e aplicá-lo no `.container` (mesmo que isso não aconteça exatamente assim &#8211; mas isso não é importante agora). Como eu disse, você também pode _estender_ seletores CSS já existentes (além de placeholders SCSS) dessa maneira:

<pre class="lang-scss">.table-zebra {
  @extend .table;

  tr:nth-of-type(even) {
    background: rgba(0,0,0,.5);
  }
}
</pre>

Esse é um caso muito comum para o uso do `@extend`. Nesse caso, pedimos para a classe `.table-zebra` se comportar exatamente como a classe `.table` e então adicionamos as regras específicas da classe `.table-zebra`. _Estender_ seletores é bastante conveniente quando você desenvolve seu site ou aplicação em componentes modulares.

## Qual utilizar?

Então, a pergunta permanece: o que você deve usar? Bem, como tudo em nossa área: **depende**. Depende do contexto e, em uma outra análise, do que você está querendo fazer.

O melhor conselho seria: se você precisa de variáveis, utilize o mixin. Caso contrário, use o placeholder. Há duas razões para isso:

  * Primeiro, você não pode usar variáveis em um placeholder. Na verdade, até pode, mas você não consegue _passar_ uma variável em um placeholder para gerar um conteúdo específico de CSS, como você faria em um mixin.
  * Segundo, a forma como o SASS lida com os mixins, os torna muito incovenientes quando você os utiliza sem variáveis contextuais. Simplificando: o SASS vai duplicar a saída de um mixin toda vez que você o utilizá-lo, resultando não apenas em CSS duplicado, mas também em uma folha de estilos maior.

Considere o primeiro exemplo desse artigo:

<pre class="lang-scss">@mixin center {
  display: block;
  margin-left: auto;
  margin-right: auto;
}

.container {
  @include center;
}

.image-cover {
  @include center;
}
</pre>

O CSS compilado seria esse:

<pre class="lang-css">.container {
  display: block;
  margin-left: auto;
  margin-right: auto;
}

.image-cover {
  display: block;
  margin-left: auto;
  margin-right: auto;
}
</pre>

Observou o CSS duplicado? Ele não é tão prejudicial se forem apenas três linhas duplicadas, mas se você tiver muitos mixins que são usados várias vezes em um projeto, essas três linhas podem facilmente se tornarem 300. E se reformularmos nosso exemplo, só que dessa vez utilizando o placeholder?

<pre class="lang-scss">%center {
  display: block;
  margin-left: auto;
  margin-right: auto;
}

.container {
  @extend %center;
}

.image-cover {
  @extend %center;
}
</pre>

Agora, esse é o CSS gerado:

<pre class="lang-css">.container, .image-cover {
  display: block;
  margin-left: auto;
  margin-right: auto;
}
</pre>

Muito melhor! A compilação leva vantagem [agrupando seletores][13], sem nenhum estilo repetido. Assim, sempre que você quiser evitar a escrever as mesmas propriedades diversas vezes, sabendo que elas não mudarão, é uma boa idéia _estender_ um placeholder. Isso resultará em um código CSS compilado muito mais limpo.

Por outro lado, se você precisa escrever as mesmas propriedades em vários lugares mas com valores diferentes (tamanho, cores, etc), um mixin é o melhor caminho a seguir. Agora se você possui ambos, um grupo de valores fixos e outro de valores variáveis, você deve tentar usar uma combinação dos dois.

<pre class="lang-scss">%center {
  margin-left: auto;
  margin-right: auto;
  display: block;
}

@mixin skin($color, $size) {
  @extend %center;
  background: $color;
  height: $size;
}

a { @include skin(pink, 10em) }
b { @include skin(blue, 90px) }
</pre>

Neste caso, o mixin está _estendendo_ o placeholder para os valores fixos em vez de jogá-los diretamente em seu corpo. Isso gera um CSS mais limpo:

<pre class="lang-css">a, b {
  margin-left: auto;
  margin-right: auto;
  display: block;
}

a {
  background: pink;
  height: 10em;
}

b {
  background: blue;
  height: 90px;
}
</pre>

## Conclusão

É isso. Espero ter deixado claro não só o que são mixins e placeholders, mas também quando você deve usá-los e qual os efeitos sobre o CSS compilado.

Se você tiver alguma coisa a acrescentar sobre suas experiências com essas _features_ dos pré-processadores de CSS, sinta-se livre para compartilhar nos comentários.

—

Texto traduzido e adaptado do [Se é um tema que sempre vejo a respeito da utilização ou não, é sobre o uso de pré processadores CSS. Alguns _devs_ que costumo seguir e ler os artigos, e que pra mim são algumas das nossas referências, apontam as suas considerações sobre o tema. O Miller Medeiros, em um [post][1] mostra alguns pontos negativos na utilização de pré processadores. O Jean Carlos Emer em um outro [post][2] mostra as reais vantagens de se utilizar um pré-processador. O Diego Eis, em um outro [post][3] faz uma conclusão muito boa sobre a utilização ou não:

> Pré processadores podem ajudar como também podem maltratar bastante. Basta um escorregão para que seu projeto vire um inferno. &#8211; Diego Eis 

A utilização ou não de um pré processador fica a seu critério mas, se você já utiliza nos seus projetos ou está pensando em usar, você sabe o que são um **placeholder** e um **mixin**? Se sim, sabe qual a principal diferença entre eles e quando usar um ou outro? Navegando um dia pela internet, achei um [artigo][4] do [Hugo Giraudel][5], um dev front-end francês, no [SitePoint][6] que trata exatamente sobre esse assunto.

—

Quando comecei a trabalhar com SASS cerca de um ano e meio atrás, uma coisa que me levou tempo para entender foi a diferença entre _[incluir um mixin][7]_ e _[estender um placeholder][8]_. Na verdade, até mesmo a noção de _placeholder_ era uma espécie de magia negra vodu naquela época.

Se você estiver em uma situação semelhante, não se preocupe, porque eu vou tentar iluminar o caminho. Hoje vamos aprender para que exatamente serve um _mixin_, e quando usar um _placeholder do SASS_. Você vai entender que ambos tem diferentes finalidades e não devem ser confundidas.

_Nota: Enquanto pretendo falar sobre SASS, esse artigo pode ser aplicado a qualquer outro pré-processador CSS, seja Stylus, LESS, ou outro que você venha a usar. Essas tecnologias geralmente fazem a mesma coisa, portanto fique a vontade para adaptar o conteúdo deste artigo para a ferramenta de sua escolha_.

Primeiro devemos fazer um breve resumo sobre o que estamos falando quando nos referimos aos **placeholder e mixins do SASS**, então vamos fazer isso já.

## Entendendo o mixin

Um mixin é uma diretiva que permite que você defina várias regras com diversos argumentos. Pense nisso como uma função que irá retornar conteúdo CSS ao invés de um valor. Aqui está a definição de _mixin_ da [referência do SASS][9]:

<blockquote cite="http://sass-lang.com/documentation/file.SASS_REFERENCE.html#mixin-content">
  <p>
    Mixins permitem definir estilos que podem ser reutilizados em toda a folha de estilo, sem a necessidade de recorrer a classes não semânticas como <i>.float-left</i>. Mixins podem também conter regras completas de CSS e quaisquer outras coisas permitidas em um documento SASS. Eles podem até mesmo possuírem argumentos que lhe permitem produzir uma ampla variedade de estilos com poucos mixins.
  </p>
</blockquote>

Agora que cobrimos a terminologia, vamos dizer que você encontra algumas declarações que são repetidas várias vezes ao longo da sua folha de estilos. Você que está familiarizado com o conceito de DRY ([Don&#8217;t Repeat Yourself][10]), sabe que a repetição de código é ruim. Para corrigir isso, você pode escrever um mixin para todas aquelas declarações repetidas:

<pre class="lang-scss">@mixin center() {
    display: block;
    margin-left: auto;
    margin-right: auto;
}

.container {
    @include center();
    /* Outros estilos aqui... */
}

/* Outros estilos... */

.image-cover {
    @include center;
}
</pre>

_Nota: Se você não passar um argumento para um mixin, você pode omitir os parênteses. Na verdade, você pode até omiti-los na definição do `@mixin`_.

Com este mixin recém-criado, você não precisa repetir aquelas três linhas de código cada vez que precisar centralizar um elemento; você simplesmente inclui o mixin. Muito prático, não é?!

Algumas vezes você vai querer um mixin para construir o que você chamaria de _shorthand_ para algumas propriedades. Por exemplo, largura e altura. Você não está cansado de escrever as duas linhas várias e várias vezes? Especialmente quando ambas tem o mesmo valor? Bem, vamos lidar com isso usando um mixin!

<pre class="lang-scss">@mixin size($width, $height: $width) {
    width: $width;
    height: $height;
}
</pre>

Muito simples, não é? Note como deixamos o parâmetro `$height` ser opcional e, por padrão assumir o mesmo valor do parâmetro `$width` na assinatura do mixin. Agora, sempre que você precisar definir as dimensões para um elemento, você pode simplesmente fazer isso:

<pre class="lang-scss">.icon {
    @include size(32px);
}

.cover {
    @include size(100%, 10em);
}
</pre>

_Nota: Um outro bom exemplo de mixin seria [este aqui][11] que eu fiz para evitar de escrever as posições `top`, `left`, `right` e `bottom` toda vez que quiser utilizar um sistema de posicionamento diferente do estático._

## Conhecendo seu Placeholder

Placeholders são um tipo de coisa estranha. Eles são classes que não são retornadas quando o seu SCSS é compilado. Você deve então pensar: _&#8220;Qual é o sentido disso?&#8221;_. Na verdade, o ponto seria minímo senão fosse a expressão `@extend`. Mas vamos por partes. Essa é a forma que você escreve um placeholder:

<pre class="lang-scss">%center {
    display: block;
    margin-left: auto;
    margin-right: auto;
}
</pre>

_Nota do editor: Como um placeholder, um mixin é igualmente inútil, a menos que seja referenciado, assim essa seção não está dizendo que eles são diferentes nesse aspecto, mas apenas esclarecendo que mesmo que se pareça similar com um bloco de declaração CSS, não será gerado por conta própria._

Basicamente você escreve exatamente como uma classe `CSS` exceto pelo símbolo % ao invés do ponto. Além disso, segue as mesmas [regras de nomenclatura][12] das classes.

Agora, se você tentar compilar seu SCSS, você não vai ver esse pedaço de código no arquivo gerado. Como eu disse: **placeholders não são compilados**.

Então, por agora, esse placeholder é totalmente inútil. Você não consegue fazer qualquer uso dele a não ser que você veja o `@extend`. Um `@extend` tem como objetivo herdar as propriedades de um seletor CSS / SCSS placeholder. Aqui como usá-lo:

<pre class="lang-scss">.container {
  @extend %center;
}
</pre>

Ao fazer isso, o arquivo SASS vai pegar o conteúdo do placeholder `%center` e aplicá-lo no `.container` (mesmo que isso não aconteça exatamente assim &#8211; mas isso não é importante agora). Como eu disse, você também pode _estender_ seletores CSS já existentes (além de placeholders SCSS) dessa maneira:

<pre class="lang-scss">.table-zebra {
  @extend .table;

  tr:nth-of-type(even) {
    background: rgba(0,0,0,.5);
  }
}
</pre>

Esse é um caso muito comum para o uso do `@extend`. Nesse caso, pedimos para a classe `.table-zebra` se comportar exatamente como a classe `.table` e então adicionamos as regras específicas da classe `.table-zebra`. _Estender_ seletores é bastante conveniente quando você desenvolve seu site ou aplicação em componentes modulares.

## Qual utilizar?

Então, a pergunta permanece: o que você deve usar? Bem, como tudo em nossa área: **depende**. Depende do contexto e, em uma outra análise, do que você está querendo fazer.

O melhor conselho seria: se você precisa de variáveis, utilize o mixin. Caso contrário, use o placeholder. Há duas razões para isso:

  * Primeiro, você não pode usar variáveis em um placeholder. Na verdade, até pode, mas você não consegue _passar_ uma variável em um placeholder para gerar um conteúdo específico de CSS, como você faria em um mixin.
  * Segundo, a forma como o SASS lida com os mixins, os torna muito incovenientes quando você os utiliza sem variáveis contextuais. Simplificando: o SASS vai duplicar a saída de um mixin toda vez que você o utilizá-lo, resultando não apenas em CSS duplicado, mas também em uma folha de estilos maior.

Considere o primeiro exemplo desse artigo:

<pre class="lang-scss">@mixin center {
  display: block;
  margin-left: auto;
  margin-right: auto;
}

.container {
  @include center;
}

.image-cover {
  @include center;
}
</pre>

O CSS compilado seria esse:

<pre class="lang-css">.container {
  display: block;
  margin-left: auto;
  margin-right: auto;
}

.image-cover {
  display: block;
  margin-left: auto;
  margin-right: auto;
}
</pre>

Observou o CSS duplicado? Ele não é tão prejudicial se forem apenas três linhas duplicadas, mas se você tiver muitos mixins que são usados várias vezes em um projeto, essas três linhas podem facilmente se tornarem 300. E se reformularmos nosso exemplo, só que dessa vez utilizando o placeholder?

<pre class="lang-scss">%center {
  display: block;
  margin-left: auto;
  margin-right: auto;
}

.container {
  @extend %center;
}

.image-cover {
  @extend %center;
}
</pre>

Agora, esse é o CSS gerado:

<pre class="lang-css">.container, .image-cover {
  display: block;
  margin-left: auto;
  margin-right: auto;
}
</pre>

Muito melhor! A compilação leva vantagem [agrupando seletores][13], sem nenhum estilo repetido. Assim, sempre que você quiser evitar a escrever as mesmas propriedades diversas vezes, sabendo que elas não mudarão, é uma boa idéia _estender_ um placeholder. Isso resultará em um código CSS compilado muito mais limpo.

Por outro lado, se você precisa escrever as mesmas propriedades em vários lugares mas com valores diferentes (tamanho, cores, etc), um mixin é o melhor caminho a seguir. Agora se você possui ambos, um grupo de valores fixos e outro de valores variáveis, você deve tentar usar uma combinação dos dois.

<pre class="lang-scss">%center {
  margin-left: auto;
  margin-right: auto;
  display: block;
}

@mixin skin($color, $size) {
  @extend %center;
  background: $color;
  height: $size;
}

a { @include skin(pink, 10em) }
b { @include skin(blue, 90px) }
</pre>

Neste caso, o mixin está _estendendo_ o placeholder para os valores fixos em vez de jogá-los diretamente em seu corpo. Isso gera um CSS mais limpo:

<pre class="lang-css">a, b {
  margin-left: auto;
  margin-right: auto;
  display: block;
}

a {
  background: pink;
  height: 10em;
}

b {
  background: blue;
  height: 90px;
}
</pre>

## Conclusão

É isso. Espero ter deixado claro não só o que são mixins e placeholders, mas também quando você deve usá-los e qual os efeitos sobre o CSS compilado.

Se você tiver alguma coisa a acrescentar sobre suas experiências com essas _features_ dos pré-processadores de CSS, sinta-se livre para compartilhar nos comentários.

—

Texto traduzido e adaptado do][4] escrito pelo [Hugo Giraudel][14] em 30 de janeiro de 2014.

Tradução autorizada pelo [SitePoint][15].

Qualquer erro ou sugestão de melhoria na tradução, é bem vinda! 🙂

 [1]: http://blog.millermedeiros.com/the-problem-with-css-pre-processors/
 [2]: http://tableless.com.br/css-steroids/ "CSS on steroids"
 [3]: http://tableless.com.br/pre-processadores-usar-ou-nao-usar/ "Pré processadores: usar ou não usar?"
 [4]: http://www.sitepoint.com/sass-mixin-placeholder/
 [5]: https://twitter.com/HugoGiraudel "Perfil do twitter do desenvolvedor Hugo Giraudel"
 [6]: http://www.sitepoint.com/ "Link do website SitePoint"
 [7]: http://sass-lang.com/documentation/file.SASS_REFERENCE.html#mixins
 [8]: http://sass-lang.com/documentation/file.SASS_REFERENCE.html#placeholders
 [9]: http://sass-lang.com/documentation/file.SASS_REFERENCE.html#mixin-content
 [10]: http://en.wikipedia.org/wiki/Don't_repeat_yourself
 [11]: http://hugogiraudel.com/2013/08/05/offsets-sass-mixin/
 [12]: http://www.w3.org/TR/html401/types.html#type-cdata
 [13]: http://reference.sitepoint.com/css/selectorgrouping
 [14]: https://twitter.com/HugoGiraudel "Perfil do twitter"
 [15]: http://www.sitepoint.com/