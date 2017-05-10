---
title: Navegabilidade em Dispositivos Móveis
author: Talita Pagani
type: post
date: 2010-11-17
excerpt: Minimizar a quantidade de informações e o esforço de interação com os elementos de interface. Estes são os princípios-chave que para que websites possam ser utilizados da melhor forma em dispositivos móveis.
url: /navegabilidade-em-dispositivos-moveis/
aktt_notify_twitter:
  - yes
tweetbackscheck:
  - 1356439422
shorturls:
  - 'a:3:{s:9:"permalink";s:61:"http://tableless.com.br/navegabilidade-em-dispositivos-moveis";s:7:"tinyurl";s:26:"http://tinyurl.com/44zm5k4";s:4:"isgd";s:19:"http://is.gd/udAiyH";}'
twittercomments:
  - 'a:12:{i:10039589313974272;s:7:"retweet";i:10038945760935938;s:7:"retweet";i:10036494471274496;s:7:"retweet";i:131118261176770561;s:7:"retweet";i:131117213972312064;s:7:"retweet";i:131089157580800002;s:7:"retweet";i:131086710468644864;s:7:"retweet";i:131082793206812672;s:7:"retweet";i:131055918484946944;s:7:"retweet";i:131055784187543553;s:7:"retweet";i:131055425318694912;s:7:"retweet";i:131054363467714561;s:7:"retweet";}'
tweetcount:
  - 29
dsq_thread_id: 503039719
categories:
  - Acessibilidade
  - Artigos
  - Mobile
tags:
  - acessibilidade
  - CSS
  - html
  - mobile
  - xhtml

---
Um dos principais desafios ao projetar um site ou um sistema web para mobile é o tamanho em KB do conteúdo. Internet pelo celular ainda é cobrada por KB utilizados por muitas operadoras e o custo ainda é muito elevado no Brasil. Além disso, temos um espaço muito pequeno para mostrar o conteúdo. Mesmo os melhores _smartphones touch-screen_ têm telas relativamente pequenas se compararmos com um monitor convencional ou notebook, o que cria um esforço de interação maior.

O princípio de acessibilidade para sites visualizados em dispositivos móveis é a apresentação sucinta de informações e para isso uma diretriz fundamental é utilizar corretamente as tags do HTML e fazer uma marcação adequada e semântica. Por exemplo, utilizar corretamente as tags de cabeçalho para estruturar títulos, _P_ para parágrafos e outras recomendações que são comuns também aos sites convencionais.

Porém, deve ser minimizado o uso de tags, utilizando apenas as que forem necessárias. Por termos um conteúdo resumido e mais verticalizado, não há necessidade de muitas tags para estruturação e posicionamento do conteúdo. E, nesse ponto, entra outra questão: muitos sites disponibilizam o mesmo layout para web e para mobile, apenas acrescentando uma folha de estilo com atributo _mediatype=”handheld”_ para adaptar a apresentação do conteúdo aos dispositivos móveis.

O mais adequado é prover uma página alternativa, com HTML e CSS próprios para a visualização neste tipo de dispositivo. Existem verificações server-side (depende da linguagem utilizada) que permitem identificar se o usuário está acessando o site a partir de um dispositivo móvel e então fazer o redirecionamento para a versão mobile.

Desenvolver uma versão mobile de seu website implica também em reduzir as informações que são apresentadas, disponibilizando apenas textos, links e imagens que sejam mais relevantes. Fazendo isto, reduzimos a densidade informacional e possibilitamos que os usuários encontrem mais facilmente as informações. Além disso, conseguimos reduzir o tráfego de conteúdo por diminuir o tamanho da página.

Outras dicas importantes sobre acessibilidade (e também usabilidade) para dispositivos móveis:

  * Evite o uso de javascript e flash, ainda há dispositivos que não suportam corretamente estes elementos. Mesmo para dispositivos que suportem scripts, eles devem ser utilizados apenas caso não haja outra forma de realizar uma determinada função. Scripts aumentam o consumo de energia.
  * O título das páginas deve ser curto e descritivo, para que o usuário identifique a página que ele está;
  * Prover, sempre que possível, pré-seleção para valores em campos de formulário, pois isto minimiza a quantidade de entrada de dados que o usuário deve fazer.
  * Quando possível, utilizar também listas de seleção, radio buttons e outros controles que não requerem digitação.
  * Garantir que cada formulário presente tenha um botão submit, evitando submissões por de javascript através de um evento no campo de formulário.
  * Reduza a quantidade de seletores e propriedades em seu CSS e, se possível, coloque declarações em uma única linha para reduzir o tamanho dos arquivos. Você também pode optar por utilizar script server-side para a compressão das folhas de estilo.
  * Para os textos, evite medidas absolutas e em pixels, permitindo que os navegadores ajustem o conteúdo à tela.  No CSS, utilize porcentagens e medidas relativas como _em_, _ex_, _bolder_, _larger_ e _thick_.
  * Especificar as dimensões exatas da imagem em pixels ajuda o navegador a continuar o carregamento da página e evitar o recarregamento depois da página ter sido exibida por completo. Os dispositivos podem perceber melhor as intenções do desenvolvedor se as margens, bordas e espaçamentos forem especificados em pixels.

Algumas destas recomendações foram obtidas no site <a title="Ready.mobi" href="http://ready.mobi/" target="_blank">ready.mobi</a> com base em diretrizes do W3C.