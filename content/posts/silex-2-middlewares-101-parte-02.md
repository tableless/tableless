---
title: 'Silex 2 & Middlewares 101 – Parte 02'
author: Nando Kstro Net
type: post
date: 2017-02-19
excerpt: |
  Olá devs! Tudo bem? Espero que sim! Estamos de volta com mais um post da série sobre o micro-framework Silex! Desta vez, vamos fazer uma parada para atualizar a versão do nosso micro-framework, para versão 2.*!
  A partir deste post vamos escrever baseada nesta versão e falaremos ao longo de cada post, sobre as principais diferenças em relação as versões passadas! Vamos lá!
url: /silex-2-middlewares-101-parte-02/
categories:
  - Back-end
  - PHP
tags:
  - Middlewares Silex
  - Silex
  - Symfony

---
Estamos de volta com mais um post da série sobre o micro-framework Silex! Desta vez, vamos fazer uma parada para atualizar a versão do nosso micro-framework, para versão 2.*!

A partir deste post vamos escrever baseada nesta versão e falaremos ao longo de cada post, sobre as principais diferenças em relação as versões passadas! Vamos lá!

## Silex 2

Uma das grandes mudanças do micro-framework, foi o seu componente de Dependency Injection, o Pimple. O que impactou diretamente na parte de services.  Houveram algumas implementações na parte de controllers básicos e também alguns serviços internos que foram renomeados ou integrados diretamente no micro-fw. Como comentei, veremos cada particularidade nas mudanças ao longo dos posts!

### Atualizando para a versão 2

Para atualizarmos o Silex para sua versão mais recente, precisamos alterar nosso arquivo composer.json. Nosso composer.json fica da seguinte forma, em relação ao <a href="https://tableless.com.br/conhecendo-e-instalando-o-silex/" target="_blank">primeiro post</a>:

<pre class="lang-json">{
    "require" : {
    "silex/silex" : "2.*"
    }
}
</pre>

Agora, basta executarmos um composer update em nosso terminal para obtermos o Silex atualizado!

<img class="size-full wp-image-57045 aligncenter" src="uploads/2017/01/Screen-Shot-2017-01-23-at-13.36.09.png" alt="" width="582" height="631" />

## Middlewares (Continuação)

Em <a href="https://tableless.com.br/silex-middlewares-101-parte-1/" target="_blank">nosso último post</a>, da série, falamos sobre os middlewares de aplicação, como vimos, seu impacto abrange todo o app!

### Middlewares de Rota

A diferença entre os middlewares de rota pros middlewares de aplicação, além do escopo que abrange apenas a rota na qual o middleware está definido, é que os middlewares de rota não possuem o método `finish`, apenas o `before` e o `after`. O comportamento é o mesmo. Veja o código a seguir:

<pre class="lang-php">&lt;?php
require __DIR__ . '/vendor/autoload.php';

use Silex\Application;

$app = new Application();
$app-&gt;get('/', function(Application $app) {
    return $app-&gt;escape('Router Content!');
})
-&gt;before(function(){
    print 'Before Route Middleware | ';
})
-&gt;after(function(){ print ' After Route Middleware'; }); 

$app-&gt;run();</pre>

No código acima temos os dois middlewares de rotas disponíveis, porém os mesmos só serão executados quando acessarmos a rota / (Rota principal de nosso app), mantendo o mesmo comportamento dos de aplicação.

### Definindo ordem de execução

&nbsp;

Podemos encadear quantos middlewares quisermos, para Rota e para Aplicação, e também definirmos uma ordem de execução.  Por padrão, os middlewares serão executados na ordem em que estão escritos, seguindo suas regras! Porém, o Silex nos disponibiliza duas constantes para alterarmos a ordem de execução dos mesmos. São elas:

  * `Application::EARLY_EVENT;`
  * `Application::LATE_EVENT;`

Vejamos o código a seguir:

<pre class="lang-php">$app = new Application();
$app-&gt;get('/', function(Application $app) {
    return $app-&gt;escape('Router Content!');
})
-&gt;before(function(){
    print 'Executará segundo por conta do LateEvent';
}, Application::LATE_EVENT)
-&gt;before(function(){ 
    print 'Executará primeiro por conta do EarlyEvent'; 
}, Application::EARLY_EVENT); 
</pre>

O código acima, por padrão, executaria os middlewares before na ordem em que seguem, porém o primeiro middleware a ser executado será o segundo before e logo em seguida o primeiro before definido. Isso acontece por conta da ordem de prioridade estabelecida com as contantes, onde, tudo que tiver EARLY\_EVENT executará primeiro, e LATE\_EVENT executará por último.

## Conclusão

Bom, vamos chegando ao fim de mais um post sobre o micro-framework Silex, até o momento já temos o conhecimento geral de como os middlewares funcionam e com certeza eles serão bem úteis em determinados cenários quando você estiver utilizando o Silex em suas criações! Nas próximas postagens falaremos mais sobre o micro-framework, especificamente sobre como os Services trabalham! Nos vemos lá!