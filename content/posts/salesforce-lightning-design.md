---
title: Salesforce Lightning Design System
authors: Diego Eis
type: post
date: 2017-12-21
excerpt: Uma coleção de padrões de designs, componentes e guidelines da Salesforce
image: https://i.imgur.com/C43GNJS.png
categories:
  - Design
  - front-end
  - UX
  - framework
  - biblioteca
tags:
  - Design
  - front-end
  - UX
  - framework
  - biblioteca
---

Eu sei que criar uma biblioteca de interface para sua empresa não é algo novo. Empresas fazem isso há anos. Isso virou um padrão muito forte no mercado. Toda reestruturação de código ou de visual, é uma chance para criar uma biblioteca de interface, claro que isso não é ruim, é ótimo, dado que criar uma biblioteca desse tipo te ajuda em uma série de aspectos. Mas o interessante é que sempre que uma grande empresa faz isso, ela divulga seu projeto para o mundo, permitindo que todos possam usar ou pelo menos aprender com elas.

![](https://i.imgur.com/ylgyNha.png)

A bola da vez é o [Salesforce Lightning Design System](https://www.lightningdesignsystem.com/), que é uma coleção inteira de componentes e guidelines de Design que a Salesforce disponibiliza para a comunidade.

![](https://i.imgur.com/ViJGjKb.png)


Os componentes são blocos que compoem as aplicações da Salesforce, permitindo que os designers e desenvolvedores diminuam os processo de criação e aplicação dos layouts. Esses componentes estão disponíveis em HTML e CSS, além de [Templates de Sketch disponíveis para download](https://www.lightningdesignsystem.com/downloads/#ui-kit).

![](https://i.imgur.com/ATB9DJt.png)

Eles aplicam a ideia do [Princípio de Responsabilidade Única](https://csswizardry.com/2012/04/the-single-responsibility-principle-applied-to-css/) no CSS, onde cada parte do código CSS faz apenas uma coisa. Não é uma prática incomum e todos os devs fazem isso em algum nível no seu código, dado que é regra geral que cada parte do código possa ser reutilizado em qualquer lugar do sistema/layout sem grandes depêndencias do contexto do layout ou de outras funções do código. A ideia é que todas as classes que eles usam sejam simples, reutilizáveis, simbólico e que tenha apenas uma responsabilidade.

![](https://i.imgur.com/ViJGjKb.png)

Os [Design tokens](https://www.lightningdesignsystem.com/design-tokens/) são coleções de atributos visuais que geralmente hard-coded, como valores hexadecimais, valores de espaços, medidas, etc). Isso permite que o sistema de design permaneça escalável e consistente, além de aumentar ainda mais a customização dos sistemas deles.

![](https://i.imgur.com/YqPBTFx.png)

Algo muito interessante é que todos os componentes do framework foram pensados em ser [acessíveis](https://www.lightningdesignsystem.com/accessibility/overview/) desde que nasceram. Eles previram até um um padrão de navegação por teclado. Além disso, os componentes foram criados de acordo com o padrão ARIA, com atributos que são entendíveis por leitores de tela.

Achei bem completo a biblioteca que a Salesforce criou e serve de exemplo para qualquer empresa que queira chegar nesse nível de organização. Pena que muitas empresas demoram para fazer algo assim, pois querem já ter um framework completo. Se esse for o caso da empresa em que trabalha, tente conversar com o pessoal para convencê-los de começar pequeno. Comece com o padrão de botões, depois cores e assim por diante. Uma biblioteca como essa é construída pedaço por pedaço.