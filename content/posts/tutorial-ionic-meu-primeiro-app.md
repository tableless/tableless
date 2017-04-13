---
title: Tutorial Ionic – Meu primeiro app
author: grillorafael
type: post
date: 2015-03-05
excerpt: Tutorial de como criar seu primeiro app utilizando o Ionic Framework através de uma app meteorológica geolocalizada para Android e iOS
url: /tutorial-ionic-meu-primeiro-app/
categories:
  - Mobile
tags:
  - app
  - ionic
  - mobile
  - tutorial

---
## Introdução

Após publicar uma <a href="http://tableless.com.br/introducao-ao-ionic-framework/" target="_blank">breve introdução do Ionic Framework</a>, vamos agora tentar construir uma app que consiga abordar o uso de componentes nativos de um celular assim como o build para as determinadas plataformas.

Para isso, ao decorrer deste tutorial, vamos construir uma app bastante simples que utiliza a posição do usuário para exibir os dados do tempo na tela.

## O que é necessário?

  1. NodeJS
  2. NPM

Após instalar os 2, vamos instalar o _ionic_ e o _cordova_ como módulos globais.

<pre class="lang-bash">npm install -g ionic cordova
</pre>

## Criando o projeto

Para criar a estrutura inicial do projeto, vamos utilizar o gerador do Ionic CLI. Como o app é bastante simples, vamos utilizar o gerador _blank_ do ionic.

<pre class="lang-bash">ionic start weather blank
</pre>

[<img alt="estrutura de páginas do Ionic" src="http://tableless.com.br/uploads/2015/02/Screen-Shot-2015-02-28-at-12.21.21-AM.png" width="163" height="440" class="alignnone size-full wp-image-47368" srcset="uploads/2015/02/Screen-Shot-2015-02-28-at-12.21.21-AM.png 163w, uploads/2015/02/Screen-Shot-2015-02-28-at-12.21.21-AM-51x139.png 51w" sizes="(max-width: 163px) 100vw, 163px" />][1]

Podemos ver então a estrutura de pastas inicial do projeto. Inicialmente vamos mexer somente no conteúdo da pasta _www_ que é onde se encontra nosso projecto html, css e js.

## APIS e Plugins utilizados

Para fazer a captura dos dados meteorológicos vamos utilizar uma API gratuita chamada <a href="https://developer.forecast.io/" target="_blank">Forecast for Developers</a>. Para fazer a captura dos dados temos que utilizar um plugin do Cordova de Geolocalização. É importante dizer que não é recomendável utilizar o _navigator.geolocation_ nativo pois ele irá pedir permissão para o usuário com frequência e irá mostrar uma mensagem não amigável para isso como a imagem abaixo ilustra.

<img alt="Diálogo de permissão de localização via html5" src="http://www.raymondcamden.com/images/bad.png" width="320" height="480" class="aligncenter" />

Para instalar o plugin de geolocalização do Cordova, basta rodarmos o comando abaixo na pasta do projeto.

<pre class="lang-bash">cordova plugin add org.apache.cordova.geolocation
</pre>

Após instalado o plugin do cordova, vamos instalar uma lib que tem implementado a comunicação com alguns plugins do Cordova de uma forma mais amigável para o AngularJS que é o <a href="http://ngcordova.com/" target="_blank">ngCordova</a>.

Para instalar o _ngCordova_ basta rodar

<pre class="lang-bash">bower install ngCordova
</pre>

E importar no arquivo _www/index.html_.

<pre class="lang-html">&lt;script src="lib/ngCordova/dist/ng-cordova.js"&gt;&lt;/script&gt; 
&lt;script src="cordova.js"&gt;&lt;/script&gt; 
</pre>

Após feito isso, devemos avisar para o AngularJS que nosso projeto depende deste módulo. Esta definição está no arquivo _www/js/app.js_

<pre class="lang-js">(function() {
    angular.module('weather', ['ionic', 'ngCordova'])
        .run(function($ionicPlatform) {
            $ionicPlatform.ready(function() {
                // Hide the accessory bar by default (remove this to show the accessory bar above the keyboard
                // for form inputs)
                if (window.cordova && window.cordova.plugins.Keyboard) {
                    cordova.plugins.Keyboard.hideKeyboardAccessoryBar(true);
                }
                if (window.StatusBar) {
                    StatusBar.styleDefault();
                }
            });
        });
})();
</pre>

Desse momento em diante temos acesso a todos os módulos do _ngCordova_.

## Organização

Como a App é bastante simples, não vamos fragmentar a implementação em diversos arquivos. Vamos focar em construir apenas utilizando o _app.js_. Vamos então construir 2 componentes no AngularJS, o serviço _Weather_ para se comunicar com a API e o controller _WeatherCtrl_ para fazer a ponte entre a nossa view e a api.

<pre class="lang-js">(function() {
    angular.module('weather', ['ionic', 'ngCordova'])
        .run(function($ionicPlatform) {
            $ionicPlatform.ready(function() {
                // Hide the accessory bar by default (remove this to show the accessory bar above the keyboard
                // for form inputs)
                if (window.cordova && window.cordova.plugins.Keyboard) {
                    cordova.plugins.Keyboard.hideKeyboardAccessoryBar(true);
                }
                if (window.StatusBar) {
                    StatusBar.styleDefault();
                }
            });
        })
        .factory('Weather', function($http) {

        })
        .controller('WeatherCtrl', function($scope, Weather) {

        });
})();
</pre>

Após feito isso, devemos fazer o bind entre o _WeatherCtrl_ e o nosso HTML.

<pre class="lang-html">&lt;body ng-app="weather" ng-controller="WeatherCtrl as weatherCtrl"&gt;
    &lt;ion-pane&gt;
        &lt;ion-header-bar class="bar-stable"&gt;
            &lt;h1 class="title"&gt;Weather&lt;/h1&gt;
        &lt;/ion-header-bar&gt;
        &lt;ion-content&gt;
            
        &lt;/ion-content&gt;
    &lt;/ion-pane&gt;
&lt;/body&gt;
</pre>

Feito isso, devemos então implementar o acesso aos dados da API através de uma posição geográfica.

<pre class="lang-js">.factory('Weather', function($q, $http) {
            var deferred = $q.defer();

            function getCurrentWeather(lat, lng) {
                var url = 'https://api.forecast.io/forecast/SUA_CHAVE_DE_API/' + lat +',' + lng + '?callback=JSON_CALLBACK';
                $http.jsonp(url)
                    .success(deferred.resolve)
                    .error(deferred.reject);

                return deferred.promise;
            }

            return {
                getCurrentWeather: getCurrentWeather
            };
        })
</pre>

O serviço retorna uma promise que é o retorno da chamada JSONP para a API que iremos capturar no controller após acessarmos a localização do dispositivo.

Com o serviço pronto, vamos então fazer a chamada ao GPS no _controller_ e com a posição, vamos capturar os dados meteorológicos.

<pre class="lang-js">.controller('WeatherCtrl', function($scope, $cordovaGeolocation, Weather) {
            $scope.loading = true;

            $scope.toCelsius = function(temperature) {
                return ((temperature - 32) / 1.8).toFixed(1);
            };

            $cordovaGeolocation
                .getCurrentPosition({
                    timeout: 10000,
                    enableHighAccuracy: false
                })
                .then(function(position) {
                    var lat = position.coords.latitude;
                    var long = position.coords.longitude;

                    Weather.getCurrentWeather(lat, long).then(function(data) {
                        $scope.weatherInfo = data;
                        $scope.loading = false;
                    }, function(error) {
                        //TODO Display error message
                    });
                }, function(err) {
                    //TODO Display error message
                });
        });
</pre>

Se vocês repararem, eu adicionei umas variáveis ao escopo para controlar se está carregando dados ou não e para converter de Fahrenheit para Celsius que usaremos posteriormente no nosso HTML.

Com o _controller_ preparado vamos então preparar o nosso HTML para mostrar uma imagem de carregamento enquanto não demos os dados e posteriormente mostrar a temperatura e a sensação térmica em celsius.

<pre class="lang-html">&lt;body ng-app="weather" ng-controller="WeatherCtrl as weatherCtrl"&gt;
    &lt;ion-pane&gt;
        &lt;ion-header-bar class="bar-stable"&gt;
            &lt;h1 class="title"&gt;Weather&lt;/h1&gt;
        &lt;/ion-header-bar&gt;
        &lt;ion-content class="text-center"&gt;
            &lt;div ng-show="loading"&gt;
                Carregando informações...
            &lt;/div&gt;
            &lt;div ng-hide="loading"&gt;
                &lt;p&gt;
                    Temperatura: {{toCelsius(weatherInfo.currently.temperature)}}º
                &lt;/p&gt;
                &lt;p&gt;
                    Sensação térmica: {{toCelsius(weatherInfo.currently.apparentTemperature)}}º
                &lt;/p&gt;
            &lt;/div&gt;
        &lt;/ion-content&gt;
    &lt;/ion-pane&gt;
&lt;/body&gt;
</pre>

Para visualizar o resultado podemos rodar o projeto no navegador utilizando o comando

<pre class="lang-bash">ionic serve
</pre>

## Gerando as _builds_ para o celular

Para gerar as os pacotes de App para celular basta rodarmos alguns comandos no Ionic CLI. É importante ressaltar que para criar o projeto iOS é necessário possuir um computador OSX.

### Adicionando as plataformas

Para adicionarmos as plataformas em que vamos compilar nossa app bastar rodar o comando _ionic platform add PLATFORM_ passando a plataforma desejada. Para efeitos de teste, vamos utilizar apenas o Android.

<pre class="lang-bash">ionic platform add android
</pre>

Após rodar esse comando vamos ver que o Ionic está criando um projeto Android dentro da pasta _platforms_.

[<img src="http://tableless.com.br/uploads/2015/02/Screen-Shot-2015-02-28-at-1.13.16-AM.png" alt="Criação do projeto Android" width="1061" height="258" class="alignnone size-full wp-image-47383" srcset="uploads/2015/02/Screen-Shot-2015-02-28-at-1.13.16-AM.png 1061w, uploads/2015/02/Screen-Shot-2015-02-28-at-1.13.16-AM-265x64.png 265w, uploads/2015/02/Screen-Shot-2015-02-28-at-1.13.16-AM-400x97.png 400w" sizes="(max-width: 1061px) 100vw, 1061px" />][2]

A partir daí não precisamos fazer mais nada! Basta rodar a app em seu aparelho ou emulador através do comando

<pre class="lang-bash">ionic run android
</pre>

Este comando irá fazer o _build_ e enviar para o celular que estiver conectado ou emulador que estiver aberto.

Para quem quiser, o projeto está disponível no <a href="https://github.com/grillorafael/ionic-weather" target="_blank">Github</a>

 [1]: http://tableless.com.br/uploads/2015/02/Screen-Shot-2015-02-28-at-12.21.21-AM.png
 [2]: http://tableless.com.br/uploads/2015/02/Screen-Shot-2015-02-28-at-1.13.16-AM.png