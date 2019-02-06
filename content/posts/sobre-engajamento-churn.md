---
title: Sobre engajamento e churn
authors: Diego Eis
type: post
date: 2019-02-11
publishdate: 2019-02-11
excerpt: Você trabalha em algum Produto Digital com assinatura? Então já ouviu falar de uma métrica chamada churn.
image: https://i.imgur.com/e1ETOhO.jpg
categories:
  - Gestão
  - Produtos Digitais
tags:
  - Product Management
---

Churn é uma métrica tão comum no mundo dos produtos digitais que ao usá-la, nós nem paramos para pensar direito nas suas variações. 

## O que é churn? Não responda rápido.

Fácil, né?! Churn seria a quantidade de usuários que deixam de ser clientes do produto num determinado período de tempo. Você pega a quantidade de clientes que cancelou seu produto no mês e divide pelo total de clientes na base no último dia do mês... pronto, você tem a porcentagem de churn do seu produto.

Essa resposta vale muito bem para produtos SaaS, onde clientes pagam para continuar usando o serviço. Aí fica fácil medir: se o cliente deixar de pagar a mensalidade, deixando assim de ser oficialmente seu cliente, logo, ele vira churn.

Até aqui eu acho que todo mundo fica na mesma página. Mas e se seu produto é um produto freemium, onde você pode usá-lo de forma limitada, sem pagar mensalidade, como é o churn é calculado? Ou, como no exemplo da Easynvest, onde o usuário entra no produto, investe, e depois não investe mais, mas continua usando o produto frequentemente para acompanhar seus investimentos?

Eu acho que podemos dizer que o churn é muito mais do que o turnover de usuários de um produto, certo? Há vários cenários onde você, como Product Manager, juntamente com outras equipes (stakeholders, atendimento
- marketing) podem definir quando tratar um usuário como churn.

Nós podemos considerar níveis de churn a partir do momento que o usuário deixa de fazer determinadas ações no seu produto. Tarefas essas que trazem valor para a empresa, tanto de receita quanto de engajamento (tarefas que levem o usuário a usar com mais recorrência seu produto).

Logo, para mim, o churn não pode ser atrelado a simplesmente geração de receita. Existem estágios anteriores que podemos considerar como churn.

## E como nós definimos esses estágios de churn?

Só existe churn porque o usuário para de engajar de alguma forma com seu produto. Nós temos uma série de métricas que mostram o quanto seu produto está badalado. Duas métricas comuns são o DAU (Daily Active Users) e o MAU (Monthly Active Users), que quase todo mundo usa para indicar a quantidade de clientes ativos no dia/mês. Um cliente entra nessas duas métricas quando ele executa qualquer tipo de interação no produto. É normal que as empresas contabilizem o cliente nessas métricas a partir do login do usuário. O racional é: se o usuário fez login no seu produto, ele deve ter usado seu produto, logo, ele é um usuário ativo no sistema.

> Churn não pode estar ligado simplesmente à geração de receita. Você pode e deve definir estágios anteriores de churn e engajamento.

Embora essas duas métricas sejam bem legais para termos uma visão ampla do fluxo de ações dos usuários, elas não são boas métricas para definir se um usuário pode ser churn ou se ele está engajado. O usuário pode simplesmente se logar uma vez por mês, não executar nenhuma outra ação, e você vai contá-lo como um usuário ativo. Contudo, esse usuário não está efetivamente usando seu produto.

> While big numbers are a nice signal of, well, big numbers, I don't think they are an indicator at all for whether a product is really working. - Josh Elman, [The only metric that matters](https://medium.com/@joshelman/the-only-metric-that-matters-ab24a585b5ea)

Qual é a tarefa que o usuário precisa executar no seu produto, que pode ser usada como métrica para indicar que os usuários estão realmente usando seu produto?

Logo, o churn não se torna apenas a falta de geração de receita, mas a **falta de engajamento do usuário em determinados goals importantes no produto**. 

Um exemplo: O Josh Elman, que trabalhou em várias empresas, inclusive no Twitter, diz que uma das métricas que eles usavam era que se um usuários visitasse o Twitter pelo menos 7 vezes no mês, era provável que você fosse um cliente que iria continuar visitando o twitter nos próximos meses. Essa era a métrica deles para definir que você, usuário de twitter, estava realmente usando o produto deles. 


## Qual ação do usuário faz ele voltar mais vezes para o seu produto

Embora essa métrica do Josh no Twitter seja boa, uma boa pergunta é: o que faz o usuário voltar a usar o seu produto nos dias posteriores? 

Um exemplo hipotético do Spotify: imagina que você descobre que geralmente, quando os usuários criam uma playlist, eles voltam a usar seu produto mais vezes e por mais tempo que usuários não criam playlists. Ou que é mais frequente que usuários que não compartilham músicas nas redes sociais, deixam de pagar a mensalidade do produto.

O gráfico (usando o Amplitude), fica mais ou menos assim:

![](https://i.imgur.com/pI11wz1.png)

Organizado numa tabela cohort, visualizamos mais ou menos assim:

![](https://i.imgur.com/ADa8wfW.png)

Essa é uma visão das quatro últimas semanas, onde o usuário usou uma determinada feature do produto. Significa que o perto de 25% dos usuários que usaram essa feature, voltaram a usar o produto 2 dias ou mais. Desses, perto de 18,1% voltaram 3 dias ou mais... e assim por diante. 

Qual feature do seu produto faz os usuários voltarem mais? Qual feature do seu produto, faz os usuários usarem outras features? Quais as features do seu produto que **geram retenção de usuários**?

## Definindo o que realmente é um usuário ativo e conclusão

Quando falamos sobre métricas que trazem apenas números em si, estamos falando de métricas de vaidade. Métricas de vaidade são aquelas métricas que fazem a empresa e o time se sentirem melhores. Dizer que seu produto tem um MAU de 5MM, é afagar o ego. Esse número sozinho não quer dizer nada. Você pode ter tido 5MM usuários que não fizeram nada, como vimos anteriormente. A ideia é que nós fujamos dessas métricas que servem apenas para a vaidade do produto. Mas também é uma bobeira dizer que elas são totalmente descartáveis, elas só não são boas quando usadas sozinhas. Nós precisamos ter contexto por trás dessas métricas.

Então, o que precisamos fazer é definir o que realmente é um usuário ativo. Não é só porque o usuário faz login no seu app todos os dias que ele é um usuário ativo, você precisa de algo mais concreto do que isso.

Um usuário ativo, é um usuário que executa os goals do seu produto, fazendo com que ele use seu produto de forma consistente e frequente, consequentemente gerando receita. Além disso, o usuário precisa suprir suas necessidades no produto. Se você souber quais os principais desejos que o usuário quer suprir nas várias fases do seu lifetime no produto, você vai saber quais os goals que indicam se um usuário é ativo ou não.

Uma boa feature, retém o usuário e o estimula a usar seu produto de forma mais consistente e frequente. Aqui tem outra história que pode ser legal para estudar: queremos que o usuário use cada vez mais nossos produtos, mas até onde isso é saudável? Como nós podemos usar a tecnologia e o design para "viciar" o usuário nos nossos produtos? Quais as "armadilhas" os grandes produtos usam para fazer com que os usuários chequem suas timelines a cada 5 minutos? Para aquecer o assunto, leia esses dois artigos: [Estamos viciados em ser infelizes](https://www.papodehomem.com.br/estamos-viciados-em-ser-infelizes) e [How Technology is Hijacking Your Mind — from a Magician and Google Design Ethicist](https://journal.thriveglobal.com/how-technology-hijacks-peoples-minds-from-a-magician-and-google-s-design-ethicist-56d62ef5edf3)


## Para ler mais:
- [The only metric that matters](https://medium.com/@joshelman/the-only-metric-that-matters-ab24a585b5ea)
- [customer success-driven growth](https://sixteenventures.com/active-users-vanity-metric)
- [You’re Measuring Daily Active Users Wrong](https://amplitude.com/blog/2016/01/14/measuring-active-users/)
- [4 Data Drive ways to measure customer experience](https://centricdigital.com/blog/customer-experience/4-data-driven-ways-to-measure-customer-experience/)
- [NPS, Lifetime Value, Churn: Are You Using the Right Customer Retention Metrics?](https://business.linkedin.com/marketing-solutions/blog/best-practices--marketing-metrics/2016/nps-lifetime-vlaue-churn-are-you-using-the-right-customer-retention-metrics)
- [http://grow.kissmetrics.com/webinar-86-recording](http://grow.kissmetrics.com/webinar-86-recording)
- [Success gap](https://sixteenventures.com/success-gap)

