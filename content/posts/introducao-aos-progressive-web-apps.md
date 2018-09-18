---
title: Introdução aos Progressive Web Apps
authors: Matheus Lima
type: post
date: 2017-11-23
excerpt: Olhe pro seu smartphone agora mesmo. Você fez o download do aplicativo do Shopping que mais frequenta? E da franquia de restaurantes? E da agência de viagens?
image: https://i.imgur.com/Gv11YUs.jpg
categories:
  - Adaptive Web Design (AWD)
  - Javascript
  - Mobile
  - Responsive Web Design (RWD)
tags:
  - pwa
  - Progressive WebApps
  - Responsive Web Design (RWD)
  - WebApps
  - Mobile
---

Olhe pro seu *smartphone* agora mesmo e se pergunte: você fez o *download *do
aplicativo do Shopping que mais frequenta? E da franquia de restaurantes? E da
agência de viagens?

Pois é, eu também não.

![](https://cdn-images-1.medium.com/max/800/1*iI1oJN0FRKlcx21Kl0c_TQ.jpeg)

As grandes empresas de tecnologia já perceberam essa tendência e, lideradas pelo
Google, começaram a investir fortemente nos [Progressive Web
Apps](https://developers.google.com/web/progressive-web-apps/).

Mas ficam algumas perguntas:

* Existe uma crise dos aplicativos nativos?
* O que são os Progressive Web Apps?
* O que os PWAs trazem de novo?
* Quais são os cases de sucesso dos PWAs?

Nesse *post* vou tentar respondê-las.

*****

## A Crise dos Aplicativos

A visão original do Steve Jobs para o iPhone, em 2007, era de que [os
aplicativos na verdade fossem aplicações
web](https://9to5mac.com/2011/10/21/jobs-original-vision-for-the-iphone-no-third-party-native-apps/):

> Vocês já tem tudo o que precisam se querem saber como desenvolver aplicativos
> para o iPhone hoje: basta usar os padrões modernos da web.

![](https://cdn-images-1.medium.com/max/800/1*wqbuhgSP1dEsx_IKL_tNdA.jpeg)

Mas essa visão original foi alterada, em 2008 o grande *boom *de aplicativos
começou quando a Apple primeiramente nos apresentou a App Store.

Só tem um problema nessa história: [esse boom está
acabando](https://www.recode.net/2016/6/8/11883518/app-boom-over-snapchat-uber).

Nos Estados Unidos, por exemplo, [o número de downloads de aplicativos vem
diminuindo em
20%](https://www.androidauthority.com/end-era-app-downloads-decline-usa-698555/)
a cada ano. A imagem abaixo mostra o declínio para todos os principais *apps* do
mercado, exceto **Snapchat**, **Uber **e **Airbnb**, de 2015 para 2016:

![](https://cdn-images-1.medium.com/max/800/1*3Z7vG0x17UmZqdSbJXlTWA.png)

Outros estudos apontam ainda que [60% de todos os apps, nunca foram sequer
baixados](https://www.tinethygesen.com/post/42502739988/60-of-apps-have-never-been-used-stats-for-app).

Além disso, [mais de 65% dos usuários de smartphones, não fazem nenhum download
de aplicativo por
mês](https://qz.com/253618/most-smartphone-users-download-zero-apps-per-month/).

Um outro dado interessante é que dos [1,5 milhões de aplicativos na Google Play
Store, somente alguns poucos milhares tem algum
engajamento](https://andrewchen.co/new-data-shows-why-losing-80-of-your-mobile-users-is-normal-and-that-the-best-apps-do-much-better/).

E pra terminar, [os usuários de smartphones gastam 80% do tempo usando apenas os
mesmo 5
apps](https://marketingland.com/report-mobile-users-spend-80-percent-time-just-five-apps-116858).

Todos esses dados nos fazem ficar preocupados. Mas mesmo com todas essas
informações, os *apps* certamente ainda tem seu lugar, e pra [muitas empresas
ainda fazem muito
sentido](https://www.concretesolutions.com.br/category/mobile/).

O meu ponto é: construir um aplicativo nativo pode ser uma solução bem cara para
algumas empresas, e para alguns produtos simplesmente não faz sentido ter um
*app* nativo.

Mas o que podemos fazer então?

## Progressive Web Apps

Para estarmos na mesma página, vamos começar pelas definições:

> Os **Progressive Web Apps** são um conjunto de técnicas para desenvolver
> aplicações web, adicionando **progressivamente **funcionalidades que antes só
eram possíveis em apps nativos.

As seguintes características, [criadas pelo
Google](https://developers.google.com/web/fundamentals/getting-started/codelabs/your-first-pwapp/),
definem com exatidão o que são esperados de um PWA:

* **Progressivo**: para qualquer usuário, independente do *browser*
* **Responsivo**: feito para qualquer dispositivo: *desktop*, *tablet* e *mobile*
* **Conexão**: funciona mesmo se o usuário estiver *offline*
* **App-like**: o usuário se sente em um aplicativo nativo
* **Atualizado**: não é necessário baixar atualizações do aplicativo, o *browser
*simplesmente irá detectar e atualizar automaticamente, caso necessário.
* **Seguro**: somente com *https*
* **Engajável**: através de *push notifications*, o usuário pode ser
constantemente engajado.
* **Instalável**: é possível adicionar um ícone na tela principal do *smartphone
*com apenas um clique.

Ou seja, se antes somente os aplicativos nativos tinham: *push notifications*,
funcionamento *offline*, geolocalização e ícone na *home screen*, agora podemos
desfrutar de todos esses benefícios usando uma aplicação 100% *web*.

A empolgação com essas novas tecnologias é grande por parte da comunidade. <br>
O [Christian Heilmann](https://medium.com/@codepo8), por exemplo, [falou
recentemente](https://www.christianheilmann.com/2016/05/31/progressive-web-apps-and-our-regressive-approach/)
que:

> Estou convencido de que os PWAs são necessários para caminharmos na direção
> certa. Eles são uma mudança muito importante.

## Retenção

Logo de cara já podemos ver um dos benefícios mais óbvios dos PWAs:
**retenção**.

Um usuário que deseja experimentar um aplicativo, precisa passar por diversas
etapas:

1.  Buscar o *app*
1.  Instalar
1.  Abrir
1.  Se cadastrar
1.  Interagir
1.  Compartilhar

É comum termos uma [perda de 20% dos usuários para cada uma dessas
etapas](https://blog.gaborcselle.com/2012/10/every-step-costs-you-20-of-users.html).
O mesmo não acontece na *web*. Basta acessarmos um *link *e poucos segundos
depois já estamos experimentando o produto.

Ou seja, o usuário não precisa se comprometer, e perder tempo, em instalar um
*app *para só depois poder avaliar se esse aplicativo valeu a pena ou não.

## Economia

Se você realmente precisa de um aplicativo nativo, os gastos necessários para
contratar uma equipe especializada de desenvolvedores iOS/Android certamente
serão bem investidos.

![](https://cdn-images-1.medium.com/max/800/1*kq2J2NYq1Udu47sQeOI0HA.jpeg)

Porém, como relatei anteriormente, em diversos casos simplesmente não é mais
necessária a construção de um *app*. Um PWA talvez atenda muito bem os seus
requisitos de negócio. Se esse for o caso, a economia gerada por essa decisão
será imensa.

## Cases

O *case* de sucesso mais famoso dos Progressive Web Apps é o do
[Flipkart](https://medium.com/@AdityaPunjani/building-flipkart-lite-a-progressive-web-app-2c211e641883#.erzahl96d).

O Flipkart é o maior *e-commerce* da India. A experiência na construção do
Flipkart Lite (que é a versão PWA do aplicativo) resultou em um [aumento de 70%
em conversões de
vendas](https://developers.google.com/web/showcase/2016/flipkart).

Além disso, o Flipkart Lite teve outros números impressionantes:

* Tempo de permanência dos usuários no site aumentou **3 vezes**
* Engajamento **40% maior**
* Consumo de dados quase **3 vezes menor**

O vídeo abaixo mostra um resumo do *case* do Flipkart:

*****

Outros casos de sucesso dos Progressive Web Apps:

* [Alibaba](https://developers.google.com/web/showcase/2016/alibaba)
* [The Washington Post](https://developers.google.com/web/showcase/2016/wapo)
* [Housing.com](https://developers.google.com/web/showcase/2016/housing)

## Desvantagens

Com tudo que foi analisado, nos parece que os PWA são uma escolha fácil. Mas não
são.

Ainda existem desvantagens dos Progressive Web Apps em relação a construção dos
aplicativos nativos:

1.  Os PWAs ainda não tem o controle total sobre o *hardware* do *device*:
[bluetooth, lista de contatos e NFC, são alguns exemplos de features que não
conseguem ser acessadas pelos Progressive Web
Apps](https://medium.com/dev-channel/why-progressive-web-apps-vs-native-is-the-wrong-question-to-ask-fb8555addcbb#.qsotm6xo9).
1.  Apesar de Google, Microsoft e Mozilla estarem apostando alto nos PWAs, a Apple
ainda não está. <br> Ainda existem duas *features* importantes não suportadas
pelo Safari: *push notifications *e funcionamento *offline*.<br> Mas, [a Apple
já está considerando implementar os
PWAs](https://twitter.com/jonathandavis/status/745688244323377152), mesmo porque
[talvez ela não tenha muita
escolha] (https://www.techrepublic.com/article/apple-could-lose-billions-on-progressive-web-apps-but-it-has-no-choice/).

## Conclusão

Ainda é muito cedo pra dizer se realmente os Progressive Web Apps vieram para
ficar.

Porém, se:

* a sua empresa é uma *startup*
* ou ela está com um *budget* apertado
* ou a construção de um *app* nativo não está no radar da empresa

Então talvez você deva considerar o investimento em construir um PWA antes, e
ter uma versão do seu site com cara de *app*, por um baixo custo.

## Pra onde ir

Se você se interessou pelos PWAs mas não sabe para onde ir, indico as seguintes
fontes:

* [Google | Progressive Web Apps](https://developers.google.com/web/progressive-web-apps/)
* [Progressive Web Apps Summit 2016](https://www.youtube.com/playlist?list=PLNYkxOF6rcIAWWNR_Q6eLPhsyx6VvYjVb)
* [Palestra do Sérgio Lopes — Front In Sampa 2015](https://www.youtube.com/watch?v=sH7dlRnuh-k)
* [Palestra do Jake Archibald — BrazilJS 2016](https://www.youtube.com/watch?v=k6P9ndFNarg)
