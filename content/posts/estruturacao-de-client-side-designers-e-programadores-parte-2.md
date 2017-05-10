---
title: 'Estruturação de front-end – Parte 2: Designers e Programadores'
author: Diego Eis
type: post
date: 2012-05-14
excerpt: Entendendo e sincronizando as necessidades dos designers e programadores.
url: /estruturacao-de-client-side-designers-e-programadores-parte-2/
tweetbackscheck:
  - 1356413012
shorturls:
  - 'a:3:{s:9:"permalink";s:86:"http://tableless.com.br/estruturacao-de-client-side-designers-e-programadores-parte-2/";s:7:"tinyurl";s:26:"http://tinyurl.com/c3zy6om";s:4:"isgd";s:19:"http://is.gd/51TKyf";}'
twittercomments:
  - 'a:27:{i:202935045135142913;s:7:"retweet";i:202388453743276033;s:7:"retweet";i:202386698775175169;s:7:"retweet";i:202371810770173953;s:7:"retweet";i:202204810408239104;s:7:"retweet";i:202201758246768641;s:7:"retweet";i:202201478696402944;s:7:"retweet";i:202193045138046977;s:7:"retweet";i:202176837990887425;s:7:"retweet";i:202168539589787648;s:7:"retweet";i:208180192106127360;s:7:"retweet";i:208179202778857472;s:7:"retweet";i:205289390803660801;s:7:"retweet";i:205285620384399360;s:7:"retweet";i:205280147513933824;s:7:"retweet";i:212539214510825472;s:7:"retweet";i:212535390614208514;s:7:"retweet";i:212527455632752640;s:7:"retweet";i:218331347670933505;s:7:"retweet";i:218326760306130945;s:7:"retweet";i:218325913421619200;s:7:"retweet";i:218325753656389632;s:7:"retweet";i:227749172751790081;s:7:"retweet";i:237176533846994945;s:7:"retweet";i:235720289017802752;s:7:"retweet";i:258190348071870465;s:7:"retweet";i:270878768162304000;s:7:"retweet";}'
tweetcount:
  - 90
dsq_thread_id: 689490615
categories:
  - Código
  - Técnicas e Práticas
tags:
  - 2012
  - Código
  - front-end

---
Se dividirmos as áreas de desenvolvimento, chegaremos a 3 grandes grupos, totalmente distintos que são: designers, programadores e nós, front-end.

Nós estamos no meio dos dois grupos. Nós nos relacionamos diretamente com os dois profissionais, fazendo uma ponte e tentando adequar as necessidades de cada um durante o projeto. E é aí que entra o problema.

Os dois mundos são totalmente diferentes. O designer se preocupa em deixar o sistema lindo, maravilhoso, fácil de usar, vendável e etc. O programador faz com que tudo funcione. O cliente tem que conseguir comprar quando clicar no botão. Nosso trabalho é fazer com que a beleza não estrague a funcionalidade. É fazer com que as necessidades do programador não entrem em conflito com as necessidades do designer. Nesse meio entra o seu trabalho. Sua obrigação é deixar o site acessível, com código de fácil indexação e escalonável ao mesmo tempo que você deixa o layout do designer fiel ao original do Photoshop.

### Necessidades dos Designers

Os designers precisam de liberdade para criar. Isso sempre foi muito difícil na web e por isso o Flash ganhou tanta atenção. Se antes só podíamos fazer coisas básicas utilizando CSS, o Flash dava ao designer acesso a um mundo de possibilidades. Atualmente isso mudou muito graças ao Santo protetor dos desenvolvedores front-end.

Com a vinda das features do CSS3, boa parte das funcionalidades que antes tínhamos que fazer gambiarras com imagens, hoje podemos fazer com apenas uma propriedade. Quem nunca passou horas recortando imagens de bordas arredondadas, sombrinhas e degrades? Hoje resolvemos tudo diretamente pelo CSS, que roda mais rápido e é muito mais flexível.

A ideia é transportar fielmente a arte que o designer criou no editor gráfico, para código HTML/CSS. Nesse momento você precisa se preocupar com duas coisas: fidelidade de layout e semântica de código. 

O código HTML irá refletir os elementos do layout, traduzindo a informação visual, para informação em código semântico de forma que os dispositivos, robôs de busca, scripts e afins acessem esse código e executem suas tarefas. O Google precisa saber o que é um link e um botão. Mesmo que eles tenham o mesmo design. O leitor de tela precisa entender o que é um título e um parágrafo. Isso tudo aliado com os detalhes visuais que o designer desenhou, como sombras, degrades, transparências, bordar arredondadas e etc.

Esse processo inicia a fase de código do projeto. Estamos criando uma estrutura que vai perdurar o projeto inteiro. Os programadores, posteriormente, irão produzir o sistema em cima deste código. Por isso é muito importante que sua base seja bem estruturada mas ao mesmo tempo super flexível para mantermos o layout da maneira correta.

### Necessidades dos Programadores

Os programadores precisam automatizar coisas. O projeto precisa que as tarefas sejam automatizadas para que o projeto funcione de forma escalonável e sem a necessidade de replicação de código desnecessariamente. Essas tarefas vão desde a criação de formulários até comunicação com o servidor.

O problema é que a maioria das vezes essas tarefas automatizadas não são criadas pelos programadores da equipe. São plugins, scripts e etc que foram criados pela comunidade. Não estou dizendo aqui que isso é ruim, por favor. Na verdade, é o certo. Não tem sentido recriarmos algo que já existe e que funciona muito bem. Esses plugins, scripts e etc foram criados por outros programadores que um dia tiveram a mesma necessidade que os programadores do seu projeto e por isso, nada mais sensato do que criar um plugin para ajudar outros devs com a mesma necessidade. Acontece que programadores, são programadores. Eles não tratam o HTML com o mesmo carinho que nós.

Vamos pegar um exemplo de formulários. Os programadores aqui onde trabalho programam em RUBY, utilizando Rails. Há uma GEM que cria e gerencia formulários no projeto. O código que esta GEM gera por default não é legal e o pior, é totalmente diferente do código que você usaria ou usou no projeto &#8211; Por isso é interessante entender quais ferramentas os programadores utilizarão antes de iniciarmos nosso código HTML. Assim podemos adaptar o que for preciso para códigos que fujam do seu padrão pessoal.

Você não pode obrigar os programadores a fazerem tudo na mão. Se você conseguir, ótimo. Essa é sempre a minha primeira opção&#8230; Mas caso isso seja impossível, sugiro que sente e tente entender o maldito plugin. Converse com o programador e tente mostrar as desvantagens para o projeto caso continuem a utilizar o código default. Veja se não há a possibilidade de modificar esse código. Na maioria das vezes há. Caso não dê, estude a possibilidade de trocarem para um plugin que dê.

Existem frameworks &#8211; como o Web2Py &#8211; que ainda utilizam tabelas para exibir formulários. Chorei sangue quando eu vi pela primeira vez e chorei mais ainda ao descobrir que não é algo muito fácil customizar esses código para que ele entregasse o HTML que eu queria. Paciência.

### Sincronizando as necessidades

O encontro de dois mundos gera o problema. Sincronizar as necessidades visuais dos designers com as necessidades de código dos programadores é algo que geralmente deixa traumas em qualquer dev front-end.

O programador precisa usar ferramentas que os ajudam a executar tarefas complexas, mas que adulteram demais o código. O designer precisa que seu layout seja fielmente seguido, ou seja, todas as firulas visuais como sombras, degrades, bordas, backgrounds e etc permaneçam intactas. Como você pode manter o padrão de qualidade se o código manipulado não é o seu, mas o do plugin? É aqui que os front-ends maricas pedem arrego. 

Cada efeito visual, cada estrutura, cada necessidade de layout determinam com que o HTML será escrito. Se o HTML é criado automaticamente por um plugin ou algo parecido, como você faz? Entende a questão?
  
Você até faz o layout ficar igual ao planejado, mas e a semântica? O design, a funcionalidade e a semântica precisam coexistir. Essa é a essência da responsabilidade do profissional client-side.

Não há mágica que faça isso tudo acontecer. Você precisa sentar e conversar. Eu costumo chamar o designer e o programador e explicar minhas limitações. Eles entendem e cada um abre mão de algo que pode me ajudar. O designer tira aquele efeito visual desnecessário e o programador tenta colocar aquela classe importante e retirar um ou outro código automático. A opção de conversar com os dois é melhor do que você criar uma solução com Javascript. Para retirar ou inserir as tags ou classes que você precisa. O código fica mais feio e seu site perde performance. Sem contar que para resolver suas pendências manipulando o DOM com Javascript, é pior para o Google, para os leitores de telas e para os robôs em geral.

### Padronizando tudo

Uma outra solução que eu cheguei é mais complicada, mas sem dúvida a mais duradoura. Começamos a criar dentro da empresa uma biblioteca que une código HTML/CSS semântico com o visual predefinido dos designers e que contemple as necessidades de funcionalidades dos programadores.

Assim, começamos a criar uma **cultura** de padronização de código que vai perdurar por várias gerações de serviços e acima de tudo, não quebra a linearidade dos produtos em si. Manteremos a uniformidade de código com a a uniformidade de identidade visual dos sistemas. Não estamos engessando a criação, pelo contrário, estamos criando uma base sólida que poderá ser reutilizada em toda a empresa, em larga escala e independente.

Veja a primeira parte deste artigo: [Préprocessadores, Framewoks e Bibliotecas][1]

 [1]: http://tableless.com.br/estruturacao-de-client-side-preprocessadores-framewoks-e-bibliotecas-parte-1/ "Estruturação de Client-side – Parte 1: Préprocessadores, Framewoks e Bibliotecas"