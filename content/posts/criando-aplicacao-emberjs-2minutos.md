---
title: Criando uma aplicação Ember.js em 2 minutos
authors: Aurélio Saraiva
type: post
date: 2017-10-29
excerpt: “Mas Ember parou no tempo”... Será?!
image: https://cdn-images-1.medium.com/max/800/1*zHcG2ZywrWKau3AAlYdS6g.jpeg
categories:
  - javascript
tags:
  - emberjs
  - Frameworks Javascript
  - javascript
---

Ultimamente eu tenho conversado com diversos desenvolvedores sobre Framework
Ember.js. Na grande maioria das vezes as pessoas pensam no Ember com estranheza
do tipo:

> “Mas Ember parou no tempo” , “Ember está ultrapassado”, “Ember é lento” ou
> “Ember não é produtivo”

Felizmente eu preciso discordar. Ember tem uma release nova a cada 2 meses,
estando atualmente na [versão 2.15](https://emberjs.com/builds/). Para você ter
uma ideia Angular CLI é inspirado no [Ember CLI](https://ember-cli.com/) e
projetado com a ajuda do Core-Team do Ember. Deixo esse link para você conhecer
um pouco mais. [Ember.js roubando da
comunidade](https://codetalks.net/ember-js-roubando-da-comunidade-b71c974fbd43).

Voltando ao assunto do post! Que é mostrar o quanto o Ember é ágil!

Para facilitar a criação de uma aplicação utilizando Ember, a equipe do Ember
desenvolveu uma ferramenta chamada Ember CLI que reduz toda a complexidade
envolvida para criar um projeto e configurar um ambiente de desenvolvimento.

Para exemplificar a simplicidade de criar uma aplicação Ember, usando essa
ferramenta, vamos criar um projeto e gerar uma versão de produção.

Vou assumir que você já tenha instalado **Node 4+**, caso não tenha, instale
antes de continuar.

**Esses links podem ajudar você: **
[https://nodejs.org/en/download/package-manager/](https://nodejs.org/en/download/package-manager/)<br>
[https://tableless.com.br/como-instalar-node-js-no-linux-corretamente-ubuntu-debian-elementary-os/](https://tableless.com.br/como-instalar-node-js-no-linux-corretamente-ubuntu-debian-elementary-os/)

Para começar, vamos instalar um pacote npm, **ember-cli** em sua maquina,
executando esse comando:


Feito isso, você já tem a ferramenta de desenvolvimento do Ember instalada na
sua maquina. Digite no terminal para testar:


    Usage: ember <command (Default: help)>

    Available commands in ember-cli:

    ember addon <addon-name> <options...>
      Generates a new folder structure for building an addon, complete with test harness.
      --dry-run (Boolean) (Default: false)
        aliases: -d
      --verbose (Boolean) (Default: false)
        aliases: -v
      --blueprint (String) (Default: addon)
        aliases: -b <value>
    ...

Você pode olhar com calma depois todos os comandos disponíveis.

Tendo instalado, vamos criar um projeto novo executando no terminal:


Feito isso, você deve ter uma estrutura similar essa.

    my-app/
    ├── app
    ├── config
    ├── ember-cli-build.js
    ├── node_modules
    ├── package.json
    ├── package-lock.json
    ├── public
    ├── README.md
    ├── testem.js
    ├── tests
    └── vendor

Pronto! Já temos tudo para rodar nossa aplicação Ember. Para testar execute no
terminal:

    Could not start watchman
    Visit 
     for more info.
    Livereload server on 

    Build successful (6161ms) – Serving on 

Agora acesse [https://localhost:4200](https://localhost:4200,/). Vai ser
apresentado uma tela similar a esta:

Tudo finalizado! Agora temos uma aplicação Ember funcionando em ambiente de
desenvolvimento em apenas **3 comandos**.

A medida que você vai editando os arquivos, o Ember vai compilar e atualizar
automaticamente a página. Permitindo você ganhar agilidade no desenvolvimento.

Abra o arquivo: `app/templates/application.hbs` e substitua o conteúdo por este:

    &lt;h1&gt;Hello World&lt;/h1&gt;

Se você acessar o navegador novamente, você verá que o conteúdo foi alterado.

Bom, agora que temos nossa aplicação funcionando, ela precisa ser publicada em
produção.

Para compilar uma versão para ir a produção vamos usar o comando `ember
build`que vai criar o diretório `my-app/dist` com nosso código pronto para
produção.


Pronto! feito isso seu código está pronto para ser publicado em produção.

Você pode copiar os arquivos da pasta `my-app/dist` compilado pelo Ember CLI.

Sim! Existe outras forma de publicar uma aplicação Ember em produção, usando
[Ember CLI Deploy](https://ember-cli-deploy.com/), por exemplo, mas isso é
assunto para outro post.

Bom! É isso, para saber mais ou mesmo criar uma aplicação de exemplo mais
complexa, você pode acessar a [página oficial do
Ember](https://guides.emberjs.com/v2.15.0/tutorial/ember-cli/).

Até a próxima! Leia mais abaixo:

* [Ember](https://medium.com/tag/ember?source=post)
* [Front End
Development](https://medium.com/tag/front-end-development?source=post)
* [Framework](https://medium.com/tag/framework?source=post)
* [JavaScript](https://medium.com/tag/javascript?source=post)
* [Emberjs Brasil](https://medium.com/tag/emberjs-brasil?source=post)

