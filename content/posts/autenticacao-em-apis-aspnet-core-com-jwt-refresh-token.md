+++
authors = "Wellington Nascimento"
categories = ["back-end"]
date = "2018-08-02T08:46:00+00:00"
excerpt = "Saiba o que é Refresh Token e como usá-lo com JWT e ASP.Net Core"
image = "https://i.imgur.com/l4rXdhd.jpg"
publishdate = "2018-08-02T08:00:00+00:00"
tags = ["aspnet", "jwt"]
title = "Autenticação em APIs ASP.Net Core com JWT — Refresh Token"
type = "post"

+++
Quando trabalhamos com autenticação baseada em tokens JWT temos que considerar que ele tem um tempo de expiração que irá invalidá-lo em determinado momento. Em alguns cenários pode ser interessante obter um novo token de acesso sem precisar forçar o usuário a fazer um novo login informando seu usuário e senha. Isso é muito comum quando trabalhamos com aplicativos mobile. 

Para esse artigo usei o mesmo exemplo de código de um [artigo > anterior](https://tableless.com.br/autenticacao-em-apis-asp-net-core-com-jwt/) onde mostro como implementar uma API de Autenticação simples com JWT. Você pode conferir em meu [Github](https://github.com/wellingtonjhn/DemoJwt). 

## O que é Refresh Token? 

Imagine que o cliente faça login no seu aplicativo informando usuário e senha, sua API devolve um token JWT que seu app deverá armazenar internamente. Sabemos que em todas as requisições seguintes o app deverá enviar o token no header Authorization para a API que irá consumir. 

O cliente coloca o app em background e só volta a usá-lo após algumas horas. Muito provavelmente o token de acesso criado anteriormente já expirou e ao tentar fazer qualquer chamada na API o app irá receber um HTTP Status Code 401 — Unauthorized. Você tem duas opções, a) redirecionar o cliente para a tela de login e forçá-lo a fazer um novo acesso, b) pedir para que a API de autenticação forneça um novo token JWT válido de forma transparente para o cliente. 

Caso seu app não necessite que o cliente faça um novo login a cada tempo de expiração, como é o caso de aplicativos bancários por exemplo, você pode optar por gerar um novo token de forma transparente para o cliente fazendo uso do que chamamos de **Refresh Token**. 

Para isso, além do token de acesso principal, você deve gerar um token secundário com tempo de expiração maior. Por exemplo, se o **access_token** expira em 8h, seu **refresh_token **irá expirar em 16 horas (não precisar ser necessariamente esse tempo, você deve definir um tempo adequado). 

O refresh_token dever ser devolvido para seu aplicativo junto com o token JWT principal no momento do login. O app então deverá armazenar o refresh_token internamente, assim como já faz com o access_token. 

![](https://cdn-images-1.medium.com/max/1000/1*zdyoGW-4EVEATVTwSvtlqw.png) <span class="figcaption_hack">Conjunto de tokens de acesso</span> 

## Como implementar? 

No projeto de exemplo, você irá encontrar uma classe chamada **JwtService **que é responsável por gerar um token JWT. O que eu fiz foi implementar a criação do Refresh Token da seguinte forma. 

<script src="https://gist.github.com/wellingtonjhn/d98ac8c74c016973891d76340b088d09.js"></script>

O método **CreateRefreshToken** irá gerar um valor aleatório de 32 bytes, que é convertido para string, onde em seguida são removidos alguns caracteres indesejados. Nada demais!! 

Esse método deverá ser usado no momento da criação do token JWT, no método **CreateJsonWebToken**. 

Como vocês já sabem, eu gosto muito de usar o **MediatR** em meus projetos, inclusive já escrevi um [artigo](https://medium.com/wellingtonjhn/mediatr-com-asp-net-core-7b98ba0ca640) sobre ele. 

Tenho um request chamado **Authenticate**, que irá disparar o handler **AuthenticateHandler**. 

A classe Authenticate não tem nada demais, ela contém apenas as propriedades necessárias para o input dos dados pelo aplicativo, como e-mail, password, refresh token e grant type, além de algumas validações. 

<script src="https://gist.github.com/wellingtonjhn/5d0691d91b8696d50e356aa96ab749ff.js"></script>

Na classe **AuthenticateHandler**, que é responsável por responder à uma solicitação de login, no método **Handle** verifico qual tipo de autenticação está sendo feita através da propriedade **GrantType** do request do MediatR e então executo o método apropriado. 

* **GrantType == password →** método comum de autenticação, onde verificamos as credenciais de acesso fornecidas pelo usuário, como usuário e senha por exemplo; * **GrantType == refresh_token →** método de autenticação baseado no refresh token que geramos anteriormente. 

Isso é necessário pois normalmente existe apenas um único endpoint de autenticação na API que irá gerar um token de acesso, e é através do GrantType que diferenciamos a forma de autenticação. Existem implementações diferentes disso, onde temos dois endpoints de autenticação, um para validar as credenciais inseridas pelo usuário (login e senha) e outro exclusivo para o Refresh Token. Em nosso exemplo vamos usar um único endpoint. 

Além disso, veja que ao gerar um token JWT no método **HandleJwt**, o Refresh Token gerado é salvo no banco de dados, sempre sobrescrevendo o anterior de forma que só exista um único hash de refresh por usuário. Isso é importante pois quando o app tentar fazer a atualização do token de acesso, devemos verificar se o refresh token informado é válido, nesse caso, no método **HandleRefreshToken **faço uma busca no banco de dados pelo hash informado, verifico se ele realmente existe e se está expirado, lembre-se que ele também tem um tempo de expiração. Além dessas duas validações, você pode implementar um mecanismo de revogação do refresh token, para inutilizá-lo imediatamente, e então poderia fazer essa validação de revogação nesse momento. 

Caso o refresh token seja válido, basta consultar os dados do usuário no banco e gerar um novo JWT, bem como um novo refresh token. 

A controller na API é bem simples, ela apenas recebe o request HTTP de login, o mecanismo de Model Binding do ASP.Net se encarrega de fazer o bind apropriado para o objeto **Authenticate**, e então ele é enviado para o MediatR que irá disparar o handler **AuthenticateHandler** que vimos anteriormente. 

<script src="https://gist.github.com/wellingtonjhn/4f878b2ebe7f261e0e65b32022922ff2.js"></script>

Além disso, existe a configuração do tempo de expiração do Refresh Token, que fica no arquivo **appsettings.json** da nossa API e é representado pela chave **RefreshTokenValidForMinutes**. Nesse exemplo o access_token (JWT) tem um tempo de expiração de 60 minutos, já o refresh_token irá expirar em 120 minutos. Como eu disse anteriormente, o tempo de expiração do refresh token deve ser maior que o tempo de expiração do JWT. Essa configuração é materializada na classe **JwtSettings**. 

<script src="https://gist.github.com/wellingtonjhn/7e4b9a81c08673bd91aa3d4255c36900.js"></script>

## Testando 

Ao executar a API uma tela do Swagger será aberta, mas nesse caso vou usar o Postman para fazer os testes. 

Com a API em execução e com um usuário criado, devo fazer um novo login informando um usuário e senha. Note que informei o **GrantType** com o valor **password**. Caso as credenciais informadas estejam corretas um token JWT é devolvido. 

![](https://cdn-images-1.medium.com/max/1000/1*qsnS5_qqX4No6jXvZ-nlOQ.png) <span class="figcaption_hack">Login na API de Autenticação</span> 

Conforme disse anteriormente, o aplicativo deve armazenar os valores de **access_token** e também do **refresh_token **internamente para posterior uso. 

Em posse do token JWT, o app deverá enviá-lo através do header **Authorization **em todas as demais requisições nas APIs que são utilizadas. Quando o token estiver expirado, a API irá retornar um HTTP Status Code 401 — Unauthorized. Nesse momento o app pode pedir um novo token de acesso fazendo uso do hash de refresh token armazenado, desde que ele também não esteja expirado, sendo que nesse caso o usuário deveria fazer um novo login. 

Para pedir um novo token basta chamar novamente o endpoint de login, entretanto agora devemos informar o **GrantType** com o valor **refresh_token** e o hash armazenado anteriormente. Caso tudo esteja certo, um novo token JWT é devolvido, juntamente com um novo hash de refresh token. 

![](https://cdn-images-1.medium.com/max/1000/1*TTE-Zpg9mzPVuU7tOjqoIA.png) 

Caso o hash de refresh não seja válido a API de autenticação poderá exibir as devidas mensagens de erro durante a atualização do token. 

![](https://cdn-images-1.medium.com/max/1000/1*Eo5mAqtD76kRYZxevL8v-g.png) <span class="figcaption_hack">Refresh Token não encontrado</span> 

![](https://cdn-images-1.medium.com/max/1000/1*PWI_8LYcTwwy1vM8KID9ug.png) <span class="figcaption_hack">Refresh Token expirado</span> 

E com isso temos um mecanismo simples de atualização de tokens de acesso. 

## Conclusão 

Conforme vimos, a atualização de tokens de acesso é um recurso muito poderoso e pode nos poupar algumas dores de cabeça, afinal, ninguém quer um cliente insatisfeito por ter que fazer login seguidas vezes em seu aplicativo. 

Lembrando que essa é apenas uma das várias formas de implementar o Refresh Token em sua API de Autenticação. Se você procurar, irá encontrar outros modelos de implementação. 

Soluções como o [Identity Server](https://identityserver.io/) já possuem esse e outros recursos de segurança nativos e mais completos, sendo essa demo apenas um modelo simples para implementar autenticação em seu app. 

Espero que tenham gostado, e se ficou alguma dúvida ou tenham críticas e sugestões, não deixem de entrar em contato. 

Abraços!