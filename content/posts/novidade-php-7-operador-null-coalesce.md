---
title: Novidade PHP 7 – Operador Null Coalesce
author: Eduardo Abreu
type: post
date: 2016-02-19
excerpt: Existente em diversas outras linguagens, o operador Null Coalesce agora também faz parte da sintaxe do PHP 7.
url: /novidade-php-7-operador-null-coalesce/
categories:
  - Back-end
  - Código
  - PHP
tags:
  - null coalesce
  - php
  - php7

---
Estou começando a estudar as _features_ do PHP 7 e paralelamente irei escrever sobre elas. A primeira _feature_ que vou falar é sobre o operador **Null Coalescing**.

Este operador já existia em outras linguagens, como C# e Pearl. Eu achei muito interessante como ele melhora a legibilidade do código na checagem de variáveis.

A lógica do operador é a seguinte: retornar o primeiro valor que exista e não seja nulo dentre os valores passados. Em alguns casos, para pegar o valor de GET, por exemplo, utilizamos a seguinte sintaxe:

<pre class="lang-php">$valor = (isset($_GET['id']))? $_GET['id'] : 1;
</pre>

O trecho acima verifica se o índice ‘id’ está setado em GET, e caso esteja, ele seta na variável $valor, caso contrário, é informado o valor 1.

Já com o operador _null coalesce_, este trecho fica muito mais claro e fácil de entender.

<pre class="lang-php">$valor = $_GET['id'] ?? 1;
</pre>

O operador **??** (_null coalesce_) ficará responsável por retornar o primeiro valor que existe e não nulo. Então, se caso não seja passado um ‘id’ via GET, o valor 1 será setado em $valor.

Agora, vamos imaginar que temos o seguinte cenário: precisamos setar um valor na variável $valor, só que este valor pode vir de diversos lugares e há uma ordem a ser seguida de verificação. Como você faria?

Com o _null coalesce_ isso torna-se muito simples:

<pre class="lang-php">$valor = $_GET['id']  ?? $_POST['id'] ?? 1;
</pre>

Primeiro, o operador verifica GET, caso não exista ou seja nulo, ele irá verificar POST. Caso também não exista ou seja nulo, ele irá retornar 1.

É isso galera. Qualquer dúvida, sugestão ou crítica é só comentar. Regards!