---
title: O que é cache e como ele pode nos ajudar
authors: Marcelo Serpa
type: post
publishdate: 2018-04-18
date: 2018-04-18
excerpt: Entenda como o cache nos ajuda no dia a dia
image: https://i.imgur.com/6s9S1wz.jpg
categories:
  - Tecnologias e tendências
  - back-end
  - front-end
---

A internet é uma imensa rede de computadores e, quando uma solicitação HTTP é realizada, ela passa por diversos intermediários até chegar ao seu destino. Uma request/solicitação feita do Brasil para Japão vai passar por N computadores até chegar em um computador do país de destino, que irá processar de fato seu pedido. Como podemos ver, isso é um processo que tende a ser lento.

![](https://i.imgur.com/0cT66qV.png)

Além disso, quando uma Interface de Programação de Aplicativos (API) recebe uma request, precisa realizar algum processamento, acessar um banco de dados ou até mesmo fazer uma chamada para outra API, para compor a resposta do usuário. No final, o tempo de resposta será a soma do tempo utilizado para realizar sua regra de negócio mais o tempo gasto no tráfego na rede.

Caching é uma técnica utilizada para reduzir a quantidade de round-trip necessária para realizar uma solicitação. Com essa técnica, a request será interceptada para verificar se existe uma cópia válida em cache do resultado da operação, caso tenha, será retornada a cópia, caso contrário, a request será realizada e o retorno será armazenado.

Quais são os benefícios?

* Redução de consumo de banda, pois muitas vezes o cliente não necessita baixar do conteúdo.
* Diminuição da quantidade de requisições que a aplicação irá receber.
* Redução da latência, pois menos round-trips serão necessários para buscar o recurso.

## Como funciona

O mecanismo de cache HTTP é fortemente baseado no uso de headers que são enviados nas requisições e nas respostas.
Existem dois cabeçalhos que possibilitam o uso de cache:

### Expires

Define uma data em que o recurso será considerado obsoleto, sendo necessário ir até a origem para buscar os dados. Segundo a especificação, não devemos definir uma data maior que um ano.

![](https://i.imgur.com/qi19JUJ.png)

### Cache-Control

Como podemos ver, Expires é um cabeçalho bem limitado. Cache-Control foi introduzido na especificação do HTTP/1.1 para substituir o cabeçalho Expires. Esse novo cabeçalho traz mais opções para trabalhar com cache. Abaixo, um print da seção [Cache-Control da especificação HTTP/1.1](https://www.w3.org/Protocols/rfc2616/rfc2616-sec14.html).

![](https://i.imgur.com/Am1FBCJ.png)


### Etag

Quando um cache é expirado, devido ao tempo de validade, nem sempre indica que a resposta tenha mudado. Nesse caso, quando o usuário realizar uma requisição, será retornado exatamente o mesmo valor do cache local, que está obsoleto, no entanto, com o custo de trafegar um conteúdo já existente pela banda.

Um meio de evitar isso é utilizando Etag, que é basicamente um token de validação gerado e associado ao conteúdo de um recurso e enviado nos headers do response. Quando um cliente realizar uma requisição, pode enviar nos cabeçalhos o parâmetro “If-None-Match” com o valor da Etag, então, a aplicação irá validar se o conteúdo a ser retornado é igual ao associado a Etag. Caso o conteúdo não tenha sido alterado, será retornado um status http 304 Not modified, indicando que não houve alteração da resposta e que poderá ser usado a cópia local.

## Existem 4 tipos de cache:

**1 - Cache de aplicação**: Esse tipo é criado dentro da própria aplicação. Podem ser utilizadas ferramentas como EhCache para aplicações Java, técnicas como Memoization ou até mesmo banco de dados chave-valor em memória, como o Redis. Como faz parte da aplicação, conseguimos maior controle sobre, podendo limpá-lo a qualquer momento

**2 - Cache de gateway**: Um gateway, geralmente, fica na frente da aplicação. Sendo assim, ele pode fazer cache das requests, evitando que a aplicação tenha que processar a request.

![](https://i.imgur.com/SuJmUgM.png)

**3 - Cache de proxy**: Quando uma request é realizada, passa por diversos computadores - conhecidos como proxy - até chegar ao servidor de destino. Esses podem fazer cache e armazená-lo localmente. Esse tipo, geralmente, é referente a vários usuários.

![](https://i.imgur.com/bUQ0oQx.png)

O comportamento pode ser alterado passando o parâmetro Cache-Control: private, que indica que nenhum proxy pode armazenar a cópia daquela resposta, ideal quando trabalhamos com dados sensíveis e privados.

Outro ponto que requer atenção é que não temos controle sobre os proxy, sendo assim, não podemos limpar o cache a qualquer momento.

**4 - Cache de browser**: Mais comum no dia a dia. Gerenciado pelo próprio browser, que mantém a cópia no disco do cliente, é referente apenas àquele usuário que tem o controle nesse modelo e não será compartilhado.


## Considerações

Cache é uma técnica muito poderosa, que permite aumentarmos a performance da aplicação e melhorar a experiência do usuário final. Entretanto, como em qualquer tecnologia, precisamos ter em mente como ela funciona para utilizá-la nos cenários adequados. Analisar o tempo de vida da cópia é essencial para não gerar falsas respostas com o tempo.

Outro ponto que requer cuidado é o nível de controle sobre tipo de cache. Caso uma resposta inválida seja armazenada por um proxy, teremos que esperar que seja expirada.

Fontes:

- [https://klauslaube.com.br/2012/05/14/o-cache-e-o-http.html](https://klauslaube.com.br/2012/05/14/o-cache-e-o-http.html)
- [https://www.w3.org/Protocols/rfc2616/rfc2616-sec13.html](https://www.w3.org/Protocols/rfc2616/rfc2616-sec13.html)
- [https://developers.google.com/web/fundamentals/performance/optimizing-content-efficiency/http-caching?hl=pt-br](https://developers.google.com/web/fundamentals/performance/optimizing-content-efficiency/http-caching?hl=pt-br)
- [https://developer.mozilla.org/en-US/docs/Web/HTTP/Caching](https://developer.mozilla.org/en-US/docs/Web/HTTP/Caching)
- [https://odino.org/rest-better-http-cache/](https://odino.org/rest-better-http-cache/)
- [https://devcenter.heroku.com/articles/increasing-application-performance-with-http-cache-headers](https://devcenter.heroku.com/articles/increasing-application-performance-with-http-cache-headers)
- [https://www.mnot.net/cache_docs/#CACHE-CONTROL](https://www.mnot.net/cache_docs/#CACHE-CONTROL)
- [https://betterexplained.com/articles/how-to-optimize-your-site-with-http-caching/](https://betterexplained.com/articles/how-to-optimize-your-site-with-http-caching/)
