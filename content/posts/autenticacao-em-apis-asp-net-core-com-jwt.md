---
title: Autenticação em APIs ASP.Net Core com JWT
authors: Wellington Nascimento
type: post
publishdate: 2018-05-28
date: 2018-05-28
excerpt: Resolvendo autenticaçnao em APIs usando tokens de acesso JWT
image: https://i.imgur.com/CtZkygb.jpg
categories:
  - back-end
tags:
  - asp.net
  - JWT
  - API
---

A segurança de aplicações sempre foi, ou deveria ser, uma das principais
preocupações dos times de desenvolvimento, e nos últimos anos a autenticação de
APIs vem sendo bastante discutida nas comunidades técnicas em todo o mundo.

Existem diversas maneiras de resolver a autenticação em APIs, e uma delas é
fazendo uso de tokens de acesso, sendo o JWT (Json Web Token) um dos padrões de
tokens de acesso mais famosos e seguros da atualidade. Eu falei sobre ele em um
[artigo anterior](https://tableless.com.br/entendendo-tokens-jwt/).

Hoje irei explicar os principais pontos da criação de uma API de autenticação
com JWT em ASP.Net Core. O código completo de exemplo encontra-se em meu
[Github](https://github.com/wellingtonjhn/DemoJwt).

> Lembrando que neste artigo irei focar em uma implementação simples, mas você
> também pode usar outras soluções mais robustas para implementar autenticação,
como o [Identity Server](https://identityserver.io/), que é open source e mantido
pela comunidade.

*****

## Conceitos

Antes de ver como funciona a criação de tokens JWT no ASP.Net Core vamos lembrar
dois conceitos fundamentais.

**Autenticação **→ é o ato de identificar que o usuário é quem ele diz ser,
validando suas credenciais de acesso que geralmente são um login e uma senha.
Também podem ser usados outros meios para identificar um usuário de um sistema,
como por exemplo usando biometria ou cartões de identificação;

**Autorização **→ é o ato de verificar se o usuário pode ou não ter acesso à um
recurso ou executar determinada ação dentro do sistema. Nesse ponto o usuário já
foi identificado (autenticado) previamente. Normalmente usamos Roles ou Policies
para autorizar o acesso à determinado recurso.

Hoje vamos focar somente na autenticação. Em um próximo artigo irei mostrar como
podemos fazer a autorização dos usuários em uma API ASP.Net Core.

De qualquer modo, tenha em mente esses dois conceitos pois eles são muito
importantes.

*****

## Como criar um token JWT

No projeto de exemplo existe uma classe chamada **JwtService **de modo à
simplificar a criação de um token JWT. Ela faz uso da classe
**JwtSecurityTokenHandler** (pacote nuget
[System.IdentityModel.Tokens.Jwt](https://www.nuget.org/packages/System.IdentityModel.Tokens.Jwt/))
que é quem realmente irá gerar um Json Web Token devidamente assinado e válido.

As informações contidas no token JWT são armazenadas em formato de Claims, sendo
assim, podemos usar o método **GetClaimsIdentity** passando uma instância de um
usuário préviamente *autenticado *através de suas credenciais de acesso para
obter a identificação do usuário. Esse método irá ler as propriedades do usuário
e criar um objeto **ClaimsIdentity**, que é armazenado na claim **Subject**
representando a identidade do usuário dentro do token.

> *Por segurança recomenda-se não armazenar informações confidenciais ou sensíveis
> no token.*

Perceba que durante a criação do token informamos mais alguns dados, chamados de
Reserved Claims segundo a especificação do JWT, que são atributos não
obrigatórios (mas recomendados) usados na validação do token pelos protocolos de
segurança das APIs.

Esses dados estão encapsulados em uma classe chamada **JwtSettings**, onde uma
instância de objeto é criada no momento em que a aplicação se inicia e
registrada no container de injeção de dependências. Os valores dela estão no
arquivo de configuração da aplicação, nosso querido **appsettings.json**.

Basicamente essas claims são:

* Issuer (iss) → quem emite o token JWT;
* Audience (aud) → aplicações que podem usar o token JWT, normalmente temos apenas
um valor, mas você pode informar mais de uma;
* Expires (exp) → data e hora em que o token irá expirar;
* IssuedAt (iat) → data e hora em que o token foi emitido;

> Você pode conferir a [especificação do JWT](https://tools.ietf.org/html/rfc7519)
> para obter mais detalhes sobre as claims.

De modo a garantir a segurança o token deve ser assinado digitalmente, sendo que
para isso normalmente usamos algoritmos como
[HMAC](https://tools.ietf.org/html/rfc2104) ou
[RSA](https://tools.ietf.org/html/rfc8017).

Para assinar o token via RSA você precisa ter um certificado digital válido, já
para a assinatura HMAC é necessário apenas uma chave privada. Na aplicação de
exemplo estou usando HMAC.

<script src="https://gist.github.com/wellingtonjhn/6def8db60abe2634e753cda8f9eca619.js"></script>

A classe **JwtService **deverá ser utilizada por alguma classe de aplicação ou
até mesmo uma controller do MVC. Eu particularmente gosto muito de utilizar o
[MediatR](https://github.com/jbogard/MediatR) em meus projetos, sendo que já
falei sobre ele em um [artigo
anterior](https://medium.com/@wellingtonjhn/mediatr-com-asp-net-core-7b98ba0ca640).
Então no projeto de exemplo você encontrará a classe **AuthenticateUserHandler
**que será responsável por tratar/orquestrar um comando de login, que é
representado pela classe **AuthenticateUser** e que por sua vez, encapsula as
credenciais de acesso do usuário.

A classe **AuthenticateUserHandler **recebe em seu construtor dois parâmetros,
uma instância do repositório de usuários e uma instância do **JwtService** que
vimos anteriormente. Caso o usuário seja autenticado com sucesso pelo
repositório usamos o serviço para gerar um novo token JWT.

> No projeto de exemplo eu uso a classe InMemoryDatabaseContext e uma lista de
> User para representar o banco de dados e a tabela de usúarios, bem simples. O
foco deste artigo não é o repositório ou onde o dado está armazenado, mas em um
projeto real você deverá usar um banco de dados NoSql ou relacional.

Veja que também fazemos uso do padrão [Notification
Pattern](https://martinfowler.com/eaaDev/Notification.html) para retornar
mensagens de erro ao usuário, dessa forma não precisamos levantar Exceptions na
aplicação. Eu também falei sobre isso em um [artigo
anterior](https://medium.com/@wellingtonjhn/fail-fast-validations-com-pipeline-behavior-no-mediatr-e-asp-net-core-f3854d3c21fa).

<script src="https://gist.github.com/wellingtonjhn/d712b9f79141456563d522b29d719235.js"></script>

Agora só precisamos recepcionar uma solicitação de login na API através de uma
Controller e encaminhar para o MediatR executar o processo de autenticação na
aplicação, dessa forma nossa Controller fica bem limpa.

<script src="https://gist.github.com/wellingtonjhn/5b5ff3a0d20928b21334445f663c57f3.js"></script>

*****

## Como validar o token JWT

Com um token JWT devidamente criado, ele deverá ser enviado via **Authorization
**header em todas as demais solicitações feitas à nossas APIs, sendo assim,
precisamos garantir que esse token esteja válido.

Para isso, o ASP.Net Core já possui um middleware responsável pela validação de
tokens de acesso.

Se você usa o meta-package **Microsoft.AspNetCore.All** então você já tem esse
middleware disponível e pode começar a usá-lo de imediato, caso contrário pode
instalar o pacote nuget
[Microsoft.AspNetCore.Authentication.JwtBearer](https://www.nuget.org/packages/Microsoft.AspNetCore.Authentication.JwtBearer).

> Essa configuração deverá ser feita em todas as APIs que irão receber o token
> JWT, então você pode componentizar isso caso ache necessário.

<script src="https://gist.github.com/wellingtonjhn/5ab4cbcf6bb6025020fdd8e4ca6cb628.js"></script>

Nesse método apenas estamos adicionando os middlewares necessários no injetor de
dependências nativo do ASP.Net Core e configurando alguns parâmetros que serão
verificados quando um token JWT for recepcionado pela API, como o Issuer,
Audience, assinatura e tempo de vida do token.

Além disso, você deve instruir o pipeline do ASP.Net Core a usar a Autenticação.
Isso deve ser feito no método Configure dentro da classe Startup da API.

<script src="https://gist.github.com/wellingtonjhn/ef98761e3c039f604daa9a08ae4eccde.js"></script>

*****

## Testando

Podemos usar o [Postman](https://www.getpostman.com/) para fazer as chamadas à
nossa API. Se você não quiser instalar o Postman não tem problema, a aplicação
de exemplo faz uso do Swagger para documentar e disponibilizar uma forma de
testar API de forma simples.

Primeiramente devemos registrar um usuário em nossa API informando seu nome,
e-mail e senha de acesso.

![](https://cdn-images-1.medium.com/max/800/1*lrbQ23jGDYFpMU9sUaxmKA.png)
<span class="figcaption_hack">Criação de um novo usuário</span>

Com o usuário criado, podemo usar o e-mail e senha para fazer a autenticação. Um
token JWT é retornado em caso de sucesso. Junto com o token informamos seu tipo
“bearer” e o tempo de expiração do mesmo.

![](https://cdn-images-1.medium.com/max/800/1*SgLIbodnki8KNwQo6v3JEA.png)
<span class="figcaption_hack">Autenticação — retorna um token JWT</span>

Caso as credenciais de acesso não estejam corretas, apenas retornamos uma
mensagem informando o problema, neste caso “Usuário ou senha inválidos”.

> Nunca retorne exatamente qual foi o o motivo pelo qual a autenticação não foi
> feita, por exemplo “Senha inválida”, pois isso já mostra para um possível
atacante que possivelmente o e-mail informado existe na base e então ele pode
apenas ficar testando as senhas para obter acesso indevido.

![](https://cdn-images-1.medium.com/max/800/1*4ZT01J0WVjlXyxAGEImnNA.png)
<span class="figcaption_hack">Usuário não autenticado</span>

Com um token JWT válido podemos fazer a chamada à recursos restritos onde
somente usuários autenticados tem acesso. Nesse exemplo ele apenas retorna os
dados do próprio usuário.

Para isso você deve enviar o token no header **Authorization** da requisição
HTTP, usando a palavra “Bearer” como prefixo.

    Authorization: Bearer [token_jwt]

![](https://cdn-images-1.medium.com/max/800/1*CP-I-3DXYU1A4FxAxlitOg.png)
<span class="figcaption_hack">Consulta o profile do usuário autenticado</span>

Caso você tente consultar esse endpoint sem informar um token JWT válido, a API
irá retornar um HTTP Status Code 401 (Unauthorized) informando que você não está
autorizado à acessar esse recurso.

![](https://cdn-images-1.medium.com/max/800/1*bQxILKqo_zWc6eBwfHmnjA.png)
<span class="figcaption_hack">Usuário não está autenticado para visualizar seu profile</span>

*****

## Conclusão

Como você pode ver a autenticação em APIs é realmente necessária hoje em dia.
Não podemos expor nossas APIs para o mundo sem garantir o mínimo de segurança, a
não ser que a intenção seja realmente deixá-la aberta.

Existem muitos outros pontos a observar, como uso de Refresh Tokens,
autenticação externa via Facebook, Google e Twitter por exemplo.

Este exemplo é uma implementação simples de uma API de autenticação, e conforme
eu disse anteriormente você pode utilizar uma solução mais robusta como o
[Identity Server](https://identityserver.io/) para usar em ambiente de produção.

Espero que tenham gostado e se ficou alguma dúvida, ou tenham críticas e
sugestões entrem em contato.

Abraços!

*****

**Referências**

* [Autenticação no ASP.Net Core](https://docs.microsoft.com/en-us/aspnet/core/security/authentication/?view=aspnetcore-2.1)
* [RFC 7519: Json Web Token](https://tools.ietf.org/html/rfc7519)
* [jwt.io](https://jwt.io/)
* [7 Best Practices fot Json Web Tokens](https://dev.to/neilmadden/7-best-practices-for-json-web-tokens)