---
title: Deploy automático com GIT e Netlify
authors: Diego Eis
type: post
publishdate: 2018-03-22
date: 2018-03-11
image: https://i.imgur.com/cVwvHUa.jpg
excerpt: Entendendo como fazer deploy automático no Netlify fazendo push no GIT
categories:
  - git
  - netlify
  - jamstack
  - Tecnologia e Tendências
tags:
  - git
  - netlify
  - jamstack
  - Tecnologia e Tendências
---

A ideia de passar o Tableless para uma JamStack, era simplificar o processo de manutenção e ainda diminuir a complexidade de toda a stack que envolvia o site. Uma coisa que facilitou bastante foi o deploy. Atualmente nós estamos hospedados no [Netlify](https://www.netlify.com) e todo o código fica no GIT, usando o Github como casa permanente.

## Introdução rápida sobre o Netlify
O [Netlify](https://www.netlify.com) é um serviço para hospedar sistemas que tem sua stack baseada em tecnologias front-end, que basicamente não precisam de banco de dados ou linguagens back-end para funcionar. Além disso, complexidades como chave SSL, CDN, a hospedagem em si, testes A/B, autenticação com OAuth, JWT e até formulários podem ser gerenciados pelo Netlify.

> Netlify is a unified platform that automates your code to create high-performant, easily maintainable sites and web apps.

Sistemas baseados em React, Angular e etc são ótimos candidatos para ficarem lá. Lembre-se que uma das ideias chave de um projeto baseado na ideia de JamStack, é que você separa o front-end do back-end, e o back-end basicamente fica responsável por servir APIs, logo, as APIs devem ficar em outro servidor próprio pra isso. O Netlify nesse caso, irá só hospedar a parte front-end da coisa.

O Netlify é grátis. Você só precisa se [cadastrar](https://netlify.com/) e correr pro abraço. Contudo, na versão paga você tem algumas outras regalias. Mas para quem tem projetos pequenos, é uma mão na roda. Grande parte dos meus projetos estão lá, inclusive o Tableless.

## Como faço o deploy automático do Tableless usando GIT e Netlify

Atualmente o Tableless faz um build agendado automático todos os dias às 6 horas da manha. Eu uso um agendamento do [IFTTT](https://ifttt.com/), que manda um webhook para meu Netlify, que ativa um deploy automático. Aí o Netlify faz o build do Hugo (Gerador de código estático que uso para o Tableless) e se tiver algum artigo agendado, por exemplo ele é publicado depois do build. Mas essa é uma história para outros post.
  
Basicamente, sempre que acontece um push na [branch master do repositório do Tableless](https://github.com/tableless/tableless), o site é buildado e as atualizações vão pro ar.

Como isso é feito? Simples. 

### 1. Insira seu site do GIT para o Netlify
Primeiro você precisa liga o seu Netlify no seu repositório. No caso nós usamos GitHub. Depois de logado na conta da Netlify, clique no botão "New site from GIT".

![](https://i.imgur.com/FXLPrzW.png)

Clicando nesse botão, você é redirecionado para o primeiro passo, que é integrar o repositório do seu projeto no Netlify. No nosso caso, Github.

![](https://i.imgur.com/rHHKby7.png)

Você encontra e clica no seu projeto na lista:

![](https://i.imgur.com/V3hH3Qb.png)

E no próximo passo você vai escolher qual a branch que o Netlify vai vigiar para fazer os deploys. Além disso, você vai definir o comando que o Netlify deve executar para fazer o build do seu projeto. No nosso caso, como usamos Hugo, o comando que eu rodo é `hugo -d`.

O próximo campo é para definir qual é o nome da pasta de publicação. Geralmente em projetos "estáticos", existe uma pasta que é a pasta do projeto "funcionando". Normalmente o nome padrão é `dist` ou `public` ou o nome que você e seu time escolherem.

Se caso seu projeto depender de variáveis de ambiente, nesse ponto você também pode definir as variáveis de ambiente necessárias para seu projeto funcionar.

![](https://i.imgur.com/quk38lV.png)

Feito isso, você pode clicar no botão de DEPLOY que o Netlify vai fazer o resto.

![](https://i.imgur.com/vPDZ6ih.png)

Agora, toda a vez que houver um deploy na branch escolhida, o Netlify vai fazer o build do sistema e publicar na pasta destino.

Enquanto você não define um domínio definitivo para o seu projeto, o Netlify mantém um domínio temporário, tipo [https://tableless.netlify.com/](https://tableless.netlify.com/). Pense nos seus freelas... Você pode usar esse domínio para mostrar os resultados para o cliente.

![](https://i.imgur.com/vjZ0y3v.gif)

Lá no Git do Tableless, sempre que há uma aprovação de Pull Request, o código novo vai para a Master, que por sua vez vai para produção depois do Build do Netlify.

## Contextos de Deploys

Para você não ficar fazendo testes em produção, o Netlify tem uma feature muito interessante que se chama "Deploy Contexts". Essa feature permite que você diga para o Netlify como fazer o build do seu site, permitindo que você configure o build o site dependendo do contexto que ele deve ser deplorado.

Existem 3 contextos já predefinidos pelo Netlify:
- **production**: esse contexto corresponde ao deploy principal do site. Lembra que no início você define uma branch para fazer o deploy? Pois é... Essa branch é a que vai para produção, no seu domínio padrão ou no domínio `nomedosite.netlify.com`
- **deploy-preview**: Esse contexto é onde a Netlify faz build do projeto baseado nas integrações definidas de Pull Requests e Merge Requests. Nesse caso, o Netlify faz o deploy numa URL com o prefixo `deploy-preview`, seguido pelo identificador do Merge Request ou Pull Request. Exemplo: um pull request com o ID de #50 terá seu deploy-preview na url `deploy-preview-50--nomedosite.netlify.com`.
- **branch-deploy**: Corresponde ao deploys de branch específicas, que não tem a ver com a sua branch de produção. Branch-deploy ficam disponíveis em URLs específicas com o nome da branch, exemplo: se a branch se chama `feature123`, isso será deployado na URL `feature123-nomedosite.netlify.com`.

![](https://i.imgur.com/2xt45nZ.png)

A [documentação deles é bem simples de entender](https://www.netlify.com/docs/continuous-deployment/#deploy-contexts) e explica como você pode configurar isso nas configurações de build do seu projeto.

## Conclusão

O Netlify é uma daquelas ferramentas que você não pode viver sem. Para quem é freelancer e quer mostrar seus projetos baseados em front-end, vai fundo, o Netlify é o que você precisa. 

