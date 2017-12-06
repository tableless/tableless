---
title: Explorando a PDO — Introdução
authors: Wanderson Macêdo
type: post
date: 2017-08-16
excerpt: Por que e como eu deveria usar a PDO - PHP Data Objects.
image: https://cdn-images-1.medium.com/max/2000/1*ajTdzWkHl8Vb0XcJ6IbAPA.png
categories:
  - php
  - back-end
tags:
  - back-end
  - pdo
---

Ao escrever aplicações partindo do back-end uma das primeiras preocupações do
desenvolvedor é escrever o código responsável por suas regras de negócio e como
os dados gerados pela aplicação será armazenada no banco de dados.

Por um bom tempo, no PHP, usamos extensões bem especificas para esta tarefa,
funções prefixadas com **mysql_* **estavam espalhadas pela aplicação, e mesmo
encapsulando este código em **DAO**s, haviam outros problemas. Caso o banco não
fosse mais o MySQL, iríamos mudar todas as funções para atender essa mudança.

Uma outra preocupação, era estruturar esta camada para que não se usasse um
estilo de código muito sequencial. Deste problema a extensão MySQL**i
**(*improved*) cuidou bem. Agora poderia-se usar as funções prefixadas com
**mysqli_*** ou apenas os métodos do objeto que poderia ser obtido através desta
extensão.

O maior problema que a **PDO **resolveu, foi abstrair o banco utilizado. Com ela
não é mais preciso correr atrás de funções com prefixos **mssql_, mysqli_, pg_,
oci_** que são para os bancos Microsoft, MySQL, Postgres e Oracle. Preciso
apenas de um objeto PDO e pronto, ele cuida de selecionar o driver e executar as
consultas. **Mas o que é a PDO exatamente?**

*The PHP Data Objects (PDO) ***extension ***defines a lightweight, consistent
***interface*** for accessing databases in PHP. PDO provides a data-access
***abstraction layer***, which means that, regardless of which database you’re
using, ***you use the same functions to issue queries and fetch data** —
Extraido da documentação.

Traduzindo resumidamente: É uma extensão que define uma interface para acesso ao
banco de dados. Ela fornece uma camada de abstração que independe do banco, o
que significa que você utilizará as mesmas funções para executar suas consultas.

É importante notar que, a PDO não traduz consultas específicas de um banco. É
uma abstração do acesso ao banco e não do banco em si. Para uso funções
específicas — *O que particularmente, acho incomum de acontecer*. A melhor saída
é usar a extensão prefixada.

Certo, é uma extensão define uma interface. Então, como usamos? Simples, basta
criar um objeto da classe PDO da seguinte forma.

<script src="https://gist.github.com/wandersonmaceds/52b4a329076f77221f1dbad86ee7a310.js"></script>

Perceba, que estamos criando uma conexão com o MySQL. Cada driver que implementa
a interface PDO, define uma forma de conexão que difere um pouco. Contudo,
basicamente, essas são as informações básicas necessárias.

A partir deste ponto, já podemos começar a fazer consultas, porém, por questões
de boas práticas, devemos envolver este código com um bloco try/catch, pois
qualquer erro nos dados pode retornar uma exceção do tipo PDOException. Sendo
assim, teremos:

<script src="https://gist.github.com/wandersonmaceds/96993ee9c27165c7b245fd7b3a233289.js"></script>

Este foi nosso primeiro passo para começarmos a utilizar a PDO. Nos próximos
artigos vamos explorar o que a PDO nos fornece, métodos deste objeto criado e
outras classes presentes na extensão. Deixo abaixo alguns links para explorarem:


- [PDO BOOK](http://php.net/manual/en/book.pdo.php)
- [PDO](http://php.net/manual/en/intro.pdo.php)
- [PDO Drivers](http://php.net/manual/en/pdo.drivers.php)
- [Databases Extensions](http://php.net/manual/en/refs.database.php)
