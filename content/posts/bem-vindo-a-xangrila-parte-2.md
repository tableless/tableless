---
title: Bem vindo a Xangri-lá – Parte 2
author: Alysson Franklin
type: post
date: 2010-12-06
excerpt: Voltamos a Xangri-lá, para entender como as coisas funcionam. Veja como aplicar o Progressive Enhancement criando e customizando metodologias de trabalho. As expectativas e considerações do cliente geram o design e a funcionalidade de sua aplicação.
url: /bem-vindo-a-xangrila-parte-2/
aktt_notify_twitter:
  - yes
tweetbackscheck:
  - 1356439783
shorturls:
  - 'a:3:{s:9:"permalink";s:52:"http://tableless.com.br/bem-vindo-a-xangrila-parte-2";s:7:"tinyurl";s:26:"http://tinyurl.com/4y3ewwn";s:4:"isgd";s:19:"http://is.gd/N6dAKg";}'
twittercomments:
  - 'a:1:{i:174582270278111233;s:7:"retweet";}'
tweetcount:
  - 1
dsq_thread_id: 503039798
categories:
  - Acessibilidade
  - Artigos
  - CSS
  - HTML
  - JavaScript
  - Mobile
  - SEO
tags:
  - 2010
  - CSS
  - desenvolvimento web
  - dispositivos moveis
  - Na Prática
  - padroes web
  - Progressive Enhancement
  - Semântica
  - web standards
  - wireframes

---
Uma vez familiares com a premissa do Progressive Enhancement, vamos entender como aplicar a abordagem para criar suas páginas do zero, garantindo que elas funcionem na maior aplitude de navegadores e dispositivos. Antes de começar, é importante lembrar que para tudo funcionar bem, você precisa conhecer as funcionalidades e limitações da especificacao HTML, seus elementos, tags, e atributos aprovados, isso esta disponivel no site do w3c. É importante tambem se manter no _bleeding edge_, para que novas linguagens (como o HTML5) não fiquem de fora de suas análises e ponderações. Um plus é você conhecer (ou pelo menos ter em mãos para referência) as especificacoes de CSS 2.1 e 3 disponiveis no w3c. Vale lembrar que CSS3 e HTML5 são assuntos novos e ainda não se tornaram especificação (ainda está no status de _working draft_), o que não nos impede de usar todo o poder já disponível para se criar aplicações online.

## Analisando a aplicação: Um raio-x

As expectativas e considerações do cliente geram o design e a funcionalidade de sua aplicação. Mas como esse design deve funcionar nos mais diversos cenários é responsabilidade nossa. A primeira etapa é fazer um scan detalhado do que vai ser construido naquela etapa do processo. Se você recebeu wireframes que mostram como sua página deve ser visualizada em um monitores 4:3, 16:9 e mobile em telas paisagem e retrato você deve pegar estes 3 designs e sua estrutura **básica** de HTML para entender quais serão as partes em comum para a partir daí escrever o HTML.

<div id="attachment_2381" style="width: 710px" class="wp-caption aligncenter">
  <a href="http://tableless.com.br/uploads/2010/12/layouts.png"><img src="http://tableless.com.br/uploads/2010/12/layouts.png" alt="Wireframes mostrando diferentes designs para 16:9, 4:3, mobile horizontal e vertical" width="700" height="167" class="size-full wp-image-2381" srcset="uploads/2010/12/layouts.png 700w, uploads/2010/12/layouts-300x71.png 300w" sizes="(max-width: 700px) 100vw, 700px" /></a>
  
  <p class="wp-caption-text">
    Diferentes Wireframes para o mesmo design
  </p>
</div>

O que está presente em todas as páginas? Como deve ser a semântica e a linearidade do HTML ponderando os wireframes desktop X mobile? Se a navegação (em amarelo escuro nos designs) fizer uso de um acordion, como o HTML mais básico deverá ser escrito, de modo que o design acima seja garantido para todos os dispositivos que vão acessar a página, independente de sua configuração? (isso seria válido para qualquer plugin na página)

Com um raio-x nos designs acima, veremos que o cabeçalho(em laranja), pesquisa(azul topo), navegacao (amarelo escuro com boxes), conteúdo (centro) e rodapé (azul fundo) são as partes presentes em todos os designs. Dá até pra assumir que o exemplo acima é o de um portal – se o usuário acessa de uma tela desktop wide, anúncios (amarelo claro) são mostrados. Se o cara acessa de um desktop, uma animação no cabecalho é mostrada. 

As condições deste exemplo são simples – na vida real é **sempre** mais complexo – mas é assim que você deve montar a sua análise. Eu poderia por exemplo colocar os anúncios do wireframe 16:9 em um elemento **aside** sabendo de suas funcionalidades. A navegação poderia ser embarcada no elemento **nav**. 

Você pode se perguntar: Mas o elemento ****nav**** e **aside**, nativos do HTML5 são novos e precisaremos de um **document.createElement()** para que ele renderize em navegadores sem suporte a linguagem. Não estamos misturando Graceful Degradation aqui, uma vez que estamos usando uma solução e depois corringindo “deficiências” da solução com um patch?

Sim, estamos usando princípios de Graceful Degradation para corrigir essa limitação do HTML5, mas como estamos no planejamento da aplicação, e ela ainda não está nem perto de ser codificada, a orientação geral continua sendo o Progressive Enhancement.

Os wireframes são intuitivos, e as regras muito claras. Para as páginas de conteúdo a única funcionalidade avançada existente está na navegação(um accordion) e no topo (um slideshow). Passando um plugin de um accordion em um raio-x, vemos que o HTML dele é semântico:

<pre class="lang-html">&lt;ul&gt;&lt;!--primeiro nivel--&gt;
&lt;li&gt;
   &lt;ul&gt;&lt;!--segundo nivel--&gt;
	&lt;li&gt;
	   &lt;ul&gt;&lt;!--terceiro nivel--&gt;
		&lt;li&gt;&lt;/li&gt;
	   &lt;/ul&gt;
	 &lt;/li&gt;
     &lt;/ul&gt;
&lt;/li&gt;
&lt;/ul&gt;
</pre>

Sabemos que a manipulação que o jQuery faz não será disponível para dispositivos com javascript desabilitado. Como resolver então os níveis que devem ser ocultos em situações como essa? CSS **display:none/block;**

A estrutura usual de slideshows é muito parecida com o accordion, e a solução provavelmente seria a mesma. E esta estrutura garante a mesma experiencia de navegação ao usuario, com javascript ou não.

## Aplicando o Progressive Enhancement

Como você pode ver, os maiores segredos dessa abordagem é separar bem HTML, CSS e javascript de acordo com funcionalidades que podem ser renderizadas nos dispositivos que acessam sua página.

  * Tenha um documento HTML semântico e bem estruturado;
  * Mantenha sempre o layout separado do conteúdo (e mantenha as linhas que dividem essas áreas sempre muito bem visíveis)
  * Mantenha suas iterações avancadas em uma camada específica, tanto estilo como script, sempre atento as limitações de Usabilidade e Acessibilidade.

<div id="attachment_2380" style="width: 986px" class="wp-caption aligncenter">
  <a href="http://tableless.com.br/uploads/2010/12/fluxo_dev.png"><img src="http://tableless.com.br/uploads/2010/12/fluxo_dev.png" alt="Fluxograma de desenvolvimento orientado ao Progressive Enhancement" width="700" height="146" class="size-full wp-image-2380" srcset="uploads/2010/12/fluxo_dev.png 976w, uploads/2010/12/fluxo_dev-300x62.png 300w, uploads/2010/12/fluxo_dev-940x198.png 940w" sizes="(max-width: 700px) 100vw, 700px" /></a>
  
  <p class="wp-caption-text">
    Evolução do código HTML e CSS em uma aplicação que usa PE para diferentes versões: Básica, Mobile, Desktop e Enhanced
  </p>
</div>

As abordagens de Progressive Enhancement pedem um documento HTML muito bem estruturado e escalável, e a evolução de seu desenvolvimento é mostrado na primeira linha da visualização acima. Com um _markup_ mais básico, podemos garantir a visualização em dispositivos primitivos, fazendo com que o propósito da aplicação seja garantido. Esse markup evolui para englobar as outras versões, e com o desenvolvimento CSS não é diferente. Linearizar o desenvolvimento desta maneira traz vários benefícios: pode garantir a entrega de releases a medida que o desenvolvimento caminha, mostrando a evolução do projeto para o cliente, mantem o time de testes (se existente) com uma carga de trabalho para detecção de erros, fazendo com que o período de homoogação seja menos doloroso na entrega do projeto, a lista cresce. Normalmente para a criação de um site ou aplicação, eu uso este diagrama de fluxo para garantir que o meu desenvolvimento vai ser o mais alinhado aos métodos de Progressive Enhancement possível. Cada uma das caixas em cinza tem várias sub-divisões que vou adicionando de acordo com a necessidade do projeto. Com ele consigo garantir um grande número de dispositivos com um pouco menos de trabalho la na frente adequando páginas aos mais diferentes tipos de dispositivo.

Eu coloco o desenvolvimento da versão mobile em primeiro, e este é um ponto de discordância com alguns amigos nos papos de bar – e de IM também. Considero mobile uma versão incipiente das informações que o usuário costuma encontrar em uma versão desktop. Posso confessar que esta é uma metodologia que foi desenvolvida adequada a uma certa realidade. Ela pode variar se seu workflow de desenvolvimento é direfente. Repito o que disse no post anterior – **desenvolva, adote ou customize uma metodologia**. A minha metodologia partiu do livro do Filament Group _<a href="http://filamentgroup.com/dwpe/" target="_blank" title="Acessar o site do Filament Group">Designing with Progressive Enhancement</a>_, de artigos na web (alguns deles eu usei para montar a minha série de posts) e de análises da minha carga e tipo de trabalho.

Um exemplo? Se o seu design está sendo feito para interfaces mobile apenas, sabemos que as preocupações para engine de renderização e desktop somem, mas ainda sim teríamos uma versão **básica**, para aqueles navegadores dos celulares mais antigos, uma versão **mobile**, uma versão **enhanced**, e uma versão para **print**.

Separar a versão mobile de enhanced é apenas uma preocupação com a **escalabilidade do código**. Ainda não enfrentamos tantos problemas de interface em navegadores mobile, mas possivelmente iremos enfrentar. Não temos muitas aplicações que dependam de serviços de impressão, como o que temos no <a href="http://labnol.org/?p=17827" target="_blank" title="Acessar o Digital Inspiration">Dropbox</a>. Mas ainda vamos ter. Uma aplicação mobile que gerencie os pedidos de qualquer negócio e precise gerar a impressão de uma nota de compra ainda não aparece com frequência no mercado para se desenvolver. Mas vai. 

Percebem as águas que vamos navegar em breve? Os problemas que iremos ter que lidar, a complexidade que o desenvolvimento web vai requerer? Esse fluxograma é o que eu uso **hoje** no meu trabalho. Mas agora no final do ano ele vai ganhar um upgrade porque o iPad não está na jogada ainda quer entrar no bolo, afinal um design feito com uma palheta de cores mais viva pode ganhar com tom mais intenso, tirando maior proveito da tecnologia Retina do visor dos iPads (e dos iPhones também). 

No próximo post irei continuar o assunto que abordei no meu primeiro artigo, discutir um Plano de Usabilidade e suas fases; vamos aplicá-las em uma empresa fictícia e após termos um “Plano de Governo”, voltaremos a Xangri-lá, para a última parte desta série de posts, fazendo um grande lab mostrando a implantação de um projeto web usando os conceitos de Progressive Enhancement. _Namastê_.

### Referência

  * <a href="http://filamentgroup.com/lab/announcing_our_book_designing_with_progressive_enhancement/" target="_blank" title="Acessar o site do Filament Group e o livro">Designing with Progressive Enhancement</a>
  * <a href="http://thomasmaier.me/2010/06/css-for-iphone-4-retina-display/" target="_blank" title="Acessar o blog do Thomas Maier">Criando CSS para iPhone4</a>
  * <a href="http://thomasmaier.me/2010/03/howto-css-for-the-ipad/" target="_blank" title="Acessar o blog do Thomas Maier 2">Criando CSS para iPads</a>
  * <a href="http://www.labnol.org/internet/print-from-mobile-phones/17827/" target="_blank" title="Acessar o Digital Inspiration">Imprindo de telefones usando dropbox</a>