---
title: Como criar aplicações em tempo real usando Node.js e RethinkDB
author: Jscrambler
type: post
date: 2017-02-22
aliases: 
    - /?p=57217
    - /como-criar-aplicacoes-em-tempo-real-usando-node-js-e-rethinkdb/
titulo_personalizado:
  - 'Como criar aplicações em tempo real usando <strong>Node.js e RethinkDB</strong>'
categories:
  - JavaScript
  - NodeJS
tags:
  - JavaScript
  - node.js
  - rethinkDB
  - Web Development

---
## Sobre o RethinkDB

Se você precisa de um banco de dados NoSQL que funcione com dados JSON e tenha suporte completo para buscas em tempo real e uma mistura de modelos entre SQL e NoSQL, então uma boa opção é o RethinkDB.

Trata-se de uma base de dados em código aberto em que todos os dados JSON são persistidos em tabelas como um banco de dados SQL convencional, permitindo que você execute queries entre múltiplas tabelas utilizando o comando clássico **join**.

Mas você também pode persistir arrays e sub-documentos como está acostumado a fazer com o MongoDB, CouchDB ou PostgreSQL.

Há alguns materiais bacanas no RethinkDB, como:

  * Suporte ao GeoSpartial;
  * API para lidar com strings, datas, booleanos e documentos;
  * API para Math;
  * Suporte ao Map-reduce;
  * Cliente HTTP para capturar alguns dados externos;
  * Changefeeds , que é uma busca em tempo real;
  * Suporte para index (simples, composto e multi);
  * Painel de administrador nativo da web;

## Desenvolvendo o aplicativo

E então, que tal desenvolver algo útil usando o RethinkDB? Para explorar a busca em tempo real, vamos construir uma timeline global simples utilizando o recurso [changefeed][1] para listar todos os dados na timeline em tempo real, com o uso do Node.js, Express, Socket.IO e o RethinkDB.

Primeiro, você precisa instalar o RethinkDB. Antes de começar escrevendo os códigos abaixo, para instalar esse banco de dados eu recomendo que você leia e siga as instruções deste link <http://rethinkdb.com/docs/install> de acordo com seu sistema operacional.

Depois de instalá-lo, execute os comandos abaixo para iniciar o projeto:

<pre><code class="bash">mkdir timeline
cd timeline
npm init
npm install--save express socket.io rethinkdb
</code></pre>

Agora, vamos trabalhar! Para simplificar as coisas nós vamos usar o código do ES6 da versão nativa **Node v6.x.x**, e o backend será um único arquivo de código para fins de estudo, mas se você precisa desenvolver um servidor backend complexo e bem estruturado utilizando o RethinkDB, dê uma olhada neste projeto [node-api-examples][2], o qual possui uma lista com alguns exemplos de APIs utilizando os mesmos roteadores web e bancos de dados. Existem alguns exemplos do uso do RethinkDB com Koa, Express e o Hapi.js.

Bem, vamos criar o servidor backend de nossa aplicação. Você pode criar o arquivo `index.js` por meio do código abaixo:

<pre><code class="javascript">const http = require('http');
const fs = require('fs');
const express = require('express');
const socketIO = require('socket.io');
const r = require('rethinkdb');
const config = require('./config.json');

// Loading Express, HTTP, Socket.IO and RethinkDB
const db = Object.assign(config.rethinkdb, {
    db: 'timeline'
});
const app = express();
const server = http.Server(app);
const io = socketIO(server);

// Connecting to RethinkDB server
r.connect(db)
    .then(conn =&gt; {
        // Index route which renders the index.html
        app.get('/', (req, res) =&gt; {
            fs.readFile(`${__dirname}/index.html`, (err, html) =&gt; {
                res.end(html || err);
            });
        });
        // The changefeed is provided by change() function
        // which emits broadcast of new messages for all clients
        r.table('messages')
            .changes()
            .run(conn)
            .then(cursor =&gt; {
                cursor.each((err, data) =&gt; {
                    const message = data.new_val;
                    io.sockets.emit('/messages', message);
                });
            });
        // Listing all messages when new user connects into socket.io
        io.on('connection', (client) =&gt; {
            r.table('messages')
                .run(conn)
                .then(cursor =&gt; {
                    cursor.each((err, message) =&gt; {
                        io.sockets.emit('/messages', message);
                    });
                });
            // Listening the event from client and insert new messages
            client.on('/messages', (body) =&gt; {
                const {
                    name,
                    message
                } = body;
                const data = {
                    name,
                    message,
                    date: new Date()
                };
                r.table('messages').insert(data).run(conn);
            });
        });
        server.listen(3000, () =&gt; console.log('Timeline Server!'));
    })
    .error(err =&gt; {
        console.log('Can\'t connect to RethinkDB');
        throw err;
    });
</code></pre>

Existem alguns detalhes importantes que você precisa saber quando for usar o RethinkDB. Primeiro, todas as funções desse módulo funcionam usando callbacks ou [Promessas][3]. Se você escolher as promessas, você pode criar funções assíncronas bem estruturadas com gerentes de erros melhores.

O recurso **changefeed** (via `r.table('messages').changes()`) é um subscriber do banco de dados, o qual é uma query observadora e retorna qualquer modificação de uma tabela. A combinação com o `io.sockets.emit()` permite que o servidor envie dados em tempo real para o cliente.

Agora, vamos criar um script simples de migração para preparar o banco de dados antes de rodar o servidor. Essa migração é muito comum em bancos de dados relacionais. Crie o arquivo `database.js` com o script abaixo:

<pre><code class="javascript">const r = require('rethinkdb');
const config = require('./config.json');
let conn;

r.connect(config.rethinkdb)
    .then(connection =&gt; {
        console.log('Connecting RethinkDB...');
        conn = connection;
        return r.dbCreate('timeline').run(conn);
    })
    .then(() =&gt; {
        console.log('Database "timeline" created!');
        return r.db('timeline').tableCreate('messages').run(conn);
    })
    .then(() =&gt; console.log('Table "messages" created!'))
    .error(err =&gt; console.log(err))
    .finally(() =&gt; process.exit(0));
</code></pre>

E não se esqueça de criar o arquivo `config.json`, o qual possui dados para conectar no servidor RethinkDB:

<pre><code class="javascript">{
    "rethinkdb": {
        "host": "localhost",
        "port": 28015
    }
}
</code></pre>

Para finalizar nossa aplicação, precisamos criar o arquivo `index.html`, que será a parte do lado do cliente para os usuários enviarem mensagens na timeline.

<pre><code class="html">&lt;!DOCTYPE html&gt;
&lt;html&gt;

&lt;head&gt;
    &lt;meta charset="utf-8"&gt;
    &lt;title&gt;Timeline&lt;/title&gt;
    &lt;meta name="viewport" content="width=device-width,initial-scale=1"&gt;
    &lt;script src="/socket.io/socket.io.js"&gt;&lt;/script&gt;
&lt;/head&gt;

&lt;body&gt;
    &lt;form style="text-align:center;margin:50px 0"&gt;
        &lt;label for="name"&gt;Name:&lt;/label&gt;
        &lt;input type="text" id="name" /&gt;
        &lt;label for="message"&gt;Message:&lt;/label&gt;
        &lt;input type="text" id="message" /&gt;
        &lt;button type="submit"&gt;Send&lt;/button&gt;
    &lt;/form&gt;
    &lt;fieldset style="padding: 20px;width:50%;margin:0 auto"&gt;
        &lt;legend style="text-align:center"&gt;Timeline&lt;/legend&gt;
        &lt;p id="messages"&gt;&lt;/p&gt;
    &lt;/fieldset&gt;
    &lt;script&gt;
        (function() {
            var socket = io();
            var form = document.querySelector('form');
            form.addEventListener('submit', function(e) {
                e.preventDefault();
                var name = e.target.querySelector('#name');
                var message = e.target.querySelector('#message');
                var data = {
                    name: name.value,
                    message: message.value
                };
                socket.emit('/messages', data);
                e.target.reset();
            });
            socket.on('/messages', function(data) {
                var messages = document.querySelector('#messages');
                var message = '&lt;b&gt;' + data.name + ':&lt;/b&gt; ' +
                    data.message + '&lt;br /&gt;';
                messages.innerHTML += message;
            });
        })();
    &lt;/script&gt;
&lt;/body&gt;

&lt;/html&gt;
</code></pre>

Agora nós estamos prontos para rodar essa aplicação! Mas antes de iniciar o servidor, na primeira vez você deve executar a migração do banco de dados para criar o banco de dados e tabela para este projeto. Para isso, execute o seguinte comando:

    node database.js
    

Se tudo der certo, você pode iniciar o servidor ao executar:

    node index.js
    

E você pode brincar enviando mensagens nesta aplicação acessando o endereço <http://localhost:3000>.

## Protegendo o aplicativo

Se quiser saber mais sobre como começar protegendo seu aplicativo, basta acessar este [tutorial][4], que irá ajudar nos primeiros passos de uso do [Jscrambler][5].

## Conclusão

O RethinkDB é o incrível NoSQL! Esse banco de dados pode oferecer suporte total para aplicações de tempo real apenas utilizando o changefeed + socket.io. [Neste link][1], você pode ler mais sobre o que é possível criar usando o changefeeds. Quase todas as funções podem executar usando as Promises, que fazem com que você escreva um código melhor e você pode facilmente usar o recurso **ES7 async/await** para simplificar as funções de promessas também.

 [1]: http://rethinkdb.com/docs/changefeeds/javascript
 [2]: https://github.com/caio-ribeiro-pereira/node-api-examples
 [3]: https://developer.mozilla.org/en/docs/Web/JavaScript/Reference/Global_Objects/Promise
 [4]: https://blog.jscrambler.com/jscrambler-101-first-use
 [5]: https://www.jscrambler.com