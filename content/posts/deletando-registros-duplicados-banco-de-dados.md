---
title: Deletando registros duplicados no banco de dados
author: George Moura
type: post
date: 2014-01-09
excerpt: Fazendo um script para apagar entradas duplicadas no MySQL.
url: /deletando-registros-duplicados-banco-de-dados/
dsq_thread_id: 2092800532
categories:
  - Back-end
  - Código
tags:
  - banco de dados
  - mysql
  - sql

---
Precisei fazer a migração de dados de algumas tabelas de cadastro (telefones, hobbies, interesses, formações e etc.) para uma única tabela diferenciando-os pelo id do usuário e o id do campo. O problema é que meu script acabou duplicando as informações. Para a minha sorte isso aconteceu em um banco de desenvolvimento, onde era possível apagar os dados da tabela, ajustar os scripts e refazer a migração. Eu não queria ter esse trabalho novamente e logo resolvi pesquisar um script sql que me ajudasse a apagar os registros duplicados, nesse caso deixando apenas o último registro gravado.

Assumindo que você use o banco de dados MySql e tenha uma tabela chamada &#8220;nomes&#8221;, e que essa tabela tenha os campos id e nome. Essa sintaxe pode ser usada em outros bancos, utilizaremos o seguinte comando:

<pre class="lang-html">DELETE a FROM nomes AS a, nomes AS b WHERE a.nome=b.nome AND a.id &lt; b.id</pre>

Perceba que no comando sql após o `FROM` eu chamo duas vezes a tabela &#8220;nomes&#8221;, mas as diferencio pelas letras **a** e **b**. Você poderia dar o nome que quisesse. Note também que depois do `WHERE` eu faço a comparação entre as colunas, verificando a duplicidade e depois digo que o id de &#8220;a&#8221; deve ser menor que o de &#8220;b&#8221;. Dessa forma o MySql vai comparar todos os registros com o mesmo nome e apagar aqueles que contenham o menor id.

**nomes**: É a tabela com os registros duplicados.
  
**nome**: É o campo para comparação dos registros.
  
**id**: É a chave primária da tabela.

Veja na prática como acontece:

Tabelas com os registros duplicados

[<img class="alignnone size-full wp-image-40122" alt="tableless-select-mysql" src="http://tableless.com.br/uploads/2014/01/tableless-select-mysql.png" width="487" height="310" srcset="uploads/2014/01/tableless-select-mysql.png 487w, uploads/2014/01/tableless-select-mysql-263x168.png 263w" sizes="(max-width: 487px) 100vw, 487px" />][1]

Aplicando o script descrito acima:

[<img class="alignnone size-medium wp-image-40121" alt="tableless-mysql-script-delete" src="http://tableless.com.br/uploads/2014/01/tableless-mysql-script-delete-588x205.png" width="588" height="205" srcset="uploads/2014/01/tableless-mysql-script-delete-588x205.png 588w, uploads/2014/01/tableless-mysql-script-delete-329x115.png 329w, uploads/2014/01/tableless-mysql-script-delete-660x231.png 660w, uploads/2014/01/tableless-mysql-script-delete.png 720w" sizes="(max-width: 588px) 100vw, 588px" />][2]

Caso queira apagar todos os registros duplicados, deixando apenas os registros únicos é só trocar o “<” por “!=”

veja um exemplo:

[<img class="alignnone size-medium wp-image-40120" alt="tableless-mysql-script-deletall" src="http://tableless.com.br/uploads/2014/01/tableless-mysql-script-deletall-410x310.png" width="410" height="310" srcset="uploads/2014/01/tableless-mysql-script-deletall-410x310.png 410w, uploads/2014/01/tableless-mysql-script-deletall-222x168.png 222w, uploads/2014/01/tableless-mysql-script-deletall.png 733w" sizes="(max-width: 410px) 100vw, 410px" />][3]

Pronto! É isso aí pessoal, muito simples né?

 [1]: http://tableless.com.br/uploads/2014/01/tableless-select-mysql.png
 [2]: http://tableless.com.br/uploads/2014/01/tableless-mysql-script-delete.png
 [3]: http://tableless.com.br/uploads/2014/01/tableless-mysql-script-deletall.png