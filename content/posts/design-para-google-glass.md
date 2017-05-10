---
title: Design para Google Glass
author: Dani Guerrato
type: post
date: 2013-08-26
excerpt: Saiba tudo sobre o novo gadget da Google e como desenvolver conteúdo projetado especialmente para esta nova mídia.
url: /design-para-google-glass/
sharing_disabled:
  - 1
dsq_thread_id: 1648971407
categories:
  - Design
  - Geral
  - Mobile
tags:
  - 2013
  - design responsivo
  - glassware
  - google
  - google glass

---
A não ser que você tenha passado o último ano da sua vida em coma, é provável que você já tenha ouvido falar no [Google Glass][1]. Mas o que ele realmente faz? Quais são as limitações técnicas? Como criar layouts tanto para a web quanto para aplicativos nativos que possuam um design adequado para esta nova mídia? E como testar isto tudo sem possuir um aparelho? Ok, Tableless! Vamos responder estas perguntas&#8230;

## O que é Google Glass?

A resposta curta é: um par de óculos. A resposta longa: um pequeno computador inserido em uma armação leve com uma pequena tela posicionada no canto superior direito acima da linha de visão capaz de navegar na internet, ler e-mails, realizar buscas por voz, enviar mensagens SMS, tirar fotos, gravar vídeos, traduzir conteúdo, exibir mapas em tempo real, calendários, realizar ligações, iniciar um hangout do Google, enfim, praticamente tudo o que o seu smartphone faz. Só que sem as mãos.

[<img class="alignnone size-full wp-image-38672" alt="google-glass" src="http://tableless.com.br/uploads/2013/08/google-glass.jpg" width="660" height="258" srcset="uploads/2013/08/google-glass.jpg 660w, uploads/2013/08/google-glass-329x128.jpg 329w, uploads/2013/08/google-glass-588x229.jpg 588w" sizes="(max-width: 660px) 100vw, 660px" />][2]

Desde seu anúncio o Google Glass divide opiniões. Alguns acreditam que o aparelho é a maior invenção do mundo desde a pizza de pepperoni, outros acham que é um dispositivo criado por uma corporação gananciosa para monitorar todas as ações e controlar a mente das pessoas ou até mesmo que o design do aparelho é uma catástrofe da moda tirado de um filme de ficção cientifica B. Seja qual for a sua opinião é improvável que você fique indiferente ao Google Glass. E independente dela, o fato é que o dispositivo vai revolucionar a maneira como lidamos com a informação.

[<img class="alignnone size-full wp-image-38670" alt="google-glass-model" src="http://tableless.com.br/uploads/2013/08/google-glass-model.jpg" width="660" height="372" srcset="uploads/2013/08/google-glass-model.jpg 660w, uploads/2013/08/google-glass-model-298x168.jpg 298w, uploads/2013/08/google-glass-model-550x310.jpg 550w" sizes="(max-width: 660px) 100vw, 660px" />][2]

O Google Glass atualmente está em fase de teste. Existem 10.000 usuários (ou Glass Explorers) atualmente no mundo sendo que destes 2.000 são desenvolvedores encarregados de criar conteúdo fresquinho para o aparelho. A previsão de lançamento oficial é no final deste ano e, com base no hype, não deve demorar muito para escutarmos a frase &#8220;Eu quero que meu site funcione no Glass&#8221;. Para isto é necessário conhecer bem o aparelho, seus pontos fortes e fracos e como criar layouts que não atrapalhem o dia-a-dia dos usuários. E mais importante de tudo, como é ver o mundo através das lentes do Google Glass.

Bem, é mais fácil mostrar do que falar. Saca só o vídeo promocional do aparelho.

[youtube=http://www.youtube.com/watch?v=v1uyQZNg2vE&w=600]

### O Hardware

Uma armação de óculos com uma tela HD de resolução de 640×360 (equivalente a um monitor de de 25 polegadas a uma distancia de 2.5 metros). A tela é posicionada no canto superior direito de maneira que não atrapalhe o campo de visão normal. Os outros features do dispositivo incluem câmera de 5MP, transdutor de condução óssea para áudio (isto significa que você não precisa de fones de ouvido), acelerômetro, painel lateral sensível ao toque, bluetooth, WiFi e 16GB de memória flash. Tudo isto pesando cerca de 40 gramas. Se você está curioso, você pode ler as [especificações técnicas completas aqui][3].

### O que o Google Glass NÃO é

Um conceito importante para se ter em mente antes de tudo é: o Google Glass não é realidade aumentada. Na verdade o único aplicativo que combina elementos do mundo real e virtual por enquanto é o GPS. E mesmo isto é feito de maneira contida: as informações mostradas não ocupam a superfície completa do óculos. Isto cegaria o usuário e seria perigoso no dia-a-dia. O viewport do Glass é uma pequena telinha acima do ângulo de visão normal de um óculos. A intenção dos desenvolvedores era ser o menos intrusivo possível, por isto tela fica inativa por padrão. Não é possível, por exemplo, fazer reconhecimento facial (mesmo por que isto levantaria diversas questões relacionadas a privacidade).

## Razões para começar a estudar HOJE

Vou ser sincera com vocês. Na realidade é impossível prever se o Glass será um sucesso. Não dá para saber como as pessoas navegarão na internet daqui a 2, 3 ou 5 anos. Há pouco tempo anos atrás a linguagem mais popular era o Flash e quem apostou no HTML5 e padrões de desenvolvimento mais semânticos se deu bem. Saber analisar o mercado e distinguir entre quais tecnologias merecem atenção ou não é vital para qualquer profissional que deseja se manter atualizado. Talvez seja ainda um pouco cedo para decidir, mas eu colocaria algumas fichas no Glass.

Talvez você esteja pensando &#8220;WTF Dani! Este aparelho nem lançou. Por que eu deveria me preocupar com isto?&#8221;. Bem, vamos supor que você demore alguns meses para dominar estas técnicas&#8230; entre elementos de design, linguagens de desenvolvimento / programação, API, enfim, que esta seja a sua curva de aprendizado para se tornar um expert no Google Glass. Quando o aparelho for lançado significa que você vai demorar um bom tempo entre comprar, testar, aprender e de fato produzir conteúdo voltado para o Glass. Exceto que se você começar a estudar hoje vai poder ser um dos pioneiros em uma terra inexplorada e potencialmente ganhar visibilidade e poder cobrar mais caro já que encontrar profissionais qualificados será uma tarefa bem difícil. Fora a satisfação pessoal de estar produzindo algo inovador e desafiador, ganhar muitos pageviews dos early adopters desesperados por conteúdon adaptado e ter um projeto bacana no seu portfólio. Algo semelhante a como foi o Boom do desenvolvimento mobile nos primeiros anos.

Alias, a razão para o sucesso do Glass talvez esteja em uma &#8220;falha&#8221; nos smartphones: eles interrompem o relacionamento entre as pessoas. Ficar checando o celular de 5 em 5 minutos em uma situação social é um tanto intrusivo (para não dizer que faz você parecer um mala). O fato é que smartphones bloqueiam nossa visão do mundo real. Sem contar as situações que é simplesmente impossível operar o aparelho pois as mão estão ocupadas como ao dirigir um veiculo ou fazer uma operação no cérebro. Ok, esta ultima situação é mais improvável que aconteça no nosso dia-a-dia. Mas seria legal poder consultar um mapa ao em tempo real, ver o inventório durante um jogo de video-games, filmar o mundo do seu próprio ponto de vista ou ler receitas sem correr o risco de derrubar comida em cima do seu tablet. As possibilidades de uso são infinitas e é justamente isto que faz do Glass um conceito excitante. A idéia central é colocar o usuário no foco da experiência.

## Os competidores

O Google Glass mal foi lançado, mas já existem diversas empresas na corrida pelo mercado eyewear. A idéia do [Epifhany][4], por exemplo, é ser fashion. Já o [LiveMap][5] é um capacete para motociclistas com GPS embutido. O [Lumus][6] se propoe a de fato criar uma realidade aumentada. Além destes temos o GlassUp, Scope Technologies, Seebright, Innovega, Telepathy One&#8230; Os diferenciais variam entre design do produto, especificações técnicas e o mais importante: preço. Inicialmente o custo para comprar um aparelho em beta teste do Google Glass foi de $1500 dolares. Alguns [rumores][7] indicam que o valor para o consumidor final será bem mais barato: US$ 299. Mas isto não passa de especulação.

[<img class="alignnone size-full wp-image-38669" alt="http://www.epiphanyeyewear.com" src="http://tableless.com.br/uploads/2013/08/epiphany.jpg" width="660" height="355" srcset="uploads/2013/08/epiphany.jpg 660w, uploads/2013/08/epiphany-312x168.jpg 312w, uploads/2013/08/epiphany-576x310.jpg 576w" sizes="(max-width: 660px) 100vw, 660px" />][8]
  
<small>Epiphany</small>

## Glassware

A primeira coisa que você precisa saber como um desenvolvedor é: por enquanto não existem aplicativos nativos para o Google Glass. Ao menos não como este conceito é utilizado atualmente. Nada é instalado na memória interna do aparelho. Isto ainda está em estudo já que os testes atuais com aplicativos nativos ainda causam alguns problemas como gasto excessivo de bateria e super aquecimento do dispositivo. Isto deve mudar no futuro, mas o que nós temos atualmente são serviços ativados por uma interface web que, de tempos em tempos, são atualizados com novas informações. Estes serviços são chamados de Glassware e todos eles funcionam nas nuvens via [API Google Mirror Glass][9]. O layout destes serviços segue uma interface padronizadas: cards em uma timeline.

Pense na timeline como uma estante&#8230; Quando você autoriza um serviço é como se você colocasse um livro novo nesta estante. É possível trocar de livro utilizando uma sequência de toques na base do óculos. Cada página deste livro corresponde a um cartão informativo (card) contendo mensagens curtas, notificações, vídeos, fotos, atualizações, etc.

Este vídeo demonstra como interagir com a timeline.

[youtube=http://www.youtube.com/watch?v=4EvNxWhskf8&w=600]

&nbsp;

Já existem alguns serviços em funcionamento no momento como Path, [Evernote][10], CNN, New York Times, Twitter, Facebook, Elle e Tumblr. Todos eles funcionam através de uma permissão ligada a contas do Facebook e / ou Google+. Através do diretório não-oficial [Glass-apps.org][11] é possível ver outros exemplos de serviços, reviews e links para instalação.

[<img class="alignnone size-full wp-image-38668" alt="cnn-google-glass" src="http://tableless.com.br/uploads/2013/08/cnn-google-glass.jpg" width="660" height="372" srcset="uploads/2013/08/cnn-google-glass.jpg 660w, uploads/2013/08/cnn-google-glass-298x168.jpg 298w, uploads/2013/08/cnn-google-glass-550x310.jpg 550w" sizes="(max-width: 660px) 100vw, 660px" />][12]
  
[<img class="alignnone size-full wp-image-38667" alt="cnn-google-glass-2" src="http://tableless.com.br/uploads/2013/08/cnn-google-glass-2.jpg" width="660" height="372" srcset="uploads/2013/08/cnn-google-glass-2.jpg 660w, uploads/2013/08/cnn-google-glass-2-298x168.jpg 298w, uploads/2013/08/cnn-google-glass-2-550x310.jpg 550w" sizes="(max-width: 660px) 100vw, 660px" />][12]

Se empolgou para criar Glassware? A boa notícia é que você não precisa aprender nenhuma linguagem nova. É possível projetar serviços utilizando java, .net, ruby, python e php e a [documentação oficial][13] inclui muitos exemplo, [templates][14] e até mesmo o [CSS dos cards nativos][15].

## Boas práticas

Bem, antes de projetar o seu glassware ou até mesmo site otimizado para Google Glass é importante ter em mente alguns conceitos.

O Glass é projetado para ser utilizado no dia-a-dia e portanto não deve atrapalhar o mundo real! O serviço deve estar ao alcance do usuário quando ele precisar utilizar, mas sem interferir em outras situações. Isto significa nada de notificações frequentes ou inesperadas. Se uma mensagem da timeline for ignorada, por exemplo, isto não deve influenciar no restante da experiência. A idéia é entregar a informação de maneira rápida e precisa para não distrair o usuário do dia-a-dia. Isto significa que os textos devem ser curtos e objetivos. A recomendação é que os artigos mais longos sejam divididos em trechos menores (ocupando um grupo de cartões) ou até mesmo utilizar a função de leitura em voz alta. Já no caso de vídeos criados especificamente para o aparelho a documentação oficial recomenda não ultrapassar o tempo de 10 a 20 segundos.

## O Browser

O Google Glass ainda é um protótipo e portanto tem algumas limitações. Por enquanto não existe a opção de navegar diretamente até uma URL. Você deve primeiro realizar uma busca por voz no Google para então acessar o endereço. Basicamente você diz &#8220;Ok Glass. Google&#8221; e as palavras-chaves que deseja utilizar. Se o resultado da sua busca não for um conteúdo rich media você verá os primeiros 7 links do Google sobre aquele tema e um botão para a próxima página. Portanto, é bom caprichar no SEO!

O Browser aceita HTML5 (incluindo audio e video), CSS e JavaScript. Inclusive animações ou valores como position:absolute.

### Interações

Os comandos, em teoria, são bem básicos. É possível descer a barra de rolagem de um site deslizando os dedos pelo painel sensível ao toque na base da armação, utilizando dois dedos é possível direcionar o foco. Para abrir um link basta bater levemente duas vezes. Um círculo na tela serve como ponteiro. É possível ainda dar zoom in e out deslizando dois dedos para frente e para trás. E é isto! São estas as interações do Glass. Isto torna impossível, por exemplo, preencher campos de formulário de texto já que não existe um teclado! Já campos como radio buttons, checkbox e selects são mais viáveis.

## Design Responsivo

Navegar em sites não otimizados para o aparelho pode ser uma tarefa complicada. Se nenhuma tag viewport for definida o Glass irá renderizar o layout de uma página como um browser de desktop (viewport de 960px). Até aí tudo bem, mas isto causa alguns problemas já que o texto de um site &#8220;normal&#8221; é bem difícil de ler na distância focal do Glass sem zoom. O mesma vale para selecionar links com precisão. Então um bom tamanho de texto é fundamental já que, ao contrário dos smartphones, é impossível aproximar mais o aparelho do rosto. Os cards nativos utilizam a fonte Roboto com 5 tamanhos para texto padrão: 70px, 50px, 40px, 34px, 30px. Existem duas exceções: 90px para frases importantes e curtas e 26px para o footer.

[<img class="alignnone size-full wp-image-38671" alt="google-glass-template" src="http://tableless.com.br/uploads/2013/08/google-glass-template.jpg" width="660" height="372" srcset="uploads/2013/08/google-glass-template.jpg 660w, uploads/2013/08/google-glass-template-298x168.jpg 298w, uploads/2013/08/google-glass-template-550x310.jpg 550w" sizes="(max-width: 660px) 100vw, 660px" />][16]

No caso de sites que utilizam a meta-tag viewport width=device-width a renderização será igual a um smartphone em modo paisagem.

As especificações de mídia são as seguintes:
  
device-width: 640px
  
device-height: 360px
  
width: 427px
  
height: 240px
  
orientation: landscape
  
-webkit-device-pixel-ratio: 1.5

Reparem que, pela densidade de pixel ser 1.5, embora a resolução do aparelho seja 640x360px o tamanho do viewport é 427x240px. Ou seja, você pode utilizar o seguinte Media Querie para Google Glass.

<pre class="lang-css">@media screen and (width: 427px) {
/*Google Glass*/
}</pre>

## Design para Glass

É importante criar layouts com o foco na experiência do usuário. Como não é um aparelho indicado para ler textos muito longos, a dica aqui é abusar dos call to actions. Pense em destacar as informações / ações mais importantes imediatamente. Chamadas claras e objetivas como &#8220;ligue aqui&#8221;, &#8220;envie um e-mail&#8221;, &#8220;siga no twitter&#8221; ou &#8220;veja nosso endereço&#8221; além de possuirem uma integração bacana com o restante das funcionalidades do aparelho fornecem informações de contato rapidamente. De ao usuário aquilo que ele veio buscar. Os links precisam ser óbvios e grandes o suficiente para serem selecionados com facilidade. A margem entre o conteúdo principal e a borda da janela do browser também é importante para garantir a visibilidade.

O uso de contraste é fundamental, principalmente entre o texto e o background. Lembre-se que muitos usuários vão acessar o aparelho ao ar livre e é horrível tentar enxergar monitores no sol&#8230;

Uma coisa que deve ser evitada no momento é o uso de anuncios publicitários. Na verdade eles estão proibidos no caso dos &#8220;aplicativos nativos&#8221; pela política do Google. E é super justificavel. Imagina ter que selecionar um x pequenininho de uma janela popup?

Não se preocupe se isto parecer informações demais. Para ajudar os desenvolvedores a definirem com mais precisão tamanhos de texto, margem, espaçamento, ícones, etc o Google disponibilizou uma série de [templates em HTML/CSS][17] que são um bom ponto de partida para quem se interessar pela criação de layouts para o aparelho.

## Inspiração

O Google Glass abriu um mundo de possibilidades (semi) infinitas para designers e desenvolvedores. Basta uma busca no [Dribbble][18] para ver exemplos de conceitos para o aparelho.

Alguns projetos são perfeitamente possíveis como este app de Fitness do [Ok Glass][19].

[<img class="alignnone size-full wp-image-38674" alt="okglass-2" src="http://tableless.com.br/uploads/2013/08/okglass-2.jpg" width="660" height="375" srcset="uploads/2013/08/okglass-2.jpg 660w, uploads/2013/08/okglass-2-295x168.jpg 295w, uploads/2013/08/okglass-2-545x310.jpg 545w" sizes="(max-width: 660px) 100vw, 660px" />][20]

Outros nem tanto como este de reconhecimento facial feito pelo mesmo designer.

[<img class="alignnone size-full wp-image-38675" alt="okglass" src="http://tableless.com.br/uploads/2013/08/okglass.jpg" width="660" height="372" srcset="uploads/2013/08/okglass.jpg 660w, uploads/2013/08/okglass-298x168.jpg 298w, uploads/2013/08/okglass-550x310.jpg 550w" sizes="(max-width: 660px) 100vw, 660px" />][20]

Ainda assim pesquisar os protótipos para a plataforma pode ser uma boa fonte de inspiração. [Este vídeo da Playground Inc][21] também apresenta ideias de aplicativos bem interessantes.

## Como testar sem possuir um Glass

Nenhuma destas ferramentas é perfeita. Mesmo por que interação é algo muito difícil de medir sem de fato possuir o aparelho. Por mais que você possa visualizar o layout é difícil de prever se um objeto será fácil de selecionar utilizando apenas o movimento dos dedos e o olhar. Mas mesmo assim vale a pena utilizar alguma(s) destas ferramentas para testar outros elementos do layout como como peso, tamanho, tipografia, contraste, paleta de cores, etc.

### Playground

Através do [Google Mirror API Playground][22] você pode brincar com templates de cards padrão no seu próprio browser. É possível anexar imagens, escrever textos, renderizar html, cruar menus personalizados, notificações falsas e até visualisar algumas ações da timeline com inserir, modificar e deletar itens.

[<img class="alignnone size-full wp-image-38673" alt="mirror-API-playground" src="http://tableless.com.br/uploads/2013/08/mirror-API-playground.jpg" width="660" height="270" srcset="uploads/2013/08/mirror-API-playground.jpg 660w, uploads/2013/08/mirror-API-playground-329x134.jpg 329w, uploads/2013/08/mirror-API-playground-588x240.jpg 588w" sizes="(max-width: 660px) 100vw, 660px" />][23]

Este [projeto no Github][24] criado pelo desenvolvedor Gerwin Sturm emula a API para que você possa baixar e realizar testes mais complexos sem ser um dos desenvolvedores oficiais (AKA explores) da plataforma.

### GlassSim

O [GlassSim][25] é uma das ferramentas mais interessantes que eu encontrei para simular como é a experiência de utilizar o Glass. Você escolhe um template de card padrão ou escreve do zero a sua própria estrutura utilizando HTML e CSS inline. Depois é possível realizar o upload de uma foto para simular o campo de visão ou até mesmo abrir a sua webcam e ver o layout em ação no mundo real. É possível a partir daí tirar screenshots ou compartilhar o link com outras pessoas. A [galeria][26] exibe alguns exemplos interessantes do que seria possível fazer com o Glass.

[<img class="alignnone size-full wp-image-38688" alt="glassSim" src="http://tableless.com.br/uploads/2013/08/glassSim.jpg" width="660" height="352" srcset="uploads/2013/08/glassSim.jpg 660w, uploads/2013/08/glassSim-315x168.jpg 315w, uploads/2013/08/glassSim-581x310.jpg 581w" sizes="(max-width: 660px) 100vw, 660px" />][27]

## Conclusão

Independente de você ser um fã da tecnologia ou não se interessar nem um pouco pela experiência, o Google Glass trará uma revolução na maneira como o ser humano interage com interfaces digitais. Estar preparado para atender as demandas futuras do mercado e proporcionar aos usuários um design que facilite o acesso a informação independente da mídia deve ser a prioridade de qualquer desenvolvedor que se orgulhe em dizer que faz design responsivo. Pode ser que o Glass torne-se apenas um produto de nicho ou que daqui a 10 anos seja o meio mais popular de acesso a internet. É impossível prever o futuro e quais caminhos o desenvolvimento web trilhará. Mas podemos estar preparados.

### Saiba mais

[Documentação Oficial][28]
  
[Google Glass FAQ][29]
  
[The web designers guide to Google Glass][30]
  
[Google Glass Browser: HTML5 and Responsive Web Design in your head][31]
  
[Grupo de Desenvolvedores no Google+][32]

 [1]: http://www.google.com/glass/start/ "Google Glass"
 [2]: http://www.google.com/glass/start/
 [3]: https://support.google.com/glass/answer/3064128?hl=en "Support Google - Glass"
 [4]: http://www.epiphanyeyewear.com/ "Epiphany"
 [5]: http://www.livemap.info/ "LiveMap"
 [6]: http://www.lumus-optical.com/ "Lumus"
 [7]: http://www.techtudo.com.br/noticias/noticia/2013/08/google-glass-pode-ficar-cinco-vezes-mais-barato-no-lancamento-diz-estudo.html "Google Glass pode ficar cinco vezes mais barato no lançamento, diz estudo"
 [8]: http://www.epiphanyeyewear.com/
 [9]: https://developers.google.com/glass/ "Google Mirror Glass"
 [10]: http://blog.evernote.com/blog/2013/05/16/first-look-evernote-for-google-glass/ "Evernote"
 [11]: http://glass-apps.org/google-glass-application-list "Glass-apps.org"
 [12]: http://cnn.currentnewsnotify.com/
 [13]: https://developers.google.com/glass/ "Developers Google - Glass"
 [14]: https://developers.google.com/glass/downloads/ "Developers Goole - Glass - Downloads"
 [15]: https://mirror-api-playground.appspot.com/assets/css/base_style.css "Mirror API Playgrounds - Base Style"
 [16]: https://developers.google.com/glass/ui-guidelines
 [17]: https://developers.google.com/glass/playground "Deevelopers Google - Playground"
 [18]: http://dribbble.com/search?q=google+glass "Dribbble"
 [19]: http://jackwmorgan.com/ok-glass/ "Ok Glass"
 [20]: http://jackwmorgan.com/ok-glass/
 [21]: http://playgroundinc.com/blog/the-future-of-google-glass/ "Playground Inc."
 [22]: https://developers.google.com/glass/playground "Google Mirror API Playground"
 [23]: https://developers.google.com/glass/playground
 [24]: https://github.com/Scarygami/mirror-api "Scarygami Mirror-API"
 [25]: http://www.glasssim.com/ "GlassSim"
 [26]: https://plus.google.com/photos/116585924925440751072/albums/5873077927767143073 "GlassSim Album @Google+"
 [27]: http://glasssim.com/
 [28]: https://developers.google.com/glass/overview "Developers Google - Glass"
 [29]: https://sites.google.com/site/glasscomms/faqs "FAQ"
 [30]: http://webdesign.tutsplus.com/articles/general/the-web-designers-guide-to-google-glass/ "The web designers guide to Google Glass"
 [31]: http://www.mobilexweb.com/blog/google-glass-browser-html5-responsive-web-design "http://www.mobilexweb.com/blog/google-glass-browser-html5-responsive-web-design"
 [32]: https://plus.google.com/communities/105104639432156353586 "Glass Developers"