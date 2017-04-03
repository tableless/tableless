---
title: Upload de imagens desmistificado com simpleGallery.js
author: Fabio Carvalho
type: post
date: 2016-09-07
excerpt: Upload, certamente, é uma parte difícil na programação, provavelmente você já teve problemas com isso. Por que não simplificar? Confira como o simpleGallery.js pode lhe ajudar nesta jornada.
url: /upload-de-imagens-desmistificado-com-simplegallery-js/
categories:
  - AJAX
  - Artigos
  - Back-end
  - Destaques
  - HTML
  - Técnicas e Práticas
tags:
  - galeria
  - galeria de imagens
  - js
  - js vanilla
  - upload
  - upload de imagens

---
Olá pessoal, tudo bem?

Neste artigo vou procurar abordar algo comum no dia-a-dia de qualquer desenvolver, o &#8220;temido&#8221; upload de imagens. No processo utilizarei NodeJS e Express para o back-end. A grande sacada será a utilização da lib [simpleGallery.js][1], que nos auxiliará no front-end.

## Passos iniciais..

A seguir criaremos um servidor bem simples. Utilizarei o package &#8220;Multer&#8221; como middleware para as requisições de arquivo. Não vou prezar por segurança nem boas práticas, já que este artigo é apenas para encorajar aqueles que ainda possuem dificuldades.

Primeiro começaremos com a instalação do NodeJS e NPM, para mais informações:

  * <https://nodejs.org/en/>
  * <http://blog.npmjs.org/post/85484771375/how-to-install-npm>

Após NodeJS e NPM instalados, é hora de criarmos nosso `package.json`, que será responsável por armazenar o nome do app, versão, nossos packages etc. Abra o terminal e digite:

<pre>npm init /my-upload-app
cd my-upload-app
mkdir public</pre>

Após todos os dados inseridos, partiremos para a inclusão dos packages que utilizaremos.

<pre>npm install --save-dev express multer</pre>

Este comando instalará as últimas versões de cada package, permitindo a sua utilização junto ao NodeJS.

## Criando o Server

Com tudo instalado, basta criar um arquivo em nosso diretório chamado de `index.js`. Este conterá o básico para criar nossa API e seus respectivos endpoints. Estou utilizando o Hello World do próprio Express, que está presente [neste][2] link.

<pre>const express = require('express')
const app = express()

app.get('/', (req, res) =&gt; {
 res.sendFile('public/index.html')
})

app.listen(3000, () =&gt; console.log('Lstening on port 3000!'))

</pre>

Isto já é o suficiente para rodar nosso server (digite `node index.js`). Tudo que estiver dentro da pasta `/public` obviamente será considerado como público e &#8220;visível&#8221; ao browser.

Sem mais delongas, vamos partir para o endpoint que receberá os arquivos e retornará um JSON com as respectivas URL&#8217;s, ele também será responsável por armazenar nossas imagens na pasta `/uploads`. Neste ponto utilizo uma configuração mínima do &#8216;Multer&#8217;, você pode melhorar este processo limitando os arquivos por tamanho, tipo, quantidade etc. Para mais informações, clique [aqui][3].

<pre>const express = require('express')
const app = express()
const multer = require('multer')

const upload = multer({ dest: 'public/uploads/' }) // Configuramos o destino dos arquivos.

app.get('/', (req, res) =&gt; {
 res.sendFile('public/index.html')
})

app.post('/upload', upload.array('gallery[]'), (req, res) =&gt; {
 let gallery = []
 req.files.map((image) =&gt; gallery.push({'url': `http://localhost:3000/uploads/${image.filename}`}))
 res.status(200).json(gallery)
})

app.listen(3000, () =&gt; console.log('Listening on port 3000!'))</pre>

&nbsp;

Agora nossa API já está 100% funcional. Para testar, submeta um POST com as imagens para a url `http://localhost:3000/uploads`. Você receberá uma resposta formato JSON com a URL das imagens enviadas.

## Já no Front-End..

Com a nossa API criada, agora precisamos configurar o nosso front-end. Para isto, vamos iniciar criando um `index.html` dentro da pasta `/public`. Após criado, é hora de escrevermos nosso HTML:

<pre>&lt;!DOCTYPE html&gt;
&lt;html&gt;
 &lt;head&gt;
 &lt;meta charset="utf-8"&gt;
 &lt;title&gt;Upload App&lt;/title&gt;
 &lt;/head&gt;
 &lt;body&gt;
 &lt;form class="form-upload" action="/" method="POST" enctype="multipart/form-data"&gt;
 &lt;input type="hidden" name="gallery"&gt;
 &lt;label for=""&gt;Image Gallery&lt;/label&gt;
 &lt;div class="input-upload btn"&gt;
 Upload
 &lt;input class="upload" type="file" multiple="multiple" accept="image/*"&gt;
 &lt;/div&gt;
 &lt;div class="gallery-container"&gt;&lt;/div&gt;
 &lt;/form&gt;
 &lt;/body&gt;
&lt;/html&gt;</pre>

Até agora nenhuma novidade, um formulário `enctype="multipart/form-data"` com os campos necessários para enviarmos as fotos para nossa API.

## &#8220;Hora do show!&#8221;

Chegou a hora de implementarmos o [simpleGallery.js][1], uma lib JS vanilla, de apenas 2kb gzipped. Esta será responsável por submeter as imagens e salvar o JSON de retorno em algum input hidden, em nosso exemplo, utilizaremos o padrão da lib que será:

<pre>&lt;input type="hidden" name="gallery"&gt;</pre>

Também faremos a inclusão do CSS e JS, que pode ser encontrado no próprio repositório do [simpleGallery.js][1]. Ou via NPM/Bower, basta procurar por: `simple-gallery-js`.

O [Sortable][4], uma lib JS vanilla, será responsável por permitir a reordenação de nossa galeria.

O código final fica assim:

<pre>&lt;!DOCTYPE html&gt;
&lt;html&gt;
 &lt;head&gt;
 &lt;meta charset="utf-8"&gt;
 &lt;title&gt;Upload App&lt;/title&gt;
 &lt;link rel="stylesheet" href="https://raw.githubusercontent.com/fccoelho7/simpleGallery.js/master/dist/simple-gallery.min.css" media="screen" charset="utf-8"&gt;
 &lt;/head&gt;
 &lt;body&gt;
 &lt;form class="form-upload" action="/" method="POST" enctype="multipart/form-data"&gt;
 &lt;input type="hidden" name="gallery"&gt;
 &lt;label for=""&gt;Image Gallery&lt;/label&gt;
 &lt;div class="input-upload btn"&gt;
Upload
 &lt;input class="upload" type="file" multiple="multiple" accept="image/*"&gt;
 &lt;/div&gt;
 &lt;div class="gallery-container"&gt;&lt;/div&gt;
 &lt;/form&gt;

&lt;script src="https://cdnjs.cloudflare.com/ajax/libs/Sortable/1.4.2/Sortable.min.js"&gt;&lt;/script&gt;
 &lt;script src="https://raw.githubusercontent.com/fccoelho7/simpleGallery.js/master/dist/simple-gallery.min.js"&gt;&lt;/script&gt;
 &lt;script type="text/javascript"&gt;
 new SimpleGallery('.form-upload');
 &lt;/script&gt;
 &lt;/body&gt;
&lt;/html&gt;


</pre>

## Mas pera!

&#8220;Eu tenho minha API de uploads em uma URL e meu formulário será enviado para outro endpoint, como farei isso?&#8221; Bom, caso você não deseje utilizar o mesmo endpoint para upload de imagens e requisição do formulário, o [simpleGallery.js][1] nos permite criar um segundo **action. **Basta inserir um `data-action-gallery`, como no exemplo abaixo:

<pre>&lt;form class="form-upload" action="/" data-action-gallery="/uploads" method="POST" enctype="multipart/form-data"&gt;

</pre>

## Por fim.

Outras opções como: trocar o name do input que receberá o JSON das url&#8217;s e a classe que conterá a galeria também são possíveis, para mais informações acesse o repositório oficial do [simpleGallery.js][1].

O conteúdo deste artigo pode ser encontrado [aqui][5].

Bom, é isso. Espero que tenha gostado e perdido o medo quando o assunto é &#8220;upload de imagens&#8221;.

 [1]: https://github.com/fccoelho7/simpleGallery.js/
 [2]: http://expressjs.com/pt-br/starter/hello-world.html
 [3]: https://github.com/expressjs/multer
 [4]: https://github.com/RubaXa/Sortable
 [5]: https://github.com/fccoelho7/simple-gallery-demo