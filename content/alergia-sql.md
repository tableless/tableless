---
title: Alergia à SQL
author: grillorafael
type: post
date: 2015-03-16
url: /alergia-sql/
categories:
  - Back-end
  - Código
  - Técnicas e Práticas

---
## Introdução

Quem nunca ouviu as seguintes frases: “Escrever SQL nos dias de hoje não é uma boa prática” ou “Tente não escrever SQL, usa os recursos do ORM”, ainda não trabalhou o suficiente.

O mercado de startups parece cada vez mais alérgico ao SQL, um dos recursos mais poderosos e antigos(1974!) no mundo dos bancos de dados.

O que as pessoas esquecem ou escolhem ignorar é a <a href="http://rob.conery.io/2015/02/24/embracing-sql-in-postgres/" target="_blank">capacidade que um banco de dados tem</a> e pode te oferecer para resolver problemas banais.

Mas a questão é, como e porque devemos perder o medo do SQL?

## Escrever SQL é sim uma boa prática

Quando estamos envolvidos demais com os ORMs que utilizamos para fazer aplicações, tentamos cada vez mais resolver os problemas de acesso de dados utilizando os recursos do ORM que muitas vezes são muito bons e completos.

Porém, quando precisamos resolver consultas mais complexas, nós enfrentamos elas geralmente de duas formas diferentes:

  1. Realizando diversas buscas e processando a nível de aplicação
  2. Escrever uma String de SQL e executá-la com o ORM

Por mais vantajoso em termos de desempenho seja escrever a String da consulta dentro do ORM, muitas vezes preferimos processar essas consultas em tempo de execução utilizando os lindos recursos de nossas maravilhosas linguagens dinâmicas. Afinal, é deselegante escrever uma String com uma query SQL no meio do nosso Business Logic, né?

Esse pensamento é bastante comum, pouco eficiente e bastante errado. Quando assumimos fazer o item 1, perdemos os recursos de <a href="http://en.wikipedia.org/wiki/Query_optimization" target="_blank">otimização de query</a> que o banco nos fornece e damos lugar um código que é muito provavelmente ineficiente e tem pouca garantia de consistência. Quando assumimos o item 2, ganhamos o fator otimização porém perdemos no fator manutenibilidade.

Você pode alegar que não se pode ganhar todas né? Nesse caso, você pode sim ganhar todas.

## Routines e Procedures

Funções internas do banco de dados são normalmente chamadas de Procedure ou Routine. Essas procedures se comportam como uma função em qualquer linguagem de programação, ou seja, podemos chama-las através de consultas, podemos utilizá-las em outras procedures e podemos também chama-las através do nosso ORM de preferência.

Se quiser ler mais sobre procedures nativas do PostgreSQL tem uma <a href="http://rob.conery.io/2015/02/24/embracing-sql-in-postgres/" target="_blank">matéria bem legal</a> dando uma palhinha do que ele pode fazer por você.

### Minhas procedures

Você também pode definir procedures para trabalhar com suas tabelas e fazer operações nos seus dados. A forma de definir é bastante simples.

<pre>CREATE OR REPLACE FUNCTION hello_world(p_name character varying)
RETURNS character varying
AS
$BODY$
BEGIN
    RETURN CONCAT('Hello, ', p_name, '!');
END;
$BODY$
    LANGUAGE plpgsql VOLATILE;
</pre>

Para executar a procedure basta realizar uma consulta nela.

<pre>select hello_world('rafael');

-- Retorno
hello_world
----------------
Hello, Rafael!
(1 row)
</pre>

Podemos ver então que a declaração de uma procedure é bastante simples e flexível. Podemos ter funções com diversos retornos como tabelas, tipos nativos e tipos criados pelo usuário.

Existe também aqueles que gostam de trabalhar somente com SQL por já ter se estressado o suficiente com o ORM e tentou <a href="http://rob.conery.io/2015/02/21/its-time-to-get-over-that-stored-procedure-aversion-you-have/" target="_blank">recriar o Devise utilizando procedures</a> (Este é um artigo bastante interessante de alguém que cansou de ter problemas com ORMs).

## Lógica de Dados VS Lógica de Negócios

Hoje em dia chamamos tudo que está rodando na nossa aplicação de lógica de negócios, porém, não é bem assim. É importante conhecer os limites e as diferenças do que é lógica de dados e o que é lógica de negócios.

### Lógica de Dados

Lógico de dados é tudo aquilo que opera somente na camada dos dados (Duh), ou seja, é tudo aquilo que representa condições do nosso dado.

Exemplos:

  1. Criptografia de senhas
  2. Timestamps de tabela (createdAt, updatedAt)
  3. Softdelete (deletedAt)
  4. Consistências (Verificação de unicidade, chaves primárias, etc)
  5. Quando criar registro X, criar registro Y também

### Lógica de Negócios

  1. Quando um usuário criar uma conta, disparar um Email de boas vindas
  2. Quando o usuário inserir um registro na tabela, notificar via SMS outro usuário
  3. Usuário x só pode acessar lugares x, y e z do sistema

Para fazer a lógica de negócios funcionar, devemos mapear a lógica em dados e trabalhar a lógica de dados para atender nossa lógica de negócios.

Em um mundo ideal existe uma completa separação entre essas lógicas mas no mundo real isso acaba se sobrepondo para agilizar o desenvolvimento.

## Como escrever SQL da forma certa

Nos pegamos então em um mundo onde é inevitável escrever SQL. Em algum momento das nossas aplicações, vamos ter que colocar um SQL no meio do nosso código para resolver uma consulta complexa. Quando isso acontecer o que devemos fazer?

### Meça

Consultas difíceis de escrever no ORM não é o único motivo para escrever SQL na sua aplicação. <a href="https://www.airpair.com/ruby-on-rails/performance" target="_blank">Muitas vezes o ORM que você está usando é lento</a> para determinadas tarefas. Para resolver isso, fuja um pouco dele e trabalhe no nível do SQL.

### Separe as lógicas

Saiba separar o seu SQL do código da aplicação. Crie uma procedure e faça uma chamada. Dessa forma você desacopla a lógica da consulta da aplicação e se um dia essa consulta operar de forma diferente basta atualizar a procedure.

## Aproveite o melhor dos dois mundos

Meu objetivo não é convencer ninguém a parar de usar ORMs, mas saber medir e tomar deciões através de dados. ORMs não solucionam todos os problemas de acesso aos dados, além de adicionarem uma camada desnecessária de complexidade na aplicação.

Alguns exemplos:

Antes

Aplicaçao

<pre>var sql = '';
sql += ' SELECT p1.id, p1.nome, p1.descricao,  ST_AsGeoJSON(p1."poiGeometrico") geojson, a1.nome "acervo_nome", c1.nome "categoria_nome", p1."urlIcone", ';
sql += ' p2.id id2, p2.nome nome2 , p2.descricao descricao2,  ST_AsGeoJSON(p2."poiGeometrico") "geojson2", a2.nome "acervo_Nome2", c2.nome "categoria_nome2", p2."urlIcone" "urlIcone2", ';
sql += ' ST_Distance(ST_Transform(p1."poiGeometrico",3067), ST_Transform(p2."poiGeometrico",3067)) distancia ';
sql += ' FROM "Poi" p1, "Poi" p2, "Acervo" a1, "Acervo" a2, "Categoria" c1, "Categoria" c2 ';
sql += ' WHERE c1.id = :categoriaId1 AND c2.id = :categoriaId2 AND ';
sql += ' p1."AcervoId" = a1.id AND p2."AcervoId" = a2.id AND ';
sql += ' p1."CategoriumId" = c1.id AND p2."CategoriumId" = c2.id ';
sql += ' AND ST_Distance(ST_Transform(p1."poiGeometrico",3067), ST_Transform(p2."poiGeometrico",3067)) &lt; :distancia &#039;;

var parametros = {
    categoriaId1: parseInt(req.body.categoriaId1, 10),
    categoriaId2: parseInt(req.body.categoriaId2, 10),
    distancia: parseInt(req.body.distancia, 10)
};

db.sequelize.query(sql, null, {
    raw: true
}, parametros)
    .then(function(data) {
        res.send(data);
    });
</pre>

Depois

SQL

<pre>CREATE OR REPLACE FUNCTION deteccao_de_impacto(
    p_categoria_id1 integer,
    p_categoria_id2 integer,
    p_distancia integer
)
RETURNS TABLE (
    id integer,
    nome varchar,
    descricao varchar,
    geojson json,
    acervo_nome varchar,
    categoria_nome varchar,
    urlIcone varchar,
    id2 integer,
    nome2 varchar,
    descricao2 varchar,
    geojson2 json,
    acervo_Nome2 varchar,
    categoria_nome2 varchar,
    urlIcone2 varchar,
    distancia integer
) AS
$BODY$
#variable_conflict use_variable
BEGIN
    RETURN QUERY
    SELECT
        p1.id,
        p1.nome,
        p1.descricao,
        ST_AsGeoJSON(p1.poiGeometrico) geojson,
        a1.nome acervo_nome,
        c1.nome categoria_nome,
        p1.urlIcone,
        p2.id id2,
        p2.nome nome2,
        p2.descricao descricao2,
        ST_AsGeoJSON(p2.poiGeometrico) geojson2,
        a2.nome acervo_Nome2,
        c2.nome categoria_nome2,
        p2.urlIcone urlIcone2,
        ST_Distance(
            ST_Transform(p1.poiGeometrico, 3067),
            ST_Transform(p2.poiGeometrico, 3067)
        ) distancia
    FROM
        Poi p1,
        Poi p2,
        Acervo a1,
        Acervo a2,
        Categoria c1,
        Categoria c2
    WHERE
        c1.id = p_categoria_id1 AND
        c2.id = p_categoria_id2 AND
        p1.AcervoId = a1.id AND
        p2.AcervoId = a2.id AND
        p1.CategoriumId = c1.id AND
        p2.CategoriumId = c2.id AND
        ST_Distance(
            ST_Transform(p1.poiGeometrico, 3067),
            ST_Transform(p2.poiGeometrico, 3067)
        ) &lt; p_distancia
    ;
END;
$BODY$
  LANGUAGE plpgsql VOLATILE
  COST 100;
ALTER FUNCTION deteccao_de_impacto(integer, integer, integer)
  OWNER TO postgres;
</pre>

Aplicaçao

<pre>var sql = "select deteccao_de_impacto(:categoriaId1, :categoriaId2, :distancia)";
var parametros = {
    categoriaId1: parseInt(req.body.categoriaId1, 10),
    categoriaId2: parseInt(req.body.categoriaId2, 10),
    distancia: parseInt(req.body.distancia, 10)
};

db.sequelize.query(sql, null, {
    raw: true
}, parametros)
    .then(function(data) {
        res.send(data);
    });
</pre>