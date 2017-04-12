---
title: Criando aplicações portáveis entre diferentes SGBDs usando PDO(PHP Data Objects)
author: Anrahh
type: post
date: 2016-09-26
url: /criando-aplicacoes-portaveis-entre-diferentes-sgbds-usando-pdophp-data-objects/
categories:
  - Artigos
  - Back-end
  - PHP
tags:
  - mysql
  - PDO
  - php
  - PHPPOO
  - PostgreSql

---
Quero apresentar nesse artigo as principais funcionalidades do PDO. PDO é uma biblioteca que implementa abstração ao acesso dos dados, ou seja, ela utiliza um driver específico, para cada SGBD (Sistema Gerenciador de Banco de Dados), tornando possível a portabilidade da base de dados de sua aplicação, sem que a mesma sofra danos ou que você passe horas e horas reescrevendo linhas e mais linhas de código.

O primeiro passo é habilitar o driver do PDO no php.ini retirando o &#8220;;&#8221; da sua frente;

No Windows:

<pre>extension=php_pdo.dll
extension=php_pdo_mysql.dll</pre>

No Linux:

<pre>extension=pdo.so
extension=pdo_mysql.so
</pre>

Consideremos o seguinte banco de dados:

<pre class="lang-sql">create database livraria;
use livraria;
create table livros(
id int not null auto_increment,
titulo varchar(75) not null,
preco decimal(10,2) not null,
estoque int not null,
PRIMARY KEY (id));
</pre>

Estabelecemos a conexão com o Banco de dados no nosso arquivo connect.php

<pre class="lang-php">//Local do banco
$host = "localhost";
//Nome do banco de dados
$db = "livraria";
//Seu Usuário no banco de dados
$user = "root";
//Senha do banco de dados
$pass = "";
//Estabelecendo a conexão
try
{
  /**
   *Agora o pulo do gato,aqui é onde a mágica acontece, precisamos especificar o banco de dados 
que iremos trabalhar,no nosso caso, optei pelo mysql. Em seguida especificamos o local 
e o nome do banco de dados e por último o usuário e a senha
    */
    $pdo = new PDO("mysql:host=$host;dbname=$db", $user, $pass);
}
catch (Exception $e)
{
    echo "Erro ao estabelecer conexão com o banco de dados:".$e-&gt;getMessage();
    die;
}
</pre>

Para inserir no Banco de dados criamos o arquivo insert.php.

<pre class="lang-php">/**
 * Insere conexão com o banco de dados estabelecida anteriormente 
 */
include 'connect.php';
/**
 * Variáveis que podem receber os valores do seu formulário
 */
 $titulo = "Padrões de Projeto - PHP";
 $preco = 140.5;
 $estoque = 5;

try 
{   /**
    *Aqui preparamos primeiramente nossa instrução de inserção e como valores, 
passamos as "?"(interrogações) para referencia-las com o parâmetro passado pela função bindParam. 
    * */
    $sql="INSERT INTO `livros` (`titulo`, `preco`, `estoque`) VALUES (?, ?, ?)";
    $stmt = $pdo-&gt;prepare($sql);
    $stmt-&gt;bindParam(1,$titulo);
    $stmt-&gt;bindParam(2,$preco);
    $stmt-&gt;bindParam(3,$estoque);
    
    if($stmt-&gt;execute())
        echo "Gravado com Sucesso";
    else
        throw new Exception("Erro ao gravar informação");

}
catch (Exception $e) 
{
    echo $e-&gt;getMessage();   
}
</pre>

Para atualizar os arquivos no banco de dados utilizamos nosso arquivo update.php:

<pre>/**
*   Inclusão da minha Conexão
* */
include 'connect.php';
/**
 * Variáveis que vem do seu formulário html  
 */
$titulo = "Padrões de Projeto - PHP";
$preco = 60;
$estoque = 5;
try 
{   
       /**
    *Aqui preparamos nossa instrução de atualização dos dados  
    * */
    $sql="UPDATE `livros` SET `preco` = ?, `estoque`= ? WHERE `titulo` = ?";
    $stmt = $pdo-&gt;prepare($sql);
    $stmt-&gt;bindParam(1,$preco);
    $stmt-&gt;bindParam(2,$estoque);
    $stmt-&gt;bindParam(3,$titulo);

    if($stmt-&gt;execute())
        echo "Atualizado com Sucesso";
    else
        throw new Exception('Erro ao Atualizar');

} 
catch (Exception $e) 
{
    echo $e-&gt;getMessage();   
}
</pre>

Para listar os dados no list.php:

<pre class="lang-php">include 'conect.php';
   //listando os livros
   $sql = "SELECT * FROM livros";
   $dados = $pdo-&gt;query($sql);
/**
*fetch()-&gt;Retorna a próxima linha do resultado.
*fetchAll()-&gt; Retorna um array com todos os resultados.
*fetchObject()-&gt; Retorna a próxima linha do resultado como objeto.
*fetchColumn()-&gt; Retorna uma coluna da próxima linha do resultado.
**/
while ($result = $dados-&gt;fetch())
{   
 echo $result['titulo'] . " - ". $result['preco']. "-". $result['estoque']."
";
}
</pre>

E para deletar os arquivos criamos o delete.php:

<pre class="lang-php">/**
 *  Inclusão da minha Conexão
 **/
include 'conect.php';
/**
 * Variáveis que vem do seu formulário html  
 */
$titulo = "Padrões de Projeto - PHP";
$preco = 60;
$estoque = 5;

try 
{   
    /**
    * Aqui preparamos nossa instrução de exclusão dos dados.  
    **/
      $sql="DELETE FROM `livros` WHERE `titulo` = ?";
    $stmt = $pdo-&gt;prepare($sql);
    $stmt-&gt;bindParam(1,$titulo);

    if($stmt-&gt;execute())
        echo "Deletado com Sucesso";
    else
        throw new Exception('Erro ao Deletar');

} 
catch (Exception $e) 
{
    echo $e-&gt;getMessage();   
}
</pre>

**Métodos da classe PDO:**

<pre>exec int Utilizado para insert, update e delete
query PDOStatement Utilizado para resultados tabulares, comando select.
prepare PDOStatement Cria um prepared statement, utilizado para dados variáveis.
</pre>

Trabalhar com PDO tem várias vantagens, além da portabilidade, existe também a questão da segurança, mas isso é cena para os próximos capítulos. Aconselho que visitem a [documentação][1] para que possam ter acesso a informação completa da biblioteca, pois a mesma é muito rica e fornecerá ao desenvolvedor inúmeras vantagens que facilitarão no dia a dia do seu desenvolvimento. Obrigado ^^!

[clique aqui para baixar o código completo.][2]

**Referências**

<http://www.diogomatheus.com.br/blog/php/trabalhando-com-pdo-no-php/>
  
<http://php.net/manual/en/book.pdo.php>
  
<http://www.php.net/manual/en/pdo.drivers.php>

 [1]: http://php.net/manual/pt_BR/class.pdostatement.php
 [2]: https://github.com/Anrahh/pdo_tableless