---
title: Como criar seu primeiro Progressive Web App do Zero
authors: Matheus Lima
type: post
date: 2017-08-09
excerpt: Entenda e crie seu Progressive Web App
categories:
  - Javascript
  - Na Prática
tags:
  - Progressive web app
  - Service Workers
image: https://cdn-images-1.medium.com/max/800/1*mHnQtkESVGKj91eunuu7GA.jpeg
---


No meu último *post*, fiz uma [Introdução aos Progressive Web
Apps](https://medium.com/tableless/introduÃ§Ã£o-aos-progressive-web-apps-ad47ba24cddb#.xe70z63nw)
onde foquei nas motivações de se criar um PWA, ao invés de um *app* nativo, e em
suas principais características.

Agora que você já sabe o **porquê** de desenvolver um Progressive Web App vamos
estudar, e entender, o **como**.

![](https://cdn-images-1.medium.com/max/800/1*mHnQtkESVGKj91eunuu7GA.jpeg)

Então continue a ler esse *post* para aprender:

* Como criar aplicações que funcionam *offline*
* Como fazer seu primeiro Service Worker
* O que é o arquivo *manifest.json*
* Como inspecionar seu PWA com o Google Lighthouse

*****

## Sobre a aplicação

Primeiramente vamos conhecer a aplicação que iremos adicionar as técnicas
necessárias para que ela seja transformada em um PWA.

Para quem trabalha com [metologias
ágeis](https://www.agilealliance.org/agile101/), está acostumado com um ritual
chamado [Planning
Poker](https://www.culturaagil.com.br/planning-poker-tecnica-baseada-consenso/).
Em resumo ele serve para que cada membro do time consiga fazer uma estimativa
das tarefas a serem desenvolvidas.

O *app* construído faz exatamente isso.

Essa é a tela principal:

![](https://cdn-images-1.medium.com/max/800/1*8qEhkajK4PchTGfjvAmYIQ.png)

E essa é a tela após a seleção de uma das cartas:

![](https://cdn-images-1.medium.com/max/800/1*PmT8ORCdRxzEKvLAsajkwQ.png)

Para visualizar a aplicação em produção, basta acessar:
[https://agilepoker.us/](https://agilepoker.us/)

E o código completo aqui:
[https://github.com/matheusml/pwa-planning-poker](https://github.com/matheusml/pwa-planning-poker)

## O arquivo manifest.json

O primeiro passo, e também o mais fácil, é adicionar o arquivo
[manifest.json](https://developer.mozilla.org/en-US/docs/Web/Manifest).

O propósito do arquivo *manifest* é transformar uma aplicação *web* em algo
instalável em um *smartphone*. Abaixo segue um exemplo de um arquivo
*manifest.json* válido:

<script src="https://gist.github.com/matheusml/6f3430a156ad1d4b2b065809c7faa2b2.js"></script>

Pensei em ir campo a campo e mostrar o que cada um deles significa, mas é
simplesmente mais fácil mostrar o resultado final em uma imagem:

![](https://cdn-images-1.medium.com/max/800/1*_g69Ucy5JNMZKaa06hObnw.jpeg)

Ou seja, a sua aplicação *web* agora pode abrir um *splash screen* exatamente
igual aos *apps* nativos com pouquíssimo esforço.

Ah, lembrando que o arquivo deve ser importado no *index.html*, assim:

    <link rel="manifest" href="/manifest.json">

Lembrando que você não precisa criar o arquivo *manifest* do zero. Existem
algumas ferramentas gratuitas que fazem todo o trabalho para você. Recomendo
principalmente essas duas:

* [Web App Manifest Generator](https://app-manifest.firebaseapp.com/)
* [PWA Builder](https://preview.pwabuilder.com/)

Para conferir o *manifest* final da aplicação que construímos basta entrar no
GitHub do projeto:
[https://github.com/matheusml/pwa-planning-poker/blob/master/manifest.json](https://github.com/matheusml/pwa-planning-poker/blob/master/manifest.json)

Outras fontes boas sobre o arquivo *manifest.json*:

* [Google | Manifest File
Format](https://developer.chrome.com/extensions/manifest)
* [MDN | Web App Manifest](https://developer.mozilla.org/pt-BR/docs/Web/Manifest)

## O que é um Service Worker?

Um problema bem comum que os usuários enfrentam desde o começo da *web*, e que
vem aumentando com o uso dos dispositivos móveis, é a perda da conexão.

Nada é mais frustrante do que ter preenchido todos os dados para realizar uma
compra, e no último instante isso aparecer:

![](https://cdn-images-1.medium.com/max/800/1*wV3X7vQtnePGPXBuvMSA6A.jpeg)

Os Services Workers vem para tentar consertar, ou pelo menos minimizar, esse
problema.

Mas vamos começar pela definição do SW:

> Um Service Worker é um script que seu navegador executa em segundo plano,
> separado da página da Web, possibilitando recursos que não precisam de uma
página da Web ou de interação do usuário.

Em resumo, o SW te dá a opção de manipular as requisições que são feitas por sua
aplicação e com isso algo que nunca foi possível antes na *web* agora ficou
extremamente fácil: o funcionamento *offline*.

## Como criar um Service Worker

Agora que já sabemos o que é um SW, e pra quê ele serve, vamos aprender a criar
um do zero.

A primeira coisa que precisamos fazer, é instalar o Service Worker. Durante a
instalação, vamos adicionar ao *cache* todos os arquivos estáticos, que são
gerados no *build* final:

<script src="https://gist.github.com/matheusml/fa2f2250680a8c03a866ff2493899c9d.js"></script>

Repare que criamos uma variável chamada **CACHE_NAME**. Ela serve para
“versionarmos” o *cache*. Ou seja, se coisas novas forem adicionadas ao código,
simplesmente o *static-v1* vira *static-v2*.

Agora precisamos fazer a ativação do Service Worker. Nesse passo vamos atualizar
o *cache*, se for necessário:

<script src="https://gist.github.com/matheusml/8a430c688e5a53241859e8c517a5cecc.js"></script>

Para finalizar, vamos usar o SW para interceptar requisições. A ideia é tentar
pegarmos o que for solicitado do *cache*, e se ele não existir, aí sim vamos
fazer um *request*:

<script src="https://gist.github.com/matheusml/fcd1facdcd61d6eb80136810a6861ca4.js"></script>

Aqui está a versão final do SW que fizemos:

<script src="https://gist.github.com/matheusml/945aa965065c1462537a7bdd404ff016.js"></script>

Lembrando que precisamos adicionar o SW que criamos no *index.html*, dessa
forma:

<script src="https://gist.github.com/matheusml/8d0c61d75724ba0e50964bba6fe6a6f1.js"></script>

E com isso temos nosso Service Worker completo e a aplicação agora funciona em
modo *offline* \o/

Para saber mais sobre os Service Workers:

* [Google | Service Workers: uma
introdução](https://developers.google.com/web/fundamentals/getting-started/primers/service-workers?hl=pt-br)
* [MDN | Service Worker
API](https://developer.mozilla.org/en-US/docs/Web/API/Service_Worker_API)
* [Service worker: A revolução da plataforma
web](https://braziljs.org/blog/service-worker-a-revolucao-da-plataforma-web/)

## Lighthouse

A forma fácil de saber se você está no caminho certo na construção do seu
Progressive Web App é usar alguma ferramenta de inspeção, no caso a que eu mais
recomendo é o
[Lighthouse](https://developers.google.com/web/tools/lighthouse/?hl=pt-br) do
Google.

Basta fazer o *download* da [extensão para o
Chrome](https://chrome.google.com/webstore/detail/lighthouse/blipmdconlkpinefehnmjammfjpmpbjk?hl=pt-br),
entrar no site que você deseja inspecionar e clicar no *widget*:

Depois basta aguardar o resultado, e visualizar o *feedback* do Google:

*****

## Conclusão

Pra fechar, com alguns simples passos conseguimos transformar nossa aplicação em
um Progressive Web App, sendo que agora são possíveis: funcionamento *offline*,
adicionar o *app* na *home screen* do usuário, *etc*.

Lembrando que a experiência do usuário no ambiente *mobile* pode ser, e
geralmente é, bem diferente do ambiente *desktop*, então sua aplicação tem que
ser responsiva e adaptada para esse ambiente independente de ser um PWA ou não.

*Agradecimentos especiais ao *[Flavio Nazario](https://medium.com/@flaviozed)*
pelo trabalho de UX feito no *[AgilePoker](https://agilepoker.us/)*.*