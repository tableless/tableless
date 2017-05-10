---
title: GeoURL explicadinho
author: Elcio Ferreira
type: post
date: 2006-05-26
url: /geourl-explicadinho/
tweetbackscheck:
  - 1355624919
shorturls:
  - 'a:3:{s:9:"permalink";s:43:"http://tableless.com.br/geourl-explicadinho";s:7:"tinyurl";s:26:"http://tinyurl.com/3gltv8y";s:4:"isgd";s:19:"http://is.gd/dV1MvG";}'
twittercomments:
  - 'a:0:{}'
dsq_thread_id: 503035389
categories:
  - Geral
tags:
  - Técnicas e Práticas

---
![Extensão GeoURL][1]

Motivado pela nossa nova sala de treinamento, da qual eu falarei em breve no [blog da Visie][2], acabo de atualizar as informações ICBM daqui e do site da [Visie][3].

As informações ICBM permitem localizar seu site num ponto do planeta. Quer ver como funciona? Instale a extensão [GeoURL][4] para o Firefox.

Depois de instalá-la, entre aqui no Tableless e você vai ver um globo colorido na barra de status do Firefox. Clique nele com o botão direito e você vai ver um menu com as opções: [GeoURL][5], [Google Maps][6], [Multimap][7], [flickr nearby][8] e [Maplink][9].

Não divertido? Quer aprender a fazer em seu site? Vou mostrar um passo a passo baseado no que se encontra no [GeoURL.org][10].

  1. **Que coordenadas usar?** Se a página é sobre você, suas coordenadas. Se é sobre algum lugar, as do lugar. Se é de algum cliente seu, as do seu cliente. As coordenadas do servidor que hospeda seu site provavelmente não são muito interessantes.
  2. **Encontre sua localização.** Eu uso o [Google Maps][11] para isso. Nele, encontre sua casa, escritório ou caverna e click em &#8220;Link to this page&#8221;. Na URL que será carregada, copie o parâmetro ll. Ele contém sua latitude e longitude no padrão ICBM. Se não conseguir se encontrar no Google Maps, há uma porção de recursos úteis [na página de resources do GeoURL.org][12].
  3. **Crie as tags meta** na seção head de sua página, assim:
  
    `<meta content="<strong>Coordenadas (que você copia da URL do Google Maps)</strong>" name="ICBM" /><br />
<meta content="<strong>O nome do seu site</strong>" name="DC.title" />`
  
    Se você conseguiu suas coordenadas em outro lugar que não o Google, num GPS por exemplo, basta colocar suas coordenadas em formato decimal, separadas por vígula.
  4. Entre [nesta página][13] e **adicione seu site** ao GeoURL.org.
  5. **Conte aos outros**. Quanto mais gente usar isso, mais interessante a coisa fica.

Curiosidades:

  * ICBM significa &#8220;Intercontinental ballistic missile&#8221;. [Entenda a história][14].
  * Coloquei GeoURL em [meu blog][15] também, apontando para minha humilde morada.
  * Nunca copie as meta tags alheias sem saber o que está fazendo. Há dois sites indicados no GeoURL em [meu antigo escritório][16], inclusive o de uma imobiliária de Minas Gerais.

 [1]: http://tableless.com.br/uploads/2006/05/geourl.jpg
 [2]: http://visie.com.br/blog/
 [3]: http://visie.com.br "Visie Padrões Web - Treinamentos de Web Standards, Tableless, Ajax e Mobilidade"
 [4]: https://addons.mozilla.org/firefox/530/
 [5]: http://geourl.org/near?lat=-23.682205&long=-46.638637
 [6]: http://maps.google.com/?sll=-23.682205,-46.638637
 [7]: http://www.multimap.com/map/browse.cgi?lat=-23.682205&lon=-46.638637&scale=200000&icon=x
 [8]: http://www.allthegoodness.com/projects/map/firefox/index.php?lat=-23.682205&long=-46.638637
 [9]: http://www.mapquest.com/maps/map.adp?latlongtype=decimal&latitude=-23.682205&longitude=-46.638637
 [10]: http://geourl.org/add.html
 [11]: http://maps.google.com/
 [12]: http://geourl.org/resources.html
 [13]: http://geourl.org/ping/
 [14]: http://www.catb.org/~esr/jargon/html/I/ICBM-address.html
 [15]: http://blog.elcio.com.br/ "fechaTag - blog do Elcio"
 [16]: http://geourl.org/near?lat=-23.662&long=-46.638