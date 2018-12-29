---
title: Entendendo os três tipos de deploy mais comuns
authors: Breno Panzolini
type: post
date: 2018-12-28
excerpt: Entendendo os tipos de deploy Rolling, Blue-Green e Canary.
categories:
  - Tecnologia e Tendências
tags:
  - Tecnologia e Tendências
image: https://deploy.zenc.io/assets/deploy-cli-logo.png
---

Com o avanço dos microserviços e tecnologias de *CI/CD*, a quantidade de deploys dos nossos serviços aumentaram muito. Há alguns anos atrás os deploys eram feitos em um ritmo muito menor do que atualmente, e por isso ter uma boa estratégia é muito importante para não afetar nenhuma parte do seu sistema.

O objetivo desse post é ser bem sucinto explicando o básico de três estratégias muito utilizadas para deploy e que são simples de se implementar na maioria das ferramentas de orquestração (Kubernetes, Nomad, etc).

# Rolling

Essa estratégia é a mais simples e é a default na maioria dos serviços, basicamente ela consiste em ir subindo os nossos serviços com a nova versão do código, substituindo a versão antiga.

A versão antiga só é "desligada" quando a nova versão está pronta para ser executada, ou seja, em algum momento desse deploy vamos ter N+1 instâncias do mesmo serviço sendo executada.

# Blue-Green

O deploy blue-green consiste em ter dois ambientes idênticos, mais conhecido como *mirror* cujo na frente desses ambientes existe um *load balancer* que permite com que eu direcione o tráfego para o ambiente desejado.

A vantagem desse tipo de deploy é que posso subir minha aplicação em produção e somente a *blue* está recebendo as requisições. Assim que eu terminar todos os meus testes na nova versão (a *green*), basta trocar a chave do load balancer e as novas requisições já irão apontar para a nova versão do código e após isso posso "matar" a minha versão antiga (a *blue*).

Uma das maiores vantagens dessa estratégia é que nosso serviço vai ter praticamente zero de indisponibilidade já que a mudança no load balancer é praticamente instantânea. Outra vantagem é a possibilidade de podermos realizar os nossos testes em produção, antes de liberar o serviço para ser utilizado.

A desvantagem é que por essa estratégia precisar de um *mirror* ela irá consumir mais recursos da sua infraestrutura, e além disso por haver a troca física do switch pelo load balancer a *session* será perdida e por isso o seu código precisa estar preparado para esse tipo de abordagem.

# Canary

Minha opinião pessoal é que essa estratégia é a mais complexa de ser adotada, ela consiste em colocar a nossa versão em produção porém apenas para uma parcela de usuários.

Ou seja, colocamos a nova versão e configuramos para que apenas uma porcentagem de usuários passe por esse novo serviço. Essa configuração na maioria das ferramentas pode ser feita por *feature toggle*, isso significa que podemos liberar por exemplo o novo serviço apenas para usuários do sexo feminino, ou para usuários com mais de 30 anos, etc.

A grande vantagem é que podemos ir testando a nova versão aos poucos em produção com os usuários reais e assim ir acompanhando os logs de erros para ver se tudo está correndo bem.

A grande desvantagem na minha opinião é que se você não tem uma aplicação que tem um grande volume de requisições, a nova versão do seu serviço pode demorar para ser validada pelos usuários
