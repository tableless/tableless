---
title: MySQL Essencial (parte 1)
author: Claudio Melo
type: post
date: 2016-04-28
url: /mysql-essencial-parte-1/
categories:
  - Back-end
tags:
  - banco de dados
  - dev
  - mysql

---
## O inicio e quem usa o MySQL

O MySQL é um sistema relacional de gerenciamento de banco de dados de código aberto, que utiliza o SQL (Linguagem de consulta estruturada) como interface, é atualmente um dos bancos de dados mais populares na internet, mais de 10 milhões de instalações pelo mundo inteiro. Em Julho de 2013, foi considerado o segundo banco mais utilizado do mundo.

Criado na Suécia por David Axmark, Allan Larsson e Michael &#8220;Monty&#8221; Widenius, a primeira versão surgiu em 23 de Maio de 1995. Hoje, seu desenvolvimento emprega mais de 400 profissionais no mundo inteiro. Em 2008, a MySQL AB, desenvolvedora do MySQL, foi comprada pela Sun Microsystems (que em 2009, foi comprada pela Oracle), por 1 bilhão de dólares.

Entre alguns dos usuários mais famosos do MySQL, estão: PayPal, YouTube, Google, Walmart, NASA, Bradesco, Nokia, HP, Lufthansa, etc&#8230;

## Mão na massa

Neste artigo, partiremos do principio que você já tem o MySQL instalado e rodando bonitinho&#8230;

Para acessar o MySQL utilize o comando a seguir:

<pre class="lang-sql">mysql -u &lt;usuário&gt; -p</pre>

Depois desse comando, o MySQL vai te pedir a senha do usuário, obviamente, por segurança.

Dentro do MySQL, você tem poderes para atualizar, criar e editar qualquer tabela/banco. Para acessar o help, simplesmente digite &#8216;help&#8217; no terminal e aparecerá o menu de ajuda do MySQL.

Para ver todos os bancos criados, utilize o:

<pre class="lang-sql">show databases;
</pre>

Para criar um banco, depois de logado no MySQL, você pode seguir o seguir o seguinte comando:

<pre class="lang-sql">CREATE DATABASE banco_exemplo;
</pre>

E &#8216;paaaah&#8217;, seu banco foi criado com sucesso. Agora você precisa acessar este banco:

<pre class="lang-sql">USE banco_exemplo;
</pre>

Agora, para a coisa ficar mais interessante, vamos criar uma tabela, para podermos adicionar dados nela:

<pre class="lang-sql">CREATE TABLE tabela_do_banco_exemplo (
id INT(11) AUTO_INCREMENT PRIMARY KEY,
first_name VARCHAR(30) NOT NULL,
last_name VARCHAR(30) NOT NULL,
mail VARCHAR(100) NOT NULL,
mobile VARCHAR(100),
created_at TIMESTAMP
);
</pre>

No comando acima, criamos uma tabela dentro o seu banco. Nessa tabela teremos 6 colunas:

  * ID &#8211; um número inteiro de até 11 caracteres que se auto incrementa, ou seja, nunca se repete, se já existir o 1, ele coloca o 2 e que é a chave principal da nossa tabela.
  * first_name &#8211; um campo que aceita numeros, letras e caracteres especiais, com até 30 caracteres e não pode ser NULL.
  * last_name &#8211; um campo que aceita numeros, letras e caracteres especiais, com até 30 caracteres e não pode ser NULL.
  * mail &#8211; um campo que aceita numeros, letras e caracteres especiais, com até 100 caracteres e não pode ser NULL.
  * mobile &#8211; um campo que aceita numeros, letras e caracteres especiais, com até 100 caracteres.
  * created_at &#8211; TIMESTAMP preenche a coluna com o exato horário da inserção da linha na tabela, ou seja, o momento em que a linha foi inserida.

Agora vamos partir para a inserção de conteúdo dentro desta tabela, a final, uma tabela sem nenhuma linha de conteúdo não tem nenhuma função. Então vamos lá:

<pre class="lang-sql">INSERT INTO tabela_do_banco_exemplo (first_name, last_name, mail, mobile, created_at) VALUES ('claudio', 'melo','claudio@claudiomelo.net','(11) 99999-9999', NOW());
</pre>

Ao infinito e além, bom, é o seguinte, na linha acima, inserimos uma linha na tabela que criamos, o INSERT INTO, se explica por si só, né? Lembrando que não colocamos o ID pois ele se &#8220;AUTO INCREMENTA&#8221;, como setamos ao criar a nossa tabela.

Quando especificamos as colunas que devem ser inseridas, não precisamos necessariamente respeitar a ordem que fizemos quando criamos a tabela, como podem ver no exemplo, eu inverti o mobile e o mail, como dizia na matemática, a ordem dos fatores não altera o produto. Porém, lembre-se de, quando setar o conteúdo da coluna nos VALUES, você tem que seguir a mesma ordem que declarou na lista de colunas que serão atingidas.

Agora que já criamos um banco, já criamos uma tabela, já inserimos conteúdo dentro desta tabela, chegou o momento de buscar algum conteúdo dentro dessa tabela:

<pre class="lang-sql">SELECT * FROM tabela_do_banco_exemplo;
</pre>

Isso vai te retornar TODAS as colunas de uma tabela, simples né? Se tiver 50 linhas na sua tabela, o select vai te retornar todas as colunas das 50 linhas. E mais uma vez, você deve estar prestes a me xingar por que quer só as colunas que precisa, mas ai eu te digo, vamos pegar somente as colunas que queremos neste momento:

<pre class="lang-sql">SELECT first_name FROM tabela_do_banco_exemplo;
</pre>

Mais simples que isso, faça um esforço e tente entender a linha que escrevemos, esqueça o CTRL+C e CTRL+V. Pedimos ao banco um SELECT da coluna first\_name, isso vai nos retornar o first\_name de todas as linhas da nossa tabela.

Nesse momento, podemos ser até um pouco mais ousados, eu diria, vamos selecionar a coluna mobile somente de linhas que tem números de telefone diferentes, ou seja, dois cadastros com números iguais de telefone, não aparecerão nessa lista:

<pre class="lang-sql">SELECT DISTINCT mobile FROM tabela_do_banco_exemplo;
</pre>

Agora você deve estar louco para buscar duas colunas junto com o DISTINCT, então vamos nessa:

<pre class="lang-sql">SELECT DISTINCT mobile, first_name FROM tabela_do_banco_exemplo;
</pre>

Isso vai nos retornar uma lista onde não haverá linhas que repitam o número de telefone E (preste bem a atenção neste E) o primeiro nome.

Bom, por enquanto é só. Criticas ou sugestões é só falar nos comentários ou entrar em contato comigo, ficarei muito agradecido! Em breve teremos a parte 2 para continuar esse papo legal sobre MySQL.