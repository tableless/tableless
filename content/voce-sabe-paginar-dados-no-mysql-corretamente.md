---
title: Você sabe paginar dados no MySQL corretamente?
author: Adriano dos Santos Júnior
type: post
date: 2016-07-15
excerpt: O uso de uma simples instrução pode otimizar a performance de suas consultas ao banco.
url: /voce-sabe-paginar-dados-no-mysql-corretamente/
categories:
  - Back-end
  - Código
  - O Básico
tags:
  - mysql

---
Esta postagem já começa com uma pergunta: **Será que sabemos realmente fazer uma paginação de dados da forma correta?**

> <p style="text-align: center;">
>   <strong>ATENÇÃO!</strong> Não irei falar do uso de nenhum framework PHP, bibliotecas de ORM ou plugins em JavaScript. Irei tratar sobre a consulta ao banco de dados, somente.
> </p>

&nbsp;

<p style="text-align: left;">
  Talvez você conheça esta funcionalidade do MySQL, e talvez até comentará que isto é algo &#8220;muito básico&#8221;, mas vale lembrar: <em>&#8220;Nem todos sabem de tudo. A internet é uma grande comunidade.&#8221;</em>
</p>

## Como a maioria faria

<p style="text-align: left;">
  A grande maioria de nós simplesmente iria executar 2 instruções de SELECT no MySQL. Uma para retornar o total dos registros e outra para paginar estes registros. Alguns, talvez, fariam a consulta de todos os registros no banco e depois limitariam os registros no PHP (Vish!).
</p>

<p style="text-align: left;">
  As nossas consultas ao banco ficariam algo mais ou menos assim:
</p>

<pre class="lang-php">/** Recuperamos o total de registros **/
SELECT * FROM pessoa

/** Recuperamos somente os 10 primeiros registros **/
SELECT * FROM pessoa LIMIT 0,10
</pre>

Certo, talvez esta execução de comandos não tenha afetado o desempenho do seu site ou aplicação até o momento.

Agora, imagine ter que tratar milhares de registros, para diversos usuários ao mesmo tempo. Haja memória e servidor para isto!

Como desenvolvedores, sempre temos que prezar por um excelente desempenho e a utilização mínima de recursos em nossas aplicações, que podem tomar proporções que não imaginamos na sua criação.

## O MySQL nos dá uma força

Existe um parâmetro no MySQL que é pouco conhecido da maioria desenvolvedores. Ele foi criado justamente para facilitar as paginações de registros em uma consulta.

Com somente um comando SELECT você terá a quantidade de registros e os seus dados paginados de forma simples, e sem uma grande curva de aprendizado. Veja como é simples:

<pre class="lang-php">/** Recupera somente os 10 primeiros registros **/
SELECT SQL_CALC_FOUND_ROWS * FROM pessoa LIMIT 0,10

/** Retorna o total de linhas do comando SELECT anterior sem considerar o LIMIT **/
SELECT FOUND_ROWS();
</pre>

Que simples e útil é esta função do MySQL! Não existem grandes modificações para serem feitas. Como exemplo, eu adaptei facilmente alguns frameworks que desenvolvi para aumentar a performance.

<p style="text-align: left;">
  Você pode saber mais destas funções do MySQL <a href="http://dev.mysql.com/doc/refman/5.7/en/information-functions.html#function_found-rows" target="_blank">diretamente na documentação do próprio banco</a>.
</p>

<p style="text-align: left;">
  Além disto, o site <a href="https://www.percona.com/blog/2007/08/28/to-sql_calc_found_rows-or-not-to-sql_calc_found_rows/" target="_blank">Percona trás uma análise da performance do comando</a>, mas em resumo, o site diz:
</p>

> <p style="text-align: center;">
>   <em>&#8220;Se você tem ÍNDICES nas suas cláusulas WHERE, é melhor não utilizar o SQL_CALC_FOUND_ROWS e utilizar 2 consultas.</em><br /> <em>Mas caso você não tenha ÍNDICES em suas cláusulas WHERE, se você usar o SQL_CALC_FOUND_ROWS será mais eficiente.&#8221;</em>
> </p>

&nbsp;

<p style="text-align: center;">
  <strong>Para cada realidade, uma aplicação é válida. Utilizar esta função não é REGRA, mas conhecimento sempre fará diferença em nossas carreiras.</strong>
</p>

<p style="text-align: left;">
  Espero que tenha servido para agregar ao conhecimento de alguém. Grande abraço, e até a próxima!
</p>