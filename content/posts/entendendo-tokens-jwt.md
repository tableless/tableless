---
title: Entendendo tokens JWT (Json Web Token)
authors: Wellington Nascimento
type: post
publishdate: 2018-03-12
date: 2018-03-11
excerpt: O JWT é um padrão (RFC-7519) de mercado que define como transmitir e armazenar objetos JSON de forma compacta e segura entre diferentes aplicações.
image: https://i.imgur.com/U6JBKKI.png
categories:
  - back-end
tags:
  - jwt
  - json
  - javascript
  - csharp
---

O JWT é um padrão ([RFC-7519](https://tools.ietf.org/html/rfc7519)) de mercado
que define como transmitir e armazenar objetos JSON de forma compacta e segura
entre diferentes aplicações. Os dados nele contidos podem ser validados a
qualquer momento pois o token é assinado digitalmente.

Ele é formado por três seções: **Header, Payload e Signature.**

## Header

O Header é um objeto JSON que define informações sobre o tipo do token (typ),
nesse caso JWT, e o algorítmo de criptografia usado em sua assinatura (alg),
normalmente [HMAC SHA256](https://tools.ietf.org/html/rfc2104) ou
[RSA](https://tools.ietf.org/html/rfc8017).

```
{
  "alg": "HS256",
  "typ": "JWT"
}
```

<span class="figcaption_hack">Header</span>

## Payload

O Payload é um objeto JSON com as Claims (informações) da entidade tratada,
normalmente o usuário autenticado.

Essas claims podem ser de 3 tipos:

**Reserved claims:** atributos não obrigatórios (mas recomendados) que são usados na validação do token pelos protocolos de segurança das APIs.

- sub (subject) = Entidade à quem o token pertence, normalmente o ID do usuário;
- iss (issuer) = Emissor do token;
- exp (expiration) = Timestamp de quando o token irá expirar;
- iat (issued at) = Timestamp de quando o token foi criado;
- aud (audience) = Destinatário do token, representa a aplicação que irá usá-lo.

Geralmente os atributos mais utilizados são: **sub**, **iss **e **exp**.

**Public claims:** atributos que usamos em nossas aplicações. Normalmente armazenamos as informações do usuário autenticado na aplicação.

- name
- roles
- permissions

**Private claims:** atributos definidos especialmente para compartilhar informações entre aplicações.

```
{
  "sub": "1234567890",
  "name": "John Doe",
  "admin": true
}
```

<span class="figcaption_hack">Payload</span>

> Por segurança recomenda-se não armazenar informações confidenciais ou sensíveis no token.

## Signature

A assinatura é a concatenação dos hashes gerados a partir do Header e Payload
usando base64UrlEncode, com uma chave secreta ou certificado RSA.

![](https://i.imgur.com/cs0LfgL.png)
<span class="figcaption_hack">Signature</span>

Essa assinatura é utilizada para garantir a integridade do token, no caso, se
ele foi modificado e se realmente foi gerado por você.

Isso previne ataques do tipo man-in-the-middle, onde o invasor poderia
interceptar a requisição e modificar seu conteúdo, desta forma personificando o
usuário com informações falsas. Caso o payload seja alterado, o hash final não
será válido pois não foi assinado com sua chave secreta.

> Apenas quem está de posse da chave pode criar, alterar e validar o token.

## Resultado final

O resultado final é um token com três seções (header, payload, signature)
separadas por *“.” — ponto*.

![](https://i.imgur.com/lAHURmd.png)
<span class="figcaption_hack">Token JWT</span>

## Usando o token

Ao fazer login em um serviço de autenticação um token JWT é criado e retornado
para o client. Esse token deve ser enviado para as APIs através do header
**Authorization **de cada requisição HTTP com a flag **Bearer**, conforme
ilustra o diagrama abaixo.

    Authorization: Bearer <token>

![](https://i.imgur.com/U6JBKKI.png)
<span class="figcaption_hack">Diagrama de sequência usando token JWT</span>

Em posse do token, a API não precisa ir até o banco de dados consultar as
informações do usuário, pois contido no próprio token JWT já temos suas
credenciais de acesso.

## Referências

- [RFC 7519 (Json Web Token Specification)](https://tools.ietf.org/html/rfc7519)
- [RFC 2104 (HMAC: Keyed-Hashing for Message Authentication)](https://tools.ietf.org/html/rfc2104)
- [RFC 8017 (RSA Cryptography Specification)](https://tools.ietf.org/html/rfc8017)
- [jwt.io](https://jwt.io/)
- [Auth0](https://auth0.com/docs/jwt)

*****

Nos próximos artigos mostrarei como criar uma API em ASP.NET Core com
autenticação usando JWT.

Espero que tenham gostado e se ficou alguma dúvida ou tenham críticas e
sugestões, por favor entrem em contato.

