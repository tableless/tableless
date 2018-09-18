---
title: Node.js - o back-end do front-end
authors: Tableless
type: post
date: 2017-07-17
excerpt: Um pouco sobre hospedagem e a história do Node.JS
categories:
  - Javascript
  - publieditorial
tags:
  - nodejs
  - Javascript
image: https://i.imgur.com/l65nOub.png
---

O Node.js se tornou popular a partir de 2009 quando Ryan Dahl, criador do Node.js, divulgou seu projeto para o mundo. De lá para cá ele só tem crescido e ajudado o JavaScript a se popularizar ainda mais com a "Linguagem da Web", agora, não apenas por ser praticamente onipresente na web, mas por quebrar a barreira de ser usada apenas no front-end, passando a ser usada também no Back-end.

Se liga na Timeline legal que o Gergely Nemeth fez contando a história e os passos do Node.js:

<iframe src="//cdn.knightlab.com/libs/timeline3/latest/embed/index.html?source=1rt8Xqpno-s7oNFCEKMYHoJexw24DIUcSkTABx2avcV8&amp;font=Default&amp;lang=en&amp;initial_zoom=2&amp;height=650" width="100%" height="650" frameborder="0"></iframe>

Aqui você também consegue [ver a lista de todos os contribuidores](https://github.com/nodejs/node/blob/master/AUTHORS) do Node.js, por ordem de contribuição. São 1417 contribuidores até agora.

Um desenvolvedor que trabalha com Node.js é um back-end ou um front-end?
Eu brinco bastante com isso com alguns front-end que se embrenham no mundo do Node.js, porque dado que podemos chamá-lo uma linguagem hack-end, o ser que começa a programar em Node.js, começa a fazer Back-end. Logo, essa divisão de front-end + back-end passa a não fazer mais sentido. Nós trabalhamos com uma linguagem de programação, que pode ser usada tanto no front, quanto no back e pronto.

A partir de uma ideia tão legal quanto o Node.js, surgiu o **io.js**. O io.js apareceu em Dezembro de 2014, a partir de um fork do Node feito pelo Fedor Indutny (que pela lista do Node, foi o 112 contribuidor do Node), mas que era um integrante core do time.

O problema era que entre 2014 e 2015, a quantidade de commits no projeto do Node caíram bastante e como o Node estava ganhando popularidade, isso prejudicou um bocado quem já tinha adotado a tecnologia. Além disso, a galera não estava gostando muito da forma com que a Joyent - que é a dona da marca Node.js - estava levando a governança da coisa toda. Aí você já sabe: a galera insatisfeita com o caminho que o projeto estava tomando, forkou o projeto e criaram o **io.js**. Mas isso nem durou tanto tempo, logo depois, em 2015, houve um merge do **io.js** para o projeto original, que já estava na versão 4 e os dois grupos voltaram a trabalhar juntos sobre as regras da **Node.js Foundation**. E desde 2016 o site do **[io.js](https://iojs.org/en/)** recomenda o Node.js.

[Nesse post](https://anandmanisankar.com/posts/nodejs-iojs-why-the-fork/), o Anand Mani fala um pouco de toda essa história que rolou entre io.js e Node.js.

Para hospedar Node.js é simples: a plataforma inteira do Node pode rodar em Linux, OS X ou FreeBSD e até em Windows. Como várias linguagens, o Node também pode ser controlada via linha de comando. Existem algumas empresas online que facilitam a hospedagem de Node.js, como a [Umbler](https://www.umbler.com/br/), que tem um [serviço maneiro que roda o Node.js em um container Docker](https://www.umbler.com/br/hospedagem-nodejs), com MongoDB nativo e tudo o que tem direito. Você não precisa ficar configurando servidor para lá e pra cá. Só chegar e já era.
E hoje, com hospedagem barata, não há desculpa para você não começar a aprender um pouco que seja de Node.js.

Para aprender Node.js é importante ter uma base de JavaScript, para isso existem cursos online, por exemplo, vídeos no Umbler Academy, tutoriais e comunidades no Facebook e Google+. Para quem quiser ir além, vale estar por dentro de MongoDB e Docker - duas tecnologias utilizadas pela maioria dos desenvolvedores em Node.js, de acordo com pesquisa da Node.js Foundation.

### Para ler mais
- Uma [categoria inteira do Tableless sobre Node.js](https://tableless.com.br/categories/nodejs/)
- [IoT - Node.js - Arduino etc - NodeJS](https://forum.tableless.com.br/t/iot-node-js-arduino-etc/243)
- Se você se decidiu pela Umbler, eles tem uma [área inteira com tutoriais de Ajuda com Node.js](https://help.umbler.com/hc/pt-br/articles/115001793863)
- [Podcast da Umbler](https://academy.umbler.com/umblercast-mandanodes/)
- [História sobre a quebra do Node.js e o io.js](https://anandmanisankar.com/posts/nodejs-iojs-why-the-fork/)
- [Vídeo Primeiros passos com Node](https://academy.umbler.com/primeiros-passos-com-node-js/​)
