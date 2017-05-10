---
title: O dilema da sintaxe no HTML5
author: Talita Pagani
type: post
date: 2012-01-11
excerpt: Fechar ou não as tags? Colocar os valores de atributo entre aspas? Estas escolhas nem sempre podem ser uma questão de gosto.
url: /o-dilema-da-sintaxe-no-html5/
tweetbackscheck:
  - 1356396946
shorturls:
  - 'a:3:{s:9:"permalink";s:31:"http://tableless.com.br/?p=5130";s:7:"tinyurl";s:26:"http://tinyurl.com/7pfyan7";s:4:"isgd";s:19:"http://is.gd/QeyzS7";}'
twittercomments:
  - 'a:0:{}'
dsq_thread_id: 534832523
categories:
  - HTML
  - HTML5
tags:
  - elementos html
  - html5
  - melhores práticas
  - sintaxe

---
Com o HTML5, a sintaxe volta a ser aquela do HTML, sem as restrições preconizadas pelo XHTML (todas as tags com fechamento, tags e propriedades em minúscula, valores de propriedades entre aspas, etc). E os desenvolvedores voltaram a se sentir livres para codificar o HTML da forma que lhes é mais conveniente.

Bom, não é bem assim. Embora o XHTML fosse frustrante com relação à semântica e não era tão revolucionário quanto propunha, as regras mais rígidas de sintaxe foram seu maior legado. O código escrito era consistente e, se não seguisse as regras, não iria renderizar corretamente no navegador. Além disso, era compreensível para qualquer desenvolvedor. É uma questão de organização e padronização, como uma diretriz que normatiza o comportamento dos elementos para que haja qualidade e consistência.

Pense nas linguagens que você conhece, tanto de programação, quanto de marcação, estilo, etc. Por exemplo: PHP, CSS, XML, JS.  Todas possuem regras de sintaxe que, se não forem seguidas, o código não funcionará. Quem programa em PHP sabe que se esquecer um único ponto-e-vírgula, compromete a interpretação de todo o código. O JS, apesar da flexibilidade com relação a o ponto-e-vírgula no final da linha, é _case sensitive_, ou seja, há diferença entre o que é escrito em maiúsculas e minúsculas.

Em grande parte das linguagens existentes, há uma sintaxe a ser respeitada e esta serve para que o código seja bem formado e tenha uma estruturação lógica, definindo um sentido para a interpretação do código. Basta remetermos ao significado original de sintaxe, que herdamos da linguística:

> A sintaxe é a parte da gramática que estuda a disposição das palavras na frase e das frases no discurso, incluindo a sua **relação lógica**, entre as múltiplas combinações possíveis para transmitir um **significado completo e compreensível**. [&#8230;] É o ramo que estuda os processos generativos ou combinatórios das frases das línguas naturais, tendo em vista **especificar a sua estrutura interna e funcionamento**.
> 
> Fonte: <http://pt.wikipedia.org/wiki/Sintaxe> (grifo nosso)

E no HTML5 nada impede que você use a sintaxe do XHTML, portanto, continuar mantendo as principais características de sintaxe do XHTML no HTML5 (uma prática que muitos chamam de XHTML5), para manter um formato consistente de codificação. É como realizar um _merge_ entre as duas linguagens.

Algumas práticas recomendadas:

  * Utilizar todos os elementos e atributos em minúsculas;
  * Incluir tag de abertura de fechamento para as tags que possuem conteúdo (no caso de tags órfãs, como <img>, <input>, <meta>, isto não fica tão grosseiro se for escrito com a sintaxe do HTML);
  * Inserir todos os valores de propriedades entre aspas duplas;

&nbsp;

## Artigos relacionados

[HTML5 syntax guidelines][1]

[My preferred syntax style for HTML5 markup][2]

 [1]: http://www.456bereastreet.com/archive/201011/html5_syntax_guidelines/
 [2]: http://www.impressivewebs.com/html5-syntax-style/