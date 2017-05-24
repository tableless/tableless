---
title: Performance do Tableless estático
author: Diego Eis
excerpt: Uma análise simples de velocidade do Tableless depois da mudança para código estático.
type: post
date: 2017-05-23
image: http://imgh.us/pexels-photo-83948.jpeg
categories:
  - Código
  - middleman
  - CSS
  - HTML
  - Técnicas e Práticas
  - hugo
tags:
  - performance
  - middleman
  - jekyll
---

Não faz muito tempo eu decidi [retirar o Wordpress do Tableless e migrá-lo totalmente para o Hugo](https://tableless.com.br/site-tableless-estatico/), que é um gerador de websites estáticos, como o Middleman ou o Jekyll. Dentre todas as vantagens, a mais aparente, sem dúvida, é o aumento de performance de carregamento do site.

Todo mundo sabe [como fazer um site carregar mais rápido](https://browserdiet.com/pt/). Existem diversas dicas, diversas manobras para fazer um site carregar num piscar de olhos, mas nenhuma se compara em ter um site totalmente estático, sem dependencias de banco ou back-end. Para você ter uma ideia do quão rápido ficou o Tableless depois da mudança, veja os gráficos abaixo.

O tempo médio de carregamento da página melhorou em 41%.

![tempo médio de carregamento da página](http://imgh.us/tempo-medio-carregamento-pagina.gif)

O tempo médio de resposta do servidor melhorou em 55.72%.

![Tempo médio de resposta do servidor](http://imgh.us/tempo-medio-resposta-servidor.gif)

Já o tempo médio de download da página, melhorou em 37.8%.

![Tempo médio de download da página](http://imgh.us/tempo-medio-download-pagina.gif)

Não há segredo nenhum: apenas código HTML puro, com o mínimo de CSS, JS e claro, imagens. Estou usando imagens apenas onde realmente é necessário. O uso de JS pesado aqui fica por conta do Disqus, que é um monstro, mas por enquanto é necessário por conta dos comentários.

Não fiz nenhuma mudança no servidor, que é o mais barato da DigitalOcean, com NGINX rodando num Ubuntu.

Fazendo o teste no WebPageTest.org, você pode ver [bons resultados também](https://www.webpagetest.org/result/170524_Q6_4RQ/1/details/#waterfall_view_step1). Veja que um número importante ali é o [Speed Index](http://blog.caelum.com.br/porque-voce-nao-deveria-ligar-para-o-tempo-do-onload-ou-as-metricas-que-importam-para-performance-real-na-web/). O ideal, de acordo com o [Sergio Lopes](https://www.youtube.com/watch?v=EMCBd3kw4zs) é 1000 ou menos. Sem fazer esforço cheguei nos 2400... 

No caso, a página testada foi [https://tableless.com.br/o-basico-sobre-sparql-turtle/](https://tableless.com.br/o-basico-sobre-sparql-turtle/).

Veja abaixo o vídeo de carregamento da página:
<iframe src="https://www.webpagetest.org/video/view.php?id=170524_Q6_4RQ.1.0&embed=1&width=520&height=448" width="520" height="448"></iframe>

[Nesse link](https://www.webpagetest.org/video/compare.php?tests=170524_Q6_4RQ-r:1-c:0) você consegue ver o filme separado em frames como imagens. Perceba que aos 2.5s o site já foi 99% carregado.

![](http://imgh.us/Screen_Shot_2017-05-23_at_23.25.36.png)

Tem coisa para caramba para arrumar ainda, já que o svg do logo e o campo de busca aparecem apenas aos 2.0 segundos. Isso quer dizer que o site fica 2 segundos se aparecer NADA na tela. Já sei que o problema são as malditas fonts... Mas como sou teimoso e gosto dessas fonts, quero manter assim por enquanto.

Mas, o indicador mais importante para performance além de todos os números e os indicadores acima, é a percepção do usuário. Uma pancada de leitores observou que o site ficou muito mais rápido que o antigo. Nesse caso, podemos nos dar ao luxo de não perdermos a cabeça tentando melhorar os indicadores até a perfeição.

Faz muito tempo que tenho indicado para várias pessoas migrarem seus sites para versões estáticas. A maioria dos sites não precisam de um CMS pesado para funcionar. Existem sim, momentos onde o cliente ou a empresa não tem um desenvolvedor para manter um site estático e que ter um CMS significa liberdade e controle de conteúdo e etc. Mas se você for uma empresa cheia de desenvolvedores, a melhor saída é ter um website estático, com um sistema de deploy facilitado para mudanças rápidas.
Se as pessoas realmente precisarem de um CMS para modificar texto, a maioria dos geradores de websites estáticos como Middleman, Hugo e Jekyll (principalmente os dois últimos), já tem plugins que facilitam a edição e manutenção do texto e imagens via interface web.

Aconselho muito estudar qualquer gerador estático disponível no mercado. Todos eles são bem fáceis de aprender e com certeza você vai sentir uma liberdade gigante quando perceber que não depende de nenhuma linguagem back-end, servidor pesado e nem banco de dados.
