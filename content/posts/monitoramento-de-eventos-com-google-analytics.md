---
title: Monitoramento de eventos com Google Analytics
author: Fabiano de Lima Abreu
type: post
date: 2015-03-06
excerpt: Aprenda a mensurar a interação dos usuários no seu site através do Google Analytics.
url: /monitoramento-de-eventos-com-google-analytics/
categories:
  - SEO
tags:
  - eventos
  - google analytics
  - monitorar

---
Você gastou um &#8220;tempão&#8221; construindo algumas coisas novas legais em seu site, mas como é que você pode ter certeza que seus visitantes estão interagindo com elas? Este artigo abordará justamente isso.

Primeiramente para quem ainda não conhece ou possa interessar, segue uma breve descrição sobre o Google Analytics: O [Google Analytics][1] é uma Application Programming Interface (API) ou, em português, Interface de Programação de Aplicativos. Essa ferramenta é gratuita e disponibilizada pelo Google para ser usada pelos desenvolvedores de sites e profissionais de Search Engine Optimization (SEO), que em português significa Otimização para Motores de Busca. Com o Analytics você consegue acompanhar detalhes sobre a visitação e estatísticas do seu site, além de tornar possível a verificação de variáveis interessantes, como a quantidade de visitas por dia ou então as Keywords que estão sendo relacionadas ao seu site. Todos os dados são extraídos diariamente das estatísticas do próprio Google. Atualmente, o Google Analytics é a ferramenta de Otimização de Sites mais utilizada no mundo.

Partindo do ponto de que você já tenha ativado o Google Analytics no seu site (<a href="https://developers.google.com/analytics/devguides/collection/analyticsjs/advanced?hl=pt-br" target="_blank">Se não souber ativar acesse a página oficial do google analytics para desenvolvedores</a>) , vamos ao que interessa:

## Configuração

Não há nenhuma configuração adicional requerida no Google Analytics para receber eventos, apenas tenha seu código **GA** na página e adicione o código ga abaixo para os eventos HTML desejados e PRONTO! você já está &#8220;rastreando&#8221;!

**Nota**: _na versão gratuita do Google Analytics você está limitado a 10 milhões de eventos no mês. Esta é a maneira mais que suficiente para a maioria dos sites, mas pode esgota-los rápido se você adicionar um monte de onmouseover e eventos OnScroll._

## Estrutura de código do acompanhamento de eventos

<pre>ga('track','event', 'categoria', 'acao', 'rotulo opcional');</pre>

  * &#8216;**track**&#8216; &#8211; Este é o método javascript que realizada a chamada desta função.
  * &#8216;**event**&#8216; &#8211; Parâmetro para a função em &#8216;_track_&#8216;.
  * &#8216;**categoria**&#8216; &#8211; A categoria que você deseja mostrar. Use algo amplo como links externos, laços sociais, imagens, vídeos ou formulário.
  * &#8216;**acao**&#8216; &#8211; Esta é a ação que ocorreu; algo que o usuário fez que você está rastreando. Para a propriedade &#8220;acao&#8221; use: clicado, copia&#8230; qualquer coisa que você esteja rastreando do usuário.
  * ‘**rotulo opcional**’ – Este é um campo opcional, mas quando você começa a rastrear uma grande quantidade de coisas, você quer ser capaz de segmenta-las. Para esta finalidade, pense neste campo como uma categoria especifica, por exemplo, facebook, imagem superior&#8230;

## Trabalhando com eventos

Agora, digamos que você tem uma landing page e a meta dela é que as pessoas ao acessa-la, baixem um papel de parede, vamos mapear quantas vezes as pessoas clicam no link de download:

Podemos tanto fazer da forma mais simples através da chamada do javascript _inline_ em nosso html:

<pre>&lt;a href="/walpaper.jpg" onclick="ga('send', 'event', 'link','click', 'Download clicado');" id="download"&gt;Download&lt;/a&gt;</pre>

Ou podemos realizar a chamada através de eventos via jquery:

<pre>jQuery(document).ready(function ($) {
   $('#download').on('click', function() {
     ga('send', 'event', 'link','click', 'Download clicado');
   });
});</pre>

Uma vez implementado, você pode checar as &#8220;tracks&#8221; dos seus eventos corretamente após 24hr, em: **Comportamento** > **Eventos** dentro do google analytics, assim como a imagem abaixo ilustra:

[<img class="alignleft wp-image-47502 size-full" src="http://tableless.com.br/uploads/2015/03/custom-event1-658x415.jpg" alt="relatório de eventos" width="658" height="415" srcset="uploads/2015/03/custom-event1-658x415.jpg 658w, uploads/2015/03/custom-event1-658x415-220x139.jpg 220w, uploads/2015/03/custom-event1-658x415-400x252.jpg 400w" sizes="(max-width: 658px) 100vw, 658px" />][2]

## 

## 

## 

## 

## 

## 

## 

## 

## Concluindo

São incontáveis os ganhos, principalmente no âmbito da análise ao monitorarmos os eventos dentro da página e gerar por exemplo um relatório quantitativo com tais dados no final de um determinado período. Assim como foi digo no post, Temos  uma grande quantidade de eventos disponíveis no mês, o suficiente para mensurar com qualidade todos ou os principais eventos que possam ocorrer em nosso site.

## Referências

<a title="How to track custom click/touch events in Google Universal Analytics" href="http://www.creare.co.uk/track-custom-events-universal-ga" target="_blank">How to track custom click/touch events in Google Universal Analytics</a>
  
<a title="Event tracking in google analytics explained for non-coders" href="http://www.seerinteractive.com/blog/event-tracking-explained/" target="_blank">Event tracking in google analytics explained for non-coders</a>
  
<a title="Configuração avançada - acompanhamento da Web " href="https://developers.google.com/analytics/devguides/collection/analyticsjs/advanced?hl=pt-br" target="_blank">Configuração avançada &#8211; acompanhamento da Web </a>

 [1]: http://google.com/analytics
 [2]: http://tableless.com.br/uploads/2015/03/custom-event1-658x415.jpg