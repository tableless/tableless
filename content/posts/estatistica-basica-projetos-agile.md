---
date: "2017-05-01T20:55:20-03:00"
title: "Estatística básica nas entregas de projetos agile — Moda, mediana e percentil"
categories:
  - Agile e Gestão
  - Artigos
excerpt: "Como um pouco de estatística básica pode nos ajudar a entender melhor as entregas de projetos web"
image: http://imgh.us/pexels-photo-147408.jpeg
type: "post"
author: "Diego Eis"
---

Cada uma das metodologias de gestão de projetos tem suas próprias
características de funcionamento e essência. Mas todas elas tentam responder uma
grande pergunta que virou clichê faz milhares de anos: **quando o projeto será
entregue?**

A graça das metodologias ágeis é que você trabalha em cima de transparência,
incluindo o usuário e os stakeholders no processo, permitindo mudanças de planos
no meio do caminho, apressando as falhas e tentando entregar incrementos de
valor ao final de cada ciclo. Tudo isso serve para gerenciar as expectativas e
fazer as informações do projeto fluirem. Aproximando os stakeholders e os
clientes, eles ganham visibilidade do status do projeto, diminuindo a ansiedade
sobre quando o projeto vai ser entregue. Mesmo que as expectativas estejam bem
gerenciadas, saber o dia de entrega do projeto é importante para o planejamento
do produto, é uma questão estratégica para a empresa.

Para ajudar nessa tarefa, existem uma série de métricas já bem conhecidas que
monitoram a saúde do processo de desenvolvimento. Alguns deles você já conhece
como o CFD, Lead Time, Cycle Time etc. Contudo, essas métricas por si só,
mostram o cenário presente do projeto. Elas são importantes, porque mostram se
você está no caminho certo ou errado. Mas não basta apenas saber que estamos no
caminho correto, é muito mais inteligente enxergarmos parte do caminho que
iremos trilhar afim de prevermos nossas entregas e consequentemente termos um
vislumbre de quando o projeto irá de fato terminar.

A ideia desse artigo não é abordar as [previsões
probabilísticas](http://blog.kudoos.com.br/lean/previsao-probabilistica/) de
projetos (que é um assunto muito mais profissa), mas é dar alguma ideia básica
para você que pode estar querendo fazer um pouco mais do que só olhar o CFD do
seu time.

### Consistência e tamanho das histórias

O primeiro segredo para prever o futuro das entregas em um projeto é ter
consistência. O time precisa ter uma frequência de entrega consistente. Isso não
é algo fácil de se conseguir, pois o processo de desenvolvimento não é linear,
pelo contrário: imprevistos acontecem, pessoas ficam doentes, o caso do bus
factor, ambientes de desenvolvimento quebram, o mercado muda… Tudo isso faz com
que o desenvolvimento de software seja um lugar
[complexo](https://medium.com/gestao-produtos/management-3-0-primeiras-pÃ¡ginas-5fbf082ddf74#.l3caqqirt)
de se trabalhar. Para tentar diminuir as incertezas, nós precisamos entregar
tarefas sempre do mesmo tamanho e você sabe que isso é algo difícil de se fazer.
Não quero falar aqui sobre metodologias de estimativa, porque não importa qual
metodologia você usa, o que importa é que no final você e seu time tenham
histórias do mesmo tamanho e que sejam claras para todo mundo.

Essa coisa de histórias **pequenas, médias e grandes** não existe. Você precisa
que todas as histórias tenham de preferência, o menor tamanho possível, mas que
continuem entregando valor para o usuário. A ideia é que seu backlog seja
recheado de tarefas mais ou menos do mesmo tamanho, possibilitando sua entrega
dentro do ciclo (sprint ou semana). Como você vai saber qual o tamanho ideal das
tarefas do seu time? Experimentando. Aqui não tem segredo nenhum, é só medir e
comparar com o passado. Pegue os outliers (tarefas que demoraram muito mais
tempo para fazer do que as outras) e descubra o que aconteceu e tente se
certificar de que isso não aconteça mais. Existem cerimônias para facilitar o
processo como o Incepction, Refinement, Plannings etc…

Uma das maneiras de validar que a frequencia de entrega do seu time é
consistente, você pode usar o Throughput. O **Throughput** tem uma série de
definições por aí, principalmente no mundo Agile, mas para mim e para algumas
empresas de tecnologia **throughput é a quantidade de histórias (user story)
entregues na semana**. Se seu time consegue quebrar bem as histórias, de forma
que elas entreguem valor e sejam pequenas o bastante para serem entregues sem
ultrapassar o ciclo, vocês conseguiram dar o primeiro passo para prever o
futuro. Veja um exemplo:

![](https://cdn-images-1.medium.com/max/2000/1*B-bROvrbGKp8E3i7wsIStQ.png)
<span class="figcaption_hack">Throughput vs Semana</span>

Esse é o gráfico de um time de produto real. Os valores são das últimas semanas
de 2016. Veja que a partir da semana 39 até a semana 47 as entregas eram
realmente desproporcionais. Depois de uma ou duas reuniões, descobrimos que um
dos motivos era que estávamos quebrando muito mau as histórias. A partir da
semana 48 até a 52, quando começamos a tentar quebrar as histórias no menor
tamanho possível (mas ainda entregando valor para o cliente), retirando as
incertezas nos Refinamentos e Plannings, percebemos uma melhora gigante nas
entregas. Perceba que mesmo assim há uma diferença da quantidade de entregas nas
últimas semanas (48 à 52), mas nós já tínhamos certeza de que o motivo não era o
tamanho das tarefas, mas com problemas de infraestrutura, feriados etc.

> Se seu time consegue quebrar bem as histórias, de forma que elas entreguem valor
> e sejam pequenas o bastante para serem entregues sem ultrapassar o ciclo, vocês
conseguiram dar o primeiro passo para prever o futuro

Conheça o Throughput do seu time. Marque a quantidade de entregas numa planilha
e faça um gráfico. Perceba no gráfico que a média de entregas são 9 histórias
por semana. Embora a média seja 9, na semana 41 o time entregou 14 histórias…
Mas na semana seguinte, eles entregaram apenas 1. Isso não é consistência. A
partir da semana 48 a coisa toda começou a melhorar e nós podíamos ter um pouco
mais de certeza do número de entrega que iríamos executar. Mesmo assim, há um
problema nesse gráfico: a média. É aí que entra a estatística básica.

### **Estatística descritiva básica**

A média é interessante, mas não pode ser usada sozinha para dar a resposta de
quanto o time entrega semanalmente. Isso não quer dizer que você vai deixar de
usar médias nos seus cálculos, pelo contrário. Mas então o que podemos fazer
para ter uma resposta melhor? Vamos usar algumas técnicas básicas da estatística
descritiva. A estatística descritiva é a parte da estatística responsável por
apontar tendências de comportamento e descrever conjuntos de dados. Fazem parte
da estatística descritiva as medidas de tendência central ou medidas de posição
como a **média aritmética**, **moda**, **mediana** e **percentil**. Há também as
**medidas de dispersão**, que envolvem o desvio padrão, variância e outros… que
também são úteis para descobrir insights sobre as entregas do seu time, mas não
vamos ver isso nesse artigo.

#### **Moda**

A **moda** é o número que aparece mais vezes em uma distribuição de dados.
Imagine os dados de entrega de um time fictício:

O número que aparece mais vezes na coluna de entregas é o um. Isso quer dizer
que **na maior parte das semanas esse time entregava apenas uma tarefa**.
Terrível. Quanto maior esse número, melhor. Se a "moda" do seu time aumentar,
quer dizer que frequentemente ele tem entregue uma mesma quantidade de tarefas.
Mas isso ainda não diz que o número de entregas são constantes.


*Quero deixar apenas uma observação*: a distribuição de dados que eu estou usando
é bastante pequena, mas vai servir para o nosso exemplo. Quanto mais dados
históricos você tiver, melhor. **Contudo,** **se houver alguma mudança drástica
no modo com que seu time entrega as tarefas, por exemplo, começar a fazer o
deploy das tarefas de forma automatizada, você deve levar em consideração essa
mudança nas suas análises.**


#### **Mediana**

A mediana é a irmã mais sensata da média. Ela não é influenciada pelos valores
extremos e por isso pode trazer uma resposta muito mais consistente sobre uma
distribuição de valores: a mediana é o número que divide uma distribuição de
dados exatamente no meio.

Imagine que durante 10 semanas, seu time teve os seguintes throughputs semanais:
2, 2, 4, 2, 5, 3, 3, 5, 4. Se você somar todos esses números de entregas (dá 30)
e dividir pela quantidade de semanas (que é 10) a média de entregas do time será
de 3.3 tarefas por semana. Mas imagine que em uma semana atípica, o time
entregou 30 tarefas porque você deu RedBull pra todo mundo. A média, nesse caso,
seria puxada para cima, virando 6 entregas por semana. E aqui está o problema:
por causa de uma única semana, você obteve um cenário totalmente falso sobre a
capacidade de entregas do seu time.

A **mediana**, por sua vez, não seria influenciada por essa semana atípica. A
mediana nesse caso é 3.5, um valor muito próximo da média sem contar com as
entregas da semana atípica.** **No nosso exemplo a média sem a semana atípico
era de 3.3 e a nossa mediana é de 3.5, o que nos leva à conclusão que **para
distribuições sem valores extremos, a média e a mediana são sempre
semelhantes.**

Usar média não é errado e só usar a mediana não quer dizer que você está sempre
certo. O segredo é **saber qual medida do meio usar em cada situação**. Eu
sugiro que você evite usar apenas uma das medidas do meio. Eu sempre deixo à mão
nas minhas planilhas as duas medidas.

#### Percentis

Como disse, a **mediana define o meio de uma distribuição.** Logo, podemos
dividir uma distribuição de dados em quatro partes iguais, chamados de
**quartis**. O primeiro quartil consiste em 25% das distribuições inferiores. O
segundo quartil consiste nos 25% seguintes da distribuição e assim por diante.
Nós podemos dividir a distribuição em centésimos ou como é comumente chamada de
percentis, onde cada percentil representa 1% da distribuição. **A vantagem do
percentil é que ele mostra onde uma observação particular pode se encontrar em
comparação à todo o restante**.

Não se preocupe com as fórmulas. Você pode confiar nas fórmulas do Google Sheets
ou do Excel. Eu confirmei os números desse artigo Google Sheets. Logo, é só ter
uma distribuição em qualquer programa de planilha do seu gosto, escrever , fica
algo assim:  para descobrir o primeiro quarto do percentil, que é o que ocorre
em 75% do tempo do seu time.

Dado a tabela acima, que mostra as distribuições das entregas do time fictício,
conseguimos separar os percentis. Ficou algo assim:

* **Percentil de 25% é igual a 3.8:** o que significa que em 75% do tempo o nosso
time entrega 3.8 (4, se for arredondar) tarefas por semana ou menos;
* **Percentil 50% é igual a 6.5:** significando que em 50% das semanas, o time
entrega 6.5 histórias ou menos;
* **Percentil dos 75% é 12:** que significa que em 25% das semanas, o time entrega
12 histórias ou mais e que em 75% das semanas, o time entrega menos do que 12
histórias.

### Concluindo

Trabalhar com Agile quer dizer que você precisa aprender com o passado. Todo
aquela história Empirical Process que as metodologias ágeis pregam
(principalmente o Scrum), só fizeram sentido pra mim quando eu vi as mudanças se
refletindo nos números.

> Os números ajudam o time a alcançar a frequência consistente de entregas, que é
> o segredo para iniciar a previsibilidade de entrega do seu projeto.

Geralmente eu uso Jira para recolher esses dados, mas não importa a ferramenta
que você utiliza, desde que você consiga extrair os dados necessários para
conseguir essas respostas.

É claro que esses dados não garantem que o seu usuário estará recebendo valor de
verdade e que as features priorizadas estão realmente fazendo a diferença para o
produto e para o negócio. O trabalho de análise desses dados só fazem sentido se
você tiver feito as lições de casa antes com seu time, trabalhando para que o
produto tenha uma visão clara e que os objetivos do negócio estejam realmente
alinhados com as expectativas de todos.

Para se aprofundar e ler mais:

* [Agile](https://medium.com/tag/agile?source=post)
* [Gestao De Projetos](https://medium.com/tag/gestao-de-projetos?source=post)
* [Scrum](https://medium.com/tag/scrum?source=post)
* [Kanban](https://medium.com/tag/kanban?source=post)
* [Statistics](https://medium.com/tag/statistics?source=post)

### [Diego Eis](https://medium.com/@diegoeis)

Trabalha como gestor de produtos maravilhosos para web. É Scrum Master,
Adventista, palestrante e metido a besta.
[http://diegoeis.com/](http://diegoeis.com/)

### [Gestão de Produtos](https://medium.com/gestao-produtos?source=footer_card)

Canal de dedicado à artigos sobre gestão de produtos web. Gestores de diversas
empresas brasileiras se juntaram para escrever sobre como eles gerem seus
produtos e empresas.

Ótimo texto Diego.

Escrevi algo sobre o assunto e que talvez possa servir como complemento:

