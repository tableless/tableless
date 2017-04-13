---
title: Alternativa de CMS com Keystone.js
author: victorkurauchi
type: post
date: 2016-04-14
excerpt: O Keystone.js é um framework desenvolvido em Node.js para servir de CMS e também de Web Application.
url: /alternativa-de-cms-com-keystone-js/
categories:
  - CMS
  - JavaScript
tags:
  - JavaScript
  - keystone.js
  - NodeJS

---
Este é o primeiro artigo de uma série sobre o <a href="http://keystonejs.com/" target="_blank">Keystone.js</a>, um framework desenvolvido em Node.js para servir de CMS e também Web Application. Pra começarmos, será necessário nesse primeiro artigo um pouco de teoria, pra termos uma noção.

Aos apressados, o link do repo está disponível no <a href="https://github.com/victorkurauchi/post-keystone" target="_blank">github</a>.

Pra começar, não vou falar detalhadamente sobre sua descrição, pois no site deles está bem explicado, apenas um resumo sobre, e depois, quando formos iniciar o projeto, ficará mais claro.

O Keystone.js utiliza o <a href="http://expressjs.com/" target="_blank">Express</a>, então para muitos a curva de aprendizado será bem pequena e é um ponto bom, pois a customização (quando necessária) será tranquila. Na interface admin, utilizam o <a href="https://facebook.github.io/react/" target="_blank">React.js</a>. Este framework me chamou muito a atenção pelo fato de agilizar MUITA coisa no desenvolvimento, e ao mesmo tempo não deixar o desenvolvedor sem saber o que ocorre por baixo dos panos, os módulos de rotas/models/views são bem organizados.

Atualmente, a comunidade Keystone.js está trabalhando na próxima versão (0.4) que terá um rebuild da interface admin com o React e mais novidades.

O projeto que faremos utilizará a versão 0.3.16

A idéia nessa série é desenvolver um CMS (obviamente) onde vamos publicar posts, cadastro e listagem de produtos, e também customizar o Framework (é Javascript!) para termos uma API para posterior consumo.

> Showmethecode!

Pré requisitos: <a href="https://nodejs.org/en/" target="_blank">Node.js</a> e <a href="http://mongodb.org" target="_blank">Mongodb</a>. No terminal, digite:

<pre class="lang-shell">$npm install -g generator-keystone
    $mkdir projeto-keystone
    $cd projeto-keystone
    $yo keystone
    $node keystone
</pre>

Após a instalação via NPM, o generator fará algumas perguntas sobre as engines que deseja utilizar e informações sobre seu projeto (exemplo nome), esta parte fica a seu critério. Itens como template engine, pré-processor, taskers&#8230;

<a href="http://ornitorrinko.com/blog/uploads/2016/03/Screen-Shot-2016-03-10-at-3.41.32-PM-300x156.png" rel="attachment wp-att-254"><img class="alignnone wp-image-254 size-medium" src="http://ornitorrinko.com/blog/uploads/2016/03/Screen-Shot-2016-03-10-at-3.41.32-PM-300x156.png" alt="Tela Instalação Keystone.JS" width="300" height="156" /></a>

Agora você já consegue navegar em <http://localhost:3000> pra ter uma noção do que o framework estruturou para você. Nesse momento, repare que já temos um Blog e uma Galeria de imagens (utilizando uma conta temporária da <a href="http://cloudinary.com/" target="_blank">Cloudinary</a>).

Para acessar o admin, navegue em <a href="http://localhost:3000/keystone" target="_blank">http://localhost:3000/keystone</a> e informe usuário e senha que informou no generator (se não informou nada, é user: user@keystonejs.com pass: admin)

## Um pouco sobre as models e rotas

Esta parte é uma mão na roda, dê um check na estrutura de _./models/Post.js_ e _./models/Gallery.js_ pra saber do que estamos tratando. O interessante, é que no momento de estruturar as models, você não precisa se preocupar em criar o formulário de cadastro/edição no adminUI (o Keystone.js faz isso conforme vc seta as propriedades da model).

Já as rotas, ficam em _./routes/index.js_ para serem registradas. Possuímos o arquivo _./routes/middleware.js_ para interceptar e tratar as requests de acordo com a nossa necessidade (veremos mais adiante).

Uma boa prática que adotamos aqui na Ornito é separar a pasta de rotas em _./routes/api/*_ e _./routes/views/*, onde, respectivamente, incluiremos os arquivos de API  retornardos de nosso JSON, e ServerViews, que vamos renderizar pela template engine (<a href="http://jade-lang.com/" target="_blank">Jade</a> foi a escolhida)._

### **Cadastro de Produtos**

Ao subir o Keystone.js pela primeira vez, ele gerou as models de Post e Galeria para nós, por isso, não teremos muito trabalho nesta parte (já está pronto). Vamos agora focar no código para criação de produtos.

Nosso fluxo de criação: definir Model, definir Rota, definir View.

Vamos criar o arquivo ./models/Produto.js:

<pre class="lang-javascript">// models/Produto.js

var keystone = require('keystone');
var Types = keystone.Field.Types;

/**
 * Model Produto
 * ==========
 */

var Produto = new keystone.List('Produto', {
  map: { name: 'produto' },
  autokey: { path: 'slug', from: 'produto', unique: true }
});

Produto.add({
  produto: { type: String, required: true },
  ativo: { type: Types.Boolean, initial: true, required: true },
  preco: { type: Types.Money, format: '$0.0,00', label: 'Valor do produto', },
  descricao: {
    breve: { type: Types.Textarea, height: 150, label: "Breve descrição" },
    completa: { type: Types.Html, wysiwyg: true, height: 200, label: "Descricao completa" }
  },
  criadoEm: { type: Types.Date, index: true, default: new Date() },
  detalhes: { type: Types.TextArray },
  imagens: { type: Types.CloudinaryImages }
  
});

Produto.schema.virtual('descricao.full').get(function() {
  return this.descricao.completa || this.descricao.breve;
});

Produto.defaultColumns = 'produto, ativo, preco, criadoEm';
Produto.register();
</pre>

Já criamos a model, então podemos navegar pelo admin, e [http://localhost:3000/keystone][1] nos levará para o cadastro de um produto. Preencha as informações do produto.

Agora temos que configurar a rota em _./routes/views/produtos.js_ , _./routes/index.js_ e _./routes/middleware.js_

<pre class="lang-javascript">// routes/views/produtos.js
var keystone = require('keystone');

exports = module.exports = function(req, res) {
  
  var view = new keystone.View(req, res);
  var locals = res.locals;
  
  // Set locals
  locals.section = 'produtos';
  
  // Load the galleries by sortOrder
  view.query('produtos', keystone.list('Produto').model.find().sort('sortOrder'));
  
  // Render the view
  view.render('produtos');
  
};
</pre>

A rota _views/produtos.js_ é a responsável por consultar nossa base no mongoDB e retornar os produtos existentes.

<pre class="lang-javascript">// routes/index.js
var keystone = require('keystone');
var middleware = require('./middleware');
var importRoutes = keystone.importer(__dirname);

// Common Middleware
keystone.pre('routes', middleware.initLocals);
keystone.pre('render', middleware.flashMessages);

// Import Route Controllers
var routes = {
  views: importRoutes('./views')
};

// Setup Route Bindings
exports = module.exports = function(app) {
  
  // Views
  app.get('/', routes.views.index);
  app.get('/blog/:category?', routes.views.blog);
  app.get('/blog/post/:post', routes.views.post);
  app.get('/gallery', routes.views.gallery);
  app.all('/contact', routes.views.contact);

  app.get('/produtos', routes.views.produtos);

};
</pre>

Em _routes/index.js_ registramos igual a um app comum em express com _app.get()_ e apontamos para nossa rota de produtos, a qual vamos consultar os produtos na base.

<pre class="lang-javascript">// routes/middleware.js
var _ = require('underscore');

/**
  Initialises the standard view locals
*/

exports.initLocals = function(req, res, next) {
  
  var locals = res.locals;
  
  locals.navLinks = [
    { label: 'Home',    key: 'home',    href: '/' },
    { label: 'Blog',    key: 'blog',    href: '/blog' },
    { label: 'Gallery',   key: 'gallery',   href: '/gallery' },
    { label: 'Contact',   key: 'contact',   href: '/contact' },
    { label: 'Produtos',    key: 'produtos',    href: '/produtos' }
  ];
  
  locals.user = req.user;
  
  next();
  
};

/**
  Fetches and clears the flashMessages before a view is rendered
*/

exports.flashMessages = function(req, res, next) {
  
  var flashMessages = {
    info: req.flash('info'),
    success: req.flash('success'),
    warning: req.flash('warning'),
    error: req.flash('error')
  };
  
  res.locals.messages = _.any(flashMessages, function(msgs) { return msgs.length; }) ? flashMessages : false;
  
  next();
  
};

/**
  Prevents people from accessing protected pages when they're not signed in
 */

exports.requireUser = function(req, res, next) {
  
  if (!req.user) {
    req.flash('error', 'Please sign in to access this page.');
    res.redirect('/keystone/signin');
  } else {
    next();
  }
  
};
</pre>

Em _routes/middeware.js_ estamos apenas estruturando os _navLinks_ para exibirmos o link de produtos na home.

E agora vamos exibir nossos produtos em _./templates/views/produtos.jade_

<pre class="lang-jade">//- templates/views/produtos.jade
extends ../layouts/default

block intro
  .container
    h1 Nossos produtos
  
block content
  .container
    if produtos.length
      each item in produtos
        h2= item.produto
          .pull-right.text-muted R$ #{item.preco}

        p= item.descricao.breve
        
        .row.gallery-images
          each image in item.imagens
            .col-xs-6.col-sm-4.col-md-3.gallery-image: img(src=image.limit(300,300)).img-rounded
    else
      h3.text-muted Ainda não temos produtos cadastrados 🙁

</pre>

Navegue em <a href="http://localhost:3000/produtos" target="_blank">http://localhost:3000/produtos</a> e verá o resultado 🙂

<a href="http://ornitorrinko.com/blog/uploads/2016/03/Screen-Shot-2016-03-11-at-6.10.11-PM-300x148.png" rel="attachment wp-att-271"><img class="alignnone wp-image-271 size-medium" src="http://ornitorrinko.com/blog/uploads/2016/03/Screen-Shot-2016-03-11-at-6.10.11-PM-300x148.png" alt="Página Nossos Produtos com Keystone.js" width="300" height="148" /></a>

Neste artigo não foi possível cobrir TODOS os detalhes do Keystone.js. Mas, se você se interessou pelo framework, vale dar uma olhada na <a href="http://keystonejs.com/docs/getting-started/" target="_blank">documentação</a> sobre tipos de dados, formatos, middlewares, serviços já integrados e tudo mais.

Fiz aqui uma pequena imersão ao framework para mostrar o que ele pode fazer com pouco tempo e dedicação. No próximo artigo vamos ao detalhe do produto, e também começar com nossa API (para produtos e posts).

Repo: <a href="https://github.com/victorkurauchi/post-keystone" target="_blank">https://github.com/victorkurauchi/post-keystone</a>

Até mais.

@victorkurauchi

 [1]: http://localhost:3000/keystone/produtos