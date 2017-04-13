---
title: Analisando o código Stylus de um projeto
author: helderburato
type: post
date: 2016-11-18
url: /iniciando-com-o-pre-processador-stylus/
categories:
  - Código
  - CSS
  - Pré-processadores
tags:
  - front-end
  - pre-processadores
  - Stylus

---
## **O que é um pré-processador CSS?**

Como o nome ja diz, é uma linguagem que precisa ser pré-processada por um _parser_ para assim gerar o arquivo de extensão **.css** que será renderizado pelo browser. Atualmente há vários pré-processadores que você pode utilizar para facilitar a codificação e reaproveitamento de código, você pode estar utilizando SASS, LESS e Stylus que são os mais conhecidos no mercado. A diferença do <a href="http://stylus-lang.com/" target="_blank" rel="nofollow">Stylus</a> para os outros pré-processadores que estão sendo utilizados no mercado é que ele já é baseado em <a href="https://nodejs.org/en/" target="_blank" rel="nofollow">NodeJS</a> e não em ruby. Por conta disso não há necessidade de uma tecnologia intermediária em seu workflow para processá-lo.

## Vamos começar!

Tendo em mente que você ja conhece um pouco sobre pré-processadores e algumas de suas vantagens (variáveis, mixins, operadores, funções) vamos criar um projeto utilizando algumas dessas funcionalidades.

  1. Faça o download do <a href="https://nodejs.org/en/" target="_blank" rel="nofollow"><strong>NodeJS</strong></a> e efetue a instalação**;**
  2. Considerando que tenha o node rodando em seu sistema, instale o **Stylus **de forma global e execute o seguinte comando em seu terminal **npm install -g stylus**;
  3. Vamos criar a estrutura de diretórios de nosso projeto:

![][1]

Após ter seu diretório criado de acordo com a estrutura da imagem acima, você pode acessá-lo via terminal com o comando **cd /seu-diretorio** e na sequência executar o compilador stylus da seguinte maneira:

`stylus -w a`

### **Parâmetros**

  * -w (Observar alterações nos arquivos .styl e re-compilar gerando os arquivos resultantes .css);
  * -o (Após este parâmetro deve ser passado o caminho que deve ser salvo o arquivo compilado);

## Desmistificando a Estrutura

### ASSETS

Costumo sempre utilizar esta estrutura como raíz para os diretórios front-end principalmente pela facilidade em migrar para servidores independentes e também para evitar confusão entre o pessoal de back-end.

### **ASSETS/css**

Arquivos gerados após executar o pré-processador, gerando assim os arquivos com extensão **.css** prontos para utilização em seu código.

### ASSETS/stylus

Neste diretório fica toda a nossa organização de diretórios e arquivos .styl (Extensão utilizada pelo **Stylus**).

### ASSETS/stylus/base (Tipografia, reset, variáveis, cores)

O nome dos arquivos em si é bem descritivo, colors.styl para cores, variables.styl para variáveis reutilizáveis, typography.styl para definições de fonts e reset.styl (reset de elementos css).

### ASSETS/stylus/components (Pequenos componentes)

Utilizado para pequenos componentes como botões, formulários, modals e o que surgir de necessidade conforme o desenvolvimento de seu projeto.

### ASSETS/stylus/helpers (Utilitários para seus projetos)

Neste diretório geralmente são encontrados os seguintes arquivos: functions.styl, helpers.styl (classes utilitárias ex.: .pull-left, .show), mixins.styl (são blocos de códigos reutilizáveis semelhantes a funções).

### ASSETS/stylus/layout (Definições do seu layout)

Você vai encontrar os arquivos com definições de estilo com a cara do seu layout, como header, footer e grid.

### ASSETS/stylus/theme (Temas do projeto)

Definições de temas do projeto. Caso o projeto tenha mais de um tema, é uma boa prática para manter a organização e facilidade de manutenção no código.

### ASSETS/stylus/main.styl

Este é o arquivo primário que será lido pelo seu compilador, deve possuir todas as importações necessárias para gerar o arquivo .css resultante. Obs: Todos os arquivos all.styl servem para facilitar a importação no arquivo principal.

## Botando a mão na massa

Uma vez que você compreendeu a ideia dos diretórios criados e está com o compilador rodando corretamente, vamos ao código:

### assets/stylus/base

**all.styl (Import de todos os arquivos do diretório)**

<pre>// Import all from base
&lt;a title="Twitter profile for @import" href="http://twitter.com/import" target="_blank" rel="nofollow"&gt;@import&lt;/a&gt; ‘reset.styl’
&lt;a title="Twitter profile for @import" href="http://twitter.com/import" target="_blank" rel="nofollow"&gt;@import&lt;/a&gt; ‘colors.styl’
&lt;a title="Twitter profile for @import" href="http://twitter.com/import" target="_blank" rel="nofollow"&gt;@import&lt;/a&gt; ‘typography.styl’
&lt;a title="Twitter profile for @import" href="http://twitter.com/import" target="_blank" rel="nofollow"&gt;@import&lt;/a&gt; ‘variables.styl’</pre>

**colors.styl (Definições de cores do projeto)**

<pre class="lang-css">orange = #FF6347
gray-darker = #AAAAAA
gray-lighter = #EEEEEE
lighter = #FFF
darker = #444444
blue = #0080FF
blue-lighter = #1EC0FF
yellow = #F9C00C
red = #E71D36
green = #3AC569
</pre>

**reset.styl (Foi utilizado o normalize.css)**

<a href="https://necolas.github.io/normalize.css/" target="_blank" rel="nofollow">normalize.css</a>

**typography.styl (Definições de fonts)**

<pre class="lang-css">font-size-h1 = 40px
font-size-h2 = 34px
font-size-h3 = 28px
line-height-h1 = 55px
line-height-h2 = 46px
line-height-h3 = 38px
h1, h2, h3
 color darker
 font-weight bold
h1
 font-size font-size-h1
 line-height line-height-h1
 color darker
 margin-bottom 30px
h2
 font-size font-size-h2
 line-height line-height-h1
h3
 font-size font-size-h3
 line-height line-height-h3
</pre>

**variables.styl (Variáveis reutilizáveis do projeto)**

<pre>// Font Weights
light = 300
regular = 400
bold = 700</pre>

<pre>// Base Font
base-font-family = ‘Open Sans’, sans-serif
base-font-weight = light
base-font-size = 20px
base-line-height = 27px
form-label-font-size = base-font-size
form-field-font-size = 18px</pre>

<pre>// Buttons
btn-font-weight = bold
btn-default-border = gray-darker
btn-default-color = darker
btn-primary-color = lighter
btn-success-color = lighter
btn-danger-color = lighter
btn-warning-color = lighter
btn-info-color = lighter
</pre>

### assets/stylus/components

**all.styl**

<pre>// Import all from components
<a title="Twitter profile for @import" href="http://twitter.com/import" target="_blank" rel="nofollow">@import</a> ‘buttons.styl’
<a title="Twitter profile for @import" href="http://twitter.com/import" target="_blank" rel="nofollow">@import</a> ‘forms.styl’</pre>

**buttons.styl**

<pre>.btn
 font-weight bold
 padding 15px 27px
 border 1px solid transparent
 display inline-block
 cursor pointer
 border-radius(5px)
&-info
 &-primary
 &-success
 &-danger
 color lighter
&-default
 color darker
 border-color gray-darker
 background-color lighter
&-primary
 background-color blue
 border-color blue
&:hover
 &:focus
 background-color darken(blue, 20%)
 border-color darken(blue, 20%)
&-info
 background-color blue-lighter
 border-color blue-lighter
&:hover
 &:focus
 background-color darken(blue-lighter, 20%)
 border-color darken(blue-lighter, 20%)
&-warning
 background-color yellow
 border-color yellow
&:hover
 &:focus
 background-color darken(yellow, 20%)
 border-color darken(yellow, 20%)
&-success
 background-color green
 border-color green
&:hover
 &:focus
 background-color darken(green, 20%)
 border-color darken(green, 20%)
&-danger
 background-color red
 border-color red
&:hover
 &:focus
 background-color darken(red, 20%)
 border-color darken(red, 20%)</pre>

**forms.styl**

<pre>.form
 &__group
 margin-bottom 20px
&__label
 color darker
 font-size form-label-font-size
 font-weight bold
 margin-bottom 10px
&__field
 display block
 width 100%
 padding 6px 18px
 height 60px
 border 1px solid gray-darker
 color darker
 font-size form-field-font-size
 border-radius(3px)
&:hover
 &:focus
 border-color orange</pre>

**helpers.styl (Utilitários do projeto)**

**all.styl (Import de todos os arquivos do diretório)**

<pre>// Import all from helpers
<a title="Twitter profile for @import" href="http://twitter.com/import" target="_blank" rel="nofollow">@import</a> ‘functions.styl’
<a title="Twitter profile for @import" href="http://twitter.com/import" target="_blank" rel="nofollow">@import</a> ‘helpers.styl’
<a title="Twitter profile for @import" href="http://twitter.com/import" target="_blank" rel="nofollow">@import</a> ‘mixins.styl’</pre>

**functions.styl**

<pre>make-media-queries-breakpoints()
 for screen-width in screen-desktop-large screen-desktop screen-tablet screen-mobile
 <a title="Twitter profile for @media" href="http://twitter.com/media" target="_blank" rel="nofollow">@media</a> only screen and (max-width: screen-width)
 if (screen-width == screen-desktop-large)
 .container
 width container-desktop
 else if (screen-width == screen-desktop)
 .container
 width container-tablet
 else if (screen-width == screen-tablet)
 .container
 .columns
 width container-mobile !important
make-row()
 margin 0 (-(grid-gutter-width / 2))
calc-container-padding()
 padding 0 (grid-gutter-width / 2)
make-columns()
 for i in grid-columns..0
 .col-{i}
 width percentage(i, grid-columns)
.col-offset-{i}
 margin-left percentage(i, grid-columns)
percentage(index, divider)
 if index == 0
 0
 else
 unit((index * 100) / divider, “%”)</pre>

**helpers.styl (Classes utilitárias para uso no html)**

<pre>.pull-left
 float left
.pull-right
 float right
.show
 display block
.hide
 display none
.text-center
 text-align center
.text-left
 text-align left
.text-right
 text-align right
.absolute
 position absolute
.relative
 position relative
.in-block
 display inline-block
.center-block
 margin 0 auto
 display block
.img-responsive
 max-width 100%
.clearfix
 &:before
 &:after
 content “ “
 display table
&:after
 clear both</pre>

**mixins.styl**

<pre>vendor(prop, args)
 -webkit-{prop} args
 -moz-{prop} args
 {prop} args
border-radius()
 vendor(‘border-radius’, arguments)
box-shadow()
 vendor(‘box-shadow’, arguments)
opacity(n)
 opacity n
 filter unquote(‘progid:DXImageTransform.Microsoft.Alpha(Opacity=’ + round(n * 100) + ‘)’)</pre>

### assets/stylus/layout

**header.styl**

<pre class="lang-css">.header
 background-color orange
 padding 30px 0
.header__img
 max-width 150px</pre>

**footer.styl**

<pre class="lang-css">.footer
 padding 40px 0
 background-color darker
 color lighter
& a
 color lighter
 &:hover
 color orange
& p
 font-size 16px
 line-height 22px
 margin 0 0 10px 0
& .fa
 color #E84545
 margin 0 2px
& img
 max-width 150px
 &:hover
 opacity(0.6)</pre>

**grid.styl (Sistema de grids utilizado no projeto)**

<pre class="lang-css">// Media Queries Breakpoints
screen-desktop-large = 1200px
screen-desktop = 992px
screen-tablet = 768px
screen-mobile = 480px
// Grid System
grid-columns = 12
grid-gutter-width = 30px
// Container Sizes
container-desktop-large = 1170px
container-desktop = 940px
container-tablet = 720px
container-mobile = 100%
.container
 width container-desktop-large
 calc-container-padding()
 margin 0 auto
.row
.columns
 box-sizing border-box
.row
 make-row()
&:before
 &:after
 content “ “
 display table
&:after
 clear both
.columns
 <a title="Twitter profile for @extend" href="http://twitter.com/extend" target="_blank" rel="nofollow">@extend</a> .relative
 <a title="Twitter profile for @extend" href="http://twitter.com/extend" target="_blank" rel="nofollow">@extend</a> .pull-left
 padding 0 (grid-gutter-width / 2)
make-media-queries-breakpoints()
make-columns()</pre>

**login.styl**

<pre class="lang-css">.content
 padding-top 60px
 padding-bottom 60px
 min-height 470px
&__login
 padding 30px
 border-radius(3px)
 background-color gray-lighter
 box-shadow(0 0 5px rgba(0,0,0,0.09))
 max-width 530px
 background-color darker
& .form__label
 & h3
 color lighter
& h3
 margin-bottom 20px</pre>

**assets/stylus/themes (Temas do projeto admin, padrão e quais forem necessários)**

**default.styl (Tema padrão)**

<pre class="lang-css">*
 vendor(‘box-sizing’, border-box)
body
 font-family base-font-family
 font-weight base-font-weight
 font-size base-font-size
 line-height base-line-height
 background-color lighter
a
 text-decoration none</pre>

### assets/stylus/main.styl (Arquivo principal)

Neste arquivo você deve efetuar todas as importações necessárias do seu projeto. Em nosso tutorial o arquivo ficou assim:

<pre><a title="Twitter profile for @charset" href="http://twitter.com/charset" target="_blank" rel="nofollow">@charset</a> “UTF-8”
<a title="Twitter profile for @import" href="http://twitter.com/import" target="_blank" rel="nofollow">@import</a> ‘base/all.styl’
<a title="Twitter profile for @import" href="http://twitter.com/import" target="_blank" rel="nofollow">@import</a> ‘helpers/all.styl’
<a title="Twitter profile for @import" href="http://twitter.com/import" target="_blank" rel="nofollow">@import</a> ‘components/all.styl’
// Imports from layout
<a title="Twitter profile for @import" href="http://twitter.com/import" target="_blank" rel="nofollow">@import</a> ‘layout/grid.styl’
<a title="Twitter profile for @import" href="http://twitter.com/import" target="_blank" rel="nofollow">@import</a> ‘layout/header.styl’
<a title="Twitter profile for @import" href="http://twitter.com/import" target="_blank" rel="nofollow">@import</a> ‘layout/footer.styl’
<a title="Twitter profile for @import" href="http://twitter.com/import" target="_blank" rel="nofollow">@import</a> ‘layout/login.styl’
// Import themes
<a title="Twitter profile for @import" href="http://twitter.com/import" target="_blank" rel="nofollow">@import</a> ‘themes/default.styl’</pre>

Por fim, crie um arquivo **index.html** na raíz de seu projeto com o seguinte código:

<pre>&lt;!DOCTYPE html&gt;
&lt;html lang=”en”&gt;
&lt;head&gt;
 &lt;meta charset=”UTF-8"&gt;
 &lt;title&gt;Iniciando com Stylus&lt;/title&gt;
&lt;link href=”<a href="https://fonts.googleapis.com/css?family=Open+Sans:300,400,700" target="_blank" rel="nofollow">https://fonts.googleapis.com/css?family=Open+Sans:300,400,700</a>" rel=”stylesheet”&gt;
&lt;link rel=”stylesheet” href=”<a href="https://maxcdn.bootstrapcdn.com/font-awesome/4.5.0/css/font-awesome.min.css" target="_blank" rel="nofollow">https://maxcdn.bootstrapcdn.com/font-awesome/4.5.0/css/font-awesome.min.css</a>"&gt;
&lt;link rel=”stylesheet” href=”assets/css/main.css”&gt;
&lt;/head&gt;
&lt;body&gt;
 &lt;header class=”header”&gt;
 &lt;div class=”container”&gt;
 &lt;img class=”header__img img-responsive center-block” src=”assets/images/stylus-logo.png” alt=”” /&gt;
 &lt;/div&gt;
 &lt;/header&gt;
&lt;div class=”content container”&gt;
 &lt;h1 class=”text-center”&gt;Iniciando com Stylus&lt;/h1&gt;
&lt;div class=”content__login center-block”&gt;
 &lt;h3 class=”text-center”&gt;Acesse sua conta&lt;/h3&gt;
&lt;form action=”#”&gt;
 &lt;div class=”form__group”&gt;
 &lt;label for=”name” class=”form__label show”&gt;Nome&lt;/label&gt;
&lt;input type=”text” name=”name” id=”name” class=”form__field”&gt;
 &lt;/div&gt;
 &lt;div class=”form__group”&gt;
 &lt;label for=”email” class=”form__label show”&gt;Email&lt;/label&gt;
&lt;input type=”text” name=”email” id=”email” class=”form__field”&gt;
 &lt;/div&gt;
 &lt;div class=”submit text-right”&gt;
 &lt;button type=”submit” class=”btn btn-success”&gt;
 Submit
 &lt;/button&gt;
 &lt;/div&gt;
 &lt;/form&gt;
 &lt;/div&gt;
 &lt;/div&gt;
&lt;footer class=”footer text-center”&gt;
 &lt;div class=”container”&gt;
 &lt;p&gt;
 Feito com &lt;i class=”fa fa-heart”&gt;&lt;/i&gt; por &lt;a href=”<a href="http://helderburato.com/" target="_blank" rel="nofollow">http://helderburato.com/</a>”&gt;Helder Burato Berto&lt;/a&gt;
 &lt;/p&gt;
&lt;a class=”in-block” href=”<a href="http://uilab.com.br/" target="_blank" rel="nofollow">http://uilab.com.br/</a>"&gt;
 &lt;img class=”img-responsive” src=”assets/images/uilab-logo.png” alt=””&gt;
 &lt;/a&gt;
 &lt;/div&gt;
 &lt;/footer&gt;
&lt;/body&gt;
&lt;/html&gt;</pre>

## Compreendendo a linguagem Stylus

Você pode observar que foram utilizados algumas particularidades da linguagem, que não são comuns para quem está acostumado apenas com CSS, sendo elas: **&:** Usado para referenciar parcialmente um elemento citado anteriormente, por exemplo:

<pre>.foo
 color #000
 & a
 color #fff</pre>

Será compilado para:

<pre>.foo {
 color: #000;
}
.foo a {
 color: #fff;
}</pre>

Você percebe o quanto isso é poderoso e tem utilidade?

**border-radius():** Mixin definido para ser reutilizado e com possibilidade de uso com parâmetros.

Exemplo de uso:

<pre>.foo
 border-radius(5px)</pre>

Será compilado para:

<pre>.foo {
 border-radius: 5px;
 -webkit-border-radius: 5px;
 -moz-border-radius: 5px;
}</pre>

Observe que foi gerado o código ja com os prefixos para outros browsers, facilitando na escrita.

**IF** e **FOR:** Vamos descrever o uso de IF e for com uma função que foi utilizado no tutorial chamada **make-media-queries-breakpoints()**.

<pre>make-media-queries-breakpoints()
 for screen-width in screen-desktop-large screen-desktop screen-tablet screen-mobile
 <a title="Twitter profile for @media" href="http://twitter.com/media" target="_blank" rel="nofollow">@media</a> only screen and (max-width: screen-width)
 if (screen-width == screen-desktop-large)
 .container
 width container-desktop
 else if (screen-width == screen-desktop)
 .container
 width container-tablet
 else if (screen-width == screen-tablet)
 .container
 .columns
 width container-mobile !important</pre>

Nós utilizamos o FOR para percorrer as variáveis declaradas posteriormente e IF para modificar a width de nosso container principal de acordo com a media queria utilizada.

O código acima após a compilação:

<pre><a title="Twitter profile for @media" href="http://twitter.com/media" target="_blank" rel="nofollow">@media</a> only screen and (max-width: 1200px) {
 .container {
 width: 1170px;
 }
}
<a title="Twitter profile for @media" href="http://twitter.com/media" target="_blank" rel="nofollow">@media</a> only screen and (max-width: 992px) {
 .container {
 width: 720px;
 }
}
<a title="Twitter profile for @media" href="http://twitter.com/media" target="_blank" rel="nofollow">@media</a> only screen and (max-width: 768px) {
 .container,
 .columns {
 width: 100%;
 }
}</pre>

### Sintaxe

Você provavelmente deve ter percebido que com Stylus não temos a necessidade do uso de **{}** e**;** nas declarações CSS, isso em prática ajuda muito na produtividade.

### Variáveis

Você pode declarar variáveis sem o uso de **$** mas caso você já utilizou outros pré;-processadores, fica a seu crité;rio o uso dele ou não.

Bom espero que tenha conseguido compartilhar um pouco do que é; esta grande ferramenta e que lhe seja útil na hora de pensar em usar um pré;-processador.

Um grande abraço, obrigado!

  * Link do Projeto: <a href="https://helderburato.github.io/iniciando-stylus/" target="_blank" rel="nofollow">https://helderburato.github.io/iniciando-stylus/</a>
  * Git do Projeto: <a href="https://github.com/helderburato/iniciando-stylus" target="_blank" rel="nofollow">https://github.com/helderburato/iniciando-stylus</a>
  * Layout: <a href="https://github.com/helderburato/iniciando-stylus/tree/master/sketch" target="_blank" rel="nofollow">https://github.com/helderburato/iniciando-stylus/tree/master/sketch</a>

 [1]: http://tableless.com.br/uploads/2016/10/director.png