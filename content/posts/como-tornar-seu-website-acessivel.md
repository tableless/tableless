---
title: Como tornar seu website acessível?
author: Thaiana Poplade
type: post
date: 2010-10-18
excerpt: 'Ao ler este título talvez você esteja se perguntando: “mas se ele já foi publicado, já pode ser acessado por todos, certo?!” e a resposta mais correta é: “depende”. Que tal entender melhor o que significa acessibilidade na web?'
url: /como-tornar-seu-website-acessivel/
aktt_notify_twitter:
  - yes
tweetbackscheck:
  - 1356448605
shorturls:
  - 'a:3:{s:9:"permalink";s:57:"http://tableless.com.br/como-tornar-seu-website-acessivel";s:7:"tinyurl";s:26:"http://tinyurl.com/3ccl9so";s:4:"isgd";s:19:"http://is.gd/9K4DaG";}'
twittercomments:
  - 'a:0:{}'
dsq_thread_id: 503039664
categories:
  - Acessibilidade
  - Artigos
tags:
  - acessibilidade
  - desenvolvimento web
  - web standards

---
Tornar um site acessível, ainda que num processo lento, tem sido uma das buscas de alguns desenvolvedores, seja pelo objetivo específico de um site em questão ou por algum novo público que a agência ou empresa a qual ele trabalha está buscando atender.
  
Assim como no mundo real, onde lugares adaptados à pessoas com deficiências físicas ou mentais ainda estão em expansão, na internet este mesmo público também encontra dificuldades de acessar diversos websites por falta de um código bem elaborado ou estudado para cumprir as exigências de leitores de tela e navegadores textuais.

Poucos também são, os tutoriais que realmente exemplificam técnicas de acessibilidade e vários são os artigos que ainda insistem em atribuir a necessidade desta característica apenas à websites governamentais.
  
Ainda que você não tenha visto uma necessidade de elaborar projetos mais acessíveis, saiba que podemos utilizar as mesmas técnicas de acessibilidade para [aplicar técnicas de SEO][1] à seu código podendo também garantir um ganho de posições nos resultados de busca.

Então, para colaborar com um público pouco levado em consideração na elaboração de projetos web e ainda de priorizar a “conversa” entre seu código e mecanismos de busca, vamos às dicas para tornar seu website mais acessível.

Nas primeiras linhas de sua página já teremos as primeiras definições.
  
Iniciamos os códigos html nos “comunicando” com o navegador e &#8220;dizendo&#8221; que tipo de documento será lido e como ele deve ser validado:

<pre lang="html" line="1"></pre>

Na segunda linha do código atribuímos o idioma do website e esta informação é de suma importância para que o leitor utilize o dicionário correto ao sintetizar as palavras. Utilizamos tanto a tag **xml:lang** quanto apenas **lang**, devido as diferentes versões de navegadores:

<pre lang="html" line="1">&lt;html xmlns="http://www.w3.org/1999/xhtml" <strong>xml:lang="pt-br" lang="pt-br”</strong>&gt;</pre>

Depois da tag de abertura _<head>_, temos a primeira linha de declaração _<meta>_ onde também é importante declarar a códificação utilizada para o conteúdo do website. Normalmente, sites em português, utilizam a codificação **ISO-8859-1**:

<pre lang="html" line="1">&lt;meta http-equiv="Content-Type" content="text/html; <strong>charset=ISO-8859-1"</strong> /&gt;</pre>

Assim como nas técnicas de SEO, a tag _<title>_ que atribui título à página, também é de igual importância para as técnicas de Acessibilidade. Devido à este fato, temos o primeiro embate entre elas &#8211; uma preza por palavras-chave que garantem um melhor page-rank e outra preza pela leitura mais clara do nome e objetivo de um website acessados por navegadores textuais e leitores de tela. A dica é: procure elaborar todos os textos, que serão interpretados por sintetizadores e mecanismos de busca, unindo essas técnicas. No caso da tag _title_ procure escrever um título claro e coerente sem excluir as palavras-chave. Por exemplo:

<pre lang="html" line="1"><title>
  Como tornar seu website acessível? | Boas práticas de Desenvolvimento com Padrões Web
</title></pre>

Percebe? Está claro o título da página e não deixamos de usar palavras-chave que vão referenciar o site nos resultados de busca.

Outro atributo bastante importante a ser utilizado é o atributo _rel_ na tag _link_. Quando linkamos arquivos externos à nossa página é importante para os navegadores textuais que determinemos que tipo de arquivo ou página externa está sendo linkada. Este atributo tem valor pré-definido e o mais usado é: _stylesheet_. De qualquer forma, a lista prevê conteúdos (content), páginas anteriores (prev) e páginas posteriores (next). Pensando nas técnicas de SEO, caso você não saiba atribuir o conteúdo a ser linkado, é aconselhável que você utilize o valor “nofollow”, que fará com que mecanismos de buscas o ignorem e não saiam da linha geral de leitura da página. Exemplo:

<pre lang="html" line="1"></pre>

Continuando o código, no _<body>_ de seu site, várias precauções devem ser igualmente tomadas. Os atributos _alt_ e _longdesc_ na tag _<img>_ devem ser preenchidos com textos intuitivos tanto para a falta de carregamento da imagem (no caso de um cuidado na usabilidade do website &#8211; <a href="http://tableless.com.br/usabilidade-para-desenvolvedores-front-end" target="_blank">vide Usabilidade para desenvolvedores front-end &#8211; pela Talita Pagani</a>), quanto no caso dos navegadores textuais e leitores de tela. Lembrando que _longdesc_ não tem suporte em todos os navegadores e é mais utilizado para leitores de tela. O ideal é utilizar os dois atributos:

<pre lang="html" line="1"><img src="images/1.jpg" alt="Imagem teste" longdesc="Imagem inserida  para  teste de atributos longdesc na tag img do html" /></pre>

Para hyperlinks, tag _<a>_, a dica é utilizar o atributo _<title>_, com textos claros que exemplifiquem o destino do usuário ao clicar no link e não apenas com a descrição “clique aqui”. Além deste, outros dois atributos bastante valiosos para esta tag, são _tabindex_ e _accesskey_. A primeira permite que seja atribuída a ordem a qual a tecla _tab_ acessará o referido link e a segunda atribui uma tecla de atalho para o mesmo. Exemplo:

<pre lang="html" line="1"><ul>
  <li>
    <a href="index.html">PÁGINA INICIAL</a>
  </li>
  
</ul></pre>

Por fim, para que o deficiente visual não gaste muito tempo ouvindo, através do leitor de tela, todas as linhas de código que seus scripts tem, aconselha-se o uso da tag _<noscript>_ para descrever o objetivo do script na página. Por exemplo:

<pre lang="html" line="1"><!--mce:0-->
Funções para auxílio de animações do portal da ANEEL</pre>

Quer saber mais detalhes sobre Acessibilidade na Web? Abaixo 3 links que podem te ajudar nesta pesquisa.

A avaliação de acessibilidade de seu site pode ser feita pela URL: <a href="http://www.dasilva.org.br/" target="_blank">http://www.dasilva.org.br/</a>.
  
A documentação da W3C, para acessibilidade, pode ser adquirida neste link: <a href="http://www.w3.org/WAI/" target="_blank">http://www.w3.org/WAI/</a>
  
Para visualizar seu site em um navegador textual, acesse: <a href="http://www.delorie.com/web/lynxview.html" target="_blank">http://www.delorie.com/web/lynxview.html</a>

Com o HTML5 algumas dessas técnicas devem ser extintas, porque muitas das tags já estão sendo preparadas para ter um valor especialmente elaborado para cumprir requisitos de usabilidade, acessibilidade e SEO. Porém, enquanto a documentação se mantém em fase de formulação, vamos tornando acessíveis os sites que estão hoje na internet, mas ainda dificultam muito a vida deste público também inserido ao mundo virtual.

 [1]: http://tableless.com.br/seo-iniciantes-basico "SEO para iniciantes"