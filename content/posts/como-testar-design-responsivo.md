---
title: Como testar design responsivo
author: Dani Guerrato
type: post
date: 2013-10-16
excerpt: 'Conheça algumas ferramentas essenciais para testar o seu layout, aprenda a sincronizar dispositivos móveis, organize sua própria biblioteca de testes e saiba o que fazer caso você não possua um smartphone. '
url: /como-testar-design-responsivo/
dsq_thread_id: 1863790969
categories:
  - Artigos
tags:
  - design responsivo
  - responsive

---
Você já sabe como criar layouts e desenvolver um site responsivo. Na verdade seu projeto já está quase pronto. A última etapa é testar o funcionamento! Existem diversas maneira de garantir a efetividade do layout. A primeira delas, e mais óbvia, é testando ao vivo em diversos dispositivos. Em um mundo ideal você deveria testar o seu layout na maior quantidade de aparelhos, browsers e sistemas operacionais possíveis! Alias, você pode até ser fanático por isto e incomodar todo amigo que ver com um celular diferente com um &#8220;posso testar uma coisa rapidinho?&#8221;. Diga que leu isto em um artigo. É pelo bem do design! Ok, talvez nem tanto. Se quiser manter seus amigos E garantir que o seu layout está bacana em diferentes dispositivos você pode utilizar algumas das soluções abaixo.

## Bibliotecas de Dispositivos

Se você trabalhar em uma empresa grande (ou tiver grana sobrando) talvez seja bacana investir em um laboratório de testes com uma biblioteca de dispositivos. Este é um conceito comum no exterior e alguns locais são até gratuitos para a utilização da comunidade. Se você for sortudo e estiver em algum destas cidades de uma olhada nestas bibliotecas aqui:

[Device Lab][1] &#8211; Rio de Janeiro, Brasil
  
[Clearleft][2] &#8211; Brighton, Inglaterra
  
[Helsinki Open Device Lab][3] &#8211; Helsinque, Finlândia
  
[Mobile Portland][4]  &#8211; Portland, EUA
  
[Ottawa Open Device Lab][5] &#8211; Ottawa, Canadá

Através do site [Open Device Lab][6] é possível procurar o laboratório mais perto de você. Infelizmente no Brasil só encontrei no Rio de Janeiro. Tomara que a idéia se espalhe! Só para ficar com um gostinho a imagem abaixo é do Helsinki Open Device Lab.

[<img class="alignnone size-full wp-image-39216" alt="helsinki-open-device-lab" src="http://tableless.com.br/uploads/2013/10/helsinki-open-device-lab.jpg" width="660" height="400" srcset="uploads/2013/10/helsinki-open-device-lab.jpg 660w, uploads/2013/10/helsinki-open-device-lab-277x168.jpg 277w, uploads/2013/10/helsinki-open-device-lab-511x310.jpg 511w" sizes="(max-width: 660px) 100vw, 660px" />][7]

Artigos interessantes sobre como montar seu próprio laboratório:
  
[LabUp][8]
  
[Establishing An Open Device Lab][9]
  
[Test on Real Mobile Devices without Breaking the Bank][10]
  
[How to Build a Device Lab][11]

Se você tem o espaço disponível e quiser se aventurar na construção da sua própria biblioteca lembre-se de pensar também na estrutura do local como cabeamento, hub USB, prateleiras, roteador wi-fi e segurança. Existem até empresas como a [Vanamco][12] que oferecem suportes especialmente projetados para o dia-a-dia de desenvolvimento.

[<img class="alignnone size-full wp-image-39215" alt="device-lab-stand" src="http://tableless.com.br/uploads/2013/10/device-lab-stand.jpg" width="660" height="400" srcset="uploads/2013/10/device-lab-stand.jpg 660w, uploads/2013/10/device-lab-stand-277x168.jpg 277w, uploads/2013/10/device-lab-stand-511x310.jpg 511w" sizes="(max-width: 660px) 100vw, 660px" />][13]

Ou você pode entrar em uma onda faça você mesmo e improvisar a estrutura. Se precisar de inspiração a [Adobe Device Wall][14] possui um passo-a-passo recheado de fotos.

[<img class="alignnone size-full wp-image-39213" alt="adobe-device-wall" src="http://tableless.com.br/uploads/2013/10/adobe-device-wall.jpg" width="660" height="400" srcset="uploads/2013/10/adobe-device-wall.jpg 660w, uploads/2013/10/adobe-device-wall-277x168.jpg 277w, uploads/2013/10/adobe-device-wall-511x310.jpg 511w" sizes="(max-width: 660px) 100vw, 660px" />][15]

Mesmo que você não tenha grana para montar uma estrutura como esta na sua empresa, se estiver em uma equipe grande é provável que tenha uma certa variedade de dispositivos entre todos os profissionais presentes&#8230; Aquele celular velhão ou console portátil que você ia jogar fora pode ser útil para testes, mesmo com a tela rachada ao meio! E assim aos poucos você pode construir uma mini biblioteca. Mesmo que você não possua aparelhos antigos para dispor (ou não queira se separar deles!) pode ser legal instituir um dia da semana na empresa onde todos levem seus aparelhos e emprestam para os colegas testarem por alguns minutinhos. Saber trabalhar em grupo as vezes inclui emprestar brinquedos… Como última opção existem empresas que prestam serviço de locação de aparelhos. Por cerca de R$15 por dia é possível alugar um iPad ou Galaxy Tab em São Paulo, por exemplo. Considerando quanto você pode potencialmente lucrar com design responsivo 15 reais é um investimento bem baixo&#8230;

## Simuladores

Se uma biblioteca de dispositivos ainda for um sonho distante você pode recorrer a um emulador online. Não vou mentir para você. Nenhum é 100% confiável. Mas é definitivamente melhor do que confiar na sorte, certo?

### Screenfly

O [Screenfly][16] possui uma grande gama de aparelhos (incluindo até televisores). É possível compartilhar as capturas de tela, modificar a orientação e determinar manualmente um breakpoint. A régua de pixels também quebra um galho. Para utilizar o sistema basta digitar a URL que o Screenfly cuida do resto.

[<img class="alignnone size-full wp-image-39220" alt="screenfly" src="http://tableless.com.br/uploads/2013/10/screenfly.jpg" width="660" height="400" srcset="uploads/2013/10/screenfly.jpg 660w, uploads/2013/10/screenfly-277x168.jpg 277w, uploads/2013/10/screenfly-511x310.jpg 511w" sizes="(max-width: 660px) 100vw, 660px" />][17]

### Responsinator

O [Responsinator][18] funciona de maneira semelhante ao Screenfly. Basta digitar o endereço do site que a ferramenta simula o layout em alguns aparelhos como iPhone, iPad, Android e Kindle . Tem também um [bookmarklet][19] útil para facilitar ainda mais o processo. É possível testar sites fixos utilizando o sufixo **&fixed_width=x** depois da URL. O serviço ainda conta com uma função premium. Por $6 mensais é possível ter um simulador customizado.

[<img class="alignnone size-full wp-image-39228" alt="responsinator-home" src="http://tableless.com.br/uploads/2013/10/responsinator-home.jpg" width="660" height="400" srcset="uploads/2013/10/responsinator-home.jpg 660w, uploads/2013/10/responsinator-home-277x168.jpg 277w, uploads/2013/10/responsinator-home-511x310.jpg 511w" sizes="(max-width: 660px) 100vw, 660px" />][20]

### Mobile Emulators & Simulators: The Ultimate Guide

Este [site][21] apresenta uma curadoria de emuladores para Windows, Mac e Linux que você pode instalar no seu computador e testar aparelhos diferentes. Não é tão prático como simplesmente digitar uma URL, mas o resultado é mais fiel e é a única maneira de testar funcionalidades como acelerômetro e giroscópio.

## Outras ferramentas

Não é só de emuladores que vive um desenvolvedor focado em design responsivo. É necessário ter mais alguns truques na manga. Estas ferramentas vão facilitar a sua vida e ajudar a cumprir a deadline sem crise.

### Adobe Edge Inspect

[<img class="alignnone size-full wp-image-39214" alt="adobe-edge-inspect" src="http://tableless.com.br/uploads/2013/10/adobe-edge-inspect.jpg" width="660" height="400" srcset="uploads/2013/10/adobe-edge-inspect.jpg 660w, uploads/2013/10/adobe-edge-inspect-277x168.jpg 277w, uploads/2013/10/adobe-edge-inspect-511x310.jpg 511w" sizes="(max-width: 660px) 100vw, 660px" />][22]

O processo de desenvolvimento responsivo pode ser longo e tedioso. A cada mudança é necessário escrever o código em um computador, salvar, realizar upload em um servidor, pegar o dispositivo que você deseja testar, digitar a URL e verificar se deu certo. E recomeçar esta cadeia a cada vez! O [Adobe Edge Inspect ][23]torna este processo muito mais rápido. O software basicamente sincroniza aparelhos com o sistema Android e / ou iOS com o Google Chrome de um desktop através de uma rede sem fio. Isto significa que você pode desenvolver e fazer uso de funções do developers tools, por exemplo, e ver as mudanças em tempo real. Tudo isto inclusive através do localhost. Vale a pena conferir a ferramenta, principalmente por que já vem inclusa na suite Creative Cloud.

### Viewport Resizer

[<img class="alignnone size-full wp-image-39221" alt="viewport-resizer" src="http://tableless.com.br/uploads/2013/10/viewport-resizer.jpg" width="660" height="400" srcset="uploads/2013/10/viewport-resizer.jpg 660w, uploads/2013/10/viewport-resizer-277x168.jpg 277w, uploads/2013/10/viewport-resizer-511x310.jpg 511w" sizes="(max-width: 660px) 100vw, 660px" />][24]

Este [bookmarklet][25] adiciona uma barra de opções onde é possível rapidamente trocar a largura da tela de acordo com os aparelhos mais populares, modificar a orientação, verificar o tamanho atual da janela ou escolher manualmente uma medida em pixels.

Para quem nunca utilizou algo do tipo: bookmarklets são pequenos programinhas em javascript que são armazenados no formato de link favorito do seu navegador e servem para realizar rapidamente uma determinada ação. Para utilizar basta adicionar um bookmarklet a sua barra de favoritos, navegar até o site que você deseja realizar a ação e clicar no bookmarklet.

### Screensiz.es

[<img class="alignnone size-full wp-image-39223" alt="screensizes" src="http://tableless.com.br/uploads/2013/10/screensizes.jpg" width="660" height="400" srcset="uploads/2013/10/screensizes.jpg 660w, uploads/2013/10/screensizes-277x168.jpg 277w, uploads/2013/10/screensizes-511x310.jpg 511w" sizes="(max-width: 660px) 100vw, 660px" />][26]

O [Screensiz.es][27] é basicamente uma tabela gigante de tamanhos de dispositivos divididos entre smartphones, tablets e monitores. É possível verificar resolução, densidade de pixels e proporção de cada aparelho. Útil para projetar Media Queries mais específicos.

### PageSpeed Insights

[<img class="alignnone size-full wp-image-39218" alt="page-speed-insights" src="http://tableless.com.br/uploads/2013/10/page-speed-insights.jpg" width="660" height="400" srcset="uploads/2013/10/page-speed-insights.jpg 660w, uploads/2013/10/page-speed-insights-277x168.jpg 277w, uploads/2013/10/page-speed-insights-511x310.jpg 511w" sizes="(max-width: 660px) 100vw, 660px" />][28]

O aspecto visual é apenas a ponta do iceberg. A velocidade de carregamento também tem um grande impacto na aceitação de um site e, com algumas dicas rápidas, é possível melhorar bastante o carregamento de um site responsivo. O [PageSpeed Insights][29] da Google dá uma nota de 0 a 100 e oferece algumas sugestões para otimizar o loading.

### I am mobile

[<img class="alignnone size-full wp-image-39217" alt="i-a-mobile" src="http://tableless.com.br/uploads/2013/10/i-a-mobile.jpg" width="660" height="400" srcset="uploads/2013/10/i-a-mobile.jpg 660w, uploads/2013/10/i-a-mobile-277x168.jpg 277w, uploads/2013/10/i-a-mobile-511x310.jpg 511w" sizes="(max-width: 660px) 100vw, 660px" />][30]

Descubra o quanto o seu site é amigável com dispositivos móveis em um ranking the 0 a 8. Esta [ferramenta online][31] dá uma nota para o layout de acordo com alguns padrões como presença da metatag viewport, utilização de touch-icons e outras tags amigáveis. Não leve o resultado a ferro e fogo. Algumas das opções são meio genéricas e subjetivas, mas vale a pena mesmo assim conferir as sugestões. Otimizar nunca é demais.

### Conclusão

Seguindo estas dicas é possível garantir um ótimo resultado em múltiplas plataformas. E vocês? Que ferramenta costumam utilizar para testar design responsivo? Deixem sugestões nos comentários e até a próxima!

 [1]: http://www.devicelab.com.br/ "Device Lab"
 [2]: http://clearleft.com/testlab/ "Clearleft"
 [3]: http://devicelab.fi/ "Device Lab"
 [4]: http://mobileportland.com/device-lab "Mobile Portland"
 [5]: http://www.bv02.com/device-lab "http://www.bv02.com/device-lab"
 [6]: http://opendevicelab.com/ "Open Device Lab"
 [7]: http://devicelab.fi/
 [8]: http://lab-up.org/ "LabUp"
 [9]: http://mobile.smashingmagazine.com/2012/09/24/establishing-an-open-device-lab/ "Establishing An Open Device Lab"
 [10]: http://bradfrostweb.com/blog/mobile/test-on-real-mobile-devices-without-breaking-the-bank/ "Test on Real Mobile Devices without Breaking the Bank"
 [11]: http://dmolsen.com/2012/06/26/how-to-build-a-device-lab-part-1/ "How to Build a Device Lab"
 [12]: http://devicelab.vanamco.com/ "Device Lab"
 [13]: http://devicelab.vanamco.com/
 [14]: http://www.chadmanley.ca/ADOBE-DEVICE-WALL "Adobe Device Wall"
 [15]: http://www.chadmanley.ca/ADOBE-DEVICE-WALL
 [16]: http://quirktools.com/screenfly/ "Screenfly"
 [17]: http://quirktools.com/screenfly/
 [18]: http://www.responsinator.com/ "Responsinator"
 [19]: http://www.responsinator.com/about/ "Responsinator - About"
 [20]: http://www.responsinator.com/
 [21]: http://www.mobilexweb.com/emulators "Emulators"
 [22]: http://html.adobe.com/edge/inspect/
 [23]: http://html.adobe.com/edge/inspect/ "Adobe Edge Inspect"
 [24]: http://lab.maltewassermann.com/viewport-resizer/
 [25]: http://lab.maltewassermann.com/viewport-resizer/ "Viewport Resizer"
 [26]: http://screensiz.es/
 [27]: http://screensiz.es/ "Screensiz.es"
 [28]: https://developers.google.com/speed/pagespeed/insights/
 [29]: https://developers.google.com/speed/pagespeed/insights/ "Insights"
 [30]: http://www.iammobile.co.uk/
 [31]: http://www.iammobile.co.uk/ "I am mobile"