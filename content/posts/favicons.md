---
title: Favicons
author: Dani Guerrato
type: post
date: 2013-02-06
excerpt: Os favicons são pequenos mas indispensáveis. Entenda como eles funcionam e quais as melhores práticas.
url: /favicons/
dsq_thread_id: 1062038448
categories:
  - Acessibilidade
  - Browsers
  - Código
  - Design
tags:
  - 2013
  - browser
  - favicons

---
## Favicons

Se você ainda não sabe, Favicons são aqueles pequenos ícones que ficam ao lado da barra de endereços de um navegador e servem, entre outras funções, para identificar rapidamente um site. Os Favicons são um velhos conhecidos dos designers e desenvolvedores. Já são 14 anos de história. E neste meio tempo muita coisa evoluiu. Surgiram smartphones, tablets, televisores, sistemas operacionais modernos, telas de alta resolução e o favicon foi mudando de tamanho, posição e formato, conquistando um espaço muito além da barra de ferramentas do navegador. Neste artigo vamos conhecer mais profundamente esta parte tão importante, mas muitas vezes tão negligenciada, do webdesign.

> A função de um favicon não é apenas ser, como o nome nos leva a deduzir, um símbolo relacionado aos favoritos. Favicons são parte integrante do branding.

O primeiro browser a utilizar favicon foi (pasmem!) o Internet Explorer 5. Naqueles idos tempos de 1999 os simpáticos ícones de 16 pixels tinham outras funções como estimar o número de usuários que favoritavam um site com base em requisições do ícone no servidor. Este método deixou de ter utilidade quando os browsers passaram a exibir favicons também na barra de tarefas, independente do site estar salvo nos favoritos ou não. Mas o nome &#8211; uma junção dos termos favorite e icons &#8211; ficou.

## Função

Ícones podem ter diversos propósitos como representar uma determinada ação, superar barreiras de linguagem, sinalização e/ou transmitir uma mensagem. Você não precisa conhecer a língua local em uma estação de trem de outro país para saber onde é a saída. A figura de um homem passando por uma porta acompanhada de uma seta é suficiente para comunicar esta informação. Da mesma forma, portas de banheiro são demarcadas com silhuetas masculinas ou femininas para você não errar na hora do aperto. Estas representações imagéticas acabam rapidamente se tornando convenções sociais. Não é necessário pensar muito para saber qual botão toca ou pausa um aparelho de som ou vídeo&#8230;

A função de um favicon não é apenas ser, como o nome nos leva a deduzir, um símbolo relacionado aos favoritos. Favicons são parte integrante do branding. Eles servem para representar um website como uma entidade dentro de um browser.

## Design de ícones

Criar um ícone é uma atividade multidisciplinar. Semiótica, gestalt, branding e cultura pop são alguns dos assuntos importantes para se ter em mente na hora de projetar ícones. Pesquisa e bom senso também são fundamentais, afinal, um mesmo símbolo pode ter dezenas de significados diferentes de acordo com idade, sexo, nacionalidade, profissão, religião e cultura do público alvo. Além, é claro, do conhecimento técnico necessário para garantir uniformidade, visibilidade, nitidez e identificação de uma imagem em tamanhos reduzidos. Este artigo não tem a pretensão de ensinar design de ícones, mas sim fornecer informações relevantes para utilizar de maneira mais inteligente os recursos disponíveis em diferentes browsers, sistemas operacionais e aparelhos para fazer da iconografia uma ferramenta de divulgação uma marca.

> O primeiro browser a utilizar favicon foi (pasmem!) o Internet Explorer 5.

Se você precisa de algumas dicas sobre o por que e como criar um ícone vale a pena ler o livro [The Icon Handbook][1] por Jon Hicks.

Existem diversas opções de ferramentas digitais para a criação de ícones. [Desde plugins para Photoshop][2] até alguns softwares exclusivos para este fim. O importante é ter o cuidado de repensar o design com mais ou menos detalhes de acordo com o tamanho do ícone ao invés de simplesmente redimensionar o arquivo. Até mesmo reduções proporcionais podem gerar um resultado distorcido e com baixa nitidez. Como em qualquer outro trabalho, quanto mais tempo e carinho você dedicar para criar o seu ícone melhor será o resultado final. Faça o que fizer, passe longe dos conversores automáticos online! O resultado é tão desastroso quanto um layout WYSIWYG em tabela com gifs animados de gatos tocando teclado.

## Formatos

#### .ICO

Este tipo de arquivo ainda é o mais utilizado devido ao grande suporte por parte dos navegadores e pela opção de conter diversas imagens encapsuladas. Ou seja, em um mesmo arquivo é possível atender diversas funções e resoluções de tela. (E não. Você não vai conseguir isto simplesmente renomeando um .gif ou .png. É necessário buscar um software próprio)/ Mas é necessário cuidado para que o arquivo final não fique muito pesado. Alguns desenvolvedores recomendam um tamanho máximo de 20K.

#### .PNG

Os browsers modernos &#8211; leia-se todo mundo menos o Internet Explorer &#8211; já suportam outras extenções como PNG, por exemplo. As vantagens do PNG é a qualidade maior da imagem, tamanho reduzido e a conveniência na fase de criação. É bem provável que você já tenha no seu computador algum software capaz de salvar ou exportar arquivos para este formato. Mas como não é possível incluir diversas resoluções em um único arquivo é necessário declarar manualmente cada uma das resoluções.

#### Outros formatos

Existe a possibilidade de uso para alguns outros formatos além de ICO e PNG, mas ainda não existem vantagens consistentes para a adoção de nenhum. JPG, por exemplo, não é adequado devido a pixelização das imagens e a falta de um canal de transparência. O GIF tem uma qualidade inferior e ainda não encontrei quem é o cidadão que acha uma boa ideia utilizar APNG (uma espécie de PNG animado).

> Como em qualquer outro trabalho, quanto mais tempo e carinho você dedicar para criar o seu ícone melhor será o resultado final.

Uma opção promissora é o SVG. Como o SVG é um arquivo vetor não teriamos que nos preocupar com os diversos tamanhos. Mas até agora só Opera e o Google Chrome suportam. Então, como grande parte das novidades interessantes, teremos que esperar os outros browsers para começar a brincar&#8230;

Se você tem curiosidade em saber qual navegador aceita o que a partir de qual versão, esta é a tabela de compatibilidade segundo a Wikipedia.

<table>
  <tr>
    <td>
      Browser
    </td>
    
    <td>
      ICO
    </td>
    
    <td>
      PNG
    </td>
    
    <td>
      GIF
    </td>
    
    <td>
      animated GIFs
    </td>
    
    <td>
      JPEG
    </td>
    
    <td>
      APNG
    </td>
    
    <td>
      SVG
    </td>
  </tr>
  
  <tr>
    <td>
      Firefox
    </td>
    
    <td>
      1.0+
    </td>
    
    <td>
      1.0+
    </td>
    
    <td>
      1.0+
    </td>
    
    <td>
      Sim
    </td>
    
    <td>
      Sim
    </td>
    
    <td>
      3.0+
    </td>
    
    <td>
      &#8211;
    </td>
  </tr>
  
  <tr>
    <td>
      Chrome
    </td>
    
    <td>
      Sim
    </td>
    
    <td>
      Sim
    </td>
    
    <td>
      4.0+
    </td>
    
    <td>
      4.0+
    </td>
    
    <td>
      4.0+
    </td>
    
    <td>
      &#8211;
    </td>
    
    <td>
      Sim
    </td>
  </tr>
  
  <tr>
    <td>
      IE
    </td>
    
    <td>
      5.0+
    </td>
    
    <td>
      &#8211;
    </td>
    
    <td>
      &#8211;
    </td>
    
    <td>
      &#8211;
    </td>
    
    <td>
      &#8211;
    </td>
    
    <td>
      &#8211;
    </td>
    
    <td>
      &#8211;
    </td>
  </tr>
  
  <tr>
    <td>
      Opera
    </td>
    
    <td>
      7.0+
    </td>
    
    <td>
      7.0+
    </td>
    
    <td>
      7.0+
    </td>
    
    <td>
      7.0+
    </td>
    
    <td>
      7.0+
    </td>
    
    <td>
      9.5+
    </td>
    
    <td>
      9.6+
    </td>
  </tr>
  
  <tr>
    <td>
      Safari
    </td>
    
    <td>
      Sim
    </td>
    
    <td>
      4.0+
    </td>
    
    <td>
      4.0+
    </td>
    
    <td>
      &#8211;
    </td>
    
    <td>
      4.0+
    </td>
    
    <td>
      &#8211;
    </td>
    
    <td>
      &#8211;
    </td>
  </tr>
</table>

Se quer um conselho amigo passe longe de favicons animados. Além de bregas eles distraem o usuário e passam a impressão que você é carente por atenção.

A melhor pedida é utilizar PNG com um fallback em ICO para o Internet Explorer.

## Tamanho

Aqui começa a confusão. Os favicons clássicos tinham 16px quadrados. Mas hoje grande parte dos browsers utilizam uma versão de 32px. Esta é a versão padrão para a barra de ferramentas do Internet Explorer 10, pro exemplo. Ícones para home screen de dispositivos móveis são outro pepino&#8230; Só o iOS vai ter 4 tamanhos diferentes de acordo com o aparelho e resolução de tela. Ainda existem outras coisas para se considerar como tiles do Windows 8 e quadradinhos do Opera Speed Dial e até mesmo Google TV. Segue uma listinha básica de tamanhos:

**&#8211; 16px:** Barra de endereço, abas e favoritos da maior parte dos navegadores.
  
**&#8211; 24px:** Barra de ferramentas do Internet Explorer 9
  
**&#8211; 32px:** Nova aba no IE, site fixo na barra de tarefas do Windos 7 e sidebar do Safari **&#8211; 57px:** iPhone sem tela retina e iPod Touch
  
**&#8211; 72px:** iPad sem tela retina
  
**&#8211; 96px:** GoogleTV
  
**&#8211; 114px:** iPhone com tela retina
  
**&#8211; 128px:** Chrome Web Store
  
**&#8211; 144px:** iPad Retina, Windows 8 Tiles
  
**&#8211; 256x160px:** Opera Speed Dial

Parece muita coisa, mas raramente você vai precisar utilizar todos estes tamanhos. Isto vai variar de acordo com as necessidades do público alvo de cada projeto, que incluem navegador, aparelho e sistema operacional mais utilizados. Minha recomendação é incluir ao menos o clássico de 16px, uma versão HD de 32px e os touch icons para iOS. Segundo estatísticas da Microsoft um site fixado na barra de tarefas do Windows 7 recebia uma porcentagem de visita de 15% a 50% maior&#8230; Segundo esta lógica criar um tile para o Windows 8 também é uma boa prática, já que as opções de interação se estendem além do navegador.

## Como implementar um favicon

Esta é simples. Basta deixar um arquivo de nome favicon.ico na pasta raíz do servidor. Certo?

Sim e não. Isto funcionaria bem para apenas um arquivo&#8230; Mas se você deseja trabalhar com múltiplos tamanhos e formatos vai ser necessário declarar no HTML. Vamos supor que temos um arquivo favicon.png dentro de uma pasta chamada IMG.

Antigamente você provavelmente faria isto da seguinte maneira:

<pre class="lang-html">&lt;link rel="icon" type="image/png" href="img/favicon.png" /&gt;</pre>

Como somos bacanas e utilizamos HTML5 as coisas ficam mais simples:

<pre class="lang-html">&lt;link rel="icon" href="img/favicon.png" /&gt;</pre>

Okay. Isto funciona para a maior parte dos browsers inteligentes. Falta o fallback para o IE&#8230;

Aviso mega Importante! Não cometa o erro de declarar o png E o ico sem comentários condicionais. Sério. Isto da problemas. Cada navegador possui a sua lógica. Uns vão ler o primeiro que você declarar, outros o último, alguns escolhem aleatoriamente&#8230; Sério! Caos!

Poderíamos fazer o fallback através de comentários condicionais:

<pre class="lang-html">&lt;!--[if IE]&gt;&lt;link rel="shortcut icon" href="img/favicon.ico"&gt;&lt;![endif]--&gt;
&lt;link rel="icon" href="img/favicon.png"&gt;</pre>

Poderíamos&#8230; mas para a Microsoft não basta atrapalhar a vida dos desenvolvedores com os problemas dos navegadores antigos. Ela gosta de criar novos problemas! O IE10 não suporta comentários condicionais. É isto mesmo. A salvação mágica para aquelas longas noites insones desenvolvendo não funciona mais. Pode esquecer. Ah, e não sei se você deu uma espiadinha na tabela lá em cima, mas também não suportam PNG. Legal, né? Bem, são estas pequenas coisas que fazem a vida de um desenvolvedor web preocupado com acessibilidade e experiência do usuário um pouco como resolver quebra cabeças&#8230; Uma solução possível seria declarar apenas o arquivo em PNG e manter o ICO na raíz.

<pre class="lang-html">&lt;link rel="icon" href="img/favicon.png" /&gt;</pre>

Se você desejar incluir diversos tamanhos, basta declarar cada um deles.

<pre class="lang-html">&lt;link rel="icon" href="favicon-16.png" sizes="16x16"&gt;
&lt;link rel="icon" href="favicon-32.png" sizes="32x32"&gt;
&lt;link rel="icon" href="favicon-48.png" sizes="48x48"&gt;
&lt;link rel="icon" href="favicon-64.png" sizes="64x64"&gt;
&lt;link rel="icon" href="favicon-128.png" sizes="128x128"&gt;</pre>

## Apple Touch Icons

No caso de dispositivos que utilizam o sistema iOS (iPhone, iPod e iPad) existe a opção de fixar qualquer site como um favorito diretamente na tela de inicio, independente da existência de uma versão mobile ou design responsivo. Por padrão uma thumbnail é gerada automaticamente a partir de uma screenshot da página, mas o resultado é não apenas visualmente confuso como nada prático do ponto de vista da rápida identificação em meio a tantos outros ícones&#8230; Muitas vezes o usuário pode até resolver desafixar o seu site dali por que deixou a tela &#8220;feia&#8221;. Criar uma imagem exclusiva, chamada apple touch icon, é portanto uma boa prática de usabilidade.

Para isto basta criar 4 imagem quadradas com os cantos retos em formato png nos tamanhos 57px, 72px, 114px e 144px. [## Favicons

Se você ainda não sabe, Favicons são aqueles pequenos ícones que ficam ao lado da barra de endereços de um navegador e servem, entre outras funções, para identificar rapidamente um site. Os Favicons são um velhos conhecidos dos designers e desenvolvedores. Já são 14 anos de história. E neste meio tempo muita coisa evoluiu. Surgiram smartphones, tablets, televisores, sistemas operacionais modernos, telas de alta resolução e o favicon foi mudando de tamanho, posição e formato, conquistando um espaço muito além da barra de ferramentas do navegador. Neste artigo vamos conhecer mais profundamente esta parte tão importante, mas muitas vezes tão negligenciada, do webdesign.

> A função de um favicon não é apenas ser, como o nome nos leva a deduzir, um símbolo relacionado aos favoritos. Favicons são parte integrante do branding.

O primeiro browser a utilizar favicon foi (pasmem!) o Internet Explorer 5. Naqueles idos tempos de 1999 os simpáticos ícones de 16 pixels tinham outras funções como estimar o número de usuários que favoritavam um site com base em requisições do ícone no servidor. Este método deixou de ter utilidade quando os browsers passaram a exibir favicons também na barra de tarefas, independente do site estar salvo nos favoritos ou não. Mas o nome &#8211; uma junção dos termos favorite e icons &#8211; ficou.

## Função

Ícones podem ter diversos propósitos como representar uma determinada ação, superar barreiras de linguagem, sinalização e/ou transmitir uma mensagem. Você não precisa conhecer a língua local em uma estação de trem de outro país para saber onde é a saída. A figura de um homem passando por uma porta acompanhada de uma seta é suficiente para comunicar esta informação. Da mesma forma, portas de banheiro são demarcadas com silhuetas masculinas ou femininas para você não errar na hora do aperto. Estas representações imagéticas acabam rapidamente se tornando convenções sociais. Não é necessário pensar muito para saber qual botão toca ou pausa um aparelho de som ou vídeo&#8230;

A função de um favicon não é apenas ser, como o nome nos leva a deduzir, um símbolo relacionado aos favoritos. Favicons são parte integrante do branding. Eles servem para representar um website como uma entidade dentro de um browser.

## Design de ícones

Criar um ícone é uma atividade multidisciplinar. Semiótica, gestalt, branding e cultura pop são alguns dos assuntos importantes para se ter em mente na hora de projetar ícones. Pesquisa e bom senso também são fundamentais, afinal, um mesmo símbolo pode ter dezenas de significados diferentes de acordo com idade, sexo, nacionalidade, profissão, religião e cultura do público alvo. Além, é claro, do conhecimento técnico necessário para garantir uniformidade, visibilidade, nitidez e identificação de uma imagem em tamanhos reduzidos. Este artigo não tem a pretensão de ensinar design de ícones, mas sim fornecer informações relevantes para utilizar de maneira mais inteligente os recursos disponíveis em diferentes browsers, sistemas operacionais e aparelhos para fazer da iconografia uma ferramenta de divulgação uma marca.

> O primeiro browser a utilizar favicon foi (pasmem!) o Internet Explorer 5.

Se você precisa de algumas dicas sobre o por que e como criar um ícone vale a pena ler o livro [The Icon Handbook][1] por Jon Hicks.

Existem diversas opções de ferramentas digitais para a criação de ícones. [Desde plugins para Photoshop][2] até alguns softwares exclusivos para este fim. O importante é ter o cuidado de repensar o design com mais ou menos detalhes de acordo com o tamanho do ícone ao invés de simplesmente redimensionar o arquivo. Até mesmo reduções proporcionais podem gerar um resultado distorcido e com baixa nitidez. Como em qualquer outro trabalho, quanto mais tempo e carinho você dedicar para criar o seu ícone melhor será o resultado final. Faça o que fizer, passe longe dos conversores automáticos online! O resultado é tão desastroso quanto um layout WYSIWYG em tabela com gifs animados de gatos tocando teclado.

## Formatos

#### .ICO

Este tipo de arquivo ainda é o mais utilizado devido ao grande suporte por parte dos navegadores e pela opção de conter diversas imagens encapsuladas. Ou seja, em um mesmo arquivo é possível atender diversas funções e resoluções de tela. (E não. Você não vai conseguir isto simplesmente renomeando um .gif ou .png. É necessário buscar um software próprio)/ Mas é necessário cuidado para que o arquivo final não fique muito pesado. Alguns desenvolvedores recomendam um tamanho máximo de 20K.

#### .PNG

Os browsers modernos &#8211; leia-se todo mundo menos o Internet Explorer &#8211; já suportam outras extenções como PNG, por exemplo. As vantagens do PNG é a qualidade maior da imagem, tamanho reduzido e a conveniência na fase de criação. É bem provável que você já tenha no seu computador algum software capaz de salvar ou exportar arquivos para este formato. Mas como não é possível incluir diversas resoluções em um único arquivo é necessário declarar manualmente cada uma das resoluções.

#### Outros formatos

Existe a possibilidade de uso para alguns outros formatos além de ICO e PNG, mas ainda não existem vantagens consistentes para a adoção de nenhum. JPG, por exemplo, não é adequado devido a pixelização das imagens e a falta de um canal de transparência. O GIF tem uma qualidade inferior e ainda não encontrei quem é o cidadão que acha uma boa ideia utilizar APNG (uma espécie de PNG animado).

> Como em qualquer outro trabalho, quanto mais tempo e carinho você dedicar para criar o seu ícone melhor será o resultado final.

Uma opção promissora é o SVG. Como o SVG é um arquivo vetor não teriamos que nos preocupar com os diversos tamanhos. Mas até agora só Opera e o Google Chrome suportam. Então, como grande parte das novidades interessantes, teremos que esperar os outros browsers para começar a brincar&#8230;

Se você tem curiosidade em saber qual navegador aceita o que a partir de qual versão, esta é a tabela de compatibilidade segundo a Wikipedia.

<table>
  <tr>
    <td>
      Browser
    </td>
    
    <td>
      ICO
    </td>
    
    <td>
      PNG
    </td>
    
    <td>
      GIF
    </td>
    
    <td>
      animated GIFs
    </td>
    
    <td>
      JPEG
    </td>
    
    <td>
      APNG
    </td>
    
    <td>
      SVG
    </td>
  </tr>
  
  <tr>
    <td>
      Firefox
    </td>
    
    <td>
      1.0+
    </td>
    
    <td>
      1.0+
    </td>
    
    <td>
      1.0+
    </td>
    
    <td>
      Sim
    </td>
    
    <td>
      Sim
    </td>
    
    <td>
      3.0+
    </td>
    
    <td>
      &#8211;
    </td>
  </tr>
  
  <tr>
    <td>
      Chrome
    </td>
    
    <td>
      Sim
    </td>
    
    <td>
      Sim
    </td>
    
    <td>
      4.0+
    </td>
    
    <td>
      4.0+
    </td>
    
    <td>
      4.0+
    </td>
    
    <td>
      &#8211;
    </td>
    
    <td>
      Sim
    </td>
  </tr>
  
  <tr>
    <td>
      IE
    </td>
    
    <td>
      5.0+
    </td>
    
    <td>
      &#8211;
    </td>
    
    <td>
      &#8211;
    </td>
    
    <td>
      &#8211;
    </td>
    
    <td>
      &#8211;
    </td>
    
    <td>
      &#8211;
    </td>
    
    <td>
      &#8211;
    </td>
  </tr>
  
  <tr>
    <td>
      Opera
    </td>
    
    <td>
      7.0+
    </td>
    
    <td>
      7.0+
    </td>
    
    <td>
      7.0+
    </td>
    
    <td>
      7.0+
    </td>
    
    <td>
      7.0+
    </td>
    
    <td>
      9.5+
    </td>
    
    <td>
      9.6+
    </td>
  </tr>
  
  <tr>
    <td>
      Safari
    </td>
    
    <td>
      Sim
    </td>
    
    <td>
      4.0+
    </td>
    
    <td>
      4.0+
    </td>
    
    <td>
      &#8211;
    </td>
    
    <td>
      4.0+
    </td>
    
    <td>
      &#8211;
    </td>
    
    <td>
      &#8211;
    </td>
  </tr>
</table>

Se quer um conselho amigo passe longe de favicons animados. Além de bregas eles distraem o usuário e passam a impressão que você é carente por atenção.

A melhor pedida é utilizar PNG com um fallback em ICO para o Internet Explorer.

## Tamanho

Aqui começa a confusão. Os favicons clássicos tinham 16px quadrados. Mas hoje grande parte dos browsers utilizam uma versão de 32px. Esta é a versão padrão para a barra de ferramentas do Internet Explorer 10, pro exemplo. Ícones para home screen de dispositivos móveis são outro pepino&#8230; Só o iOS vai ter 4 tamanhos diferentes de acordo com o aparelho e resolução de tela. Ainda existem outras coisas para se considerar como tiles do Windows 8 e quadradinhos do Opera Speed Dial e até mesmo Google TV. Segue uma listinha básica de tamanhos:

**&#8211; 16px:** Barra de endereço, abas e favoritos da maior parte dos navegadores.
  
**&#8211; 24px:** Barra de ferramentas do Internet Explorer 9
  
**&#8211; 32px:** Nova aba no IE, site fixo na barra de tarefas do Windos 7 e sidebar do Safari **&#8211; 57px:** iPhone sem tela retina e iPod Touch
  
**&#8211; 72px:** iPad sem tela retina
  
**&#8211; 96px:** GoogleTV
  
**&#8211; 114px:** iPhone com tela retina
  
**&#8211; 128px:** Chrome Web Store
  
**&#8211; 144px:** iPad Retina, Windows 8 Tiles
  
**&#8211; 256x160px:** Opera Speed Dial

Parece muita coisa, mas raramente você vai precisar utilizar todos estes tamanhos. Isto vai variar de acordo com as necessidades do público alvo de cada projeto, que incluem navegador, aparelho e sistema operacional mais utilizados. Minha recomendação é incluir ao menos o clássico de 16px, uma versão HD de 32px e os touch icons para iOS. Segundo estatísticas da Microsoft um site fixado na barra de tarefas do Windows 7 recebia uma porcentagem de visita de 15% a 50% maior&#8230; Segundo esta lógica criar um tile para o Windows 8 também é uma boa prática, já que as opções de interação se estendem além do navegador.

## Como implementar um favicon

Esta é simples. Basta deixar um arquivo de nome favicon.ico na pasta raíz do servidor. Certo?

Sim e não. Isto funcionaria bem para apenas um arquivo&#8230; Mas se você deseja trabalhar com múltiplos tamanhos e formatos vai ser necessário declarar no HTML. Vamos supor que temos um arquivo favicon.png dentro de uma pasta chamada IMG.

Antigamente você provavelmente faria isto da seguinte maneira:

<pre class="lang-html">&lt;link rel="icon" type="image/png" href="img/favicon.png" /&gt;</pre>

Como somos bacanas e utilizamos HTML5 as coisas ficam mais simples:

<pre class="lang-html">&lt;link rel="icon" href="img/favicon.png" /&gt;</pre>

Okay. Isto funciona para a maior parte dos browsers inteligentes. Falta o fallback para o IE&#8230;

Aviso mega Importante! Não cometa o erro de declarar o png E o ico sem comentários condicionais. Sério. Isto da problemas. Cada navegador possui a sua lógica. Uns vão ler o primeiro que você declarar, outros o último, alguns escolhem aleatoriamente&#8230; Sério! Caos!

Poderíamos fazer o fallback através de comentários condicionais:

<pre class="lang-html">&lt;!--[if IE]&gt;&lt;link rel="shortcut icon" href="img/favicon.ico"&gt;&lt;![endif]--&gt;
&lt;link rel="icon" href="img/favicon.png"&gt;</pre>

Poderíamos&#8230; mas para a Microsoft não basta atrapalhar a vida dos desenvolvedores com os problemas dos navegadores antigos. Ela gosta de criar novos problemas! O IE10 não suporta comentários condicionais. É isto mesmo. A salvação mágica para aquelas longas noites insones desenvolvendo não funciona mais. Pode esquecer. Ah, e não sei se você deu uma espiadinha na tabela lá em cima, mas também não suportam PNG. Legal, né? Bem, são estas pequenas coisas que fazem a vida de um desenvolvedor web preocupado com acessibilidade e experiência do usuário um pouco como resolver quebra cabeças&#8230; Uma solução possível seria declarar apenas o arquivo em PNG e manter o ICO na raíz.

<pre class="lang-html">&lt;link rel="icon" href="img/favicon.png" /&gt;</pre>

Se você desejar incluir diversos tamanhos, basta declarar cada um deles.

<pre class="lang-html">&lt;link rel="icon" href="favicon-16.png" sizes="16x16"&gt;
&lt;link rel="icon" href="favicon-32.png" sizes="32x32"&gt;
&lt;link rel="icon" href="favicon-48.png" sizes="48x48"&gt;
&lt;link rel="icon" href="favicon-64.png" sizes="64x64"&gt;
&lt;link rel="icon" href="favicon-128.png" sizes="128x128"&gt;</pre>

## Apple Touch Icons

No caso de dispositivos que utilizam o sistema iOS (iPhone, iPod e iPad) existe a opção de fixar qualquer site como um favorito diretamente na tela de inicio, independente da existência de uma versão mobile ou design responsivo. Por padrão uma thumbnail é gerada automaticamente a partir de uma screenshot da página, mas o resultado é não apenas visualmente confuso como nada prático do ponto de vista da rápida identificação em meio a tantos outros ícones&#8230; Muitas vezes o usuário pode até resolver desafixar o seu site dali por que deixou a tela &#8220;feia&#8221;. Criar uma imagem exclusiva, chamada apple touch icon, é portanto uma boa prática de usabilidade.

Para isto basta criar 4 imagem quadradas com os cantos retos em formato png nos tamanhos 57px, 72px, 114px e 144px.][3]  quebra um galho nesta hora.

Depois é só nomear os arquivos com o prefixo &#8220;apple-touch-icon&#8221; e colocar na raíz do diretório. A vantagem disto é que você economiza algumas linhas de código, mas em alguns casos como em um tema para tumblr, por exemplo, não temos acesso a pasta raiz. Nestas horas é importante declarar o caminho no HTML. Outra vantagem em apontar o caminho do ícone no código é a acessibilidade. Não importa se o seu usuário é fanboy da Apple ou não. Quando devidamente apontados, os touch icons também são utilizados pelo Android (a partir da versão 2.2) e em alguns outros aplicativos como o Reeder para iPad.

Bem, prepare seus icones e cole isto aqui entre as tags head do seu HTML e seja feliz:

<pre class="lang-html">&lt;!-- iPad com Retina Display --&gt;
&lt;link rel="apple-touch-icon" sizes="144x144" href="apple-touch-icon-144x144.png"&gt;
&lt;!-- iPhone com Retina Display --&gt;
&lt;link rel="apple-touch-icon" sizes="114x114" href="apple-touch-icon-114x114.png"&gt;
&lt;!-- Primeira e segunda geração de iPad --&gt;
&lt;link rel="apple-touch-icon" sizes="72x72" href="apple-touch-icon-72x72.png"&gt;
&lt;!-- Versões antigas de iPhone, iPod Touch e Android 2.2+  --&gt;
&lt;link rel="apple-touch-icon" href="apple-touch-icon.png"&gt;</pre>

Você pode notar que estou declarando as imagens da maior para a menor. Esta é uma boa prática que garante que versões mais antigas do iOS baixem o arquivo de menor tamanho, já que o atributo sizes só foi implantado a partir do iOS 4. Nas versões anteriores por padrão o sistema escolhe a última imagem determinada. Ou seja, é uma questão de progressive enhancement, pois não faz sentido o usuário baixar uma imagem mais pesada em uma tela de resolução mais baixa.

Por padrão o iOS adiciona alguns efeitinhos como cantos arredondados, drop shadow e reflexo. Como nada grita mais web 2.0 do que gelzinhos bregas se você não quiser o reflexo basta utilizar o sufixo &#8220;precomposed&#8221; no nome do seu arquivo.

<pre class="lang-html">&lt;link rel="apple-touch-icon-precomposed" href="apple-touch-icon-precomposed.png"&gt;</pre>

Se você for preguiçoso e só tiver tempo para criar um ícone faça o de 144px que ele será redimensionado automaticamente. Só tenha em mente que a imagem pode perder a qualidade e você estará forçando o usuário a gastar mais banda do que necessário&#8230;

## <span style="color: #ff0000">Atualização &#8211; iOS7</span>

Com a implantação do iOS7 ocorreram algumas modificações no formato Apple Touch Icon. A primeira é com relação ao layout: a Apple retirou os efeitos de gel e transparência a lá web 2.0 (já foi tarde!), portanto não existem mais as versões &#8220;pre-composed&#8221;. Mas a mudança mais significativa ocorreu no tamanho: todos os ícones para iOS7 estão 5% maiores.

Seguem os três novos tamanhos:
  
iPhone / iPod touch retina &#8211; 120px
  
iPad 2 / iPad mini &#8211; 76px
  
iPad retina &#8211; 152px

Como o iOS7 não é compatível com versões do iPhone pré-retina (iPhone 3GS e anterior) não existe um novo formato para ele. Portanto, é recomendável incluir ainda uma versão de 57px para estes aparelhos mais antigos que não tem a possibilidade de atualizar.

As meta-tags ficariam assim:

<pre class="lang-html">&lt;!-- iPad iOS7+ com Retina Display --&gt;
&lt;link rel="apple-touch-icon" sizes="152x152" href="apple-touch-icon-152x152.png"&gt;
&lt;!-- iPhone iOS7+ com Retina Display --&gt;
&lt;link rel="apple-touch-icon" sizes="120x120" href="apple-touch-icon-120x120.png"&gt;
&lt;!-- iPad iOS7+ sem retina display e iPad Mini--&gt;
&lt;link rel="apple-touch-icon" sizes="76x76" href="apple-touch-icon-76x76.png"&gt;
&lt;!-- iPhone iOS7-, iPod Touch e Android 2.2+  --&gt;
&lt;link rel="apple-touch-icon" href="apple-touch-icon.png"&gt;</pre>

Se você for um fanático e quiser garantir a absoluta compatibilidade com todos os aparelhos vai precisar incluir todas as versões antigas de ícones. O código neste caso seria:

<pre class="lang-html">&lt;!-- iPad iOS7+ com Retina Display --&gt;
&lt;link rel="apple-touch-icon" sizes="152x152" href="apple-touch-icon-152x152.png"&gt;
&lt;!-- iPad iOS7- com Retina Display --&gt;
&lt;link rel="apple-touch-icon" sizes="144x144" href="apple-touch-icon-144x144.png"&gt;
&lt;!-- iPhone iOS7+ com Retina Display --&gt;
&lt;link rel="apple-touch-icon" sizes="120x120" href="apple-touch-icon-120x120.png"&gt;
&lt;!-- iPhone iOS7- com Retina Display --&gt;
&lt;link rel="apple-touch-icon" sizes="114x114" href="apple-touch-icon-114x114.png"&gt;
&lt;!-- iPad iOS7+ sem retina display e iPad Mini--&gt;
&lt;link rel="apple-touch-icon" sizes="76x76" href="apple-touch-icon-76x76.png"&gt;
&lt;!-- iPad iOS7- sem retina display  --&gt;
&lt;link rel="apple-touch-icon" sizes="72x72" href="apple-touch-icon-72x72.png"&gt;
&lt;!-- iPhone iOS7-, iPod Touch e Android 2.2+  --&gt;
&lt;link rel="apple-touch-icon" href="apple-touch-icon.png"&gt;</pre>

## Windows 8 Tiles

Se um usuário gostou o suficiente do seu site para querer guarda-lo entre os seus favoritos um ícone deve ser um convite implicito para que ele possa voltar a visita-lo novamente. Se este convite é grande, colorido e uma presença constante na área de trabalho a probabilidade dele retornar é maior ainda, certo?

É o que acontece no Windows 8. Aqueles blocos coloridos de aplicativos da interface Metro, chamados Tiles também podem ser utilizados para salvar favoritos.

O padrão do Windows 8 é utilizar um favicon ou o ícone do próprio Internet Explorer quando um site é fixado como favoritos na tela inicial. Não é preciso ser um gênio do design para deduzir que se aproveitarmos melhor a área disponível &#8211; 144px quadrados &#8211; o resultado seria muito mais bacana.

Para criar uma image tile para o seu site basta utilizar um PNG quadrado de 144px por 144 pixels. O recomendável é utilizar um fundo de arquivo transparente, já que o Windows escolhe automaticamente a cor do fundo com base no tom dominante do seu ícone. É possível ainda escolher a cor do fundo do tile no próprio código HTML através de valores hexadecimais ou rgb. Depois é só apontar o caminho da imagem da seguinte forma:

<pre class="lang-html">&lt;meta name="msapplication-TileImage" content="img/tile.png"/&gt;
&lt;meta name="msapplication-TileColor" content="#FF0000"/&gt;</pre>

Esta imagem só é baixada no momento que o usuário fixa o site como favorito, então não existe nenhum custo de banda adicional.

Existem ainda mais alguns opções avançadas de uso. É possível, por exemplo, criar um arquivo XML que atualiza periodicamente este tile com informações do site. É ótimo para mostrar os últimos posts de um blog, novas promoções de uma loja ou número de mensagens não lidas de uma rede social, por exemplo. Isto significa que o usuário receberá notificações de atualização sem ao menos precisar entrar no site. É possível retornar um valor numérico entre 1 e 99 e ainda mostrar alguns símbolos específicos chamados de glyph badges. [A lista de símbolos disponívels inclui um ícones de mensagem, alerta, atenção, erro, etc.][4] [Este tutorial][5] ensina como criar o XML

É possível &#8211; na verdade desde o Windows 7 &#8211; ainda criar uma [## Favicons

Se você ainda não sabe, Favicons são aqueles pequenos ícones que ficam ao lado da barra de endereços de um navegador e servem, entre outras funções, para identificar rapidamente um site. Os Favicons são um velhos conhecidos dos designers e desenvolvedores. Já são 14 anos de história. E neste meio tempo muita coisa evoluiu. Surgiram smartphones, tablets, televisores, sistemas operacionais modernos, telas de alta resolução e o favicon foi mudando de tamanho, posição e formato, conquistando um espaço muito além da barra de ferramentas do navegador. Neste artigo vamos conhecer mais profundamente esta parte tão importante, mas muitas vezes tão negligenciada, do webdesign.

> A função de um favicon não é apenas ser, como o nome nos leva a deduzir, um símbolo relacionado aos favoritos. Favicons são parte integrante do branding.

O primeiro browser a utilizar favicon foi (pasmem!) o Internet Explorer 5. Naqueles idos tempos de 1999 os simpáticos ícones de 16 pixels tinham outras funções como estimar o número de usuários que favoritavam um site com base em requisições do ícone no servidor. Este método deixou de ter utilidade quando os browsers passaram a exibir favicons também na barra de tarefas, independente do site estar salvo nos favoritos ou não. Mas o nome &#8211; uma junção dos termos favorite e icons &#8211; ficou.

## Função

Ícones podem ter diversos propósitos como representar uma determinada ação, superar barreiras de linguagem, sinalização e/ou transmitir uma mensagem. Você não precisa conhecer a língua local em uma estação de trem de outro país para saber onde é a saída. A figura de um homem passando por uma porta acompanhada de uma seta é suficiente para comunicar esta informação. Da mesma forma, portas de banheiro são demarcadas com silhuetas masculinas ou femininas para você não errar na hora do aperto. Estas representações imagéticas acabam rapidamente se tornando convenções sociais. Não é necessário pensar muito para saber qual botão toca ou pausa um aparelho de som ou vídeo&#8230;

A função de um favicon não é apenas ser, como o nome nos leva a deduzir, um símbolo relacionado aos favoritos. Favicons são parte integrante do branding. Eles servem para representar um website como uma entidade dentro de um browser.

## Design de ícones

Criar um ícone é uma atividade multidisciplinar. Semiótica, gestalt, branding e cultura pop são alguns dos assuntos importantes para se ter em mente na hora de projetar ícones. Pesquisa e bom senso também são fundamentais, afinal, um mesmo símbolo pode ter dezenas de significados diferentes de acordo com idade, sexo, nacionalidade, profissão, religião e cultura do público alvo. Além, é claro, do conhecimento técnico necessário para garantir uniformidade, visibilidade, nitidez e identificação de uma imagem em tamanhos reduzidos. Este artigo não tem a pretensão de ensinar design de ícones, mas sim fornecer informações relevantes para utilizar de maneira mais inteligente os recursos disponíveis em diferentes browsers, sistemas operacionais e aparelhos para fazer da iconografia uma ferramenta de divulgação uma marca.

> O primeiro browser a utilizar favicon foi (pasmem!) o Internet Explorer 5.

Se você precisa de algumas dicas sobre o por que e como criar um ícone vale a pena ler o livro [The Icon Handbook][1] por Jon Hicks.

Existem diversas opções de ferramentas digitais para a criação de ícones. [Desde plugins para Photoshop][2] até alguns softwares exclusivos para este fim. O importante é ter o cuidado de repensar o design com mais ou menos detalhes de acordo com o tamanho do ícone ao invés de simplesmente redimensionar o arquivo. Até mesmo reduções proporcionais podem gerar um resultado distorcido e com baixa nitidez. Como em qualquer outro trabalho, quanto mais tempo e carinho você dedicar para criar o seu ícone melhor será o resultado final. Faça o que fizer, passe longe dos conversores automáticos online! O resultado é tão desastroso quanto um layout WYSIWYG em tabela com gifs animados de gatos tocando teclado.

## Formatos

#### .ICO

Este tipo de arquivo ainda é o mais utilizado devido ao grande suporte por parte dos navegadores e pela opção de conter diversas imagens encapsuladas. Ou seja, em um mesmo arquivo é possível atender diversas funções e resoluções de tela. (E não. Você não vai conseguir isto simplesmente renomeando um .gif ou .png. É necessário buscar um software próprio)/ Mas é necessário cuidado para que o arquivo final não fique muito pesado. Alguns desenvolvedores recomendam um tamanho máximo de 20K.

#### .PNG

Os browsers modernos &#8211; leia-se todo mundo menos o Internet Explorer &#8211; já suportam outras extenções como PNG, por exemplo. As vantagens do PNG é a qualidade maior da imagem, tamanho reduzido e a conveniência na fase de criação. É bem provável que você já tenha no seu computador algum software capaz de salvar ou exportar arquivos para este formato. Mas como não é possível incluir diversas resoluções em um único arquivo é necessário declarar manualmente cada uma das resoluções.

#### Outros formatos

Existe a possibilidade de uso para alguns outros formatos além de ICO e PNG, mas ainda não existem vantagens consistentes para a adoção de nenhum. JPG, por exemplo, não é adequado devido a pixelização das imagens e a falta de um canal de transparência. O GIF tem uma qualidade inferior e ainda não encontrei quem é o cidadão que acha uma boa ideia utilizar APNG (uma espécie de PNG animado).

> Como em qualquer outro trabalho, quanto mais tempo e carinho você dedicar para criar o seu ícone melhor será o resultado final.

Uma opção promissora é o SVG. Como o SVG é um arquivo vetor não teriamos que nos preocupar com os diversos tamanhos. Mas até agora só Opera e o Google Chrome suportam. Então, como grande parte das novidades interessantes, teremos que esperar os outros browsers para começar a brincar&#8230;

Se você tem curiosidade em saber qual navegador aceita o que a partir de qual versão, esta é a tabela de compatibilidade segundo a Wikipedia.

<table>
  <tr>
    <td>
      Browser
    </td>
    
    <td>
      ICO
    </td>
    
    <td>
      PNG
    </td>
    
    <td>
      GIF
    </td>
    
    <td>
      animated GIFs
    </td>
    
    <td>
      JPEG
    </td>
    
    <td>
      APNG
    </td>
    
    <td>
      SVG
    </td>
  </tr>
  
  <tr>
    <td>
      Firefox
    </td>
    
    <td>
      1.0+
    </td>
    
    <td>
      1.0+
    </td>
    
    <td>
      1.0+
    </td>
    
    <td>
      Sim
    </td>
    
    <td>
      Sim
    </td>
    
    <td>
      3.0+
    </td>
    
    <td>
      &#8211;
    </td>
  </tr>
  
  <tr>
    <td>
      Chrome
    </td>
    
    <td>
      Sim
    </td>
    
    <td>
      Sim
    </td>
    
    <td>
      4.0+
    </td>
    
    <td>
      4.0+
    </td>
    
    <td>
      4.0+
    </td>
    
    <td>
      &#8211;
    </td>
    
    <td>
      Sim
    </td>
  </tr>
  
  <tr>
    <td>
      IE
    </td>
    
    <td>
      5.0+
    </td>
    
    <td>
      &#8211;
    </td>
    
    <td>
      &#8211;
    </td>
    
    <td>
      &#8211;
    </td>
    
    <td>
      &#8211;
    </td>
    
    <td>
      &#8211;
    </td>
    
    <td>
      &#8211;
    </td>
  </tr>
  
  <tr>
    <td>
      Opera
    </td>
    
    <td>
      7.0+
    </td>
    
    <td>
      7.0+
    </td>
    
    <td>
      7.0+
    </td>
    
    <td>
      7.0+
    </td>
    
    <td>
      7.0+
    </td>
    
    <td>
      9.5+
    </td>
    
    <td>
      9.6+
    </td>
  </tr>
  
  <tr>
    <td>
      Safari
    </td>
    
    <td>
      Sim
    </td>
    
    <td>
      4.0+
    </td>
    
    <td>
      4.0+
    </td>
    
    <td>
      &#8211;
    </td>
    
    <td>
      4.0+
    </td>
    
    <td>
      &#8211;
    </td>
    
    <td>
      &#8211;
    </td>
  </tr>
</table>

Se quer um conselho amigo passe longe de favicons animados. Além de bregas eles distraem o usuário e passam a impressão que você é carente por atenção.

A melhor pedida é utilizar PNG com um fallback em ICO para o Internet Explorer.

## Tamanho

Aqui começa a confusão. Os favicons clássicos tinham 16px quadrados. Mas hoje grande parte dos browsers utilizam uma versão de 32px. Esta é a versão padrão para a barra de ferramentas do Internet Explorer 10, pro exemplo. Ícones para home screen de dispositivos móveis são outro pepino&#8230; Só o iOS vai ter 4 tamanhos diferentes de acordo com o aparelho e resolução de tela. Ainda existem outras coisas para se considerar como tiles do Windows 8 e quadradinhos do Opera Speed Dial e até mesmo Google TV. Segue uma listinha básica de tamanhos:

**&#8211; 16px:** Barra de endereço, abas e favoritos da maior parte dos navegadores.
  
**&#8211; 24px:** Barra de ferramentas do Internet Explorer 9
  
**&#8211; 32px:** Nova aba no IE, site fixo na barra de tarefas do Windos 7 e sidebar do Safari **&#8211; 57px:** iPhone sem tela retina e iPod Touch
  
**&#8211; 72px:** iPad sem tela retina
  
**&#8211; 96px:** GoogleTV
  
**&#8211; 114px:** iPhone com tela retina
  
**&#8211; 128px:** Chrome Web Store
  
**&#8211; 144px:** iPad Retina, Windows 8 Tiles
  
**&#8211; 256x160px:** Opera Speed Dial

Parece muita coisa, mas raramente você vai precisar utilizar todos estes tamanhos. Isto vai variar de acordo com as necessidades do público alvo de cada projeto, que incluem navegador, aparelho e sistema operacional mais utilizados. Minha recomendação é incluir ao menos o clássico de 16px, uma versão HD de 32px e os touch icons para iOS. Segundo estatísticas da Microsoft um site fixado na barra de tarefas do Windows 7 recebia uma porcentagem de visita de 15% a 50% maior&#8230; Segundo esta lógica criar um tile para o Windows 8 também é uma boa prática, já que as opções de interação se estendem além do navegador.

## Como implementar um favicon

Esta é simples. Basta deixar um arquivo de nome favicon.ico na pasta raíz do servidor. Certo?

Sim e não. Isto funcionaria bem para apenas um arquivo&#8230; Mas se você deseja trabalhar com múltiplos tamanhos e formatos vai ser necessário declarar no HTML. Vamos supor que temos um arquivo favicon.png dentro de uma pasta chamada IMG.

Antigamente você provavelmente faria isto da seguinte maneira:

<pre class="lang-html">&lt;link rel="icon" type="image/png" href="img/favicon.png" /&gt;</pre>

Como somos bacanas e utilizamos HTML5 as coisas ficam mais simples:

<pre class="lang-html">&lt;link rel="icon" href="img/favicon.png" /&gt;</pre>

Okay. Isto funciona para a maior parte dos browsers inteligentes. Falta o fallback para o IE&#8230;

Aviso mega Importante! Não cometa o erro de declarar o png E o ico sem comentários condicionais. Sério. Isto da problemas. Cada navegador possui a sua lógica. Uns vão ler o primeiro que você declarar, outros o último, alguns escolhem aleatoriamente&#8230; Sério! Caos!

Poderíamos fazer o fallback através de comentários condicionais:

<pre class="lang-html">&lt;!--[if IE]&gt;&lt;link rel="shortcut icon" href="img/favicon.ico"&gt;&lt;![endif]--&gt;
&lt;link rel="icon" href="img/favicon.png"&gt;</pre>

Poderíamos&#8230; mas para a Microsoft não basta atrapalhar a vida dos desenvolvedores com os problemas dos navegadores antigos. Ela gosta de criar novos problemas! O IE10 não suporta comentários condicionais. É isto mesmo. A salvação mágica para aquelas longas noites insones desenvolvendo não funciona mais. Pode esquecer. Ah, e não sei se você deu uma espiadinha na tabela lá em cima, mas também não suportam PNG. Legal, né? Bem, são estas pequenas coisas que fazem a vida de um desenvolvedor web preocupado com acessibilidade e experiência do usuário um pouco como resolver quebra cabeças&#8230; Uma solução possível seria declarar apenas o arquivo em PNG e manter o ICO na raíz.

<pre class="lang-html">&lt;link rel="icon" href="img/favicon.png" /&gt;</pre>

Se você desejar incluir diversos tamanhos, basta declarar cada um deles.

<pre class="lang-html">&lt;link rel="icon" href="favicon-16.png" sizes="16x16"&gt;
&lt;link rel="icon" href="favicon-32.png" sizes="32x32"&gt;
&lt;link rel="icon" href="favicon-48.png" sizes="48x48"&gt;
&lt;link rel="icon" href="favicon-64.png" sizes="64x64"&gt;
&lt;link rel="icon" href="favicon-128.png" sizes="128x128"&gt;</pre>

## Apple Touch Icons

No caso de dispositivos que utilizam o sistema iOS (iPhone, iPod e iPad) existe a opção de fixar qualquer site como um favorito diretamente na tela de inicio, independente da existência de uma versão mobile ou design responsivo. Por padrão uma thumbnail é gerada automaticamente a partir de uma screenshot da página, mas o resultado é não apenas visualmente confuso como nada prático do ponto de vista da rápida identificação em meio a tantos outros ícones&#8230; Muitas vezes o usuário pode até resolver desafixar o seu site dali por que deixou a tela &#8220;feia&#8221;. Criar uma imagem exclusiva, chamada apple touch icon, é portanto uma boa prática de usabilidade.

Para isto basta criar 4 imagem quadradas com os cantos retos em formato png nos tamanhos 57px, 72px, 114px e 144px. [## Favicons

Se você ainda não sabe, Favicons são aqueles pequenos ícones que ficam ao lado da barra de endereços de um navegador e servem, entre outras funções, para identificar rapidamente um site. Os Favicons são um velhos conhecidos dos designers e desenvolvedores. Já são 14 anos de história. E neste meio tempo muita coisa evoluiu. Surgiram smartphones, tablets, televisores, sistemas operacionais modernos, telas de alta resolução e o favicon foi mudando de tamanho, posição e formato, conquistando um espaço muito além da barra de ferramentas do navegador. Neste artigo vamos conhecer mais profundamente esta parte tão importante, mas muitas vezes tão negligenciada, do webdesign.

> A função de um favicon não é apenas ser, como o nome nos leva a deduzir, um símbolo relacionado aos favoritos. Favicons são parte integrante do branding.

O primeiro browser a utilizar favicon foi (pasmem!) o Internet Explorer 5. Naqueles idos tempos de 1999 os simpáticos ícones de 16 pixels tinham outras funções como estimar o número de usuários que favoritavam um site com base em requisições do ícone no servidor. Este método deixou de ter utilidade quando os browsers passaram a exibir favicons também na barra de tarefas, independente do site estar salvo nos favoritos ou não. Mas o nome &#8211; uma junção dos termos favorite e icons &#8211; ficou.

## Função

Ícones podem ter diversos propósitos como representar uma determinada ação, superar barreiras de linguagem, sinalização e/ou transmitir uma mensagem. Você não precisa conhecer a língua local em uma estação de trem de outro país para saber onde é a saída. A figura de um homem passando por uma porta acompanhada de uma seta é suficiente para comunicar esta informação. Da mesma forma, portas de banheiro são demarcadas com silhuetas masculinas ou femininas para você não errar na hora do aperto. Estas representações imagéticas acabam rapidamente se tornando convenções sociais. Não é necessário pensar muito para saber qual botão toca ou pausa um aparelho de som ou vídeo&#8230;

A função de um favicon não é apenas ser, como o nome nos leva a deduzir, um símbolo relacionado aos favoritos. Favicons são parte integrante do branding. Eles servem para representar um website como uma entidade dentro de um browser.

## Design de ícones

Criar um ícone é uma atividade multidisciplinar. Semiótica, gestalt, branding e cultura pop são alguns dos assuntos importantes para se ter em mente na hora de projetar ícones. Pesquisa e bom senso também são fundamentais, afinal, um mesmo símbolo pode ter dezenas de significados diferentes de acordo com idade, sexo, nacionalidade, profissão, religião e cultura do público alvo. Além, é claro, do conhecimento técnico necessário para garantir uniformidade, visibilidade, nitidez e identificação de uma imagem em tamanhos reduzidos. Este artigo não tem a pretensão de ensinar design de ícones, mas sim fornecer informações relevantes para utilizar de maneira mais inteligente os recursos disponíveis em diferentes browsers, sistemas operacionais e aparelhos para fazer da iconografia uma ferramenta de divulgação uma marca.

> O primeiro browser a utilizar favicon foi (pasmem!) o Internet Explorer 5.

Se você precisa de algumas dicas sobre o por que e como criar um ícone vale a pena ler o livro [The Icon Handbook][1] por Jon Hicks.

Existem diversas opções de ferramentas digitais para a criação de ícones. [Desde plugins para Photoshop][2] até alguns softwares exclusivos para este fim. O importante é ter o cuidado de repensar o design com mais ou menos detalhes de acordo com o tamanho do ícone ao invés de simplesmente redimensionar o arquivo. Até mesmo reduções proporcionais podem gerar um resultado distorcido e com baixa nitidez. Como em qualquer outro trabalho, quanto mais tempo e carinho você dedicar para criar o seu ícone melhor será o resultado final. Faça o que fizer, passe longe dos conversores automáticos online! O resultado é tão desastroso quanto um layout WYSIWYG em tabela com gifs animados de gatos tocando teclado.

## Formatos

#### .ICO

Este tipo de arquivo ainda é o mais utilizado devido ao grande suporte por parte dos navegadores e pela opção de conter diversas imagens encapsuladas. Ou seja, em um mesmo arquivo é possível atender diversas funções e resoluções de tela. (E não. Você não vai conseguir isto simplesmente renomeando um .gif ou .png. É necessário buscar um software próprio)/ Mas é necessário cuidado para que o arquivo final não fique muito pesado. Alguns desenvolvedores recomendam um tamanho máximo de 20K.

#### .PNG

Os browsers modernos &#8211; leia-se todo mundo menos o Internet Explorer &#8211; já suportam outras extenções como PNG, por exemplo. As vantagens do PNG é a qualidade maior da imagem, tamanho reduzido e a conveniência na fase de criação. É bem provável que você já tenha no seu computador algum software capaz de salvar ou exportar arquivos para este formato. Mas como não é possível incluir diversas resoluções em um único arquivo é necessário declarar manualmente cada uma das resoluções.

#### Outros formatos

Existe a possibilidade de uso para alguns outros formatos além de ICO e PNG, mas ainda não existem vantagens consistentes para a adoção de nenhum. JPG, por exemplo, não é adequado devido a pixelização das imagens e a falta de um canal de transparência. O GIF tem uma qualidade inferior e ainda não encontrei quem é o cidadão que acha uma boa ideia utilizar APNG (uma espécie de PNG animado).

> Como em qualquer outro trabalho, quanto mais tempo e carinho você dedicar para criar o seu ícone melhor será o resultado final.

Uma opção promissora é o SVG. Como o SVG é um arquivo vetor não teriamos que nos preocupar com os diversos tamanhos. Mas até agora só Opera e o Google Chrome suportam. Então, como grande parte das novidades interessantes, teremos que esperar os outros browsers para começar a brincar&#8230;

Se você tem curiosidade em saber qual navegador aceita o que a partir de qual versão, esta é a tabela de compatibilidade segundo a Wikipedia.

<table>
  <tr>
    <td>
      Browser
    </td>
    
    <td>
      ICO
    </td>
    
    <td>
      PNG
    </td>
    
    <td>
      GIF
    </td>
    
    <td>
      animated GIFs
    </td>
    
    <td>
      JPEG
    </td>
    
    <td>
      APNG
    </td>
    
    <td>
      SVG
    </td>
  </tr>
  
  <tr>
    <td>
      Firefox
    </td>
    
    <td>
      1.0+
    </td>
    
    <td>
      1.0+
    </td>
    
    <td>
      1.0+
    </td>
    
    <td>
      Sim
    </td>
    
    <td>
      Sim
    </td>
    
    <td>
      3.0+
    </td>
    
    <td>
      &#8211;
    </td>
  </tr>
  
  <tr>
    <td>
      Chrome
    </td>
    
    <td>
      Sim
    </td>
    
    <td>
      Sim
    </td>
    
    <td>
      4.0+
    </td>
    
    <td>
      4.0+
    </td>
    
    <td>
      4.0+
    </td>
    
    <td>
      &#8211;
    </td>
    
    <td>
      Sim
    </td>
  </tr>
  
  <tr>
    <td>
      IE
    </td>
    
    <td>
      5.0+
    </td>
    
    <td>
      &#8211;
    </td>
    
    <td>
      &#8211;
    </td>
    
    <td>
      &#8211;
    </td>
    
    <td>
      &#8211;
    </td>
    
    <td>
      &#8211;
    </td>
    
    <td>
      &#8211;
    </td>
  </tr>
  
  <tr>
    <td>
      Opera
    </td>
    
    <td>
      7.0+
    </td>
    
    <td>
      7.0+
    </td>
    
    <td>
      7.0+
    </td>
    
    <td>
      7.0+
    </td>
    
    <td>
      7.0+
    </td>
    
    <td>
      9.5+
    </td>
    
    <td>
      9.6+
    </td>
  </tr>
  
  <tr>
    <td>
      Safari
    </td>
    
    <td>
      Sim
    </td>
    
    <td>
      4.0+
    </td>
    
    <td>
      4.0+
    </td>
    
    <td>
      &#8211;
    </td>
    
    <td>
      4.0+
    </td>
    
    <td>
      &#8211;
    </td>
    
    <td>
      &#8211;
    </td>
  </tr>
</table>

Se quer um conselho amigo passe longe de favicons animados. Além de bregas eles distraem o usuário e passam a impressão que você é carente por atenção.

A melhor pedida é utilizar PNG com um fallback em ICO para o Internet Explorer.

## Tamanho

Aqui começa a confusão. Os favicons clássicos tinham 16px quadrados. Mas hoje grande parte dos browsers utilizam uma versão de 32px. Esta é a versão padrão para a barra de ferramentas do Internet Explorer 10, pro exemplo. Ícones para home screen de dispositivos móveis são outro pepino&#8230; Só o iOS vai ter 4 tamanhos diferentes de acordo com o aparelho e resolução de tela. Ainda existem outras coisas para se considerar como tiles do Windows 8 e quadradinhos do Opera Speed Dial e até mesmo Google TV. Segue uma listinha básica de tamanhos:

**&#8211; 16px:** Barra de endereço, abas e favoritos da maior parte dos navegadores.
  
**&#8211; 24px:** Barra de ferramentas do Internet Explorer 9
  
**&#8211; 32px:** Nova aba no IE, site fixo na barra de tarefas do Windos 7 e sidebar do Safari **&#8211; 57px:** iPhone sem tela retina e iPod Touch
  
**&#8211; 72px:** iPad sem tela retina
  
**&#8211; 96px:** GoogleTV
  
**&#8211; 114px:** iPhone com tela retina
  
**&#8211; 128px:** Chrome Web Store
  
**&#8211; 144px:** iPad Retina, Windows 8 Tiles
  
**&#8211; 256x160px:** Opera Speed Dial

Parece muita coisa, mas raramente você vai precisar utilizar todos estes tamanhos. Isto vai variar de acordo com as necessidades do público alvo de cada projeto, que incluem navegador, aparelho e sistema operacional mais utilizados. Minha recomendação é incluir ao menos o clássico de 16px, uma versão HD de 32px e os touch icons para iOS. Segundo estatísticas da Microsoft um site fixado na barra de tarefas do Windows 7 recebia uma porcentagem de visita de 15% a 50% maior&#8230; Segundo esta lógica criar um tile para o Windows 8 também é uma boa prática, já que as opções de interação se estendem além do navegador.

## Como implementar um favicon

Esta é simples. Basta deixar um arquivo de nome favicon.ico na pasta raíz do servidor. Certo?

Sim e não. Isto funcionaria bem para apenas um arquivo&#8230; Mas se você deseja trabalhar com múltiplos tamanhos e formatos vai ser necessário declarar no HTML. Vamos supor que temos um arquivo favicon.png dentro de uma pasta chamada IMG.

Antigamente você provavelmente faria isto da seguinte maneira:

<pre class="lang-html">&lt;link rel="icon" type="image/png" href="img/favicon.png" /&gt;</pre>

Como somos bacanas e utilizamos HTML5 as coisas ficam mais simples:

<pre class="lang-html">&lt;link rel="icon" href="img/favicon.png" /&gt;</pre>

Okay. Isto funciona para a maior parte dos browsers inteligentes. Falta o fallback para o IE&#8230;

Aviso mega Importante! Não cometa o erro de declarar o png E o ico sem comentários condicionais. Sério. Isto da problemas. Cada navegador possui a sua lógica. Uns vão ler o primeiro que você declarar, outros o último, alguns escolhem aleatoriamente&#8230; Sério! Caos!

Poderíamos fazer o fallback através de comentários condicionais:

<pre class="lang-html">&lt;!--[if IE]&gt;&lt;link rel="shortcut icon" href="img/favicon.ico"&gt;&lt;![endif]--&gt;
&lt;link rel="icon" href="img/favicon.png"&gt;</pre>

Poderíamos&#8230; mas para a Microsoft não basta atrapalhar a vida dos desenvolvedores com os problemas dos navegadores antigos. Ela gosta de criar novos problemas! O IE10 não suporta comentários condicionais. É isto mesmo. A salvação mágica para aquelas longas noites insones desenvolvendo não funciona mais. Pode esquecer. Ah, e não sei se você deu uma espiadinha na tabela lá em cima, mas também não suportam PNG. Legal, né? Bem, são estas pequenas coisas que fazem a vida de um desenvolvedor web preocupado com acessibilidade e experiência do usuário um pouco como resolver quebra cabeças&#8230; Uma solução possível seria declarar apenas o arquivo em PNG e manter o ICO na raíz.

<pre class="lang-html">&lt;link rel="icon" href="img/favicon.png" /&gt;</pre>

Se você desejar incluir diversos tamanhos, basta declarar cada um deles.

<pre class="lang-html">&lt;link rel="icon" href="favicon-16.png" sizes="16x16"&gt;
&lt;link rel="icon" href="favicon-32.png" sizes="32x32"&gt;
&lt;link rel="icon" href="favicon-48.png" sizes="48x48"&gt;
&lt;link rel="icon" href="favicon-64.png" sizes="64x64"&gt;
&lt;link rel="icon" href="favicon-128.png" sizes="128x128"&gt;</pre>

## Apple Touch Icons

No caso de dispositivos que utilizam o sistema iOS (iPhone, iPod e iPad) existe a opção de fixar qualquer site como um favorito diretamente na tela de inicio, independente da existência de uma versão mobile ou design responsivo. Por padrão uma thumbnail é gerada automaticamente a partir de uma screenshot da página, mas o resultado é não apenas visualmente confuso como nada prático do ponto de vista da rápida identificação em meio a tantos outros ícones&#8230; Muitas vezes o usuário pode até resolver desafixar o seu site dali por que deixou a tela &#8220;feia&#8221;. Criar uma imagem exclusiva, chamada apple touch icon, é portanto uma boa prática de usabilidade.

Para isto basta criar 4 imagem quadradas com os cantos retos em formato png nos tamanhos 57px, 72px, 114px e 144px.][3]  quebra um galho nesta hora.

Depois é só nomear os arquivos com o prefixo &#8220;apple-touch-icon&#8221; e colocar na raíz do diretório. A vantagem disto é que você economiza algumas linhas de código, mas em alguns casos como em um tema para tumblr, por exemplo, não temos acesso a pasta raiz. Nestas horas é importante declarar o caminho no HTML. Outra vantagem em apontar o caminho do ícone no código é a acessibilidade. Não importa se o seu usuário é fanboy da Apple ou não. Quando devidamente apontados, os touch icons também são utilizados pelo Android (a partir da versão 2.2) e em alguns outros aplicativos como o Reeder para iPad.

Bem, prepare seus icones e cole isto aqui entre as tags head do seu HTML e seja feliz:

<pre class="lang-html">&lt;!-- iPad com Retina Display --&gt;
&lt;link rel="apple-touch-icon" sizes="144x144" href="apple-touch-icon-144x144.png"&gt;
&lt;!-- iPhone com Retina Display --&gt;
&lt;link rel="apple-touch-icon" sizes="114x114" href="apple-touch-icon-114x114.png"&gt;
&lt;!-- Primeira e segunda geração de iPad --&gt;
&lt;link rel="apple-touch-icon" sizes="72x72" href="apple-touch-icon-72x72.png"&gt;
&lt;!-- Versões antigas de iPhone, iPod Touch e Android 2.2+  --&gt;
&lt;link rel="apple-touch-icon" href="apple-touch-icon.png"&gt;</pre>

Você pode notar que estou declarando as imagens da maior para a menor. Esta é uma boa prática que garante que versões mais antigas do iOS baixem o arquivo de menor tamanho, já que o atributo sizes só foi implantado a partir do iOS 4. Nas versões anteriores por padrão o sistema escolhe a última imagem determinada. Ou seja, é uma questão de progressive enhancement, pois não faz sentido o usuário baixar uma imagem mais pesada em uma tela de resolução mais baixa.

Por padrão o iOS adiciona alguns efeitinhos como cantos arredondados, drop shadow e reflexo. Como nada grita mais web 2.0 do que gelzinhos bregas se você não quiser o reflexo basta utilizar o sufixo &#8220;precomposed&#8221; no nome do seu arquivo.

<pre class="lang-html">&lt;link rel="apple-touch-icon-precomposed" href="apple-touch-icon-precomposed.png"&gt;</pre>

Se você for preguiçoso e só tiver tempo para criar um ícone faça o de 144px que ele será redimensionado automaticamente. Só tenha em mente que a imagem pode perder a qualidade e você estará forçando o usuário a gastar mais banda do que necessário&#8230;

## <span style="color: #ff0000">Atualização &#8211; iOS7</span>

Com a implantação do iOS7 ocorreram algumas modificações no formato Apple Touch Icon. A primeira é com relação ao layout: a Apple retirou os efeitos de gel e transparência a lá web 2.0 (já foi tarde!), portanto não existem mais as versões &#8220;pre-composed&#8221;. Mas a mudança mais significativa ocorreu no tamanho: todos os ícones para iOS7 estão 5% maiores.

Seguem os três novos tamanhos:
  
iPhone / iPod touch retina &#8211; 120px
  
iPad 2 / iPad mini &#8211; 76px
  
iPad retina &#8211; 152px

Como o iOS7 não é compatível com versões do iPhone pré-retina (iPhone 3GS e anterior) não existe um novo formato para ele. Portanto, é recomendável incluir ainda uma versão de 57px para estes aparelhos mais antigos que não tem a possibilidade de atualizar.

As meta-tags ficariam assim:

<pre class="lang-html">&lt;!-- iPad iOS7+ com Retina Display --&gt;
&lt;link rel="apple-touch-icon" sizes="152x152" href="apple-touch-icon-152x152.png"&gt;
&lt;!-- iPhone iOS7+ com Retina Display --&gt;
&lt;link rel="apple-touch-icon" sizes="120x120" href="apple-touch-icon-120x120.png"&gt;
&lt;!-- iPad iOS7+ sem retina display e iPad Mini--&gt;
&lt;link rel="apple-touch-icon" sizes="76x76" href="apple-touch-icon-76x76.png"&gt;
&lt;!-- iPhone iOS7-, iPod Touch e Android 2.2+  --&gt;
&lt;link rel="apple-touch-icon" href="apple-touch-icon.png"&gt;</pre>

Se você for um fanático e quiser garantir a absoluta compatibilidade com todos os aparelhos vai precisar incluir todas as versões antigas de ícones. O código neste caso seria:

<pre class="lang-html">&lt;!-- iPad iOS7+ com Retina Display --&gt;
&lt;link rel="apple-touch-icon" sizes="152x152" href="apple-touch-icon-152x152.png"&gt;
&lt;!-- iPad iOS7- com Retina Display --&gt;
&lt;link rel="apple-touch-icon" sizes="144x144" href="apple-touch-icon-144x144.png"&gt;
&lt;!-- iPhone iOS7+ com Retina Display --&gt;
&lt;link rel="apple-touch-icon" sizes="120x120" href="apple-touch-icon-120x120.png"&gt;
&lt;!-- iPhone iOS7- com Retina Display --&gt;
&lt;link rel="apple-touch-icon" sizes="114x114" href="apple-touch-icon-114x114.png"&gt;
&lt;!-- iPad iOS7+ sem retina display e iPad Mini--&gt;
&lt;link rel="apple-touch-icon" sizes="76x76" href="apple-touch-icon-76x76.png"&gt;
&lt;!-- iPad iOS7- sem retina display  --&gt;
&lt;link rel="apple-touch-icon" sizes="72x72" href="apple-touch-icon-72x72.png"&gt;
&lt;!-- iPhone iOS7-, iPod Touch e Android 2.2+  --&gt;
&lt;link rel="apple-touch-icon" href="apple-touch-icon.png"&gt;</pre>

## Windows 8 Tiles

Se um usuário gostou o suficiente do seu site para querer guarda-lo entre os seus favoritos um ícone deve ser um convite implicito para que ele possa voltar a visita-lo novamente. Se este convite é grande, colorido e uma presença constante na área de trabalho a probabilidade dele retornar é maior ainda, certo?

É o que acontece no Windows 8. Aqueles blocos coloridos de aplicativos da interface Metro, chamados Tiles também podem ser utilizados para salvar favoritos.

O padrão do Windows 8 é utilizar um favicon ou o ícone do próprio Internet Explorer quando um site é fixado como favoritos na tela inicial. Não é preciso ser um gênio do design para deduzir que se aproveitarmos melhor a área disponível &#8211; 144px quadrados &#8211; o resultado seria muito mais bacana.

Para criar uma image tile para o seu site basta utilizar um PNG quadrado de 144px por 144 pixels. O recomendável é utilizar um fundo de arquivo transparente, já que o Windows escolhe automaticamente a cor do fundo com base no tom dominante do seu ícone. É possível ainda escolher a cor do fundo do tile no próprio código HTML através de valores hexadecimais ou rgb. Depois é só apontar o caminho da imagem da seguinte forma:

<pre class="lang-html">&lt;meta name="msapplication-TileImage" content="img/tile.png"/&gt;
&lt;meta name="msapplication-TileColor" content="#FF0000"/&gt;</pre>

Esta imagem só é baixada no momento que o usuário fixa o site como favorito, então não existe nenhum custo de banda adicional.

Existem ainda mais alguns opções avançadas de uso. É possível, por exemplo, criar um arquivo XML que atualiza periodicamente este tile com informações do site. É ótimo para mostrar os últimos posts de um blog, novas promoções de uma loja ou número de mensagens não lidas de uma rede social, por exemplo. Isto significa que o usuário receberá notificações de atualização sem ao menos precisar entrar no site. É possível retornar um valor numérico entre 1 e 99 e ainda mostrar alguns símbolos específicos chamados de glyph badges. [A lista de símbolos disponívels inclui um ícones de mensagem, alerta, atenção, erro, etc.][4] [Este tutorial][5] ensina como criar o XML

É possível &#8211; na verdade desde o Windows 7 &#8211; ainda criar uma][6]  ou [gerada dinamicamente][7] através da interação do usuário para que ele visite diretamente através da tile.

## Conclusão

As vezes são os detalhes que fazem toda a diferença. Criar um ícone projetado especificamente para melhor atender cada situação pode dar um pouquinho a mais de trabalho, mas certamente garante uma melhor integração entre o site o usuário final e, consequentemente, uma divulgação maior da marca. Quem fizer o esforço a mais certamente será ganhará destaque na barra de favoritos, home screen ou área de trabalho, ganhando assim mais visitas e o principal &#8211; clientes e usuários mais felizes.

#### Leia mais

[Understand the Favicon][8]
  
[Create perfect favicon][9]
  
[The icon handbook][1]
  
[Touch Icons][10]
  
[Pinned sites in windows 8][5]

 [1]: http://www.fivesimplesteps.com/products/the-icon-handbook
 [2]: http://www.telegraphics.com.au/sw/
 [3]: http://appicontemplate.com/
 [4]: http://msdn.microsoft.com/en-us/library/windows/apps/br212849.aspx
 [5]: http://blogs.msdn.com/b/ie/archive/2012/04/03/pinned-sites-in-windows-8.aspx
 [6]: http://msdn.microsoft.com/en-us/library/gg491725(v=vs.85).aspx
 [7]: http://msdn.microsoft.com/en-us/library/gg491724(v=vs.85).aspx
 [8]: http://www.jonathantneal.com/blog/understand-the-favicon/
 [9]: http://www.netmagazine.com/features/create-perfect-favicon
 [10]: http://mathiasbynens.be/notes/touch-icons