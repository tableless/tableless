---
title: Treinando Inteligência Artificial para fazer código front-end
authors: Diego Eis
type: post
date: 2018-03-13
image: https://i.imgur.com/Zhqfl1S.jpg
excerpt: 'Como um programador treinou uma máquina para fazer HTML e CSS a partir de Mockups'
categories:
  - Técnicas e Práticas
  - Tecnologia e Tendências
  - Mercado
  - Notícias
Tags:
  - Técnicas e Práticas
  - Tecnologia e Tendências
  - Mercado
  - Notícias
---

> Within three years, deep learning will change front-end development. It will increase prototyping speed and lower the barrier for building software.

E assim começa o artigo do [How you can train AI to convert design mockups into HTML and CSS](https://thenextweb.com/syndication/2018/02/11/can-train-ai-convert-design-mockups-html-css/) escrito [Emil Wallner](https://twitter.com/EmilWallner) no The Next Web. No artigo ele explica como ele usou Machine Learning para transformar mockups em HTML e CSS, com código semântico, de forma consistente e automática. 

[O Airbnb já tem alguns experimentos desse tipo](https://tableless.com.br/gerando-codigo-de-wireframes-de-baixa-fidelidade/), onde a partir de um simples mockup, a máquina já consegue fazer predições de código HTML que representam aquele design, mas o artigo do Emil mostra que esse tipo de abordagem está muito mais avançada do que imaginamos. 

Atualmente a grande barreira de automatização de front-end é o poder computacional. Contudo, nós podemos usar algoritmos atuais de deep learning com treino de dados sintetizados para começar a explorar automação front-end com inteligência artificial.

Foram usados imagens de mockups de design para para treinar uma rede neural a fazer código HTML e CSS. O processo é mais ou menos esse:

**1. Mostre uma imagem de design para uma rede neural treinada**

![](https://blog.floydhub.com/static/image_to_notebookfile-3354b407064e4d95a0217612a5463434-4a3e0.png)

**2. A rede neural converte essa imagem em código HTML**

![](https://blog.floydhub.com/generate_html_markup-b6ceec69a7c9cfd447d188648049f2a4.gif)

**3. Os assets com o output é gerado**

![](https://blog.floydhub.com/static/render_example-4c9df7e5e8bb455c71dd7856acca7aae-6c1a3.png)

A lógica principal do trabalho é construir uma rede neural que geral marcação HTML/CSS que corresponda ao screenshot/mockup.
Para treinar essa rede neural, eles dão uma série de screenshots  que representam aquele pedaço de HTML para a máquina. A máquina por sua vez aprende predizendo o código HTML, tag por tag.  Quando a máquina prevê qual é a tag, ele recebe novamente o screenshot e toda a marcação correta até aquele ponto, para validar os erros e acertos.

O Emil montou uma planilha simples que mostra como é o [treino de dados representado em palavras aqui](https://docs.google.com/spreadsheets/d/1xXwarcQZAHluorveZsACtXRdmNFbwGtN3WMNhcTdEyQ/edit#gid=0).

Ele explica que a ideia de predição é mais ou menos assim:
Suponha que a máquina tenha que predizer a sentença "Eu posso codificar." Quando ele recebe a primeira pista da predição, ou seja, a palavra "Eu", ele prediz que a próxima palavra será "posso". A próxima pista que ele terá será "Eu posso", então a máquina irá predizer que a próxima palavra será "codificar". Então, ele recebera sempre todas as palavras anteriores e terá que prever apenas a próxima palavra. Isso é aplicado, em vez de com palavras, com as tags HTML/CSS. 

![](https://blog.floydhub.com/static/input_and_output_data-555f7b04c75a202041f0a4438af5cd51-6c1a3.png)

A partir dos dados, a rede neural cria recursos. A rede neural constrói recursos para vincular os dados de entrada com os dados de saída. Ele tem que criar representações para entender o que está em cada captura de tela, a sintaxe HTML, que previu. Isso cria o conhecimento para prever a próxima tag.

Agora sendo bem franco, para mim é incrível esse processo todo. Eu não entendo muito desse negócio de Machine Learning, mas ele explica que existem várias abordagens de predição e a abordagem usada por ele de "palavra por palavra" é a mais comum. 

No artigo, ele mostra como fazer um Hello World.

![](https://blog.floydhub.com/hello_world_generation-039d78c27eb584fa639b89d564b94772.gif)

E tem uma grande explicação de como funciona todo o pensamento de como fazer a máquina entender a imagem e montar o código inteiro. 

Aqui está a versão pronta do experimento que ele fez: [https://emilwallner.github.io/html/550_epochs/](https://emilwallner.github.io/html/550_epochs/).

Eu achei o código BEM ÓTIMO. Dado que agora a semântica do código não é a coisa mais importante do mundo, dado que existem formatos como o JSON-LD que abstrai a semântica do código HTML. 

Pelo que pude entender, o CSS não é feito automaticamente como o HTML, exatamente porque a máquina não cria o design, logo, ainda deve existir um trabalho para criar um CSS personalizado. No exemplo do Emil, ele usou Bootstrap para combinar o HTML e CSS. Isso é ótimo para sistemas padronizados, tipo, sistemas administrativos. Ainda não deve fazer milagres para designs personalizados, mas para mim, isso é questão de tempo, dado que ele vai conseguir ler relacionar elementos de um layout no Sketch, por exemplo, com o código CSS.

Ao final do artigo tem o código que ele usou para fazer o teste de exatidão e o código para fazer a predição.

Acho que vale a pena dar uma lida no artigo inteiro. É pelo menos muito interessante entender como esse negócio de Machine Learning funciona.

São coisas assim que me fizeram escrever o artigo [O fim da profissão front-end](https://tableless.com.br/carreira-de-front-end-vai-morrer/), entendendo que num futuro próximo não será mais necessário escrever código front-end. O que me leva a querer escrever um outro artigo, sobre "O que você, dev front-end, vai fazer com o tempo economizado pelos robôs"?
