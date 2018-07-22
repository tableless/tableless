---
title: 'Documentação de APIs com Swagger no ASP.Net Core'
authors: Wellington Nascimento
type: post
publishdate: 2018-06-11
date: 2018-06-11
excerpt: 'Criando uma documentação de API utilizando Swagger'
image: https://cdn-images-1.medium.com/max/2000/1*_6Abwv6Dd_I8GBtlRp6XeA.png
categories:
  - back-end
tags:
  - asp.net
  - Swagger
  - API
---

Não basta apenas desenvolver nossas aplicações e largar na mão dos times que
farão uso delas. Uma boa documentação é um dos quesitos chave para o sucesso de
todo sistema hoje em dia, ainda mais em um mundo de APIs que vivemos hoje, onde
existem cada vez mais integrações entre aplicações e serviços.

Imagina você ter que entrar em contato com o desenvolvedor de determinada API
para saber quais endpoints você precisa usar, e quais são os parâmetros
necessários para a correta integração com seu sistema. Tanto você, quanto ele
ficarão loucos com as trocas de e-mails e telefonemas. Você também não precisa
escrever um documento que detalhe o funcionamento de sua API no Word. Esqueça
isso!

Hoje vamos ver como criar uma documentação de API efetiva com o Swagger.

> Não deixe de conferir um dos meus projetos de exemplo, onde eu faço uso do
> Swagger, e que está disponível em meu
[Github](https://github.com/wellingtonjhn/DemoJwt).



## O que é o Swagger?

O Swagger é um framework open source que ajuda os desenvolvedores no desenho,
especificação e documentação de suas APIs. Ele segue a iniciativa [Open
API](https://www.openapis.org/) que busca a padronização de APIs REST. Essa
especificação basicamente descreve os recursos de suas APIs, como endpoints,
parâmetros de entrada, objetos de retorno, códigos HTTP, métodos de
autenticação, entre outros.

O Swagger possui algumas ferramentas que nos auxiliam em todo o processo de
desenvolvimento de nossas APIs, entre elas:

* [Swagger Editor](https://editor.swagger.io/) → editor online para criar
especificações Open API;
* [Swagger UI](https://swagger.io/tools/swagger-ui/) → renderiza especificações
Open API em uma interface interativa;
* [Swagger CodeGen](https://github.com/swagger-api/swagger-codegen) → gera
templates de código a partir de uma especificação Open API.



## Configurando o Swagger no ASP.Net Core

Não é necessário criar um arquivo de especificação do Swagger ao utilizar o
ASP.Net, podemos gerar a especificação em tempo de execução de forma automática
usando a biblioteca **Swashbuckle**, que conta com versões para ASP.Net (full
framework) e ASP.Net Core.

Primeiramente você deve instalar o pacote nuget **Swashbuckle.AspNetCore **em
seu projeto de API.


Em seguida, no arquivo *Startup.cs* do seu projeto será necessário adicionar a
configuração necessária para a geração da especificação do Swagger. Isso deve
ser feito no método *ConfigureServices*.

Com isso você já pode rodar sua API e acessar a documentação através do endpoint
**/swagger**. Se você quiser modificar essa rota, basta alterar a propriedade
**RoutePrefix **da configuração ao chamar o método **UseSwaggerUI**.

![](https://cdn-images-1.medium.com/max/1000/1*wRnURp4-4u-Ypi3DWE9bhQ.png)
<span class="figcaption_hack">Listagem de endpoints no Swagger</span>

Perceba que você pode fazer as chamadas para os recursos de sua API diretamente
pela interface do Swagger. Informe os parâmetros necessários e clique no botão
**Try it out!**.

![](https://cdn-images-1.medium.com/max/1000/1*xVdzvLWKLl_fR--rieCnCA.png)
<span class="figcaption_hack">Teste de endpoint pelo Swagger</span>

Caso sua API necessite de autenticação para ser acessada, você pode configurar o
schema de autenticação usando o método **AddSecurityDefinition**. No meu caso
estou usando **ApiKeyScheme**, que representa autenticação baseada em token.
Para conhecer outros schemas de autenticação do Swagger recomendo a leitura da
[documentação](https://swagger.io/docs/specification/authentication/).

Com isso, o botão **Authorize **será exibido no cabeçalho da interface do
Swagger.

![](https://cdn-images-1.medium.com/max/800/1*cTuk5d5g429A6wXUCQr1SA.png)
<span class="figcaption_hack">Botão Authorize na interface do Swagger</span>

Ao clicar nele será exibida uma janela onde você deve inserir seu token de
acesso, no meu caso estou utilizando schema de autenticação Bearer com JWT.

![](https://cdn-images-1.medium.com/max/1000/1*sz4Gnq4K6fxMIeLIlztSDQ.png)

Você também pode usar os comentários de documentação XML (summary) do .Net e
deixar sua documentação do Swagger mais rica. Para isso use o método
**IncludeXmlComments **informando o path onde está o arquivo gerado com os
comentários.

Para ativar a geração do arquivo de comentários XML, vá nas propriedades do seu
projeto de API, clique na guia **Build**, e em seguida marque a opção **“XML
documentation file”***, deixando o path padrão*.

![](https://cdn-images-1.medium.com/max/800/1*qYwawax2WaAZ6y7I68j5nw.png)

Durante o build de sua aplicação o arquivo de documentação XML será gerado no
local especificado e com isso sua documentação do Swagger irá exibir essas
mesmas informações.



## Conclusão

Como vimos, com a simples adição do Swagger em nossa aplicação, qualquer
consumidor conseguirá de forma efetiva usar nossa API.

Além dos recursos descritos nesse artigo, você também pode criar filtros de
execução do Swagger, onde por exemplo, você pode omitir determinadas
propriedades de modelos da documentação, exibir os endpoints em caixa baixa.

Caso você use versionamento em suas APIs será necessário fazer a configuração no
Swagger, mas deixarei para explicar isso em outro artigo.

Espero que tenham gostado!

Se ficou qualquer dúvida ou tenham críticas e sugestões, não deixem de entrar em
contato.

Abraços!

*****

## Referências

* [https://swagger.io](https://swagger.io/)
* [https://swagger.io/docs/specification/about/](https://swagger.io/docs/specification/about/)
* [https://www.openapis.org](https://www.openapis.org/)
* [Swashbuckle.AspNetCore](https://github.com/domaindrivendev/Swashbuckle.AspNetCore)
