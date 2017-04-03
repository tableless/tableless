---
title: Workflow Front-end
author: Bruno Ruiz
type: post
date: 2015-01-21
excerpt: O desenvolvimento em html, javascript e CSS é uma forma mágica de se construir um mundo novo a cada linha de código. Os mágicos do front-end precisam de cartolas para que retirem seus coelhos.
url: /workflow-front-end/
categories:
  - CSS
  - CSS3
  - LESS
  - Pré-processadores
  - SASS
  - Técnicas e Práticas
tags:
  - CSS
  - LESS
  - SASS

---
O desenvolvimento em html, javascript e CSS é uma forma mágica de se construir um mundo novo a cada linha de código. Os mágicos do front-end precisam de cartolas para que retirem seus coelhos. Essas cartolas e varinhas mágicas devem ser escolhidas a dedo, para que a mágica aconteça de forma suave e agradável à plateia.

Cada mágico tem sua técnica, portanto o objetivo não é estabelecer um padrão imutável, mas estabelecer diretrizes que possam servir de auxílio a qualquer ilusionista. Vamos entender magia.

## Baralho

Todo mágico possui um baralho. Com ele é possível fazer um número imenso de ilusões. Tão versátil quanto um baralho, deve ser o editor de texto a ser usado pelo desenvolvedor.

Vamos falar de dois editores: Edge Code e Sublime Text.

O Edge Code tem como objetivo permitir o foco no trabalho, para isso ele tem uma interface propositalmente simples. Uma mágica que adoro nele é poder editar conteúdo de um arquivo por meio de outro com base em uma relação específica – ou seja, tenho no arquivo html uma marcação que faz referência a uma classe CSS, clicando com o botão direito nessa classe e selecionando quick edit podemos editar o CSS do arquivo externo com base no arquivo html. Esse baralho tem muito mais mágicas.

O Sublime Text tem tantos recursos que possibilitam uma produtividade imensa. Quando você acessa <http://www.sublimetext.com/>, nota-se o foco em mostrar o quão produtivo o Sublime Text é. Uma mágica de produtividade é a possibilidade de selecionar um texto que se repete em um arquivo html por meio da tecla de atalho Ctrl+d e alterar todos ao mesmo tempo. Adoro isso.

## Cartola

O NodeJS permite que mágicas que eram feitas somente no palco – navegador –, possam ser feitas atrás das cortinas – servidor. No entanto essas mágicas são cada vez mais complexas, gerando uma dependência de recursos que necessitariam de outra ferramenta mágica para gerenciá-las.

Essa outra ferramenta mágica é nossa cartola. Dela tiramos tudo que é necessário para fazermos o show. Duas cartolas não podem deixar de serem conhecidas: NPM e Bower.

O NPM é o que todo gerenciador de dependências precisa ser: instalador de pacotes, gerenciador de versão e gerenciador de dependências.

O Bower é o que o NPM é, mas para componentes front-end.

Se este é o cenário, então é bom termos duas cartolas, cada uma fazendo seu tipo de mágica: NPM no desenvolvimento com Grunt, Gulp, JSHint, etc; e Bower para componentes front-end.

## Assistentes

Assistentes de palco são vitais no contexto de muitas mágicas. Além de distrair quem vê o espetáculo, elas embelezam o ambiente. Elas são o CSS da ilusão.

Frameworks de estilo podem agilizar muito um trabalho, porque muitas das preocupações iniciais do projeto, podem ser deixadas de lado pela adoção de um padrão, que já respondeu a todas elas. Nossas assistentes de palco são: Bootstrap e Pure.

Bootstrap é de longe a ferramenta mais popular para atribuição de estilo aos projetos. Pontos positivos: variedade de componentes, utilizado por grandes empresas que contribuem com o projeto e boa documentação. Ele é a assistente que sabe como as mágicas são feitas.

Pure tem como objetivo fornecer estilo totalmente independente de qualquer javascript e de uma maneira muito leve. É uma assistente magrinha que faz seu trabalho bem feito.

É inquestionável que a aparência faz muita diferença.

## Caixas e lâminas

Na mágica da mulher cortada ao meio, uma mulher entra numa caixa e o mágico enfia uma lâmina no meio da caixa, e ela é separada em duas partes. As mãos, a cabeça e os pés continuam se mexendo. Quando uso pré-processadores CSS me sinto separado um corpo ao meio, mas ao mesmo tempo confiando que ele irá unir as partes e no final teremos um corpo inteiro.

É claro que escrever CSS puro gerará menos código que o uso errôneo de mixins em SASS. Mas devemos medir a relação de custo e benefício em relação a produtividade (após a curva de aprendizagem ser superada) e qualidade do nosso código, para podermos escolher aquilo que é melhor para o projeto &#8211; espetáculo. Nossas caixas e lâminas para separarem corpos podem ser: LESS e SASS.

As características da LESS que devem ser sempre destacadas são, em sua maioria, comuns aos pré-processadores. Mas devem ser ditas aqui:

  * Variáveis: valores que são usados em vários lugares podem ser reutilizados por todo o estilo do projeto, e quando uma alteração for necessária, poderá ser feita com muita facilidade.
  * Mixins: servem ao mesmo propósito das variáveis – a reutilização –, mas sendo usadas para classes completas. Podendo incluir uma classe dentro de outra classe, como se fosse uma propriedade.
  * Aninhamento: a possibilidade de aninhar seletores dentro de outros seletores é um truque que me encanta muito. Porque ele criará os seletores longos por conta própria e você ficará com o trabalho de apenas construir a hierarquia a seletores por meio de aninhamento.
  * Operações: executar operações com propriedades e cores por meio do CSS é tão fora de cogitação que se torna muito surpreendente.

SASS faz tudo isso descrito acima, e faz antes de o LESS ter feito. Mas a consideração que deve ser feita é: LESS tem uma sintaxe mais simples, que leva a uma curva de aprendizagem menor, e quando essa curva atinge uma boa inclinação, ela é mais produtiva.

## Automatização

Muitas coisas precisam ser feitas, que não necessariamente são observadas, mas tem valor. Isso se aplica a tudo na vida. Montar o palco para o espetáculo, preparar e limpar as ferramentas, checar se tudo está apto para funcionamento, etc. Concatenar arquivos, minificar código, realizar o deploy, etc.

Estas tarefas podem continuar a serem feitas, mas sem o trabalho que normalmente se tem para as suas execuções. A ferramenta a ser usada neste caso é o Grunt.

Com o Grunt você pode automatizar tarefas para serem executadas via linha de comando. Basta ter o NodeJS e configurar as tarefas a serem automatizadas.

## Qualidade

Uma mágica bem feita pode ser repetida diversas vezes, e ainda causará boas impressões. Isso se deve a qualidade com que a mágica foi feita. Existe a melhor maneira de executá-la, e quando isso é feito, tudo flui muito bem. Escrever códigos javascript e css com qualidade &#8211; o que inclui boas práticas de sintaxe e construção – é um desafio, porque escrever sem boas práticas também funciona.

Para verificar a qualidade do nosso código temos: JSLint, JSHint e CSSLint.

JSLint realiza uma busca com foco em erros de sintaxe e erros estruturais.

JSHint é um fork do JSLint com uma melhoria que permite customizações, ele permite flexibilidade.

CSSLint tem o objetivo de verificar além da sintaxe a performance do CSS.

## Enfim

Cada mágico tem um conjunto de mágicas que são apresentadas. Mas todos tem o mesmo objetivo: encantar. Todo desenvolvedor precisa encantar a todos para ter seu trabalho reconhecido. Essas ferramentas, e muitas outras, podem fazer a diferença. Então faça a diferença.