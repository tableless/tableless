---
title: 'Jasmine: entendendo os matchers'
author: Raphael Fabeni
type: post
date: 2015-03-30
excerpt: Provavelmente você já deve ter ouvido de Jasmine certo? Por acaso, você conhece todos os matchers que ele nos oferece pra testar?
url: /jasmine-entendendo-os-matchers/
categories:
  - JavaScript
tags:
  - jasmine
  - JavaScript
  - test

---
Uma parte legal do **Jasmine** e que adianta muito o nosso lado são os _matchers_: de um modo resumido e direto, um _matcher_ implementa uma comparação _booleana_ entre o valor atual e o valor esperado. É responsável em passar para o _framework_ se o que  _esperamos_ através do nosso teste é _verdadeiro_ ou _falso_. Com base nisso, o _Jasmine_ vai passar ou falhar a _spec_.

## toEqual

Esse talvez seja o mais básico e um dos que mais iremos usar. Simplemente verifica se duas coisas são iguais (e não necessariamente o mesmo objeto). Por exemplo, as seguintes _expects_ iriam passar:

<pre class="lang-js">expect(true).toEqual(true);
expect([1, 2, 3]).toEqual([1, 2, 3]);
</pre>

Da mesma forma, as seguintes iriam falhar:

<pre class="lang-js">expect(5).toEqual(12);
expect([1, 2, 3]).toEqual([11, 12, 13]);
</pre>

## toBe

O _matcher_ `toBe` a princípio parece ser igual ao anterior `toEqual`. A diferença é que `toBe` verifica não só se os dois valores são iguais, mas também como se eles são do mesmo objeto.

Pra podermos ver a diferença entre os dois:

<pre class="lang-js">var bob = { model: "Camaro" };
var john = { model: "Camaro" };

expect(bob).toEqual(john); // passa =&gt; são equivalentes
expect(bob).toBe(john); // falha =&gt; não é o mesmo objeto
</pre>

Apesar de _bob_ e _john_ serem similares, eles não são o mesmo objeto, o que faz a _spec_ passar se for usado o _matcher_ **toEqual** mas falha se for usado o _matcher_ `toBe`. O mesmo acontece para arrays:

<pre class="lang-js">var group = [100, 101, 102];
expect(group).toEqual([100, 101, 102]); // passa =&gt; são equivalentes
expect(group).toBe([100, 101, 102]); // falha =&gt; não é o mesmo array
</pre>

## toBeTruthy e toBeFalsy

Para testar se algum valor é avaliado commo **_true_** ou **_false_**, podemos usar respectivamente os _matchers_ `toBeTruthy` e `toBeFalsy`:

<pre class="lang-js">expect(true).toBeTruthy();
expect(1000).toBeTruthy();
expect({}).toBeTruthy();

expect("").toBeFalsy();
expect(null).toBeFalsy();
expect(false).toBeFalsy();
</pre>

Se pararmos pra olhar com calma o exemplo anterior podemos notar que a avaliação dos _matchers_ `toBeTruthy` e `toBeFalsy` é idêntica ao _JavaScript_. Então temos alguns valores específicos que são considerados _falsy_ e todo o restante é avaliado como _truthy_. Pra nossa referência, uma lista dos valores que são avaliados como _falsy_ pelo _Jasmine_:

* **_false_**
  
* _****_
  
* _**&#8220;&#8221;**_
  
* **_undefined_**
  
* _**null**_
  
* _**NaN**_

## not

Muitas vezes podemos inverter um _matcher_  pra termos certeza de que ele não é um valor **_true_**. Podemos fazer isso facilmente adicionando o prefixo `.not`:

<pre class="lang-js">expect('Fabeni').not.toEqual('Finelli');
</pre>

## toContain

Conseguimos também verificar se um elemento _está contido_ em um _array_ ou **_string_** por exemplo, como o _matcher_ `toContain`.

<pre class="lang-js">expect([10, 11, 12, 13, 14, 15]).toContain(13);
expect('Raphael Fabeni').toContain('Fabeni');
</pre>

## toBeDefined e toBeUndefined

Da mesma maneira que vimos os _matchers_ `toBeTruthy` e `toBeFalsy`, _Jasmine_ também nos oferece os benditos `toBeDefined` e `toBeUndefined` que verificam se um valor é **_defined_** ou **_undefined_**.

<pre class="lang-js">var iAmUndefined;
expect(null).toBeDefined(); // passa
expect('Fabeni').toBeDefined(); // passa
expect(iAmUndefined).toBeDefined(); // falha

expect(iAmUndefined).toBeUndefined(); // passa
expect(12).toBeUndefined(); // falha
expect(null).toBeUndefined(); // falha
</pre>

## toBeNull

Direto ao ponto, esse brother simplesmente avalia se um valor é **_null_**:

<pre class="lang-js">expect(null).toBeNull(); // passa
expect(false).toBeNull(); // falha
expect(1).toBeNull(); // falha
</pre>

## toBeNaN

Sem muitas delongas, esse _matcher_ verifica se um valor é **_NaN_**:

<pre class="lang-js">expect(0).toBeNaN(); // falha
expect(10).not.toBeNaN(); // passa
</pre>

## toBeGreatherThan e toBeLessThan

Esses dois _matchers_ verificam se um valor é maior ou menor que um outro valor passado.

<pre class="lang-js">expect(10).toBeGreatherThan(1); // passa
expect(10).toBeLessThan(20); // passa
</pre>

## toBeCloseTo

Esse _matcher_ permite que possamos verificar se um certo número está próximo de um outro número, dado uma certa precisão decimal como segundo argumento. Poderíamos por exemplo, verificar se um número é próximo de _25.23_ com um ponto decimal, poderíamos fazer algo assim:

<pre class="lang-js">expect(25.23).toBeCloseTo(25.2, 1); // passa
</pre>

## toMatch

Esse cara verifica se algum valor está de acordo com base em uma **_expressão regular_**.

<pre class="lang-js">expect('Yes, we can!').toMatch(/we/); // passa
</pre>

## toThrow

Esse _matcher_ permite que verifiquemos se uma função lançou um erro. Como exemplo, vamos imaginar que temos uma função `onlyNumbers` que deve **_lançar uma exceção_** caso o argumento passado seja uma _string_ e não um número. Podemos usar aqui uma _função anônima_ para nos facilitar a vida:

<pre class="lang-js">expect(function() {
    onlyNumbers('argumento errado')
}).toThrow();
</pre>

## Ufa&#8230;

Deu pra ver que o _framework_ nos oferece um monte de opção para utilizarmos em nossos testes. É ainda é possível fazer nossos _matchers_ customizados, mas vou deixar isso para um próximo post. Se você se interessar mais pelo assunto, recomendo o livro <a href="http://shop.oreilly.com/product/0636920028277.do" target="_blank">JavaScript Testing with Jasmine</a> que inclusive li recentemente e tive a idéia de escrever o post.

Acho que é isso. Se encontrar algum erro ou melhoria no post, pode postar no comentário ou pode me chamar no <a href="https://twitter.com/raphaelfabeni" target="_blank">twitter</a>.