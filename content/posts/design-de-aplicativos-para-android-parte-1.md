---
title: Design de Aplicativos para Android – Parte 1
author: Dani Guerrato
type: post
date: 2014-01-27
excerpt: Conheça mais sobre a plataforma e veja quais são os primeiros passos para projetar suas próprias aplicações.
url: /design-de-aplicativos-para-android-parte-1/
dsq_thread_id: 2179663213
categories:
  - Design
  - Mobile
tags:
  - android
  - design de aplicativos
  - mobile

---
## Uma questão de motivação

Recentemente participei de uma maratona de desenvolvimento chamada [Google Developer Bus][1]  onde encarei o seguinte desafio: criar o layout para um aplicativo Android em apenas 3 dias. Já trabalho há alguns anos com design para a web e, quem acompanha meus textos sabe, sou uma grande evangelista do design responsivo. Mas esta experiência anterior não foi o suficiente para me preparar para a tarefa. Criar aplicativos nativos é algo completamente diferente! Envolve um pouco de matemática, muita paciência e conhecimento do sistema.

A ausência de material didático também representa um empecilho. Fora a [documentação oficial][2], existe pouquíssimo material disponível para designers… Este é um dado surpreendente considerando que o Android é atualmente o sistema operacional móvel mais popular do mundo com [81% de market share][3].  Pensando nisto decidi criar uma série de artigos sobre o tema voltados para quem, como eu, é iniciante na área. Minha intenção é dividir com vocês o que aprendi e compartilhar algumas dicas e atalhos para criar apps bonitos, funcionais e coerentes com as guidelines específicas da plataforma. Pense neste artigo como um starter kit para você que pretende se aventurar pelo maravilhoso mundo do design de aplicativos e não faz idéia por onde começar.

Nesta primeira etapa vamos conhecer de perto a estrutura e navegação do Android e as principais diferenças entre outros sistema operacionais móveis. Este artigo foi criado tendo em mente as diretrizes para a versão do **Android 4.4 KitKat**.

## Conheça o Android

O primeiro passo para criar bons aplicativos para Android é: passe algum tempo se familiarizando com o sistema. Parece um ponto óbvio, mas muitas pessoas ignoram esta etapa e acabam criando aplicativos inconsistentes. Se você possui um aparelho, baixe alguns apps e explore todas as telas. Tente encontrar, dentre cases bem sucedidos, quais pontos eles tem em comum e quais pontos eles diferem. Se você está a procura de inspiração pode procurar por showcases específicos como o [Android Niceties][4] e [Android App Patterns][5]. Mas não é necessário se limitar a isto. O próprio [Google Play][6] (loja de apps do Google) fornece screenshots de todos os aplicativos. Veja quais são os mais populares e conheça seus prováveis concorrentes. Vale até criar uma pequena biblioteca de inspiração em uma pastinha no computador ou em alguma rede como [Kippt][7] ou [Pinterest][8]. Quanto mais você se cercar de boas idéias, mais fácil será para desenvolver a sua.

## A anatomia de um App

Ser um usuário de aparelho Android não qualifica você automaticamente um especialista no sistema. Conhecer a anatomia de uma interface Android (e no que ela difere de outros sistemas operacionais como iOS e Windows Phone) é fundamental para criar bons aplicativos. Vamos explorar a diagramação padrão de um aplicativo.

### Action Bar (Barra de Ação)

A barra de ação é equivalente a seção header de um site:  logotipo, título da página e itens de navegação. Esta barra deve ser flexível para acomodar ícones, menus ou caixas de texto expansíveis. O espaço também é utilizado para notificações de itens novos, alertas em geral e trocas de modo de visualização quando existe esta função (lista ou grid, por exemplo).

<img class="alignnone size-full wp-image-40477" alt="action-bar" src="http://tableless.com.br/uploads/2014/01/action-bar.jpg" width="660" height="400" srcset="uploads/2014/01/action-bar.jpg 660w, uploads/2014/01/action-bar-277x168.jpg 277w, uploads/2014/01/action-bar-511x310.jpg 511w" sizes="(max-width: 660px) 100vw, 660px" />

#### Branding

Este espaço é destinado a logo ou ícone do app.

#### Action Icons (Ícones de Ação)

Do centro para o canto direito temos Action Icons, ou ícones de ação. Estes ícones servem de atalho para representar ações globais frequentes que um usuário poderá realizar no seu app como buscar uma informação ou compartilhar conteúdo.

Normalmente são exibidos de 2 a 5 ícones, dependendo do tamanho da área de exibição do aparelho. Se mesmo assim você achar que não é suficiente organize as ações que não couberem na action bar em um menu complementar dropdown chamado **Action Overflow** (ícone de três quadradinhos pequenos). Lembre-se de exibir apenas os ícones de ações que estão disponíveis naquele momento. Se não é possível realizar uma determinada ação dentro de uma tela, esconda o ícone!

É muito importante que cada ícone represente claramente o conceito. O ideal seria sempre procurar no [conjunto de ícones oficiais][9] se já existe um ícone padrão do Android para a ação que você deseja realizar. Desta maneira você garante a consistência do aplicativo e que o usuário não precise pensar muito para deduzir o que o seu ícone faz, já que ele já viu a mesma ação em outros lugares. Uma das dicas de ouro da documentação oficial é: se parece igual, deve funcionar igual. Ações como compartilhar ou buscar, por exemplo, devem usar os ícones padrões. Você pode personalizar estes ícones trocando cores e adicionando efeitos sutis para que reflita o seu branding, mas sem que isto afete a essência do ícone.

[<img class="alignnone size-full wp-image-40494" alt="action-icons-android" src="http://tableless.com.br/uploads/2014/01/action-icons-android.jpg" width="660" height="400" srcset="uploads/2014/01/action-icons-android.jpg 660w, uploads/2014/01/action-icons-android-277x168.jpg 277w, uploads/2014/01/action-icons-android-511x310.jpg 511w" sizes="(max-width: 660px) 100vw, 660px" />][10]

#### Navigation Drawer (Gaveta de Navegação)

Menu de navegação que surge da esquerda para a direita, cobrindo o conteúdo do aplicativo. Para abrir a gaveta basta clicar no ícone (três risquinhos) ao lado esquerdo do logotipo.

#### Contextual Action Bar (Barra de Ação Contextual)

A Contextual Action Bar, ou CAB para os íntimos, é uma barra de ação temporária que substitui os itens padrões durante uma determinada tarefa. Exemplo: exibir quantos elementos de uma lista foram selecionados.

<img class="alignnone size-full wp-image-40480" alt="contextal-action-bar" src="http://tableless.com.br/uploads/2014/01/contextal-action-bar.jpg" width="660" height="400" srcset="uploads/2014/01/contextal-action-bar.jpg 660w, uploads/2014/01/contextal-action-bar-277x168.jpg 277w, uploads/2014/01/contextal-action-bar-511x310.jpg 511w" sizes="(max-width: 660px) 100vw, 660px" />

#### Das diferentes maneiras de voltar

Uma das principais características do Android é que o botão voltar está sempre presente, seja como um botão físico no hardware ou um equivalente virtual do sistema. A função deste botão é voltar para a última tela em ordem cronológica e isto pode significar, muitas vezes, sair do aplicativo atual. O botão de voltar, portanto, reflete sempre o seu histórico de navegação. Seria redundante ter a mesma função repetida dentro do seu aplicativo&#8230; Ao invés disto podemos fazer uso do botão **Up**, simbolizado por uma seta voltada para a esquerda na barra de ação ao lado do logotipo. A idéia deste ícone é voltar para uma tela relacionada, de nível acima da atual. Vamos supor que você esteja na dashboard do Youtube, por exemplo e navegou para uma lista de reproduções de vídeos. O Up faria você voltar da tela &#8220;filha&#8221; para a tela &#8220;pai&#8221;. Ou seja, de volta da lista de vídeos para a dashboard. Por isto que, na tela inicial de uma aplicativo, não existe botão up pois você já está no primeiro nível da hierarquia.

<img class="alignnone size-full wp-image-40486" alt="up-back" src="http://tableless.com.br/uploads/2014/01/up-back.jpg" width="660" height="400" srcset="uploads/2014/01/up-back.jpg 660w, uploads/2014/01/up-back-277x168.jpg 277w, uploads/2014/01/up-back-511x310.jpg 511w" sizes="(max-width: 660px) 100vw, 660px" />

### Bottom Bar (barra inferior)

Espaço localizado no rodapé do aplicativo de maneira fixa. Serve como um complemento da barra de ação, exibindo outros ícones de ação que você julgar importante.

<img class="alignnone size-full wp-image-40479" alt="bottom-bar" src="http://tableless.com.br/uploads/2014/01/bottom-bar.jpg" width="660" height="400" srcset="uploads/2014/01/bottom-bar.jpg 660w, uploads/2014/01/bottom-bar-277x168.jpg 277w, uploads/2014/01/bottom-bar-511x310.jpg 511w" sizes="(max-width: 660px) 100vw, 660px" />

## Tipos de Navegação

Já falamos um pouco sobre gavetas de navegação, mas existem diversos outros tipos de menu; cada um é mais apropriado para um tipo de situação. Vamos a eles!

### Fixed Tabs (Abas Fixas)

As Fixed Tabs ficam no topo do aplicativo, logo abaixo da Barra de Ação. O conceito aqui é deixar os itens do menu sempre a vista, para que o usuário possa navegar rapidamente entre as seções internas do aplicativo tocando na tab ou através de um swipe para esquerda ou para a direta. Este tipo de navegação em abas é ideal para quando você espera que o usuário alterne entre as telas frequentemente. O contra é que, por conta das diferenças de largura dos aparelhos, as abas fixas só acomodam confortavelmente três itens no máximo.

### Scrollable Tabs (Abas roláveis )

O funcionamento é bem parecido com as abas fixas, com a diferença que o usuário poderá deslizar para o lado para visualizar mais itens. O recurso combina a praticidade das abas fixas com a possibilidade maior de exibição. Mas não abuse! O ideal é utilizar de 5 a 7 abas no máximo.

<img class="alignnone size-full wp-image-40485" alt="tabs" src="http://tableless.com.br/uploads/2014/01/tabs.jpg" width="660" height="400" srcset="uploads/2014/01/tabs.jpg 660w, uploads/2014/01/tabs-277x168.jpg 277w, uploads/2014/01/tabs-511x310.jpg 511w" sizes="(max-width: 660px) 100vw, 660px" />

### Spinners

Um Spinner é um menu drop-down simbolizado por um pequeno triângulo no canto inferior direito da âncora. É comum posicionar um Spinner abaixo do logotipo do aplicativo para sinalizar o menu. Mas você pode utilizar Spinners sempre que quiser otimizar o espaço ou mostrar diversas opções de dados como em um campo de formulário com múltiplas opções (estilo select), alternar entre duas contas de um serviço ou escolher datas em um calendário.

<img class="alignnone size-full wp-image-40484" alt="spinner" src="http://tableless.com.br/uploads/2014/01/spinner.jpg" width="660" height="400" srcset="uploads/2014/01/spinner.jpg 660w, uploads/2014/01/spinner-277x168.jpg 277w, uploads/2014/01/spinner-511x310.jpg 511w" sizes="(max-width: 660px) 100vw, 660px" />

### Navigation Drawer (Gaveta de Navegação)

Menu que escorrega da esquerda para a direita. É ótimo para navegação complexas (3 ou mais itens) já que é um menu global que pode ser acessado de qualquer lugar do app. É especialmente útil para navegação multinivel e para economia de espaço da tela. O ponto contra é que a gaveta fica sempre escondida, o que leva um pouco mais de tempo para o usuário descobrir e acessar.

<img class="alignnone size-full wp-image-40483" alt="navigation-drawer" src="http://tableless.com.br/uploads/2014/01/navigation-drawer.jpg" width="660" height="400" srcset="uploads/2014/01/navigation-drawer.jpg 660w, uploads/2014/01/navigation-drawer-277x168.jpg 277w, uploads/2014/01/navigation-drawer-511x310.jpg 511w" sizes="(max-width: 660px) 100vw, 660px" />

### Não misture tipos de navegação

Evite misturar diversos tipos de navegação ao mesmo tempo pois isto pode confundir o usuário. Prefira basear sua escolha em critérios como quantidade de itens, frequência de uso e importância.

### Conteúdo primeiro!

Alguns aplicativos mais antigos exibem um layout estilo dashboard mostrando apenas a navegação na tela inicial. Esta é uma abordagem confusa que afasta as pessoas do que elas realmente vieram ali para ver: o conteúdo! Valorize o tempo do seu usuário e prefira sempre utilizar uma abordagem mais direta mostrando na tela inicial o que você tiver de mais interessante para oferecer.

<img class="alignnone size-full wp-image-40495" alt="distribuicao-de-conteudo" src="http://tableless.com.br/uploads/2014/01/distribuicao-de-conteudo.jpg" width="660" height="400" srcset="uploads/2014/01/distribuicao-de-conteudo.jpg 660w, uploads/2014/01/distribuicao-de-conteudo-277x168.jpg 277w, uploads/2014/01/distribuicao-de-conteudo-511x310.jpg 511w" sizes="(max-width: 660px) 100vw, 660px" />

## Não reutilize layouts de outros sistemas

Sim. Isto significa que para dar suporte a diversas plataformas você terá que repensar todo o design do seu app! E o motivo para isto acontecer é que os sistemas operacionais móveis, embora tenham praticamente as mesmas funcionalidades, são estruturados de maneira completamente diferente.

Só a título de comparação vamos dar uma olhadinha no aplicativo do WhatsApp nas três plataformas. As diferenças já começam nos ícones de lançamento do aplicativo. No Android eles podem possuir qualquer formato e normalmente tem algum efeito de profundidade já que são usados arquivos com transparência. Já no iPhone eles são quadrados com cantos arredondados e no Windows Phone são tiles animados que mostram informações em tempo real e podem ter cores e tamanhos diferentes. Ufa! E nem abrimos o app ainda…

<img class="alignnone size-full wp-image-40482" alt="launcher-icons" src="http://tableless.com.br/uploads/2014/01/launcher-icons.jpg" width="660" height="400" srcset="uploads/2014/01/launcher-icons.jpg 660w, uploads/2014/01/launcher-icons-277x168.jpg 277w, uploads/2014/01/launcher-icons-511x310.jpg 511w" sizes="(max-width: 660px) 100vw, 660px" />

Por dentro as diferenças vão ficando mais expressivas. A função de voltar, que já comentamos neste artigo, é um exemplo disto. No Android e no Windows Phone existem botões do sistema específicos para esta função. O iPhone só possui o botão Home&#8230; Pra facilitar a vida do usuário e acrescentar esta função os aplicativos normalmente ocupam o canto superior esquerdo com uma seta ou botão rotulado voltar. Esta é exatamente a área de branding / gaveta de navegação no Android. Já no Windows Phone neste cantinho normalmente fica marcado o nome do app e logo abaixo a navegação (que é toda tipográfica e comandada por swipes). As cores e texturas dos sistemas também são bem diferentes.

<img class="alignnone size-full wp-image-40488" alt="whats-app" src="http://tableless.com.br/uploads/2014/01/whats-app.jpg" width="660" height="400" srcset="uploads/2014/01/whats-app.jpg 660w, uploads/2014/01/whats-app-277x168.jpg 277w, uploads/2014/01/whats-app-511x310.jpg 511w" sizes="(max-width: 660px) 100vw, 660px" />

Os ícones de ação são outra diferença crucial. No Android eles devem ficar na barra superior, já no iPhone e Windows Phone estes ícones são posicionados em uma barra fixa no rodapé… Os símbolos e formatos também são bem diferentes.

<img class="alignnone size-full wp-image-40481" alt="icones" src="http://tableless.com.br/uploads/2014/01/icones.jpg" width="660" height="400" srcset="uploads/2014/01/icones.jpg 660w, uploads/2014/01/icones-277x168.jpg 277w, uploads/2014/01/icones-511x310.jpg 511w" sizes="(max-width: 660px) 100vw, 660px" />

Fora as diferenças estilísticas da user interface como cantos arredondados, gradientes, tipografia, tamanhos e nem vou começar a falar sobre resoluções (Spoiler alert: este é tema do próximo artigo).

<img class="alignnone size-full wp-image-40487" alt="user-interface" src="http://tableless.com.br/uploads/2014/01/user-interface.jpg" width="660" height="400" srcset="uploads/2014/01/user-interface.jpg 660w, uploads/2014/01/user-interface-277x168.jpg 277w, uploads/2014/01/user-interface-511x310.jpg 511w" sizes="(max-width: 660px) 100vw, 660px" />

Moral da história: procure sempre planejar o layout levando em conta a experiência de cada sistema operacional. Explore os pontos fortes de cada um, tente contornar as fraquezas e use itens padronizados a seu favor. Seu usuário vai agradecer no final!

## Conclusão

Bem, agora que você já conhece a estrutura dos aplicativos Android já está pronto para colocar a mão na massa e começar a criar seus próprios apps. No próximo artigo vamos abordar aspectos mais técnicos: descubra o que diabos é um DP, aprenda sobre densidade de pixels e resolução, organize seus assets e veja quais são os entregáveis. Até a próxima!

### Saiba mais

[Documentação Oficial][11]
  
[How to design for Android devices][12]

 [1]: http://developerbus.withgoogle.com/ "Google Developer Bus"
 [2]: http://developer.android.com/design/ "Android Design,"
 [3]: http://www.idc.com/getdoc.jsp?containerId=prUS24442013 "Android Pushes Past 80% Market Share While Windows Phone Shipments Leap 156.0% Year Over Year in the Third Quarter, According to IDC "
 [4]: http://androidniceties.tumblr.com/ "Androide Niceties"
 [5]: http://www.android-app-patterns.com/ "Android App Patterns"
 [6]: https://play.google.com/store "Google Play Store"
 [7]: https://kippt.com/ "Kippt"
 [8]: http://www.pinterest.com/ "Pinterest"
 [9]: http://developer.android.com/downloads/design/Android_Design_Icons_20131106.zip "Android Design Icons"
 [10]: http://developer.android.com/design/downloads/
 [11]: http://developer.android.com/design/index.html "Android Design"
 [12]: http://blog.mengto.com/how-to-design-for-android-devices/ "Hot to design for Android devices"