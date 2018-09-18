---
title: Padronização, por que não?
authors: Vítor Capretz
type: post
publishdate: 2018-02-05
date: 2018-01-23
image: https://i.imgur.com/txUvq04.jpg
excerpt: Toda escolha é um tradeoff
categories:
  - Mercado
  - Agile
  - Tecnologia e Tendências
  - Artigos
tags:
  - agile
  - Tecnologia e Tendências
  - Mercado
---


"Toda escolha é um tradeoff". Essa foi a frase que mais chamou atenção no
Keynote (apresentação quinzenal que temos aqui no [Pagar.me](https://pagar.me/))
onde decidimos por tirar parte da autonomia dos nossos squads. Sim, você leu
certo, **tiramos** parte da autonomia que tínhamos para gerenciar as tarefas em
cada squad.

Um medo muito grande de qualquer empresa que já foi uma startup é o de adicionar
cada vez mais camadas de burocracia a cada fase de expansão, seja com a entrada
de novos funcionários, com a receita crescendo absurdamente ou com cada vez mais
produtos tendo que ser mantidos. E não é diferente aqui no
[Pagar.me](https://pagar.me/).

A empresa foi criada por
[jovens](https://projetodraft.com/pedro-18-e-henrique-19-criaram-sozinhos-uma-empresa-milionaria-a-pagar-me-e-querem-muito-mais/)
e sempre teve uma cultura que dava bastante autonomia no dia a dia: um novo
produto pode surgir da ideia de alguém que entrou mês passado na empresa, um
processo pode ser tocado independentemente do cargo da pessoa se ela estiver
afim e também mostrar que vale a pena.

No começo de 2017 vimos o quanto estávamos crescendo e o quanto ainda
pretendíamos continuar contratando. Com isso surgiu a necessidade de dividir a
equipe de desenvolvimento em
[squads](https://medium.com/project-management-learnings/spotify-squad-framework-part-i-8f74bcfcd761)*,
*o modelo foi refinado algumas vezes, até que chegamos a um escopo. Os squads
possuíam autonomia para fazer o projeto acontecer da forma considerada mais
adequada, com autonomia para gerenciar tarefas e ferramentas.

*E aí começaram as divergências.*

Com a autonomia para gerenciar tarefas cada squad acabou optando por um processo
diferente, alguns usaram Scrum, outros
[Kanban](https://pt.wikipedia.org/wiki/Kanban). Também foram feitas adaptações
em cima de processos já existentes, retirando reuniões diárias ou fazendo-as
remotamente, por exemplo.

O planejamento do produto também não era algo comum a todos, já que podiam
surgir demandas pontuais e muitos imprevistos.

A ferramenta utilizada para gerenciar as demandas também não foi unânime, já que
temos muitas opções à disposição: usar GitHub ou Trello? Ou ainda o JIRA? Quando
usar o GitHub, gerenciar issues por labels, definir milestones ou um simples
board do
[Projects](https://github.com/blog/2272-introducing-projects-for-organizations)
resolve? Difícil responder.

Percebemos então que era preciso rever essas questões: achávamos que tendo
autonomia poderíamos aumentar a produtividade em larga escala, e deixar cada um
resolver o problema da forma mais adequada a cada situação. Porém não aconteceu
assim, já que podia perder-se muito tempo testando metodologias. A troca de
conhecimento e experiência entre as equipes também foi dificultada, pois a
imersão no produto era grande.

Não ter um certo grau de padronização dificultou muito a possibilidade de
conseguirmos analisar o quão perto dos objetivos de um trimestre o time está,
por exemplo.

## Tradeoff

Começamos então a notar que por termos optado pela autonomia perdemos muito
durante o processo. Porém ainda assim ao pensar em padronizar qualquer coisa, um
calafrio já subia na espinha e trocávamos de assunto: estávamos focando nos
pontos negativos de uma escolha, ao invés de focarmos em tudo que poderia ser
maximizado.

Chegamos no dia do Keynote, quando ouvi que “toda escolha é um tradeoff”.
Percebi aí mais um aprendizado muito valioso para minha vida: ao tomar uma
decisão devemos focar muito mais no lado bom do que no ruim. Depois de analisar
os pontos positivos e negativos, pensarmos em como minimizar os negativos, sem
deixar que eles nos assustem e nos impeçam de tomar uma decisão.

## Processo de padronização

Ao levantarmos essa possibilidade nenhuma decisão chegou *top-down*, quando um
“cargo” mais alto decide tudo e apenas informa os que estão abaixo.

Primeiro foi feita uma pesquisa aberta na qual todos os envolvidos poderiam
opinar quanto ao assunto. O que cada um via de bom? O que achavam que podia
acontecer no pior caso quando uma das decisões fosse tomada? Quais eram as
ferramentas já utilizadas por cada time e o motivo disso?

Com a pesquisa feita e os resultados abertos, continuamos a discutir para
chegarmos a uma decisão final, que foi a de padronizar metodologias e
ferramentas para todos os squads. Nisso incluem-se definições de roadmap
trimestral, nas quais os [Product
Owners](https://www.desenvolvimentoagil.com.br/scrum/product_owner) (ou Business
Leaders, como chamamos no [Pagar.me](https://pagar.me/)) ajudariam bastante.

**E o que ganhamos com isso?**

* Visibilidade: a partir desse ponto fica mais fácil visualizarmos em que ponto
cada um está, comunicar sobre novas features de forma mais organizada,
identificar e melhorar os pontos críticos do desenvolvimento e conseguir avaliar
melhor a performance do time.
* Troca de conhecimento: padronizar não significa deixar de aprender ou evoluir.
Agora fica muito mais fácil o intercâmbio de pessoas entre squads, já que todos
utilizam a mesma metodologia. Além disso, como todas as equipes agora estão
testando o mesmo processo, cada uma delas pode identificar pontos a serem
melhorados em cada caso.
* Ferramentas unificadas: decidimos por utilizar o GitHub Projects e trabalhar com
labels e milestones para acompanhar o status de cada tarefa e de cada objetivo
macro do time.

## O futuro

Hoje em dia a equipe técnica do [Pagar.me](https://pagar.me/) sabe que não se
deve editar um código do core do sistema na máquina de produção. Já vimos todo o
tipo de erro, confusão e problema que isso pode causar, e não vamos deixar que
aconteça de novo. A cultura de pull requests, code review e testes unitários, já
está muito bem instaurada no sangue de todos por lá, e é esse o nosso objetivo
com a padronização de tarefas e processos.

Vamos tentar adaptar onde for necessário, retirar o que não for, trocar
conhecimento e evoluir os modelos. Não vamos descansar até que isso não seja
mais um monstro, que assombra o sonho dos jovens que vêm de um mundo de startup.

Nos vemos em breve!
