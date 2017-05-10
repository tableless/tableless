---
title: Semântica de variáveis e propriedades personalizadas em CSS
author: Jean Carlo Emer
type: post
date: 2014-04-16
excerpt: Um texto sobre variáveis em pré-processadores de CSS e a nova especificação de variáveis para folhas de estilo.
url: /semantica-de-variaveis-e-propriedades-personalizadas-em-css/
dsq_thread_id: 2616763327
categories:
  - Geral

---
## Pré-processadores

Sou defensor do uso de pré-processadores de CSS e tenho alguns [bons argumentos para convencer você][1]. Um dos benefícios dos pré-processadores é a possibilidade de uso de variáveis para armazenar medidas, cores e outros atributos do _layout_.

Além de manter seu projeto facilmente configurável e permitir o uso de álgebra, a simples tarefa de dar nome aos atributos força um raciocínio mais apurado. Variações pequenas de medidas e cores, que são resquícios das ferramentas utilizadas para _design_, serão mais facilmente identificadas e limadas.

> There are only two hard things in Computer Science: cache invalidation and naming things.
  
> &#8212; Phil Karlton

A semântica, de maneira geral, descreve o significado dos _tokens_ da linguagem. Em nosso caso, a semântica descreve quais as transformações que nosso código irá sofrer durante o processamento.

Diferentes pré-processadores possuem significativas diferenças no comportamento de variáveis. Um aspecto importante é entender qual o comportamento das variáveis em meio a estas transformações a fim de evitar resultados inesperados.

### Introdução

Seletores aninhados são a principal influência no comportamento de variáveis em pré-processadores. Variáveis definidas em um nível são visíveis para todos os níveis aninhados mais internamente.

    .list {
        $var-red: crimson;
        .list-item {
            color: $var-red;
        }
    }
    

Quando definimos uma variável fora de qualquer seletor, esta será visível em qualquer ponto do código. Chamamos estas variáveis de globais.

    $global-red: crimson;
    .list-item {
        color: $global-red;
    }
    

### Sass

Vejamos a semântica das variáveis no [Sass utilizando um exemplo][2]. Após definido o valor de uma variável em um seletor, uma nova atribuição em um aninhamento interno terá efeito também nos níveis externos. Este comportamento pode ser um pouco estranho, veja em nosso exemplo como o seletor `.just-to-confuse-you` modifica o valor de `$orange` afetando inclusive o valor da variável no seletor `.is-orange`. O caso da variável global `$red` também é curioso, qualquer ponto do código poderá modificar seu valor afetando em todos os seus usos subsequentes indiferente do nível de aninhamento do seletor.

Caso tenha um bom domínio de JavaScript, uma analogia pode ajudar no seu entendimento. Pense no aninhamento dos seletores como escopos criados por [funções imediatamente invocadas][3]. A primeira atribuição de valor a uma variável também a declara utilizando `var`. As demais atribuições de valor em escopos mais internos não fazem mais uso do `var`. Veja, _closures_ que podem alterar o valor das variáveis dos escopos em que são criadas afetando todos os demais escopos. Variáveis que tem seu primeiro valor atribuído fora de qualquer seletor serão globais, nunca farão uso de `var`.

Este comportamento é um tanto estranho e algumas vezes criticado. Um seletor aninhado pode acidentalmente atribuir valor a uma variável global e impactar no restante do projeto. Pensando nisto, as variáveis globais não poderão mais ser alteradas dentro de seletores nas próximas versões do pré-processador. A [versão 3.3.0][4] já inclui a _flag_ `!global`. Nesta versão, já é acusado um _warning_ se a _flag_ não for usada ao alterar o valor de uma global dentro de um seletor.

Vale lembrar que existe também _flag_ `!default` para os casos em que a intenção seja atribuir valor a uma variável apenas se está ainda não tiver recebido algum.

### LESS e Stylus

A semântica de variáveis no LESS e Stylus é um tanto mais previsível. Retomando a nossa analogia com o universo JavaScript, pense como se cada atribuição de valor fosse precedida de uma declaração de variável utilizando `var`. O valor do escopo mais externo será ofuscado mas não alterado.

Voltando aos pré-processadores, um seletor não terá a capacidade de alterar o valor de uma variável global ou definida em um seletor de nível mais externo. Este apenas definirá uma nova variável visível no nível atual e nos níveis mais internos. Mais simples e seguro, porém um tanto menos poderoso que no Sass. Confira o [exemplo em LESS][5] (na dúvida, [aqui está em Stylus][6]).

O LESS não dispõe de nenhuma _flag_ como `!default` e `!global`, uma pena.

### Variáveis e os mixins

Os _mixins_ também possuem um papel importante na [manipulação de variáveis][7], tanto no LESS quanto no Sass, o escopo levado em consideração é aquele em que o _mixin_ é incluído. Isto é útil para sistemas semânticos de _grids_ em porcentagem, por exemplo. Confira o código do Bourbon Neat e veja como os _mixins_ [utilizam variáveis][8] para [compartilhar][9] valores entre si.

Curiosamente, os _mixins_ do Stylus têm acesso as variáveis do seletor em que são incluídos, porém [não possuem capacidade de alterar seus valores][10]. No Stylus, os _mixins_ constituem um escopo que impossibilita alterar valores de variáveis de escopos externos.

A semântica de comportamento das variáveis segue a já ilustrada para cada um dos pré-processadores. Portanto, os _mixins_ de Sass são um tanto mais poderosos e destrutivos por poderem manipular variáveis globais mesmo quando incluídos em um seletor.

## Variáveis nativas de CSS

Os pré-processadores de CSS mais populares já tem pouco mais de meia década de existência. Neste tempo, seus benefícios puderam ser comprovados e naturalmente rascunhos de especificações surgiram para incorporar algumas das suas funcionalidades ao CSS.

O primeiro rascunho de [especificação de variáveis nativas no CSS][11] data de 2012. Esta especificação é bastante comparada com as variáveis já presentes nos pré-processadores, inclusive por [fontes renomadas][12]. Na minha opinião, a comparação é equivocada, **as variáveis nativas possuem uma semântica e uso completamente diferente das que temos nos pré-processadores**.

O último rascunho da especificação é intitulado _CSS Custom Properties_ e isto já nos dá uma boa pista da diferença de comportamento. As variáveis nativas são propriedades [com característica de herança][13] igual a `color` e `font`: seus valores são herdados por padrão pelos filhos do elemento em que são definidas. **Parece simples, mas esta é a grande diferença, o comportamento variáveis nativas é apoiado nos elementos do documento assim como o restante da folha de estilo**.

## Propriedades Personalizadas

A partir de agora, passaremos a chamar nossas variáveis nativas de propriedades personalizadas a fim de seguir a especificação e expressar melhor seu significado. A propriedade personalizada é aquela cuja definição é precedida de `--`. Seus valores podem ser acessados através da função `var()`. Vejamos um primeiro exemplo.

    .list {
        --red: crimson;
        .list-item {
            color: var(--red);
        }
    }
    

Como você pode imaginar, o conceito de variável global não mais se aplica às propriedades personalizadas. Uma certa confusão pode ser causada ao analisar trechos de código como este abaixo que inclusive fazem parte da especificação.

    :root {
    --red: crimson;
    }
    

Não há nenhuma relação com variáveis globais. O `:root` trata-se de um seletor da especificação _level_ 3 que referencia o mais externos dos elementos do documento. Na prática, este seletor pode ser substituído pelo seletor `html`. Uma das razões da criação do `:root` é a de que folhas de estilo podem ser utilizadas em documentos no formato SVG e XML, o que não vem muito ao caso.

### Componentes

O ponto forte das propriedades personalizadas está enraizado justamente na herança. Um dos assuntos mais mencionados nos últimos tempos no desenvolvimento _front-end_ são os componentes. São nos componentes que as propriedades personalizadas ganham destaque.

A melhor maneira de provar as vantagens de uma tecnologia é resolvendo um problema real. Tenho em memória um problema que enfrentei em uma plataforma de ensino. Nesta plataforma de ensino, haviam cerca de dez disciplinas, cada uma identificada com uma cor. Os componentes da plataforma ganhavam a caracterização de uma das disciplinas e as cores da disciplina eram utilizadas em diferentes propriedades como `background`, `color`, `box-shadow` e `border-color` em elementos distintos do componente. Não existe uma maneira sensata de solucionar um problema como este, a solução é duplicar bastante código. As propriedades personalizadas nos permitem resolver de uma maneira incrível, vejam o exemplo:

    /* Component lesson */
    .lesson {
        color: grey;
        border: 1px solid var(--discipline-color);
    }
    .lesson-title {
        color: var(--discipline-color);
    }
    .lesson-grade {
        background: var(--discipline-color);
    }
    
    /* Disciplines */
    .discipline-mathematics {
        --discipline-color: blue;
    }
    
    .discipline-portuguese {
        --discipline-color: red;
    }
    

Este exemplo pode ser aplicado muito facilmente ao HTML dos componentes, basta adicionarmos uma das classes de disciplina a cada um deles: `<div class="lesson discipline-mathematics">`. Veja o [exemplo em funcionamento][14] (apenas Firefox Nightly).

## Palavras finais

**As propriedades personalizadas não substituem as variáveis dos pré-processadores**. As variáveis dos pré-processadores continuarão cumprindo sua função de abstrair aspectos de _layout_ descomplicando sua organização de código. As propriedades personalizadas deverão, por sua vez, facilitar a customização de componentes. O ideal é aprendermos a utilizar estes dois recursos em conjunto.

A especificação de _CSS Custom Properties_ ainda está em rascunho e só está implementada por enquanto no Firefox Nightly. Apesar de ainda precisarmos esperar um pouco para utilizar em produção, é importante já raciocinarmos quais os problemas que as propriedades solucionam. Lembre-se que as variáveis de pré-processadores já estão por ai há um bom tempo e não tem porque deixar de usá-las.

Espero que este texto o tenha ajudado a entender a diferente semântica das variáveis em cada um dos pré-processadores e diferenciado o suficiente das propriedades personalizadas.

 [1]: http://tableless.com.br/css-steroids
 [2]: http://codepen.io/jcemer/pen/CfvLm
 [3]: http://benalman.com/news/2010/11/immediately-invoked-function-expression
 [4]: http://sass-lang.com/documentation/file.SASS_CHANGELOG.html#330_7_march_2014
 [5]: http://codepen.io/jcemer/pen/yqLoJ
 [6]: http://codepen.io/jcemer/pen/AJzwp
 [7]: http://codepen.io/jcemer/pen/qBlci
 [8]: https://github.com/thoughtbot/neat/blob/90016226abbdcc4c01cf24ce7346cb4ed2d5291b/app/assets/stylesheets/grid/_row.scss#L3
 [9]: https://github.com/thoughtbot/neat/blob/90016226abbdcc4c01cf24ce7346cb4ed2d5291b/app/assets/stylesheets/grid/_span-columns.scss#L8
 [10]: http://codepen.io/jcemer/pen/tijCI
 [11]: http://dev.w3.org/csswg/css-variables
 [12]: https://developer.mozilla.org/en-US/docs/Web/CSS/Using_CSS_variables
 [13]: http://tableless.com.br/efeito-cascata-e-especificidade-do-css
 [14]: http://codepen.io/jcemer/pen/uwntB