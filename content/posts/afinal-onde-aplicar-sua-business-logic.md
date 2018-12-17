+++
authors = "Daniel Archer"
canonical = ""
categories = ["back-end", "publieditorial", "kinghost"]
date = "2018-12-17T08:30:40-02:00"
excerpt = "Para que um código se transforme em valor, ele precisa: fazer algo de especial ou fazer algo que seja interessante para o seu stakeholder"
image = "https://cdn-images-1.medium.com/max/1000/1*pm0JX5PnQp7Rph-rxwWbWA.jpeg"
publishdate = "2018-12-17T00:00:00-02:00"
sponsor = "kinghost"
tags = ["business-logic"]
title = "Afinal onde aplicar sua Business Logic?"
type = "post"

+++
# Entendendo o que é a business logic

Desde que começamos a abraçar a arte de programar, tornar conhecimento em código e esse em valor para uma empresa, procuramos conhecimento e aprendemos novas formas de fazer as mesmas tarefas.

Para que um código se transforme em valor, ele precisa: fazer algo de especial ou fazer algo que seja interessante para o seu _stakeholder._ Seja uma lógica diferenciada, uma regra ou um cálculo. Essas regras **específicas do négocio** são referenciadas usualmente como _business logic_.

### Arquitetura

![](https://cdn-images-1.medium.com/max/800/1*_vQCLACetCQL6wfqtrR85Q.jpeg)

Teremos então que projetar e arquitetar o nosso sistema com diferentes camadas para a _application logic_ e a _business logic_. Na minha área de experiência, web, temos diversas formas de arquitetura. A mais utilizada, mas não única nos dias de hoje é o padrão **MVC** no qual temos layers representando _controllers_, _views_ e _models_. Mas exatamente nesse ponto chegamos a pergunta desse artigo “onde colocar a minha **_business logic_**?”

A resposta para essa pergunta: **não existe definição formal**. Diversos autores e formadores de opinião discutem sobre essa questão há muito tempo. Alguns autores citam como boas práticas, adicionar a lógica na model e deixar a controller responsável apenas pela transição entre a view e a model. Encapsulando assim a lógica da aplicação dentro do modelo.

Um comentário interessante de ressaltar é do Mark Seemann (autor do **Dependency Injection in .NET**) que diz:

> The business layer implements the Domain Model in a boundary-technology-neutral way. In other words, it doesn’t depend on any particular UI or service interface-related technology, such as web libraries or windowing APIs. You should be able to consume the business layer from any type of application — web, rich client, web service, etc.

### Isolando o contexto da aplicação

![](https://cdn-images-1.medium.com/max/800/1*ECEwUpioFP_mGz_E5LOC4A.jpeg)

O termo _boundary-technology-neutral_ aqui é muito interessante. Pois justamente nos dá margem para uma abordagem mais neutra em relação a esse modelo MVC.

Pandas não morrerão se você criar mais entidades além de Controllers, Views e Models. Então podemos adicionar no nosso contexto uma camada exclusiva de negócio. Seguindo esse exemplo:

    app/
        controllers/
        MyCompany/
            Composers/
            Exceptions/
            Models/
            Observers/
            Sanitizers/
            ServiceProviders/
            Services/
            Validators/
        views
        (...)

O importante dessa abordagem é manter suas classes com o menor escopo possível, sempre tendo em vista o conceito de responsabilidade única (**SOLID**) e também com o menor acoplamento possível. De forma que essas classes sejam independentes e possam ser chamadas em qualquer contexto indiferente da interface de comunicação. Seja ela por API, web ou console, com entradas e saídas bem definidas.

### Outras formas de abordagem

É interessante citar também que podemos solucionar essa questão de diversas formas. Afinal não temos certo ou errado em desenvolvimento de software, apenas formas com mais ou menos benefícios.

Pensando nisso, um artigo muito interessante que encontrei foi um defensor para adição da lógica de negócio no banco de dados. Visto que o banco de dados é a base para muitas aplicações e já possui inúmeras otimizações para diversas tarefas, é extremante justo deixa-lo competente de algumas tarefas.

![](https://cdn-images-1.medium.com/max/800/0*fAhz2jKK3l5oWbus.png)

Visando performance e integridade máxima da aplicação, é natural implementarmos algumas _business logic_ através de triggers, procedures e view diretamente no banco de dados.

Como benefício, em projetos distribuídos em diversas plataformas (web, mobile, etc), podemos garantir que essa regra seja replicada de forma transparente para todos os sistemas dependentes desse banco de dados. Além de garantir que a integridade dos dados de forma muito mais eficaz.

O malefício dessa abordagem começa quando temos muitos repositórios de dados e a falta de uma boa documentação dos locais que guardam essa business logic.

### Concluindo

Para finalizar esse artigo, lamento, não posso dar nenhuma resposta definitiva ou uma bala de prata para resolver a questão de design. Mas podemos ver que existem várias opções disponíveis para solucionar esse problema.

Portanto é da responsabilidade da equipe **escolher e documentar** qual a opção escolhida e seguir esses passos em toda a evolução do software. Uma documentação eficiente não significa uma documentação burocrática, mas esse assunto ficará para um próximo artigo.