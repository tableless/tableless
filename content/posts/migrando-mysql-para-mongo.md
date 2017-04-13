---
title: Migrando do MySQL para Mongo
author: Elvis
type: post
date: 2015-03-22
excerpt: Breve explicação sobre como migrar do MySQL para o MongoDB.
url: /migrando-mysql-para-mongo/
categories:
  - Back-end
tags:
  - mongodb

---
## Introdução

O Mongodb é um banco de dados NoSql, open-source e escrito em C++ que salva seus dados em formato JSON(usando BSON — uma versão binária de JSON) utilizando chaves e valores para isso.

[<img class=" size-full wp-image-47555 aligncenter" src="http://tableless.com.br/uploads/2015/03/documentos.png" alt="documentos" width="176" height="81" />][1]

O que mais diferencia o Mongo dos outros bancos NoSQL é a simplicidade em converter instruções SQL.
  
Alem de ser muito simples de instalar e usar, com binários e drivers disponíveis para os principais sistemas operacionais e linguagens de programação, ele ainda é suportado pelas mais populares linguagens tais como: C, C#, C++, Haskell, Java™, JavaScript, Perl, PHP, Python, Ruby e Scala.

### Vantagens

  1. escalabilidade
  2. flexibilidade
  3. manipulação de dados em grande porte
  4. desempenho
  5. facilidade nas consultas
  6. comunidade ativa
  7. Sharding
  8. GridFS
  9. Replica set
 10. Orientando a documentos
 11. Schema livre

### Desvantagens

  1. Alteração de todos os registros

## Iniciando a conversão do MYSQL para o MONGODB ?

**Criando uma tabela**

<pre class="lang-sql">CREATE TABLE `agenda` (

`id` int(11) NOT NULL AUTO_INCREMENT,
`nome` varchar(125) DEFAULT NULL,
`email` varchar(125) DEFAULT NULL,
`telefone` varchar(11) DEFAULT NULL,
PRIMARY KEY (`id`)
);</pre>

**Criando uma coleção**

<pre class="lang-sql">db.createCollection( "agenda" )</pre>

**Inserir registro na tabela**

<pre class="lang-sql">INSERT INTO agenda(id,nome,email,telefone) VALUES (NULL,'Tiozinho','tio@gmail.com','9999-9999');
</pre>

**Inseriando registro na coleção**

<pre class="lang-sql">db.agenda.insert({nome:"Tiozinho" , email: "tio@gmail.com" , telefone: "9999-9999" });</pre>

**Buscando registros na tabela** 

<pre class="lang-sql">//Lista todos os registros
SELECT * FROM agenda</pre>

<pre class="lang-sql">//Lista apenas o definido no paramentro
SELECT * FROM agenda WHERE id = 1 // 1 é o parametro
</pre>

**Buscando registro na coleção**

<pre class="lang-sql">//Lista todos os registros
db.agenda.find()
</pre>

<pre class="lang-sql">//Lista apenas o definido no parâmetro
db.agenda.find({id:1}) // {id:1} é o parâmetro
</pre>

**Excluindo registro na tabela**

<pre class="lang-sql">DELETE FROM agenda WHERE id = 1</pre>

**Excluindo registro da coleção**

<pre class="lang-sql">db.agenda.remove({id:1});
</pre>

**Atualizando um registro na tabela**

<pre class="lang-sql">UPDATE agenda SET email = 'tiozinho@gmail.com' WHERE id = 1;
</pre>

**Atualizando um registro na coleção**

<pre class="lang-sql">//Buscando o Tiozinho
var agd = db.agenda.find({id:1});
</pre>

<pre class="lang-sql">//Alterando apenas o email
agd.email = "tiozinho@gmail.com";
</pre>

<pre class="lang-sql">//Atualizando na coleção
db.agenda.save(agd);
</pre>

**Extras:** Lembrando ainda temos diversas funções do relacional que podemos utilizar tranquilo no mongodb, dentre elas podemos citar:

  * drop()
  * dropDataBase()
  * update()
  * count()
  * limit()
  * sort()

No próximo post utilizaremos todas as funções acima e ainda daremos uma alteração especial nas consultas utilizando mongo, espero vocês e até o próximo.

 [1]: http://tableless.com.br/uploads/2015/03/documentos.png