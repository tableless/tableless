---
title: WebIntents – Framework para WebApps
author: Diego Eis
type: post
date: 2012-01-06
excerpt: 'WebIntents: sistemas web falando a mesma língua.'
url: /webintents-framework-para-webapps/
tweetbackscheck:
  - 1356434968
shorturls:
  - 'a:3:{s:9:"permalink";s:58:"http://tableless.com.br/webintents-framework-para-webapps/";s:7:"tinyurl";s:26:"http://tinyurl.com/7gefncy";s:4:"isgd";s:19:"http://is.gd/iSBhZ6";}'
twittercomments:
  - 'a:10:{i:155326444292157440;s:7:"retweet";i:155325406310965248;s:7:"retweet";i:155325283178778624;s:7:"retweet";i:155325264442826752;s:7:"retweet";i:155301947002466304;s:7:"retweet";i:160692751049043968;s:7:"retweet";i:219790204372910080;s:7:"retweet";i:219781572457533440;s:7:"retweet";i:219778133426049025;s:7:"retweet";i:219778105617809408;s:7:"retweet";}'
tweetcount:
  - 14
dsq_thread_id: 529000282
categories:
  - Acessibilidade
  - Mercado e Comportamento
  - Notícias
  - Tecnologia e Tendências
tags:
  - 2012
  - acessibilidade
  - aprenda
  - Browsers
  - usabilidade
  - web
  - web standards

---
O Chrome e o Firefox estão trabalhando juntos em um framework open-source que fazem aplicações web trabalhem juntas sem que uma precise dar informações sobre seus respectivos sistemas. O nome deste framework é [WebIntents][1].

O problema a ser resolvido é que se quisermos criar um sistema que utilize algumas facilidades de outros sistemas, nós precisamos aprender a API deste determinado sistema. Acontece que as APIs não são iguais. Se você quer utilizar um sistema de localização como Foursquare ou Gowalla, você precisa aprender como a API de cada um funciona e então escolher entre um dos dois ou utilizar os dois no seu sistema. Nesse caso, você tem o dobro do trabalho para manter seu sistema. Os dois podem modificar partes da sua API e você tem que ficar atento para que seu sistema não quebre. O WebIntents faz com que você consiga usar um comando para os dois serviços. 

Web Intents, based on an existing capability in Google&#8217;s Android mobile OS, will let Web apps express a simple call for an action, like &#8216;share&#8217; or &#8216;edit,&#8217; which receiving apps will be designed to use, without either app needing to have specific knowledge of the APIs of the other. This way, instead of having to code for each specific Web app one might want to access, developers can just use these simple requests, which will be built into the browser. The Chrome and Firefox teams are each building this functionality for their own browser, but they&#8217;re combining their proposals to use a single API for Web app developers to reach both platforms.

[Paul Kinlan][2], o dono da ideia e desenvolvedor do Google, explica no em um [post no seu blog][3] o que é o WebIntents:

> &#8220;If I built an image gallery application and I wanted to let users edit an image so that they can remove red-eye from a photo I either have to build an application that edits the images, or integrate with a 3rd party solution. Doing this is hard and stops you from building an awesome image gallery; and what happens if the user has a favorite service that they already use to remove red-eye? Simple, you have a frustrated user.&#8221;

Não é de hoje que iniciativas de desenvolvedores e grandes empresas tomam forma para que o desenovlvimento web fique cada vez mais fácil e menos trabalhoso. Isso aconteceu com muitos grupos de desenvolvedores, como o pessoal da [WaSP][4], o pessoal da [WHATWG][5] e mais uma vez agora com o pessoal do [WebIntents][6]. Claro, existem outras iniciativas anônimas que nos fizeram chegar até aqui.

Eu gosto muito muito de uma frase do pessoal da WaSP utiliza há tempos: **If not now, when? If not you, who?**

[Veja aqui o GitHub do Framework.][7]

 [1]: http://www.webintents.com/?utm_source=TablelessComBr&utm_medium=postLink&utm_campaign=link
 [2]: http://paul.kinlan.me/
 [3]: http://paul.kinlan.me/web-intents-a-fresh-look
 [4]: http://webstandards.org/?utm_source=TablelessComBr&utm_medium=link&utm_campaign=postLink
 [5]: http://www.whatwg.org/?utm_source=TablelessComBr&utm_medium=link&utm_campaign=postLink
 [6]: http://www.webintents.com/?utm_source=TablelessComBr&utm_medium=link&utm_campaign=postLink
 [7]: https://github.com/PaulKinlan/WebIntents