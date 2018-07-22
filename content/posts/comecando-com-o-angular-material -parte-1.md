---
title: Começando com o Angular Material  – Parte 1
authors: Júlio Carneiro
type: post
date: 2016-08-08
url: /comecando-com-o-angular-material -parte-1/
categories:
  - Artigos
  - Técnicas e Práticas
tags:
  - angular-material
  - angularjs
  - Javascript
---
Decidi começar essa série de posts sobre **Angular** pois ultimamente é o que mais estou estudando, e pirando também rs, estou **viciado** no angular confesso, e não podia deixar de escrever sobre o **angular material** pois ele realmente me surpreendeu com sua facilidade que junto a sua beleza o torna bem **interessante**.

Vou escrever uma série com alguns posts baseados no que eu aprendi do angular material nesses tempos estudando na internet, espero que possa ajudar uma galera que queria muito conhecer porém não sabia por onde começar ou tem dificuldade de achar algo em português.

_Lembrando que esta série exige um certo conhecimento de AngularJS para ser compreendida ok?_

#### Parte 1 — Baixar e instalar

Vamos começar criando uma **nova pasta** e começando um **projeto npm **dentro dela, veja:

<pre>cd Desktop
mkdir project
cd project
npm init</pre>

Vão aparecer algumas opções do projeto npm pra preencher, preencha conforme queira ou pule apertando “**enter**”.

Agora vamos instalar o **angular,** o **angular material** e as **dependências do material**:

<pre>npm install angular angular-material angular-animate angular-aria --save</pre>

Legal, instalamos as dependências que precisamos para começar nosso projeto, agora **precisamos linkar** com nosso arquivo html certo? Então vamos começar linkando **5 arquivos de dependências**, um de css que deverá ser linkado no **<head>**, e outros 4 scripts que linkamos **antes da tag de fechamento do body**, vejamos:

<pre class="graf--pre graf-after--p">&lt;html ng-app="app"&gt;
&lt;head&gt;
    &lt;link rel="stylesheet" href="node_modules/angular-material/angular-material.css"&gt;
&lt;/head&gt;
&lt;body&gt;
    &lt;div&gt;&lt;/div&gt;
    &lt;script src="node_modules/angular/angular.min.js"&gt;&lt;/script&gt;
    &lt;script src="node_modules/angular-animate/angular-animate.min.js"&gt;&lt;/script&gt;
    &lt;script src="node_modules/angular-aria/angular-aria.min.js"&gt;&lt;/script&gt;
    &lt;script src="node_modules/angular-material/angular-material.min.js"&gt;&lt;/script&gt;
&lt;/body&gt;
&lt;/html&gt;
</pre>

Feito isso precisamos **chamar o módulo** e **incluir a dependência do angular-material**, veja:

<pre class="graf--pre graf-after--pre">&lt;script&gt;
    angular.module('app', ['ngMaterial'])
        .run(function(){
        console.log('Funcionando!')
    });
&lt;/script&gt;</pre>

Vejam que eu chamei nosso **ng-app** na tag **<html>**, isto é muito importante em nosso passo a passo pois vamos chamar o nosso módulo por ela, então como chamei na tag **<html>** ele vai se estender por toda a página procurando por diretivas, controllers etc.

Ainda neste exemplo, escrevi uma função que quando a página é carregada ela dispara uma mensagem no console, **você pode testar em sua máquina **para assimilar o que eu fiz até aqui.

Antes de dar continuidade ao artigo vou deixar o **link da documentação oficial** do angular material que é bem explicativa e com certeza vai te ajudar bastante nessa jornada de aprendizado, além do que vamos usar bastante os exemplos de lá nos artigos:

<p style="text-align: center;">
  <a href="https://material.angularjs.org/">https://material.angularjs.org/</a>
</p>

#### Action {.graf--h4.graf-after--mixtapeEmbed}

<p class="graf-after--h4">
  Ambiente preparado tudo funcionando? Legal, bora pra <strong>action</strong>, eu ia postar somente até aqui na parte 1 pro post não ficar gigante, porém acho que ficaria <strong>meio chato</strong> porque sei que se você está lendo isso quer ir logo pra <strong>action! </strong>Então decidi postar um combo parte 1 + parte 2, segura:
</p>

#### Layout

<p class="graf-after--h4">
  No Angular Material podemos usar algumas diretivas pré prontas para criarmos interfaces. Usando estas diretivas html podemos definir valores (ex:<strong>layout=”row”</strong>), que vão nos ajudar bastante a separar as coisas do jeito mais fácil para trabalharmos, pois os atributos vão definir o layout baseado nas <strong>classes css que já existem no angular material</strong>. Conforme a documentação, segue abaixo uma tabela contendo algumas especificações:
</p><figure> 

<

div class=&#8221;aspectRatioPlaceholder is-locked&#8221;>
  
<img class="progressiveMedia-image js-progressiveMedia-image aligncenter" src="https://cdn-images-1.medium.com/max/800/1*Zh1tH1Cuk-V7ljIIKukbXQ.png" />
  
</figure> 

Então, como o angular material **tem uma api flexbox** podemos setar uma div**row**, e dentro dela **criar 2 divs** com um “**flex=”50”**”, assim cada div dentro da div **row** terá o espaço de **50% da tela** uma ao lado da outra, veja o exemplo:

<pre class="graf--pre graf-after--p">&lt;div layout="row"&gt;
    &lt;div flex="50"&gt;Primeira div&lt;/div&gt;
    &lt;div flex="50"&gt;Segunda div&lt;/div&gt;
&lt;/div&gt;

</pre>

Abaixo temos algumas **especificações de breakpoints** que também serão bem importante pra criarmos nossos apps e deixarmos tudo responsivo, vamos **associar breakpoints** **a definições de mediaquery**, veja:<figure> 

<img class="progressiveMedia-image js-progressiveMedia-image" src="https://cdn-images-1.medium.com/max/800/1*gRZXmgUUu4Nu48zmSVKATA.png" />
  
</figure> 

Agora podemos **combinar o breakpoint junto a api layout** e pronto, temos responsividade em nosso app 😀 veja como funciona:<figure> 

<img class="progressiveMedia-image js-progressiveMedia-image" src="https://cdn-images-1.medium.com/max/800/1*bF72D6KkAPhg1IS9jcjvBA.png" />
  
</figure> 

Com essas informações já podemos começar a fazer algumas coisas como fazer a div aparecer com uma estrutura default para quando estiver no **desktop**, e outra quando estiver no **celular** apenas manipulando a api **layout**, veja:

<pre class="graf--pre graf-after--p">&lt;md-content class="md-padding" layout-xs="column" layout="row"&gt;&lt;/md-content&gt;</pre>

Veja que eu pedi para por default o **md-content** vir como **row**, e quando a tela for menor que **599px** como vimos nos breakpoints setando o **xs**, ele mude para **column**.

#### Layout-align

<p class="graf-after--h4">
  Podemos também alinhar elementos em nossa página com a api <strong>layout-align</strong>, veja um exemplo:
</p>

<pre class="graf--pre graf-after--p">&lt;div layout="row" layout-align="center"&gt;
    Hello World!
&lt;/div&gt;</pre>

Podemos também **combinar com os breakpoints** caso for preciso para deixarmos responsivo, veja a tabela:<figure> 

<img class="progressiveMedia-image js-progressiveMedia-image" src="https://cdn-images-1.medium.com/max/800/1*hltJORr9bcACAOwG3EkQlg.png" />
  
</figure> 

####  {.graf--h4.graf-after--figure}

####  {.graf--h4.graf-after--figure}

#### Show & Hide {.graf--h4.graf-after--figure}

<p class="graf-after--h4">
  Outra coisa muito interessante na parte de layouts do angular material é o <strong>show & hide</strong>, uma api que pode ser usada para <strong>mostrar ou esconder</strong> algum elemento conforme a resolução:
</p><figure> 

<img class="progressiveMedia-image js-progressiveMedia-image" src="https://cdn-images-1.medium.com/max/800/1*eBPJTlusl1IEA7gGhRxV0w.png" />
  
</figure> 

Reproduza o código abaixo para ver o comportamento da página quando **diminuímos a janela do navegador**:

<pre class="graf--pre graf-after--p">&lt;div layout="row"&gt;
    &lt;div hide show-gt-sm flex&gt;
        Mostrar somente em dispositivos gt-sm
    &lt;/div&gt;
    &lt;div hide-gt-sm flex&gt;
        Mostrar em resolução pequena e média&lt;br&gt;
        Esconder em dispositivos gt-sm        
    &lt;/div&gt;
    &lt;div show hide-gt-md flex&gt;
        Mostrar em resolução pequena e média&lt;br&gt;
        Esconder em dispositivos gt-md        
    &lt;/div&gt;
    &lt;div hide show-md flex&gt;
        Mostrar somente em resoluções médias&lt;br&gt;
    &lt;/div&gt;
    &lt;div hide show-gt-lg flex&gt;
        Mostrar em resoluções maiores que 1200px de largura&lt;br&gt;
    &lt;/div&gt;
&lt;/div&gt;</pre>

Viu só? Facilitou bastante o jeito como podemos construir nossas estruturas responsivas. Aprendemos hoje como colocar e iniciar o angular-material no seu projeto, e um pouco mais sobre a parte de layout e layout responsivo, creio que no próximo post vamos poder brincar com coisas mais legais, porém essa parte é **essencial para qualquer pessoa que quer aprender o angular material**, sem ela fica muito difícil de trabalharmos.

Peço desculpas **pelo tamanho do post** porque creio que tenha ficado meio enorme rs e isso não foi **absolutamente nada** do que o angular-material pode fazer, espero que tenha contribuído com seu conhecimento, e no próximo post vou explicando um pouco sobre os services do angular material,**qualquer feedback será bem-vindo**!