---
title: Jails – O Framework e a Arquitetura do Javascript
author: Javiani
type: post
date: 2015-06-17
excerpt: Eu escrevi meu próprio framework por que estava insatisfeito com os oferecidos no mercado. E foi ótimo!
url: /jails-o-framework-e-arquitetura-javascript/
categories:
  - JavaScript
  - Técnicas e Práticas
tags:
  - framework javascript
  - jails
  - JavaScript
  - js

---
Quero compartilhar algo que estive desenvolvendo há um tempo: um framework JavaScript. Sim, mais um&#8230; porém este não é um MVC. Eu não acredito muito no MVC como vem sendo difundido para o front-end. Quem já leu algo sobre o **React** deve imaginar que não estou só nesta maneira de pensar.

Faz um bom tempo que trabalho com JavaScript e dentre todas as formas que usei para elaborar um projeto, uma se destacou por ser a mais eficaz. Estou falando da arquitetura baseada em **Módulos**, ou seja, uma **Arquitetura Modular**.

## Por que mais um Framework?

A necessidade de escrever um framework nasceu após ter trabalhado dois anos em um e-commerce enorme e muito conhecido, provavelmente você deve ter comprado lá algumas dezenas de vezes. Ao chegar neste projeto, percebi que mesmo tendo sido incialmente concebido de forma modular, usando uma biblioteca **AMD**, o projeto carecia de um **Framework**. Não basta apenas criar seus módulos, você precisa saber muito mais que isso, precisa saber como classificar os problemas, como abstrair os módulos e como relacioná-los.

Ao perceber a dificuldade da manutenção e pensando em como melhorar toda a arquitetura, fui atrás dos frameworks existentes no mercado.

## AngularJS, Backbone, Ember e React.

Estes eram os que estavam no mainstream e me chamaram a atenção. Estudei todos, não sou uma assumidade em nenhum, mas para mim bastava entender os paradigmas de cada um deles. Feitos os estudos, a minha conclusão era de que seriam inviáveis para o projeto por diversas razões, resumindo:

**AngularJS:** tinha futuro incerto; não era performático; pouco controle; muitas coisas aconteciam por baixo dos panos; uma boa parte dos seus componentes seriam removidos na próxima versão ( **AngularJS 2** ).

**Backbone:** ótimo para programadores. Difícil para quem está começando, muitos métodos para aprender, é modularizado, mas ainda é necessário um trabalho manual para arquitetar os padrões no seu projeto.

**Ember:** Díficil. Embora em seus screencasts tudo acontece de forma mágica e rápida, na prática é necessário uma curva de aprendizado considerável para ser produtivo.

**React:** Embora eu goste de projetos ousados, eu ainda não me acostumei com a idéia de misturar html e construção de markup via JavaScript. Para o React, tudo é componente, o que considero o principal motivo pelo e-commerce que eu trabalhava ter falhado numa arquitetura ideal, o fato de que tudo é a mesma coisa, no caso do meu projeto, tudo era módulo.

## Conclusão

O fato de ter estudado cada uma delas me deu um conhecimento que eu não tinha, tive algumas idéias&#8230; Este aprendizado era o que precisava para olhar para todos os problemas que havia passado no projeto e imaginar qual seria a solução. Na hora, me veio na cabeça um projeto antigo que eu tinha, havia colocado o nome **Jails**, não tinha nada haver com o **Rails**, o nome surgiu de uma brincadeira. Era um MVC na época, mas seria reformulado.

## A proposta.

A idéia era desenvolver um framework leve, pequeno o bastante para gastar o menor tempo possível refatorando e fazendo atualizações, assim eu também minimizaria as falhas. Que ajudasse nas tarefas repetitivas e como organizar melhor as funções de uma aplicação seja ela complexa ou não e garantir um fluxo mais previsível. E seria modular, deveria crescer de acordo com a comunidade, assim como o **Rails**.

## Jails, A filosofia.

Basicamente o Jails abstrai sua aplicação em 4 partes.

  * **Components**
  * **Controllers**
  * **Apps**
  * **Modules**

Um **componente** resolve um determinado problema, é mais genérico, escuta e ouve eventos, manipula o dom, não sabe da existência de outros elementos e classes.

Uma **controladora** fecha um escopo um pouco maior, menos genérico, mais ligado à alguma regra de negócio, usado onde há uma relação entre dois ou mais componentes, escuta e dispara eventos para os componentes.

As **aplicações** são o maior escopo da página, escuta eventos de componentes e controladoras, realiza as regras de negócio da página numa escala mais macro, menos genérica que as controladoras.

Os **módulos** são apenas estruturas de classes ou módulos AMD, que podem ou não utilizar o Jails e seus elementos, sendo totalmente stand-alone, capaz de ser usado em projetos que não possuem o Jails. A **Model** padrão do Jails é um exemplo de um módulo, pois é independente do framework.

## A comunidade escolhe o padrão

Eu não tenho a pretensão de escrever os melhores componentes e módulos para o framework, é provável que outros desenvolvedores o façam muito melhor do que eu. Portanto, para mim faz todo o sentido fazer a **Model** como um módulo a parte, porque um desenvolvedor pode criar um projeto paralelo e fazer uma **Model** mais sofisticada.

Da mesma forma, a **View** padrão do **Jails** é apenas um componente disponibilizado no repositório. Não faz sentido a comunidade esperar por um release para usar uma **View** mais sofisticada ou diferente.

## Flexibilidade e eliminando acoplamento

O MVC no front-end das formas como foi elaborado simplesmente não escala. É burocrático, você fica vendido à um fluxo Model -> Controller -> View que em muitas vezes não faz o menor sentido. No Jails você **pode** ou não utilizar **Models** ou **Views**. Porque são apenas módulos/componentes.

Com isso vem a simplicidade, a curva de aprendizado é baixa, você precisa decorar 6 métodos que são disponibilizados igualmente para as **Controllers e Apps**. Na verdade, elas são a mesma coisa, os componentes possuem apenas 2 métodos.

Você apenas precisa aprender mais métodos conforme adiciona componentes/módulos no seu projeto, você não é obrigado a saber dezenas e dezenas de métodos que pode nunca utilizar.

## Test Drive

Existem duas formas de trabalhar com o Jails, uma é usando de forma assícrona, bom pra prototipar e subir uma aplicação rápidamente, e outra é compilando o JavaScript pra uma saída só minificado. Vou mostrar apenas a primeira que utiliza módulos/componentes do repositório do Jails.

Crie uma estrutura de pastas padrão: (É possível mudar)

+ assets/js/
  
index.htm

Jails utiliza o **gulp** como automatizador:

<pre class="lang-bash">npm install gulp-jails</pre>

Instale o gulp localmente:

<pre class="lang-bash">npm install gulp</pre>

Crie o arquivo gulpfile.js se não tiver, e carregue as tarefas do Jails:

<pre class="lang-javascript">require('gulp-jails')();</pre>

Pronto, agora já temos o automatizador do Jails.

No index.htm, adicione a variável global usada para referenciar nosso app inicial:

<pre class="lang-javascript">var global = { page :'apps/my-app' };</pre>

Aqui estamos carregando a requirejs e falando para ela executar o config.js, a variável global.page dirá ao nosso config.js qual app deveremos iniciar da nossa pasta de apps nesta tela. Tudo pronto&#8230; agora é só criar os arquivos. Por enquanto nossa pasta **js** está vazia, mas precisamos criar o **config.js** e **apps/my-app.js**.

<pre class="lang-bash">gulp jails/config -n global.page</pre>

Este comando criará o config.js, com algumas definições e apontamentos para o repositório oficial.

<pre class="lang-javascript">require.config({
    baseUrl :'assets/js/',
    deps :['jquery', 'jails', global.page],
    paths :{
        jails :'//rawgit.com/Javiani/Jails/master/source/jails.min',
        mods :'//rawgit.com/jails-org/Modules/master',
        comps :'//rawgit.com/jails-org/Components/master',
        jquery :'//code.jquery.com/jquery-2.1.1.min'
    },
    callback :function( jquery, jails ){
        jails.start({ base :jquery });
    }
});
</pre>

Agora criamos o arquivo my-app.js

<pre class="lang-bash">gulp jails/app -n my-app</pre>

`my-app.js`

<pre class="lang-javascript">define([
    'jails'
],  
function( jails ){
    jails.app('my-app', function(html, data){
        this.init = function(){};
    });
});
</pre>

Criando o app e o arquivo config, temos o mínimo para rodar um código executável, basta colocar um `alert()` ou um `console.log()` no método `.init()` da app.

Sem esquecer de referenciar no markup!

<pre class="lang-html">&lt;body data-app="my-app"&gt;
</pre>

O primeiro componente vamos criar localmente, deverá ouvir uma lista de radio buttons e disparar um evento enviando o valor do radio clicado.

<pre class="lang-javascript">define(['jails'], function( jails ){
    jails.component('my-component', function(html, anno){
        var cp = this, buttons;

        this.init = function(){
            buttons = html.find('input[type=radio]');
            html.append('Meu componente!!');
            buttons.on('change', emit);
        };

        function emit(){
            cp.emit('choose', this.value);
        }
    });
});
</pre>

Se você sabe jQuery, ou Zepto, aqui você está em casa =). É aconselhável que você passe um componente para um estagiário ou um júnior que está aprendendo JavaScript. Porque geralmente é simples e num escopo fechado, ajuda no aprendizado.

O que vamos fazer é utilizar um componente `hello-world` que está no repositório do projeto para interagir com o nosso componente inicial. Vamos fazer este relacionamento usando a application mesmo:

<pre class="lang-javascript">define([
    'jails',
    'components/my-component',
    'comps/hello-world/hello-world'
], function( jails ){

    jails.app('my-app', function(html, data){

        var app = this, cp, hello_world;

        cp = app.x('[data-component*=my-component]');
        hello_world = app.x('[data-component*=hello-world]');

        this.init = function(){
            hello_world('greetings');
            this.listen('my-component:choose', action);
        };

        function action(e, value){
            hello_world('answer', value);
        }
    });
});
</pre>

Carregamos os dois mixins dos componentes da nossa aplicação. Um de maneira externa, usando o namespace **comps ** definido no `config.js` e outro carregado localmente da nossa pasta components.

Guardamos duas referências para os dois componentes através do método `.x()`, a query usada é um seletor jQuery.

No init executamos via evento o método público `hello-world.greeting()` que apenas exibirá uma mensagem amigável =).

Depois ouvimos o evento disparado por nosso componente, sempre o nome vindo antes da ação `'meu-componente:acao'`, executamos outro método do componente `hello-world.answer()`.

Sempre utilizamos as referências para executar métodos públicos dos nossos componentes, se os componentes não existirem na página, ou não possuírem o método, a aplicação não irá quebrar, levantando um erro, assim, deixamos nossa aplicação desacoplada, pois se alguém grita e ninguém ouve, nada acontece na vida real não é mesmo?

Embora os scripts estejam sendo carregados, precisamos definir no html, onde o mixin irá atuar:

<pre class="lang-html">&lt;div data-component="hello-world"&gt;&lt;/div&gt;

    &lt;form data-component="my-component"&gt;

        &lt;label&gt;How are you?&lt;/label&gt;
        &lt;input type="radio" name="question" value="how" /&gt;

        &lt;br /&gt;
        &lt;label&gt;What day is today?&lt;/label&gt;
        &lt;input type="radio" name="question" value="today" /&gt;

        &lt;br /&gt;
        &lt;label&gt;Where should I start from?&lt;/label&gt;
        &lt;input type="radio" name="question" value="start" /&gt;

        &lt;br /&gt;
        &lt;label&gt;Bye&lt;/label&gt;
        &lt;input type="radio" name="question" value="bye" /&gt;

        &lt;br /&gt;
        &lt;label&gt;Nothing to say&lt;/label&gt;
        &lt;input type="radio" name="question" value="nothing" /&gt;
     &lt;/form&gt;

</pre>

O componente `hello-world` responde à alguns parametros no método `.answer()` como:`how`, `today`, `start`, `bye` e `nothing`. Dessa forma conseguimos fazer dois componentes disconexos funcionarem sozinhos, e fizemos a relação entre os dois usando uma application.

Há muito mais coisas envolvidas no framework, mas não daria para falar tudo aqui. Se quiserem saber mais ou atém mesmo ajudar essa iniciativa escrevendo módulos, componentes ou contribuindo de alguma outra forma, fique à vontade. Os convido a dar uma olhada no projeto pelos links no final do post. Há também screencasts e a documentação do projeto. Seria muito bom ver uma iniciativa brasileira figurar dentre os frameworks gringos do mercado.

Valeu galera, um grande abraço.

**Screencast** : <http://jails-org.github.io/Jails/docs/#/video-components>

**Repositório**: <https://github.com/Jails-org/>

**Framework**: <https://github.com/jails-org/Jails>