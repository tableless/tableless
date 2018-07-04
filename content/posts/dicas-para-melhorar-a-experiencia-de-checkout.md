---
title: 'Dicas para melhorar a experiência de checkout'
authors: Leticia Mayumi
type: post
pusblishdate: 2018-07-09
date: 2018-07-09
excerpt: 'Afinal, todo o time de desenvolvimento está diretamente ligado com pontos chave na experiência do usuário.'
image: https://i.imgur.com/jqw5Axk.jpg?2
sponsor: alura
categories:
  - front-end
  - design
tags:
  - front-end
  - design
---

No aplicativo de uma loja de ecommerce tínhamos um processo de checkout - todo o processo desde a compra até o pagamento -, que seguia essa ideia:

> **_Coletar itens de compra > Realizar pagamento > Confirmação_**

Nesse fluxo pensamos apenas na lógica do processo:

> **_Escolher itens > Carrinho de compras > Informações de entrega e pagamento > Confirmação_**

A partir desse fluxo chegamos a essas telas:

![](https://i.imgur.com/fi36C2h.png)

Só que, quando passamos por testes de usabilidade, percebemos que o maior problema desse processo para o usuários era que **parecia longo e chato de concluir**.

Tudo bem que, identificados os produtos no carrinho de compras, poderiam ter uma noção da compra final que queriam realizar, afinal, a analogia do carrinho de compras com a realidade era justamente de conseguir juntar todos os produtos de interesse e ter uma noção do que estávamos nos comprometendo a levar.

Mas, no passo seguinte de informações de entrega e pagamento, eram tantas coisas para pensar e preencher que o usuário já nem lembrava mais dos detalhes da compra.

Então, quando repensamos esse processo, o critério era conseguir melhorar a experiência de uma das partes mais importantes do app, até porque, se o usuário desistisse na reta final de compra, perderíamos mais vendas.

Então trabalhamos essas melhorias em etapas.

## Reduzir informações desnecessárias

Percebemos que o maior gargalo na experiência para os usuários ficava no processo de pagamento, que reunia todas aquelas informações para o usuário preencher.

Analisando todas as informações que o formulário pedia e quão relevantes eles eram para aquele momento do checkout, conversamos com o cliente para negociar a redução desses campos apenas às informações importantes para concluir cada etapa.

Então chegamos em uma redução bem legal:

![](https://i.imgur.com/u6bsezU.png)

Essa redução foi pensada junto com o cliente justamente para entendermos quais os interesses dele e as manobras para coletar as informações que pudessem ser importantes para o cliente mais tarde. Quer dizer, pegando algumas informações, podemos recolher dados que ajudam a identificar o perfil desse consumidor, direcionar promoções, etc., portanto são coisas difíceis de simplesmente descartar. 

No final, a redução foi enxugada ao máximo, mas ainda sobraram vários campos a preencher.

## Organizar blocos de informação

Antes de continuar a tentar reduzir essa quantidade de informações apresentadas, percebemos que algo importante era identificar a relação que cada etapa tinha uma com a outra.

![](https://i.imgur.com/7SP60gG.png)

Note que agora temos títulos que criam blocos de conteúdo relacionado.

A simples adição de uma divisão já ajuda a orientar melhor o que estamos preenchendo e o motivo dele estar lá.

Beleza, mas e agora? Já tentamos reduzir ao máximo, como melhorar a experiência se precisamos de todas aquelas informações?

## Dividindo o processo

Como ainda tínhamos bastante informações a apresentar, recorremos a uma nova forma de apresentar esse conteúdo, desta vez, fragmentado:

![](https://i.imgur.com/RCPbvpW.png)

Dividimos em telas cada bloco de informações. Se tinham relação, beleza, **deixamos junto para fazer sentido em contexto**, se não, separamos. Todas as informações ainda seriam coletadas, mas criamos uma sensação de mais fluidez ao processo, algo que [resgatamos do padrão que os Wizards trabalham em UI](http://blog.alura.com.br/coletando-informacoes-do-usuario-atraves-de-wizards/).

E, se tratando de wizards, trouxemos também as boas práticas desse padrão, como a inclusão de uma barra de progresso, que guiava o usuário em quais etapas tinha a seguir e em qual estava.

![](https://i.imgur.com/VffrcA2.png)

Deixamos ainda que o usuário tivesse controle para ir e voltar entre as etapas do checkout, clicando nos títulos da barra de progresso.

Agora sim, o processo ficou muito mais enxuto.

## A vantagem do cadastro de usuário

Uma boa prática para aplicativos desse tipo, de ecommerce, é não recolher os dados do usuário como pré-requisito para que ele conheça o produto. 

Se fôssemos implementar isso no aplicativo da loja, logo depois que o usuário passasse pela *Splash Screen* na abertura do app, teria que inserir seus dados para começar a conhecer.

O problema disso é ter que comprometer o usuário em um momento que ele ainda está em processo de conversão. Isto é, criamos uma barreira que inibe a participação dele no app, afinal, por que eu passaria informações tão pessoais minhas sem nem saber se aquilo vale a pena? Vão usar esses dados em algo ruim? Será que é um app confiável e de credibilidade?

Para evitar que isso aconteça e **permita uma maior liberdade no primeiro contato com o app**, inserimos um registro, ou login, apenas quando oportuno, isto é conhecido como [Lazy registration](http://blog.alura.com.br/quando-coletar-cadastros-de-usuario/).

No caso do ecommerce que refatoramos, o momento que identificamos ser muito relevante foi justamente quando, no processo de checkout, o usuário passa pela parte de identificação, quando poderá entrar com sua conta de usuário e, a partir do que já cadastrou, resumiremos uma etapa.

![](https://i.imgur.com/H8dpEHP.png)

Note que agora muitas coisas já vêm preenchidas, logo, diminuímos ainda mais passos e tornamos o processo mais dinâmico e prático.

Lembrando que é importante **não exagerar no formulário de cadastro** também, já que nesse momento queremos apenas que ele insira o essencial de informações para a compra.

Agora que já temos o contato dele, podemos pedir depois que atualize com informações relevantes para seu perfil de usuário e para a base de dados do cliente.

## Checkout: atenção aos detalhes

Falando em experiência do usuário, o checkout faz parte do fluxo principal dentro de um e-commerce. Precisamos convencer o usuário de que temos produtos relevantes para ele, fazê-lo juntar seus favoritos e comprar efetivamente tudo o que tiver interesse.

Quanto melhor trabalhada essa parte, melhor será a experiência e a vontade do usuário de retornar. 

Apps que complicam demais a vida do usuário em tarefas que esperamos ser simples e objetivas podem prejudicar a UX.

O que você achou dessas dicas? Já teve experiências legais em outros processos de checkout? Compartilhe com a gente!

---

Na [Carreira de UX da Alura](https://www.alura.com.br/carreira-ux-designer) temos diversas reflexões importantes para pensar em um projeto. :)