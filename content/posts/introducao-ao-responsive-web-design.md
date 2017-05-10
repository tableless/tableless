---
title: Introdução ao Responsive Web Design
author: Diego Eis
type: post
date: 2011-08-15
excerpt: Responsive Web Design é um nome bonito para um conceito antigo. Hoje seus usuários utilizam diversos dispositivos e meios de acesso para encontrar informação. Saiba como podemos entregar informação de forma eficaz e inteligente.
url: /introducao-ao-responsive-web-design/
tweetbackscheck:
  - 1356388379
shorturls:
  - 'a:3:{s:9:"permalink";s:31:"http://tableless.com.br/?p=4029";s:7:"tinyurl";s:26:"http://tinyurl.com/3wwggtd";s:4:"isgd";s:19:"http://is.gd/ZvzlSg";}'
twittercomments:
  - 'a:0:{}'
dsq_thread_id: 503016180
categories:
  - Acessibilidade
  - Adaptive Web Design (AWD)
  - Artigos
  - Código
  - CSS
  - CSS3
  - HTML
  - Mercado e Comportamento
  - Mobile
  - O Básico
  - Responsive Web Design (RWD)
  - Tecnologia e Tendências
tags:
  - 2011
  - design
  - dispositivos moveis
  - internetmovel
  - mobiles
  - mobilidade

---
Você já deve ter ouvido falar sobre Responsive Web Design. Você pode ler sobre isso [aqui][1] e [aqui][2].
  
Até pouco tempo atrás tínhamos praticamente apenas um meio de acessar a internet, que era pelo desktop. Podíamos acessar mal e porcamente a internet pelos celulares ou por outros aparelhos ligados a televisão etc, mas nenhum destes meios nos permitia acessar a internet com a facilidade que tínhamos quando utilizávamos um desktop. 
  
Hoje o cenário é totalmente diferente. Os smartphones tomaram conta. Até mesmo os celulares mais simples dispõem de browsers altamente eficazes e se não há algum browser instalado, o usuário pode facilmente baixar o [Opera Mobile][3]. Há também as Tablets, que demoraram para aparecer, mas agora trazem flexibilidade para usuários que querem algo mais prático que um notebook e mais confortável que um smartphone. Não vai demorar muito para aparecer outros aparelhos diferentes ou que você acesse sem restrições a internet pela sua TV. 

Quando não restringimos os cenários a aparelhos temos um horizonte muito maior e mais frutífero. Entenda que a informação publicada na web pode e é totalmente reutilizada a qualquer momento. O Google faz isso com seu robô todos os dias, a todo momento. O robô do Google ou o de qualquer outro sistema de busca é um meio de acesso. O leitor de tela do usuário deficiente visual também é um meio de acesso. O leitor de RSS utilizado pelo seu celular, por mais simples que seja, é um meio de acesso. Podemos dizer então que qualquer dispositivo que o usuário utilize para consumir informação na web é um meio de acesso. Esse &#8220;qualquer coisa&#8221; pode ser um robô ou um sistema manipulado pelos visitantes de seu site.

### O que é Responsive Web Design

Responsive Web Design é acima de tudo um conceito. Nós nos responsabilizamos a apresentar a informação de forma acessível e confortável para diversos meios de acesso. Muitos websites restringem o conceito a aparelhos com telas de diversos tamanhos, mas o conceito é muito mais abrangente. 

Mesmo assim irei restringir os primeiros exemplos a dispositivos que tenham telas e que estão mais presentes atualmente. Não irei me estender muito a meios de acesso como leitores de tela, robôs de busca ou outros dispositivos.

### O problema de entregar conteúdo em diversos formatos

Para fazer um website que seja acessível por qualquer dispositivo você geralmente tenta detectar o aparelho que o usuário está utilizando. Se for um desktop ou um notebook, você redireciona o acesso para um código CSS que formata seu site para o design mais confortável em grandes monitores. Se você detectar que o usuário está utilizando um dispositivo móvel, você o redireciona para uma versão que formatará o site para um formato compatível para este dispositivo. 
  
Essa ideia é simples e foi efetiva por algum tempo quando utilizávamos [Media Types][4] do CSS. 
  
Com o advento dos novos aparelhos como tablets, smartphones e até mesmo as televisões LED e LCD, essa técnica se tornou muito obsoleta.   
Entenda porque: os media types detectavam algumas características dos meios de acesso, por exemplo o valor **handheld** filtrava aparelhos com telas de tamanho pequeno e conexão com a internet limitada. O valor **screen**, filtrava aparelhos com telas coloridas, normalmente terminais com monitores.
  
Entende porque estas características estão obsoletas ou se confundem com a quantidade de aparelhos existentes? Hoje 100% dos smartphones suportam resoluções de tela maiores e com acesso a um número ilimitado de cores que os monitores antigos. Quase nenhum celular tem telas pequenas e conexão limitada com a internet. Logo, estes parâmetros ficaram totalmente inúteis.

Para termos uma ideia melhor, a tela do iPhone e do iPad suportam resoluções muito maiores do que os monitores antigos. Lembro que utilizava em meu antigo monitor de 13&#8221; resolução de 800&#215;600. A resolução do iPad é de 1024&#215;768 com 132ppp. Meu monitor de 13&#8221; até chegava nessa resolução, mas daquele jeito porco. Até o iPhone tem uma resolução melhor: 960&#215;640.

Agora entenda a regra primordial, que deve guiar todo o planejamento de design para diversos dispositivos: O que importa é a resolução e não o tamanho da tela.

Sabendo dessa regra, entenda que você não faz um layout para um determinado tipo de dispositivo, mas para aparelhos que tem uma determinada resolução. Um exemplo clássico é o site do Itaú. Eles tem uma equipe sensacional e muito pioneira. Eu consigo acessar perfeitamente o bankline por disversos dispositivos. Mas há um problema. Troquei meu smartphone Android recentemente por um Windows Phone. Eles tem as mesmas características. Mas quando entrei no bankline do Itaú, curiosamente fui redirecionado para a versão WAP do bankline. Com um bom desenvolvedor que sou, não me conformei e peguei emprestado o iPhone da minha mulher, copiei o endereço que o site redireciona os usuários do iPhone e o utilizei no meu Windows Phone. Voilá! Mesma interface, mesma usabilidade, mesmo design.
  
Eles detectaram o tipo de aparelho e não as características do aparelho. 

Para nos ajudar a detectar as características dos aparelhos, bem como a resolução, utilizamos as Media Queries em detrimento aos Media Types.

### Media Queries

Media Queries é a utilização de [Media Types][5] com uma ou mais expressões envolvendo características de uma media para definir formatações para diversos dispositivos.

Em Media Types há um valor chamado SCREEN, como já vimos anteriormente. Este valor é utilizado quando queremos direcionar uma determinada formatação para aparelhos que tem telas coloridas. Bom, telas coloridas é algo muito genérico, qualquer coisa hoje em dia tem telas coloridas. É aí que as Media Queries nos ajudam: além de identificar aparelhos com telas coloridas, você consegue definir um range de tamanho de tela para que aquele CSS possa ser ativado.
  
Veja um código de exemplo abaixo:

<pre class="lang-html">&lt;link rel="stylesheet" href="estilo.css" media="screen and (color)"&gt;
</pre>

Você já deve ter percebido o porque do QUERIES no nome. Você cria queries no valor do atributo **media** o elemento LINK.
  
Neste exemplo, estamos capturando terminais com montiores e coloridos. Você pode capturar outros terminais com alguma saída visual, mas pode ser que o usuário esteja utilizando algum aparelho com saída de monitor monocromático, por isso temos que especificar o COLOR no valor.

Outro exemplo, onde restringimos a largura máxima da tela:

<pre class="lang-html">&lt;link rel="stylesheet" href="smartphones.css" media="screen and (max-width:480px)"&gt;
</pre>

Aqui estamos direcionando o código CSS para aparelhos que tenham uma largura máxima de tela de 480px. Ou seja, qualquer aparelho que tenha essa largura de tela, deverá utilizar o código CSS que está no arquivo especificado.

É aqui que a diversão começa: com essas queries você define uma série de ranges de larguras de tela, separando uma versão de CSS para cada grupo de aparelhos que se enquadradam nestas descrições. Você faz um formato para grandes telas, outro para telas de tablets e outro para telas de smartphones.

E lá vem uma pergunta para você: as telas dos Tablets hoje em dia utilizando uma resolução de 1024&#215;768. Muitos usuários utilizam esta mesma resolução de tela em seus computadores, com monitores maiores que as tablets. Como faz?

Entenda: se você criou uma versão adaptável, confortável para resoluções de 1024&#215;768, pensando em tablets, será que essa mesma versão não seria confortável para monitores com essa resolução? E vice-versa. Se você definiu que a versão desktop será carregada a partir de uma largura de tela de 1000px. As tablets também verão essa versão. Lembre-se o que realmente importa é o tamanho da tela dos aparelhos, não o aparelho em si. Quando você especifica o aparelho, você limita os usuários, quando você específica a resolução, você amplia o número possíveis de visitantes.

Além do mais, vendo estatísticas por aí, a resolução de 1024&#215;768 está decaindo muito rápido. Com as novas TVs e novos monitores, as resoluções de tela tem aumentado bastante, levando todos a um novo patamar.
  
O que nos leva ao próximo assunto.

### Outras decisões de interface

O primeiro passo foi identificar os aparelhos e usuários que utilizam determinadas resoluções para conseguirmos entregar um CSS específico.
  
O segundo passo é fazer com que o layout seja amigável. Para isso você precisa entender os dilemas dos seus layouts e resolvê-los sem que o design mude da água para o vinho, mantendo as mesmas características e histórias de uso. Para tanto você precisa estudar e aplicar algumas premissas em seu website. Vou mostrar alguns pontos aqui, mas cada projeto terá uma abordagem diferente.

#### Layout fluido

Layouts fluidos estão sendo utilizados desde os primórdios, mesmo assim de uma forma muito restrita porque dependendo do tamanho do site são bem difíceis de planejar. Veja o site da Amazon, ele ocupa todo o espaço do navegador e seu tamanho é adequado até uma determinada largura de tela. 

O [A List a Part][2] tem um exemplo ótimo, por isso não vou fazê-lo perder tempo vendo outro exemplo. [Veja este layout][6] com a tela maximizada e vá diminuindo a janela do seu browser e veja os efeitos.

Perceba ele se encaixa em qualquer tipo de tela. Dessa forma você entregou uma boa experiência de design para todos os públicos. Este é um ótimo exemplo para entender exatamente o que é Responsive Web Design.
  
Quer [outro ótimo exemplo][7]? Neste caso o designer mostra uma mensagem para o usuário, o alertando de que o site é melhor visualizado em grandes resoluções.

#### Adaptando menus

Menus de websites são indispensáveis. É por lá que o usuário descobre todos os segredos do seu website, por onde ele se apaixona ou se perde. O menu é um dos principais elementos do seu website. É muito comum que usemos menus na horizontal. E como você sabe, menus na horizontal não são quase impossíveis em telas pequenas como as dos smarphones. Ainda mais se você tiver uma grande quantidade de opções. Logo, você precisa adaptar se menu para que ele continue usável e ao mesmo tempo não ocupe tanto espaço na tela.

Há diversos caminhos que você pode tomar: você pode transformar o menu em um selectbox (ou combobox, como preferir), sumir com alguns ítens que podem não ser interessantes para usuários de mobiles ou reformatar seu design para que ele caixa de forma funcional em telas pequenas.

Veja alguns exemplos abaixo. Entre no site e diminua a janela do browser para ver os efeitos. Se preferir ver na vida real, visite o site pelo seu smartphone:

  *  <http://www.highwayhurricanes.com/>
  * <http://www.citychoir.org.uk/>
  * <http://leica-explorer.com/>

#### Diminuindo ou trocando imagens

Não se preocupe se seu website trabalha utilizando grandes imagens, você trocar ou diminuir as imagens para que caibam em telas menores. Veja os exemplos abaixo:

  * <http://www.ciscolondon2012.com/>
  * <http://www.cujo.jp/>
  * <http://spartanrobotics.org/>
  * <http://1pictureaday.com/>

#### Media Queries &#8211; A Collection of sites using media queries

Todos os exemplos de website que mostrei acima, retirei [deste website][8]. A ideia é genial!
  
O <http://mediaqueri.es/> tem uma coleção impressionante de websites que utilizam de forma responsável as Media Queries. Veja os exemplos e entenda como você pode fazer um website adaptável para diversos cenários de uso.

### Cada meio de acesso tem sua característica

Conversamos bastante sobre o problema das resoluções e larguras de tela. Mas no começo deste post eu disse que o Responsive Web Design pode ir muito além das telas e Media Queries. Há usuários podem visitar seu site e não utilizar uma tela, tablet ou smartphone. Em vez de ler as informações ele pode ouvi-las, como é o caso dos usuários de leitores de tela. 

#### CSS Aural

Quero que você abra sua mente e entenda que mesmo você não tenho deficiencia visual, você pode ser um grande candidato a utilizar leitores de tela. Enganam-se aqueles que acham que programas que leem a tela só podem ser usados por pessoas com problemas de visão. E se você estiver dirigindo ou em qualquer outra situação em que não pode ficar o tempo inteiro com o celular na mão, mas mesmo assim quer ler um determinado artigo, site etc, como você faz? Nunca pensou em ouvir o artigo? Pois é.

Eu sei que os sistemas de leitura de tela hoje em dia precisam de uma repaginada total. Mas empresas como Apple e Microsoft já estão fazendo isso para que seus sistemas mobiles e para desktops tenham a habilidade de ler bem as telas dos dispositivos. Isso é impressionante.

Se a informação vai ser consumida dessa forma ela precisa ser formatada também. Isso mesmo, formataremos o áudio! Como? Com [CSS Aural][9].

O CSS Aural praticamente controla como o audio do leitor de tela irá se comportar. Você pode controlar volume, tipo da voz, qual caixa a voz sairá etc.
  
Imagine que você tenha um artigo sobre uma entrevista, onde há o entrevistador e o entrevistado. Você pode: especificar que a voz do entrevistador sairá na caixa da esquerda e a do entrevistado na caixa de som da direita. Que a voz do entrevistador será masculina e que voz do entrevistador será feminina.
  
Sensacional, não é?

#### Especificação Touchscreen

Já falei sobre a [Específicação Touchscreen][10], abaixo segue um resumo, mas sugiro que você leia o artigo completo.

Estamos acostumados com a experiência de interação com a ajuda do mouse. Isso foi desde os primórdios e provavelmente ainda será por bastante tempo. Nós desenhamos interfaces para ações baseadas no mouse ou qualquer aparelho que controle a setinha da sua tela. Criar interfaces touch é algo relativamente novo. Nós trouxemos ideias da interação com mouse para os dispositivos touch, mas grande parte das interações precisaram ser reinventadas porque o modo, o ato, a forma de interagir com a informação é diferente. Na interface touch você não “coloca o mouse” em cima do elemento. Você não utiliza teclas de atalho para executar ações. Normalmente as ações importantes estão expostas na interface, facilitando o acesso rápido. Isso é muito importante porque nos ensina criar interfaces mais intuitivas, com a curva de aprendizado menor.

Há também o outro lado da moeda, onde detalhes das interfaces touch não podem ser portadas para interfaces baseadas em mouse. Lembre agora na forma de como você gira uma imagem em um dispositivo touch e como você gira essa mesma imagem utilizando um mouse. A interface muda, o seu comportamento muda.

Sabendo dessas limitações você deve entender que não podemos simplesmente portar o visual de um determinado site para um dispositivo touch. Você pode dizer que “hoje fazemos isso e até agora está funcionando muito bem”. Mas pense melhor… a grande maioria dos sites que você visita hoje no iPad ou qualquer outro tablet, por exemplo, são sites onde a sua interação é limitada. O que você faz em um site hoje em dia? Clica nos links e lê. Salvo às vezes quando você visita um site mais “animadinho” com mais ações para entreter o usuário. Mas e se você faz um site onde é preciso rotacionar uma imagem ou fazer um ZOOM? Você precisará manter as mesmas ações nos dois cenários. E como antigamente, para manter o cenário das interfaces touch você precisa da ajuda de muito script.

### Concluindo

Responsive Web Design é um assunto muito extenso mas muito interessante. Nos faz pensar no futuro de forma diferente. Até 5 anos atrás não tínhamos preocupações com outro dispositivo a não ser um ou outro smartphone e os desktops. Hoje temos diversos aparelhos, com diversas limitações de tela, tamanhos, comportamentos&#8230; E isso não vai parar por aí. Todos os dias aparecerão mais e mais aparelhos e dispositivos que ajudarão os usuários a terem acesso a qualquer informação. É importante que nós possibilitemos que essas informações sejam entregues da melhor maneira possível.

Algumas referências que você pode querer dar uma olhada:

  * [Responsive Web Design][11]
  * [Guidelines for Responsive Web Design][12]
  * [Designing for a Responsive Web with Heuristic Methods][13]
  * [The Big Web Show sobre Responsive Web Design][14]

 [1]: http://bit.ly/pcrwxY
 [2]: http://bit.ly/mSCRSD
 [3]: http://www.opera.com/mobile/
 [4]: http://bit.ly/r6Vr3P
 [5]: http://bit.ly/qUeFq6
 [6]: http://www.alistapart.com/d/responsive-web-design/ex/ex-site-mini.html
 [7]: http://www.bryanjamesdesign.co.uk/
 [8]: http://mediaqueri.es/
 [9]: http://bit.ly/o25mf6
 [10]: http://bit.ly/mGTiUF
 [11]: http://www.alistapart.com/articles/responsive-web-design/
 [12]: http://coding.smashingmagazine.com/2011/01/12/guidelines-for-responsive-web-design/
 [13]: http://designreviver.com/articles/designing-for-a-responsive-web-with-heuristic-methods/
 [14]: http://5by5.tv/bigwebshow/9