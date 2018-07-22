---
title: Compressão de Respostas em APIs ASP.Net Core
authors: Wellington Nascimento
type: post
publishdate: 2018-03-28
date: 2018-03-21
excerpt: Ao desenvolver uma API, é muito importante nos preocuparmos com o tráfego de mensagens gerado, pois largura de banda é um recurso limitado.
categories:
  - back-end
  - API
tags:
  - asp.net
  - API
image: https://i.imgur.com/CtZkygb.jpg
---

Quando estamos desenvolvendo nossas APIs é muito importante nos preocuparmos com
o tráfego de mensagens que ela irá gerar, pois largura de banda é um recurso
limitado e não podemos esperar que nossos clientes irão poder contar com
conexões de banda larga via fibra ótica à todo momento, ou ainda, conexões 4G
ultra velozes sem limites de dados. Infelizmente essa não é a nossa realidade
ainda... =/

O que podemos fazer é reduzir o tamanho das respostas em nossas APIs, e isso tem
um impacto muito grande tanto financeiro, quanto de performance. Lembre-se que a
grande maioria dos players de nuvem, ou todos eles, cobram por tráfego de dados,
e além de tentar reduzir o custo devemos concordar que quanto menor for o
tamanho dos dados, mais rápida será a resposta para quem estiver consumindo
nossas APIs e assim melhorando a performance de nosso sistema de uma forma
geral.

Uma maneira de diminuir o tamanho das mensagens trafegadas é implementando um
mecanismo de compressão de respostas.

A compressão de respostas pode ser feita diretamente nos servidores web como o
IIS e Nginx, só para citar alguns. Já o Kestrel e HTTP.sys não possuem esse
recurso nativamente até o momento em que escrevo esse artigo.

---

## Middleware de Compressão de Respostas do ASP.Net Core

O ASP.Net Core conta com alguns middlewares muito úteis, e um deles serve
justamente para comprimir as respostas de nossas APIs.

Para isso basta adicionarmos uma referência ao pacote nuget
[Microsoft.AspNetCore.ResponseCompression](https://www.nuget.org/packages/Microsoft.AspNetCore.ResponseCompression/)
e seguir os trechos de código abaixo:

<script src="https://gist.github.com/wellingtonjhn/79b9e47b7576d0fa9dfedba7d1696131.js"></script>

O que fizemos foi a chamada de dois métodos bem específicos, nas linhas 12 e 23.
Esses métodos de extensão são disponibilizados quando referenciamos o componente
mencionado acima.

Linha 12 → foi adicionado o método “ services.AddResponseCompression()”, que é
responsável por adicionar o serviço de compressão de respostas no injetor de
dependências nativo do ASP.Net Core.

Linha 23 → foi adicionado o método “ app.UseResponseCompression()”, que adiciona
o middleware de compressão de respostas no pipeline do ASP.Net Core.

Com apenas duas linhas de código a compressão de resposta já irá funcionar, mas
se quiser ir além, poderá customizar alguns aspectos como otimizar ainda mais a
compressão, ou ainda, criar seu próprio algorítmo conforme podemos ver abaixo —
os trechos de código de customização foram extraídos da documentação oficial que
você encontra no fim deste artigo.

<script src="https://gist.github.com/wellingtonjhn/a15306d95a161328cbec404e356a446c.js"></script>

> Use a compressão de respostas nativa do servidor web sempre que possível, pois
> ela tende a ter melhor performance que o middleware de compressão.

---

## Como funciona?

Esse middleware irá interceptar todos os retornos das suas controllers e usar um
algorítmo de compressão para diminuir o tamanho da resposta. Por padrão ele irá
usar o algorítmo Gzip. Apenas para conhecimento, existe outro algorítmo de
compressão também muito famoso chamado Deflate.

Para ver a compressão funcionando na prática podemos fazer uma chamada à nossa
API de testes com dados fake através do navegador mesmo, conforme você pode ver
abaixo:

![Chamada da API com dados fake no navegador](https://i.imgur.com/wMlWHGD.png)

E então através do [Fiddler](https://www.telerik.com/fiddler) podemos conferir o
tamanho da resposta, que nesse exemplo foi de **1.143 bytes**, além disso foi
adicionado o header **Content-Encoding: gzip**, que indica que essa resposta foi
compactada utilizando o algorítmo Gzip conforme o esperado.

![Inspeção do requet no Fiddler — com compressão de resposta](https://i.imgur.com/uslwiCb.png)

Em uma requisição sem a compactação, podemos ver o tamanho da reposta em **6.174
bytes**, e não existe o header **Content-Encoding** indicando o algoritmo de
compressão.

![Inspeção do requet no Fiddler — sem compressão de resposta](https://i.imgur.com/9gvAumF.png)

> Verificando a documentação oficial, você irá observar uma nota de atenção para
> não tentar comprimir arquivos menores que 1.000 bytes, pois a compressão não
será eficiente, o que pode inclusive resultar em uma resposta com tamanho maior
ao original sem a compressão, além do tempo de processamento que foi gasto.

Assim podemos perceber que com uma simples adição ao nosso pipeline do ASP.Net
conseguimos comprimir a resposta de nossa API, e dessa forma reduzir o tráfego
de dados de nosso serviço.

É isso pessoal, espero que tenham gostado e se ficou qualquer dúvida ou tenham
sugestões e críticas, fico à disposição para bater um papo.


## Referências

- [Response Compression Middleware for ASP.NET Core](https://docs.microsoft.com/en-us/aspnet/core/performance/response-compression?tabs=aspnetcore2x)<br>
- [Microsoft.AspNetCore.ResponseCompression Nuget Package](https://www.nuget.org/packages/Microsoft.AspNetCore.ResponseCompression/)
- [Aspnetcore](https://medium.com/tag/aspnetcore?source=post)
- [Data Compression](https://medium.com/tag/data-compression?source=post)
