---
title: 'O básico: O que é HTML?'
author: Diego Eis
type: post
date: 2011-01-21
excerpt: Entenda o HTML básico, saiba o que significa tags do HTML e entenda como fazer.
url: /o-que-html-basico/
tweetbackscheck:
  - 1356450861
dsq_thread_id: 511187823
shorturls:
  - 'a:3:{s:9:"permalink";s:42:"http://tableless.com.br/o-que-html-basico/";s:7:"tinyurl";s:26:"http://tinyurl.com/cgp5r8b";s:4:"isgd";s:19:"http://is.gd/rCoZs5";}'
twittercomments:
  - 'a:8:{i:149599866639753217;s:7:"retweet";i:149590604609896450;s:7:"retweet";i:149575994813071360;s:7:"retweet";i:149567349270392832;s:7:"retweet";i:149566183694270464;s:7:"retweet";i:149565391172157440;s:7:"retweet";i:149565294963208192;s:7:"retweet";i:149565261299720192;s:7:"retweet";}'
tweetcount:
  - 5
categories:
  - O Básico
tags:
  - 2011
  - desenvolvimento
  - desenvolvimento web
  - padroes web

---
HTML é uma das linguagens que utilizamos para desenvolver websites. O acrônimo HTML vem do inglês e significa Hypertext Markup Language ou em português Linguagem de Marcação de Hipertexto.

O HTML é a liguagem base da internet. Foi criada para ser de fácil entendimento por seres humanos e também por máquinas, como por exemplo o Google ou outros sistemas que percorrem a internet capturando informação.

### Quem criou o HTML?

Tim Berners-Lee. Esse é o nome do homem que criou o HTML. Ele criou o HTML para a comunicação e disseminação de pesquisas entre ele e seu grupo de colegas. O HTML ficou bastante conhecido quando começou a ser utilizada para formar a rede pública daquela época, o que se tornaria mais tarde a internet que conhecemos hoje.

### O que são as tags do HTML?

O HTML é uma linguagem baseada em marcação. Nós marcamos os elementos para mostrar quais informações a página exibe. Por exemplo, um título importante. Aquele título do artigo, da manchete do site, nós marcamos com uma tag/elemento chamado H1. Veja um exemplo:

<pre class="lang-html">&lt;h1&gt;Aqui vai o texto do t&iacute;tulo&lt;/h1&gt;
</pre>

Perceba que o texto está entre duas marcações. Essas marcações são chamadas de TAGS. As tags são abertas e depois fechadas. No exemplo acima abrimos a tag com **<h1>** e fechamos com **</h1>**. O que está dentro é o conteúdo mostrado para o usuário.

O parágrafos são marcados com a tag P. Assim:

<pre class="lang-html">&lt;p&gt;Aqui vai o texto do par&aacute;grafo. 
Geralmente par&aacute;grafos tem muitas palavras, 
letras menores que as do t&iacute;tulo&lt;/p&gt;
</pre>

Utilizando as tags, nós dizemos para o navegador o que é cada informação. O que é um título, o que é um parágrafo, o que é um botão, um formulário etc. Dizemos também o que é cada coisa para os sistemas de busca, como o Google. O Google, nesse caso, para exibir os resultados de busca, ele precisa saber o que é um parágrafo e o que é um título. Ele sabe disso através das tags.

### A estrutura básica

Todo HTML começa do mesmo jeito. Não há segredos aqui. Você pode simplesmente copiar em algum lugar para usar esse código toda vez iniciar um novo HTML.

<pre class="lang-html">&lt;!DOCTYPE html&gt;

&lt;html lang="pt-br"&gt;
&lt;head&gt;
	&lt;meta charset="utf-8"&gt;
	&lt;title&gt;T&iacute;tulo da p&aacute;gina&lt;/title&gt;
&lt;/head&gt;
&lt;body&gt;
 ... aqui vai todo o codigo HTML que faz seu site...
&lt;/body&gt;
&lt;/html&gt;
</pre>

A primeira linha se chamada DOCTYPE. O Doctype avisa aos browsers, robôs de busca, leitores de tela e outras coisas que tipo de documento e aquele que eles estao prestes a carregar. Existem outros códigos que podemos carregar, por exemplo XML. Por isso o Doctype avisa o browser para que ele saiba como se comportar ao ler o código.

Depois começamos com a Tag HTML. Isso quer dizer que todo o que estiver entre as tags <html></html> é escrito em HTML. Ao lado da palavra HTML tem um atributo (explico o que são atributos mais pra frente) chamado lang, onde indicamos qual o idioma do texto que escreveremos.

Logo após a tag html temos a tag <head>. Na tag Head nós indicamos o título do documento e indicamos a tabela de caractéres que o browser deve usar para renderizar seu texto. Também não se preocupe com isso agora.
  
A tag &lttitle> é muito importante. É com ela que você indica o título do documento. O Google e outros sistemas de busca utilizam essa tag para indicar em suas buscas o título da págin. Isso é muito importante para que você apareça bem nas buscas.

Logo depois da tag de fechamento </head> começamos a tag <body>. Dentro deste elemento é que vamos escrever todo o código HTML do resto do site.

<pre class="lang-html">&lt;!DOCTYPE html&gt;

&lt;html lang="pt-br"&gt;
&lt;head&gt;
	&lt;meta charset="utf-8"&gt;
	&lt;title&gt;T&iacute;tulo da p&aacute;gina&lt;/title&gt;
&lt;/head&gt;
&lt;body&gt;
   &lt;h1&gt;Aqui vai o texto do t&iacute;tulo&lt;/h1&gt;
   &lt;p&gt;Aqui vai o texto do par&aacute;grafo. 
   Geralmente par&aacute;grafos tem muitas palavras, letras menores que as do t&iacute;tulo&lt;/p&gt;
&lt;/body&gt;
&lt;/html&gt;
</pre>

### Criando seu primeiro HTML

Para criar seu HTML é muito simples. Primeiro, abra e crie um arquivo vazio, sem texto, com o nome **index.html**. Utilize o Notepad (se estiver no windows) ou o TextEdit (se estiver no Mac).
  
Perceba que a extensão do seu arquivo é **.html** e não **.txt**

Feito isso, copie o código utilizado no exemplo acima e cole neste documento. Salve e abra no seu navegador. Voilá! Você fez seu primeiro arquivo HTML

### Um pouco avançado: Desenvolvimento em Camadas

Um dos principais problemas no desenvolvimento para internet é a mistura dos diversos códigos. Nós não usamos apenas o HTML para fazer sites. Além do HTML, utilizamos ainda o CSS, que é uma linguagem para configurarmos o visual das páginas e o Javascript, que vai cuidar do comportamento da página, por exemplo, o que acontece quando o usuário clica em um botão.
  
Há também as linguagens chamadas Linguagens Server-Side, que são linguagens como PHP, Python, Ruby, ASP e etc. Essas linguagens fazem tudo funcionar. Elas fazem os cálculos nos servidores e dão a resposta para o navegador do usuário.

Para que os códigos não se misturem, nós os separamos em diversas camadas. Para ficar mais fácil de entender, imagine que o HTML é sempre o esqueleto do site. É com ele que vamos fazer toda a estrutura de código, onde iremos dizer o que é um título, o que é um parágrafo, uma imagem e etc. O CSS será a parte externa do corpo. É o que deixará o esqueleto bonito. É com o CSS que iremos dar cor para o título, configurar o tamanho do texto, largura das colunas e etc.

Dessa forma nós não misturamos o código HTML e o código CSS. Utilizamos a mesma ideia para separar os outros códigos citados acima.

Este é o básico. É conceito puro, por que você precisa começar de algum lugar. 😉

Mais referências:

  * [Quer aprender HTML? Faça aulas particulares conosco.][1]
  * [Videos tutoriais sobre desenvolvimento web][2]
  * [Um artigo muito completo no Wikipedia][3]
  * [Sobre o desenvolvimento web em camadas.][4]
  * [Áudio: Sobre marcação HTML][5]

 [1]: http://tableless.com.br/servicos/aula-particular.php "aula particular de html"
 [2]: http://campus.tableless.com.br/?utm_source=Tableless&utm_medium=linkOqueHTML&utm_campaign=linkCampusOnline
 [3]: http://pt.wikipedia.org/wiki/HTML
 [4]: http://wp.me/p1vY5N-kS
 [5]: http://tableless.com.br/drops-2-a-palavra-marcacao-do-html/ "Drops 2 – A palavra Marcação do HTML"