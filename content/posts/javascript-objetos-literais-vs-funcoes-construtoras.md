---
title: 'JavaScript: Objetos Literais vs. Funções Construtoras'
author: Davi Ferreira
type: post
date: 2013-06-04
excerpt: Neste artigo apresento um pouco mais sobre as duas formas disponíveis para criação de objetos em JavaScript, Objetos Literais e Construtores, suas vantagens e desvantagens.
url: /javascript-objetos-literais-vs-funcoes-construtoras/
dsq_thread_id: 1357506101
categories:
  - JavaScript
  - Técnicas e Práticas
tags:
  - funcoes
  - JavaScript
  - objetos

---
Existem duas maneiras de criar objetos JavaScript e muita gente as confunde ou acha que são a mesma coisa. No entanto, Objetos Literais e Funções Construtoras são conceitos bem diferentes e entendê-los vai fazer com que você tire melhor proveito da linguagem.

## Objetos Literais

Este é o tipo básico de objetos JavaScript. É o formato popularizado através do JSON (JavaScript Object Notation). O objeto é criado utilizando um par de chaves ({}) e suas propriedades e métodos são todos públicos. Este tipo de objeto também é chamado de objeto estático.

<pre class="lang-javascript">var tableless = {
    init: function (artigos) {
        this.artigos = artigos;
    }
};
var tableless2 = tableless;</pre>

Todo objeto literal é um objeto único e, mesmo que você armazene ele em diferentes variáveis todas apontarão para o mesmo objeto. No exemplo acima, caso você altere/adicione propriedades em qualquer uma das variáveis (tableless ou tableless2), as modificações valem para ambas.

Seu uso é recomendado em situações onde não podem existir mais de uma instância do objeto, como por exemplo, objetos de configurações do projeto ou coleções de objetos. Além disso, este tipo de notação é muito utilizado para definir o _namespace_ do seu código JavaScript.

<pre class="lang-javascript">// Objeto Literal definindo namespace
var tableless = tableless || {};
// Construtor para Artigo utilizando o namespace tableless
tableless.Artigo = function (titulo) {
    this.titulo = titulo;
};
var artigo = new tableless.Artigo('Mais um artigo sobre JavaScript');</pre>

## Construtores

Um construtor nada mais é do que uma função. Ela pode ser executada como uma função ou pode ser utilizada para instanciar um objeto utilizando a palavra reservada _new_.

(Caso você execute a função como uma chamada normal, vale realçar que o **this** dentro da função, nesse contexto, será o objeto global **window**.)

<pre class="lang-javascript">function Categoria(nome) {
    this.nome = nome;
}

var categoria = new Categoria('Livros');</pre>

Ao executar a função Categoria com **new** estamos fazendo quatro coisas:

  1. criamos um novo objeto JavaScript ({});
  2. definimos o construtor do objeto **categoria** como **Categoria** &#8211; definindo também o tipo dele (retornado no instanceof);
  3. definimos o protótipo do objeto **categoria** como **Categoria.prototype**;
  4. executamos a função **Categoria** dentro do escopo do novo objeto, criando assim uma nova instância.

Uma outra particularidade das funções construtoras é a possibilidade de criar métodos e propriedades privadas.

<pre class="lang-javascript">function Categoria(nome) {
    var totalProdutos = 0,
        self = this,
        atualizaTotalProdutos = function() {
            self.totalProdutos += 1;
        };
    this.nome = nome;
    atualizaTotalProdutos();
}</pre>

A variável **totalProdutos** e o método **atualizaTotalProdutos** só existem no escopo do objeto Categoria criado e podem ser utilizados apenas por métodos do objeto.

Aqui utilizamos um &#8220;truque&#8221; importante. Como cada função possui o seu próprio contexto e o **this** dentro do método **atualizaTotalProdutos** referencia a própria função e não o objeto Categoria precisamos armazenar o contexto do objeto dentro da variável **self**. (Outra forma seria utilizar os métodos **call** e **aply** para definir o **this** da função, mas isso é papo para outro artigo.)

Utilizando a cadeia de protótipos, podemos atualizar propriedades ou inserir novos métodos em objetos criados a partir de funções construtoras.

<pre class="lang-javascript">Categoria.prototype.exibeProdutos = function () {
    var html = '',
        i;
    for (i = 0; i &lt; this.produtos.length; i++) {
        html += this.produtos[i].nome;
    }
    return html;
};</pre>

O código acima adiciona o método **exibeProdutos** ao protótipo de Categoria e também a todos os objetos da cadeia, instanciados ou não. 

As funções construtoras, portanto, são ideais para objetos que podem existir como múltiplas instâncias no mesmo contexto.

Uma observação: para melhor organizar seu código uma boa prática é utilizar a primeira letra maiúscula nos nomes de funções construtoras, diferenciando-as de funções comuns.

&#8212;

Entender conceitos de orientação a objetos em JavaScript pode levar um pouco de tempo e pode parecer bem estranho no início. Mas, uma vez entendido o funcionamento desses conceitos você descobrirá que é possível fazer diversas coisas legais e diferentes e que JavaScript é uma linguagem extremamente flexível.