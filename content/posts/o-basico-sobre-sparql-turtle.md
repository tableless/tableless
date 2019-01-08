---
title: "O básico sobre Sparql e Turtle"
categories:
  - Semântica
  - HTML
excerpt: Entendendo um pouco sobre serialização RDF com Turtle e criando queries simples com Sparql
image: https://imgh.us/pexels-photo-245618.jpeg
type: "post"
authors: Diego Eis
date: "2017-05-07T16:10:22-03:00"
---

A Web Semântica tem um conteúdo técnico extenso, onde você pode se aprofundar infinitamente. Eu adoro o assunto Web Semântica, mas não sou nem um pouco capaz de entender as partes mais técnicas dessa matéria. Por isso, estudo bastante toda a parte conceitual e teorica, que já é suficientemente interessante. Mesmo assim, queria introduzir dois assuntos que podem ser o ponto de partida para uma segunda fase de estudos para estudos mais técnicos: o Turtle e o SPARQL.

O Turtle é uma serialização do RDF pra representação de Triplas. O SPARQL é uma linguagem de query para extrair informações de fontes de dados baseado em triplas.

## O básico do básico Turtle
Existem um monte de serializações do RDF como N-Triples, Notation 3, N-Quads e outras. Eu não quero dar ênfase para todas elas por que tenho quase certeza de que não haverá uso prático nos seus projetos diários. Mas gostaria de dar um pitaco sobre o Turtle, que talvez possa te ajudar, assim como me ajudou, a entender todo esse esquema de relação de Triplas.

Como vimos, o RDF é apenas um framework, ele é um modelo de abstração. O RDF é escrito baseando-se na sintaxe do XML, que é a representação oficial do W3C para explicar o RDF. O Turtle é uma maneira de serializar o RDF, com uma linguagem muito mais amigável, legível e fácil de editar do que o XML. 

O RDF por si só não tem uma maneira de expressar Triplas. Um documento Turtle permite representar um grafo RDF em uma forma compacta baseada em texto. 

O Turtle permite que substituamos as grandes URLs que usamos para identificar nossos dados, por um namespace amigável. Ainda com o exemplo do Steve Jobs, nós definimos um prefixo logo no início do código (que é nosso contexto, onde vamos definir o vocabulário) e depois modificamos o endereço dos predicados por esse prefixo. Teríamos o seguinte código:

```xml
@prefix schema:<https://schema.org/> .

<https://dbpedia.org/resource/Steve_Jobs> 
    schema:alternateName
    "Steve Jobs"

<https://dbpedia.org/resource/Steve_Jobs>
    schema:spouse>
    <https://dbpedia.org/resource/Laurene_Powell_Jobs>
    
<https://dbpedia.org/resource/Steve_Jobs>
    schema:owns
    <https://dbpedia.org/resource/Apple_Inc.>

<https://dbpedia.org/resource/Steve_Jobs>
    schema:birthPlace
    <https://dbpedia.org/resource/San_Francisco>
    
<https://dbpedia.org/resource/Steve_Jobs>
    schema:birthDate
    "24 de Fevereiro de 1955"

<https://dbpedia.org/resource/Steve_Jobs>
    schema:deathPlace
    <https://dbpedia.org/resource/Palo_Alto,_California>

<https://dbpedia.org/resource/Steve_Jobs>
    schema:deathDate
    "5 de Outubro de 2011"
```

Esse código seria colocado num arquivo **.ttl** e servido separadamente. O W3c mostra alguns exemplos de diferentes maneiras de escrever URLs no Turtle:

```xml
# Uma tripla com todas as URLs absolutas. Como no nosso primeiro exemplo
<https://one.example/subject1> <https://one.example/predicate1> <https://one.example/object1> .

@base <https://one.example/> .
<subject2> <predicate2> <object2> .     # URLs relativa, ex. https://one.example/subject2

BASE <https://one.example/>
<subject2> <predicate2> <object2> .     # URLs relativa, ex. https://one.example/subject2

@prefix p: <https://two.example/> .
p:subject3 p:predicate3 p:object3 .     # prefixo de nome, ex. https://two.example/subject3

PREFIX p: <https://two.example/>
p:subject3 p:predicate3 p:object3 .     # prefixo de nome, ex. https://two.example/subject3

@prefix p: <path/> .                    # prefixo p: agora se refere a https://one.example/path/
p:subject4 p:predicate4 p:object4 .     # prefixo de nome, ex. https://one.example/path/subject4

@prefix : <https://another.example/> .    # prefixo vazio
:subject5 :predicate5 :object5 .        # prefixo de nome, ex. https://another.example/subject5

:subject6 a :subject7 .                 # atributo 'same as' :subject6 <https://www.w3.org/1999/02/22-rdf-syntax-ns#type> :subject7 .
```

Com uma linguagem de query, as máquinas podem vasculhar bancos de dados que estão estruturados por meio de triplas para conseguir extrair informações úteis. Uma dessas linguagens é o SPARQL.


## O básico do básico sobre SPARQL
O SPARQL é uma linguagem de query para realizar consultas em dados estruturados usando o padrão RDF. O termo SPARQL é um acrônimo recursivo que significa *SPARQL Protocol and RDF Query Language*. 

Uma query SPARQL consiste numa estrutura simples de duas clausulas: SELECT e WHERE. O **SELECT** identifica as variáveis que aparecerão nos resultados da query e o **WHERE** mostra o padrão básico do grafo que bate com os dados. 

No exemplo abaixo pego todas as obras de Mozart. Estou usando para esse exemplo um banco de dados de triplas RDF online do DBPedia. Se você quiser testar, entre na interface do iSPARQL da própria DBPedia. É uma interface bem feinha, não se espante: https://dbpedia.org/isparql/

Segue o exemplo:

```sql
SELECT ?musics
WHERE {
  ?musics dbo:musicComposer dbr:Wolfgang_Amadeus_Mozart
}
```

A resposta que recebi em XML no formato RDF:

```XML
<rdf:RDF xmlns:res="https://www.w3.org/2005/sparql-results#" xmlns:rdf="https://www.w3.org/1999/02/22-rdf-syntax-ns#">
<rdf:Description rdf:nodeID="rset">
<rdf:type rdf:resource="https://www.w3.org/2005/sparql-results#ResultSet"/>
    <res:resultVariable>musics</res:resultVariable>
    <res:solution rdf:nodeID="r0">
      <res:binding rdf:nodeID="r0c0"><res:variable>musics</res:variable><res:value rdf:resource="https://dbpedia.org/resource/Teorema_(film)"/></res:binding>
    </res:solution>
    <res:solution rdf:nodeID="r1">
      <res:binding rdf:nodeID="r1c0"><res:variable>musics</res:variable><res:value rdf:resource="https://dbpedia.org/resource/Balthus_Through_the_Looking_Glass"/></res:binding>
    </res:solution>
    <res:solution rdf:nodeID="r2">
      <res:binding rdf:nodeID="r2c0"><res:variable>musics</res:variable><res:value rdf:resource="https://dbpedia.org/resource/Teaching_to_See"/></res:binding>
    </res:solution>
    <res:solution rdf:nodeID="r3">
      <res:binding rdf:nodeID="r3c0"><res:variable>musics</res:variable><res:value rdf:resource="https://dbpedia.org/resource/Écoute_voir"/></res:binding>
    </res:solution>
    <res:solution rdf:nodeID="r4">
      <res:binding rdf:nodeID="r4c0"><res:variable>musics</res:variable><res:value rdf:resource="https://dbpedia.org/resource/A_Man_Escaped"/></res:binding>
    </res:solution>
    <res:solution rdf:nodeID="r5">
      <res:binding rdf:nodeID="r5c0"><res:variable>musics</res:variable><res:value rdf:resource="https://dbpedia.org/resource/Ehrengard"/></res:binding>
    </res:solution>
    <res:solution rdf:nodeID="r6">
      <res:binding rdf:nodeID="r6c0"><res:variable>musics</res:variable><res:value rdf:resource="https://dbpedia.org/resource/Tale_of_Tales_(1979_film)"/></res:binding>
    </res:solution>
    <res:solution rdf:nodeID="r7">
      <res:binding rdf:nodeID="r7c0"><res:variable>musics</res:variable><res:value rdf:resource="https://dbpedia.org/resource/The_Magic_Flute_(1975_film)"/></res:binding>
    </res:solution>
    <res:solution rdf:nodeID="r8">
      <res:binding rdf:nodeID="r8c0"><res:variable>musics</res:variable><res:value rdf:resource="https://dbpedia.org/resource/The_Magic_Flute_(2006_film)"/></res:binding>
    </res:solution>
    <res:solution rdf:nodeID="r9">
      <res:binding rdf:nodeID="r9c0"><res:variable>musics</res:variable><res:value rdf:resource="https://dbpedia.org/resource/Quiet_Night_In"/></res:binding>
    </res:solution>
    <res:solution rdf:nodeID="r10">
      <res:binding rdf:nodeID="r10c0"><res:variable>musics</res:variable><res:value rdf:resource="https://dbpedia.org/resource/Live_Together,_Die_Alone"/></res:binding>
    </res:solution>
    <res:solution rdf:nodeID="r11">
      <res:binding rdf:nodeID="r11c0"><res:variable>musics</res:variable><res:value rdf:resource="https://dbpedia.org/resource/Eroica_(2003_film)"/></res:binding>
    </res:solution>
    <res:solution rdf:nodeID="r12">
      <res:binding rdf:nodeID="r12c0"><res:variable>musics</res:variable><res:value rdf:resource="https://dbpedia.org/resource/Killing_Time_(2013_film)"/></res:binding>
    </res:solution>
    <res:solution rdf:nodeID="r13">
      <res:binding rdf:nodeID="r13c0"><res:variable>musics</res:variable><res:value rdf:resource="https://dbpedia.org/resource/Don_Giovanni_(1979_film)"/></res:binding>
    </res:solution>
    <res:solution rdf:nodeID="r14">
      <res:binding rdf:nodeID="r14c0"><res:variable>musics</res:variable><res:value rdf:resource="https://dbpedia.org/resource/Under_the_Pavement_Lies_the_Strand"/></res:binding>
    </res:solution>
    <res:solution rdf:nodeID="r15">
      <res:binding rdf:nodeID="r15c0"><res:variable>musics</res:variable><res:value rdf:resource="https://dbpedia.org/resource/A_Woman_Is_a_Risky_Bet:_Six_Orchestra_Conductors"/></res:binding>
    </res:solution>
  </rdf:Description>
</rdf:RDF>
```

Lá você consegue ver a descrição das triplas, a query e também a resposta XML.

Tente pegar, por exemplo, todos os artistas relacionados a John Lennon. Coisa simples, assim:

```sql
SELECT ?artists
WHERE {
  ?artists dbo:associatedMusicalArtist dbr:John_Lennon
}
```

Ou as músicas escritas por ele:

```sql
SELECT ?musics
WHERE {
  ?musics dbp:artist dbr:John_Lennon
}
```

Há uma série de combinações de filtros e comandos que você pode usar com SPARQL para combinar e extrair informações. O pessoal da Wiki Base22 tem uma [documentação](https://wiki.base22.com/display/btg/SPARQL+Query+Examples) por exemplos muito boa. Lá você vai aprender a fazer perguntas usando esses dados. 

As declarações RDF (as Triplas) são apenas um framework, um padrão, para ser usado em vários outros formatos como JSON-LD, Turtle, N-triples e outros. A ideia é que não importa qual o formato você esteja usando para expressar os dados, a informação ainda será representada e organizada usando o trio sujeito, predicado e objeto.

O W3C dá um exemplo bem legal para entender isso: números são o oposto de numerais. Números são um conceito matemático. Já os numerais são uma representação usando Romanos, Arábicos, Hexadecimal etc. Se você vai mostrar os números usando o formato romano, não importa.

O RDF também não é uma aplicação XML. O modelo fundamental do RDF é totalmente independente do XML. Ele é um modelo que descreve e qualifica relações entre duas fontes web.

A página do *John Lennon* lá na [DBPedia](https://dbpedia.org/page/John_Lennon), tem todas as informações sobre o cantor. Você consegue essas informações em diversos formatos. Incluindo XML em padrão [RDF](https://dbpedia.org/data/John_Lennon.rdf). Esse arquivo RDF tem algo em torno de 2148 linhas, com todos os dados que a DBPedia tem de John Lennon. Há outros formatos disponíveis, como [JSON-LD](https://dbpedia.org/sparql?default-graph-uri=http%3A%2F%2Fdbpedia.org&query=DESCRIBE%20%3Chttp%3A%2F%2Fdbpedia.org%2Fresource%2FJohn_Lennon%3E&format=application%2Fjson-ld).