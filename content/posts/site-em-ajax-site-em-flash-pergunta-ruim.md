---
title: Site em Ajax? Site em Flash? Pergunta ruim.
author: Elcio Ferreira
type: post
date: 2007-09-14
url: /site-em-ajax-site-em-flash-pergunta-ruim/
tweetbackscheck:
  - 1356449607
shorturls:
  - 'a:3:{s:9:"permalink";s:64:"http://tableless.com.br/site-em-ajax-site-em-flash-pergunta-ruim";s:7:"tinyurl";s:26:"http://tinyurl.com/3hj4mwc";s:4:"isgd";s:19:"http://is.gd/lHVTUZ";}'
twittercomments:
  - 'a:20:{i:19484621888552960;s:7:"retweet";i:19458907562844160;s:7:"retweet";i:184681464380665856;s:7:"retweet";i:184659373975552000;s:7:"retweet";i:184657996666769411;s:7:"retweet";i:184657903146385410;s:7:"retweet";i:184656484913774592;s:7:"retweet";i:184656240436183041;s:7:"retweet";i:184655466985570307;s:7:"retweet";i:195591864580190209;s:7:"retweet";i:202956514208649217;s:7:"retweet";i:202896179426631682;s:7:"retweet";i:202861146380840960;s:7:"retweet";i:202858430036328449;s:7:"retweet";i:217332825576308737;s:7:"retweet";i:230752034897412096;s:7:"retweet";i:230741654624169985;s:7:"retweet";i:230741081686409216;s:7:"retweet";i:256110919665459200;s:7:"retweet";i:256108193036517376;s:7:"retweet";}'
tweetcount:
  - 35
dsq_thread_id: 503037463
categories:
  - Artigos
  - Técnicas e Práticas
  - Tecnologia e Tendências
tags:
  - acessibilidade
  - AJAX
  - cotidiano

---
Recebi há poucos dias um email que me deixou intrigado. Um amigo descrevia um site que vai construir em breve e me perguntava: você acha que devo fazê-lo em Ajax? Essa é uma pergunta ruim. A boa pergunta seria: onde, nesse site, eu deveria usar Ajax?

Enquanto os cabeças-pequenas ficam discutindo se devem fazer ou não site em Flash, o Flickr faz um site HTML, com um excelente slideshow em Flash. Deixe-me perguntar: o [YouTube][1] é um &#8220;site em Flash&#8221;? O [Google Video][2]? E o [Charges.com.br][3]? Não? Uma vez que o uso de Flash era inevitável, porque não fizeram logo o site todo em Flash? Porque, amiguinhos, Flash é bom para umas coisas, HTML é bom para outras. Eis uma lição que precisamos aprender: não ao radicalismo, nem oito, nem oitenta.

HTML é a ferramenta ideal se você quer que as pessoas consigam usar o botão voltar, adicionar bookmarks, mandar o endereço para os amigos, selecionar e copiar texto, imprimir a página, encontrar seu conteúdo no Google e etc. Claro, dá para fazer **quase** tudo isso funcionar com Flash ou Ajax, mas com HTML você faz isso sem trabalho nenhum. Está pronto. Basta escrever bom HTML que o resto acontece sozinho. Além disso, HTML tem um custo de desenvolvimento muito reduzido em relação ao Flash. Custo de desenvolvimento, amigos, se mede em horas de trabalho. Gerar formulários, buscas, listagens e relatórios é muito mais fácil em HTML do que em Flash. Se você usa um desses frameworks modernosos então, nem se fala.

Por outro lado, Flash é bom para algumas outras coisas. Por exemplo, se você vai publicar vídeo numa página web, Flash é hoje a opção mais leve, simples e compatível. Ajax, por sua vez, é excelente para evitar refreshs e modifica o modelo de interação com a página. Então não precisamos escolher entre um &#8220;site em Flash&#8221; e um &#8220;site em Ajax&#8221; em detrimento de um &#8220;site comum, em HTML&#8221;.

Para ajudar meu amigo, vou publicar aqui algumas coisas que levo em consideração ao escolher onde usar Javascript e Ajax em um site. Entenda que isso não é uma verdade absoluta, há provavelmente muito mais coisas que você pode levar em consideração, em que eu talvez nunca tenha pensado. Hoje, eu penso no seguinte:

  * **Acessibilidade**: o bom Javascript não quebra a acessibilidade do bom HTML (posso falar mais sobre isso outro dia.) Mas isso pode dar algum trabalho. É preciso levar em conta a importância da acessibilidade para aquela aplicação específica. Sim, acessibilidade pode não ser importante para determinadas aplicações. Por exemplo, o [Google Maps][4] é inacessível a deficientes visuais e a qualquer um que não consiga usar um mouse. Quem aí vai dizer que eles fizeram uma escolha errada? Mas, para a maioria das aplicações, acessibilidade é importante, e é preciso pensar nisso antes de planejar nosso Javascript.
  * **Modelo de interação**: você pode torcer o nariz, mas as pessoas estão acostumadas com o modelo de interação com páginas: clica &#8211; espera um pouquinho &#8211; carrega uma nova página. Elas sabem usar os recursos do navegador feitos para esse modelo, como a barra de endereços, os bookmarks, e o botão voltar. Ah, o que seria de nós sem o botão voltar? Então, eu uso Javascript sem medo onde é claro para as pessoas que elas estão interagindo com a mesma página, no modelo &#8220;aplicação&#8221;. Mas evito usá-lo onde possa dar a impressão de que estão navegando para outra página. Caso contrário, elas vão tentar usar o botão voltar e o resto todo. Você leu certo, &#8220;evito&#8221; não quer dizer que eu nunca faça, só tento ser muito parcimonioso. O nosso [Tutorial de Ajax][5] (e também a [continuação][6]) foi feito em Ajax por motivos didáticos. Navegando nele você vai sentir falta do botão voltar e de poder usar bookmarks.
  * **Custo x benefício**: convenhamos, HTML comum funciona bem para a maioria das coisas, e realmente muito bem para algumas. É a ferramenta ideal, por exemplo, para publicar um site de conteúdo, como esse aqui. Um portal de notícias, um blog, um manual de produto, etc. Usando Ajax você pode fazer com que, ao navegar em um site assim, seja recarregada apenas a parte principal, com o conteúdo. Menus, cabeçalho e rodapé permanecem. Mas será que vale a pena? Trabalhando com padrões web, com seu CSS, javascript e imagens no cache, você vai economizar quanto em banda com esse Ajax? Aqui no Tableless economizaríamos cerca de 15 Kb por página. Por outro lado, teríamos que incluir um bocado de Javascript colocar esse Ajax para funcionar, e manter funcionando coisas como o botão voltar. Sendo que cada visitante vê em média 2 páginas (1,95 para ser mais exato) isso dificilmente representaria alguma economia em banda. E daria um bocado de trabalho.

Logo, meu conselho é: não faça sites &#8220;em Ajax&#8221;, nem sites &#8220;em Flash&#8221;. Faça sites com os padrões web, e use Ajax ou Flash onde isso for realmente ajudar seus usuários.

 [1]: http://www.youtube.com
 [2]: http://video.google.com/
 [3]: http://www.charges.com.br
 [4]: http://maps.google.com/
 [5]: http://tableless.com.br/artigos/ajaxdemo/ "Tutorial de Ajax"
 [6]: http://tableless.com.br/artigos/ajaxdemo2/ "Tutorial de Ajax, parte 2"