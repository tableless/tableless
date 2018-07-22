---
title: Obtendo o Usuário Logado em APIs ASP.Net Core
authors: Wellington Nascimento
type: post
publishdate: 2018-06-04
date: 2018-06-04
excerpt: Obtendo o usuário autenticado extraindo dados do token pelo JWT
categories:
  - back-end
tags:
  - asp.net
  - API
image: https://i.imgur.com/CtZkygb.jpg
---

No [artigo anterior](https://tableless.com.br/autenticacao-em-apis-asp-net-core-com-jwt/)
eu mostrei como criar uma API de autenticação em ASP.Net Core com JWT. Hoje
iremos ver como podemos obter o usuário autenticado, extraindo os dados do token
de uma forma muito simples.

Para isso o ASP.Net Core oferece uma biblioteca de abstrações HTTP (pacote nuget
[Microsoft.AspNetCore.Http.Abstractions](https://www.nuget.org/packages/Microsoft.AspNetCore.Http.Abstractions/2.1.0-rc1-final))
que contém a interface **IHttpContextAccessor.**

A classe **HttpContextAccessor** implementa tal interface, e possui uma
propriedade onde podemos obter o **HttpContext **da requisição e com ele a
identidade do usuário logado. Ela deve ser registrada no contêiner de DI como
**Singleton.**

Para simplificar as coisas, podemos criar uma classe que representa nosso
usuário logado na aplicação, em meu caso ela se chama **AuthenticatedUser**, e
recebe em seu construtor uma instância de **IHttpContextAccessor**.

<script src="https://gist.github.com/wellingtonjhn/17b2972d1e3de5d6324602267c7cdf1f.js"></script>

Também devemos fazer o registro dessa classe no contêiner de DI, e ela deve ser
utilizada onde for necessário obter o usuário logado.

<script src="https://gist.github.com/wellingtonjhn/c1d158376291764a6efa82553f33aa0a.js"></script>

> O HttpContext será recriado à cada nova requisição HTTP na aplicação.

Com isso podemos injetar um **AuthenticatedUser **em qualquer classe que
precisarmos dele.

![](https://cdn-images-1.medium.com/max/800/1*ezhfYijWeoaRVXFB0rWHQA.png)

*****

## Conclusão

Fazendo uso do **HttpContextAccessor** em conjunto com a injeção de
dependências, temos um jeito fácil de obter o usuário autenticado e utilizá-lo
em qualquer camada de nossa aplicação conforme a necessidade. Em versões
anteriores do ASP.Net isso também era possível, porém um pouco mais trabalhoso.
Com isso temos á nossa disposição um recurso muito poderoso que nos dá muita
flexibilidade ao se trabalhar com o contexto da requisição HTTP em nossas
aplicações.

Espero que tenham gostado e se ficou alguma dúvida, ou tenham críticas e
sugestões entrem em contato.

Abraços!
