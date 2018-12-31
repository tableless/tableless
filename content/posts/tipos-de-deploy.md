---
title: Entendendo os três tipos de deploy mais comuns
authors: Breno Panzolini
type: post
date: 2018-12-31
excerpt: Entendendo os tipos de deploy Rolling, Blue-Green e Canary.
categories:
  - Tecnologia e Tendências
tags:
  - Deploy
  - Tecnologia
image: https://deploy.zenc.io/assets/deploy-cli-logo.png
---

Com o avanço dos microserviços e tecnologias de *CI/CD*, a quantidade de deploys dos nossos serviços aumentaram drasticamente. 

Há alguns anos os deploys eram feitos em um ritmo muito menos acelerado do que atualmente, e por isso ter uma boa estratégia é muito importante para não afetar nenhuma parte do seu sistema e principalmente os usuários que o utilizão.

O objetivo desse post é ser bem sucinto, explicando o básico de três estratégias muito utilizadas para deploy e que são simples de se implementar na maioria das ferramentas de orquestração (Kubernetes, Nomad, etc).

# Rolling

Essa estratégia é a mais simples de ser adotada e é a default na maioria dos serviços de orquestração. Resumindo, ela consiste em ir subindo os nossos serviços com a nova versão do código, substituindo a versão antiga.

A versão antiga só é "desligada" quando a nova versão está pronta para ser executada, ou seja, em algum momento dessa estratégia de deploy vamos ter N+1 instâncias do mesmo serviço sendo executada.

![rolling](https://opensource.com/sites/default/files/images/business-uploads/rolling2.gif)

*Fonte: https://opensource.com*

Como podemos notar no exemplo acima, o deploy é feito gradualmente e é importante se atentar que até que ele esteja 100% completo ambas as versões coexistem ao mesmo tempo em produção. Por isso, é importante ficar atento nas mudanças para que nenhum efeito indesejado aconteça.

# Blue-Green

O deploy blue-green consiste em ter dois ambientes idênticos (também chamado de *mirror*), cujo na frente desses ambientes exista um *load balancer* que permita o direcionamento do tráfego para o ambiente desejado.

![blue-green](https://opensource.com/sites/default/files/f1_2.png)

*Fonte: https://opensource.com*

A vantagem dessa estratégia é que posso subir a nova versão da aplicação em produção e somente a versão atual (*blue*) estará recebendo as requisições.

Assim que eu finalizar todos os testes na nova versão (*green*), basta trocar a chave do *load balancer* e as novas requisições já irão apontar para a nova versão do código.

Uma das maiores vantagens dessa estratégia é que nosso serviço vai ter praticamente zero de indisponibilidade, já que a mudança no *load balancer* é praticamente instantânea. Outra vantagem é a possibilidade de poder realizar os testes em produção, antes de liberar o serviço para ser utilizado pelos usuários.

A desvantagem é que por essa estratégia precisar de um *mirror* ela irá consumir mais recursos da sua infraestrutura. Além disso por haver a troca física do switch pelo *load balancer* a *session*, por exemplo, será perdida e por isso o seu código precisa estar preparado para esse tipo de abordagem.

# Canary

Minha opinião pessoal é que essa é estratégia mais complexa de ser adotada. Basicamente ela consiste em colocar a nova versão em produção, porém apenas para uma parcela dos usuários.

![canary](https://opensource.com/sites/default/files/f3_0.png)

*Fonte: https://opensource.com*

Ou seja, colocamos a nova versão e configuramos para que apenas uma porcentagem de usuários passe por esse novo serviço.

Essa configuração na maioria das ferramentas pode ser feita através de *feature toggle*, isso significa que podemos liberar, por exemplo, o novo serviço apenas para usuários do sexo feminino, ou para usuários com mais de 30 anos, etc.

A grande vantagem dessa abordagem é poder ir testando a nova versão aos poucos com usuários reais e acompanhar os logs para ver se tudo está correndo bem, assim liberando a nova versão gradualmente.

A grande desvantagem, na minha opinião, é que se sua aplicação não tem um grande volume de usuários, a validação no ambiente de produção pode demorar mais tempo do que o desejado.

# Conclusão

O objetivo desse artigo foi apenas dar uma leve introdução aos tipos mais comuns de deploy, sem entrar nos detalhes específicos de cada um.

Já adianto que não existe estratégia milagrosa, todas tem vantagens e desvantagems. O importante é que você esteja ciente da que melhor se adequa ao tipo da sua aplicação, custos, infraestrutura, etc.
