---
title: Turbinando as Media Queries
author: Átila Fassina
type: post
date: 2013-12-12
excerpt: Entenda um pouco mais sobre como melhorar o gerenciamento de breakpoints com SASS.
url: /turbinando-media-queries/
dsq_thread_id: 2037688855
categories:
  - CSS
  - Pré-processadores
  - SASS
  - Técnicas e Práticas
tags:
  - breakpoints
  - CSS
  - media queries
  - responsive
  - SASS

---
Media Queries são uma das ferramenta mais importante do CSS pra quem se preocupa com Web Design Responsivo. Com uma ajudinha dos pré-processadores as media queries podem ficar ainda melhores. Neste artigo vamos turbinar as Media Queries usando um pouco das opções que o SASS nos oferece para ajudar na organização, manutenção e garantir legibilidade ao nosso código.

Nota: os exemplos deste post serão todos em SASS com a sintaxe do `.scss`.

## Breakpoints em variáveis

Se você já usou algum pré-processador, sem dúvida já usou variáveis.

<pre class="lang-css prettyprint linenums">// width
$bp-smallest: 10em;
$bp-small: 30em;
$tp-small-1: 37.5em;
</pre>

Dessa forma, você consegue manter seus breakpoints sob controle e replicá-los de forma concisa e prática. Como estamos falando de organização de código, consistência na nomenclatura é muito importante, então vamos dar uma olhada na que adotei para mim. Você pode criar a sua e se tiver em uma equipe, é bom que todos da equipe concordem com uma mesma nomenclatura:

  * **bp**: Breakpoints são pontos onde a mudança interfere amplamente no layout (redução/aumento de colunas, posição de elementos importantes, etc)
  * **tp**: Tweakpoints são para mudanças menores, que interferem em apenas um elemento

Facilita a leitura se colocar juntamente com a sigla uma característica (no caso, **small**). Além disso, Tweakpoints costumam ter uma ocorrência maior que Breakpoints, por isso numerá-los é uma boa forma de manter o controle.

## Media Features em variáveis

Outra forma de trabalhar com variáveis em suas Media Queries é armazenar toda a **media feature** como uma `string`. Por exemplo:

<pre class="lang-css prettyprint linenums">// width
$bp-w-small: '(min-width: 30em)';
$tp-w-small-1: '(min-width: 37.5em)';

// height
$bp-h-small: '(min-height: 10em)';
</pre>

Essa técnica tem maior legibilidade das variáveis. Utilizei os mesmos valores no exemplo acima, mas antes não era possível perceber que uma delas era utilizada para a altura da viewport e as outras duas para a largura.

Com relação à nomenclatura, uma pequena alteração para auxiliar na legibilidade (uma vez que a string não aparecerá ao longo do seu código de desenvolvimento), coloquei um `h` para height e um `w` para width.

Lembrando que, nesse caso é preciso escapar envolvendo a variável com `#{}` quando inserí-la no código para garantir que seu valor não seja interpretado pelo compilador.

<pre class="lang-css prettyprint linenums">@media #{$bp-w-small} {
        /*--styles--*/
}

@media #{$tp-w-small-1} {
        /*--styles--*/
}

@media #{$bp-h-small} {
    /*--styles--*/
}
</pre>

## Media Queries com mixins

Outra maneira de lidar com suas media queries é colocando-as em um `mixin` e selecionando a partir de condicionais (`@if`). Segue o exemplo:

<pre class="lang-css prettyprint linenums">$bp-width-small : "(min-width: 24em)";
$tp-height-small : 10em;

@mixin mq($breakpoint) {
    @if $breakpoint == $tp-height-small {
        @media (max-height: $tp-height-small) {
                @content;
        }
    }
    @if $breakpoint == $bp-width-small {
        @media #{$bp-width-small} {
                @content;
        }
    }
    @if $breakpoint == 50 {
        @media (max-width: 50em) {
                @content;
        }
    }
}
</pre>

Outro ponto positivo de utilizar as Media Queries envolvidas em `mixin` é de oferecer uma CSS como fallback para navegadores que não suportam Media Queries. Para isso, é só estabeler mais um condicional. Veja o exemplo:

<pre class="lang-css prettyprint linenums">$bp-width-small : "(min-width: 24em)";
$tp-height-small : 10em;

$mediaqueries: true;

@mixin mq($breakpoint) {
    @if $mediaqueries == true {
        @if $breakpoint == $tp-height-small {
                @media (max-height: $tp-height-small) {
                        @content;
            }
        }
        @if $breakpoint == #{$bp-width-small} {
                @media #{$bp-width-small} {
                        @content;
            }
        }
        @if $breakpoint == 50 {
                @media (max-width: 50em) {
                        @content;
                }
        }
    }

}
</pre>

Nesse caso, o compilador vai avaliar se a variável `$mediaqueries` é `true` ou `false`. Caso seja `true`, significa que há suporte para Media Queries e portanto, ele vai compilar o mixin; se for `false` ele ignora a declaração do `mixin` e compila o restante do código sem Media Queries.

Espero que o post tenha sido útil e ajudado a ilustrar um pouco melhor as facilidades que um pré-processador pode trazer para o seu workflow. Você já usa alguma técnica dessa em seus projetos?