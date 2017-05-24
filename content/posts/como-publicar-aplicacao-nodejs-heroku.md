---
title: Como publicar aplicação NodeJS no Heroku
author: Igor Ribeiro Lima
type: post
date: 2014-06-22
excerpt: 'Neste artigo vou utilizar uma <a href="http://minhas-midias-sociais.herokuapp.com/" rel="noreferrer">aplicação <em>single page</em></a> para demonstrar passo a passo as etapas necessárias para publicar uma aplicação no <a href="https://www.heroku.com/" rel="noreferrer">Heroku</a>.'
url: /como-publicar-aplicacao-nodejs-heroku/
dsq_thread_id: 2739418004
categories:
  - nodejs
  - javascript
  - Técnicas e Práticas
tags:
  - Heroku
  - JavaScript
  - NodeJS
  - Procfile
  - Sinatra
  - SSH key
---

O código da aplicação de exemplo está disponível em um [gist][1], para baixá-lo digite o comando:

<pre class="prettyprint lang-sh">git clone gist@gist.github.com:69153705256f6a9a4557.git minhas-midias-sociais</pre>

Dentro da pasta **_minhas midias sociais_**, o arquivo _<a href="https://gist.github.com/igorlima/69153705256f6a9a4557#file-index-html" rel="noreferrer">index.html</a>_ pode ser aberto utilizando qualquer navegador. Como são arquivos estáticos, será possível visualizar a aplicação web normalmente.

Para rodar esse pequeno projeto no serviço de cloud, será preciso criar um servidor para tal. Nesse caso, vamos usar o <a href="http://expressjs.com/" rel="noreferrer">Express</a>, framework para <a href="http://nodejs.org/" rel="noreferrer">NodeJS</a> inspirado no [Sinatra][2]. O código está no arquivo _<a href="https://gist.github.com/igorlima/69153705256f6a9a4557#file-server-js" rel="noreferrer">server.js</a>_. Para rodá-lo execute:

<pre class="prettyprint lang-sh">npm install
node server.js</pre>

Para confirmar que tudo está funcionando como o esperado, acesse o endereço `http://localhost:5000` e pingo, já temos uma aplicação NodeJS para ser hospedada na nuvem.

Agora, vá ao site Heroku e faça os seguintes passos: (i) se <a href="https://id.heroku.com/signup/www-home-top" rel="noreferrer">cadastre</a>, (ii) <a href="https://dashboard.heroku.com/apps" rel="noreferrer">crie uma aplicação</a> e (iii) carregue sua chave pública ssh na <a href="https://dashboard.heroku.com/account" rel="noreferrer">sessão SSH Keys</a>. Caso precise de detalhes de como gerar uma _chave ssh_, acesse o <a href="https://help.github.com/articles/generating-ssh-keys" rel="noreferrer">link</a>.

Heroku possui um mecanismo para declarar qual comando deve ser executado para iniciar um serviço na nuvem: no nosso caso, o script `node server.js`. Isso deve ser declarado no arquivo de texto _<a href="https://gist.github.com/igorlima/69153705256f6a9a4557#file-procfile" rel="noreferrer">Procfile</a>_. Após esses passos, tudo está pronto para a nossa primeira publicação na nuvem. Digite o script abaixo no diretório do projeto e a mágica estará feita:

<pre class="prettyprint lang-sh">git remote add heroku git@heroku.com:o-nome-da-aplicacao-criada-no-heroku.git
git push heroku HEAD:master</pre>

Após o **_push_**, sua aplicação pode ser visualizada no endereço `http:/o-nome-da-aplicacao-criada-no-heroku.herokuapp.com/`, conforme ilustra imagem abaixo. E é isso, pessoal. Espero que tenha gostado. Até a próxima.

![Screenshot da aplicação 'minhas midias sociais'][3]

 [1]: https://gist.github.com/igorlima/69153705256f6a9a4557 "gist"
 [2]: http://www.sinatrarb.com/ "sinatra"
 [3]: http://i1368.photobucket.com/albums/ag182/igorribeirolima/a0000d4f6b3b7ca0469fcdeba8a6f6e2_zps2ba999fa.jpg
