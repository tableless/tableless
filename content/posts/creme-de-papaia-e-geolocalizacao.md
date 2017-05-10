---
title: Creme de papaia e Geolocalização
author: Reinaldo Ferraz
type: post
date: 2012-11-28
excerpt: Utilize a API de geolocalização de uma maneira mais útil.
url: /creme-de-papaia-e-geolocalizacao/
tweetbackscheck:
  - 1356389720
shorturls:
  - 'a:3:{s:9:"permalink";s:31:"http://tableless.com.br/?p=7408";s:7:"tinyurl";s:26:"http://tinyurl.com/cyd6o5w";s:4:"isgd";s:19:"http://is.gd/hb0OgL";}'
twittercomments:
  - 'a:0:{}'
dsq_thread_id: 948116804
categories:
  - HTML
  - HTML5
tags:
  - geolocalização
  - html5

---
Eu não sou um grande apreciador de doces, mas uma das minhas sobremesas preferidas é o popular [creme de mamão papaia com licor de cassis][1]. Sempre achei que essa era a combinação perfeita para uma sobremesa, especialmente no calor. Mas o mamão papaia é um grande injustiçado. Se você perguntar para qualquer pessoa o nome de uma sobremesa feita com mamão papaia, com certeza a grande maioria vai dizer &#8220;creme de papaia com licor de cassis&#8221;. Falta de criatividade? Pois é. O mesmo acontece com a API de Geolocalização do HTML5.

Sim, a [API de Geolocalização][2] (documentação mantida pelo [W3C Geolocation Working Group][3]) acaba sendo sub-aproveitada em diversos projetos. Faça pesquisa rápida no escritório ou uma busca pelo Google que você vai se deparar com uma grande quantidade de exemplos utilizando Geolocalização baseadas simplesmente na [interface do Google Maps para obter sua localização atual][4]. Uma ótima utilização da API, mas não a única.

Da mesma forma que existem [diversas de receitas de sobremesa utilizando mamão papaia][5], existem diversas aplicações interessantes para o uso da API de Geolocalização. Basta exercitar a criatividade. Não estou dizendo que uma aplicação que identifica minha localização seja inútil. Pelo contrário. Consigo identificar serviços e estabelecimentos próximos de forma muito precisa. Mas podemos ir um pouco além.

Veja este exemplo de [Trip Meter][6]. Utilizando a API de Geolocalização você consegue identificar sua localização inicial e comparar com a localização final e ainda incrementar com o tempo percorrido, pontos turísticos interessantes, etc. Nesse mesmo exemplo, você pode fazer um cruzamento de dados e [calcular a previsão do tempo da cidade que você está passando nesse exato momento][7]. Muito útil para acompanhar todo o seu itinerário de viagem.

Mas e no meu dia-a-dia, como fazer uso da API de Geolocalização de uma forma mais útil? Bem, você pode criar um website de venda de produtos que pode utilizar a localização do usuário para determinar o custo do frete, ou um conversor de moedas extrangeiras por exemplo. Pode ainda criar um sistema para verificar disponibilidade de vagas em hotéis ou aluguel de casas conforme a localização do usuário. Pode parecer estranho uma pessoa chegar a uma cidade sem ter hotel reservado, mas não é. [Uma pesquisa feita em 2010 pelo site MalaPronta.com][8] mostra que 67% dos usuários do site fazem a reserva do hotel com menos de 30 dias de antecedência. Já uma [pesquisa feita pelo website Trip Advisor][9] aponta que grande parte de seus usuários utilizam dispositivos móveis para planejar suas viagens. Ainda sobre viagens, [outra pesquisa mostra que hospedes preferem Wifi do que qualquer outro serviço do hotel][10]. A internet móvel possibilita aplicações inimagináveis na web.

E como anda o suporte a API de Geolocalização nos dispositivos? Bem, seu status atual de [Canditata a Recomendação no W3C][2] pode dar uma idéia. Fazendo uma rápida pesquisa pelo [CanIUse.com][11] podemos ver que mais de 80% dos navegadores pesquisados dão suporte a API (inclusive os browsers de dispositivos móveis). Mas e sobre a minha privacidade? A especificação é bem clara: [_User agents must not send location information to Web sites without the express permission of the user_][12]. A escolha de permitir ou não o compartilhamento da sua localização está nas mãos do usuário.

Fazer uso dos recursos do HTML5 é muito mais simples do que se imagina. Com um pouco de JavaScript você [pode começar a brincar e fazer experimentos com essa API][13] identificando latitude, longitude e integrando com o Google Maps para começar. Esse é apenas o primeiro passo.

Você vai ver que utilizar a API de Geolocalização do HTML5 é mamão com açúcar (Desculpe. Não podia deixar esse trocadilho fora do post).

 [1]: http://guiadacozinha.uol.com.br/receitas/1722-Receita-de-Creme-de-papaia-com-cassis
 [2]: http://www.w3.org/TR/2010/CR-geolocation-API-20100907/
 [3]: http://www.w3.org/2008/geolocation/
 [4]: http://html5demos.com/geo
 [5]: http://cybercook.terra.com.br/resultado.php?palavra1=mamao+papaya&ingredientes=S
 [6]: http://www.html5rocks.com/en/tutorials/geolocation/trip_meter/
 [7]: http://demo.tutorialzine.com/2012/05/weather-forecast-geolocation-jquery/
 [8]: http://www.malapronta.com.br/blog/2010/12/16/como-o-brasileiro-planeja-suas-ferias/
 [9]: http://www.tripadvisor.com/PressCenter-i4720-c1-Press_Releases.html
 [10]: http://travel.usatoday.com/hotels/post/2012/04/survey-reveals-hotels-guests-want-wifi-over-everything-else/666250/1
 [11]: http://caniuse.com/#feat=geolocation
 [12]: http://www.w3.org/TR/2010/CR-geolocation-API-20100907/#security
 [13]: http://dev.opera.com/articles/view/how-to-use-the-w3c-geolocation-api/