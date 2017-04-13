---
title: Qualidade de Imagens e densidade de pixels
author: Diego Eis
type: post
date: 2012-03-26
excerpt: Entenda melhor sobre densidade de pixels em aparelhos como o iPhone 4 e outros dispositivos que carregam Android.
url: /qualidade-de-imagens-e-densidade-de-pixels/
categories:
  - Acessibilidade
  - Mercado e Comportamento
  - Mobile
  - Técnicas e Práticas
  - Tecnologia e Tendências
tags:
  - 2012
  - acessibilidade
  - CSS3
  - desenvolvimento web
  - design
  - dispositivos moveis
  - Na Prática
  - tableless

---
Você se lembra quando planejavamos nossos layouts para resoluções acima de 1024? Chega ser engraçado lembrar que um dia fizemos websites para 640&#215;480, pensando que a resolução de 1024&#215;768 eram a minoria dos usuários. Os tempos mudaram e naturalmente diversas outras resoluções apareceram por conta de novos dispositivos, melhores monitores e etc. Acontece que na web nada é tão fácil assim. A gente se livra de um problema, mas aparece outro no lugar.

Este ano eu estou trabalhando a maior parte do tempo em um monitor fullHD. Notei uma diferença gritante ao digitar código pela primeira vez em um monitor desses. E não são apenas os monitores que estão mudando para uma resolução decente. Também, seguindo o ciclo natural, dispositivos menores estão recebendo a dádiva de ter a alta resolução em suas telas. E isso, meu caro, é uma dádiva para o usuário, para você é mais trabalho. 😉

### Pixels não são mais como eram antigamente

Na minha época de escola &#8211; nem tanto tempo assim &#8211; os professores me ensinaram que o átomo era indivisível. Era incrível por que eu, como criança, me divertia tentando entender como algo poderia ser tão pequeno que não pudesse ser partido ao meio, ficando menor&#8230; Mas aí eu descobri que os prótons, os elentrons e outras partículas subatomicas existiam também&#8230; 

A mesma coisa aconteceu com o pixel. O pixel sempre representou a menor unidade da sua tela. Para os designers, o pixel é a unidade central. É onde tudo se baseia: medidas, tamanhos, alinhamentos etc&#8230; Mas o pixel não é mais como era antigamente.

Com o advento das telas HD em aparelhos móveis, o conceito de pixel mudou um <del>pouco</del> muito. Quando a tela retina display do iPhone 4 foi lançada o queixo de todo mundo caiu. A Apple conseguiu apertar quatro pixels onde apenas caberia um. Logo o pixel pode ser definido como a menor unidade na tela, como você já conhece ou pode ser baseada em uma unidade chamada hoje em dia de &#8220;pixel referência&#8221; ou do inglês **[reference pixel][1]**: que significa que esse novo &#8220;pixel&#8221; é uma **referência ótica** de unidade.

Para entrar em detalhes, leia [o que é um pixel][2]. Vai te ajudar a entender melhor.

### Densidade de pixels

A sigla PPI ([que é diferente de DPI][3]) significa **Pixel Per Inch**, ou seja, é o número de pixels que seu dispositivo pode conter em uma polegada. Quanto mais pixels em uma polegada, mais nítida a imagem é. 

Os aparelhos como o iPhone 4 e outros que carregam Android tem uma densidade de pixels muito alta. Ou seja, eles conseguem comprimir um grande número de pixels em suas telas, tornando as imagens melhores. O problema é que as imagens que criamos hoje podem parecer ruins nesses dispositivos. Algo parecido como aumentar uma imagem pequena no Photoshop, entende? Ela fica toda pixelada, sem qualidade nenhuma. Isso por que você está aumentando o tamanho de uma imagem que é pequena e não tem pixels suficientes para dividir pelo tamanho que você definiu. 

Entenda fazendo um teste: Vá até o site da Apple utilizando SAFARI. Agora, dê um zoom em alguma imagem. Veja como ela parece pixelada por causa do zoom. Agora abra o Inspector do seu navegador, vá até o console e coloque as duas linhas abaixo:

[cc lang=&#8221;javascript&#8221;]
  
AC.ImageReplacer._devicePixelRatio = 2
  
new AC.ImageReplacer()
  
[/cc]

A imagem foi trocada para uma imagem com o dobro de tamanho da imagem original para que ela ficasse melhor em telas com alta densidade de pixels&#8230; [Veja a diferença][4]. [Eu vi esse truque aqui][5].

### Ações para otimizar

Existem algumas atitudes que vocês já pode tomar agora para poder chavear estes aparelhos e entregar uma experiência melhor para seus usuários.

#### Utilize media queries

[Media Queries são um chuchuzinho][6]. Você pode utilizar uma regra chamada **device-pixel-ratio** para detectar qual CSS servir dependendo do pixel-ratio do dispositivo. Não precisa ser maníaco e servir vários CSS para vários pixel-ratios&#8230; Você vai ficar doido se fizer isso.

Abaixo veja uma tabela de exemplos de aparelhos com seus valores de pixel-ratios:

<table style="margin: auto">
  <tr>
    <td width="200px">
      <strong>Dispositivo</strong>
    </td>
    
    <td width="100px">
      <strong>Resolução</strong>
    </td>
    
    <td width="150px">
      <strong>device-pixel-ratio</strong>
    </td>
  </tr>
  
  <tr>
    <td>
      Android LDPI
    </td>
    
    <td>
      320×240
    </td>
    
    <td>
      0.75
    </td>
  </tr>
  
  <tr>
    <td>
      Iphone 3 & Android MDPI
    </td>
    
    <td>
      320×480
    </td>
    
    <td>
      1
    </td>
  </tr>
  
  <tr>
    <td>
      Android HDPI
    </td>
    
    <td>
      480×800
    </td>
    
    <td>
      1.5
    </td>
  </tr>
  
  <tr>
    <td>
      Iphone 4
    </td>
    
    <td>
      960×640
    </td>
    
    <td>
      2.0
    </td>
  </tr>
</table>

Agora, como seria o CSS:

[cc lang=&#8221;css&#8221;] 

<link rel="stylesheet" media="screen and (-webkit-device-pixel-ratio: 0.75)" href="low-ppi.css" />

<link rel="stylesheet" media="screen and (-webkit-device-pixel-ratio: 1.0)" href="medium-ppi.css" />

<link rel="stylesheet" media="screen and (-webkit-device-pixel-ratio: 1.5)" href="high-ppi.css" />

<link rel="stylesheet" media="screen and (-webkit-device-pixel-ratio: 2.0)" href="retina.css" />
[/cc]

Eu sugiro que você se limite apenas para o pixel-ratio 2. Do jeito que as coisas estão andando, os aparelhos de pixel-ratio menor do que 2 desaparecerão logo e os aparelhos com pixel-ratio igual a 1 são maioria e você já faz versões para eles, já que não precisam de fallbacks.

#### Considere chavear versões de imagens

Este é um problema que ainda não existe uma solução inteligente e definitiva.
  
A ideia é tentar evitar que o usuário baixe duas imagens iguais, mas de tamanhos diferentes para cada tipo de necessidade. Logo, existem vários fallbacks, em Javascript ou linguagens server-side para servir apenas a imagem necessária.

O pessoal da Clound Four escreveu [um artigo muito interessante sobre isso][7].

Há outros artigos bons por aí. Eu estou dando uma lida em vários para tentar escrever um artigo mais simples aqui no Tableless. Mas o assunto é muito vasto e ninguém tem uma opinião definida ainda. Isso não é útil apenas para a situação dos aparelhos hires, mas também para encontrarmos maneiras de servir imagens menores para versões de sites mobiles.

#### Text rendering

Você consegue melhorar muito a leitura dos usuários utilizando a propriedade **text-rendering**.

[cc lang=&#8221;css&#8221;]
  
h1, h2, h3 { text-rendering: optimizeLegibility; }
  
[/cc]

Esta propriedade melhora muito a leitura quando o usuário dá o zoom nos aparelhos móveis e também corrige suporte de ligaduras e kerning. Coisa linda.

#### Text Smoothing

A propriedade **font-smoothing** é útil agora! A leitura melhora demais em monitores normais e previne serrilhamentos ocasionais quando utilizandos @font-face.

[cc lang=&#8221;css&#8221;]
  
body * {
  
-webkit-font-smoothing: antialiased;
  
-moz-font-smoothing: antialiased;
  
-o-font-smoothing: antialiased;
  
-ms-font-smoothing: antialiased;
  
font-smoothing: antialiased;
  
}
  
[/cc]

#### Tente usar CSS3

Tente usar e abusar dos efeitos do CSS como sombras, gradientes, bordas arredondadas e etc. Além de facilitarem sua vida evitando a criação de imagens desnecessárias, elas ajudam na velocidade de carregamento do site.

#### Considere utilizar SVG

Já tem alguns que estão começando a utilizar SVG para facilitar a vida. Para ícones, SVG é ótimo. Você consegue reutilizá-los em diversos tamanhos, aumentando o diminuindo de acordo com a sua necessidade e também do aparelho. Veja um exemplo que a [Smashing Magazine escreveu][8].

#### Novo elemento HTML

O W3C já criou um grupo chamado [Responsive Images Community Group][9] para a criação de elementos do HTML que facilitam a entrega de assets dependendo do contexto. Eles estão propondo um novo elemento que identifica as dimensões do dispositivo, velocidade de rede, densidade de pixels e outros pontos para servir melhor imagens e outros assets dependendo do contexto.

### Muitos artigos para ler

  * [How to make your web content look stunning on the iPhone 4&#8217;s new Retina Display][10] 
  * [Retina Display and CSS Background Images][11] 
  * [Designing for the Retina Display (326ppi)][12] 
  * [Você se lembra quando planejavamos nossos layouts para resoluções acima de 1024? Chega ser engraçado lembrar que um dia fizemos websites para 640&#215;480, pensando que a resolução de 1024&#215;768 eram a minoria dos usuários. Os tempos mudaram e naturalmente diversas outras resoluções apareceram por conta de novos dispositivos, melhores monitores e etc. Acontece que na web nada é tão fácil assim. A gente se livra de um problema, mas aparece outro no lugar.

Este ano eu estou trabalhando a maior parte do tempo em um monitor fullHD. Notei uma diferença gritante ao digitar código pela primeira vez em um monitor desses. E não são apenas os monitores que estão mudando para uma resolução decente. Também, seguindo o ciclo natural, dispositivos menores estão recebendo a dádiva de ter a alta resolução em suas telas. E isso, meu caro, é uma dádiva para o usuário, para você é mais trabalho. 😉

### Pixels não são mais como eram antigamente

Na minha época de escola &#8211; nem tanto tempo assim &#8211; os professores me ensinaram que o átomo era indivisível. Era incrível por que eu, como criança, me divertia tentando entender como algo poderia ser tão pequeno que não pudesse ser partido ao meio, ficando menor&#8230; Mas aí eu descobri que os prótons, os elentrons e outras partículas subatomicas existiam também&#8230; 

A mesma coisa aconteceu com o pixel. O pixel sempre representou a menor unidade da sua tela. Para os designers, o pixel é a unidade central. É onde tudo se baseia: medidas, tamanhos, alinhamentos etc&#8230; Mas o pixel não é mais como era antigamente.

Com o advento das telas HD em aparelhos móveis, o conceito de pixel mudou um <del>pouco</del> muito. Quando a tela retina display do iPhone 4 foi lançada o queixo de todo mundo caiu. A Apple conseguiu apertar quatro pixels onde apenas caberia um. Logo o pixel pode ser definido como a menor unidade na tela, como você já conhece ou pode ser baseada em uma unidade chamada hoje em dia de &#8220;pixel referência&#8221; ou do inglês **[reference pixel][1]**: que significa que esse novo &#8220;pixel&#8221; é uma **referência ótica** de unidade.

Para entrar em detalhes, leia [o que é um pixel][2]. Vai te ajudar a entender melhor.

### Densidade de pixels

A sigla PPI ([que é diferente de DPI][3]) significa **Pixel Per Inch**, ou seja, é o número de pixels que seu dispositivo pode conter em uma polegada. Quanto mais pixels em uma polegada, mais nítida a imagem é. 

Os aparelhos como o iPhone 4 e outros que carregam Android tem uma densidade de pixels muito alta. Ou seja, eles conseguem comprimir um grande número de pixels em suas telas, tornando as imagens melhores. O problema é que as imagens que criamos hoje podem parecer ruins nesses dispositivos. Algo parecido como aumentar uma imagem pequena no Photoshop, entende? Ela fica toda pixelada, sem qualidade nenhuma. Isso por que você está aumentando o tamanho de uma imagem que é pequena e não tem pixels suficientes para dividir pelo tamanho que você definiu. 

Entenda fazendo um teste: Vá até o site da Apple utilizando SAFARI. Agora, dê um zoom em alguma imagem. Veja como ela parece pixelada por causa do zoom. Agora abra o Inspector do seu navegador, vá até o console e coloque as duas linhas abaixo:

[cc lang=&#8221;javascript&#8221;]
  
AC.ImageReplacer._devicePixelRatio = 2
  
new AC.ImageReplacer()
  
[/cc]

A imagem foi trocada para uma imagem com o dobro de tamanho da imagem original para que ela ficasse melhor em telas com alta densidade de pixels&#8230; [Veja a diferença][4]. [Eu vi esse truque aqui][5].

### Ações para otimizar

Existem algumas atitudes que vocês já pode tomar agora para poder chavear estes aparelhos e entregar uma experiência melhor para seus usuários.

#### Utilize media queries

[Media Queries são um chuchuzinho][6]. Você pode utilizar uma regra chamada **device-pixel-ratio** para detectar qual CSS servir dependendo do pixel-ratio do dispositivo. Não precisa ser maníaco e servir vários CSS para vários pixel-ratios&#8230; Você vai ficar doido se fizer isso.

Abaixo veja uma tabela de exemplos de aparelhos com seus valores de pixel-ratios:

<table style="margin: auto">
  <tr>
    <td width="200px">
      <strong>Dispositivo</strong>
    </td>
    
    <td width="100px">
      <strong>Resolução</strong>
    </td>
    
    <td width="150px">
      <strong>device-pixel-ratio</strong>
    </td>
  </tr>
  
  <tr>
    <td>
      Android LDPI
    </td>
    
    <td>
      320×240
    </td>
    
    <td>
      0.75
    </td>
  </tr>
  
  <tr>
    <td>
      Iphone 3 & Android MDPI
    </td>
    
    <td>
      320×480
    </td>
    
    <td>
      1
    </td>
  </tr>
  
  <tr>
    <td>
      Android HDPI
    </td>
    
    <td>
      480×800
    </td>
    
    <td>
      1.5
    </td>
  </tr>
  
  <tr>
    <td>
      Iphone 4
    </td>
    
    <td>
      960×640
    </td>
    
    <td>
      2.0
    </td>
  </tr>
</table>

Agora, como seria o CSS:

[cc lang=&#8221;css&#8221;] 

<link rel="stylesheet" media="screen and (-webkit-device-pixel-ratio: 0.75)" href="low-ppi.css" />

<link rel="stylesheet" media="screen and (-webkit-device-pixel-ratio: 1.0)" href="medium-ppi.css" />

<link rel="stylesheet" media="screen and (-webkit-device-pixel-ratio: 1.5)" href="high-ppi.css" />

<link rel="stylesheet" media="screen and (-webkit-device-pixel-ratio: 2.0)" href="retina.css" />
[/cc]

Eu sugiro que você se limite apenas para o pixel-ratio 2. Do jeito que as coisas estão andando, os aparelhos de pixel-ratio menor do que 2 desaparecerão logo e os aparelhos com pixel-ratio igual a 1 são maioria e você já faz versões para eles, já que não precisam de fallbacks.

#### Considere chavear versões de imagens

Este é um problema que ainda não existe uma solução inteligente e definitiva.
  
A ideia é tentar evitar que o usuário baixe duas imagens iguais, mas de tamanhos diferentes para cada tipo de necessidade. Logo, existem vários fallbacks, em Javascript ou linguagens server-side para servir apenas a imagem necessária.

O pessoal da Clound Four escreveu [um artigo muito interessante sobre isso][7].

Há outros artigos bons por aí. Eu estou dando uma lida em vários para tentar escrever um artigo mais simples aqui no Tableless. Mas o assunto é muito vasto e ninguém tem uma opinião definida ainda. Isso não é útil apenas para a situação dos aparelhos hires, mas também para encontrarmos maneiras de servir imagens menores para versões de sites mobiles.

#### Text rendering

Você consegue melhorar muito a leitura dos usuários utilizando a propriedade **text-rendering**.

[cc lang=&#8221;css&#8221;]
  
h1, h2, h3 { text-rendering: optimizeLegibility; }
  
[/cc]

Esta propriedade melhora muito a leitura quando o usuário dá o zoom nos aparelhos móveis e também corrige suporte de ligaduras e kerning. Coisa linda.

#### Text Smoothing

A propriedade **font-smoothing** é útil agora! A leitura melhora demais em monitores normais e previne serrilhamentos ocasionais quando utilizandos @font-face.

[cc lang=&#8221;css&#8221;]
  
body * {
  
-webkit-font-smoothing: antialiased;
  
-moz-font-smoothing: antialiased;
  
-o-font-smoothing: antialiased;
  
-ms-font-smoothing: antialiased;
  
font-smoothing: antialiased;
  
}
  
[/cc]

#### Tente usar CSS3

Tente usar e abusar dos efeitos do CSS como sombras, gradientes, bordas arredondadas e etc. Além de facilitarem sua vida evitando a criação de imagens desnecessárias, elas ajudam na velocidade de carregamento do site.

#### Considere utilizar SVG

Já tem alguns que estão começando a utilizar SVG para facilitar a vida. Para ícones, SVG é ótimo. Você consegue reutilizá-los em diversos tamanhos, aumentando o diminuindo de acordo com a sua necessidade e também do aparelho. Veja um exemplo que a [Smashing Magazine escreveu][8].

#### Novo elemento HTML

O W3C já criou um grupo chamado [Responsive Images Community Group][9] para a criação de elementos do HTML que facilitam a entrega de assets dependendo do contexto. Eles estão propondo um novo elemento que identifica as dimensões do dispositivo, velocidade de rede, densidade de pixels e outros pontos para servir melhor imagens e outros assets dependendo do contexto.

### Muitos artigos para ler

  * [How to make your web content look stunning on the iPhone 4&#8217;s new Retina Display][10] 
  * [Retina Display and CSS Background Images][11] 
  * [Designing for the Retina Display (326ppi)][12] 
  *][13] 
  * [Targeting High Screen Densities with CSS Media Queries][14] 
  * [A Pixel Identity Crisis][1] 
  * [optimizing web experiences for high resolution screens][15]

 [1]: http://www.alistapart.com/articles/a-pixel-identity-crisis/?utm_source=TablelessComBr&utm_medium=PostLink&utm_campaign=TablelessComBr&utm_nooverride=1
 [2]: http://en.wikipedia.org/wiki/Pixel
 [3]: http://www.andrewdaceyphotography.com/articles/dpi/
 [4]: http://tableless.com.br/uploads/2012/03/retina.jpg
 [5]: http://www.appleinsider.com/articles/12/03/13/how_to_preview_the_retina_display_enhanced_applecom_in_safari_on_mac_or_pc.html
 [6]: http://tableless.com.br/introducao-sobre-media-queries/
 [7]: http://cloudfour.com/how-apple-com-will-serve-retina-images-to-new-ipads/?utm_source=TablelessComBr&utm_medium=PostLink&utm_campaign=TablelessComBr&utm_nooverride=1
 [8]: http://coding.smashingmagazine.com/2012/01/16/resolution-independence-with-svg/?utm_source=TablelessComBr&utm_medium=PostLink&utm_campaign=TablelessComBr&utm_nooverride=1
 [9]: http://www.w3.org/community/respimg/
 [10]: http://aralbalkan.com/3331?utm_source=TablelessComBr&utm_medium=PostLink&utm_campaign=TablelessComBr&utm_nooverride=1
 [11]: http://www.weedygarden.net/2010/10/13/retina-display-and-css-background-images/?utm_source=TablelessComBr&utm_medium=PostLink&utm_campaign=TablelessComBr&utm_nooverride=1
 [12]: http://www.lukew.com/ff/entry.asp?1142&utm_source=TablelessComBr&utm_medium=PostLink&utm_campaign=TablelessComBr&utm_nooverride=1
 [13]: http://eisabainyo.net/weblog/2011/06/07/how-to-use-hi-res-images-for-web-apps-in-iphone4/?utm_source=TablelessComBr&utm_medium=PostLink&utm_campaign=TablelessComBr&utm_nooverride=1
 [14]: http://www.fiveminutes.eu/targeting-hight-screen-densities-with-css-media-queries/?utm_source=TablelessComBr&utm_medium=PostLink&utm_campaign=TablelessComBr&utm_nooverride=1
 [15]: http://bradfrostweb.com/blog/mobile/hi-res-optimization/?utm_source=TablelessComBr&utm_medium=PostLink&utm_campaign=TablelessComBr&utm_nooverride=1