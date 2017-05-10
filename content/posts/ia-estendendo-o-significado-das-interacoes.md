---
title: WAI-ARIA – Estendendo o significado das interações
author: Diego Eis
type: post
date: 2013-11-18
excerpt: Saiba como você pode aumentar a acessibilidade da sua página de um jeito fácil com WAI-ARIA.
url: /wai-aria-estendendo-o-significado-das-interacoes/
dsq_thread_id: 1976320508
categories:
  - Acessibilidade
  - Código
  - HTML
  - HTML5
  - Técnicas e Práticas
tags:
  - acessibilidade
  - html5
  - wai-aria

---
O HTML serve para apenas uma coisa: dar significado à informação. Ele faz isso marcando a informação com as famosas tags. Feito isso você passa para o CSS e o Javascript, que ficarão com as responsabilidades de formatar essa informação e manipular seu comportamento.

O ponto é que a semântica não fica apenas na hora de marcar a informação com HTML puro. Como você faz para que um usuário com deficiência visual saiba que a informação que ele procura está dentro de um collapse, e esse collapse está fechado? Como você avisa que aquele lugar onde ele está navegando é o lugar mais importante da página? Que aquele monte de links que o leitor de tela está falando é o menu principal do site?

## Estendendo o significado

A WAI-ARIA serve para estender o significado das interações do seu site. Quando as tags do HTML5 vieram, elas já começaram um trabalho importante de dar significado às estruturas do layout. Você consegue marcar agora o que é um menu de navegação, uma sidebar, um header, um footer etc. Esse trabalho é muito importante por que ajuda a definir a importância dos elementos que cada elemento contém.

A semântica que as [Microdatas][1] trazem também são uma maneira de estender o significado do conteúdo. Conteúdo este que pode levar informações importantes, mas que passam despercebidos pelos robôs de busca e outros meios de acesso.

A WAI-ARIA vai ajudar muito em aplicações onde a informação é dividida em várias porções na tela em diversos elementos que precisam de interação para que a informação seja visualizada, como um clique, fazendo com que a acessibilidade seja prejudicada e o usuário não consiga acessar todas as partes desse layout de maneira linear.

## Roles, states e properties

A WAI-ARIA é divide a semântica em duas partes: Roles, que define que tipo de elemento o usuário está interagindo e States/Properties que são suportadas pelas Roles, que definem o estado daquele elemento.

Com a Role você fala que determinado elemento é uma collapse, com o States/Properties você diz se esse collapse está aberto ou fechado.

Isso tudo você vai definir direto no elemento, via atributos. Coisa simples.

### Roles

São 4 tipos de roles. Cada tipo de role é responsável por um determinado gênero de elemento.

  * **Abstract** para definição de conceitos gerais. Não devemos usar para marcar conteúdo. Confesso que ainda estou tentando entender esse tipo de Role. &#8220;Conceitos abstratos&#8221; é algo muito abstrato para eu entender. 🙂
  * **Widgets** para marcar elementos de interface soltos, como caixas de alerta, botões, checkbox, links, tabs etc.
  * **Document Structure** para definir estruturas de organização da página. Estruturas que não são interativas como o header, footer, sidebar, main, essas coisas.
  * **Landmarks** para regiões de página que são pontos importantes para onde o usuário navegaria, por exemplo: buscas, conteúdo principal, sidebar, formulários etc… 

Não dá para mostrar aqui todas as roles que existem. São muitas. Para ver toda a lista, [vá direto no site do W3C][2]. Lá você vai encontrar todas as categorizações das roles. Aqui vou dar alguns exemplos simples de cada tipo.

#### Role Document Structure

As roles dessa categoria servem para indicar que aquele elemento faz parte da estrutura do layout. Veja um exemplo bem básico:

<pre class="lang-html">&lt;article role="article"&gt;
   &lt;p&gt;Texto&lt;/p&gt;
&lt;/article&gt;
</pre>

Claro, da forma escrita acima, fica muito redundante. Mas suponha que você esteja usando outro elemento para envolver o texto do artigo/post/conteúdo do seu site:

<pre class="lang-html">&lt;div class="post" role="article"&gt;
   &lt;p&gt;Texto&lt;/p&gt;
&lt;/div&gt;
</pre>

Ou se você for fazer um menu:

<pre class="lang-html">&lt;ul role="menubar"&gt;
  &lt;li role="menuitem"&gt;&Iacute;tem&lt;/li&gt;
  &lt;li role="menuitem"&gt;&Iacute;tem 1&lt;/li&gt;
  &lt;li role="menuitem"&gt;&Iacute;tem 2&lt;/li&gt;
&lt;/ul&gt;
</pre>

Ou uma sidebar ou algum elemento que complementa a informação da página:

<pre class="lang-html">&lt;aside role="complementary"&gt;
   ...conte&uacute;do...
&lt;/aside&gt;
</pre>

#### Role Widget

Tabs é um elemento muito comum nos websites. Ajuda bastante a organização de conteúdos. Mas pode ser um parto para quem usa leitores de tela e está tentando navegar no site. Um código comum de tabs seria este:

<pre class="lang-html">&lt;ul class="tabs"&gt;
   &lt;li&gt;
      &lt;a href="#tab-panel1" class="active" id="tab1"&gt;Primeira Aba&lt;/a&gt;
      &lt;a href="#tab-panel2" id="tab2"&gt;Segunda Aba&lt;/a&gt;
      &lt;a href="#tab-panel3" id="tab3"&gt;Terceira Aba&lt;/a&gt;
   &lt;/li&gt;
&lt;/ul&gt;

&lt;div class="tab-content" id="tab-panel1"&gt;
  Conte&uacute;do primeira aba
&lt;/div&gt;
&lt;div class="tab-content" id="tab-panel2"&gt;
  Conte&uacute;do segunda aba
&lt;/div&gt;
&lt;div class="tab-content" id="tab-panel3"&gt;
  Conte&uacute;do terceira aba
&lt;/div&gt;
</pre>

Agora, aplicando a WAI-ARIA, fica assim:

<pre class="lang-html">&lt;ul class="tabs"&gt;
   &lt;li&gt;
      &lt;a href="#tab-panel1" class="active" id="tab1" role="tab" aria-selected="true"&gt;Primeira Aba&lt;/a&gt;
      &lt;a href="#tab-panel2" id="tab2" role="tab"&gt;Segunda Aba&lt;/a&gt;
      &lt;a href="#tab-panel3" id="tab3" role="tab"&gt;Terceira Aba&lt;/a&gt;
   &lt;/li&gt;
&lt;/ul&gt;

&lt;div class="tab-content" id="tab-panel1" role="tabpanel" aria-labelledby="tab1"&gt;
  Conte&uacute;do primeira aba
&lt;/div&gt;
&lt;div class="tab-content" id="tab-panel2" role="tabpanel" aria-labelledby="tab2"&gt;
  Conte&uacute;do segunda aba
&lt;/div&gt;
&lt;div class="tab-content" id="tab-panel3" role="tabpanel" aria-labelledby="tab3"&gt;
  Conte&uacute;do terceira aba
&lt;/div&gt;
</pre>

#### Role Landmarks

As **landmarks** servem para conduzir a navegação do usuário. Com as roles de landmarks você vai marcar áreas na página importantes para que o usuário encontre os blocos de informações mais importantes. Veja um exemplo:

Para um bloco que contém links para navegação:

<pre class="lang-html">&lt;nav role="navigation"&gt;
</pre>

Ou para o bloco principal da página:

<pre class="lang-html">&lt;main role="main"&gt;
</pre>

Eu sei, você deve estar se perguntando: &#8220;Poxa, mas as novas tags do HTML5 já não fazem este trabalho?&#8221;, aí eu respondo: &#8220;Sim, fazem!&#8221;.
  
Mas pode ser que você precisou marcar áreas da página sem usar as tags do HTML5. Nesse caso você tem toda a liberdade de marcar qualquer elemento do HTML essas roles.

Mesmo assim, existem algumas roles de landmarks que não tem tags relativas no HTML. Veja algumas:

**role=&#8221;banner&#8221;** Uma região que contém uma imagem principal ou um título de destaque que introduz a página. Pode ser aplicado também em áreas onde por exemplo você coloca logos de outras empresas, banires de publicidade e etc.

**role=&#8221;complementary&#8221;** para marcar uma seção do documento que agrega mais informações ao conteúdo principal da página. Uma sidebar, um footer, blocos de navegação relacionada e etc podem ser marcadas com essa role.

**role=&#8221;content info&#8221;** usado para marcar dados que indicam mais informações sobre o site. Como por exemplo notas de rodapé, informações de copyright, links para termos de uso e etc.

Portanto, mesmo que alguns elementos fiquem redundantes, é interessante você saber que a WAI-ARIA precisa ser genérica para dar flexibilidade para os devs colocarem esse tipo de informação em qualquer tipo de elemento. Saiba também que grande parte dos leitores de tela não conhecem as tags do HTML5 e dão ênfase para as WAI-ARIA em vez das novas tags.

### Estados e Propriedades

Aqui você marca os estados ou as propriedades de cada elemento. É muito simples também. Por exemplo, suponha que você tenha um collapse com o código abaixo:

<img src="http://tableless.com.br/uploads/2013/11/Screen-Shot-2013-11-18-at-11.36.46-AM.png" alt="Screen Shot 2013-11-18 at 11.36.46 AM" width="857" height="263" class="alignnone size-full wp-image-39521" srcset="uploads/2013/11/Screen-Shot-2013-11-18-at-11.36.46-AM.png 857w, uploads/2013/11/Screen-Shot-2013-11-18-at-11.36.46-AM-329x100.png 329w, uploads/2013/11/Screen-Shot-2013-11-18-at-11.36.46-AM-588x180.png 588w, uploads/2013/11/Screen-Shot-2013-11-18-at-11.36.46-AM-660x202.png 660w" sizes="(max-width: 857px) 100vw, 857px" />

Quando o collapse abre, o código pode ficar assim:

<pre class="lang-html">&lt;div class="collapse"&gt;
   &lt;h1&gt;Um exemplo simples com texto&lt;/h1&gt;	
   &lt;p&gt;Conteúdo que ativa a collapse&lt;/p&gt;

   &lt;div class="collapse-box" aria-expanded=&ldquo;true&rdquo;&gt;
     Conteúdo da collapse.
   &lt;/div&gt;
&lt;/div&gt;
</pre>

Note que o atributo `aria-expanded="true"` indica que o collapse está aberto. Quando ele está fechado, basta mudarmos o valor para `aria-expanded="false"`

Há também o caso de algum elemento que controle uma modal ou tenha um submenu. Veja como é simples:

<img src="http://tableless.com.br/uploads/2013/11/Screen-Shot-2013-11-18-at-11.40.54-AM.png" alt="Screen Shot 2013-11-18 at 11.40.54 AM" width="384" height="383" class="alignnone size-full wp-image-39522" srcset="uploads/2013/11/Screen-Shot-2013-11-18-at-11.40.54-AM.png 384w, uploads/2013/11/Screen-Shot-2013-11-18-at-11.40.54-AM-168x168.png 168w, uploads/2013/11/Screen-Shot-2013-11-18-at-11.40.54-AM-310x310.png 310w" sizes="(max-width: 384px) 100vw, 384px" />

<pre class="lang-html">&lt;ul&gt;
  &lt;li aria-haspopup="true"&gt;
    &lt;a href="#"&gt;Mensagens&lt;/a&gt;
    &lt;ul&gt;
      &lt;li&gt;&lt;a href="#"&gt;Enviar&lt;/a&gt;&lt;/li&gt;
      &lt;li&gt;&lt;a href="#"&gt;Criar&lt;/a&gt;&lt;/li&gt;
      &lt;li&gt;&lt;a href="#"&gt;Editar&lt;/a&gt;&lt;/li&gt;
      &lt;li&gt;&lt;a href="#"&gt;Relat&oacute;rios&lt;/a&gt;&lt;/li&gt;
    &lt;/ul&gt;
  &lt;/li&gt;
&lt;/ul&gt;
</pre>

Note o atributo `aria-haspopup="true"` que indica que aquele LI controla um submenu.

Ou, suponha que você tenha um botão de enviar. Essa ação precisa de uma descrição explicativa. Como o exemplo abaixo:

<img src="http://tableless.com.br/uploads/2013/11/Screen-Shot-2013-11-18-at-11.42.53-AM.png" alt="Screen Shot 2013-11-18 at 11.42.53 AM" width="648" height="141" class="alignnone size-full wp-image-39523" srcset="uploads/2013/11/Screen-Shot-2013-11-18-at-11.42.53-AM.png 648w, uploads/2013/11/Screen-Shot-2013-11-18-at-11.42.53-AM-329x71.png 329w, uploads/2013/11/Screen-Shot-2013-11-18-at-11.42.53-AM-588x127.png 588w" sizes="(max-width: 648px) 100vw, 648px" />

<pre class="lang-html">&lt;a class="btn btn-primary" aria-describeby="desc-send"&gt;
  Enviar
&lt;/a&gt;

&lt;p id="desc-send"&gt;
  Esta &eacute; uma descri&ccedil;&atilde;o explicando a a&ccedil;&atilde;o&hellip;
&lt;/p&gt;
</pre>

O atributo `aria-describeby="id-do-elemento-descricao"` indica qual elemento está descrevendo aquela ação.

Outro exemplo muito interessante:
  
<img src="http://tableless.com.br/uploads/2013/11/Screen-Shot-2013-11-18-at-11.45.32-AM.png" alt="Screen Shot 2013-11-18 at 11.45.32 AM" width="576" height="140" class="alignnone size-full wp-image-39524" srcset="uploads/2013/11/Screen-Shot-2013-11-18-at-11.45.32-AM.png 576w, uploads/2013/11/Screen-Shot-2013-11-18-at-11.45.32-AM-329x79.png 329w" sizes="(max-width: 576px) 100vw, 576px" />

Eu sei que é chato customizar essas coisas, mas às vezes é necessário. Se tiver que fazê-lo, faça do jeito certo. Assim:

<pre class="lang-html">&lt;div role="radiogroup"&gt;
  &lt;span role="radio" aria-checked="unchecked"&gt;
    Option Unchecked
  &lt;/span&gt;

  &lt;span role="radio" aria-checked="checked"&gt;
    Option Checked
  &lt;/span&gt;
&lt;/div&gt;
</pre>

## Observações importantes</h3> 

Existem algumas restrições e observações importantes que você precisa estar ciente. Alguns devs acham que é só sair colocando os atributos do WAI-ARIA que tudo passa a fiar semântico, o que é mentira.

### Prefira sempre usar os elementos corretos

Eu sei que WAI-ARIA é muito, muito bom. Mas não prefira usá-las ao invés de usar os elementos padrão do HTML. Eles trazem mais semântica do que elementos neutros usando WAI-ARIA.

Nunca faça isso:

<pre class="lang-html">&lt;span role="button"&gt;Bot&atilde;o&lt;/span&gt;
</pre>

Prefira fazer assim:

<pre class="lang-html">&lt;button role="button"&gt;Bot&atilde;o&lt;/button&gt;
</pre>

Sempre a semântica natural do HTML é a mais indicada e sempre prevalece. 

### Interação com o teclado

Todas as interações com WAI-ARIA devem ser usadas via teclado.

Se você cria um widget que o usuário pode clicar, fazer drag and drop, slide, scroll etc, o usuário deve também interagir com o widget e performar essa interação com uma ação equivalente usando o teclado.

Todos os &#8220;widgets&#8221; devem responder aos comandos e combinações padrão de teclas dos sistemas operacionais. Por exemplo, se você desenha um botão com uma tag `span` e coloca um `role="button"`, este elemento deve trabalhar como um botão, ou seja, se o usuário der foco a este elemento e apertar ENTER, o botão deve agir.

### Inserindo atributos do WAI-ARIA via script

Prefira colocar estes atributos via Javascript. Não há problema algum fazer dessa forma.
  
Sugiro até que você faça isso integrando com as respectivas funções. Por exemplo: se há uma função que fazem as tabs funcionarem, coloque as **roles** correspondentes às tabs nesta função.

Por outro lado, se você sabe que o seu público usa Javascript desabilitado (o que é muito, muito difícil), prefira colocar diretamente no código HTML do elemento. Assim você garante que o WAI-ARIA vai funcionar mesmo que o usuário desabilite o JS.

## Apresentação

Fiz uma apresentação na [Conferência do W3C][3] este ano falando sobre esse assunto. Veja ela aqui:



 **<a href="https://www.slideshare.net/diegoeis/waiaria-interaes-acessveis-na-web" title="WAI-ARIA - Interações acessíveis na web" target="_blank">WAI-ARIA &#8211; Interações acessíveis na web</a>** de **<a href="http://www.slideshare.net/diegoeis" target="_blank">Diego Eis</a>** 

## Para ler mais:

Veja vários exemplos [no site OpenAjax][4].

Aqui tem a [documentação oficial do W3C][5].

Mais de [WAI-ARIA no MDN da Mozilla][6].

Usando [WAI-ARIA Landmarks][7].

 [1]: http://tableless.com.br/introducao-a-microdata-no-html5/
 [2]: http://www.w3.org/TR/wai-aria/roles#roles_categorization
 [3]: http://conferenciaweb.w3c.br
 [4]: http://oaa-accessibility.org/examples/
 [5]: http://www.w3.org/TR/wai-aria/
 [6]: https://developer.mozilla.org/en-US/docs/Accessibility/ARIA
 [7]: http://blog.paciellogroup.com/2013/02/using-wai-aria-landmarks-2013/