---
title: CakePHP convenções de nomenclatura e o poderoso Inflector!
author: Lucas Macedo
type: post
date: 2015-03-19
excerpt: Entenda como funcionam as convenções de nomenclatura do CakePHP.
url: /cakephp-convencoes-de-nomenclatura-e-o-poderoso-inflector/
categories:
  - PHP
tags:
  - cakephp
  - php

---
Geralmente eu tenho problemas para encontrar os nomes corretos para os meus controllers, views, models e tabelas. Talvez a tarefa mais difícil de todo programador seja nomear as coisas. Quem nunca ficou indeciso por causa do nome de uma função ou de uma variável? Eu busco sempre permanecer o projeto todo em inglês.

Bem, **CakePHP** faz um monte de trabalho tedioso e repetitivo para você, para que você possa se concentrar melhor nas regras do negocio. Mas o CakePHP depende de você! Ele se agarrar às suas convenções de nomenclatura, por isso é importante ter atenção em nomes de **tabelas**, **controllers**, **models**..

Eu mesmo já tive diversos problemas com nomenclaturas e passei por muita dor de cabeça! Acredite.. O CakePHP espera que você converta corretamente esse problema entre singular, plural, etc 😉

As Models são singular. Ex: **BigPerson** e **ReallyBigPerson** são exemplos de nomes de modelos convencionais. Os nomes das tabelas correspondentes a model do CakePHP são plurais e sublinhado. As tabelas para as models acima mencionadas seriam **big_people**, **really\_big\_people**, respectivamente.

Aparentemente CakePHP converte substantivos irregulares corretamente e eu me pergunto: Como? Será que ela tem um look-up table enorme para todos eles? Bem, não! Em vez disso, ele faz algumas coisas muito sofisticadas em uma classe chamada **cake/libs/ inflector.php,**
  
com um monte de correspondências de regex e muito mais!

## Métodos

  * **pluralize**: Converte para o plural: Apple, Man → Apples, Men
  * **singularize**: Converte para o singular: Apples, Men → Apple, Man
  * **camelize**: Converte underscored hadron_collider → hadronCollider
  * **underscore**: Converte para underscored adronCollider → hadron_collider
  * **humanize**: Converte unserscore para stirng com Captalize devine_intervention → Devine Intervention
  * **tableize**: Converte para underscore e plural MajorFeatureThing → major\_feature\_things
  * **classify**: Converte para underscore com plural para string no singular major\_feature\_things → MajorFeatureThing
  * **variable**: Converte de underscored plural ou singular para singular e lowercase. major\_feature\_things → majorFeatureThing
  * **slug**: Converte caracteres especias/espaços em underscore de qualquer formatação. Este método é UTF-8 encoding! apple purée → apple_puree

Agora que você tem uma ideia do que o Inflector pode fazer por você, vamos explorar cada um desses métodos em detalhes.

**Inflector::pluralize();**
  
O método pluralize () recebe uma palavra no singular (string) e retorna a versão plural da mesma. Aqui estão alguns exemplos:

<pre class="lang-php">Inflector::pluralize('Apple'); // returns "Apples"
Inflector::pluralize('Menu'); // returns "Menus"
Inflector::pluralize('News'); // returns "News"</pre>

**Inflector::singularize()**
  
O método singularize() recebe uma palavra no plural (string) e retorna a versão no singular dele. Aqui estão alguns exemplos:

<pre class="lang-php">Inflector::singularize('Houses'); // returns "House"
Inflector::singularize('Bananas'); // returns "Banana"
Inflector::singularize('Men'); // returns "Man"</pre>

**Inflector::camelize ()** 

Você pode passar um método ou a ou uma palavra under_scored para o camelize () e ele
  
irá retornar esta palavra FooBar ou fooBar(se você passar false como o segundo argumento). Alguns exemplos:

<pre class="lang-php">Inflector::camelize('foo_bar'); // returns "FooBar" 
Inflector::camelize('foo_bar', false); // returns "fooBar"
</pre>

**Inflector::underscore()**
  
Este o nome já diz.
  
O método underscore () tem basicamente uma palavra e converte os espaços dela em &#8220;_&#8221; , e também converte os caracteres especiais em caracteres normais. Ex:

<pre class="lang-php">Inflector::underscore('TestField') // returns test_field
Inflector::underscore('FeineApfel') // returns feine_aepfel
</pre>

Este é o meu preferido!

**Inflector::slug()**

O método slug () recebe uma string e cria uma representação &#8220;slugged&#8221; dele.
  
Isto significa basicamente que todos os espaços serão substituídos por um determinado caractere (o padrão é &#8220;-&#8220;),
  
o que não for palavra será removido e os caracteres com acentos como &#8220;áÁéÍÓÚ&#8221; será traduzida para a sua representação ASCII.
  
Aqui estão alguns exemplos:

<pre class="lang-php">Inflector::slug('The truth - and- more- news'); // returns "the-truth-and-more-news"
Inflector::slug('!@$#exciting stuff! - what !@-# was that?'); // returns "exciting-stuff-what-was-that"
</pre>

**Inflector::humanize()** 
  
O método humanize () recebe uma palavra sublinhada, remove um determinado seperator (padrão para &#8220;_&#8221;) e uppercases os primeiros caracteres das palavras. Alguns exemplos dos testes principais:

<pre class="lang:php decode:true ">Inflector::humanize('posts'); // returns "Posts"
Inflector::humanize('posts_tags'); // returns "Posts Tags"
Inflector::humanize('file_systems'); // returns  "File Systems"</pre>

Estes são os que eu achei mais importante ..
  
Mas se você quiser ver todos os métodos veja na [documentação aqui][1].

Adicione suas próprias regras
  
Se você precisar, você pode adicionar suas próprias regras e / ou substituir regras padrão. As regras inflector::method() é responsável por isso e funciona como um setter ou getter para todas as regras armazenados. Os testes básicos proporcionam um exemplo:

<pre lang="php">Inflector::rules('singular', array('/rata/' =&gt; '\1ratus'));
</pre>

Você também pode adicionar transliterações que mapeia caracteres específicos ou acentuados de linguagem para os ASCII (que são usados ​​para criar slugs, por exemplo). Os teste no core também oferecem um bom exemplo:

<pre class="lang-php">$this-&gt;assertNotEqual(Inflector::slug('JØRGEN'), 'JORGEN');
Inflector::rules('transliteration', array('/Ø/' =&gt; 'O'));
$this-&gt;assertEqual(Inflector::slug('JØRGEN'), 'JORGEN');
</pre>

Uma boa prática é armazenar suas regras personalizadas em um arquivo de inicialização, de modo que eles estão imediatamente disponíveis para a sua aplicação quando estiver totalmente carregado.
  
Minha dica é criar dentro do arquivo Bootstrap =D ou até mesmo um helper..

Agora, vá! Vá e diga a todos os seus amigos sobre a sua nova descoberta! \o/

 [1]: http://book.cakephp.org/2.0/en/core-utility-libraries/inflector.html