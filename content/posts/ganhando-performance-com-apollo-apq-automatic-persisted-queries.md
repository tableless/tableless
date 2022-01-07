---
title: Ganhando performance com Apollo APQ — Automatic persisted queries
authors: Roger Albino
type: post
image: uploads/2017/03/pexels-photo-296983-2.jpg
date: 2017-03-20
excerpt: Melhorando a performance enviando requests menores.
categories:
  - técnicas-e-práticas
  - javascript
tags:
  - GraphQL
  - front-end
  - javascript
  - back-end
---

Uma das maiores reclamações que temos sobre o GraphQL é sobre o tamanho das requests que são enviadas a todo momento para o server. Algumas queries podem ser realmente grandes, e ficar enviando em toda request pode ser um pouco custoso. Para isso, o Apollo Server teve uma solução bem legal que são as Automatic Persisted Queries.

Temos um exemplo de uma query relativamente pequena:

```graphql
query vehicles($page: Int) {
  vehicles(page: $page) {
    name
    model
    crew
    vehicle_class
    manufacturer
    length
    cost_in_credits
    passengers
    max_atmosphering_speed
    cargo_capacity
    pilots {
      name
      height
      hair_color
      mass
      skin_color
      created
      edited
      gender
      eye_color
      birth_year
    }
  }
}
```

Com o Apollo APQ, reduzimos a nossa query para uma hash.

```graphql
{
  "operationName":"vehicles",
  "variables":{"page":1},
  "extensions": {
    "persistedQuery": {
      "version":1,
 "sha256Hash":"fc2fb9c15545c9894983d8992918a8804c0ead52e5ec76475499d560a7c220f5"
    }
  }
}
```

### Configuração

O Apollo Server suporta as automatic persisted queries sem nenhuma configuração adicional. Mas tem algumas configurações de cache que vamos fazer.

**Apollo Client**

Para configurar as APQ no Apollo Client, vamos precisar instalar um link chamado [apollo-link-persisted-queries](https://github.com/apollographql/apollo-link-persisted-queries).

```bash
npm install apollo-link-persisted-queries
```

Depois de instalado, basta adicionar o link na configuração do seu ApolloClient antes do seu link de HTTP. E temos persisted queries funcionando.

Uma opção bem legal é o useGETForHashedQueries, ativando essa flag, faremos com que todas as queries que já foram persistidas sejam feitas usando o método GET ao invés do POST como de padrão.

Usando GET nas queries podemos usar uma CDN futuramente para servir nossas queries.

```js
import { ApolloClient, InMemoryCache } from '@apollo/client';
import { ApolloLink } from "apollo-link";
import { createHttpLink } from "apollo-link-http";
import { createPersistedQueryLink } from "apollo-link-persisted-queries";
const link = ApolloLink.from([
  createPersistedQueryLink({ useGETForHashedQueries: true }),
  createHttpLink({ uri: 'http://localhost:4000/graphql' })
]);
const client = new ApolloClient({
  link,
  cache: new InMemoryCache()
});
export default client
```

### Configurando cache com Redis

Para uma configuração simples de cache utilizando o redis, podemos instalar a dependência [apollo-server-cache-redis](https://www.npmjs.com/package/apollo-server-cache-redis). Depois de instalado, basta configurarmos o cache como no exemplo. Temos outros tipos de configurações de cache que podem ser encontrados no link abaixo.

> https://www.apollographql.com/docs/apollo-server/performance/apq/#cache-configuration

```js
const { ApolloServer } = require('apollo-server');
const typeDefs = require('./src/graphql/schemas/types')
const resolvers = require('./src/graphql/resolvers')
const { RedisCache } = require('apollo-server-cache-redis');
const dataSources = require('./src/graphql/datasources')
const server = new ApolloServer({
  typeDefs,
  resolvers,
  dataSources,
  cacheControl: { defaultMaxAge: 5 }, cache: new RedisCache({
    port      : 6379,
    host      : '127.0.0.1',
    connectTimeout: 10000
  }), tracing: true
});
server.listen().then(({ url }) => {
  console.log(`🚀  Server ready at ${url} with redis cache`);
});
```

Como tudo isso funciona? Uma imagem que explica bem como tudo isso funciona está na própria documentação do Apollo Server.

Imagens: https://www.apollographql.com/docs/apollo-server/performance/apq/#how-it-works

![apq-exemplo](https://user-images.githubusercontent.com/4194366/148597182-0829a21e-3618-4742-845e-05e8a6dcc4a9.png)

- O Apollo Client tenta usar uma hash que representa a query;
- Se ela existir dentro do redis, ela é passada para o Apollo Server e retorna o resultado para o client;
- Caso ela não exista, ela retornará um erro avisando que a query não foi persistida;
- O Apollo Client então envia a query completa com a hash, e o Apollo Server persiste no redis para uma próxima request.

![apq-exemplo-2](https://user-images.githubusercontent.com/4194366/148597255-02286797-a70f-4892-b693-4ffd1a6e66b4.png)

Com poucas configurações, podemos ter APQ funcionando e reduzir significativamente o tamanho das requests com graphql.
Para mais detalhes você pode dar uma olhada na própria documentação do Apollo Server sobre APQ.
