---
title: O que há de novo no Rails 5
author: João Almeida
type: post
date: 2015-08-24
excerpt: |
  |
    Durante sua keynote no RailsConf 2015, DHH - o criador do framework, apresentou as novidades em andamento no projeto Rails e anunciou o lançamento da versão 5 para o último trimestre de 2015.
url: /novidades-do-rails-5/
categories:
  - Back-end
  - Código
  - Rails
  - Ruby

---
O framework é o mais utilizado pelos desenvolvedores Ruby ao criar aplicações web e mantém a frequência de uma grande atualização a cada 2 anos. Vamos conferir um pouco destas novidades.

## Incorporando a gem rails-api

Muitas aplicações Rails são criadas com objetivo de prover uma API para outros serviços/aplicações. A gem <a href="https://github.com/rails-api/rails-api" target="_blank">rails-api</a> é famosa na comunidade por permitir a criação de aplicações Rails que descartam funcionalidades e aspectos desnecessários em uma API. Com isso essas aplicações são mais leves e rápidas.

Uma das novidades do Rails 5 é que essa gem vai ser incorporada ao projeto principal, permitindo a criação nativa de APIs. Esta é uma novidade interessante para times que trabalham com microserviços e aplicações client-side que dependem de dados externos.

## Turbolinks 3

A manutenção do Turbolinks no framework é mais uma decisão polêmica que o time do Rails toma em sua trajetória. Apesar da proposta de tornar sua aplicação mais rápida usando Javascript para gerenciar trechos do conteúdo, as alterações necessárias para tirar proveito do Turbolinks ainda são uma barreira para sua adoção.

Em seu <a href="https://github.com/rails/turbolinks" target="_blank">repositório no Github</a> ainda podemos ver um aviso de que a versão 3 não está pronta para uso em produção. Nos resta então aguardar as novidades que veremos e se o Turbolinks 3 vai realmente tornar nossas aplicações mais rápidas sem muito sofrimento no desenvolvimento.

## Ruby 2.2.1

Desenvolvedores Ruby já estão acostumados com a velocidade de anúncio de novas versões e também com o <a href="https://www.ruby-lang.org/en/news/2014/01/10/ruby-1-9-3-will-end-on-2015/" target="_blank">fim de suporte de versões antigas</a>. Isso não surpreende tanto dado o cenário de uma linguagem tão nova e com uma comunidade bastante ativa.

A versão 2.2 do Ruby trouxe tantos benefícios e resolveu problemas antigos de performance (falaremos disso em outro post) que foi adotada como base para o Rails 5. Portanto, antes de pensar em adotar a nova versão do Rails em seu projeto você pode se antecipar e começar a migração para Ruby 2.2.1.

## Action Cables

Rails sempre foi famoso por ser um framework web completo. Mas o uso crescente de WebSockets, que permitem o envio de informações em tempo real direto para o lado do cliente, danificou um pouco essa imagem do Rails.

Para suprir a carência de websockets nativos teremos o ActionCable na versão 5. Trata-se de um <a href="https://github.com/rails/actioncable" target="_blank">projeto recente</a> mas já muito aguardado. Quem está aguardando para tirar proveito dessa novidade pode acompanhar o projeto <a href="https://github.com/rails/actioncable-examples" target="_blank">actioncable-examples</a>, mantido pela equipe do Rails afim de promover o ActionCable.

## Outras novidades

Para facilitar um pouco a vida especialmente dos iniciantes em Rails, o uso de comandos `rake` poderá ser feito com o alias `rails`. Teremos então:

<pre class="lang-ruby">rails db:migrate</pre>

ao invés de

<pre class="lang-ruby">rake db:migrate</pre>

Pequenas mudanças no ActiveRecord e no Minitest e a manutenção do CoffeeScript também foram anunciadas. Agora resta saber como todo este pacote será recebido pela comunidade no fim do ano.