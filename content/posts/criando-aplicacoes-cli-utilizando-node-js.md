---
title: Criando aplicações CLI utilizando Node.js
author: Igor Santana
type: post
date: 2016-05-03
url: /criando-aplicacoes-cli-utilizando-node-js/
categories:
  - nodejs
  - Back-end
  - Código
  - JavaScript

---
## Introdução

As aplicações que se utilizam da linha de comando do Sistema Operacional são comumente chamadas de `CLI Applications` ou `Command-Line Interface Applications`.  O que isto quer dizer? Estas aplicações só sofrerão alguma interação caso ela seja feita através de um Shell (BASH, DOS, ZSH, entre outros), mediante entrada de texto.

Este tipo de aplicação é contrária as `GUI Applications` ou `Graphical User Interface Applications`, que permitem o usuário interagir com a aplicação através de ícones, disposição dos elementos na tela, utilizando-se do Mouse para isto.

## Por que utilizar CLI?

Um dos principais motivos é a agilidade com que algumas tarefas podem ser executadas. Por utilizar apenas texto, algumas tarefas triviais são mais simples de serem executadas. Por exemplo, para copiar todos os arquivos com terminação `.js` de um diretório para outro:

**GUI:**

  1. Abrir o gerenciador de arquivos
  2. Navegar entre os diretórios até achar o desejado
  3. Selecionar todos os arquivos que terminam com `.js`
  4. Copiar os arquivos
  5. Trocar de diretório no gerenciador de arquivos
  6. Colar os arquivos

**CLI:**

  1. Abrir o terminal
  2. Executar o comando de cópia `cp *.js destinationfolder`

<img class="aligncenter size-full wp-image-53787" src="http://tableless.com.br/uploads/2016/04/tableless.gif" alt="Cópia de arquivos exemplo" width="639" height="114" />

Além disto, você consegue automatizar diversas tarefas criando arquivos executáveis, simplesmente executando estes arquivos (que podem ser em bash, python, ou qualquer outra linguagem que rode em ambiente Shell).

## Como fazer CLI Applications com Javascript?

Antes de tudo, faça o download do <a href="https://nodejs.org/en/download/" target="_blank">NodeJS</a>, que é o _runtime_ utilizado para executar Javascript no server-side.

Após ter o Node instalado, vá até o seu terminal e execute os seguintes comandos:

<pre class="lang-bash" style="padding-left: 30px">mkdir tableless-cli
cd tableless-cli
npm init--yes
</pre>

Estes comandos irão gerar um arquivo chamado `package.json`, que terá o seguinte formato:

<pre class="lang-javascript">{
  "name": "tableless-cli",
  "version": "1.0.0",
  "description": "",
  "main": "index.js",
  "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1"
  },
  "keywords": [],
  "author": "",
  "license": "ISC"
}
</pre>

O `package.json` é um arquivo de configuração do `NPM``(Node Package Manager)` que é utilizado como um descritor do seu projeto, além de manusear suas dependências, e o mais importante para nós neste tutorial, transformar seu arquivo Javascript em um executável no sistema.

Nosso projeto vai consistir de um arquivo javascript que, ao ser executado, nos trará a previsão do tempo da cidade passada como parâmetro. Esta previsão do tempo será resgatada através de uma busca para a API de Geocoding do <a href="https://developers.google.com/maps/documentation/geocoding/intro?hl=pt-br#GeocodingRequests" target="_blank">Google Maps</a>, e em seguida para a API do <a href="http://forecast.io" target="_blank">forecast.io</a>.

Vamos criar nosso arquivo index.js dentro de uma pasta `bin`.

<pre class="lang-bash" style="padding-left: 30px">mkdir bin
cd bin
touch index.js
</pre>

E, dentro do nosso package.json, vamos dizer ao npm que quando o comando &#8220;forecast&#8221; for executado no terminal, queremos que execute o arquivo `./bin/index.js`

<pre class="lang-javascript">{
  "name": "tableless-cli",
  "version": "1.0.0",
  "description": "",
  "main": "index.js",
  "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1"
  },
  "keywords": [],
  "author": "",
  "license": "ISC",
  "bin": {
    "forecast": "./bin/index.js"
  }
}
</pre>

No nosso arquivo `index.js`, vamos dizer para o sistema que o arquivo deve ser executado utilizando o NodeJS e vamos importar uma biblioteca padrão para realizar chamadas HTTPS.

<pre class="lang-javascript">#! /usr/bin/env node
  var https = require('https')
</pre>

Vamos adicionar mais duas linhas de códigos para testarmos se está tudo funcionando.

<pre class="lang-javascript">#! /usr/bin/env node
  var https = require('https')
  var arguments = process.argv.splice(2, process.argv.length -1).join(' ')
  console.log(arguments);
</pre>

A linha **3** captura os argumentos passados para nossa aplicação, ignorando os dois primeiros itens. Eles são ignorados pois são o caminho dos executáveis que farão nossa aplicação ser executada, e nós não precisamos desta informação. Além disto, transformamos o `Array` de argumentos para uma `String`, através do comando `.join(' ')`.

Voltando a pasta onde o arquivo `package.json` está, vá até seu terminal e execute os seguintes comandos:

<pre class="lang-bash" style="padding-left: 30px">npm link
forecast
</pre>

O comando `npm link` irá transformar em executável nosso arquivo dentro do sistema, deixando-o disponível para ser executado, e o comando `forecast` foi o que definimos dentro do nosso `package.json`.

Pronto, criamos nosso primeiro executável! Agora vamos fazer uma busca para a API do Google Maps para transformar o endereço digitado em Latitude e Longitude.

Para fazermos a busca para a API do Google Maps, precisamos de mais uma biblioteca padrão do Node.js: `querystring`. Utilizaremos a função `stringify` dela, para podermos normalizar o texto que enviaremos para a API.

<pre class="lang-javascript">#! /usr/bin/env node
var https = require('https')
var querystring = require('querystring')

var arguments = process.argv.splice(2, process.argv.length -1).join(' ')
var search    = querystring.stringify({ address: arguments })

https
  .get('https://maps.googleapis.com/maps/api/geocode/json?' + search, function(res){
    var data = ''

    res.on('data', function(newData){
      data += newData
    });

    res.on('end', function(){
      var location = JSON.parse(data).results[0].geometry.location
    })
  })
</pre>

Na linha 9, estamos fazendo uma chamada https para a API do google maps passando como parâmetro o que foi passado para nossa aplicação.

Na linha 18, obtemos como resultado da busca a Latitude e a Longitude da nossa pesquisa. Por prática estou usando apenas o primeiro resultado, mas sinta-se a vontade para brincar com os resultados da API.

Até agora, geramos um arquivo javascript executável através da linha de comando que faz uma busca na API do Google para um endereço passado como parâmetro.

## Utilizando a API do Forecast.

O [Forecast][1] é um site que mostra a condição do tempo e possui uma API muito boa para que nós, desenvolvedores, possamos aproveitar. É necessário uma `key` para fazermos uma requisição e, na versão gratuita, podemos fazer no máximo 1.000 chamadas por dia para a API. Como não teremos um volume muito grande de chamadas, vamos utilizá-la.

Para conseguir sua key de acesso, faça o cadastro [aqui][2].

Vamos utilizar agora o objeto de Geolocalização que obtivemos da API do Google Maps para fazermos uma chamada para API do Forecast.

<pre class="lang-javascript">#! /usr/bin/env node
var https = require('https')
var querystring = require('querystring')

var arguments = process.argv.splice(2, process.argv.length -1).join(' ')
var search    = querystring.stringify({ address: arguments })

https
  .get('https://maps.googleapis.com/maps/api/geocode/json?' + search, function(res){
    var data = ''

    res.on('data', function(newData){
      data += newData
    });

   res.on('end', function(){
      var location = JSON.parse(data).results[0].geometry.location
      var options = querystring.stringify({ units: 'si', lang: 'pt' })
      https
        .get('https://api.forecast.io/forecast//' + location.lat +',' + location.lng + '?' + options, function(resForecast){
          var data = ''

          resForecast.on('data', function(newData){
            data += newData
          });

          resForecast.on('end', function(){
            var json = JSON.parse(data)
            console.log('Temperatura Atual: ' + json.currently.temperature + ' ºC')
            console.log('Sensação Térmica: ' + json.currently.apparentTemperature + ' ºC')
            console.log(json.daily.summary)
          })
        })
    })
  })
</pre>

Com isto, finalizamos nossa aplicação. Foi feita uma chamada para a API do Forecast passando a latitude e longitude descobertas através da API do Google Maps.

Utilizamos o retorno da API do Forecast para mostrar no terminal algumas das informações retornadas. As opções que foram passadas para a API do Forecast foram utilizadas para formatar tanto o sistema de medidas (`units: 'si'`), quanto o idioma de retorno: (`lang: 'pt'`).

Executando a aplicação após ela estar finalizada:

<img src="http://tableless.com.br/uploads/2016/04/3EFswyb-Imgur.gif" alt="Finalizado a aplicação" width="858" height="152" class="alignnone size-full wp-image-53802" />

## Conclusão

Fazer aplicações que serão executadas na linha de comando com NodeJS é muito simples, e requer conhecimentos apenas da linguagem. Estas aplicações poderão ser executadas em qualquer Sistema Operacional (Windows, Linux, Mac) e podem nos ajudar e muito na resolução de tarefas corriqueiras do dia a dia.

O código desta aplicação está no meu [github][3], para quem quiser dar uma olhada.

 [1]: http://forecast.io
 [2]: https://developer.forecast.io/
 [3]: https://github.com/igorsantana/tableless-cli
