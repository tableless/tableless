---
title: Prepared Statements no MySQL
author: Layo Azevedo
type: post
date: 2013-04-18
excerpt: Para iniciantes, entenda como o Prepared Statements funciona no MySQL.
url: /prepared-statements-no-mysql/
dsq_thread_id: 1219210821
categories:
  - Técnicas e Práticas

---
Para quem adora padronização e organização, no MySQL existe o recurso chamado **Prepared Statements**.

Imagine a seguinte situação: você precisa criar uma procedure que faça todas as consultas em todas as entidades do seu banco e outra que apenas inserções e assim por diante&#8230; Uma para cada DML (data manipulation language) tudo passando por parametros, esse é o statement prepare.

Resumidamente você prepara a query antes de executa-lá no banco de dados, então vamos colocar a mão na massa e mostrar esse recurso.

## Criando o usuário

O primeiro passo é criar um usuário no banco de dados que tenha permissão para executar rotinas. Eu que trabalho sempre com stored procedures utilizo apenas o EXECUTE, mas se você trabalha com DMLs diretas nas aplicações, pode criar diversas permissões ou um usuário com todos os privilégios (ALL PRIVILEGES).

**Segue abaixo o exemplo de EXECUTE:**

<pre class="lang-sql">GRANT EXECUTE 
ON *.*
TO layo.azevedo@localhost IDENTIFIED BY 'w9QSK4yD' WITH GRANT OPTION;</pre>

**Segue abaixo o exemplo de um ALL PRIVILEGES:**

<pre class="lang-sql">GRANT ALL PRIVILEGES
ON *.*
TO layo.azevedo@localhost IDENTIFIED BY 'w9QSK4yD' WITH GRANT OPTION;</pre>

**ESSES FORAM OS COMANDOS PARA CRIAR UM USUARIO:**

**GRANT** &#8211; CRIA USUARIO
  
**EXECUTE** &#8211; EXECUTA APENAS ROTINAS
  
**ALL PRIVILEGES** &#8211; PERMITE EXECUTAR TUDO NO BANCO DE DADOS
  
**\*.\*** &#8211; O PRIVILEGIO APLICA-SE A TODAS AS BASES
  
**IDENTIFIED BY** &#8211; É A SUA SENHA
  
**WITH GRANT OPTION** &#8211; O USUARIO PODE CRIAR DIVERSOS USUARIOS E CONCEDER PRIVILEGIOS A ELE.

Sinceramente eu aconselho trabalhar com o EXECUTE. Com ele é difícil de tentarem injection sql. 

Agora que criamos o usuario **layo.azevedo@localhost** vou criar uma procedure com a função de executar qualquer select no MySQL, começando com o delimitador do código para não parar quando o MySQL achar o sinal de &#8216;;&#8217; (ponto vírgula):

<pre class="lang-sql">DELIMITER $$
$$</pre>

Dentro do DELIMITER colocamos a procedure com o nome de SelectGeral com três parâmetros: nome da tabela, condição e valor:

**1 &#8211;** Chamarei tabela de p\_tabela, condição de p\_condicao e valor de p_valor (lembre-se que o MySQL é fortemente tipado então coloque o tipo se é VARCHAR, CHAR, INT, etc&#8230;)

<pre class="lang-sql">DELIMITER $$

create procedure SelectGeral (p_tabela(VARCHAR(20), p_condicao(VARCHAR(10), p_valor (VARCHAR(30)) 
BEGIN

END
$$</pre>

Proximo passo é criar uma variável para executar a query dentro do banco. Nesse caso usaremos o SET juntamente com o comando CONCAT para concatenarmos os dados.

<pre class="lang-sql">DELIMITER $$

create procedure SelectGeral (p_tabela VARCHAR(20), p_condicao VARCHAR(10), p_valor VARCHAR(30))
BEGIN
SET @Variavel = CONCAT('SELECT * from  ', p_tabela,' WHERE ', p_condicao , ' = ''' ,p_valor,'''');
END
$$</pre>

O último passo é executar a variável:

<pre class="lang-sql">DELIMITER $$

create procedure SelectGeral (p_tabela VARCHAR(20), p_condicao VARCHAR(10), p_valor VARCHAR(30))
BEGIN
SET @Variavel = CONCAT('SELECT * from  ', p_tabela,' WHERE ', p_condicao , ' = ''' ,p_valor,'''');
PREPARE consulta_geral FROM @Variavel ;
EXECUTE consulta_geral;
END
$$</pre>

Pronto criamos a procedure SelectGeral com o Prepared Statements. Para visualizar basta executar o seguinte comando:

<pre class="lang-sql">CALL SelectGeral ('usuario', 'nome', 'layo.azevedo');</pre>

Ou seja seria essa query = **SELECT * from usuario WHERE  nome = &#8216;layo.azevedo&#8217;**

Esse foi um exemplo bem básico, mostrando o caminho das pedras para iniciantes que tenham alguma dúvida sobre Prepared Statements.