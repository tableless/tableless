---
title: Features que sua API REST precisa ter desde o início
author: Ulysses Marins
type: post
date: 2016-11-17
url: /features-que-sua-api-rest-precisa-ter-desde-o-inicio/
titulo_personalizado:
  - 'Features que sua API REST precisa ter <strong>desde o início</strong>'
categories:
  - Artigos
  - Back-end
  - Destaques
  - Tecnologia e Tendências
tags:
  - api
  - arquitetura de software
  - backend
  - microservices
  - rest
  - web service

---
Eu tenho trabalhado com dados suavemente flutuando através do protocolo http por um tempo e agora eu tenho esse sentimento altruísta de que eu posso contribuir com os desenvolvedores mais jovens com algumas histórias sobre os desafios que enfrentei durante a minha jornada.

Este artigo basicamente tem o objetivo de listar e discutir sobre alguns pontos importantes que sua API, possivelmente, poderia abraçar desde o início do projeto, a fim de acelerar o processo de desenvolvimento para todos em sua equipe.

## Autenticação e Autorização

Se você se preocupa com quem vai acessar seus endpoints, é necessário prestar atenção sobre este tópico. Existem algumas especificações conhecidas para lidar com este assunto, principalmente [JWT][1], [OAuth][2] e [OAuth2][3]. Estas abordagens irão abranger a maioria dos cenários em seus aplicativos, mas às vezes você será desafiado a criar um novo tipo de camada de segurança para atender algum requisito específico, neste caso, tente não reinventar a roda e adapte suas necessidades em um desses listados.

## Query, Filtering, Sorting e Pagination

Assim que o seu banco de dados cresce, você vai começar a notar que alguns recursos estão demorando muito para serem recuperados. As abordagens comuns para esta situação são: armazenar em cache seus objetos (próximo tópico) e / ou criar a paginação / filtragem. Se você pode obter o seu recurso com algo como:

<pre class="lang-js">shiny.api.com/resources?query[type=2]&limit=5&start=1&order=[name]</pre>

&#8230;seus clients serão capazes de selecionar apenas o que eles realmente precisam para processar uma página ou tela específica. É bom para dar uma certa autonomia para seus consumidores. Próximo nível deste assunto é [GraphQL][4].

## Cache

Uma boa maneira de recuperar seus recursos incrivelmente rápido é desenvolver alguma estratégia de cache. O custo de suas requisições serão menores uma vez que seus dados estarão prontos para serem consumidos em um banco de dados in-memory. Com algum esforço você pode lidar com isso usando [Redis][5] ou [Memcached][6]. Boa sorte com sua expiração de cache. Confira algumas reflexões sobre este tema com o [Russian Doll Caching][7].

## Wrappers e Summarized Fields

Às vezes, você precisará fornecer alguns campos calculados &#8211; ou quaisquer dados agregados em geral &#8211; em suas respostas e para esse cenário, posso sugerir-lhe montar algo nessa linha:

<pre class="lang-js">{
  "summay": {
    "total": 2
    "averageAge": 22
  },
  "data":[
  {
    "name": "John",
    "age": 22
  },
  {
    "name": "Mary",
    "age": 22
  }
  ]
}
</pre>

## HATEOS

HATEOAS significa _Hypermedia as the application state of the engine_. É uma abordagem que permite que os clientes interpretem de forma autônima e dinâmica o estado atual de um recurso e as transições que podem ser iniciados decorrente deste mesmo estado.

<pre class="lang-js">{
  "id": 276,
  "amount": 90.00,
  "links": [
  {
    "type": "orders",
    "rel": "self",
    "href": "/orders/ 276"
  },
  {
    "type": "customer",
    "rel": "order's customer",
    "href": "/orders/276/customers"
  }
  ]
}
</pre>

Sobre o JSON acima, você pode tirar as seguintes conclusões:

  * Dentro do array &#8220;links&#8221; são todas as &#8216;transições&#8217; possíveis com o recurso, neste caso, podem acessar o cliente que criou as ordens com o URI /orders/276/customers.
  * **rel:auto** significa que esta URI é a referência do estado atual, neste caso, a ordem com ID 276. **rel**, em geral, representa a relação entre a ligação com o recurso atual.
  * **type** indica o tipo de recurso que é o link em questão.

Ao padronizar seus serviços RESTful usando HATEOAS você permite que os clientes usem os recursos de maneiras mais fáceis, afinal de contas, as possibilidades de navegação entre os estados serão listadas em cada hit em seus recursos.

Conforme descrito em um [post][8] de Martin Fowler, HATEOAS em sua API é o último passo para atingir a &#8216;Glória de REST&#8221;, o estado da arte.

## Message Queue

Aposto que você tem algumas rotas em suas APIs que são síncronas mas não precisam necessariamente ser. Alguns casos de uso para uso de fila de mensagens são: enviar e-mails após alguma ação, redimensionamento de imagem, codificação de vídeo, etc. Uma prática comum para esta situação é colocar essas ações em uma fila de mensagens para serem processadas posteriormente de forma assíncrona. Dê uma olhada na [RabbitMQ][9] ou [Kafka][10], ambas são grandes soluções.

&#8211;

É isso aí. Pelo menos para mim estes são os principais aspectos que eu vi nos últimos anos no desenvolvimento de novos apis http/rpc/rest. Se você acha que existem alguns outros pontos importantes para mencionar, por favor deixe nos comentários e conversamos sobre 🙂

 [1]: https://jwt.io/
 [2]: https://oauth.net/
 [3]: https://oauth.net/2/
 [4]: http://graphql.org/learn/
 [5]: http://redis.io/
 [6]: https://memcached.org/
 [7]: http://blog.remarkablelabs.com/2012/12/russian-doll-caching-cache-digests-rails-4-countdown-to-2013
 [8]: http://martinfowler.com/articles/richardsonMaturityModel.html
 [9]: https://www.rabbitmq.com/
 [10]: https://kafka.apache.org/