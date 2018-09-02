+++
authors = "Macgyver"
canonical = ""
categories = ["javascript", "reactjs"]
date = "2018-08-27T09:29:58-03:00"
excerpt = "Dicas para dar manutenção pro seu app React + Redux"
image = "https://i.imgur.com/PT3Icdw.jpg"
publishdate = "2018-08-27T09:29:00-03:00"
tags = ["reactjs"]
title = "Como evitar que seu app React com Redux vire um ninho de rato"
type = "post"

+++
React com Redux é um bicho de 7 cabeças sim! Mas é domesticável.

Esse post é um compilado de humildes dicas pra você, cidadão novo na vida de front-endista, usar no seu projeto de React + Redux pra ele não virar uma bagunça. Por que sim, um app feito com esses dois, pode sim virar uma massaroca de código que desrespeita o intelecto e a saúde mental dos seus colegas de trabalho.

Existe algumas causas do porquê isso acontece, mas é assunto pra um outro post.

As dicas aqui são para projetos pequenos, como de Startups, onde poucas, ou só uma pessoa atuam no front-end. Geralmente os membros dessas equipes não tem cargos muito específicos. Uma pessoa especializada em back-end acaba, de vez em quando, indo no front-end pra fazer alterações mais simples ou colocando aquele plugin maroto no site. Por isso é importante que quem for trabalhar no app consiga se achar no código, mesmo não tendo tanta experiência com react.

Então vamos lá!

***

# create-react-app

O [create-react-app](https://github.com/facebook/create-react-app) é o CLI feito pelo facebook pra te ajudar a cuspir um app React sem muita dor de cabeça. Disso provavelmente você ja sabe, mas a questão aqui é: use esse cara pelo amor de Deus!

Não comece um projeto do zero, configurando um mundo de coisas no Webpack e etc. Se você ja configurou um na vida, eu acho que nem preciso te falar o porquê isso seria uma perda de tempo enorme.

Outra coisa: **Evite ejetar do boilerplate**. Eu sei que é tentador usar todos aqueles imports e mágicas que a gente vê em projeto gringos, e que só são possíveis quando vc faz o eject do boilerplate default do Facebook. MAS isso não é nenhum pouco necessário no início. E sua vida (assim como a dos seus colegas de trampo) será muito mais tranquila mantendo a simplicidade inicial pelo maior tempo possível.

Sendo assim, as próximas dicas estão levando em conta que você usa o boilerplate default do create-react-app

# Separando pastas

Aqui vai uma boa estrutura de pastas, foca da `src`:

    my-app
    ├── public/
    └── src
        ├── layouts/
        ├── pages/
        ├── components/
        ├── containers/
        ├── actions/
        ├── reducers/
        ├── services/
        └── helpers/

## Layouts

Como você já deve saber a essa altura do campeonato, as rotas no react são quase sempre criadas com o [react-router](https://github.com/ReactTraining/react-router). E por mais estranho que pareça, as rotas são escritas junto com o "[HTML](https://reactjs.org/docs/introducing-jsx.html)". Sendo assim, ao invés de ter um monte de rotas perdidas por ai no seu código, concentre todos os componentes de rotas dentro da pasta layouts.

Aqui vai um exemplo de componente layout. Esse _PrimaryLayout_ é o component responsável por gerenciar as rotas da aplicação à partir da raiz:

<script src="https://gist.github.com/MacgyverMartins/842282e916dd25553ecb32c488bdce37.js"></script>

## Pages

O próprio nome ja diz né. Mesmo que seu produto seja 3 telas, é muito importante tem um wrapper pra cada tela. Ter um wrapper vai te dar um contexto para manipular o estilo dos componentes filhos. Vou abordar esse tema de contexto + components em outro post e por o link aqui, mas basicamente significa que vc pode ter um estilo css específico pro seu componente, e alterar o comportamento dele para contextos específicos usando a class wrapper da página.

As "regras" aqui são:

* Esse componente deve ser exportado com o nome da página + prefixo **Page.** Ex: **HomePage**
* A div que faz o wrapper do component deve ter o mesmo nome dele, trocando o uppercase por hífen. Ex: **home-page**

Um exemplo de página:

<script src="https://gist.github.com/MacgyverMartins/6e293d4f09630d4d7be6025f575be9f2.js"></script>

## Components

Sem mistérios aqui também. As únicas regras são:

* Seguir a mesmo lógica de class wrapper das páginas. Ou seja, se seu component se chama MainMenu, a class wrapper será main-menu
* Os components daqui não se conectam direto com o Redux state. Quem faz isso são os **Containers.** Os components aqui só recebem dados nas props, fazem o trampo com o state e etc. Apenas oq os components existem pra fazer

## Containers

Beleza! Agora os containers.

Esses cidadões aqui são os quem conectam com o Redux state e fazem a mágica de atualizar os components filhos.

Não saia conectando todos os components do seu app no redux como se não houvesse amanhã. Ou vc vai entender o conceito de atrofiamento cerebral quando precisar descobrir quem é que está lendo/setando um valor q esta espalhado em vários lugares no app. Sem contar todo o B.O de re-render e etc.

![](https://cdn-images-1.medium.com/max/800/1*KFBDttMDWN_MktzeztWG-A.jpeg)

* Esses componentes devem ser exportado com o nome do component + prefixo **Cont.** Ex: **MainFilterCont**
* Os arquivos serão nomeados com .container Ex: MainFilter.container.jsx

Essas duas regrinhas ai de cima vão ajudar muuuito quando vc for debugar, criar feature e etc. E será muito fácil bater o olho no código e identificar de cara um container.

Exemplo de um container e como ele ficaria importado em um component:

<script src="https://gist.github.com/MacgyverMartins/6522dd02dee46a1eed29da08c08a1fbf.js"></script>

<script src="https://gist.github.com/MacgyverMartins/e9bd8d6e2cf2a766641e1f64693f5896.js"></script>

Eu sei que esse container ai parece muito verboso, mas na vida real os containers são maiores, então faz sentido destrinchar bem as coisas, para achá-las com mais facilidade depois.

## Action e Reducers

Você ja sabe como isso aqui funciona. Então só umas dicas bem pessoais:

* As actions tem a extensão .actions Ex: customers.actions.js
* Os reducers tem a extensão .reducer
* Ao invés de criar uma pasta com constantes das actions type e importar nas actions e reducers, Eu prefiro exportar as constantes direto das actions. Assim os reducers importam direto das actions e fica tudo lindo. EX:

<script src="https://gist.github.com/MacgyverMartins/c95678b3a0afbd88c0c0a5949cc8fea2.js"></script>

<script src="https://gist.github.com/MacgyverMartins/c95678b3a0afbd88c0c0a5949cc8fea2.js"></script>

Ja vi projetos onde a constant é usada tbm no nome da action, mas como existe casos que é melhor um action.type mais autoexplicativo, eu prefiro deixar as coisas separadas.

**BONUS**: Aqui eu estou usando uma lib chamada [redux-promise-middleware](https://github.com/pburtchaell/redux-promise-middleware)que facilita mt encaixar código assíncrono no data-flow de react+redux

* De nomes para as actions type que realmente signifique o que ela fez ou vai fazer. Isso irá facilitar muito a vida e o debug no devtool. Um type: _customer_ é muito genérico. Escreva coisas como _set customer, get customer, remove customer, wtf is this customer_ e por ai vai.

## Services e Helpers

A intenção de ter a pasta services é apenas pra separar APIs e serviços de terceiros, do core sua aplicação. Óbvio.

Os helpers são pra você reaproveitar seus códigos e dizer pro seus amigos que você segue DRY a risca. Mas por favor, crie um padrão para export e import desses dois caras. E principalmente, de nomes que façam sentido.

Agora, o mais importante dessa parte é que, vc só vai criar esses arquivos se valer muuuuito a pena. Se não, [NPM](https://www.npmjs.com/) ta ai pra isso.

# Tenha padrões internos do projeto

Tenha um padrão de como é a estrutura de container, reducer, actions ou qualquer modulo do projeto. Teste o que funciona melhor com sua equipe e o mantenha.Você só tem a ganhar com isso.

Para manter um padrão, é importante fazer code reviews prestando bastante atenção se o você e os amiguinhos estão seguindo o que foi acordado.

Quanto mais padrão tiver seu app, mais rápido você e outras pessoas se acostumam com ele, e conseguem ir direto para as partes mais importantes da task ao invés de levar tempo entendendo o que está acontecendo no código.

Tendo um padrão de componente, container, redux e etc.. Você pode criar snippets de boilerplate pra sua equipe. Dessa forma, prototipar ou implementar features novas vai ser uma bala.

# Não sabe brincar, devolve os hominho

React com Redux é feito pra você usar todo o conceito de reatividade e _one way data flow_, sem medo. Então, não fique usando callbacks pra saber quando algo aconteceu no app, retornando promises de actions ou alterando state através de services ou middleware. Isso fará você ir contra a principal ideia da brincadeira que é tudo ser reativo e trackeavel (não sei se existe essa palavra).

Se o state mudou, existe uma action (com um bom action type) pra dizer o porque aquilo aconteceu. Por exemplo: Se um botão na sua aplicação precisa mudar de cor depois de uma info no app mudar, isso significa q ela tem que "reagir" (trocadilho alert) a mudança de state do app. O botão precisa esperar um evento específico acontecer que irá avisar quando a info mudar no reducer. Quando isso acontecer, o botão vai automaticamente receber a info nova, e fazer o re-render, trocando a cor no final.

Pode parecer muita coisa acontecendo, mas na verdade é só uma forma diferente de olhar o fluxo de dados no app. E é a forma default do Redux trabalhar com React.

Não é sua responsabilidade como dev informar em um callback pro botão, q ele tem que mudar de cor. Use o data flow, state e props do React como eles deveriam ser usados

Claro que, as vezes, em casos muito específicos e bem explicados no seu Pull Request, você pode acabar fazendo um dispatch de dentro de um middleware ou usando callbacks com interações para fora do seu component. Mas deixe isso pra ocasiões muito especiais. A maioria dos desafios de um app podem ser resolvidos usando a simplicidade da reatividade.

# Estilização, SASS, mudar as corzinhas e etc

Bom, essa parte só funciona se vc seguiu direito as dicas de wrapper classes.E eu tbm já estou contando que você está usando SASS. Se não estiver, ja sabe né.

A pasta de estilo deve seguir a estrutura da src. Ou SEJA você terá uma pasta pages/ com o home-page.scss la dentro, uma pasta para components e assim por diante. No final, uma index importa todo mundo e faz a mágica.

Você pode [seguir a guia oficial](https://github.com/facebook/create-react-app/blob/master/packages/react-scripts/template/README.md#adding-a-css-preprocessor-sass-less-etc) do create-react-app pra adicionar o sass no seu projeto, **sem fazer o eject**

**BONUS:** Eu recomendo apontar o entry point do build-css para o _/styles/index.scss_ ou invés de apenas para _/styles_ como mostra no guia. Assim você não vai acabar com um monte de css dentro de uma pasta q ja tinha sass originalmente.

Leve a arquitetura do CSS da sua aplicação muito a serio. Poucas coisas nessa vida conseguem causar uma sensação de desespero tão grande como dar manutenção em um CSS ruim.

![](https://cdn-images-1.medium.com/max/800/1*xi7ddfL9LpTH-pdY20Y_Cw.gif)

#### Cada um manda no seu

E por fim, vamos falar de contextos.

Cada component tem seu estilo específico e que funciona independente de onde ele está no app. Isso mesmo! INDEPENDENTE.

Sempre que for preciso alterar o comportamento de um component, você deve ser perguntar: _Essa alteração será aplicada a todos os lugares onde esse component está ou será apenas pra esse contexto específico?_

Se a resposta for sim, beleza, vc altera o estilo do component no respectivo arquivo e ja era. Se for não, então vc **nem chega perto do sass** do component. Ao invés disso, cabe ao contexto a responsabilidade de alterar o estilo através da hierarquia de classes, usando o wrapper class como endpoint

**Exemplo:** Você precisa alterar o background do componente **Card** apenas para a página home.

ERRADO:

    //styles/component/card.scss
    .card {
      background: #eee
    }

CERTO:

    //styles/pages/home-page.scss
    .home-page {
      .card {
        background: #eee
       }
    }

***

![](https://cdn-images-1.medium.com/max/800/1*V33kq484lKxkHxHA28CXIQ.gif)

É isso ai por hoje.

Essas dicas ai saíram da minha cabeça. Então é óbvio que tem como deixar ainda melhor. Se você tem alguma contribuição, deixe nos comentários e vamos atualizando o post :)

# Se você gostou, fortalece com aquele comentário

Eu escrevo apenas pra compartilhar e aprender mais. Se esse artigo te fez pensar melhor a respeito do React + Redux, deixa aquele seu comentário.

Compartilha esse artigo com pessoas que vc acredita quem vão aprender coisas legais com ele. Ou envie pra aquele ser humano que você sabe que ta num momento difícil do relacionamento com o Redux.