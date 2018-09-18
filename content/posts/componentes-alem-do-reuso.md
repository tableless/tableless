---
title: Componentes além do reuso
authors: Conta Azul
type: post
publishdate: 2018-02-19
date: 2018-02-18
excerpt: Como trabalhar com componentes está tornando obsoleto o conceito de Model/View/Controller?
image: https://i.imgur.com/2vabSUQ.jpg
categories:
  - Javascript
tags:
  - reactjs
  - react-native
---

Vivemos tempos em que o conceito Model/View/Controller está ficando cada vez mais obsoleto fazendo da abordagem Component-Based o padrão atual no desenvolvimento de aplicações web.

Porém, ao mesmo tempo que a abordagem Component-Based tem se tornado cada vez mais popular, percebo ainda muitos desenvolvedores entendendo componentes de um jeito surpreendentemente estranho.

Que tipo de estranheza? (você deve estar pensando)

a) No primeiro caso, vejo desenvolvedores considerando toda uma View como componente. Ou seja, o “componente” é neste caso um enorme pedaço de código extremamente acoplado ao seu contexto oferecendo zero flexibilidade e reuso.

b) No segundo, vejo desenvolvedores não considerar componentes sem comportamento como componentes. Encapsular marcação seria algo não necessário na visão deles. O resultado acaba sendo marcação replicada e, consequentemente, dor no momento em que é necessário fazer mudanças em algo que deveria estar apenas em um único lugar.

Antes de mais nada, acho interessante compartilhar o conceito do que acredito ser um componente. A seguir, algumas sábias palavras escritas por [​Derick Bailey​](https://twitter.com/derickbailey) em um ​[post​](https://derickbailey.com/2015/08/26/building-a-component-based-web-ui-with-modern-javascript-frameworks/) do seu blog:

> "[...] a component in a web application’s UI could be the display panel used to show an employee’s information, such as their name, email address, employee id and more. This component may include buttons to edit the employee or other controls to perform other functions as well. What makes that example a component, in the end, is not just the code that controls it and the UI that represents it on the screen. Rather, it is the encapsulation of this behavior, UI and associated code and configuration, into something that is easily orchestrated into a larger system."

Traduzindo livremente:
“[...] um componente na interface gráfica de uma aplicação web poderia ser um painel usado para exibir algumas informações sobre um funcionário, como nome, email, id, entre outras. Esse componente pode incluir botões para editar as informações do usuário ou demais controles que executam outras funções.

No final das contas, o que faz desse exemplo um componente não é apenas o código que o controla e o visual que o representa na tela. O que o torna um componente é o encapsulamento de seu comportamento, seu visual e qualquer outro código ou configuração em algo que é facilmente orquestrado dentro de um sistema maior.”

Dito isto, vou mostrar agora dois outros benefício além do reuso que a maioria das pessoas podem não se dar conta num primeiro momento:

## Pequenas Responsabilidades
Ao encapsular uma pequena parte da View em um componente independente, você está removendo responsabilidades daquele grande pedaço de código que controlaria toda a View. Imagine, por exemplo, um site exibindo um Weather Card na sua homepage. Na mesma homepage você vê também uma barra mostrando o valor de ações diversas, um logo, um carrossel contendo algumas manchetes, e um outro card exibindo a cotação de algumas moedas em real time.

![Pequenas responsabilidades](https://user-images.githubusercontent.com/4738687/35834748-39799be0-0abe-11e8-89c3-48fb225acc4a.png)

Por quê toda essa homepage deveria ser controlada por um único pedaço de código? Não faz sentido. Quanto mais você concentra responsabilidades, menos você desfruta do poder da flexibilidade.

## Flexibilidade

Agora, suponha que o time de produto tenha decidido mover o Weather Card para uma outra View. Você tem em suas mãos o trabalho de movê-lo de uma View para outra. Moleza, certo?

![Flexibilidade para usar em qualquer lugar](https://user-images.githubusercontent.com/4738687/35684732-f11f2b3e-074e-11e8-8224-5e1661c928d9.png)

Talvez. Depende de como você organizou o código distribuído ao longo da homepage. Se a homepage for controlada por apenas um pedaço de código, você provavelmente vai precisar fazer uma delicada cirurgia nele. Você tem que remover a porção de código relacionada ao Weather Card daqueles grandes arquivos que controlam marcação, estilo e comportamento da homepage. Em seguida, você terá de acomodar exatamente essa mesma porção de código nos arquivos que controlam marcação, estilo e comportamento da outra View.

Concluído, ok? Ainda não.

Os testes da homepage não vão mais passar. Você acabou de mudá-la. O mesmo pode acabar acontecendo com os testes da outra View, uma vez que você também a alterou.

Numa abordagem baseada em componentes, Weather Card é um componente. Ele encapsula toda sua marcação, estilo, comportamento e testes. Então, tudo que você precisa fazer é mover uma simples tag HTML de uma View para a outra.

![Reuso é na verdade consequencia dos dois benefícios](https://user-images.githubusercontent.com/4738687/35834754-3f24ecca-0abe-11e8-9afa-9ea3700eac1b.png)

Como você pode ver, reuso é na verdade uma consequência dos dois benefícios acima. Quando você quebra qualquer View em diversos pequenos pedaços de código (pequenas responsabilidades), você torna tudo mais fácil quando precisa movê-los de um contexto para outro (flexibilidade) ou, consequentemente, reutilizá-los em alguma outra View.

_Curtiu os benefícios que a abordagem baseada em componentes pode trazer para a arquitetura do seu código? Já pratica essa abordagem no dia-a-dia? Se sim, [clique aqui​](https://bit.ly/vagas-contaazul-tableless) e mande um alô. Nós aqui no ​ContaAzul​ queremos conhecer você!_