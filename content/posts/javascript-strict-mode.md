---
title: JavaScript Strict Mode
author: Fabiano de Lima Abreu
type: post
date: 2014-07-17
excerpt: "Como funciona o 'use strict' no JavaScript e saiba como ele pode ajudá-lo."
url: /javascript-strict-mode/
dsq_thread_id: 2850931825
categories:
  - JavaScript
tags:
  - JavaScript
  - strict mode

---
## O que é e porque usá-lo

**ECMAScript5** introduziu o **&#8220;use strict&#8221;**, que basicamente faz o browser interpretar o código JavaScript no modo mais rigoroso. Quando usamos o JS em strict mode, o browser mostra os erros que antes eram silenciados, como utilizar uma variável que não foi declarada, utilizar palavras reservadas no código, ou utilizar recursos da linguagem que já foram declarados obsoletos e até mesmo, proibindo o uso de partes da linguagem que são tidas como problemáticas, nos forçando a escrever um código de melhor qualidade e ajudando a capturar bugs mais precocemente. Sem habilitarmos o modo restrito, o código abaixo é executado sem lançar qualquer excepção, ainda que seja uma má prática utilizar a variável “nome” sem declará-la:

<pre class="lang-javascript">function minhaFuncao() {
    nome = "Caio Proiete";
    // ...
 } 
 minhaFuncao();
</pre>

Se habilitarmos o strict mode, será lançada uma excepção para notificar que temos um problema no código:

<pre class="lang-javascript">function minhaFuncao() {
    "use strict";
 
    // 0x800a13b2 - JavaScript runtime error: Variable undefined in strict mode
    nome = "Caio Proiete";
    // ...
}

minhaFuncao();
</pre>

## Habilitando

Podemos habilitar o modo restrito em diferentes âmbitos: A primeira forma é a nível de arquivo. Para isso, basta por a string `"use strict";` no começo de um arquivo JS para que todo o código deste arquivo seja executado no modo restrito. Nenhum código pode vir antes da declaração &#8220;use strict&#8221;; (apenas whitespace e comentários são permitidos). Caso um trecho de código apareça antes, o modo restrito não é disparado.

<pre class="lang-javascript">// código "strict"
 "use strict";
 var foo = "bar";

 // código "não strict"
 var whatsUp = "suuup";
 "use strict";

</pre>

A outra forma de uso é a nível de função. Quando usado dentro de uma função, apenas o código dentro dela é executado no modo restrito. Todo o código externo continua a ser executado normalmente.

<pre class="lang-javascript">function foo() {
  "use strict";
  // código da função em modo "strict"
}

function bar() {
  // código da função em modo "não strict"
}
</pre>

Hoje é muito comum concatenarmos arquivos para diminuir a quantidade de dados trafegados e o número de requisições. Para não disparar o modo restrito em código que não foi testado neste modo, é interessante deixarmos o código que roda e foi testado para rodar no modo restrito isolado. As funções de invocação imediata são perfeitas para isso.

<pre class="lang-javascript">// código no modo "não strict"
(function() {
  "use strict";
  // código no modo "strict"
}());
// código no modo "não strict"
</pre>

## O que muda?

O _strict mode _trouxe várias mudanças na forma de como o JavaScript é executado. Mas vou focar nas principais partes. Caso queira descer mais ainda na toca do coelho, o artigo do_ _<span style="text-decoration: underline"><a style="color: #666666;text-decoration: underline" href="http://dmitrysoshnikov.com/ecmascript/es5-chapter-2-strict-mode/">Dmitry Soshnikov</a> é uma ótima leitura sobre todos os detalhes das mudanças que o <em>strict mode</em> trouxe.</p> 

<h3 id="remoo_do_with">
  Remoção do <em>with</em>
</h3>

<p>
  A tão mal compreendida declaração <em><code>with</code></em><em> </em>foi removida da linguagem. No <strong><em>strict mode</em></strong> seu uso gera um erro de sintaxe.
</p>

<pre class="lang-javascript">"use strict";
// gera um erro de sintaxe no "strict mode"
with (location) {
  console.log(href);
}
</pre>

<h3 id="declarao_implcita_de_variveis_globais">
  Declaração implícita de variáveis globais
</h3>

<p>
  Um dos erros mais comuns em JavaScript. Sem o <em>strict mode</em>, uma nova variável global é criada sempre que atribuímos um valor a uma variável não declarada. No modo restrito, isto gera um erro.
</p>

<pre class="lang-javascript">// gera um erro no "strict mode"
(function() {
  "use strict";
  variavelNaoDeclarada = 'foo';
}());
</pre>

<h3 id="restrio_de_nomes">
  Restrição de nomes
</h3>

<p>
  O modo restrito impõe uma série de restrições aos nomes de variáveis, funções e parâmetros. <code>eval</code> e <em><code>arguments</code></em><em> </em>não mais podem ser usados como identificadores, muito menos tentar atribuir um valor a eles. O que é muito bom, uma vez que o JavaScript possui nativamente uma função <code>eval</code> e um objeto <em><code>arguments</code></em>.
</p>

<pre class="lang-javascript">// gera um erro de sintaxe no "strict mode"
function() {
  "use strict";
  arguments = 'foo';
}
</pre>

<p>
  Algumas palavras também são proibidas de serem usadas como identificadores pois são candidatas a serem usadas como nomes de futuras <em>features</em> da linguagem. Entre elas estão:
</p>

<ul>
  <li>
    implements
  </li>
  <li>
    interface
  </li>
  <li>
    let
  </li>
  <li>
    package
  </li>
  <li>
    private
  </li>
  <li>
    protected
  </li>
  <li>
    public
  </li>
  <li>
    static
  </li>
  <li>
    yield
  </li>
</ul>

<h3 id="uso_do_this">
  Uso do this
</h3>

<p>
  O uso do <code>this</code> foi levemente modificado. Quando usado dentro de uma função, o <code>this </code>aponta para o objeto que contem a função. Porém quando a função não pertence a um objeto específico, ele aponta para o objeto global <code>window</code>.
</p>

<p>
  No modo restrito, caso o <code>this</code> seja usado em uma função que é definida no escopo global, ele retorna o valor <code>undefined</code>. Caso uma função pertença a um objeto, ele continua a apontar para o objeto, como acontecia anteriormente.
</p>

<pre class="lang-javascript">// retorna "undefined"
function() {
  "use strict";
  return this;
}
</pre>

<p>
  Isso evita erros comuns com funções usadas como construtores. No código abaixo chamamos uma função construtora sem o uso do <code>new</code>. No modo não restrito, o <code>this </code>apontaria para <code>window</code> e uma variável global <code>nome</code> seria criada. Como no <em>strict mode</em> o <code>this</code> retorna <code>undefined</code>, e não podemos adicionar propriedades a<code>undefined</code>, um erro é gerado. Quando usado da forma apropriada, com o <code>new</code>, nenhum erro é disparado.
</p>

<pre class="lang-javascript">"use strict";

function Blog(nome) {
  this.nome = nome;
}

// gera um erro no "strict mode"
var blog = Blog('Loop Infinito');
</pre>

<h3 id="parmetros_e_propriedades_duplicadas">
  Parâmetros e propriedades duplicadas
</h3>

<p>
  O JavaScript não reclama caso você declare duas propriedades de um objeto com o mesmo nome. A última declaração vai simplesmente sobrescrever a anterior. O modo restrito força o uso de nomes únicos de propriedades.
</p>

<pre class="lang-javascript">"use strict";

// gera um erro de sintaxe no modo strict
obj = {
  foo: 1,
  bar: 2,
  foo: 3
}
</pre>

<p>
  Com o nome de parâmetros temos um cenário parecido. Normalmente o JavaScript aceita como sintaxe válida a declaração de parâmetros com o mesmo nome. No modo restrito isso gera um erro de sintaxe.
</p>

<pre class="lang-javascript">// gera um erro de sintaxe
function foo(param1, param1) {
  "use strict";
  return param1 + 1;
}
</pre>

<h3>
  Variáveis do contexto <em>eval()</em>
</h3>

<p>
  O <code>eval</code>, em código não <em>strict</em>, pode adicionar variáveis ao contexto em que ele está inserido. E antes do <abbr title="JavaScript Object Notation">JSON</abbr> ser nativamente implementado nos <em>browsers</em>, o <code>eval</code> era muito usado para construir objetos a partir de <em>strings</em> e os inserir no contexto externo ao <code>eval</code>.
</p>

<p>
  Com o <em>strict mode</em>, o <code>eval</code> não pode mais adicionar variáveis fora de seu contexto. Variáveis adicionadas no <code>eval</code> ficam contidas no contexto do <code>eval</code>. No código abaixo, sem o <em>strict mode</em>, seria inserido uma variável <code>foo</code> e o valor do <code>alert</code> seria “bar”. No <em>strict mode </em>acontece um erro de sintaxe pois a variável não foi definida.
</p>

<pre class="lang-javascript">"use strict";
eval('var foo="bar";');
alert(foo); // gera um erro de sintaxe no "strict mode"
</pre>

<h3 id="nmeros_no_sistema_octal">
  Números no sistema octal
</h3>

<p>
  Números no sistema octal são números representados na base 8. Ou seja, 10 em octal equivale a 8 em decimal. Em JavaScript, e em várias outras linguagens, os números no sistema octal são representados com um 0 na frente do número. 023 em JavaScript equivale a 19 em decimal. Isso gerava muita confusão, já que muitos achavam que um zero a esquerda não iria fazer nenhuma diferença na representação do número.
</p>

<pre class="lang-javascript">"use strict";

// gera um erro de sintaxe no modo strict
var foo = 023;
</pre>

<p>
  No modo restrito o uso de números no sistema octal não é permitido. Caso um 0 seja posto na frente de um número octal válido, será gerado um erro de sintaxe. Caso contrário ele será simplesmente tratado como decimal.
</p>

<pre class="lang-javascript">"use strict";

// octal válido. gera erro de sintaxe no "strict mode"
var foo = 023;

// ocatal não válido. é tratado como decimal
var bar = 08;
</pre>

<p>
  Como o número 08 não é um número octal válido, já que números no sistema octal vão de 0 a 7, ele é tratado como um número decimal. No caso do número 023, por ser um octal válido, um erro de sintaxe é gerado. Caso você não saiba o que um octal é, ande pela sombra evitando o uso de 0’s na frente de números.
</p>

<h2>
  Suporte
</h2>

<p>
  O <em>strict mode</em> pode ser usado sem medo em todos os navegadores. Caso um navegador que não o implemente passe pela declaração <code>"use strict";</code>, ele irá tratá-la como uma <em>string</em> e não irá afetar o comportamento do código seguinte.
</p>

<p>
  O cenário contrário também é compatível. Caso você desenvolva JavaScript em modo restrito em um navegador que o implementa, o código válido no modo restrito deste navegador é retrocompatível com qualquer outro que implemente o ECMAScript 3. Ou seja, irá rodar até no IE. 😀 haha
</p>

<p>
  De qualquer forma, você pode ter acesso a lista de compatibilidade do &#8220;use strict&#8221; junto aos navegadores, no no seguinte link: <a href="http://caniuse.com/use-strict">CanIUse</a>
</p>

<h2>
  Concluindo
</h2>

<p>
  O Modo restrito além de melhorar a legibilidade e estabilidade do seu código, ajuda a diminuir erros e ainda melhora a segurança associada à execução do código.Seu suporte é muito amplo e mesmo que não seja suportado não irá atrapalhar em nada na execução do código, ou seja, não há motivos para não utiliza-lo.
</p>

<p>
  Espero que tenham gostado do artigo.
</p>

<p>
  Dúvidas, criticas, sugestões&#8230; nos comentários 😉
</p>

<h2>
  Referências
</h2>

<ul>
  <li>
    <a href="http://www.nczonline.net/blog/2012/03/13/its-time-to-start-using-javascript-strict-mode/">Nicholas C. Zakas. It’s time to start using JavaScript strict mode</a>
  </li>
  <li>
    <a href="http://loopinfinito.com.br/2013/07/16/javascript-strict-mode/">Caio Gondim. JavaScript Strict Mode. Lopinfinito</a>
  </li>
  <li>
    <a href="http://tutsmais.com.br/blog/javascript-2/o-que-e-o-mode-strict-dojavascript/">Rodrigo Nery. O que é o Mode Strict no JavaScript.</a>
  </li>
</ul>