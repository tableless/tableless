---
title: Templates client-side com Mustache.js
author: Davi Ferreira
type: post
date: 2013-04-15
excerpt: 'Mustache é uma especificação de templates que não utiliza lógica, ou seja, não possui declarações com <em>if</em>, <em>for</em>, <em>while</em> etc, toda sua construção é baseada em tags. Aprenda a implementar este tipo de template em seus projetos.'
url: /templates-client-side-com-mustache-js/
dsq_thread_id: 1210128019
categories:
  - Código
  - JavaScript
tags:
  - JavaScript
  - mustache
  - template

---
Antes de começarmos, uma pergunta: quem nunca implementou um &#8220;template&#8221; nos moldes do código abaixo?

<pre class="lang-javascript">html  = '&lt;li class="clearfix"&gt;';
html += ' &lt;div class="foto"&gt;';
html += '   &lt;a href="' + item.permalink + '"&gt;';
html += '     &lt;img src="' + item.thumb + '" width="180" height="124" alt="' + item.titulo + '"&gt;';
html += '   &lt;/a&gt;';
html += ' &lt;/div&gt;';
html += ' &lt;span&gt;';
html += item.titulo;
html += ' &lt;/span&gt;';
html += '&lt;/li&gt;';</pre>

Se você ainda faz isso, chegou a hora de parar.

Neste artigo abordaremos a [implementação JavaScript para templates Mustache][1]. A sintaxe já foi portada para diferentes linguagens, incluindo Ruby, Python, PHP e Java. Para uma lista completa, visite o [site oficial do projeto][2].

A principal diferença do Mustache para outras formas de templating no client-side ([jQuery Template][3], por exemplo) é que ele não aceita lógica, como declarações condicionais, loops etc. Pode não parecer, mas isso é muito bom: um template não deveria conter nenhuma lógica, já que é apenas uma camada de apresentação.

Por ser &#8220;logic-less&#8221;, o Mustache.js é bem enxuto, pesando 8.5kb em sua versão minificada.

## Criando um template

Os templates Mustache esperam receber dados no formato JSON. Os dados podem ser textos, variáveis e até mesmo funções. Vamos começar com um exemplo básico onde renderizamos um template de um artigo.

<pre class="lang-javascript">var item = {
      titulo: "Templates client-side com Mustache.js",
      permalink: "http://tableless.com.br/templates-client-side-com-mustache-js"
      thumb: "mustache.jpg",
    },
    output = Mustache.render("&lt;h1&gt;{{title}}&lt;/h1&gt;&lt;p&gt;{{abstract}}&lt;/p&gt;", item);
console.log(output);</pre>

O método **render** é o responsável por retornar o template com os dados formatados. O primeiro parâmetro é o template e o segundo o objeto JSON com os dados que devem ser aplicados.

Os dados armazenados no JSON são representados no template utilizando duas chaves (bigode-bigode) com o nome da propriedade.

Uma boa prática é separar o template do seu código JavaScript armazenando a estrutura do template em uma tag **script** do tipo **&#8220;text/template&#8221;**.

<pre class="lang-html">&lt;script id="item-template" type="text/template"&gt;
&lt;li class="clearfix"&gt;
  &lt;div class="foto"&gt;
    &lt;a href="{{ item.permalink }}"&gt;
      &lt;img src="{{ item.thumb }}" width="180" height="124" alt="{{ item.titulo }}"&gt;
    &lt;/a&gt;
  &lt;/div&gt;
  &lt;span&gt;{{ item.titulo }}&lt;/span&gt;
&lt;/li&gt;
&lt;/script&gt;</pre>

Os dados do template são utilizados buscando o conteúdo HTML da tag.

<pre class="lang-javascript">var item = {
      titulo: "Templates client-side com Mustache.js",
      permalink: "http://tableless.com.br/templates-client-side-com-mustache-js"
      thumb: "mustache.jpg",
    },
    template = document.getElementById('article-template').innerHTML;
    output = Mustache.render(template, item);
console.log(output);</pre>

Nos exemplos a seguir, para facilitar a leitura, vamos continuar utilizando os templates diretamente no método **render** do Mustache.

## Lógica?

É verdade que não existem tags para condicionais e loops, mas sua implementação é possível utilizando caracteres especiais nas tags do template. 

No exemplo abaixo temos um objeto tableless que armazena um conjunto de artigos. Para realizarmos um loop nos artigos, basta utilizar o caractere &#8216;#&#8217; seguido do nome da propriedade como uma tag do nosso template. Dentro do bloco **#artigos** temos acesso às propriedades de cada artigo.

<pre class="lang-javascript">var tableless = {
      'artigos': [
        { 'titulo': 'Templates client-side com Mustache.js' },
        { 'titulo': 'Zepto.js: JavaScript peso-leve' },
        { 'titulo': 'JavaScript: o que fazer e aprender para se tornar um dev melhor?' }
      ]
    },
    output = Mustache.render('{{#artigos}}&lt;li&gt;{{titulo}}&lt;/li&gt;{{/artigos}}', tableless);
console.log(output);</pre>

A lógica de condicionais é tratada no próprio objeto. Assim como o loop acima, basta adicionarmos o caracatere &#8216;#&#8217; a uma variável booleana para exibir ou não um conteúdo de acordo com o valor da mesma:

<pre class="lang-javascript">var tableless = {
      'artigos': [
        { 'titulo': 'Templates client-side com Mustache.js', publicado: true },
        { 'titulo': 'Zepto.js: JavaScript peso-leve', publicado: true },
        { 'titulo': 'JavaScript: o que fazer e aprender para se tornar um dev melhor?', publicado: false }
      ]
    },
    output = Mustache.render('{{#artigos}}{{#publicado}}&lt;li&gt;{{titulo}}&lt;/li&gt;{{/publicado}}{{/artigos}}', tableless);
console.log(output);</pre>

## Funções

As tags podem conter funções como valores. Por exemplo, no objeto abaixo, a função buzz soma a quantidade de likes, tweets e comentários de um artigo.

<pre class="lang-javascript">var artigo = {
    'titulo': 'Templates client-side com Mustache.js',
      'likes': 32,
    'tweets': 22,
      'comentarios': 45,
    'buzz': function () {
      return this.likes + this.tweets + this.comentarios;
    }
  },
  output = Mustache.render('&lt;h1&gt;{{titulo}} &lt;small&gt;{{buzz}}&lt;/small&gt;&lt;/h1&gt;', artigo);
console.log(output);</pre>

Quando o valor de uma tag é representado por uma função e o caractere &#8216;#&#8217; é utilizado, a mesma pode retornar uma outra função que recebe dois parâmetros: o texto do bloco do template e uma versão especial do método render para ser executada no contexto do bloco.

<pre class="lang-javascript">var artigo = {
    'titulo': 'Templates client-side com Mustache.js',
    'url': 'http://tableless.com.br/templates-client-side-com-mustache-js',
    'permalink': function () {
      return function (text, render) {
        return '&lt;a href="' + this.url + '" class="permalink"&gt;' + render(text) + '&lt;/a&gt;';
      }
    }
  },
  output = Mustache.render('&lt;p&gt;{{#permalink}}{{titulo}}{{/permalink}}&lt;/p&gt;', artigo);
console.log(output);</pre>

Esse tipo de função é chamado de helper, podendo conter lógicas exclusivas da view e evitando a repetição de trechos de template comuns.

## Parciais

Outra maneira de evitar repetição é utilizando templates parciais. Parciais são referenciados com o caractere &#8216;>&#8217; dentro da tag.

<pre class="lang-javascript">var tableless = {
      'artigos': [
        { 'titulo': 'Templates client-side com Mustache.js' },
        { 'titulo': 'Zepto.js: JavaScript peso-leve' },
        { 'titulo': 'JavaScript: o que fazer e aprender para se tornar um dev melhor?' }
      ]
    },
    parciais = {'artigo': '

<li>
  {{titulo}}
</li>'},
    output = Mustache.render('{{#artigos}}{{&gt;artigo}}{{/artigos}}', tableless, parciais);
console.log(output);</pre>

Os templates parciais devem ser informados como terceiro parâmetro do método **render** e seu valor deve ser um objeto contendo um ou mais templates. A chave informada no objeto é o nome da tag que será utilizada no template principal.

## E tem mais

Além das funcionalidades apresentadas neste artigo, a biblioteca Mustache.js ainda trás alguns outros benefícios como templates compilados, delimitadores personalizados e seções invertidas. Para saber mais, visite a [página do projeto no GitHub][1].

E você? Utiliza alguma solução de templating no client-side? Compartilhe nos comentários!

 [1]: https://github.com/janl/mustache.js/
 [2]: http://mustache.github.com/
 [3]: http://tableless.com.br/templates-e-jquery-parte-1/ "http://tableless.com.br/templates-e-jquery-parte-1/"