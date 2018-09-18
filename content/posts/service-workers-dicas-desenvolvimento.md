---
title: "Service Workers: Dicas de desenvolvimento"
authors: Aurélio Saraiva
type: post
publishdate: 2018-03-27
date: 2018-03-11
image: https://i.imgur.com/icwrMlb.jpg
excerpt: Saiba algumas dicas sobre Service Workers e seu funcionamento.
categories:
  - service workers
  - Na prática
  - Código
  - Tecnologia e Tendências
tags:
  - service workers
  - Na prática
  - Código
  - Tecnologia e Tendências
---

Recentemente precisamos implementar uma feature em uma das aplicações front-end
que temos na Creditas. Parecia simples, colocar notificações utilizando
[Pusher](https://pucher.com/) para informar o usuário que algo aconteceu.

[Pusher](https://pusher.com/) é um PaaS que oferece serviço de notificações de
eventos em Real-Time para sua aplicação.

Porém analisando a forma como nossos usuários utilizavam a aplicação,
encontramos um padrão de uso que dificultaria a implementação. Nossos usuários
abriam uma nova aba para cada tarefa que eles precisavam gerenciar. Até ai tudo
bem, o problema é que cada aba no browser é um processo (existem controvérsia)
separado que não compartilha estado entre si. Ao implementar o
[Pusher](https://pusher.com/), ele criava uma conexão socket para cada aba, ou
seja, ao ser enviado um evento para um channel no [Pusher](https://pusher.com/),
todas as abas iriam escutar e executar a ação ao mesmo tempo. Com certeza essa
não era a experiencia que queríamos, pois existia uma grande chance de algo dar
errado.

![](https://i.imgur.com/GZu2uwb.png)
<span class="figcaption_hack">Implementação sem Service Workers: Como é possível ver, existe uma conexão
socket para cada aba no browser aberta.</span>

Entendendo o problema e pesquisando soluções encontramos Service Worker como
alternativa. Service Worker faz parte do conjunto de especificações em torno do
HTML5, você pode saber mais na [Web Docs da
Mozilla](https://developer.mozilla.org/en-US/docs/Web/API/Service_Worker_API).

**Definição por** [Matt Gaunt](https://developers.google.com/web/fundamentals/primers/service-workers/)

> A service worker is a script that your browser runs in the background, separate from a web page, opening the door to features that don’t need a web page or user interaction. Today, they already include features like push notifications and background sync.

Service Worker não é uma novidade, eu já tinha estudado há uns anos atrás como
solução para processamento em background em aplicativos mobiles. Mas, pela
primeira vez considerei usa-lo para resolver um problema em browser desktop e
não mobile.

![](https://i.imgur.com/LXRIujR.png)
<span class="figcaption_hack">Implementação com Service Worker: Neste modelo agora temos um worker conectado
em todas as abas abertas com apenas uma conexão socket aberta.</span>

*****

Vou apresentar um pouco do que aprendi implementando Service Worker no browser
desktop.

Basicamente existem muitas aplicabilidades para Service Worker, podemos receber
push notifications, processos em background, requisições off-line, entre outros.

Service Worker vem sendo bastante explorado em Progressive Web App (PWA) para
oferecer uma experiencia mobile em uma aplicação web. Nesse post da [Magnetis](https://medium.com/magnetis-backstage/transformando-o-site-da-magnetis-em-um-pwa-fc2a18d722e7)
eles explicam um pouco mais sobre PWA e como usando o Service Worker.

Vamos lá, separei alguns pontos interessantes:

## Localização do arquivo

Seu Service Worker só será instalado se o arquivo estiver no mesmo nível do
local onde está sendo instalado.

Supondo que você tenha um arquivo **index.html** que registra o seu Service
Worker localizado na pasta **/blog/**. Neste caso, a localização do seu arquivo
do Service Worker deve está localizado no mesmo nível **/blog/sw.js**. Caso
contrario ele não será instalado.

project-with-sw/<br> ├── home.html<br> └── blog<br>  ├── index.html ←Esse
arquivo deve registrar o Service Worker<br>  └── **sw.js**

É importante comentar que o Service Worker só irá funcionar dentro do caminho
que ele foi registrado. No exemplo acima o Service Worker vai funcionar somente
para o caminho **https:/meudominio.com/blog/** em diante. O caminho
**https:/meudominio.com/** não estará sob o controle do Service Worker. Caso
você precise aplicar o Service Worker em todo o seu domínio você precisa
registra-lo na raiz, em **https:/meudominio.com/sw.js**

Exemplo:

**Service Worker**:
[https://meudominio.com/blog/sw.js](https://meudominio.com/blog/sw.js)<br>
**Página inicial**: [https://meudominio.com/](https://meudominio.com/) ←Service
Worker não consegue atuar neste endereço<br> **Página do blog**:
[https://meudominio.com/blog/outra-pagina](https://meudominio.com/blog/outra-pagina)
← Service Workers tem acesso e controla essa página

## Certificado SSL (HTTPS)

Um Service Worker precisa obrigatoriamente está rodando em um domínio seguro,
com suporte a HTTPS. A única exceção neste caso é para localhost durante o
desenvolvimento.

## Cross-Domain

Muitas das aplicações front-end tem seus arquivos assets servidos de CDN, o
problema aqui é quando esses arquivos são servidos para outro domínio.

**Site**: https://meudominio.com<br> **Arquivo Javascript**:
[https://minha-cdn.com/blog/main.js](https://minha-cdn.com/js/index.js)<br>
**Service Worker**:
[https://minha-cdn.com/blog/sw.js](https://minha-cdn.com/js/index.js)

Essa configuração acima, não vai funcionar, mesmo se se você configurar para
aceitar Cross-Domain o browser vai bloquear.

Solução:

**Site**: [https://meudominio.com](https://meudominio.com/)<br> **Arquivo
Javascript**:
[https://meudominio.com/blog/main.js](https://minha-cdn.com/js/index.js)<br>
**Service Worker**:
[https://meudominio.com/blog/sw.js](https://minha-cdn.com/js/index.js)

## Controle de cache com assinatura no arquivo

Diversas aplicações front-end implementam um modelo de assinatura nos arquivos
para controlar o cache, e cada alteração no arquivo essa assinatura muda.

**Exemplos de assinatura:**

* sw-d58e3582afa99040e27b92b13c8f2280.js
* sw.js?_gc=20180101

Se você pretende trabalhar com Service Worker, você deve garantir que esse
comportamento não aconteça, caso contrário cada vez que uma alteração é feita no
arquivo, uma nova instalação será feita, sem remover a anterior. Basicamente
esse comportamento fará com que você tenha diversas versões instaladas ao mesmo
tempo e rodando juntas. Isso pode trazer diversos comportamentos inesperado na
sua aplicação.

Isso acontece por que o browser considera o caminho do arquivo como nome do
Service Worker.

**Exemplo:**

* sw.js?_gc=123
* sw.js?_gc=321

No exemplo acima, teríamos 2 Service Workers iguais instalados.

## Cache no header da requisição

Se eu não posso controlar o cache com assinatura no arquivo, então como eu
controlo o cache do Service Worker?

Basicamente a resposta é, você não controla nenhum cache!

O ideal para esses arquivos de Service Worker é enviar no header parâmetros
informando o browser para não fazer nenhum tipo de cache:

    // response header
    Cache-Control: no-store, no-cache, must-revalidate, proxy-revalidate, max-age=0

Por que? Basicamente o Browser faz download do arquivo e faz comparações
**byte-to-byte** para identificar que precisa instalar uma nova versão do
Service Worker.

## Acesso ao DOM

Service Worker não é uma página web, logo você não tem acesso ao DOM, a maioria
dos recursos disponíveis no browser não vão funcionar. Se você precisar alterar
algo no DOM da página com base em algum evento no Service Worker, você vai
precisar enviar um evento com **postMessage** para página ativa. Na sua página
você terá que ter um **addEventListener** escutando e executando a ação que você
precisa. *Vou falar mais sobre isso em outro post*.

    // in sw.js
    this.clients.matchAll().then(clients => {
      clients.forEach(client => 
    ( { property, ...} ));
    });

    // in page.html
    navigator.serviceWorker.addEventListener(
    , event => { console.log(event.data) }, false);


## LocalStorage

LocalStorage ou SessionStorage disponível no browser para armazenar pequenas
quantidades de dados não vão funcionar dentro de um Service Worker. Somente
IndexedDB está disponível até o momento.

Quem já mexeu com IndexedDB conhece dor de cabeça que é gerenciar ele. Para não
ter que passar esse trabalho todo, recomendo utilizar esse projeto que
implementa um interface similar ao LocalStorage para armazenar dados no
IndexedDB.

[https://github.com/localForage/localForage](https://github.com/localForage/localForage)

## Librarys JavaScript

Algumas libs JS não foram pensadas para funcionar em um Service Worker, muitas
estão usando recursos que não são suportadas. Muitas tem referencia a variáveis
globais como **window** ou **document** que não existem dentro de uma instância
de Service Worker. Se está pensando em usar algo, procure por libs que ofereça
uma versão exclusiva para Service Workers.

*****

Esses foram alguns pontos que gostaria de citar ao se trabalhar com Service
Workers. Apesar dos pontos acima, Service Worker é relativamente simples de
usar. Quase nunca consideramos usar recursos do browser similar a este por
acreditar que são avançados ou complexos de mais para nossa aplicação.

## Um último ponto!

Nos exemplos que você verá pela WEB, quase todos são relacionados a PWA,
principalmente para trabalhar com dados off-line. Mas, Service Worker é muito
mais que somente disponibilizar dados off-line, você pode aproveita-lo para
resolver outros problemas, basta ter criatividade.

Você já fez algo com Service Workers? Deixe um comentário!

## Links uteis:

- [https://developer.mozilla.org/en-US/docs/Web/API/Service_Worker_API/Using_Service_Workers](https://developer.mozilla.org/en-US/docs/Web/API/Service_Worker_API/Using_Service_Workers)<br>
- [https://jbmoelker.github.io/serviceworker-introduction/steps/](https://jbmoelker.github.io/serviceworker-introduction/steps/)<br>
- [https://developers.google.com/web/fundamentals/primers/service-workers/](https://developers.google.com/web/fundamentals/primers/service-workers/)

