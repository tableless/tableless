---
title: Como criar um time de Dados eficiente dentro da sua organização
authors: Allan Sene
type: post
date: 2017-10-15
excerpt: Como definir seus pilares para tratar Big Data com eficiência, extraindo o máximo de valor de seus dados para aplicação eficiente de Data Science e Business Intelligence nos seus produtos.
categories:
  - Big Data
  - Gestão
tags:
  - Big Data
image: https://cdn-images-1.medium.com/max/2000/1*9CNjZ6CIv9n41vxcXN2Sng.jpeg
---

Certas construções são tão bem feitas que merecem reconhecimento, principalmente
daqueles que estão envolvidos com aquela ciência/arte: Arquitetura, Engenharia,
Música, Computação ou outras. Como qualquer interprete tem orgulho e gosto ao
cantar [Under Pressure](https://www.youtube.com/watch?v=a01QQZyl-_I),
engenheiros/desenvolvedores de software também sentem-se felizes ao utilizarem
aquele *framework* que deixa sua aplicação mais bonita e gostosa de se
desenvolver.

![](https://cdn-images-1.medium.com/max/600/1*QPnc7Am4UR4rlfBRC3ZKuQ.jpeg)
<span class="figcaption_hack">Imagina esses 2 gênios esconderem Under Pressure da gente</span>

[Eu já introduzi a vocês o Incrível
BigQuery](https://medium.com/@allan.sene/destrua-seu-data-warehouse-f362ae6e4460):
solução de armazém de dados do Google, uma das construções de software mais
inteligentes dos últimos anos quando o assunto é Bancos de Dados Distribuídos e
[Motores de
Consulta](https://stackoverflow.com/questions/10458824/whats-the-difference-between-a-database-engine-and-a-query-engine)
e que resolve grandes dores pra quem tem dados massivos para processar.

Mas não é só a estética da ferramenta que conta. Lembrei que construir uma
arquitetura complexa de processamento de dados distribuídos normalmente **sai
bastante caro, **seja em gastos com infra ou com pessoal. De nada adianta ser
uma solução perfeitamente estética e bem construída se ela é **cara, demorada,
difícil** de se implantar e, pior, **longe de resolver os mais importantes
problemas da sua organização.**

## The Data Swamp

![](https://cdn-images-1.medium.com/max/800/1*TV_9rn7D7onzYuiqBlmRzw.jpeg)
<span class="figcaption_hack">Você satisfeitão no seu Data Lake</span>

Na onda do [hype do Big
Data](https://medium.com/tableless/as-verdades-que-o-mercado-brasileiro-e-vocÃª-precisam-ouvir-sobre-big-data-9fb6f8d5b9d3),
muitas organizações estão começando a aplicar o conceito de [Data
Lake](https://www.kdnuggets.com/2015/09/data-lake-vs-data-warehouse-key-differences.html)
em suas operações de tecnologia. Estão se distanciando das ferramentas e
técnicas tradicionais de [Business
Intelligence](https://en.wikipedia.org/wiki/Business_intelligence)*. *Tudo na
ilusão de que trazendo tudo que há de dados desestruturados rolando no negócio
para um repositório único vai *magicamente* trazer *insights* que seus analistas
de dados nunca tiveram antes. E vão surfando nessa onda… até por terem pouca
maturidade, serem pouco
[data-driven](https://techcrunch.com/2017/06/23/five-building-blocks-of-a-data-driven-culture/)*
*intrinsecamente, vão sem perceber que essa onda criada artificialmente na sua
piscina tem todo um aparato *shiny new and disruptive *que é** muito custoso**.

A empresa quer ser **disruptiva**. Quer virar *data-driven, sem se tocar que
isso é uma cultura, quase um hábito*. Olha pra fora e contrata vários
**sabichões** técnicos em Hadoop, famosos queimadores de créditos AWS.

E constrói aquela armadilha gigantesca e começa a colocar de tudo lá dentro:
tabelas de negócio do produto mais importante, logs de acesso da aplicação,
planilhas do pessoal do financeiro, videos do sistema de segurança interno,
registro de ponto em PDF do rapaz que entrega o lanche, **tudo**… **TUDO**… vai
jogando lá…

E é claro que faz sentido… dizem que o [IBM
Watson](https://www.ibm.com/watson/services/discovery/) consegue entender até
que o atraso nas segundas do rapaz do lanche implica numa piora de desempenho da
galera de DevOps que por sua vez interfere na disponibilidade da aplicação,
resultando aumento em 0,5% do *churn rate* e por consequência queda da receita!

> Oh God! Que ferramenta incrível! Vou só montar um Data Lake aqui então…Ué… TUDO
> TA INTERLIGADO! Só basta um “Machine Learning” pra resolver esse negócio não é
não?

Diz aí Fausto: **ERRROOOOUU!!1!**

> E é assim que grande parte dos projetos de Big Data tem surgido: Ferramenta -> Solução -> Problema. Exatamente o inverso do que deveria ser: Problema -> Solução -> Ferramenta

Aqui então vai minha sugestão para o enfrentamento deste cenário de maneira
pragmaticamente correta:

### **Problema:**

Sem Governança dos Dados, sem Curadoria dos Dados, seu Data Lake vai virar um
Data Swamp! Ninguém, *absolutamente ninguém*, vai conseguir pescar nada de lá.
Nem mesmo seu time de Dados vai saber diferenciar bem o que é peixe e o que é
bota na hora que puxar a rede. Não tem documentação que acompanhe a variedade e
volume dos dados. Não tem time suficiente para mastigar tudo para entregar
informações úteis para o negócio. Seu **Data Swamp** não vai passar de um
estorvo gigantesco dentro da sua organização e cedo ou tarde vai ter que ser
limado de lá — junto com os **sabichões** — a fim de otimizar os custos.

### Solução:

Construir algo que **acompanhe os dados de ponta a ponta**, explicando sua
evolução e transformação. Algo que **extraia valor somente do que há de valor**.
A construção do Data Lake deve ser iterativa e **entregar valor a cada
entrega**, assim como já [aprendemos com Desenvolvimento de
Software](https://martinfowler.com/agile.html). Ele também deve ser
**inteligível para todas as áreas de negócio**, deixando de empatar seu time de
dados para que ele atue realmente no que lhe interessa: melhoria contínua do
processo de **aquisição de dados** para** disponibilização de informação**.

## Nossos pilares

Um dos maiores desafios em qualquer empresa que tem crescimento acelerado é
manter todo o time, novo e antigo, focado na **Cultura** e nas **Metas**. Para
Cultura, há métodos de RH e Gestão comumente aplicados que conseguem manter a
**missão** e **visão** da empresa fresca na memória dos colaboradores mais
antigos e bem fixada na mente dos colaboradores novos.

> Para **Metas**, o desafio já ultrapassa o RH, com treinamentos e ações de
> ambientação e até cultura data-driven: Vontade e Gestão Eficiente não basta.
> É necessária a **Democratização dos Dados** para a facilitar a Tomada de
> Decisão.

É isso que tem guiado todas decisões de arquitetura do time de Dados da
[MaxMilhas](https://www.maxmilhas.com.br/quemsomos). Ter poucos "*consultores"*
independentes, que monopolizam o entendimento dos dados de negócio da empresa
não é saudável e muito menos contribuem para o crescimento da organização como
um todo.

Sendo assim, levantamos como requisitos de uma **Arquitetura Democrática de
Dados**:

* **Inteligibilidade: **Toda área deve ser capaz de **ver e entender** os dados
que lhes interessam sem necessidade de *consultoria *especial do time de Dados a
todo momento.
* **Integrabilidade: **Todas fontes de dados devem ser **mutuamente integráveis**,
de forma que partes do negócio não se isolem, deixando de entregar valor para
toda a organização.
* **Rastreabilidade: **Todos dados devem ser **rastreáveis e acompanhados de ponta
a ponta**, de forma que, ao menos o time de Dados, seja **Autoridade** sobre as
fontes, suas transformações e disponibilização final, sejam brutos ou em
*insights.*
* **Escalabilidade: **Toda a arquitetura de dados deve ser construída de forma a
**suportar o crescimento exponencial** da empresa, evitando gargalos e erros ao
prover informação de valor para os decisores.
* **Confiança:** Toda a arquitetura de dados deve prover **confiança total dos
dados que disponibiliza**. Isso implica em dados idealmente sem erros, sem
atraso e sem perdas.

> Entender nossos clientes, TODOS eles, com Dados, e CADA UM deles, com UX/Design,
> é essencial para guiar todo rumo do negócio de nossa empresa.

Tais pilares nos guiam para as escolhas de arquitetura corporativa e também de
nosso produto. São esses pilares inclusive alguns dos motivos de **nosso time de
Dados ser uma célula dentro de nosso time de Produto ***— buscando sempre o
*[conceito de Data-Driven Product](https://blog.intercom.com/sharing-the-power-of-data-through-partnerships-and-storytelling/)* contando com profissionais de qualidade, design, engenharia e desenvolvimento.