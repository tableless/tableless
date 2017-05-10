---
title: O Caminho Suave para o Tableless
author: Elcio Ferreira
type: post
date: 2007-12-06
url: /o-caminho-suave-para-o-tableless/
tweetbackscheck:
  - 1356411116
shorturls:
  - 'a:3:{s:9:"permalink";s:56:"http://tableless.com.br/o-caminho-suave-para-o-tableless";s:7:"tinyurl";s:26:"http://tinyurl.com/3ls4hqa";s:4:"isgd";s:19:"http://is.gd/vynHZ8";}'
twittercomments:
  - 'a:1:{i:20193385138626560;s:6:"136520";}'
tweetcount:
  - 1
dsq_thread_id: 503037717
categories:
  - Artigos
  - Técnicas e Práticas
  - Tecnologia e Tendências
tags:
  - CSS
  - desenvolvimento
  - design
  - html
  - internet
  - opera
  - Semântica
  - tableless
  - tableless.com.br
  - tags
  - tutorial
  - web standards
  - xhtml
  - xml
  - xslt

---
A maior parte dos desenvolvedores web, designers ou programadores, começaram antes do surgimento dos movimentos em prol dos [padrões web][1], usando tabelas para montar layouts em editores <acronym title="What You See Is What You Get, Editores Visuais">WYSIWYG</acronym>, e ainda hoje este método é usado na maioria dos projetos de internet. Logo, é natural que muita gente, ao começar a entender o valor dos [padrões][1], se pergunte como migrar do desenvolvimento &#8220;tradicional&#8221; para o desenvolvimento de código semanticamente coerente.

É um caminho muito duro o que separa o desenvolvedor acostumado a editores visuais do desenvolvimento de código coerente. E é muito comum que o designer desista após uma primeira tentativa frustrada de desenvolver um website tableless, com layout [CSS][2] e [XHTML][3] [validado][4].

Por isso gostaria de propor um caminho gradual, mais suave, para aqueles que querem se aventurar pela primeira vez pelos [padrões web][1]. O princípio desse método é da recompensa. Você pode obter um grande benefício aproximando seu código dos [padrões web][1], mesmo que não faça tudo de uma vez. Quero mostrar como você pode começar, e obter benefícios imediatos.

### Limpe seu HTML

A minha primeira recomendação é que você estude [CSS][2]. Comece pela formatação básica de fonte, cor e tamanho. Isso vai te garantir código menor e produtividade maior com pouquíssimo esforço.

Assim, ao criar um item de menu, você vai evitar códigos como este:

<pre>&lt;a href="parceiros.asp"&gt;&lt;font
face="Arial, Helvetica, Sans-serif" size="2"
color="#FF3300"&gt;&lt;b&gt;Parceiros&lt;/b&gt;&lt;/font&gt;&lt;/a&gt;</pre>

Colocando no lugar:

<pre>&lt;a href="parceiros.asp" class="menu"&gt;Parceiros&lt;/a&gt;</pre>

Tendo no [CSS][2]:

<pre>.menu{
<a href="http://www.w3.org/TR/REC-CSS1#font-family">font-family</a>: Arial, Helvetica, Sans-serif;
<a href="http://www.w3.org/TR/REC-CSS1#font-size">font-size</a>: 80%;
<a href="http://www.w3.org/TR/REC-CSS1#font-weight">font-weight</a>: bold;
<a href="http://www.w3.org/TR/REC-CSS1#color">color</a>:#FF3300;
}</pre>

Como você pode ver, o [CSS][2] é extremamente simples. Aprender esses quatro atributos, mais o &#8220;[font-style][5]&#8221; (para fazer itálico), é a primeira coisa que eu recomendo. É claro, isso apenas faz cócegas nas possibilidades do [CSS][2], ainda há muito o que aprender, mas recomendo começar por aí porque é algo que você pode aprender em alguns minutos e vai te salvar muito, muito tempo. E você vai começar a ter o controle da formatação, tendo todas as definições de fonte em um único arquivo, podendo alterar, por exemplo, a qualquer momento, a fonte de todo o conteúdo ou de todos os menus do site.

O passo seguinte para limpar seu HTML é se livrar do spacer.gif, aquele gif transparente de 1 pixel que se usa para dar espaços em tabelas, e das dezenas de tabelas aninhadas. Para isso vamos começar a estudar o &#8220;box-model&#8221;.

O pulo-do-gato aqui é um atributo [CSS][2] chamado [padding][6]. O [padding][6] é a distância entre as bordas de um elemento e o texto dentro dele. Assim, se é preciso que o conteúdo de uma célula esteja a 10 pixels da borda esquerda, ao invés de inserir uma célula extra como espaçador, ou inserir mais uma tabela, basta definir uma classe para essa célula. Uma vez que você já está colocando a formatação no [CSS][2], provavelmente esta célula já tem uma classe. Então basta:

<pre>.conteudo{
<a href="http://www.w3.org/TR/REC-CSS1#padding">padding</a>-left:10px;
}</pre>

Isso vai fazer com que o texto esteja a 10 pixels da borda esquerda do documento. Ah, claro, o [CSS][2] também pode livrar você de definir no HTML as bordas e o background das células de sua tabela. Lembre-se, quanto mais layout e formatação você colocar no [CSS][2], mais controle terá sobre seu site, principalmente em mudanças de layout durante o processo de produção e em futuras manutenções. O site também será mais leve para carregar.

Concluímos então que, após aprender os atributos de formatação de fonte, o passo seguinte é aprender os atributos [background][7], [border][8] e [padding][6]. Indo até aqui você com certeza será um desenvolvedor muito mais feliz! Depois de limpar seu HTML, ganhar controle sobre a formatação de seu site e se tornar muito mais produtivo, você está pronto para passar à segunda etapa, correndo atrás da semântica.

### Começando o Trabalho de Gente Grande

Muito bem, agora você já pode limpar seu código. Vamos estudar um exemplo prático. No começo de cada uma de suas páginas você tem um título, cujo código hoje é assim:

<pre>&lt;font face="Arial, Helvetica, Sans-serif" size="4"
color="#FFFF00"&gt;&lt;b&gt;Novidades&lt;/b&gt;&lt;/font&gt;</pre>

Ao limpar esse código, você vai substituir esse monte de tags por uma só. Que tag você vai usar? Como o [CSS][2] te permite formatar qualquer elemento, muita gente que começa a estudar o assunto acha que é indiferente que tag usar, e coloca algo como:

<pre>&lt;p class="titulo"&gt;Novidades&lt;/p&gt;</pre>

Agora, veja bem, outro desenvolvedor poderia resolver o mesmo problema com:

<pre>&lt;div class="titulo"&gt;Novidades&lt;/div&gt;</pre>

E o resultado visual poderia ser o mesmo. Acontece que há algo na natureza do HTML que nos diz que tag usar. Chamamos esse algo de &#8220;semântica&#8221;: as tags do HTML tem significado. A tag P é para parágrafos, a tag DIV para divisões no conteúdo, e há uma série de tags para título, h1, h2, h3, h4, h5 e h6. Assim, se você pode usar qualquer tag, pode fazer assim:

<pre>&lt;h1&gt;Novidades&lt;/h1&gt;</pre>

O que você ganha com essa preocupação? Os buscadores inteligentes podem ler semanticamente o conteúdo de um documento, entendendo que trecho de código é um título, por exemplo. Assim, escrever HTML semanticamente correto pode melhorar muito sua visibilidade em buscadores. O segundo bom motivo é que você vai saber para que serve cada tag se tiver que mexer nesse mesmo documento daqui a alguns meses. E vai ser mais fácil também se outra pessoa tiver que dar manutenção no seu código.

Logo, use as tags do HTML para aquilo para o que foram criadas:

  * dd, dl e dt para listas de definições (um glossário, por exemplo)
  * h1 a h6 para títulos
  * p para parágrafos
  * abbr para abreviaturas e acronym para acrônimos
  * blockquote e q para citações longas e curtas
  * address para endereços (sabe aquele rodapé onde vai o endereço e o telefone da empresa?)
  * ul e ol para listas e li para os itens da lista

Você pode obter uma lista mais abrangente em:
  
[http://www.w3schools.com/xhtml/xhtml_reference.asp][9]

E formate tudo ao seu gosto com [CSS][2].

### Finalmente, Livrando-se das Tabelas

Não há bons motivos para você eliminar a qualquer custo todas as tabelas de seu primeiro trabalho. Conheço alguns excelentes profissionais, muito talentosos, que fizeram um ótimo trabalho em sua primeira tentativa de tableless. Mas a maioria dos que eu vi tentarem demoraram muito para conseguir da primeira vez, e alguns não obtiveram os resultados que esperavam. Isso tudo serve para que você possa produzir mais rápido e melhor, não o contrário. Então vá com calma. Faça alguns estudos em tableless, comece eliminando parte das tabelas em seus primeiros trabalhos. Por exemplo, remover as células de tabela que formam o menu, trocando por uma lista (com as tags ul e li), é um ótimo desafio para o primeiro projeto.

Ah, e não se esqueça que para dados como uma tabela periódica ou um calendário a solução semanticamente correta é a tabela mesmo. Ou seja, tableless não é ausência de tabelas, é o seu uso apenas onde é semanticamente justificável.

Não vou entrar em detalhes aqui, porque já escrevi bastante sobre como construir um layout no [Tutorial Tableless Básico][10], mas o conselho é ir com calma, sem estresse. Você logo vai estar produzindo tableless mais fácil do que produz sites com tabelas.

### XHTML

Há uma coisa que muita gente que está começando me pergunta: o que é e para que serve esse tal de [XHTML][3]? É muito mais simples do que parece. Um arquivo [XHTML][3] é um arquivo HTML, que pode ser lido por qualquer browser. Não estamos falando de um novo HTML, com novas tags ou coisa assim. Pelo contrário, o [XHTML][3] 1 foi feito para funcionar mesmo em navegadores antigos. Mas, ao mesmo tempo, Um arquivo [XHTML][3] é também um arquivo [XML][11] [válido][4], que pode ser lido por qualquer interpretador de [XML][11].

Meu primeiro conselho, nesse caso, é que você, se não trabalha com [XML][11], deixe preocupação com o [XHTML][3] para depois de dominar bem o código semântico e o layout tableless. Não porque seja complicado, pelo contrário, transformar bom HTML em [XHTML][3] é bem simples, mas simplesmente porque você pode obter benefícios muito significativos, e muito mais rapidamente, aprendendo [CSS][2] do que [XHTML][3].

O segundo conselho é que você comece a estudar o assunto. Depois de dominar bem layouts [CSS][2], mergulhe no [XML][11]. A maioria dos bancos de dados hoje permite extrair dados diretamente em [XML][11] e todas as plataformas de aplicações web trabalham bem com [XML][11]. E com a poderosa linguagem [XSLT][12] você pode muito facilmente oferecer seus os dados em [XHTML][3] para o navegador. 

### Voando Alto

Estamos falando de muito mais do que criar sites estilosos. Há duas semanas esteve aqui um amigo com um Palm novo, um [Zire 71][13], e um celular com acesso à internet. Isso está se tornando cada vez mais barato e comum. Conheço também uma porção de empresas e instituições, entre elas uma série significativa de TeleCentros e órgãos públicos, que estão adotando [Linux][14] como sistema operacional para desktops. O [Google][15] hoje é responsável por 90% do tráfego que meu site consegue de buscadores. É o primeiro colocado absoluto entre os buscadores. E conseguiu isso indexando semanticamente o conteúdo real dos sites. Praticamente todas as plataformas web estão oferendo suporte a [XML][11] e apostando na idéia de [webservices][16].

Quem segue os [padrões web][1] não precisa ter medo do futuro. Não importa que browser vai ser o mais usado daqui a dois anos, que tecnologia vai estar na moda ou de onde as pessoas vão estar usando a internet. Seu site estará lá, leve, acessível, atual e útil.

 [1]: http://www.webstandards.org/ "Web Standards Project"
 [2]: http://www.w3.org/Style/CSS/ "Cascading Style Sheets"
 [3]: http://www.w3schools.com/xhtml/ "Extensible HyperText Markup Language"
 [4]: http://validator.w3.org/ "W3C MarkUp Validation Service"
 [5]: http://www.w3.org/TR/REC-CSS1#font-style
 [6]: http://www.w3.org/TR/REC-CSS1#padding
 [7]: http://www.w3.org/TR/REC-CSS1#background
 [8]: http://www.w3.org/TR/REC-CSS1#border
 [9]: http://www.w3schools.com/xhtml/xhtml_reference.asp "XHTML Reference"
 [10]: http://tableless.com.br/tutorial/
 [11]: http://www.w3.org/XML/ "Extensible Markup Language"
 [12]: http://www.w3.org/Style/XSL/ "Extensible Stylesheet Language"
 [13]: http://www.palmone.com/us/products/handhelds/zire71/
 [14]: http://www.google.com.br/search?q=Linux&btnI=1&lr=lang_pt
 [15]: http://www.google.com.br "O Oráculo"
 [16]: http://www.google.com.br/search?q=webservices+xml&btnI=1&lr=lang_pt