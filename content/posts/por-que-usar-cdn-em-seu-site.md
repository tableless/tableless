---
title: Por que você deveria usar uma CDN em seu site
authors: Bill Bordallo
type: post
image: https://i.imgur.com/atYhsVW.jpg
date: 2018-02-05
excerpt: Ter um site veloz pode envolver muitos aspectos. Conheça a CDN e suas vantagens neste artigo.
url: /por-que-usar-cdn-em-seu-site/
categories:
  - Tecnologia e tendências
tags:
  - cdn
  - hospedagem de sites
  - performance

---

Se anos atrás ter um site era uma vantagem competitiva, agora **é preciso muito mais do que isso para se destacar na internet**. Um site precisa garantir uma boa experiência para os usuários, o que inclui, entre outras coisas, uma boa velocidade de carregamento das páginas, mesmo em conexões lentas.

Somado a isso, o desempenho no carregamento de um site também vem sendo considerado como um dos fatores de ranqueamento pelo Google. Ou seja, **otimizar a performance não é mais uma opção, e sim uma obrigação**.

E quando falamos de otimizar o desempenho de um site, existem muitos aspectos a serem considerados. Estes aspectos vão desde um código enxuto até a infraestrutura, como o servidor de hospedagem e a velocidade da rede.  Para quem quer ir além, **existe ainda uma tecnologia que proporciona ganhos extras no desempenho de um site**. Me refiro à **CDN**.

## O que é CDN

A sigla CDN significa _Content Delivery Network_. Em tradução literal seria algo como "rede de entrega de conteúdo" ou "rede de distribuição de conteúdo". Pela tradução já é possível imaginar o que uma CDN faz: **distribui o conteúdo de um site por diversos servidores espalhados ao redor do mundo**.

Você pode estar se perguntando: _– ok, mas qual é o propósito disso?_ O objetivo principal de uma CDN é **entregar conteúdo a partir do servidor mais próximo do usuário final**. Assim, **o tempo de resposta da requisição pode ser bem menor** do que seria em condições normais, quando a resposta vem unicamente do servidor de hospedagem, independente da localização do usuário.

Este princípio, quando combinado com outras tecnologias (cache, por exemplo), **pode fazer um site ganhar muito em desempenho**. Principalmente sites que demandam processamento do servidor, como CMSs e lojas virtuais. Ao utilizar cache e a distribuição de uma CDN, sites WordPress, por exemplo, podem ter um desempenho tão bom quanto o obtido em sites estáticos ([como é o caso do Tableless](https://tableless.com.br/site-tableless-estatico/)). Está certo que um site estático performa muito bem (muito bem mesmo!) quando comparado com um CMS. Mas, dependendo do projeto, o uso de um CMS pode ser indispensável.

## Vantagens de usar uma CDN

Agora que já vimos o que é uma CDN e para que serve, vamos conhecer as vantagens de utilizar uma.

### Redução do tempo de resposta do servidor

Ao acessar uma URL, o browser envia uma requisição para o servidor. Essa requisição percorre um caminho até chegar ao seu destino. Uma vez que o servidor recebe o pedido, há ainda um tempo para que o mesmo seja processado antes do retorno ser finalmente enviado para o usuário. Sites dinâmicos e que dependem de processamento _server-side_ para montagem das páginas podem aumentar bastante o tempo total de resposta do servidor.

**Quando há o uso de uma CDN para cachear o conteúdo, o tempo de processamento da requisição pode ser reduzido consideravelmente**, já que o que será entregue é uma cópia estática do conteúdo solicitado.

Além disso, uma CDN provavelmente tem condições de entregar conteúdo a partir de um servidor mais próximo fisicamente do usuário, o que contribui ainda mais para reduzir o [TTFB](https://blog.apiki.com/2017/07/11/ttfb-time-to-first-byte/) (_time to first byte_, que é o tempo que o cliente leva para receber o primeiro byte) e o envio do conteúdo integral da página.

### Aumento da velocidade de carregamento das páginas

**Uma CDN é muito boa em cachear conteúdo estático.** Imagens, JavaScript e CSS são fortes candidatos a serem armazenados em cache para agilizar a entrega. O próprio HTML pode ser cacheado, dependendo das configurações do serviço. Nestes dois cenários o tempo de entrega dos assets da página é menor do que seria quando apenas o servidor de hospedagem é o responsável por isso.

**O resultado dessa configuração é a redução do tempo total de carregamento das páginas**, já que há [redução no tempo de resposta do servidor](https://developers.google.com/speed/docs/insights/Server?hl=pt-br). Nem sempre é possível cachear todo o conteúdo de um site ou aplicação, mas sempre existem elementos estáticos que podem ser servidos com vantagem a partir de uma CDN.

### Aumento da capacidade de aguentar tráfego

Sites e blogs que passam por picos de acesso, como quando uma postagem viraliza, frequentemente se deparam com quedas ou instabilidades no serviço de hospedagem. É uma situação contraditória, pois você fica na mão justamente no momento em que mais precisa do seu site no ar.

É claro que não existe uma "bala de prata" em cenários como esse: é necessário avaliar a demanda e adequar o serviço de hospedagem. Mas ainda assim **uma CDN pode ajudar, já que grande parte das requisições nem chega ao servidor de origem**.

### Proteção contra invasões e ataques DDoS

Ataques DDoS e tentativas de invasão são uma realidade. Muitas vezes esse tipo de ocorrência pode prejudicar milhares de sites e aplicações que estão no mesmo datacenter.

**A maioria dos serviços de CDN possui recursos para reduzir o impacto de um ataque distribuído de negação de serviço**. E isso geralmente é feito automaticamente. A proteção contra ataques do tipo _SQL injection_ e _cross-site scripting_ também é outro recurso frequentemente oferecido pelas CDNs.

### Prolongamento da vida útil da sua hospedagem

Por aliviar a carga de processamento do servidor e ajudar com a demanda de tráfego, uma CDN pode permitir que um site em crescimento permaneça mais tempo na mesma hospedagem para sites em crescimento. A lógica é a seguinte: se determinado site ou blog possui uma audiência crescente, em algum momento de sua vida ele precisará migrar para uma hospedagem mais robusta, que atenda à crescente demanda sem interrupções. **Ao aliviar a carga do servidor, a CDN pode adiar o momento de um upgrade de hospedagem**.

### SSL gratuito

Ter um **certificado SSL** também era um item considerado opcional há alguns anos, mas que agora **é indispensável para qualquer site profissional**. O certificado de segurança está entre os fatores de ranqueamento do Google [desde 2014](https://webmasters.googleblog.com/2014/08/https-as-ranking-signal.html).

Grande parte das empresas provedoras de CDN oferece um certificado SSL gratuitamente. Geralmente o processo é completamente automatizado, ou seja, é apertar um botão e aguardar a instalação do certificado. Há ainda a possibilidade de escolher se a encriptação ocorrerá apenas na borda (_edge_: CDN <-> clientes) ou totalmente (_full_: servidor de origem <-> CDN <-> clientes).

## Quando a CDN não poderá ajudar

**A CDN não vai interferir nos recursos externos de um site**. Em situações nas quais é necessário o carregamento de scripts externos (ex.: Google Analytics, pixel do Facebook e outros) você sempre dependerá do tempo de processamento e de resposta dos servidores do serviço em questão. Em alguns casos, o recurso poderia ser copiado e servido a partir da CDN, no entanto, qualquer atualização no script seria ignorada, o que pode não ser uma boa ideia.

Portanto, cabe avaliar se o recurso é indispensável. Se não for, pode ser interessante desenvolver uma alternativa dentro do seu domínio ou até mesmo remover completamente a funcionalidade.

## Formas de usar a CDN para servir conteúdo

Existem duas maneiras distintas de configurar uma CDN em um site. Vamos conhecê-las agora.

### Servindo recursos estáticos

Nessa modalidade **os links para os recursos estáticos do site são alterados para que sejam servidos pela CDN**. Tradicionalmente, um site faz suas requisições dentro do mesmo domínio, seja o caminho relativo ou não. Como por exemplo:

```
/imagens/figura1.jpg
/js/script.js
/css/style.css
...
```

Você pode configurar estes recursos para serem servidos pela CDN. Nesse caso, seus links ficarão parecidos com:
```
https://minhacdn.dominio.com/imagens/figura1.jpg
https://minhacdn.dominio.com/js/script.js
https://minhacdn.dominio.com/css/style.css
...
```

Pode ser um subdomínio da própria CDN ou um subdomínio dentro do seu site, configurado para apontar para os servidores da CDN.
Esse modo de utilização já pode reduzir o uso de recursos do servidor. Mas se você quiser ainda mais desempenho, confira a modalidade a seguir.

### Como proxy reverso

Nesta modalidade, não há necessidade da criação de subdomínios, porque **o DNS deve ser apontado para a CDN**, ao invés de apontar para o servidor de hospedagem. **Os recursos estáticos serão cacheados da mesma forma como seriam na situação anterior, mas permanecem dentro do domínio.** Além dos recursos estáticos, cópias inteiras das páginas de um site podem ser cacheadas.

Quando a requisição de uma página é feita, o proxy reverso avalia quais recursos estão cacheados e retorna com o conteúdo em cache. Caso não haja uma cópia em cache, aí sim a requisição é endereçada para o servidor web de origem. Muitas CDNs trabalham dessa maneira. A CloudFlare, que oferece o serviço incluindo uma modalidade gratuita, opera assim e **utiliza o NGINX como proxy reverso**.

## Conclusão

Se você deseja ter um site veloz, alguns aspectos precisam ser analisados. Entre eles, **considere a utilização de uma CDN para acelerar o carregamento das páginas e para aliviar a carga do servidor de hospedagem**.

Existem muitas empresas oferecendo o recurso hoje em dia. Algumas, inclusive, o oferecem junto com a própria hospedagem. E isso não precisa custar muito caro. Pelo contrário: há empresas oferecendo CDN gratuitamente, como é o caso da CloudFlare.
Ficou com alguma dúvida ou quer acrescentar uma informação? Deixe um comentário. ;)

---
Crédito da imagem: [Unsplash](https://unsplash.com/photos/NqOInJ-ttqM)
