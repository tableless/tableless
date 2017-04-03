---
title: Lodash ou Underscore? Talvez, nenhum!
author: Eduardo Rabelo
type: post
date: 2016-03-31
url: /lodash-ou-underscore-talvez-nenhum/
titulo_personalizado:
  - 'Lodash ou Underscore? <strong>Talvez, nenhum!</strong>'
categories:
  - Artigos
  - Código
  - JavaScript
  - Técnicas e Práticas
  - Traduções
tags:
  - JavaScript
  - Técnicas e Práticas

---
Durante os últimos anos, bibliotecas como [Underscore][1] e [lodash][2], encontraram seu espaço no cinto de utilidades de muitos programadores JavaScript.

Embora essas bibliotecas ajudem a escrever e até facilitar a sua vida em partes do seu código, não necessariamente, esse código, fica simples ou de fácil entendimento. Quem estiver lendo ou mantendo o código será obrigado a, além de conhecer a linguagem e sua biblioteca padrão, também conhecer a biblioteca de utilitários que está sendo usada.

Bibliotecas vem e vão, e todo mundo tem sua favorita. Qual é a ordem de argumentos para essa função _map()_? De qual biblioteca que essa função vem? _Underscore_ (o eterno favorito), _lodash_ (o versátil e mais rápido irmão mais novo), _Ramda_ (o primo que tem uma abordagem mais funcional, que tem todos os argumentos começando do lado direito), ou qualquer abstração legal que você encontrar hoje em dia?

Se você estiver em um time, quais bibliotecas favoritas você escolheria? E se eu te disser, que você pode escolher a biblioteca padrão do JavaScript?

Quando você escreve código usando a biblioteca padrão de funções, você está tornando ele mais fácil para usar, entender e manter futuramente (aliás, pode ser você essa pessoa, daqui uns meses, quem sabe?).

Tudo bem, pode ser que você tenha que digitar um pouco mais para atingir a mesma funcionalidade, mas, desde quando, a velocidade que escrevemos código, é o gargalo para criar e manter um bom software? 😉

> É mais fácil de recuperar uma não-abstração do que uma abstração errada &#8211; [Sebastian Markbåge][3]

É muito mais fácil refatorar código verboso com poucas abstrações, do que códigos resumidos com uma abstração errada. Quando você começa a ver os padrões no seu código, repetidos por toda a parte, é hora de abstrair, você tem uma idéia de qual abstração correta você deve fazer, e provavelmente, vai acabar criando uma que valha a pena, mesmo contando com toda a sobrecarga que toda abstração adiciona.

JavaScript está evoluindo, e as novas edições, ES2015 e ES2016 (antes conhecidas como ES6 e ES7) trazem novas possibilidades, e ferramentas como Babel, deixam isso ainda mais fácil de se usar hoje em dia. Com isso em mãos, essas bibliotecas de funções utilitárias ficam obsoletas.

Ótimos recursos para aprender mais sobre as novas funções, a página em inglês, [Learn ES2015][4] no site do Babel e o livro, em inglês, [Understanding ECMAScript 6][5], escrito pelo [Nicholas C. Zakas][6]. Aprender e utilizar todos os poderosos recursos do JavaScript te dá uma segurança futura, pois elas terão vida mais longa do que a biblioteca do momento.

Mas não estou dizendo que não há espaço para bibliotecas de utilitários. Eu só estou dizendo que muitas das funções que eram essenciais para nós sermos produtivos quando escrevíamos ES3, podem ser escritas nativamente usando os recursos padrões do JavaScript.

Talvez você não precise de _lodash_ ou _Underscore_.

## Exemplos

Esses exemplos demonstram funcionalidades do ES5.1, ES2015 e ES2016, ficaram tão simples que você não precisa de uma biblioteca externa mais.

## O que eu preciso para usá-los hoje em dia?

ES5 é suportado atualmente em todos os navegadores e no Node.js. Exemplos usando ES2015 e ES2016, podem ser compilados para ES5 usando Babel. É muito simples integrar o Babel no seu sistema, quase todas as ferramentas de automação hoje em dia, tem uma integração oficial. Se você precisar dar suporte para navegadores antigos (IE8), você pode utilizar a biblioteca [es-shim][7], que traz quase todos os polyffils para ES5.

### Arrays

#### Iteração

**Underscore**

<pre class="lang-js">_.each(array, fn)</pre>

**ES5.1**

<pre class="lang-js">array.forEach(fn)
</pre>

#### Map

**Underscore**

<pre class="lang-js">_.map(array, fn)
</pre>

**ES5.1**

<pre class="lang-js">array.map(fn)
</pre>

#### Usar uma função para acumular o valor de um array (da esquerda para a direita)

**Underscore**

<pre class="lang-js">_.reduce(array, fn, init)
</pre>

**ES5.1**

<pre class="lang-javascript">array.reduce(fn, init)
</pre>

#### Usar uma função para acumular o valor de um array (da direita para a esquerda)

**Underscore**

<pre class="lang-javascript">_.reduceRight(array, fn, init)
</pre>

**ES5.1**

<pre class="lang-javascript">array.reduceRight(fn, init)
</pre>

#### Testar se todos os elementos de um array passam em uma operação

**Underscore**

<pre class="lang-javascript">_.every(array, fn)
</pre>

**ES5.1**

<pre class="lang-javascript">array.every(fn)
</pre>

#### Testar se um dos elementos de um array passam em uma operação

**Underscore**

<pre class="lang-javascript">_.some(array, fn)
</pre>

**ES5.1**

<pre class="lang-javascript">array.some(fn)
</pre>

#### Achar um valor em um array

**Underscore**

<pre class="lang-javascript">_.find(array, fn)
</pre>

**ES2015**

<pre class="lang-javascript">array.find(fn)
</pre>

#### Pegar uma propriedade de cada elemento do array

**Underscore**

<pre class="lang-javascript">_.pluck(array, prop)
</pre>

**ES2015**

<pre class="lang-javascript">array.map(value =&gt; value[prop])
</pre>

#### Verificar se o array contém o elemento

**Underscore**

<pre class="lang-javascript">_.includes(array, el)
</pre>

**ES2016**

<pre class="lang-javascript">array.includes(el)
</pre>

#### Convertendo um objeto array-like em array

**Underscore**

<pre class="lang-javascript">_.toArray(arguments)
</pre>

**ES2015**

<pre class="lang-javascript">[...arguments]
</pre>

#### Criando uma cópia do array e removendo todos os valores falsos

**Underscore**

<pre class="lang-javascript">_.compact(array)
</pre>

**ES5.1**

<pre class="lang-javascript">array.filter(Boolean)
</pre>

**ES2015**

<pre class="lang-javascript">array.filter(x =&gt; !!x)
</pre>

#### Criando uma cópia do array e removendo itens duplicados

**Underscore**

<pre class="lang-javascript">_.uniq(array)
</pre>

**ES2015**

<pre class="lang-javascript">[...new Set(array)]
</pre>

#### Achando o index de um valor no array

**Underscore**

<pre class="lang-javascript">_.indexOf(array, val)
</pre>

**ES5.1**

<pre class="lang-javascript">array.indexOf(val)
</pre>

#### Achar o index de um valor no array baseado em uma operação

**Underscore**

<pre class="lang-javascript">_.findIndex([4, 6, 7, 12], numPrimo);
</pre>

**ES2015**

<pre class="lang-javascript">[4, 6, 7, 12].findIndex(numPrimo);
</pre>

#### Criar um array com N números, começando do X

**Underscore**

<pre class="lang-javascript">_.range(x, x + n)
</pre>

**ES2015**

<pre class="lang-javascript">Array.from(Array(n), (v, k) =&gt; k + x)
</pre>

### Objetos

#### Nomes de todas as propriedades enumeráveis do próprio objeto

**Underscore**

<pre class="lang-javascript">_.keys(object)
</pre>

**ES5.1**

<pre class="lang-javascript">Object.keys(object)
</pre>

#### Número de chaves em um objeto

**Underscore**

<pre class="lang-javascript">_.size(object)
</pre>

**ES5.1**

<pre class="lang-javascript">Object.keys(object).length
</pre>

#### Nome de todas as propriedades enumeráveis em array

**Underscore**

<pre class="lang-javascript">_.allKeys(object)
</pre>

**ES2015**

<pre class="lang-javascript">[...Reflect.enumerate(object)]
</pre>

#### Valores

**Underscore**

<pre class="lang-javascript">_.values(object)
</pre>

**ES2015**

<pre class="lang-javascript">Object.keys(object).map(key =&gt; object[key])
</pre>

#### Criar um novo objeto passando o _prototype_ e propriedades

**Underscore**

<pre class="lang-javascript">_.create(proto, prop)
</pre>

**ES2015**

<pre class="lang-javascript">Object.assign(Object.create(proto), prop)
</pre>

#### Criar um novo objeto a partir da mescla de suas propriedades

**Underscore**

<pre class="lang-javascript">_.assign({}, source, { a: false })
</pre>

**ES2015**

<pre class="lang-javascript">Object.assign({}, source, { a: false })
</pre>

**ES2016**

<pre class="lang-javascript">{ ...source, a: false }
</pre>

#### Clonando um objeto e suas propriedades (cópia não recursiva de propriedades)

**Underscore**

<pre class="lang-javascript">_.extendOwn({}, object)
</pre>

**ES2016**

<pre class="lang-javascript">{ ...object }
</pre>

#### Verificando se o dado objeto é um array

**Underscore**

<pre class="lang-javascript">_.isArray(object)
</pre>

**ES5.1**

<pre class="lang-javascript">Array.isArray(object)
</pre>

#### Verificando se o objeto é um número finito

**Underscore**

<pre class="lang-javascript">_.isNumber(object) && _.isFinite(object)
</pre>

**ES2015**

<pre class="lang-javascript">Number.isFinite(object)
</pre>

### Funções

#### Vinculando funções a novos escopos (ou _binding_)

**Underscore**

<pre class="lang-javascript">foo(_.bind(function () {
  this.bar();
}, this));
foo(_.bind(object.fun, object));
</pre>

**ES2015**

<pre class="lang-javascript">foo(() =&gt; { this.bar(); });
foo(object.fun.bind(object));
</pre>

**ES2016**

<pre class="lang-javascript">foo(() =&gt; { this.bar(); });
foo(::object.fun);
</pre>

### Utilidades

#### Funções de identidade

**Underscore**

<pre class="lang-javascript">_.identity
</pre>

**ES2015**

<pre class="lang-javascript">value =&gt; value
</pre>

#### Uma função que retorna um valor

**Underscore**

<pre class="lang-javascript">_.constant(value)
</pre>

**ES2015**

<pre class="lang-javascript">() =&gt; value
</pre>

#### Funções vazias

**Underscore**

<pre class="lang-javascript">_.noop
</pre>

**ES2015**

<pre class="lang-javascript">() =&gt; {}
</pre>

#### Pegar o valor to tempo em milisegundos

**Underscore**

<pre class="lang-javascript">_.now()
</pre>

**ES5.1**

<pre class="lang-javascript">Date.now()
</pre>

### Template

**Underscore**

<pre class="lang-javascript">var greeting = _.template("hello &lt;%= name %&gt;");
greeting({ name: 'moe' });
</pre>

**ES2015**

<pre class="lang-javascript">const greeting = ({ name }) =&gt; `hello ${name}`;
greeting({ name: 'moe' });
</pre>

## Resumindo

Cada um dos exemplos demonstra as possibilidades que os novos padrões do JavaScript traz para nosso código do dia-a-dia. Re-aprenda o JavaScript de hoje!

Se interessou pelo assunto? Quer ver mais posts desse tipo? Alguma sugestão?

Deixe sua opinião aqui nos comentários ou mande um _ping_ no [twitter][8].

Artigo traduzido e adaptado de [You Might Not Need Underscore][9] escrito por [Ville Immonen][10]

 [1]: http://underscorejs.org
 [2]: https://lodash.com
 [3]: https://twitter.com/sebmarkbage
 [4]: https://babeljs.io/docs/learn-es2015/
 [5]: https://leanpub.com/understandinges6
 [6]: https://twitter.com/slicknet
 [7]: https://github.com/es-shims/es5-shim
 [8]: https://twitter.com/oieduardorabelo
 [9]: https://www.reindex.io/blog/you-might-not-need-underscore/
 [10]: https://twitter.com/VilleImmonen