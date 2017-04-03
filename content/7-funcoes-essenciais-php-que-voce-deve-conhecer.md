---
title: 7 funções essenciais do PHP que você deve conhecer
author: Adriano dos Santos Júnior
type: post
date: 2015-07-03
excerpt: Arranjos, datas, laços e outras práticas para facilitar a programação.
url: /7-funcoes-essenciais-php-que-voce-deve-conhecer/
categories:
  - Back-end
  - Código
  - O Básico
  - PHP
tags:
  - php

---
## range()

Geralmente ao se fazer um &#8220;_loop_&#8220;, utiliza-se o _while _ou _for_. Ambas estruturas são ligeiramente &#8220;_feias_&#8221; ao visualizar o código. Uma boa alternativa é utilizar o _foreach_. Mas como fazer uma repetição, se o _foreach_ trabalha com um _array_ existente?

No exemplo vamos fazer um _loop_ de 5 posições, começando do número 1.

<pre class="lang-php">&lt;?php
foreach (range(1,5) as $ordem)
{
     print('Ordem : '.$ordem.'&lt;br&gt;');
}
//Resultado
//Ordem: 1
//Ordem: 2
//Ordem: 3
//Ordem: 4
//Ordem: 5
</pre>

## array_unique()

Diversas vezes nos deparamos com um _array_ e valores duplicados. Em uma experiência pessoal, trabalhei na criação de um sistema composto por uma divisão hierárquica entre setores. Nos relatórios, os usuários informavam diversos setores ao realizar os filtros. Quando os resultados eram filtrados no banco de dados, diversos códigos de setores vinham duplicados. Com isso, as _queries _do banco ficavam maiores e mais lentas.

Com a função _array_unique()_ resolvi meu problema. Veja o exemplo:

<pre class="lang-php">&lt;?php
$array = array ('a','b','c','d','a');
$unique = array_unique ($array);

foreach ($unique as $letra)
{
     print('Letra: '.$letra.'&lt;br&gt;');
}

//Resultado
//Letra: a
//Letra: b
//Letra: c
//Letra: d
</pre>

## in_array()

Esta função é realmente útil para verificar se existe um determinado valor em um _array_. Veja o exemplo:

<pre class="lang-php">&lt;?php
$array = array ('a','b','c','d');

if (in_array('a',$array))
{
   print('O valor está no array');
}
else
{
   print('Não está no array');
}

//Resultado: O valor está no array
</pre>

## print_r()

Uma mão na roda em momentos que você deseja depurar a estrutura de um determinado _array_ ou objeto no PHP. Em meus códigos, utilizo esta função sempre acompanhada da tag _pre_ do HTML, para assim exibir de forma mais amigável a estrutura do _array_ ou objeto. Veja o exemplo:

<pre class="lang-php">&lt;?php
$array = array ('a','b','c','d');

print_r($array);

//Resultado: Array ( [0] =&gt; a [1] =&gt; b [2] =&gt; c [3] =&gt; d )
</pre>

## implode()

Juntar os valores de um determinado _array_ e separá-los em uma determinada _string_. Utilizo muito esta função para exibir listas de nomes separados por vírgula, ou para criar cláusula _IN_ no MySQL. Veja o exemplo:

<pre class="lang-php">&lt;?php
$array = array ('a','b','c','d');

print(implode(',',$array));

//Resultado: a,b,c,d
</pre>

## explode()

Esta função é o oposto da função _implode_. Nela você informa uma _string_ e define qual separador o PHP deverá usar para dividí-la e gerar um _array_ para cada espaço dividido. Veja o exemplo:

<pre class="lang-php">&lt;?php
$string = 'O PHP é bacana.';

$array = explode (' ',$string);

print_r($array);

//Resultado: Array ( [0] =&gt; O [1] =&gt; PHP [2] =&gt; é [3] =&gt; bacana. )
</pre>

## checkdate()

Função muito útil do PHP para validar se uma determinada data está correta. Evita de inserirmos datas incorretas no banco de dados, acarretando erros de sintaxe, datas zeradas ou datas incorretas. Veja o exemplo:

<pre class="lang-php">&lt;?php
$dia = 13;
$mes = 13;
$ano = 2015;
if (checkdate($mes,$dia,$ano))
{
    print('Data correta');
}
else
{
    print('Data incorreta');
}
//Resultado: Data incorreta
</pre>