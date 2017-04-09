---
title: Atribuição múltipla com Destruturing Assignment
author: Gabriel Prates
type: post
image: uploads/2017/03/pexels-photo-296983-2.jpg
date: 2017-04-02
stick: yes
excerpt: Entenda como funciona atribuições múltiplas no JS
categories:
  - Artigos
  - Código
  - Destaques
  - Tecnologia e Tendências

---


Uma coisa que me chamou muita a atenção na linguagem <a href="https://golang.org/">Go</a> foi a possibilidade de retornos múltiplos e, até mesmo, de tipos diferentes. Recentemente, vi que agora, na era pós ES6, podemos fazer algo parecido com **JavaScript**.

Vamos supor que precisamos tratar um nome, e exibi-lo como referência do determinado autor. Poderíamos fazer assim:


<pre class="lang-javascript">const ucFirst = (str) =&gt; str.charAt(0).toUpperCase() + str.substr(1);
function nomeAutor(nome) {
  let nomes = nome.split(' ');
  let ultimoNome  = nomes.pop().toUpperCase();
  let outrosNomes = nomes.map(ucFirst).join(' ');
  return `${ultimoNome}, ${outrosNomes}`;
}

nomeAutor('gabriel oliveira prates');
// PRATES, Gabriel Oliveira
</pre>


Mas e se precisarmos de ambos os nomes separados? Poderíamos criar uma função para cada uma das ações, uma para pegar o <code>ultimoNome</code>, outra para pegar os <code>outrosNomes</code>· Isso resolve, certo? Veja só:


<pre class="lang-javascript">const ucFirst = (str) =&gt; str.charAt(0).toUpperCase() + str.substr(1);
const separaNome  = (nome) =&gt; nome.split(' ');
const ultimoNome  = (nome) =&gt; separaNome(nome).pop().toUpperCase();
const outrosNomes = (nome) =&gt; {
  let nomes = separaNome(nome);
  nomes.pop();
  return nomes.map(ucFirst).join(' ');
}

let nome = 'gabriel oliveira prates';

// Observe esta atribuição
let ultimo = ultimoNome(nome);  // PRATES
let outros = outrosNomes(nome); // Gabriel Oliveira
</pre>


Apesar de modularizado e com funções que cumprem apenas uma tarefa, precisamos atribuir cada uma das variáveis ao seu respectivo valor de uma forma não tão interessante. Podemos ter um código final melhor, de leitura e entendimento, e menor. E é aqui que entramos no ponto chave deste artigo.

## O que é “Destructuring Assignment”

**Destructuring Assignment** (ou atribuição por desestruturação) é uma sintaxe de expressão que permite extrair valores de **arrays** e **objetos**, usando o lado esquerdo da atribuição (left-hand side of assignment) para definir quais valores serão extraídos. Exemplos básicos:


<pre class="lang-javascript">// Array:
let [ a, b ] = [ 'ES6', 2015 ];
console.log(a); // ES6
console.log(b); // 2015

// Objetos:
let { x, y } = { x: 'ES6', y: 2015 };
console.log(x); // ES6
console.log(y); // 2015
</pre>


Mas é claro que isso não é tudo. Então vamos lá, vamos ver alguns detalhes de cada um dos casos.

<h3>Array</h3>
Para fazer as atribuições com um array, devemos considerar a extração de valores através das posições do array. Vamos olhar de novo o exemplo do array:


<pre class="lang-javascript">// Aqui já criamos as variáveis e atribuímos valores:
let [ a, b ] = [ 'ES6', 2015 ];


// Mas poderíamos fazer o processo separado também:
let a, b;
let array = [ 'ES6', 2015 ];
[ a, b ] = array;
</pre>


É um pouco óbvio, mas no próximo tópico você vai entender o porquê de eu ressaltar isso.

Vamos supor que temos uma função que nos retorna um array com os valores da cotação do dólar nos últimos 30 dias. Vamos supor também, que precisamos dos 5 primeiros valores. Podemos usar o <code>Array.prototype.slice()</code>, mas isso nos retornaria um novo array. Então se precisarmos das variáveis separadas, seria necessário atribuir uma a uma para as 5 primeiras posições do array.

<pre class="lang-javascript">let valores = cotacaoUltimoMes();

// Antigamente
let d1 = valores[0]
let d2 = valores[1]
let d3 = valores[2]
let d4 = valores[3]
let d5 = valores[4]

// Como podemos fazer agora:
let [ d1, d2, d3, d4, d5 ] = cotacaoUltimoMes();
</pre>

A atribuição fica muito mais enxuta, consegue perceber? Percebeu que os outros 25 elementos não fazem diferença para a atribuição? Caso esses elementos sejam necessários, e for permitido colocá-los num array mesmo, podemos utilizar o <a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Functions/rest_parameters">operador rest <code>...</code></a>:

<pre class="lang-javascript">let [ d1, d2, d3, d4, d5, ...outros ] = cotacaoUltimoMes();
// `outros` será o array com o resto dos valores.
</pre>

E se precisarmos, por exemplo, dos 7 primeiros elementos, com exceção do 4º e 6º elementos, isso quebraria a lógica, certo? **ERRADO!!!** É ainda mais simples. Para cada posição que for necessária saltar, só precisamos especificá-la com os espaços em branco separados por vírgula ( <code>,</code> ). Veja:

<pre class="lang-javascript">// Espaços em branco que representam o 4º e 6º elementos
let [ d1, d2, d3, , d5, , d7 ] = cotacaoUltimoMes();
</pre>

Em algum outro caso, se tivermos um array de retorno, com o tamanho instável e for necessário garantir determinada quantidade de valores, podemos deixar valores pré-definidos na atribuição:

<pre class="lang-javascript">// v3 e v4 pré-definidos
let [ v1, v2, v3 = 1, v4 = 0 ] = retornaArray();
</pre>

Tudo certo? Ok, então vamos passar para o próximo caso.
<h3>Objetos</h3>
Para fazer as atribuições com um objeto, devemos associar as chaves, ou nomes dos atributos (propriedades) do objeto. Observe novamente o exemplo:

<pre class="lang-javascript">// Atribuição direta associando as chaves
let { x, y } = { x: 'ES6', y: 2015 };
</pre>

Podemos também fazer a atribuição indireta, como no exemplo do array, mas aqui há uma particularidade (a que eu falei “você vai entender o porquê de eu ressaltar isso”). Se você tentar executar o código abaixo, terá um erro de sintaxe:

<pre class="lang-javascript">let a, b;
let obj = { a: 'ES6', b: 2015 };
{ a, b } = obj;
</pre>

Isso porque <code>{ a, b }</code> é considerado um bloco, então realmente há um erro de sintaxe aí. Para consertar isso, devemos colocar essa operação de atribuição dentro de uma expressão, entre parênteses:

<pre class="lang-javascript">let a, b;
let obj = { a: 'ES6', b: 2015 };
({ a, b } = obj);
</pre>

Assim como na operação para array, podemos ter valores pré-definidos também:

<pre class="lang-javascript">let { a = 'JavaScript', c = 2017 } = { a: 'ES6', b: 2015 };
console.log(a); // 'ES6'
console.log(c); // 2017
</pre>

E outra coisa legal também, é que podemos jogar os valores para uma variável com um novo nome:

<pre class="lang-javascript">let { a: lang, b: ano } = { a: 'ES6', b: 2015 };
console.log(lang);  // 'ES6'
console.log(ano);   // 2015
// Nesse caso, `a` e `b` não fazem parte deste escopo
</pre>

Voltando ao primeiro exemplo deste artigo, aquele do nome do autor, podemos reescrevê-lo assim:

<pre class="lang-javascript">const ucFirst = (str) =&gt; str.charAt(0).toUpperCase() + str.substr(1);

// Vamos modificar a função do primeiro snnipet
// para retornar múltiplos resultados
function nomeAutor(nome) {
  let nomes = nome.split(' ');
  return {
    ultimoNome: nomes.pop().toUpperCase(),
    outrosNomes: nomes.map(ucFirst).join(' ')
  };
}

let { ultimoNome, outrosNomes } = nomeAutor('gabriel oliveira prates');
</pre>

Pronto! Já temos os dois valores que queríamos e podemos trabalhar com eles da forma que for necessária.
## Conclusão
Essas novas características de destructuring assignment funcionam mais como um syntax sugar, mas realmente chegam a ser úteis. O mais legal é que você pode usá-las em conjunto e adotar a solução que seu problema pedir.

Espero ter ajudado. Caso não tenha entendido alguma parte deste artigo, e dos códigos, comente abaixo, ou me mande um tweet. É sempre um prazer.

Até a próxima

(:

## Referências
<ul>
  <li><a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Destructuring_assignment">https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Destructuring_assignment</a></li>
  <li><a href="http://www.ecma-international.org/ecma-262/6.0/#sec-destructuring-assignment">http://www.ecma-international.org/ecma-262/6.0/#sec-destructuring-assignment</a></li>
</ul>