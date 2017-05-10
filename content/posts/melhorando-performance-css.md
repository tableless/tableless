---
title: Performance do seu CSS
author: Diego Eis
type: post
date: 2011-03-29
excerpt: Entenda o que pode melhorar ou piorar a performance de carregamento do seu CSS.
url: /melhorando-performance-css/
tweetbackscheck:
  - 1356410056
shorturls:
  - 'a:3:{s:9:"permalink";s:50:"http://tableless.com.br/melhorando-performance-css";s:7:"tinyurl";s:26:"http://tinyurl.com/3o4yfp5";s:4:"isgd";s:19:"http://is.gd/V929jJ";}'
twittercomments:
  - 'a:8:{i:108208753198891009;s:7:"retweet";i:150278938252410881;s:7:"retweet";i:150271527382827008;s:7:"retweet";i:150271379189665793;s:7:"retweet";i:150270657513537536;s:7:"retweet";i:150270536692400129;s:7:"retweet";i:150270135515619329;s:7:"retweet";i:169583543826137088;s:7:"retweet";}'
tweetcount:
  - 13
dsq_thread_id: 503040162
categories:
  - Artigos
  - Browsers
  - Código
  - CSS
  - O Básico
  - Técnicas e Práticas
tags:
  - acessibilidade
  - Browsers
  - CSS
  - html
  - iniciantes
  - otimização
  - performance
  - tableless

---
[Modular seu código CSS][1] é uma boa prática para que o website carregue apenas o código necessário para montar a pagina que o visitante está. Por isso não precisamos carregar o código CSS que monta a página de contato uma vez que o usuário está na home, possibilitando um ganho de performance.
  
Podemos ainda melhorar um pouco mais nossa performance tendo atenção com a forma que escrevemos os seletores do CSS. Há algumas dicas que podemos seguir para que isso seja possível.

O seletor é a alma do CSS. É com ele que o browser procura e captura o elemento que você deseja formatar. Existem diversos seletores que possibilitam a captura de elementos em diversos cenários e necessidades. Com a atualizações dos browsers em relação a padronização do CSS 2.1 e do CSS 3, os desenvolvedores ganharam novos ferramentas e formas de capturar elementos.

Quero que você entenda que essas dicas são sugestões. Não seja um purista cabeça dura. Seja flexível e tolerante com alguns cenários que podem surgir durante o projeto. É bom sempre procurar o meio termo entre performance e velocidade de produção.

Outro ponto para pensar é que a má performance do CSS pode significar muito pouco perto de outros fatores como servidor, performance server-side, peso de imagens e outros fatores. Por isso é importante que você tenha em mente que fazendo as sugestões abaixo não é garantia de que seu site ficará super ultra rápido. =^)

### Processo de leitura

O browser segue um processo de leitura muito fácil de ser entendido.
  
Todo o seletorer (se voce não sabe o que é um seletor de CSS, recomendo que leia [isto][2] e [isto][3] antes de continuar).

O sistema de leitura consiste em encontrar o elemento da extrema direita do seletor. Logo a leitura do seletor começa da direita para a esquerda. A medida que o browser lê o seletor, ele vai encontrando os elementos e só pára quando há um erro no seletor ou não encontra o elemento.

Tenha como exemplo este seletor:
  
[cc lang=&#8221;CSS&#8221;]
  
ul li a {&#8230;}
  
[/cc]

Nesse primeiro momento, ao ler o elemento da direita, o browser seleciona TODOS os elementos **A** da página, independente se ele está ou não dentro de um **LI**.

“The style system matches a rule by starting with the rightmost selector and moving to the left through the rule’s selectors. As long as your little subtree continues to check out, the style system will continue moving to the left until it either matches the rule or bails out because of a mismatch.” – David Hyatt

### Não use IDs ou Classes ligados a tags

**EVITE**:
  
[cc lang=&#8221;CSS&#8221;]
  
div.content {&#8230;}
  
div#geral {&#8230;}
  
[/cc]

**RECOMENDADO**:
  
[cc lang=&#8221;CSS&#8221;]
  
.content {&#8230;}
  
#geral {&#8230;}
  
[/cc]

### Tente especificar os elementos

Sempre que puder tente especificar os elementos com IDs ou Classes em vez de escrever seletores longos.

**EVITE**:
  
[cc lang=&#8221;CSS&#8221;]
  
nav#menu ul li a {&#8230;}
  
[/cc]

**RECOMENDADO**:
  
[cc lang=&#8221;CSS&#8221;]
  
.menuitem {&#8230;}
  
[/cc]

Eu não gosto muito desta sugestão porque teríamos de colocar uma classe &#8220;menuitem&#8221; em cada um dos ítens do menu. O HTML ficaria horrível. Prefiro fazer como abaixo. Não é a melhor forma (como eu cito no próximo tópico), mas é um meio termo entre performance, flexibilidade e produção de código:

[cc lang=&#8221;CSS&#8221;]
  
#menu a {&#8230;}
  
[/cc]

### Não misture IDs com nomes de tags e classes

**EVITE**:
  
[cc lang=&#8221;CSS&#8221;]
  
button#botaoverde {&#8230;}
  
.menu#menuPrincipal {…}
  
[/cc]

**RECOMENDADO**
  
[cc lang=&#8221;CSS&#8221;]
  
#botaoverde {&#8230;}
  
#menuPrincipal {…}
  
[/cc]

### Não coloque nomes de tags nos nomes de classes

Muita gente relaciona o nome da tag ao nome da class ou id do CSS. Essa prática pode confundir posteriormente tanto na manutenção quanto no processo de produção por pelo menos dois motivos: **1.** Você pode atribuir essa classe a elementos diferentes e não somente aquele que você relacionou no nome. **2.** A classe pode fazer muito mais do que estava descrito inicialmente.
  
Por isso é interessante que cada nome de Classe seja ÚNICA e não seja relacionada a nenhum elemento em específico.

**EVITE**:
  
[cc lang=&#8221;CSS&#8221;]
  
li.selected {&#8230;}
  
[/cc]

**Bom, mas não muito**:
  
[cc lang=&#8221;CSS&#8221;]
  
.liselected {&#8230;}
  
[/cc]

**RECOMENDADO**:
  
[cc lang=&#8221;CSS&#8221;]
  
.selected {&#8230;}
  
[/cc]

### Evite seletores filhos

Sempre tente evitar declarar hierarquia nos seletores. Sempre que puder, coloque o nome do elemento diretamente por meio de class ou id. Mesmo assim tenha em mente a limpeza do seu HTML. Se você já aplicou boa parte dessas sugestões no resto do site, você pode abrir mão em alguns lugares que poderão ser úteis como na criação de um menu.

**EVITE**:
  
[cc lang=&#8221;CSS&#8221;]
  
section form#cadastro fieldset label input.Text {&#8230;}
  
[/cc]

**RECOMENDADO**:
  
[cc lang=&#8221;CSS&#8221;]
  
input[type=&#8221;text&#8221;] {&#8230;}
  
[/cc]

### Evite seletores descendentes

Os seletores descendentes são os seletores tem menos performance no CSS.

**EVITE**:
  
[cc lang=&#8221;CSS&#8221;]
  
section article h1 {&#8230;}
  
[/cc]

**É bom, mas nem tanto**:
  
[cc lang=&#8221;CSS&#8221;]
  
section > article > h1 {&#8230;}
  
[/cc]

**RECOMENDADO**:
  
[cc lang=&#8221;CSS&#8221;]
  
.tituloh1 {&#8230;}
  
[/cc]

Claro que é muito complexo colocar uma classe nos títulos do site, ainda mais se os títulos são gerados por outras pessoas. Por isso prefiro, dependendo do site, dependendo do cliente, dependendo de como eu acordar de manhã, utilizar a primeira sugestão, que está marcada para EVITAR. Lembre-se ache o meio termo.

#### Referências:

  * <a href="http://blog.archive.jpsykes.com/152/testing-css-performance-pt-2/" rel="external">Testing CSS Performance</a>
  * <a href="http://www.stevesouders.com/blog/2009/06/18/simplifying-css-selectors/" rel="external">Simplifying CSS Selectors</a>
  * <a href="http://css-tricks.com/more-on-css-selector-performance/" rel="external">More on CSS Selector Performance</a>
  * <a href="https://developer.mozilla.org/en/Writing_Efficient_CSS" rel="external">Wrinting Efficient CSS</a>

 [1]: http://tableless.com.br/modulando-o-css
 [2]: http://tableless.com.br/seletores-complexos-do-css?utm_source=Artigo%2BSeletores%2BPerformance&utm_medium=Artigo%2Btableless&utm_campaign=seletores%2Bperformance
 [3]: http://tableless.com.br/seletores-agrupados-e-encadeados?utm_source=Artigo%2BSeletores%2BPerformance&utm_medium=Artigo%2Btableless&utm_campaign=seletores%2Bperformance