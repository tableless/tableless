---
title: Entendendo Sistemas de Grid CSS do Zero
authors: Tamiris Bonicenha
type: post
date: 2015-08-11
excerpt: A matemática por trás dos sistemas de grid.
url: /entendendo-sistemas-de-grid-css-do-zero/
categories:
  - Artigos
  - CSS
  - Responsive Web Design (RWD)
  - Traduções
tags:
  - CSS
  - design responsivo
  - grid

---
Ao longo dos últimos anos, sistemas de grid CSS têm crescido muito em popularidade, rapidamente sendo considerada uma boa prática para a criação de layout estruturais. Como resultado, não houve falta de _frameworks_ surgindo, oferecendo seus próprios sistemas de grid e tentando conquistar espaço.

Se você é do tipo curioso, como eu, pode estar se perguntando o que exatamente sistemas de grid podem oferecer? Como eles funcionam? E como você pode criar o seu próprio? Essas são apenas algumas das perguntas que eu vou tentar responder e como explorar os vários conceitos em jogo enquanto construímos juntos um sistema de grid básico a partir do zero.

## O que é um Sistema de Grid?

No caso de você ser um novato em sistemas de grid CSS, vamos começar com uma rápida definição. Em termos básicos, um sistema de grid é uma estrutura que permite o conteúdo ser empilhado verticalmente e horizontalmente de uma forma consistente e facilmente gerenciável. Além disso, o código de um sistema de grid é um “_project-agnostic_”, dando-lhe um elevado grau de portabilidade, de modo que, possa ser adotado em novos projetos.

## Os Benefícios

  * **Eles aumentam a produtividade** fornecendo simples e previsíveis estruturas de layout para design de HTML. A estrutura de uma página pode ser formulada rapidamente sem perder tempo em adivinhar qual sua precisão ou compatibilidade _cross-browser_.
  * **Eles são versáteis** na forma em como os layouts podem ser construídos, sendo adaptados em variadas combinações de linhas e colunas. Eles ainda suportam grids aninhados para em casos de usos complexos. Não importa a necessidade do layout, um sistema de grid é quase certamente bem adaptado.
  * **Eles são ideais para layouts responsivos**. Aqui é onde os sistemas de grid dominam. Eles tornam incrivelmente fácil a criação de interfaces mobile amigáveis, que são adaptadas para diferentes tamanhos de tela.

## Componentes Básicos

Sistemas de grid incluem dois componentes principais: linhas e colunas. Linhas são usadas para acomodar as colunas. Colunas compõem a estrutura final e envolvem o conteúdo real. Alguns sistemas de grid irão incluir _containers_, que servem para envolver o layout.

## Redefinindo o Box Model

Em primeiro lugar, é muito importante para qualquer sistema de grid redefinir o _box model_. Por padrão, o navegador não inclui `padding` e `border` dentro da largura e altura declarada para o elemento. Isso não é bom para a responsividade. Felizmente, isso pode ser corrigido definindo a propriedade `box-sizing` para `border-box` para as linhas e colunas.

<pre class="lang-css">.row,
.column {
  box-sizing: border-box;
}
</pre>

Agora podemos declarar porcentagens para a largura das colunas. Isso permite que as colunas aumentem e diminuam em diferentes tamanhos de tela enquanto mantém a estrutura.

## Limpando Floats

A fim de alinhar as colunas horizontalmente, sistemas de grid irão <a href="https://css-tricks.com/all-about-floats/" target="_blank">flutuar</a> as colunas. Isso significa que você precisa limpar os elementos que flutuam sobre a linha para manter a estrutura do layout. Aqui é onde o <a href="https://www.sitepoint.com/clearing-floats-overview-different-clearfix-methods/" target="_blank">clearfix</a> entra:

<pre class="lang-css">.row:before,
.row:after {
  content: " ";
  display: table;
}

.row:after {
  clear: both;
}
</pre>

Ao aplicar o `clearfix` para a linha no seu CSS, ele fará com que a linha se estique para acomodar as colunas que ela contém sem aumentar a marcação.

## Definindo Colunas

Para as colunas, os estilos precisam ser definidos em duas partes: os estilos em comum e as larguras. Primeiro os comuns:

<pre class="lang-css">.column {
  position: relative;
  float: left;
}
</pre>

Aqui, as colunas recebem uma posição relativa para permitir que qualquer conteúdo em posição absoluta dentro da coluna possa ser posicionado em relação a ela. As colunas então flutuam a esquerda para o alinhamento horizontal, o que fará com que o elemento se torne `display: block` mesmo se ele não começou dessa forma.

## Criando Gutters  (calhas)

_Gutters_ ajudam criar a separação entre as colunas para uma maior legibilidade e estética. Existem dois tipos de abordagem quando falamos em _gutters_; definindo _paddings_ dentro de cada coluna ou margem esquerda baseada em porcentagens para cada coluna.

Eu prefiro a última abordagem, porque ela facilita _gutters_ responsivas que irão permanecer em relação as colunas e a janela de exibição como um todo em diferentes tamanhos de tela. Ela também permite que você defina _paddings_ adicionais para as colunas para uma maior flexibilidade. A maior vantagem de _gutters_ baseadas em _paddings_ é em como eles simplificam cálculos para a largura das colunas, que ficará evidente na próxima seção.

Utilizando a abordagem de margens baseadas em porcentagem, nós podemos ter como alvo colunas que são um irmão adjacente a uma coluna precedente. Isso irá criar uma margem esquerda para cada coluna, exceto a primeira, que nós vamos definir em 1.6% usando a propriedade `margin-left`:

<pre class="lang-css">.column + .column {
  margin-left: 1.6%;
}
</pre>

**Nota do tradutor**: Para calcular a porcentagem das margens:

`mr = mp / mc`

Onde:

`mr = margem em porcentagem<br />
mp = margem em pixel<br />
mc = máximo de colunas`

## Calculando Largura das Colunas

Antes que possamos começar fazer os cálculos, precisamos determinar a quantidade máxima de colunas por linha. Uma escolha popular são 12, uma vez que existe uma maior flexibilidade já que é divisível por 1,2,3,4 e 6. Isso permite uma variedade de diferentes combinações que ainda permite colunas distribuídas uniformemente com o mesmo tamanho.

É importante entender que ter no máximo 12 colunas por linha, você precisará preencher essa quantidade em cada linha, independentemente de quantas colunas você quer. Por exemplo, se você queria apenas uma linha com 3 colunas iguais, você usaria três elementos em que cada um terá 4 colunas (4×3=12). Exceder a soma de 12 resultará em uma quebra de coluna(s) adicional(is) para uma nova linha.

Agora que sabemos o número máximo de colunas, precisamos determinar a largura de uma única coluna (1/12) usando a seguinte fórmula:

`scw = (100 – (m * (mc – 1))) / mc`

Onde:

``Ao longo dos últimos anos, sistemas de grid CSS têm crescido muito em popularidade, rapidamente sendo considerada uma boa prática para a criação de layout estruturais. Como resultado, não houve falta de _frameworks_ surgindo, oferecendo seus próprios sistemas de grid e tentando conquistar espaço.

Se você é do tipo curioso, como eu, pode estar se perguntando o que exatamente sistemas de grid podem oferecer? Como eles funcionam? E como você pode criar o seu próprio? Essas são apenas algumas das perguntas que eu vou tentar responder e como explorar os vários conceitos em jogo enquanto construímos juntos um sistema de grid básico a partir do zero.

## O que é um Sistema de Grid?

No caso de você ser um novato em sistemas de grid CSS, vamos começar com uma rápida definição. Em termos básicos, um sistema de grid é uma estrutura que permite o conteúdo ser empilhado verticalmente e horizontalmente de uma forma consistente e facilmente gerenciável. Além disso, o código de um sistema de grid é um “_project-agnostic_”, dando-lhe um elevado grau de portabilidade, de modo que, possa ser adotado em novos projetos.

## Os Benefícios

  * **Eles aumentam a produtividade** fornecendo simples e previsíveis estruturas de layout para design de HTML. A estrutura de uma página pode ser formulada rapidamente sem perder tempo em adivinhar qual sua precisão ou compatibilidade _cross-browser_.
  * **Eles são versáteis** na forma em como os layouts podem ser construídos, sendo adaptados em variadas combinações de linhas e colunas. Eles ainda suportam grids aninhados para em casos de usos complexos. Não importa a necessidade do layout, um sistema de grid é quase certamente bem adaptado.
  * **Eles são ideais para layouts responsivos**. Aqui é onde os sistemas de grid dominam. Eles tornam incrivelmente fácil a criação de interfaces mobile amigáveis, que são adaptadas para diferentes tamanhos de tela.

## Componentes Básicos

Sistemas de grid incluem dois componentes principais: linhas e colunas. Linhas são usadas para acomodar as colunas. Colunas compõem a estrutura final e envolvem o conteúdo real. Alguns sistemas de grid irão incluir _containers_, que servem para envolver o layout.

## Redefinindo o Box Model

Em primeiro lugar, é muito importante para qualquer sistema de grid redefinir o _box model_. Por padrão, o navegador não inclui `padding` e `border` dentro da largura e altura declarada para o elemento. Isso não é bom para a responsividade. Felizmente, isso pode ser corrigido definindo a propriedade `box-sizing` para `border-box` para as linhas e colunas.

<pre class="lang-css">.row,
.column {
  box-sizing: border-box;
}
</pre>

Agora podemos declarar porcentagens para a largura das colunas. Isso permite que as colunas aumentem e diminuam em diferentes tamanhos de tela enquanto mantém a estrutura.

## Limpando Floats

A fim de alinhar as colunas horizontalmente, sistemas de grid irão <a href="https://css-tricks.com/all-about-floats/" target="_blank">flutuar</a> as colunas. Isso significa que você precisa limpar os elementos que flutuam sobre a linha para manter a estrutura do layout. Aqui é onde o <a href="https://www.sitepoint.com/clearing-floats-overview-different-clearfix-methods/" target="_blank">clearfix</a> entra:

<pre class="lang-css">.row:before,
.row:after {
  content: " ";
  display: table;
}

.row:after {
  clear: both;
}
</pre>

Ao aplicar o `clearfix` para a linha no seu CSS, ele fará com que a linha se estique para acomodar as colunas que ela contém sem aumentar a marcação.

## Definindo Colunas

Para as colunas, os estilos precisam ser definidos em duas partes: os estilos em comum e as larguras. Primeiro os comuns:

<pre class="lang-css">.column {
  position: relative;
  float: left;
}
</pre>

Aqui, as colunas recebem uma posição relativa para permitir que qualquer conteúdo em posição absoluta dentro da coluna possa ser posicionado em relação a ela. As colunas então flutuam a esquerda para o alinhamento horizontal, o que fará com que o elemento se torne `display: block` mesmo se ele não começou dessa forma.

## Criando Gutters  (calhas)

_Gutters_ ajudam criar a separação entre as colunas para uma maior legibilidade e estética. Existem dois tipos de abordagem quando falamos em _gutters_; definindo _paddings_ dentro de cada coluna ou margem esquerda baseada em porcentagens para cada coluna.

Eu prefiro a última abordagem, porque ela facilita _gutters_ responsivas que irão permanecer em relação as colunas e a janela de exibição como um todo em diferentes tamanhos de tela. Ela também permite que você defina _paddings_ adicionais para as colunas para uma maior flexibilidade. A maior vantagem de _gutters_ baseadas em _paddings_ é em como eles simplificam cálculos para a largura das colunas, que ficará evidente na próxima seção.

Utilizando a abordagem de margens baseadas em porcentagem, nós podemos ter como alvo colunas que são um irmão adjacente a uma coluna precedente. Isso irá criar uma margem esquerda para cada coluna, exceto a primeira, que nós vamos definir em 1.6% usando a propriedade `margin-left`:

<pre class="lang-css">.column + .column {
  margin-left: 1.6%;
}
</pre>

**Nota do tradutor**: Para calcular a porcentagem das margens:

`mr = mp / mc`

Onde:

`mr = margem em porcentagem<br />
mp = margem em pixel<br />
mc = máximo de colunas`

## Calculando Largura das Colunas

Antes que possamos começar fazer os cálculos, precisamos determinar a quantidade máxima de colunas por linha. Uma escolha popular são 12, uma vez que existe uma maior flexibilidade já que é divisível por 1,2,3,4 e 6. Isso permite uma variedade de diferentes combinações que ainda permite colunas distribuídas uniformemente com o mesmo tamanho.

É importante entender que ter no máximo 12 colunas por linha, você precisará preencher essa quantidade em cada linha, independentemente de quantas colunas você quer. Por exemplo, se você queria apenas uma linha com 3 colunas iguais, você usaria três elementos em que cada um terá 4 colunas (4×3=12). Exceder a soma de 12 resultará em uma quebra de coluna(s) adicional(is) para uma nova linha.

Agora que sabemos o número máximo de colunas, precisamos determinar a largura de uma única coluna (1/12) usando a seguinte fórmula:

`scw = (100 – (m * (mc – 1))) / mc`

Onde:

`` 

Quando resolvemos a fórmula, temos uma única coluna de largura 6.86666666667%. A partir daqui, podemos usar esse número para calcular as larguras das colunas restantes. A fórmula para isso é:

`cw = (scw * cs) + (m * (cs – 1))`

Onde:

```Ao longo dos últimos anos, sistemas de grid CSS têm crescido muito em popularidade, rapidamente sendo considerada uma boa prática para a criação de layout estruturais. Como resultado, não houve falta de _frameworks_ surgindo, oferecendo seus próprios sistemas de grid e tentando conquistar espaço.

Se você é do tipo curioso, como eu, pode estar se perguntando o que exatamente sistemas de grid podem oferecer? Como eles funcionam? E como você pode criar o seu próprio? Essas são apenas algumas das perguntas que eu vou tentar responder e como explorar os vários conceitos em jogo enquanto construímos juntos um sistema de grid básico a partir do zero.

## O que é um Sistema de Grid?

No caso de você ser um novato em sistemas de grid CSS, vamos começar com uma rápida definição. Em termos básicos, um sistema de grid é uma estrutura que permite o conteúdo ser empilhado verticalmente e horizontalmente de uma forma consistente e facilmente gerenciável. Além disso, o código de um sistema de grid é um “_project-agnostic_”, dando-lhe um elevado grau de portabilidade, de modo que, possa ser adotado em novos projetos.

## Os Benefícios

  * **Eles aumentam a produtividade** fornecendo simples e previsíveis estruturas de layout para design de HTML. A estrutura de uma página pode ser formulada rapidamente sem perder tempo em adivinhar qual sua precisão ou compatibilidade _cross-browser_.
  * **Eles são versáteis** na forma em como os layouts podem ser construídos, sendo adaptados em variadas combinações de linhas e colunas. Eles ainda suportam grids aninhados para em casos de usos complexos. Não importa a necessidade do layout, um sistema de grid é quase certamente bem adaptado.
  * **Eles são ideais para layouts responsivos**. Aqui é onde os sistemas de grid dominam. Eles tornam incrivelmente fácil a criação de interfaces mobile amigáveis, que são adaptadas para diferentes tamanhos de tela.

## Componentes Básicos

Sistemas de grid incluem dois componentes principais: linhas e colunas. Linhas são usadas para acomodar as colunas. Colunas compõem a estrutura final e envolvem o conteúdo real. Alguns sistemas de grid irão incluir _containers_, que servem para envolver o layout.

## Redefinindo o Box Model

Em primeiro lugar, é muito importante para qualquer sistema de grid redefinir o _box model_. Por padrão, o navegador não inclui `padding` e `border` dentro da largura e altura declarada para o elemento. Isso não é bom para a responsividade. Felizmente, isso pode ser corrigido definindo a propriedade `box-sizing` para `border-box` para as linhas e colunas.

<pre class="lang-css">.row,
.column {
  box-sizing: border-box;
}
</pre>

Agora podemos declarar porcentagens para a largura das colunas. Isso permite que as colunas aumentem e diminuam em diferentes tamanhos de tela enquanto mantém a estrutura.

## Limpando Floats

A fim de alinhar as colunas horizontalmente, sistemas de grid irão <a href="https://css-tricks.com/all-about-floats/" target="_blank">flutuar</a> as colunas. Isso significa que você precisa limpar os elementos que flutuam sobre a linha para manter a estrutura do layout. Aqui é onde o <a href="https://www.sitepoint.com/clearing-floats-overview-different-clearfix-methods/" target="_blank">clearfix</a> entra:

<pre class="lang-css">.row:before,
.row:after {
  content: " ";
  display: table;
}

.row:after {
  clear: both;
}
</pre>

Ao aplicar o `clearfix` para a linha no seu CSS, ele fará com que a linha se estique para acomodar as colunas que ela contém sem aumentar a marcação.

## Definindo Colunas

Para as colunas, os estilos precisam ser definidos em duas partes: os estilos em comum e as larguras. Primeiro os comuns:

<pre class="lang-css">.column {
  position: relative;
  float: left;
}
</pre>

Aqui, as colunas recebem uma posição relativa para permitir que qualquer conteúdo em posição absoluta dentro da coluna possa ser posicionado em relação a ela. As colunas então flutuam a esquerda para o alinhamento horizontal, o que fará com que o elemento se torne `display: block` mesmo se ele não começou dessa forma.

## Criando Gutters  (calhas)

_Gutters_ ajudam criar a separação entre as colunas para uma maior legibilidade e estética. Existem dois tipos de abordagem quando falamos em _gutters_; definindo _paddings_ dentro de cada coluna ou margem esquerda baseada em porcentagens para cada coluna.

Eu prefiro a última abordagem, porque ela facilita _gutters_ responsivas que irão permanecer em relação as colunas e a janela de exibição como um todo em diferentes tamanhos de tela. Ela também permite que você defina _paddings_ adicionais para as colunas para uma maior flexibilidade. A maior vantagem de _gutters_ baseadas em _paddings_ é em como eles simplificam cálculos para a largura das colunas, que ficará evidente na próxima seção.

Utilizando a abordagem de margens baseadas em porcentagem, nós podemos ter como alvo colunas que são um irmão adjacente a uma coluna precedente. Isso irá criar uma margem esquerda para cada coluna, exceto a primeira, que nós vamos definir em 1.6% usando a propriedade `margin-left`:

<pre class="lang-css">.column + .column {
  margin-left: 1.6%;
}
</pre>

**Nota do tradutor**: Para calcular a porcentagem das margens:

`mr = mp / mc`

Onde:

`mr = margem em porcentagem<br />
mp = margem em pixel<br />
mc = máximo de colunas`

## Calculando Largura das Colunas

Antes que possamos começar fazer os cálculos, precisamos determinar a quantidade máxima de colunas por linha. Uma escolha popular são 12, uma vez que existe uma maior flexibilidade já que é divisível por 1,2,3,4 e 6. Isso permite uma variedade de diferentes combinações que ainda permite colunas distribuídas uniformemente com o mesmo tamanho.

É importante entender que ter no máximo 12 colunas por linha, você precisará preencher essa quantidade em cada linha, independentemente de quantas colunas você quer. Por exemplo, se você queria apenas uma linha com 3 colunas iguais, você usaria três elementos em que cada um terá 4 colunas (4×3=12). Exceder a soma de 12 resultará em uma quebra de coluna(s) adicional(is) para uma nova linha.

Agora que sabemos o número máximo de colunas, precisamos determinar a largura de uma única coluna (1/12) usando a seguinte fórmula:

`scw = (100 – (m * (mc – 1))) / mc`

Onde:

``Ao longo dos últimos anos, sistemas de grid CSS têm crescido muito em popularidade, rapidamente sendo considerada uma boa prática para a criação de layout estruturais. Como resultado, não houve falta de _frameworks_ surgindo, oferecendo seus próprios sistemas de grid e tentando conquistar espaço.

Se você é do tipo curioso, como eu, pode estar se perguntando o que exatamente sistemas de grid podem oferecer? Como eles funcionam? E como você pode criar o seu próprio? Essas são apenas algumas das perguntas que eu vou tentar responder e como explorar os vários conceitos em jogo enquanto construímos juntos um sistema de grid básico a partir do zero.

## O que é um Sistema de Grid?

No caso de você ser um novato em sistemas de grid CSS, vamos começar com uma rápida definição. Em termos básicos, um sistema de grid é uma estrutura que permite o conteúdo ser empilhado verticalmente e horizontalmente de uma forma consistente e facilmente gerenciável. Além disso, o código de um sistema de grid é um “_project-agnostic_”, dando-lhe um elevado grau de portabilidade, de modo que, possa ser adotado em novos projetos.

## Os Benefícios

  * **Eles aumentam a produtividade** fornecendo simples e previsíveis estruturas de layout para design de HTML. A estrutura de uma página pode ser formulada rapidamente sem perder tempo em adivinhar qual sua precisão ou compatibilidade _cross-browser_.
  * **Eles são versáteis** na forma em como os layouts podem ser construídos, sendo adaptados em variadas combinações de linhas e colunas. Eles ainda suportam grids aninhados para em casos de usos complexos. Não importa a necessidade do layout, um sistema de grid é quase certamente bem adaptado.
  * **Eles são ideais para layouts responsivos**. Aqui é onde os sistemas de grid dominam. Eles tornam incrivelmente fácil a criação de interfaces mobile amigáveis, que são adaptadas para diferentes tamanhos de tela.

## Componentes Básicos

Sistemas de grid incluem dois componentes principais: linhas e colunas. Linhas são usadas para acomodar as colunas. Colunas compõem a estrutura final e envolvem o conteúdo real. Alguns sistemas de grid irão incluir _containers_, que servem para envolver o layout.

## Redefinindo o Box Model

Em primeiro lugar, é muito importante para qualquer sistema de grid redefinir o _box model_. Por padrão, o navegador não inclui `padding` e `border` dentro da largura e altura declarada para o elemento. Isso não é bom para a responsividade. Felizmente, isso pode ser corrigido definindo a propriedade `box-sizing` para `border-box` para as linhas e colunas.

<pre class="lang-css">.row,
.column {
  box-sizing: border-box;
}
</pre>

Agora podemos declarar porcentagens para a largura das colunas. Isso permite que as colunas aumentem e diminuam em diferentes tamanhos de tela enquanto mantém a estrutura.

## Limpando Floats

A fim de alinhar as colunas horizontalmente, sistemas de grid irão <a href="https://css-tricks.com/all-about-floats/" target="_blank">flutuar</a> as colunas. Isso significa que você precisa limpar os elementos que flutuam sobre a linha para manter a estrutura do layout. Aqui é onde o <a href="https://www.sitepoint.com/clearing-floats-overview-different-clearfix-methods/" target="_blank">clearfix</a> entra:

<pre class="lang-css">.row:before,
.row:after {
  content: " ";
  display: table;
}

.row:after {
  clear: both;
}
</pre>

Ao aplicar o `clearfix` para a linha no seu CSS, ele fará com que a linha se estique para acomodar as colunas que ela contém sem aumentar a marcação.

## Definindo Colunas

Para as colunas, os estilos precisam ser definidos em duas partes: os estilos em comum e as larguras. Primeiro os comuns:

<pre class="lang-css">.column {
  position: relative;
  float: left;
}
</pre>

Aqui, as colunas recebem uma posição relativa para permitir que qualquer conteúdo em posição absoluta dentro da coluna possa ser posicionado em relação a ela. As colunas então flutuam a esquerda para o alinhamento horizontal, o que fará com que o elemento se torne `display: block` mesmo se ele não começou dessa forma.

## Criando Gutters  (calhas)

_Gutters_ ajudam criar a separação entre as colunas para uma maior legibilidade e estética. Existem dois tipos de abordagem quando falamos em _gutters_; definindo _paddings_ dentro de cada coluna ou margem esquerda baseada em porcentagens para cada coluna.

Eu prefiro a última abordagem, porque ela facilita _gutters_ responsivas que irão permanecer em relação as colunas e a janela de exibição como um todo em diferentes tamanhos de tela. Ela também permite que você defina _paddings_ adicionais para as colunas para uma maior flexibilidade. A maior vantagem de _gutters_ baseadas em _paddings_ é em como eles simplificam cálculos para a largura das colunas, que ficará evidente na próxima seção.

Utilizando a abordagem de margens baseadas em porcentagem, nós podemos ter como alvo colunas que são um irmão adjacente a uma coluna precedente. Isso irá criar uma margem esquerda para cada coluna, exceto a primeira, que nós vamos definir em 1.6% usando a propriedade `margin-left`:

<pre class="lang-css">.column + .column {
  margin-left: 1.6%;
}
</pre>

**Nota do tradutor**: Para calcular a porcentagem das margens:

`mr = mp / mc`

Onde:

`mr = margem em porcentagem<br />
mp = margem em pixel<br />
mc = máximo de colunas`

## Calculando Largura das Colunas

Antes que possamos começar fazer os cálculos, precisamos determinar a quantidade máxima de colunas por linha. Uma escolha popular são 12, uma vez que existe uma maior flexibilidade já que é divisível por 1,2,3,4 e 6. Isso permite uma variedade de diferentes combinações que ainda permite colunas distribuídas uniformemente com o mesmo tamanho.

É importante entender que ter no máximo 12 colunas por linha, você precisará preencher essa quantidade em cada linha, independentemente de quantas colunas você quer. Por exemplo, se você queria apenas uma linha com 3 colunas iguais, você usaria três elementos em que cada um terá 4 colunas (4×3=12). Exceder a soma de 12 resultará em uma quebra de coluna(s) adicional(is) para uma nova linha.

Agora que sabemos o número máximo de colunas, precisamos determinar a largura de uma única coluna (1/12) usando a seguinte fórmula:

`scw = (100 – (m * (mc – 1))) / mc`

Onde:

`` 

Quando resolvemos a fórmula, temos uma única coluna de largura 6.86666666667%. A partir daqui, podemos usar esse número para calcular as larguras das colunas restantes. A fórmula para isso é:

`cw = (scw * cs) + (m * (cs – 1))`

Onde:

``` 

Aplicando essa fórmula para cada uma das 12 colunas resulta no CSS a seguir:

<pre class="lang-css">.column-1 {
  width: 6.86666666667%;
}

.column-2 {
  width: 15.3333333333%;
}

.column-3 {
  width: 23.8%;
}

.column-4 {
  width: 32.2666666667%;
}

.column-5 {
  width: 40.7333333333%;
}

.column-6 {
  width: 49.2%;
}

.column-7 {
  width: 57.6666666667%;
}

.column-8 {
  width: 66.1333333333%;
}

.column-9 {
  width: 74.6%;
}

.column-10 {
  width: 83.0666666667%;
}

.column-11 {
  width: 91.5333333333%;
}

.column-12 {
  width: 100%;
}
</pre>

## Otimizando para Dispositivos Móveis

Apesar do fato que o sistema de grid é responsivo, ele sozinho não pode ir tão longe. Para dispositivos com pequenas telas, tais como smartphones, a largura das colunas precisam se ajustar para permitir que o conteúdo que elas contêm ainda apareça legível e visualmente atraente. Consultas de mídia ajudam com isso:

<pre class="lang-css">@media only screen and (max-width: 550px) {
  .column-1,
  .column-2,
  .column-3,
  .column-4,
  .column-5,
  .column-6,
  .column-7,
  .column-8,
  .column-9,
  .column-10,
  .column-11,
  .column-12 {
    width: auto;
    float: none;
  }

  .column + .column {
    margin-left: 0;
  }
}
</pre>

Aqui, estamos dizendo ao grid para permitir que cada coluna possa ocupar a largura total do seu _container_ para dispositivos com uma janela menor que 550px de largura. _Gutters_ já não são mais necessárias aqui, então nós as removemos.

Como alternativa, você pode optar pela estratégia <a href="https://www.sitepoint.com/making-case-mobile-first-designs/" target="_blank">mobile first</a> que leva a abordagem oposta, aumentando para um layout de 12 colunas. Nesse caso, as colunas começam como uma largura total, depois estabelecemos as larguras das colunas e _floats_ para permitir que elas se alinhem horizontalmente quando a resolução da tela atinge um limite especificado.

Esse é a abordagem preferida para o sistema de grid do <a href="https://www.sitepoint.com/understanding-bootstrap-grid-system/" target="_blank">bootstrap</a>, que não institui a largura das colunas até que a janela de exibição atinja uma largura mínima de 992px. Essa pode ser uma abordagem mais favorável para seu caso, e deve ser algo para analisar melhor quando avaliar um sistema de grid.

## Juntando Tudo

Quando combinamos todos os conceitos e o CSS, podemos escrever uma estrutura de layout em HTML igual a:

<pre class="lang-html">&lt;div class="row"&gt;
  &lt;div class="column column-4"&gt;&lt;/div&gt;
  &lt;div class="column column-4"&gt;&lt;/div&gt;
  &lt;div class="column column-4"&gt;&lt;/div&gt;
&lt;/div&gt;

&lt;div class="row"&gt;
  &lt;div class="column column-2"&gt;&lt;/div&gt;
  &lt;div class="column column-4"&gt;&lt;/div&gt;
  &lt;div class="column column-4"&gt;&lt;/div&gt;
  &lt;div class="column column-2"&gt;&lt;/div&gt;
&lt;/div&gt;
</pre>

Confira abaixo a demonstração no CodePen para ver todo o sistema de grid em ação, incluindo grid aninhados.

{{< codepen 
  hash="dPqqvN"
  user="SitePoint"
  author="SitePoint"
  title="Understanding CSS Grid Systems"
>}}

Você também experimentar a <a href="https://codepen.io/ryanmorr/full/zxRzyE/" target="_blank">demo em tela cheia</a> para uma melhor impressão. Não se esqueça de brincar com as dimensões da tela para ver como o grid lida com várias resoluções.

## Conclusão

Como você pode ver, não é preciso muito para montar um sistema de grid básico. A matemática é provavelmente a parte mais complexa. Apesar da simplicidade, o grid continua a ser uma poderosa e flexível ferramenta para layouts estruturais. Com os diversos conceitos que discutimos aqui, espero que você tenha uma melhor compreensão de como sistemas de grid funcionam. Isso deve ajudá-lo a avaliar diferentes sistemas de grid que se destacam, e escolher o melhor deles para o seu próximo projeto, ou até mesmo criar o seu próprio.

Tradução: Tamiris Bonicenha

Acesse o artigo original no <a href="https://www.sitepoint.com/understanding-css-grid-systems/" target="_blank">SitePoint – &#8220;Understanding CSS Grid Systems from the Ground Up&#8221;</a>
