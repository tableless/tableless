---
title: Quando utilizar (ou não) frameworks CSS
author: Talita Pagani
type: post
date: 2011-09-01
excerpt: A utilização de frameworks HTML e/ou CSS ainda é um assunto que divide a opinião dos desenvolvedores.
url: /quando-utilizar-ou-nao-frameworks-css/
tweetbackscheck:
  - 1356390913
shorturls:
  - 'a:3:{s:9:"permalink";s:31:"http://tableless.com.br/?p=4048";s:7:"tinyurl";s:26:"http://tinyurl.com/44fc9b6";s:4:"isgd";s:19:"http://is.gd/KfsGvd";}'
twittercomments:
  - 'a:0:{}'
dsq_thread_id: 503040382
categories:
  - Artigos
  - Código
  - CSS
  - CSS3
  - HTML
  - HTML5
  - Wordpress
tags:
  - CSS
  - css layout
  - frameworks
  - modularizacao css
  - tecnicas css

---
Framework é um conjunto de componentes que provêm uma estrutura básica de elementos reutilizáveis, tendo uma arquitetura consistente de funcionalidade genérica sob a qual a aplicação será construída.

No caso de CSS, os frameworks constituem bibliotecas que visam permitir a codificação do CSS de modo mais fácil e compatível com padrões de estilos, agregando uma série de opções já prontas para projetar uma página web, como se fosse um esqueleto, reduzindo o tempo gasto com o desenvolvimento.

Os frameworks CSS geralmente apresentam definições de formatação os elementos mais comuns de uma página: formulários, cabeçalhos, estilos de textos e imagens. Alguns apresentar opções para a estruturação do conteúdo baseado em _grids_.

A utilização de frameworks HTML e/ou CSS ainda é um assunto que divide a opinião dos desenvolvedores, pois muitos consideram o framework como uma **solução pronta** e acreditam que ele tira o trabalho das mãos do designer/desenvolvedor e faz com que ele não aprimore os seus conhecimentos.

**Será que você, sem perceber, nunca criou o seu próprio framework?** Pense em um arquivo CSS padrão (além do _reset_) que você criou para melhorar a produtividade de seus projetos.

É importante esclarecer que o uso de frameworks **não substitui** a necessidade do designer/ desenvolvedor de desenvolver o CSS do site. Ele apenas fornece uma base para a formatação de elementos comuns e otimiza o trabalho repetitivo.

## Para quem os frameworks são recomendados

Utilizar um framework CSS não é uma prática recomendada para quem está começando, principalmente por privar a pessoa da prática e do conhecimento sobre o funcionamento do CSS. Além disso, se ela não compreender bem CSS, poderá ter problemas para resolver problemas de layout causados por incompatibilidade entre o framework e um código CSS específico que ela inseriu.

Portanto, é recomendável que frameworks sejam utilizados por quem possui um nível razoável de conhecimento e compreensão do código, mas tem a intenção de otimizar parte do trabalho com o uso de um framework. E isto serve não apenas para quem pretende utilizar um framework CSS, mas também qualquer tipo de framework.

## Quando é interessante utilizar?

  * Prototipação rápida em HTML
  * Sites de larga escala e com estruturas similares (como portais, blog/sites no estilo magazine)
  * Sites construídos através de plataformas de CMS
  * Projetos que tenham prazos curtos
  * Projetos realizados em equipe onde há diversas pessoas trabalhando no mesmo CSS, podendo ter um conjunto consistente de padrões de codificação

### Vantagens

  * Padronização de código entre a equipe de desenvolvimento;
  * Arquivos modularizados;
  * Flexibilidade de estilos, classes genéricas que podem ser combinadas de diversas formas nos elementos da página;
  * Geralmente já possuem uma documentação, que pode ser consultada pela equipe em caso de dúvida ou necessidade de solucionar algum problema;
  * Compatibilidade cross-browser (na maioria dos casos);
  * Você pode melhorar suas habilidades estudando o framework;
  * Redução de tempo: o desenvolvedor/designer pode se concentrar mais nos aspectos particulares do site desenvolvido, pois a base está assegurada e não precisa desenvolvê-la do zero;
  * Reduz futuros esforços de manutenção caso seja necessário resposicionar elementos ou alterar características de renderização (fonte, margens, etc) em diversos elementos.

### Desvantagens

  * Quantidade excessiva de modificações que devem ser feitas para adaptar o framework;
  * O framework pode conter códigos irrelevantes que nunca serão utilizados no projeto e serão carregados sem necessidade, podendo diminuir o desempenho da página;
  * Nem sempre o código é bem organizado;
  * Muitos frameworks apresentam classes pouco semânticas (ex.: span-5).

## Algumas dicas para melhorar o uso do framework

Como as classes geralmente não apresentam muita semântica, procure colocar IDs significativos nos elementos da página, quando possível.

Você também pode optar por utilizar somente uma parte do framework. Em projetos em que utilizei o <a title="Blueprint CSS" href="http://www.blueprintcss.org/" target="_blank">Blueprint CSS</a>, muitas vezes utilizava apenas algumas folhas de estilos do framework que se adequavam ao que eu necessitava.

**Dica:** evite usar vários frameworks CSS em um mesmo projeto. Isto quebra a ideia de consistência, uma vez que cada framework tem o seu padrão de estruturação.

## Como escolher o framework?

  * Verificar se é realmente necessário o uso de um framework CSS no projeto;
  * Avaliar se o código do framework escolhido tem uma estrutura e organização;
  * Avaliar se há código excessivo que nunca será utilizado;
  * Conferir se há uma boa documentação;
  * Verificar se os recursos do framework são adequados ao que você necessita para o projeto. Não adianta utilizar um framework CSS focado em renderização quando seria mais útil um framework de grid.

Frameworks CSS, se bem utilizados, podem trazer muitos benefícios para seus projetos, basta saber como explorar o potencial que eles possuem 😉

### Referências

Why you should NOT use a web framework &#8211; <http://checkedexception.blogspot.com/2010/04/why-you-should-not-use-web-framework.html>

To use a framework, or not to: that is the question &#8211; <http://www.phparch.com/2010/04/to-use-a-framework-or-not-to-that-is-the-question/>

Please do not Use CSS Frameworks &#8211; <http://mondaybynoon.com/2007/08/27/please-do-not-use-css-frameworks/>

Which CSS Grid Framework Should You Use for Web Design? &#8211; <http://net.tutsplus.com/tutorials/html-css-techniques/which-css-grid-framework-should-you-use-for-web-design/>

When to use CSS framework? &#8211; <http://www.vcarrer.com/2008/08/when-to-use-css-framework.html>

WHAT’S NOT TO LOVE ABOUT CSS FRAMEWORKS? &#8211; <http://jeffcroft.com/blog/2007/nov/17/whats-not-love-about-css-frameworks/>

Frameworks for Designers &#8211; <http://www.alistapart.com/articles/frameworksfordesigners>