---
title: "Agora o Tableless é estático"
categories: ["Artigos"]
excerpt: Tableless não é mais no WordPress.
image: http://i.imgur.com/bvQOlPV.png
type: "post"
author: Diego Eis
date: "2017-04-11T21:59:58-03:00"
---

Eu não sei se você já tentou cuidar de um site durante algum tempo, mas fica a dica: dá trabalho. Aqui no Tableless temos 3 servidores na DigitalOcean: um pro Fórum rodando Discourse, um pro WordPress rodando Nginx + PHP e finalmente um para o banco MySQL. Antes estava tudo em um servidor só, mas dava muita dor de cabeça com instabilidades, upgrades, configurações de infra etc. Logo decidi separar um servidor apenas para o [Fórum](http://forum.tableless.com.br/). Assim, quando eu tivesse que atualizar o fórum ou fazer qualquer coisa arriscada por lá, o blog ficaria intacto e vice-versa. Com isso, uma parte do problema foi resolvido. Sobrou o WordPress.

## WordPress
Eu AMO o WordPress. Embora muita gente não goste, o WordPress é uma ferramenta fenomenal que resolve um caminhão de problemas quando se trata de criar websites e qualquer outra coisa que dependa de um CMS. Ele é flexível, tem uma comunidade gigante, com soluções para qualquer tipo de problema: basta fazer uma pergunta no Google e pronto, você encontra a resposta. A coisa ruim é que dependendo do site, o WordPress fica carente. Você precisa dar bastante atenção para suas atualizações, performance, configurações e tudo mais. Como ele é praticamente onipresente na web, é alvo de ataques constantes...

Sobre a performance, você precisa passar um tempo tunando aqui e ali para ele ficar satisfatório. Não é só escolher um plugin de cache e pronto... O bom é conseguir tunar tudo o que você puder antes de partir para uma solução desesperada. Depois de algum tempo estudando e levando porrada, você passa a conhecer os meandros do WP e acaba fazendo um bom trabalho. Mas querendo ou não, você precisa de um setup básico: um servidor rodando PHP e MySQL.

## Custo
Como eu disse, aqui no Tableless, só para o Blog, tínhamos 2 servidores, um de USD$20 para o WP e outro de USD$5 para o MySQL. Isso dá uns USD$25 por mês, que dá algo em torno de R$945 por ano. Com o fórum a conta fecha em mais ou menos R$1700 por ano, só de servidor para manter o Tableless. Não, não há ajuda financeira de nenhuma empresa e eu tento compensar parte desse valor com o AdSense e com publieditoriais (posts pagos), banners e etc. No final saio no prejuízo, porque não gasto só com servidor (durante um tempão paguei do bolso algumas pessoas para escreverem para o site, além de designers para fazerem o layout, brindes etc). Logo, um dos objetivos, além de diminuir o trabalho de manutenção, é também diminuir os custos.


## Mudança
Cansado de tanto trabalho e tanto dinheiro indo embora, faz bastante tempo que tenho pensado em passar a usar um gerador de sites estáticos para manter o Tableless. Eu gosto muito de Middleman ([meu blog pessoal](http://diegoeis.com/) é baseado e Middleman, assim como todos os meus projetos de clientes) e então eu comecei a fazer testes com ele. Gostei bastante dos resultados e percebi que migrar do WordPress para algum gerador de site estático era uma possibilidade real. Mas por causa da correria da vida, eu adiei um tempão... Até hoje.

Estava fofocando esses dias com o [PotHix](http://pothix.com/) e ele me disse que havia migrado o blog dele de Middleman para um gerador estático chamado Hugo. Foi aí que eu resolvi tentar matar todo esse processo em três domingos. O resultado, é esse site que vocês estão vendo.

Um dos problemas que me fazia adiar essa mudança, era pensar numa solução para busca. Existem várias iniciativas para buscas de conteúdo em sites estáticos por aí. No site do Hugo mesmo há uma série de sugestões, mas como eu queria algo sem muito guéri-guéri, resolvi da maneira mais simples possível: coloquei o [DuckDuckGo Search Box](https://duckduckgo.com/search_box). Simples e fácil. Depois posso pensar em fazer um trabalho mais bem acabado, usando alguma solução mais apropriada e principalmente mais customizável. Mas por enquanto o Duck valente dá conta do recado.

## Hugo
O Hugo é um sistema gerador de arquivos estáticos desenvolvido com a linguagem Go. Não tenha medo, você não precisa saber Go para experimentar. O setup é muito, mas muito simples e em poucos minutos você já está testando o Hugo na sua máquina. Como é bastante diferente do Middleman, eu tive algumas dificuldades para me acostumar com a montagem do template, mas não foi nada aterrorizador, pelo contrário, o Hugo já tem algumas facilidades e as customizações são bem simples de se fazer via config.

Eu não tenho a pretensão de mostrar agora como o Hugo funciona, isso fica para o próximo post. Mas se você se interessar, aqui está o [site oficial](https://gohugo.io/). Taca-lhe pau.

Mas porque não Middleman? Embora eu tenha uma facilidade maior com Middleman por conhece-lo há mais tempo, o Hugo tem algumas facilidades interessantes, por exemplo:

- Migração é bico. Quando eu procurei um migrador de WP para Middleman, não encontrei nenhum migrador decente que funcionasse. O migrador do Hugo funcionou de primeira.
- A geração de estáticos é muito mais rápido que o Middleman. O Tableless tem mais de 1650 posts. Gerar o estático disso tudo leva menos de 2 segundos no Hugo.
- Boa [gestão de permalinks](https://gohugo.io/extras/permalinks/)
- Suporta vários tipos de frontmatters: json, toml e yaml
- A forma de templating usando Sections, Archetypes e Types é bastante interessante (embora eu tenha demorado para entender o conceito)
- O esquema de oganização e gestão de [Taxonomias](https://gohugo.io/taxonomies/overview/) também é bem legal
- Suporta [Syntax Hightlighting](http://gohugo.io/extras/highlighting/) nativamente
- E tem um monte de [extras](https://gohugo.io/extras/) que talvez eu nem precise usar

## Tableless está mais opensource do que nunca
O código do Tableless em Wordpress já estava todo [aberto no GitHub](http://github.com/tableless/tableless), assim como essa versão estática, usando Hugo, também está [aberta aqui](http://github.com/tableless/tableless-static) caso alguém queira ajudar.

## Quer ser autor?
Como não temos mais um CMS, você não vai precisar mais se cadastrar para submeter artigos. Para tanto, basta seguir as [instruções dessa página](http://tableless.com.br/seja-um-autor/). Agora tudo vai ser gerido via GitHub. Quer submeter um artigo? Basta abrir um Pull Request com o artigo escrito em Markdown que a gente revisa e aprova. A comunidade também poderá participar dessa revisão, o que me poupa um trabalho gigante.

Além disso, queria agradecer aos Editores, principalmente ao [Tailo Mateus](http://tailomateus.github.io/) por estar me ajudando nas revisões dos artigos.

## O Design
Quero agradecer o [Daniel Santiago](http://www.danielsantiago.com.br/), um dos designers mais talentosos que eu já conheci, que me deu vários pitacos quando mostrei esse design para ele, além de fazer todo o design mobile do site. Claro, várias coisas eu tive que adaptar por causa do Hugo (por exemplo a Busca), mas acho que no final deu tudo certo. Valeu, [Daniel](http://www.danielsantiago.com.br/)!

Espero que gostem.
