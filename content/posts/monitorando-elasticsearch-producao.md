---
title: Monitorando o ElasticSearch em Produção
authors: Allan Sene
type: post
date: 2017-10-29
excerpt: Como criar de maneira fácil e rápida um monitoramento abrangente em seu cluster de ElasticSearch de Produção com o open-source Cérebro e com o New Relic.
image: https://cdn-images-1.medium.com/max/2000/1*frALe9YeR5ruLvYxExM3EA.jpeg
categories:
  - elasticsearch
  - back-end
---


Que [o ElasticSearch é uma ferramenta incrível](https://medium.com/tableless/recomendaÃ§Ã£o-de-textos-sem-dor-de-cabeÃ§a-teoria-e-prÃ¡tica-com-elasticsearch-ea91c231146a),
você já deve saber ou ao menos ouvido falar. O não te disseram é que, mesmo com
uma **resiliência** incrível e **elasticidade** que está cravada no nome, o ES,
se não acompanhado de perto, pode criar *vários* problemas. Principalmente
porque normalmente ele é o cara que vai [receber imensas
porradas](https://www.elastic.co/elasticon/2015/sf/arrestful-development-how-netflix-uses-elasticsearch-to-better-understand)
de indexação e deve ser capaz de executar *analytics*/*searches* num piscar de
olhos para se dar o real valor como [Data Store
distribuído](https://en.wikipedia.org/wiki/Distributed_data_store).

![](https://cdn-images-1.medium.com/max/800/1*Wk5VjG-Ezqz_B56TQY3BZg.png)
<span class="figcaption_hack">[Shay: era pra ser um livro de receitas pra esposa…
❤](https://jaxenter.com/elasticsearch-founder-interview-112677.html)</span>

Logo, pra ficar ligado no que ocorre [dentro do seu
cluster](https://www.elastic.co/guide/en/elasticsearch/guide/current/distributed-cluster.html),
sem ter que ficar chamando as
[APIs](https://www.elastic.co/guide/en/elasticsearch/guide/current/_cat_api.html)
— muito úteis em várias situações— você precisa de ferramentas de monitoramento
que lhe dê respostas rápidas e visualizações simples de se entender.

### Por que não usar o Monitoring *(Marvel)*?

![](https://cdn-images-1.medium.com/max/600/1*78Vg5kAYeIdsXj4dWPMGEw.png)
<span class="figcaption_hack">Marvel era um nome tão mais legal :(</span>

O primeiro grande motivo de não sugerir o **Monitoring**, *antigo ***Marvel**,
plugin de monitoramento que [a própria Elastic
disponibiliza](https://www.elastic.co/products/x-pack/monitoring) por meio do
[X-Pack](https://www.elastic.co/products/x-pack), é que ele *completão* **é pago
e caro**. :/

Até tem uma versão *free*, que você consegue com a [licença
básica](https://www.elastic.co/guide/en/x-pack/current/license-management.html),
mas ela é limitada drasticamente após 30 dias. O Marvel utiliza a própria [API
do
Elastic](https://www.elastic.co/guide/en/elasticsearch/guide/current/_cluster_health.html)
para pegar dados do *cluster* e indexa tais retornos no próprio ES, nos índices
`.monitoring`. Estes índices são
[rotacionados](https://www.elastic.co/blog/managing-time-based-indices-efficiently)
de 7 em 7 dias. Então se alguma coisa ocorreu no seu *cluster* há mais de uma
semana, já era...

  $> sudo service elasticsearch stop

O segundo motivo é que, se você já roda um *cluster* de ES em **produção**, vai
ter um trabalho do cão pra instalar o Monitoring. Como ele roda como parte do
X-Pack, é necessário sua [instalação em todos nós do
cluster](https://www.elastic.co/guide/en/x-pack/current/installing-xpack.html)*.
E isso envolve um*** **[fucking full cluster
restart](https://www.elastic.co/guide/en/elasticsearch/reference/5.6/restart-upgrade.html)**!***
*Cara… com 1 nó em produção já é MUITO cagaço fazer isso, imagina com 10 nós com
10Tb de dados e 1bi de docs e 10k indexações por minuto?! Não, você não vai
querer fazer isso!

### Use o Cérebro!

Com esse tanto de [API REST](https://v2.wp-api.org/) supimpa que o ElasticSearch
nos oferece, é claaaro que alguém ia começar a construir um negócio
*open-source* pra galera. Esse projeto é o
[Cérebro](https://github.com/lmenezes/cerebro)! O inexorável [Leonardo
Menezes](https://twitter.com/leonardomenezes) começou por conta própria fazer um
p#$% projeto de **monitoramento** e **administração** do ElasticSearch, [o
antigo Kopf](https://github.com/lmenezes/elasticsearch-kopf). Tudo usando as
facilidades da API do ES e seu profundo conhecimento de JS e
[Scala](https://www.scala-lang.org/)! ❤

## Funcionalidades

No Cérebro temos 2 telas de monitoramento:

* **Overview:** traz dados de **todos **índices e quais nós estes tem
[shards](https://www.elastic.co/guide/en/elasticsearch/reference/5.5/_basic_concepts.html)
e **réplicas** alocadas. Nessa tela você pode fazer [roteamento de
shards](https://www.elastic.co/guide/en/elasticsearch/reference/current/cluster-reroute.html)
com apenas um **fucking clique**:

![Cada quadradinho verde desses é um shard, primário ou réplica.](https://i.imgur.com/7HfMTN0.png)

* **Nodes:** traz as estatísticas de sistema dos nós, como *load*, *cpu*, espaço
em disco e *uptime*:

![](https://i.imgur.com/CVWcneh.png)

Além delas tem a sessão **REST**, que é a mesma coisa do [DevTools do Kibana](https://www.elastic.co/guide/en/kibana/current/console-kibana.html), e **More:** com ferramentas administrativas avançadas como gerenciamento de [snapshots](https://www.elastic.co/guide/en/elasticsearch/reference/5.5/modules-snapshots.html), [aliases](https://www.elastic.co/guide/en/elasticsearch/reference/current/indices-aliases.html), [cluster settings](https://www.elastic.co/guide/en/elasticsearch/reference/current/cluster-update-settings.html)
e etc — [muito cuidado](https://www.youtube.com/watch?v=fqCRtY6j3dc) por aí!

## Instalação

É incrível, não é?! E como instalar esse negócio lindo? Simples demais:

* Baixar [uma versão do Cérebro](https://github.com/lmenezes/cerebro/releases), descompactar e rodar:

```
wget https://github.com/lmenezes/cerebro/releases/download/v0.7.0/cerebro-0.7.0.zip

unzip cerebro-0.7.0.zip .

./cerebro-0.7.0/bin/cerebro
```

* Acessar `https://localhost:9000` e apontar pra algum nó de seu *cluster*, de
preferência um mais sussa, como um nó *master* elegível ou um *client/*[coordinator](https://www.elastic.co/guide/en/elasticsearch/reference/current/modules-node.html) - *`https://meu.no.sussa:9200/`.

Pronto! Seu *cluster* tá lá, intacto, **sem restart nenhum**.

![](https://i.imgur.com/Dp3JSFJ.gif)

Pois é… a gente ainda não tem os gráficos de memória, indexações, buscas e JVM,
muito importantes pra um bom monitoramento. A gente podia coletar isso tudo com
[Logstash](https://www.elastic.co/products/logstash) e visualizar no
[Kibana](https://www.elastic.co/products/kibana), que é o que o Marvel faz, né.
Mas vai dar um traaaampo… :/

### New Relic: uma Relíquia de Monitoramentos

![](https://i.imgur.com/CCn8hyz.jpg)

Agora eu te pergunto: pra quê cê vai se preocupar em coletar seus próprios
*logs* e fazer *dashboards* se alguém já faz isso muito melhor que você?
Duvida?! Ah… então venha ver o [New Relic](https://newrelic.com/): maravilha dos
monitoramentos! [Várias empresas mundialmente
conhecidas](https://newrelic.com/why-new-relic/customers) usam o New Relic para
monitorar seus sistemas, inclusive a
[MaxMilhas](https://www.maxmilhas.com.br/quemsomos).


Ele [tem](https://newrelic.com/synthetics)
[de](https://newrelic.com/mobile-monitoring)
[tudo](https://newrelic.com/alerts)! [Desde tracking transação a transação de
aplicações web e non-web](https://newrelic.com/application-monitoring) (como
sistemas de filas, *crons*…) até [plugins](https://newrelic.com/plugins#plugin)
que qualquer um pode fazer. É aí que resolvemos nosso problema.

## [Plugin do ElasticSearch](https://newrelic.com/plugins/sergey-novikov/299)

No New Relic, temos um plugin que faz o todos os monitoramentos do Marvel e
melhor: com persistência de 3 meses. Além das informações básicas de numero de
requests e total de documentos, ele traz detalhes dos *hosts* como I/O, Memória
e CPU, [Thread
Pool](https://www.elastic.co/guide/en/elasticsearch/reference/current/modules-threadpool.html)
das Requisições de Busca e Indexação, dados do [Heap da
JVM](https://docs.oracle.com/cd/E13150_01/jrockit_jvm/jrockit/geninfo/diagnos/garbage_collect.html)
e mais. Além de poder filtrar por nós, e escolher as faixas temporais dos
gráficos:

![](https://i.imgur.com/RBjyaPE.png)
![](https://i.imgur.com/4W9NpQb.png)

Única coisa que você precisa é do coletor do New Relic rodando em algum lugar
que consegue acessar uma máquina do seu *cluster*, para ele fazer requisições
para as APIs do ES. Sua
[instalação](https://github.com/s12v/newrelic-elasticsearch) é também **muito
simples** e não requer nenhuma ação no *cluster*. Tem um **Docker** que roda
tudo:

```
docker run -e "ES_HOST=<nó_sussa_do_cluster" -e "NEW_RELIC_LICENSE_KEY=<sua_licença>" s12v/newrelic-elasticsearch
```

Obviamente, sugiro que você coloque tanto o coletor do **New Relic** quanto o
**Cérebro** em máquinas separadas do *cluster*: primeiro pra você não ficar no
escuro nas horas do disastres e segundo para não contaminar as métricas.

**Ah… mas o New Relic é pago… :|**

Sim, é. Mas é BEM mais barato que a licença do X-Pack ou do que você construir
tudo na mão, até usando a stack **ELK**. O New Relic tem um [free tier bem
generoso](https://newrelic.com/infrastructure/pricing)*.*

> Antes de sair testando e construindo ferramentas escaláveis, é fundamental que
> você avalie formas de mantê-las, pois com certeza vão crescer algum dia.

Vai sempre ter um ponto de inflexão, onde não há como utilizar só os bons e
velhos `ps | grep`e `top` para gerir sua infra.

Curtiu essa dica? Então compartilhe e recomende esse artigo pros seus colegas.
Quer sugerir um outro assunto? Comente aí embaixo! E não deixe de me seguir para
acompanhar mais paradas legais sobre dados! Abração!

* [Elasticsearch](https://medium.com/tag/elasticsearch?source=post)
* [Monitoring](https://medium.com/tag/monitoring?source=post)
* [DevOps](https://medium.com/tag/devops?source=post)
* [Database](https://medium.com/tag/database?source=post)
* [Big Data](https://medium.com/tag/big-data?source=post)
