---
title: Performance front-end – Parte 1
author: Diego Eis
type: post
date: 2012-08-13
excerpt: Entenda como você pode melhorar a velocidade do seu site de maneira rápida e simples.
url: /performance-frontend-parte1/
tweetbackscheck:
  - 1356382010
shorturls:
  - 'a:3:{s:9:"permalink";s:49:"http://tableless.com.br/diminua-tempo-viagem-rtt/";s:7:"tinyurl";s:26:"http://tinyurl.com/dxrmvmm";s:4:"isgd";s:19:"http://is.gd/BhisPB";}'
twittercomments:
  - 'a:30:{i:235821908929699840;s:7:"retweet";i:235797523334303745;s:7:"retweet";i:235795903330525184;s:7:"retweet";i:235794423018045440;s:7:"retweet";i:235792534562013184;s:7:"retweet";i:235372108543303680;s:7:"retweet";i:235350600966107136;s:7:"retweet";i:241200117452001283;s:7:"retweet";i:240939392091435008;s:7:"retweet";i:240868958260056067;s:7:"retweet";i:240867046487904256;s:7:"retweet";i:245942494582411264;s:7:"retweet";i:245938367139823616;s:7:"retweet";i:248217165562519552;s:7:"retweet";i:248113005664038912;s:7:"retweet";i:248112488061730816;s:7:"retweet";i:248112180606681091;s:7:"retweet";i:249477317229948928;s:7:"retweet";i:253286867154378752;s:7:"retweet";i:252550828852928512;s:7:"retweet";i:252483078717599744;s:7:"retweet";i:258637858582175744;s:7:"retweet";i:258622399212318720;s:7:"retweet";i:258621664965844992;s:7:"retweet";i:269850519621754880;s:7:"retweet";i:269491104355844097;s:7:"retweet";i:269272214740811776;s:7:"retweet";i:269121109104922624;s:7:"retweet";i:269116466362716161;s:7:"retweet";i:269116289484722176;s:7:"retweet";}'
tweetcount:
  - 67
dsq_thread_id: 803640165
categories:
  - Browsers
  - Código
  - Técnicas e Práticas
tags:
  - 2012
  - requisicoes

---
RTT (Road-trip Time) é o tempo que leva para o browser (ou qualquer outro cliente) conversar com o servidor buscando a informação solicitada pelo usuário.
  
Normalmente um browser inicia a comunicação com o servidor com pelo menos 3 RTTs: Uma requisição para a resolução do DNS. Outra para o setup de conexão TCP e outra para a requisição HTTP. Normalmente os websites tem muitas requisições HTTP. E isso é muito ruim.  
  
Ter muitas requisições significa que seu browser precisa ir e voltar várias vezes durante a abertura da página. Essa ida e volta são os RTT, ou a Road-trip Time. São as RTTs que contribuem para uma latência ruim nas redes. Se seu cliente demora para trazer a informação, o download da página é prejudicado.

Existem várias estratégias para que você diminua a quantidade de RTTs e melhore a performace da sua página sem fazer muito esforço. Com pequenos passos você consegue resultados bem grandes e interessantes. Lembre-se que alguma dicas não se aplicam a sites pequenos. Mas o que são sites pequenos? Sites pequenos são aqueles sites institucionais, os famosos “Home, Interna e Contato”. O site por si só já é minúsculo. A sua estrutura de arquivos é tranquila de se trabalhar e não precisa de tanta atenção. A performance desses sites dependem mais de onde o servidor está localizado, de qual CMS você estará utilizando e etc&#8230; Mas obviamente um mínimo de “asseio” é necessário.

### Evite @import

Quando utilizamos um @import para adicionar diversos arquivos de CSS em apenas um, o browser precisa baixar o arquivo que importa o código, parsear e executar antes de descobrir que ele precisa baixar os arquivos importados.

Recomenda-se utilizar a tag link para importar os arquivos separadamente ou utilizar qualquer script que junte os arquivos e minimize para que todo seu código CSS se transforme em apenas um. Dependendo da linguagem utilizada, isso pode ser feito automaticamente, como em projetos Ruby on Rails.

### Otimize a ordem dos seus scripts e estilos

Colocar a chamada dos arquivos na ordem correta pode ajudar bastante no carregamento da página. Códigos Javascripts geralmente modificam e alteram o conteúdo da página, logo os browsers demoram mais para rederizá-los por que é necessário que todas as funções daquele scripts sejam executadas e somente depois ele começa o download de outro arquivo.

Imagine que você tenha 3 arquivos de CSS e 2 de JS para chamar na sua página, e você o faz assim:

<pre class="lang-html">&lt;link rel="stylesheet" type="text/css" href="stylesheet1.css"&gt;
&lt;script type="text/javascript" src="scriptfile1.js"&gt;
&lt;script type="text/javascript" src="scriptfile2.js"&gt;
&lt;link rel="stylesheet" type="text/css" href="stylesheet2.css"&gt;
&lt;link rel="stylesheet" type="text/css" href="stylesheet3.css"&gt;
</pre>

Suponha agora que para fazer o download de cada um desses arquivos demora em torno de 100ms (milisegundos), o download dos arquivos seria algo como a imagem abaixo. Essa imagem peguei de uma página do Google que fala sobre o mesmo assunto:

![][1]

Se você simplesmente ordenar os arquivos de outra forma, o carregamento pode ficar apenas em 200ms. Ok, você deve estar falando que eu sou louco por me preocupar com milisegundos&#8230; Mas milisegundos podem se transformar em segundos quando nós nos preocupamos.

<pre class="lang-html">&lt;link rel="stylesheet" type="text/css" href="stylesheet1.css"&gt;
&lt;link rel="stylesheet" type="text/css" href="stylesheet2.css"&gt;
&lt;link rel="stylesheet" type="text/css" href="stylesheet3.css"&gt;
&lt;script type="text/javascript" src="scriptfile1.js"&gt;
&lt;script type="text/javascript" src="scriptfile2.js"&gt;
</pre>

![][2]

O browser baixa paralelamente os três arquivos de CSS e o primeiro arquivo de JS. Depois que o primeiro arquivo de JS foi baixado, ele começa a baixar o segundo. É uma boa prática colocar os arquivos de CSS baixarem primeiro, uma por que a renderização do browser é mais rápida quando se trata de código CSS e outra que o JS pode modificar características desses CSS, logo eles precisar estar carregados quando os scripts forem funcionar.

### Combine imagens utilizando sprites

Tivemos um artigo muito bom aqui no Tableless mostrando [como funcionam os CSS Sprites][3]. É uma técnica antiga, utilizada durante muito tempo em consoles com baixa memória para guardar grandes quantidades de imagens e informações. 

Sempre utilize CSS Sprites onde puder. Se você tem uma grande quantidade de ícones, se você tem uma grande quantidade de imagens decorativas e etc&#8230; Junte-as e forme um sprite de imagens que possa ser utilizado por todo o site. Isso diminui a quantidade de requisições que o browser fará no decorrer da navegação do usuário.

Quando utilizamos muitas imagens pequenas e o browser precisa fazer essas requisições juntas, há um acumulo de tarefas, chama-se [request overhead][4].

Eu sei que trabalhar com sprites dá trabalho para manter e principalmente criar o sprite inicial. Por isso dá para usar serviços para fazer esse trabalho para você. O [SpriteMe][5] é um deles.

### Combine arquivos de CSS

Modular CSS é uma coisa boa, mas é bom para sua organização. Quando nós separamos nosso código CSS em vários arquivos, isso significa que o browser vai ter que buscar cada um desses arquivos no servidor. Logo, se você modula seu CSS, você precisa fazer um trabalho de entrega desse código apenas quando for necessário. Por exemplo: se você separa o estilo da página de contato em um arquivo **contato.css**, o mais inteligente seria chamá-lo apenas na página de contato e assim por diante para as outras páginas.
  
Se você simplesmente modula seu CSS em vários arquivos, mas não faz esse planejamento de distribuição, a modularização de CSS só servirá para sua organização pessoal.

Quando combinamos os códigos CSS em um só, diminuimos a latência. O Google recomenda que tenha no máximo 3 arquivos linkados, mas o perfeito seriam 2 arquivos. Em projetos utilizando Ruby on Rails, por exemplo, é possível juntar automaticamente todo os arquivos em apenas um, sem trabalho manual. Ele ainda minimiza seu código arrancando espaços, quebras de linha e etc. Logo você precisa chamar apenas um arquivo. Baixar um arquivo grande é muito melhor do que baixar vários pequenininhos. Por quê? Requisições, lembra?

### Combine arquivos de Javascript

Pelo mesmo motivo de combinar arquivos de CSS. Dá uma olhada nessa imagem que o Google disponibilizou:

![Carregamento de arquivos separados][6]

Quando linkamos uma série de arquivos separadamente, produzimos uma série de requisições no servidor e isso é ruim. Lembre-se que o sinal tem que ir e voltar para podermos começar a carregar os arquivos. Por isso é melhor você carregar um arquivo grande do que vários pequenos. A quantidade de requisições diminui e por isso tempo de carregamento é menor. Veja a imagem abaixo:

![Carregamento de um arquivo][7]

Bem diferente, né?

Você pode modularizar seus arquivos de forma que você melhore o carregamento e ainda não prejudique seu site. Por exemplo, você pode separar em um arquivo o mínimo de código que será necessário carregar para que a página funcione e em outro arquivo vai todo código que pode ser carregado depois que a página terminar de abrir. Assim você divide as prioridades.

Se for pouco Javascript, algo bem básico mesmo, considere colocá-lo direto no HTML. Sem a necessidade de chamar um arquivo.

### Tente paralelizar downloads de vários domínios

De acordo com o protocolo de HTTP, os browsers podem pode ter duas conexões simultâneas por domínio. Se um documento contem referencias para várias recursos como CSS, Javascripts, Imagens e etc, de forma que estoure o máximo permitido pelo host, o browser começa a baixar um parte e deixa os outros recursos na fila. Quando ele termina de baixar todos os recursos atuais, ele vai pra fila e pega o próximo grupo. 

O problema é que a cada grupo que o browser baixa, é gerado um RTT. Ou seja, se você tem 100 arquivos para baixar (CSS, Javascripts, imagens etc), levando em conta que o browser baixa 4 recursos por vez, serão 25 RTTs gerados.

A estratégia é separar parte destes recursos em outro domínio. Fazendo isso o browser pode baixar o máximo de recursos por domínio paralelamente. Por isso é que normalmente separamos arquivos &#8211; como imagens &#8211; em outro servidor. 

Veja no [Browserscope][8] a lista dos browsers que aceitam ou não fazer esse truque. Normalmente os browsers mais novos estão tranquilos.

#### Outras dicas

Algumas outras dicas e recomendações podem ser vistas neste documento que o Google disponibilizou sobre [boas práticas sobre como deixar sites mais rápidos][9].

Veja a [segunda parte deste artigo aqui][10].

 [1]: http://tableless.com.br/uploads/2012/07/waterfall1.png
 [2]: http://tableless.com.br/uploads/2012/07/waterfall2.png
 [3]: http://tableless.com.br/css-sprites/
 [4]: https://developers.google.com/speed/docs/best-practices/request?hl=sv
 [5]: http://spriteme.org
 [6]: http://tableless.com.br/uploads/2012/08/externaljs1.png
 [7]: http://tableless.com.br/uploads/2012/08/externaljs2.png
 [8]: http://www.browserscope.org/
 [9]: https://developers.google.com/speed/docs/best-practices/rtt?hl=sv#AvoidCssImport
 [10]: http://tableless.com.br/performance-frontend-parte2/