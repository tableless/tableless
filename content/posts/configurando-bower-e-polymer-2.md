---
title: Configurando Bower e Polymer
author: Mateus Ortiz
type: post
date: 2014-04-10
excerpt: Bower Gerenciador de pacotes muito usado e Polymer o novo polyfill do Google para Web Components.
url: /configurando-bower-e-polymer-2/
dsq_thread_id: 2596690540
categories:
  - Tecnologia e Tendências
tags:
  - bower
  - polimer
  - tooling

---
Bower é um gerenciador de pacotes e dependências muito utilizado hoje em dia. O Polymer é um novo polyfill do Google para Web Components. Neste artigo veremos algumas configurações do Bower e criaremos nosso primeiro web component com Polymer.

[youtube http://www.youtube.com/watch?v=owT5n9jlzVI?rel=0]

# Bower

Criado pelo Twitter, o Bower promete melhorar o gerenciamento de suas dependências no client-side. Via terminal, você controla tudo, desde instalar uma Dependência até atualizar a Dependência.

## Instalando o jQuery via Bower

O caminho normal para usar o jQuery no projeto é entrar no site, baixar o script e salvar no diretório do projeto. Você tem que fazer isso toda vez que o jQuery (ou qualquer outro script de terceiros) é atualizado.

Com o Bower não: primeiro você instala a dependência:

`bower install --save jQuery`

e quando sai uma nova versão, é muito mais fácil.

`bower install jQuery#version`

Simples assim.

# Polymer

Polymer é um polyfill para web components, que é uma especificação bem recente, composta por 4 novas especificações sendo elas: Custom Elements, HTML imports, Templates, Shadow Dom.
  
Web Components promete um cenário onde constrói ou estender suas Tags e elementos. O Polymer veio para ajudar nesse processo, trazendo essas vantagens hoje, mesmo antes da especificação ser oficial.

Via Bower, baixe o Polymer:

`bower install --save polymer`

Para ter mais detalhes, veja o vídeo no início do artigo.