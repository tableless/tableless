---
title: API para Autenticar usuários com JWT e Passport
author: Jscrambler
type: post
date: 2016-10-19
url: /autenticar-usuarios-com-jwt-e-passport/
titulo_personalizado:
  - 'API para autenticar usuários com <strong>JWT e Passport</strong>'
categories:
  - Destaques
  - JavaScript
tags:
  - api
  - Authentication
  - JavaScript
  - JWT
  - Passport
  - Web Development

---
Neste artigo nós vamos explorar os principais conceitos e implementações da autenticação de usuário utilizando o mecanismo chamado JWT (_[JSON Web Token][1]_) por meio de um módulo Passport. Afinal, este é um importante passo para se certificar de que os usuários façam uma autenticação segura dentro de uma API baseada em REST.

Antes de começarmos, vamos criar uma simples API em REST, que será utilizada ao longo deste post. Para simplificar nosso exemplo, nós vamos criar uma Express API. Para começar, vamos configurar nosso projeto, abrir o terminal e digitar o seguinte comando:

<pre class="lang-bash">mkdir my-api
cd my-api
npm init</pre>

O **npm init** mostra um questionário simples para configurar algumas descrições e gerar o arquivo **package.json**, o principal arquivo que usaremos para instalar alguns módulos para nosso projeto. Você pode responder cada questão como preferir. Depois disso, instale o framework **express** e o módulo **body-parser** usando este comando:

<pre class="lang-bash">npm install express body-parser --save</pre>

Agora que temos o módulo Express instalado, vamos escrever nosso código para a API. Para isso, crie o arquivo **index.js** com o código abaixo:

<pre class="lang-js">// index.js
var express = require("express");
var bodyParser = require("body-parser");
var app = express();

app.use(bodyParser.json());

app.get("/", function(req, res) {
  res.json({status: "My API is alive!"});
});

app.listen(3000, function() {
  console.log("My API is running...");
});
module.exports = app;
</pre>

Neste post usaremos um array simples de dados de usuários para facilitar a implementação do JWT. No entanto, em aplicações reais é altamente recomendável usar um banco de dados em vez de um simples array. Então, usaremos esse array apenas para exemplo. Nós precisaremos de uma lista de dados de usuários a qual será utilizada para verificar se a solicitação é de um usuário autenticado. Para isso, crie o arquivo **users.js** com o código a seguir:

<pre class="lang-js">// users.js
// Fake list of users to be used in the authentication
var users = [
{id: 1, name: "John", email: "john@mail.com", password: "john123"},
{id: 2, name: "Sarah", email: "sarah@mail.com", password: "sarah123"}
];

module.exports = users;
</pre>

Agora nós temos uma API simples o suficiente para explorar como implementar a autenticação JWT nas próximas sessões.

## Introdução ao Passport.js e JWT

### SOBRE O PASSPORT.JS

Há um módulo Node.js muito bacana e fácil de trabalhar com autenticação de usuários, e ele é chamado de **Passport**.

Passport é um framework extremamente flexível e modular. Ele permite que você trabalhe com as principais estratégias de autenticação, que são: **Basic & Digest**, **OpenID**, **OAuth**, **OAuth 2.0** e **JWT**. Além disso, ele também permite trabalhar com serviços de autenticação externos, como **Facebook**, **Google+**, **Twitter**, entre outros. Aliás, no site oficial da framework, **há uma lista com mais de 300 estratégias de autenticação**, criadas e mantidas por terceiros.

<img class="alignnone size-full wp-image-56151" src="http://tableless.com.br/uploads/2016/10/site-passport.jpg" alt="site-passport" width="1135" height="617" />

O site oficial do Passport é: [passportjs.org][2].

### SOBRE A JWT

JWT (_JSON Web Tokens_) é uma estratégia de autenticação para APIs em REST simples e segura. Trata-se de um padrão aberto para autenticações web e é totalmente baseada em requests JSON entre o cliente e servidor. Seu mecanismo de autenticação funciona da seguinte maneira:

  1. O cliente faz uma solicitação uma única vez ao enviar as credenciais de login e senha;
  2. O servidor valida as credenciais e, se tudo estiver certo, ele retorna para o cliente um JSON com um token que codifica dados de um usuário logado no sistema;
  3. Após receber o token, o cliente pode armazená-lo da forma que preferir, seja por LocalStorage, Cookie ou outros mecanismos de armazenamento do lado do cliente;
  4. Toda vez que o cliente acessa uma rota que requere autenticação, ele apenas envia esse token para a API para autenticar e liberar os dados de consumo;
  5. O servidor sempre valida esse token para permitir ou bloquear uma solicitação de cliente.

<img class="alignnone size-full wp-image-56152" src="http://tableless.com.br/uploads/2016/10/site-jwt.jpg" alt="site-jwt" width="1135" height="609" />

Para detalhes específicos sobre JWT, acesse [jwt.io][3].

## Instalando Passport e JWT

Para começar a diversão, nós utilizaremos os seguintes módulos:

  * **passport**: como um mecanismo de autenticação;
  * **passport-jwt**: como estratégia de autenticação JWT para Passport;
  * **jwt-simple**: como codificador e decodificador para tokens JSON;

Agora, vamos instalar tudo isso rodando este comando:

<pre class="lang-bash">npm install passport passport-jwt jwt-simple --save</pre>

Para começar esta implementação, primeiro nós vamos criar um arquivo **config.js** para adicionar dois itens de configuração para o JWT (**jwtSecret** e **jwtSession**):

<pre class="lang-js">// config.js
module.exports = {
jwtSecret: "MyS3cr3tK3Y",
jwtSession: {session: false}
};</pre>

O campo **jwtSecret** mantém uma string de chave secreta que serve como base para **codificar** e **decodificar** os tokens. É altamente aconselhável utilizar uma string complexa com vários caracteres diferentes e **nunca compartilhar essa chave secreta em público**, pois se isso vazar, você deixará sua aplicação vulnerável, permitindo que qualquer pessoa má intencionada acesse o sistema e gerencie os tokens de usuários logados sem informar as credenciais corretas no processo de autenticação.

Para finalizar, o último campo incluído é o **jwtSession**, que possui o objeto {session:false}. Esse item é utilizado para informar o Passport que a API não irá gerenciar a sessão.

## Implementando a autenticação JWT

Agora que já temos as configurações do Passport e JWT prontas, vamos implementar as principais regras sobre quais o cliente será autenticado em nossa API. Para começar, vamos implementar as regras de autenticação, que também terão funções intermediárias fornecidas pelo Passport para utilizar dentro das rotas da API. Este código terá duas funções principais e uma intermediária. A middleware (intermediária) será executada no momento em que a aplicação começa a rodar, e ela basicamente recebe em sua ligação uma **payload** (carga útil) que contém um **JSON decodificado**, o qual foi decodificado utilizando a chave secreta **cfg.jwtSecret**. Esse **payload** útil terá o **ID** atribuído, o qual será o **ID** do usuário para ser utilizado como argumento para procurar um usuário no banco de dados. No nosso caso, esse **ID** será utilizado para pegar um dado de usuário da array de usuários do arquivo **users.js**. Como essa função intermediária será acessada frequentemente, para evitar processos desnecessários, vamos enviar um simples objeto contendo apenas o **ID** do usuário com a seguinte função de retorno:

<pre class="lang-js">done(null, {id: user.id});</pre>

Essa middleware será injetada por meio da função **passport.use(strategy)**. Para finalizar, duas funções serão inclusas por meio do Passport para serem utilizadas na aplicação. São as funções **initialize()**, que aciona o Passport e a **authenticate()**, que é utilizada para autenticar o acesso para uma rota.

Para entender melhor essa implementação, vamos criar na pasta raiz o arquivo **auth.js** com o seguinte código:

<pre class="lang-js">// auth.js
var passport = require("passport");
var passportJWT = require("passport-jwt");
var users = require("./users.js");
var cfg = require("./config.js");
var ExtractJwt = passportJWT.ExtractJwt;
var Strategy = passportJWT.Strategy;
var params = {
  secretOrKey: cfg.jwtSecret,
  jwtFromRequest: ExtractJwt.fromAuthHeader()
};

module.exports = function() {
  var strategy = new Strategy(params, function(payload, done) {
    var user = users[payload.id] || null;
    if (user) {
      return done(null, {id: user.id});
    } else {
      return done(new Error("User not found"), null);
    }
  });
  passport.use(strategy);
  return {
    initialize: function() {
      return passport.initialize();
    },
    authenticate: function() {
      return passport.authenticate("jwt", cfg.jwtSession);
    }
  };
};</pre>

A validação da JWT começa quando uma nova estratégia é instanciada pelo **new Strategy()**. Esse objeto, então, recebe dois importantes argumentos:

  * **secretOrkey**: a chave secreta JWT
  * **jwtFromRequest**: define para onde os tokens serão enviados na resposta (header, querystring, body). Veja mais neste link: [npmjs.com/package/passport-jwt#extracting-the-jwt-from-the-request][4].

Dentro dos callbacks da estratégia você pode fazer qualquer validação que preferir. No nosso caso, nós apenas estamos buscando pelo usuário correto se a solicitação enviar o **payload.id** correto. **No mundo real, você pode escrever autenticações para encontrar usuários em uma base de dados.**

Agora, para carregar o **auth.js** durante o tempo de boot (inicialização) do servidor e iniciar o middleware do Passport pelo **app.use(auth.initialize())**, edite o arquivo **index.js** da seguinte forma:

<pre class="lang-js">// index.js
var express = require("express");
var bodyParser = require("body-parser");
var auth = require("./auth.js")();
var app = express();

app.use(bodyParser.json());
app.use(auth.initialize());

app.get("/", function(req, res) {
  res.json({status: "My API is alive!"});
});

app.listen(3000, function() {
  console.log("My API is running...");
});

module.exports = app;</pre>

## Gerando tokens para usuários autenticados

Para finalizar a autenticação em JWT, nós vamos criar uma rota para gerar tokens de usuários que irão se autenticar utilizando seus e-mails e senhas no sistema, e vamos também fazer uma refatoração na rota principal para que seus acessos carreguem apropriadamente a autenticação dos dados de usuário. Ao fazer isso, nós finalizamos essa etapa de autenticação, tornando nossa aplicação mais confiável e segura.

Agora, vamos criar o **/token** finalizador. Esta rota será responsável por gerar um token codificado com uma **payload**, dada ao usuário que envia o e-mail e senha corretos por meio da **req.body.email** e **req.body.password** na solicitação.

O **payload** terá apenas o ID do usuário. A geração do token ocorre pelo módulo **jwt-simple** usando a função **jwt.encode(payload, cfg.jwtSecret)**, a qual obrigatoriamente utilizará a mesma chave secreta **jwtSecret**, criada dentro do arquivo **config.js**. Para simplificar o manipulador de erros desse endpoint, qualquer erro será criado utilizando o código de status **HTTP 401 &#8211; Unauthorized** a partir do uso da função **res.sendStatus(401)**.

Para incluir essa regra de geração de tokens, vamos editar o arquivo **index.js** utilizando o seguinte código:

<pre class="lang-js">// index.js
var express = require("express");
var bodyParser = require("body-parser");
var jwt = require("jwt-simple");
var auth = require("./auth.js")();
var users = require("./users.js");
var cfg = require("./config.js");
var app = express();

app.use(bodyParser.json());
app.use(auth.initialize());

app.get("/", function(req, res) {
  res.json({status: "My API is alive!"});
});

app.post("/token", function(req, res) {
  if (req.body.email && req.body.password) {
    var email = req.body.email;
    var password = req.body.password;
    var user = users.find(function(u) {
      return u.email === email && u.password === password;
    });
    if (user) {
      var payload = {id: user.id};
      var token = jwt.encode(payload, cfg.jwtSecret);
      res.json({token: token});
    } else {
      res.sendStatus(401);
    }
  } else {
    res.sendStatus(401);
  }
});

app.listen(3000, function() {
  console.log("My API is running...");
});

module.exports = app;</pre>

E para finalizar nossa API, vamos criar uma rota privada, a qual irá produzir o dado autenticado do usuário. Essa rota deve utilizar o middleware **auth.authenticate()** rodando antes da rota com a função **app.get(“/user”)**. Essa rota privada irá rodar apenas para token autenticado e você pode utilizar o objeto **req.user.id** dentro dela, pois esse dado estará disponível se você enviar o token correto, e com essa ID nós vamos produzir um JSON com o usuário autenticado por meio da função **res.json(users[req.user.id])**. Para criar esta rota, vamos editar o arquivo **index.js** novamente. Confira como ele fica:

<pre class="lang-js">// index.js
var express = require("express");
var bodyParser = require("body-parser");
var jwt = require("jwt-simple");
var auth = require("./auth.js")();
var users = require("./users.js");
var cfg = require("./config.js");
var app = express();

app.use(bodyParser.json());
app.use(auth.initialize());

app.get("/", function(req, res) {
  res.json({status: "My API is alive!"});
});

app.get("/user", auth.authenticate(), function(req, res) {
  res.json(users[req.user.id]);
});

app.post("/token", function(req, res) {
  if (req.body.email && req.body.password) {
    var email = req.body.email;
    var password = req.body.password;
    var user = users.find(function(u) {
      return u.email === email && u.password === password;
    });
    if (user) {
      var payload = {id: user.id};
      var token = jwt.encode(payload, cfg.jwtSecret);
      res.json({token: token});
    } else {
      res.sendStatus(401);
    }
  } else {
    res.sendStatus(401);
  }
});

app.listen(3000, function() {
  console.log("My API is running...");
});

module.exports = app;</pre>

## Conclusão

Parabéns! Nós terminamos uma implementação extremamente importante para vários tipos de aplicações, que é o **processo de autenticação**. Graças à JWT, agora nós temos um mecanismo seguro para autenticação de usuários entre cliente e servidor utilizando apenas dados JSON. Antes de lançar a sua aplicação, não esqueça de garantir que ela não é adulterada, arruinando a experiência de utilização. Caso tenha interesse, você pode testar a versão [trial gratuita][5] do Jscrambler que em poucos minutos você já configura sua aplicação na plataforma para aplicar proteção no código-fonte de seus projetos.

 [1]: https://jwt.io
 [2]: http://passportjs.org
 [3]: http://jwt.io
 [4]: http://npmjs.com/package/passport-jwt#extracting-the-jwt-from-the-request
 [5]: https://jscrambler.com/account/signup/?ref=http://tableless.com.br/