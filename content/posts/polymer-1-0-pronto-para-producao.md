---
title: 'Polymer 1.0 : Pronto para produção'
author: Beto Muniz
type: post
date: 2015-06-08
excerpt: Tudo sobre a mais nova versão do Polymer e porque ele está pronto para produção
url: /polymer-1-0-pronto-para-producao/
categories:
  - JavaScript
  - Mercado e Comportamento
  - Tecnologia e Tendências
tags:
  - JavaScript
  - polymer
  - web components

---
Fala Galera,&nbsp;vamos falar hoje sobre a versão 1.0 do&nbsp;<a href="https://www.polymer-project.org/" target="_blank">Polymer</a>. Fiz um compilado da palestra de lançamento realizada&nbsp;no <a href="https://events.google.com/io2015/" target="_blank">Google I/O 2015</a> que você pode conferir [aqui][1].

## Mas vamos ao que interessa&#8230;

Para&nbsp;continuar, nada melhor do que relembrar que o propósito do Polymer é de oferecer&nbsp;uma nova solução sobre&nbsp;a forma que desenvolvemos aplicações web (desktop e/ou mobile), tendo como base os Web Components e os&nbsp;diversos recursos oferecidos pela web moderna, visando assim um amadurecimento da Web Platform como um todo e a&nbsp;nível do que já encontramos em outras plataformas consolidadas.

E foi pensando nessas diretrizes que desde a <a href="https://www.polymer-project.org/0.5/" target="_blank">versão 0.5</a> do Polymer, o mesmo vem sendo reescrito, focando em máxima performance e também mantendo uma interface para desenvolvimento amigável aos seus adeptos.

Logo, o&nbsp;resultado deste empenho é visto na <a href="https://www.polymer-project.org/1.0/" target="_blank">versão 1.0</a>&nbsp;da biblioteca, que está extremamente performática em comparação a versão 0.5, visto que está três vezes mais rápida no Google Chrome e 4 vezes mais rápida no Safari. Além da&nbsp;redução de quase 40% do&nbsp;seu código, e assim, finalizando sua primeira versão e deixando&nbsp;a biblioteca pronta para produção.

## Meça suas palavras&#8230; Pronto para produção?

Em conjunto com a nova versão no Polymer, alguns serviços foram imediatamente lançados utilizando a biblioteca, justamente para exemplificar seu potencial. Dentre os vários serviços, alguns exemplos são: Google Music, Salesforce Mobile Package, Youtube WebApp, Vaadin entre outros. Sem contar outros serviços que já estão utilizando Web Components, como é o caso do Github e a Atavist.

## OK! Então&nbsp;vamos ao que mudou&#8230;

### Um catálogo de elementos remodelado e mais completo

<img class="alignleft size-full wp-image-49348" src="http://tableless.com.br/uploads/2015/06/Screen-Shot-2015-06-02-at-5.09.53-PM.png" alt="Novo Polymer Elements Catalog" width="945" height="515" />

Na nova versão a <a href="https://elements.polymer-project.org/" target="_blank">camada de elementos</a>, foi definida como uma espécie de &#8220;linhas de produtos&#8221;, basicamente, teremos segmentações mais bem definidas de componentes comumentes utilizados no desenvolvimento web, porém melhor do que falar, vamos ver quais são estes segmentos:

#### Iron Elements

Segmento que antigamente era chamado de Core Elements e que entrega elementos de baixo nível comumentes utilizados em aplicações web.

#### Paper Elements

Segmento com componentes que aplicam o modelo proposto pelo conceito do Material Design de interface através do Polymer.

#### Google Web Components

Encapsulamento de diversos serviços oferecidos pela Google, facilitando ainda mais o uso nas nossas aplicações com mapas, armazenamento em nuvem, autenticação, tradução entre vários outras funcionalidades oferecidas pelos serviços da Google através de um simples elemento HTML.

#### Gold Elements

Segmento que entrega componentes para se trabalhar com sistemas de checkouts, visto que isso ainda é uma tarefa relativamente trabalhosa, e principalmente no mundo mobile. Esta linha oferece validações de cartão de crédito, telefones etc. Além de controles para fluxo de checkout entre outras diversas funcionalidades para este nicho.

#### Platinum Elements

Segmento de componentes que abstraem APIs Web como Push Notifications, Offline Caching, Service Workers entre outras de maneira bem simplificada.

#### Neon Elements

Segmento com componentes para trabalhar com animações e efeitos de objetos na aplicação.

#### Molecules

Segmento com componentes que encapsulam bibliotecas de terceiros.

E por enquanto, é isto que temos com relação aos componentes prontos oferecidos pelo Polymer, mas a promessa é que daqui pra frente, exista um refinamento destes segmentos com a adição de novos componentes e otimização dos existentes, além da criação de novos segmentos caso a comunidade solicite para resolver problemas comuns.

## Bem-vindo Polymer Starter Kit

<img class="alignleft size-full wp-image-49352" src="http://tableless.com.br/uploads/2015/06/screenshot-developers.google.com-2015-06-02-17-12-22.png" alt="Site do Polymer Starter Kit" width="1680" height="884" />
  
Também foi lançado uma nova ferramenta chamada <a href="https://developers.google.com/web/tools/polymer-starter-kit/" target="_blank">Polymer Starter Kit</a>, que basicamente entrega um boilerplate com os últimos elementos lançados e ferramentas para colocar sua aplicação em produção.

#### E muito mais

Visto que foi muita coisa, abaixo segue uma lista dos principais impactos trazidos pela nova versão:

  * Novo sistema de data binding, mais rápido e muito mais simples.
  * Novo sistema de Tematização e Estilização, não precisaremos mais utilizar **/deep/** ou **::shadow**
  * Novo fallback de shadow DOM chamado _shady DOM_, mais leve e rápido para browsers que ainda não suportam a tecnologia.
  * Inclusão de um Sistema de _Behaviors_, tal sistema permitirá compartilhar blocos de código entre elementos. Isso sem dúvidas permite aplicar mais qualidade e compartilhar os elementos com outras aplicações e desenvolvedores.

## E como aprender para também colocar em produção?

Para tal, irei indicar alguns links, incluindo uma série de posts que fiz, independente da nova versão do Polymer, que visa desmistificar a biblioteca.

  * <a href="https://www.polymer-project.org/" target="_blank">Polymer Project</a>
  * <a href="https://www.youtube.com/playlist?list=PLOU2XLYxmsII5c3Mgw6fNYCzaWrsM3sMN" target="_blank">Polycasts</a>
  * <a href="https://github.com/Granze/awesome-polymer" target="_blank">Awesome Polymer</a>
  * <a href="http://webcomponents.org/" target="_blank">WebComponents.org</a>
  * <a href="https://github.com/obetomuniz/awesome-webcomponents" target="_blank">Awesome Web Components</a>
  * <a href="http://betomuniz.com/blog/web-components-hoje/" target="_blank">Web Components! Hoje!</a>
  * <a href="http://betomuniz.com/blog/desmistificando-o-polymer-parte-1/" target="_blank">Desmistificando o Polymer: Olá Polymer!</a>
  * <a href="http://betomuniz.com/blog/desmistificando-o-polymer-parte-2/" target="_blank">Desmistificando o Polymer: Porque o Polymer?</a>
  * <a href="http://betomuniz.com/blog/desmistificando-o-polymer-parte-3/" target="_blank">Desmistificando o Polymer: Polymer FAQ (unoffical)</a>

## E isso é tudo pessoal&#8230;

Para finalizar, agradeço muito a leitura e quero apenas deixar claro que independente de ferramenta, o teor deste artigo é de ser apenas uma chamada para que desde já, vocês se interessem pelos novos padrões trazidos, seja ele Web Components, ES6/ES7, CSS3/CSS4, WebGl, Service Workers, HTTP2.0 entre outros. É notório que a partir de 2015 teremos uma adoção no mercado em massa destes novos padrões, pois temos tecnologias e também o suporte dos browsers pra que isso seja possível, ou seja, não dá para deixar para última hora, comece agora mesmo a ler mais sobre essa hype de novidades.

E é isso, se gostou ou teve alguma dúvida, não deixe de escrever um comentário.

## Referências

Alguns links que usei de referência:

  * <a href="http://venturebeat.com/2015/05/28/google-launches-polymer-1-0-lets-developers-bring-app-like-experiences-to-the-desktop-and-mobile-web/" target="_blank">http://venturebeat.com/2015/05/28/google-launches-polymer-1-0-lets-developers-bring-app-like-experiences-to-the-desktop-and-mobile-web/</a>
  * <a href="https://blog.polymer-project.org/announcements/2015/05/29/one-dot-oh/" target="_blank">https://blog.polymer-project.org/announcements/2015/05/29/one-dot-oh/</a>
  * <a href="https://blog.polymer-project.org/announcements/2015/05/14/updated-elements/" target="_blank">https://blog.polymer-project.org/announcements/2015/05/14/updated-elements/</a>
  * <a href="https://www.polymer-project.org/1.0/" target="_blank">https://www.polymer-project.org/1.0/</a>
  * <a href="https://www.youtube.com/watch?v=fD2As5RmM8Q" target="_blank">https://www.youtube.com/watch?v=fD2As5RmM8Q</a>

 [1]: https://www.youtube.com/watch?v=fD2As5RmM8Q