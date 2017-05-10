---
title: Está perdido? Geolocalização!
author: Daniel Pereira Camargo
type: post
date: 2013-04-22
excerpt: Entendendo como utilizar a API de Geolocalização (geolocation) do HTML5 com Javascript.
url: /esta-perdido-geolocalizacao/
dsq_thread_id: 1227185682
categories:
  - HTML5
  - JavaScript
  - Técnicas e Práticas
tags:
  - 2013
  - geolocalização
  - geolocation
  - html5
  - JavaScript

---
No passado a localização dos usuários era baseada em IP. A precisão não era lá grande coisa, pois a posição do usuário era baseada em um &#8220;chute&#8221; de acordo com o seu IP. Graças ao HTML5 e sua API de Geolocalização ou Geolocation (já falamos sobre isso aqui no artigo [Creme de papaia e Geolocalização][1]) podemos saber a posição do usuário de forma muito mais precisa e com isso é possível escrever aplicações mais úteis.

## Suporte a geolocalização

Antes de colocar a mão na massa é importante saber os browsers que dão suporte a essa API:

  * Internet Explorer 9 ou superior
  * Firefox 3.5 ou superior
  * Safari 5.0 ou superior
  * Chrome 7.0 ou superior
  * Opera 10.6 ou superior
  * Safari (iOS) 3.2 ou superior
  * Andriod (browser padrão do SO) 2.1 ou superior

## Criando uma aplicação

Um exemplo de aplicação dessa API pode ser um site ou uma web app de uma empresa de guincho para carro ou auto socorro.

Vamos imaginar que o dono dessa empresa quer saber a localização dos seu clientes. Com essa informação em mão ele pode informar inicialmente o cliente se ele atende ou não a região que o cliente se localiza.

### Etapas ou fluxo da aplicação

  1. O cliente acessa o site da empresa de guincho através de seu smartphone (que permita a geolocalização).
  2. O site obtém a posição do usuário.
  3. O site verifica se o cliente está em uma região atendida e caso positivo informa ao cliente o preço do serviço.

## Primeiro passo &#8211; Pegando a posição do usuários

Nosso primeiro trecho de código é bem simples: pegamos a posição de latitude e longitude e mostramos essa informação no console.

Você pode testá-lo aqui <http://jsfiddle.net/pererinha/Mg9T5/>.

<pre class="lang-javascript">function getPosition(){
  // Verifica se o browser do usuario tem suporte a Geolocation
  if ( navigator.geolocation ){
    navigator.geolocation.getCurrentPosition( function( posicao ){
      console.log( posicao.coords.latitude, posicao.coords.longitude );
    } );
  }
}

$( document ).ready( function(){
  getPosition();
} );</pre>

Primeiro verificamos se o browser do usuário tem suporte a Geolocation. Caso positivo chamamos o método **navigator.geolocation.getCurrentPosition** e passamos uma função anônima como parâmetro. Se der tudo certo, a API chama essa função anônima e passa para ela um objeto com as coordenadas do usuário. Mas e algo der errado?

## Segundo passo &#8211; Tratando erros

Agora o nosso código ficará um pouco mais completo, vamos criar uma função que será chamada caso a Geolocalização apresente um erro.

Para testar: <http://jsfiddle.net/pererinha/Y49kd/>.

<pre class="lang-javascript">function getPosition(){
  // Verifica se o browser do usuario tem suporte a geolocation
  if ( navigator.geolocation ){
    navigator.geolocation.getCurrentPosition( 

    // sucesso! 
    function( posicao ){
      console.log( posicao.coords.latitude, posicao.coords.longitude );
    },

    // erro 🙁
    function ( erro ){
      var erroDescricao = 'Ops, ';
      switch( erro.code ) {
        case erro.PERMISSION_DENIED:
          erroDescricao += 'usuário não autorizou a Geolocation.';
        break;
        case erro.POSITION_UNAVAILABLE:
          erroDescricao += 'localização indisponível.';
        break;
        case erro.TIMEOUT:
          erroDescricao += 'tempo expirado.';
        break;
        case erro.UNKNOWN_ERROR:
         erroDescricao += 'não sei o que foi, mas deu erro!';
        break;
      }
      console.log( erroDescricao )
    }
   );
  }
}

$( document ).ready( function(){
  getPosition();
} );</pre>

### Terceiro passo &#8211; Juntando tudo

Bom, já deu para entender como funciona o tal do Geolocation. Agora vamos organizar melhor esse código e começar a utilizar os dados da posição do usuário.

Olha como ficou o script final. Para testar <http://jsfiddle.net/pererinha/dKSY5/>.

<pre class="lang-javascript">// Objeto oficina com os dados da oficina
var Oficina = {
  posicao : {
    latitude : -25.435946,
    longitude: -49.273365   
  },
  valorPorKM : 5,
  distanciaMaxima : 15,

  // Funcao que ira verificar se o cliente esta por perto e ira calcular o valor do servico
  calculaOPreco : function( posicao ){
  var distancia = Distancia.distanciaEntreDoisPontos( posicao, this.posicao );
  // Verifica se o cliente nao estah muito longe
  if( distancia &lt;= this.distanciaMaxima ){
    // Duas casas decimais e troca o . por ,
    var valor = ( this.valorPorKM * distancia ).toFixed( 2 ).toString().replace( '.', ',' );
    if ( confirm( 'O custo do guincho será R$ ' + valor + '. Posso mandar?' ) ){
      alert( 'O guincho chegará em alguns minutos!' );
    }
  } else {
    // Somente duas cadas decimais ja eh o suficiente
    distancia = distancia.toFixed( 2 );
    alert( 'Ops, você está muito longe, a distância máxima que atendemos é ' +  this.distanciaMaxima + ' KM e você está há ' + distancia + ' KM!' );
  }
  }
};

// Objeto localizacao, aqui estao as funcoes para trabalhar com a api geolocation
var Localizacao = {

  // Inicia
  inicia : function(){

  // Funcao que serah chamada quando o browser retornar a posicao do usuario
  var sucesso = function( posicao ){
    Oficina.calculaOPreco( posicao.coords );
  };

  // Funcao que serah chamada caso de algum erro nesse processo de obter a posicao
  var erro = function( erro ){
    var erroDescricao = 'Ops, ';
    switch( erro.code ) {
      case erro.PERMISSION_DENIED:
        erroDescricao += 'usuário não autorizou a Geolocation.';
      break;
      case erro.POSITION_UNAVAILABLE:
        erroDescricao += 'localização indisponível.';
      break;
      case erro.TIMEOUT:
        erroDescricao += 'tempo expirado.';
      break;
      case erro.UNKNOWN_ERROR:
        erroDescricao += 'não sei o que foi, mas deu erro!';
      break;
    }
    alert( erroDescricao )
  };

  // Verifica se o browser do usuario tem suporte a geolocation
  if ( navigator.geolocation ){
    navigator.geolocation.getCurrentPosition( sucesso, erro );
  } else {
    erro();
  }
  }
};

// Objeto para calcular a distancia entre dois pontos
var Distancia = {
  distanciaEntreDoisPontos : function( pontoInicial, pontoFinal ){
    var R = 6371; // Radio da Terra
    var dLat = this.graus2Radianos( pontoFinal.latitude - pontoInicial.latitude ); 
    var dLon = this.graus2Radianos( pontoFinal.longitude - pontoInicial.longitude ); 
    var a = Math.sin( dLat/2 ) * Math.sin( dLat/2 ) + Math.cos( this.graus2Radianos( pontoInicial.latitude ) ) * Math.cos( this.graus2Radianos( pontoFinal.latitude ) ) * Math.sin( dLon/2 ) * Math.sin( dLon/2 ); 
    var c = 2 * Math.atan2( Math.sqrt( a ), Math.sqrt( 1-a ) ); 
    var d = R * c; 
    return d;
  },
  graus2Radianos : function( graus ){
    return graus * ( Math.PI/180 )
  }
};

$( document ).ready( function(){
  Localizacao.inicia();
} );</pre>

Nessa última versão o código já está mais organizado. E também já temos alguns objetos novos. O código está todo documentado e está bem simples de entender.

Temos três objetos:

  * Oficina
  * Localizacao
  * Distancia

### Objeto Oficina

Esse objeto contém as informações sobre a oficina e um método que verifica a distância do cliente e o preço do serviço.

### Objeto Localizacao

Esse objeto contém as os métodos para trabalharmos com a api de Geolocation, do primeiro e segundo passo.

### Objeto Distancia

Esse objeto tem um método importante que é o **distanciaEntreDoisPontos** esse método calcula a distância entre dois pontos e retorna o valor em kilômetros.

Adaptado dessa formula <http://stackoverflow.com/questions/27928/how-do-i-calculate-distance-between-two-latitude-longitude-points>.

# Conclusão

Isso seria o básico para começar a brincar com essa api tão legal que é o Geolocation.

Dois plugins, para o Chrome, que podem te ajudar bastante.

  * Geo Location Chrome Extension: Esse plugin te mostra a sua posição. <https://chrome.google.com/webstore/detail/ebpepkmcecplhjpdfiojfjbjofekjhcp>
  * Manual Geolocation: Com esse plugin você pode definir a sua localização manualmente. <https://chrome.google.com/webstore/detail/manual-geolocation/mfodligkojepnddfhkbkodbamcagfhlo>

Em um próximo artigo veremos sobre conseguir a latitude e longitude do usuário a partir de seu endereço e mais alguns parâmetros que podemos utilizar com o método **navigator.geolocation.getCurrentPosition**.

 [1]: http://tableless.com.br/creme-de-papaia-e-geolocalizacao/