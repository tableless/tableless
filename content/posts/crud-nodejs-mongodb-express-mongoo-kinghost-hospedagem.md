---
title: 'Crud com Node.js e MongoDB (Express + Mongoose) na KingHost'
authors: Tableless
type: post
publishdate: 2018-01-05
date: 2018-01-05
image: https://i.imgur.com/gxYF2fP.jpg
excerpt: 'Criando uma app utilizando Express e MongoDB'
categories:
  - Publieditorial
  - NodeJS
  - MongoDB
  - Express
  - Javascript
  - Técnicas e Práticas
tags:
  - NodeJS
  - KingHost
  - MongoDB
  - Express
  - Javascript
---

A [KingHost](https://www.kinghost.com.br/?utm_source=parceiros&utm_medium=anuncio&utm_term=&utm_content=tableless-node-home&utm_campaign=oferta-produto&sa=D&ust=1514955708138000&usg=AFQjCNFJeCLPKRfqKIQ63iNQtzTYZDEUaA) está sempre buscando entregar, além de um produto de qualidade, inovação em tudo o que faz. E sempre pensando no que o desenvolvedor, como eu, precisa para focar apenas no desenvolvimento. Por isso a importância de uma infraestrutura planejada para o [Node.js](https://www.kinghost.com.br/node-js?utm_source=parceiros&utm_medium=anuncio&utm_term=&utm_content=tableless-node-hospnode&utm_campaign=oferta-produto&sa=D&ust=1514955708139000&usg=AFQjCNGft3GYAi9uVnpUKwF6-oqfindYQQ).

Aproveitando, para quem utiliza o Node.js e MongoDB, este é um tutorial básico onde vou mostrar pra vocês como criar uma app utilizando o express, framework bastante difundido no desenvolvimento node e o mongoose, uma interface de modelagem de dados que fará a comunicação da nossa app com o MongoDB. O propósito é mostrar o quão prático é iniciar um projeto com as funções CRUD.

Faça o acesso via ssh e clone o repositório do projeto:

```
\[nodejs@nodejs7601 ~\]$ mkdir apps\_nodejs; cd apps\_nodejs 
\[nodejs@nodejs7601 apps_nodejs\]$ git clone [https://github.com/henriquemennabarreto/contatos.git](https://github.com/henriquemennabarreto/contatos.git&sa=D&ust=1514955708140000&usg=AFQjCNFxfzsIQ6XSXJPazcIyHXajS-Ezig)

\[nodejs@nodejs7601 apps_nodejs\]$ cd contatos/
```

Faça a criação da app via [painel de controle da KingHost](https://painel.kinghost.com.br/login.php?uri=/index.php?utm_source=parceiros&utm_medium=anuncio&utm_term=&utm_content=tableless-node-painel&utm_campaign=oferta-produto&sa=D&ust=1514955708141000&usg=AFQjCNEi0QMRHXBN6QEQxqOHB2zxX5TAxg), o qual possui interface bem intuitiva onde poderemos parar/iniciar a app e também visualizar os logs de erro/acesso.  
  
Nome da app: contatos

Deixe em branco o caminho da app.

Script: `contatos/bin/www.js`

Na KingHost, por padrão, é utilizado o pm2 para gerenciamento e monitoramento da app via ssh:  
  
```
\[nodejs@nodejs7601 contatos\]$ pm2 status
```
  
|App name|id|mode|pid|status|restart|uptime|cpu|mem|watching|
|---|---|---|---|---|---|---|---|---|---|
|www|0|fork|49909|online|4|9m|0%|47.7MB|enabled|


Por enquanto vamos manter a app parada:  

```
\[nodejs@nodejs7601 contatos\]$ pm2 stop www  
```
  
Vamos concentrar nossa atenção toda no arquivo de rotas, onde criaremos o objeto do mongoose, faremos as operações no banco e exibição das views.  
  

```
\[nodejs@nodejs7601 contatos\]$ vim routes/index.js
```

Instanciando objetos necessários:

```
var express = require('express');  
var router = express.Router();  
var mongoose = require('mongoose');  
mongoose.connect('mongodb://usuario:senha@host/base');  
var Schema = mongoose.Schema;
```

A base de dados deverá ser criada através do painel de controle da KingHost.

O próximo passo é instanciar o objeto do mongoose e definir nossa estrutura (schema) de banco de dados.  
  
```
var userDataSchema = new Schema({  
 nome: {type: String, required: true},  
 email: String,  
 telefone: String  
}, {collection: 'contatos'});  

var Contatos = mongoose.model('UserData', userDataSchema);  
```  

Repare que eu criei uma estrutura de dados e configurei no objeto Contatos, o qual poderá realizar as funções CRUD.  
  
Vamos começar a trabalhar com o banco de dados, primeiramente com a função de inserir. A app já possui uma view esperando os dados necessários portanto basta configurar a rota e a lógica através do mongoose. Utilizaremos uma rota para get e outra para post, a primeira nos retorna a view de inserir dados e a segunda dispara o evento responsável por persistir os dados no banco. Parece doido mas vamos inserir dados na base somente realizando configurações através do código, nenhuma configuração diretamente na base será realizada.  

```
router.get('/new', function(req, res, next) {  
 res.render('new');  
});  

router.post('/new', function(req, res, next) {  

 var item = {  
   nome: req.body.nome,  
   email: req.body.email,  
   telefone: req.body.telefone  
 };  
 var data = new Contatos(item);  
 data.save();  
  
 res.redirect('/');  
});
```

A função save é responsável por persistir os dados no banco. Caso queira testar, adicione a seguinte linha no final do arquivo, para tornar acessível o módulo de roteamento:  
module.exports = router;

  
Antes de iniciar a app é necessário configurar a porta no arquivo de inicialização, em bin/www.js. A porta você descobre ao criar o projeto Node.js via painel KingHost.  


```
\[nodejs@nodejs7601 contatos\]$ node bin/www.js
```

```
module.js:471

    throw err;

    ^

Error: Cannot find module 'express'
```

Este erro indica que não instalamos as dependências da app, listadas no package.json. Bora instalar:  

```
\[nodejs@nodejs7601 contatos\]$ npm install
```

Inicie novamente a app:  

```
\[nodejs@nodejs7601 contatos\]$ node bin/www.js
```

  
Acesse o navegador e cadastre um contato.  
[https://nodejs.kinghost.net/new](https://nodejs.kinghost.net/new&sa=D&ust=1514955708144000&usg=AFQjCNHwTYlG37qUryPKa-SNvPvwPM_Qqg)  
  
Após adicionarmos os dados e clicarmos em cadastrar, veja que ocorre erro 404, pois nossa rota retorna o acesso para a raiz. Vamos implementar agora a página inicial onde exibiremos os dados do banco. Criaremos apenas uma rota get:  

```
router.get('/', function(req, res, next) {  
 Contatos.find()  
 .then(function(doc) {  
   res.render('index', {items: doc});  
 });  
});
```

Utilizamos a função find do mongoose que retorna todos os dados existentes em nosso schema. Inicie novamente a app e veja o resultado.

Para as funções de editar e deletar contatos vamos novamente criar rotas get e post. Em editar vamos utilizar as funções findById e save, no deletar a função findByIdAndRemove, veja a seguir:

```
router.get('/edit', function(req, res, next) {  
       res.render('edit');  
});  
  
router.post('/edit', function(req, res, next) {  
 var id = req.body.id;  
  
 Contatos.findById(id, function(err, doc) {  
   if (err) {  
     console.error('error, no entry found');  
   }  
   doc.nome = req.body.nome;  
   doc.email = req.body.email;  
   doc.telefone = req.body.telefone;  
   doc.save();  
 })  
 res.redirect('/');  
});  
  
router.get('/delete', function(req, res, next) {  
 res.render('delete');  
});  
  
router.post('/delete', function(req, res, next) {  
 var id = req.body.id;  
 Contatos.findByIdAndRemove(id).exec();  
 res.redirect('/');  
});
```

Não esqueça de exportar o módulo router no final do arquivo. Caso já o tenha feito, desconsidere.

```
module.exports = router;
```

Reinicie a app e veja os resultados. Para manter a app em produção utilizamos o pm2:  

```
\[nodejs@nodejs7601 contatos\]$ pm2 start www
```

O arquivo final ficará assim:  
  
```
var express = require('express');  
var router = express.Router();  
var mongoose = require('mongoose');  
mongoose.connect('mongodb://user:senha@host/base');  
var Schema = mongoose.Schema;  
  
var userDataSchema = new Schema({  
 nome: {type: String, required: true},  
 email: String,  
 telefone: String  
}, {collection: 'contatos'});  
  
var Contatos = mongoose.model('UserData', userDataSchema);  
  
router.get('/new', function(req, res, next) {  
 res.render('new');  
});  
  
router.post('/new', function(req, res, next) {  
 var item = {  
   nome: req.body.nome,  
   email: req.body.email,  
   telefone: req.body.telefone  
 };  
  
 var data = new Contatos(item);  
 data.save();  
  
 res.redirect('/');  
});  
  
router.get('/', function(req, res, next) {  
 Contatos.find()  
 .then(function(doc) {  
   res.render('index', {items: doc});  
 });  
});  
  
router.get('/edit', function(req, res, next) {  
       res.render('edit');  
});  
  
router.post('/edit', function(req, res, next) {  
 var id = req.body.id;  
  
 Contatos.findById(id, function(err, doc) {  
   if (err) {  
     console.error('error, no entry found');  
   }  
   doc.nome = req.body.nome;  
   doc.email = req.body.email;  
   doc.telefone = req.body.telefone;  
   doc.save();  
 })  
 res.redirect('/');  
});  
  
router.get('/delete', function(req, res, next) {  
 res.render('delete');  
});  
  
router.post('/delete', function(req, res, next) {  
 var id = req.body.id;  
 Contatos.findByIdAndRemove(id).exec();  
 res.redirect('/');  
});  
  
module.exports = router;
```

Espero que gostem e bons estudos! Aproveite para conhecer as opções específicas para [Node.js](https://www.kinghost.com.br/node-js?utm_source=parceiros&utm_medium=anuncio&utm_term=&utm_content=tableless-node-hospnode&utm_campaign=oferta-produto&sa=D&ust=1514955708146000&usg=AFQjCNGh46CjuDpXYYD6NAoRbzVVABmfug)e [MongoDB](https://www.kinghost.com.br/mongo-db&sa=D&ust=1514955708147000&usg=AFQjCNHCc8itrk7u9o_SYGajuNT-1w5LXA) que a KingHost oferece.