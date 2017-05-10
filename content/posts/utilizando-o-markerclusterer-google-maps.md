---
title: Utilizando o MarkerClusterer no Google Maps
author: Raphael Fabeni
type: post
date: 2014-05-07
excerpt: 'Você utiliza bastante o Google Maps em seus projetos? Já aconteceu de vários pontos ficarem muito próximos uns dos outros? Confira o MarkerClusterer, um recurso do Google para casos desse tipo que melhora a visualização do mapa. '
url: /utilizando-o-markerclusterer-google-maps/
dsq_thread_id: 2666248767
categories:
  - JavaScript
  - Técnicas e Práticas
tags:
  - api
  - google
  - googlemaps
  - JavaScript
  - maps

---
Seja você desenvolvedor ou não, temos que admitir o poder do Google Maps. É bem difícil encontrar alguém hoje em dia que não tenha acessado pelo menos uma vez o famoso _Maps_ para ver onde ficava um determinado lugar.

Esses dias me deparei novamente com o excelente artigo do Thulio Philipe sobre a [API do Google Maps V3][1] e resolvi escrever um pouco sobre um recurso chamado **MarkerClusterer**.

## O que é o MarkerClusterer?

Segundo o Google, trata-se de uma solução para o problema de muitos _pontos_ em um mapa. Indo direto ao ponto, ele agrupa pontos (_markers_) que são muito próximos uns dos outros no mapa e renderiza um ponto diferente com o número de ícones agrupados.

Confuso? Visualmente fica mais fácil para explicar. Imagine que tivéssemos um mapa assim:

[<img class="alignnone size-full wp-image-42294" src="http://tableless.com.br/uploads/2014/04/exemplo-antes-MarkerClusterer.png" alt="Exemplo de mapa simples sem a utilização do MarkerClusterer" width="624" height="424" srcset="uploads/2014/04/exemplo-antes-MarkerClusterer.png 624w, uploads/2014/04/exemplo-antes-MarkerClusterer-400x271.png 400w" sizes="(max-width: 624px) 100vw, 624px" />][2]

Temos alguns pontos que são bem próximos uns dos outros enquanto outros são mais distantes. Aplicando o MarkerClusterer ficaria assim:

[<img class="alignnone size-full wp-image-42295" src="http://tableless.com.br/uploads/2014/04/exemplo-depois-MarkerClusterer.png" alt="Exemplo de mapa simples com a utilização do MarkerClusterer" width="624" height="424" srcset="uploads/2014/04/exemplo-depois-MarkerClusterer.png 624w, uploads/2014/04/exemplo-depois-MarkerClusterer-400x271.png 400w" sizes="(max-width: 624px) 100vw, 624px" />][3]

Você pode estar pensando a mesma coisa que pensei a primeira vez que vi o exemplo: _&#8220;Ah, nem precisava agrupar os itens! Tem poucos no mapa!&#8221;_ Pode ser. Agora imagine que tivéssemos um mapa assim:

[<img class="alignnone size-full wp-image-42292" src="http://tableless.com.br/uploads/2014/04/exemplo2-antes-MarkerClusterer.png" alt="Exemplo de mapa mais complexo com a utilização do MarkerClusterer" width="624" height="424" srcset="uploads/2014/04/exemplo2-antes-MarkerClusterer.png 624w, uploads/2014/04/exemplo2-antes-MarkerClusterer-400x271.png 400w" sizes="(max-width: 624px) 100vw, 624px" />][4]

Pois é! De acordo com o próprio Google, um mapa assim acaba por se tornar lento pelo fato de um ponto no mapa ser uma combinação de vários elementos no DOM. Logo, quanto mais pontos no mapa, maior o trabalho no navegador para renderização. O legal é que existe até um [teste de velocidade][5] comparando um mapa com e sem o uso do MarkerClusterer.

Como ficaria com a utilização do MarkerClusterer:

[<img class="alignnone size-full wp-image-42293" src="http://tableless.com.br/uploads/2014/04/exemplo2-depois-MarkerClusterer.png" alt="Exemplo de mapa mais complexo sem a utilização do MarkerClusterer" width="624" height="424" srcset="uploads/2014/04/exemplo2-depois-MarkerClusterer.png 624w, uploads/2014/04/exemplo2-depois-MarkerClusterer-400x271.png 400w" sizes="(max-width: 624px) 100vw, 624px" />][6]

Pode ser até que a questão da **perfomance** não influencie tanto no seu projeto, mas um ponto que deve ser considerado é a **usabilidade** e **experiência do usuário** ao interagir com o mapa. **Se colocar no lugar do usuário** nessa hora é fundamental. Pra localizar determinado ponto no mapa: fica mais fácil com todos visíveis próximos uns dos outros ou agrupados em grupos maiores? Logicamente não existe um certo ou errado pois isso vai variar de projeto para projeto, mas vale a discussão com os membros do time.

As imagens acima foram tiradas [daqui][7] onde também é possível ler mais a respeito desse recurso.

Peguei um exemplo do próprio Google pra podermos visualizar a diferença entre um mapa [sem a utilização do MarkerClusterer][8] e [com a utilização do recurso][9].

Dando uma olhada no código do exemplo com a utilização do recurso temos o seguinte:

**HTML**

<pre class="lang-html">&lt;div id="map-container"&gt;&lt;div id="map"&gt;&lt;/div&gt;&lt;/div&gt;

&lt;!-- Scripts --&gt;
&lt;script src="http://maps.google.com/maps/api/js?sensor=false"&gt;&lt;/script&gt;
&lt;script src="http://google-maps-utility-library-v3.googlecode.com/svn/trunk/markerclusterer/src/data.json"&gt;&lt;/script&gt;
&lt;script src="http://google-maps-utility-library-v3.googlecode.com/svn/trunk/markerclusterer/src/markerclusterer.js"&gt;</pre>

**CSS**

<pre class="lang-css">body { margin: 0; }

#map-container {
  -webkit-box-shadow: rgba(64, 64, 64, 0.5) 0 2px 5px;
     -moz-box-shadow: rgba(64, 64, 64, 0.5) 0 2px 5px;
          box-shadow: rgba(64, 64, 64, 0.1) 0 2px 5px;
  width: 600px;
}

#map {
  width: 600px;
  height: 400px;
}
</pre>

**JS**

<pre class="lang-js">function initialize() {
  var center = new google.maps.LatLng(48.091534, 15.5116439);
  
  var map = new google.maps.Map(document.getElementById('map'), {
    zoom: 3,
    center: center,
    mapTypeId: google.maps.MapTypeId.ROADMAP
  });

  var markers = [];
  for (var i = 0; i &lt; 100; i++) {
    var dataPhoto = data.photos[i];
    var latLng = new google.maps.LatLng(dataPhoto.latitude,
              dataPhoto.longitude);
    var marker = new google.maps.Marker({
      position: latLng
    });
    markers.push(marker);
  }
  var markerCluster = new MarkerClusterer(map, markers);
}

google.maps.event.addDomListener(window, 'load', initialize);
</pre>

A parte de HTML e CSS é bem tranquila e, se pararmos pra olhar, até a parte do JS é de fácil entendimento.

  * Primeiro é criado o objeto do mapa com seus parâmetros e ele é passado à variável `map`.
  * Depois é criado um array vazio que vai armazenar todos os _markers._
  * Logo após é executado um `for` que vai iterar pelo JSON que contém as informações dos pontos e, adicionar cada ponto no array que criamos acima.
  * Nesse momento é criado o objeto _MarkerClusterer_ passando como parâmetros o array contendo todos os pontos do JSON e o mapa.
  * Por fim, o mapa é iniciado no _load_ da página.

É isso pessoal, a idéia era dar uma passada geral sobre o recurso que pode ser útil para alguém que for mexer com mapas que possuem muitos pontos!

 [1]: http://tableless.com.br/api-google-maps-v3/
 [2]: http://tableless.com.br/uploads/2014/04/exemplo-antes-MarkerClusterer.png
 [3]: http://tableless.com.br/uploads/2014/04/exemplo-depois-MarkerClusterer.png
 [4]: http://tableless.com.br/uploads/2014/04/exemplo2-antes-MarkerClusterer.png
 [5]: http://google-maps-utility-library-v3.googlecode.com/svn/trunk/markerclusterer/examples/speed_test_example.html?
 [6]: http://tableless.com.br/uploads/2014/04/exemplo2-depois-MarkerClusterer.png
 [7]: https://developers.google.com/maps/articles/toomanymarkers?hl=pt-br#markerclusterer
 [8]: http://codepen.io/raphaelfabeni/full/hdjgA
 [9]: http://codepen.io/raphaelfabeni/full/zjcFd