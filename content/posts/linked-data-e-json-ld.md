---
title: Linked Data e JSON-LD
author: Diego Eis
type: post
date: 2016-07-20
url: /linked-data-e-json-ld/
titulo_personalizado:
  - 'Linked Data e dados estruturados e <strong>JSON-LD</strong>'
categories:
  - Destaques
tags:
  - json
  - Semântica

---
Antes de entrarmos em como esse negócio de JSON-LD e Linked Data, queria falar um pouco sobre como a internet funciona. [Organização da Informação][1] na web é um dos assuntos que mais me fascinam no mundo da internet. Inclusive quando falamos sobre semântica e organização da informação de forma que não apenas humanos, mas computadores possam publicar e reutilizar essa informação livremente na web.

Hoje a internet é baseada basicamente em código HTML, onde nós podemos mostrar imagens, vídeos, audios e principalmente textos. Os links são o meio pelo qual nós organizamos toda a informação na internet, referenciando informações de um site para outro. Os links organizam, de certa forma, todos os websites da internet, sempre cruzando um termo com uma fonte de informação relacionada àquele termo.

Nós podemos quebrar a internet em duas partes específicas: nós temos a parte onde nós enxergamos, que basicamente é baseada em HTML, CSS e JS. É onde seres humanos interagem com nosso produto e nosso site.
  
Há também a segunda parte, que é formada basicamente por robôs e sistemas que também interagem com nossos produtos e sites, mas de forma diferente dos humanos, claro, consumindo dados que disponibilizamos de várias formas. Uma desses formatos é o JSON. Como alguns outros formatos, o JSON tem uma estrutura que é simples de ser lida por humanos e principalmente por robôs.

Linked Data é um termo relativamente novo. É um termo que apresenta um caminho para publicar dados interconectados entre diferentes sites, possibilitando que um site referencie e reutilize dados de um outro site. Tipo, um buscador, reutilizando as informações do seu site para mostrar nos resultados da busca.

Conectar as informações usando links resolve a parte de como os seres humanos conseguem relacionar um site (ou um punhado de informação), com outro. Mas como conseguimos fazer com que as máquinas entendam esse relacionamento? Você, como ser humano (eu espero que você seja um), consegue saber quando um site sobre um determinado assunto contém um link que leva para um site de um assunto completamente diferente, mudando de contexto. Mas as máquinas não conseguem fazer essa distinção. Para a máquina, um link sempre vai ser um link. Se é sobre feijão ou sobre automóveis, um link será um link, mesmo tendo uma mudança de contexto entre os assuntos. Para conseguir relacionar melhor as informações, precisamos indicar melhor para as máquinas o contexto dessa informação, ou melhor, desses dados (informação e dados são coisas diferentes).

Você já deve ter ouvido falar sobre RDFa. RDFa é um padrão básico para que possamos dar um pouco mais de contexto para as máquinas sobre os dados que elas estão consumindo. RDFa nada mais é do que um conjunto de atributos que colocamos em linguagens de marcação (HTML, XHTML, XML etc), de forma que as máquinas consigam entender que tipo de informação elas estão lidando. Algo como isso:

<pre class="lang-html">&lt;h1 property="dc:title"&gt;Um artigo sobre Semântica&lt;/h1&gt;
&lt;span property="dc:author"&gt;Diego Eis&lt;/span&gt;
</pre>

Sim. Você já viu algo parecido quando estudou sobre Microformatos, [Micro Data][2] e etc, que são modelos de dados muito mais amigáveis e inteligente do RDF/XML. Mas esse foi um dos primeiros modelos adotados pelo [W3C há muito tempo][3] e por isso, talvez, só talvez, valha a pena você dar uma lida para entender o conceito.

Deixando isso de lado, o que quero dizer é que nós marcamos esse tipo de informação, para que buscadores, redes sociais e qualquer outro tipo de sistema que precise de dados para funcionar, possa consumir os dados de forma mais inteligente. Então, enquanto as pessoas consomem HTML, lendo seus textos, vendo suas imagens e assistindo seus vídeos, as máquinas consomem esses dados vasculhando seu código procurando por algum significado.

## O JSON-LD e o @context

Mas nós não conseguimos resolver de verdade como as máquinas consomem esses dados. Como eu disse, as máquinas precisam de mais detalhes sobre os dados que publicamos. Eu fiz uma apresentação falando sobre como melhoramos a semântica do código usando as [novas tags do HTML5 e microdata][4]. Mas temos como melhorar isso, usando JSON-LD.

Quando um sistema acessar seu site, ele vai receber um arquivo JSON, que contém informações sobre o assunto do seu site. O formato é praticamente idêntico ao JSON que você já deve conhecer, mas com alguns valores e chaves diferentes, veja:

<pre class="lang-js">{
  "@context": "http://json-ld.org/contexts/person.jsonld",
  "@id": "http://dbpedia.org/page/Bob_Dylan",
  "name": "Bob Dylan",
  "born": "1941-05-24",
  "spouse": "http://dbpedia.org/resource/Sara_Dylan"
}
</pre>

O problema é quando você começa a receber esses dados de múltiplos websites. Todos eles oferecem dados como esse. Mas e se dois sites colocarem informações iguais em alguns valores? Por exemplo, um site fornece o seguinte dado:

<pre class="lang-js">{
  "name": "Diego",
  "homepage": "http://diegoeis.com"
}
</pre>

E o outro:

<pre class="lang-js">{
  "name": "diegoeis",
  "homepage": "http://diegoeis.com"
}
</pre>

Perceba que no primeiro exemplo, estamos falando sobre uma pessoa. Já no segundo exemplo, em vez do nome de alguém, está algo parecido com um nickname. O robô não tem como saber o que é cada coisa. É por isso que no JSON-LD tem um conceito chamado **@context**. O **@context** diz para a aplicação como interpretar o contexto daquelas informações. Perceba que sempre que você conversa com alguém na vida real, a conversa acontece em volta de um contexto. O exemplo legal ficaria assim:

<pre class="lang-js">{
  "@context": "http://json-ld.org/contexts/person.jsonld",
  "name": "Diego",
  "homepage": "http://diegoeis.com"
}
</pre>

### Mas e o Schema.org?

Ahh! Sabia que ia rolar essa pergunta. O [Schema.org][5] é uma comunidade colaborativa, formada por buscadores como Google e Yahoo! para criar, manter e promover formatos de dados estruturados para a internet, ajudando a estruturar dados para emails, páginas, sistemas etc.

  * O que é um vocabulário: imagina que você tem uma série de coisas para descrever para as máquinas, por exemplo: suponha um site sobre filmes. Você quer indicar para os sistemas de busca (ou qualquer outro tipo de sistema interessado), qual é o pedaço de texto na página que é a resenha do filme, qual imagem é o poster do filme etc. Você marcaria o HTML assim:

<pre class="htlang-ml">&lt;div itemscope itemtype="http://schema.org/Movie"&gt;
  &lt;a itemprop="url" href="http://www.warnerbros.com/matrix"&gt;&lt;div itemprop="name"&gt;&lt;strong&gt;Matrix&lt;/strong&gt;&lt;/div&gt;&lt;/a&gt;
  
  &lt;div itemprop="description"&gt;The best movie in the real world.&lt;/div&gt;
  
  &lt;div itemprop="director" itemscope itemtype="http://schema.org/Person"&gt;
    Directed by: &lt;span itemprop="name"&gt;The Wachowskis&lt;/span&gt;
  &lt;/div&gt;
  
  &lt;div&gt;Starring: 
    &lt;div itemprop="actors" itemscope itemtype="http://schema.org/Person"&gt;
      &lt;span itemprop="name"&gt;Laurence Fishburne&lt;/span&gt;
    &lt;/div&gt;
    &lt;div itemprop="actors" itemscope itemtype="http://schema.org/Person"&gt;
      &lt;span itemprop="name"&gt;Keanu Reeves&lt;/span&gt;
    &lt;/div&gt;
  &lt;/div&gt;

&lt;/div&gt;
</pre>

Perceba que então, o Google, por exemplo, consegue saber o que é cada pedaço de dado da página. Assim ele consegue classificar melhor a informação.

A ideia é o seguinte, o **@context** serve para que você consiga especificar o vocabulário dos tipos e propriedades que você está servindo no seu documento. Ali no exemplo, eu usei o vocabulário que o próprio pessoal do JSON-LD publicou. Mas o Google, assim como outros sistemas de busca, apoiam largamente o uso do Schema.org, que é um padrão de vocabulário. Fica assim:

<pre class="lang-js">{
  "@context": "http://schema.org",
  "@type": "Person",
  "name": "Diego",
  "homepage": "http://diegoeis.com"
}
</pre>

Veja ali que a segunda chave é o tipo. O Schema.org fornece uma série de vocabulários, logo, preciso dizer qual é o tipo do vocabulário que eu estou me referindo.

Perceba que **@context** e o **@type** definem o “significado” das outras chaves. Se fosse uma empresa:

<pre class="lang-js">{
  “@context”: “http://schema.org/“,
  “@type”: “Organization”,
  “name”: “National Public Radio”
}
</pre>

A chave **name** ali agora se refere ao nome de uma Organização e não de uma pessoa. E assim segue com outras “coisas”.

## E o Microdata?

Bom, se você usar o JSON-LD, você não precisa usar Microdata. O Google está investindo pesando com o JSON-LD, por isso, acho que você devia pensar em usá-lo. Outra coisa: para usar Microdata, você vai precisar mexer no seu código HTML para inserir os atributos necessários. Já com o JSON-LD isso não é necessário, já que você serve via JSON as partes necessárias das informações que você quer publicar.

## Identificadores Globais do JSON-LTD

Mas não adianta usar uma terminologia curta, que máquinas e humanos entendam, contendo um contexto, se você ainda não consegue identificar exatamente qual o assunto da conversa. No exemplo acima, o assunto era uma pessoa chamada **Diego**. Mas qual **Diego**? Existem milhares deles por aí. Para fazer isso, o JSON-LD usa uma **@id** para identificar globalmente esse assunto (que pode ser um animal, uma pessoa, um objeto etc).

Logo, se alguém quiser falar sobre o **Diego**, basta referenciar esse id específico.

<pre class="lang-js">{
  “@context”: “http://json-ld.org/contexts/person.jsonld”,
  “@id”: “http://diegoeis.com/sobre”
  “name”: “Diego”,
  “homepage”: “http://diegoeis.com”
}
</pre>

Logo, existem três coisas principais que precisamos entender sobre o JSON-LD. 

  1. Ele te dá um contexto para a informação.
  2. Ele usa uma terminologia e uma estrutura fácil para máquinas e humanos.
  3. Ele identifica o assunto para resolver a ambiguidade de informações.

## Como eu sirvo o JSON-LD

Simples: basta chamar na sua página o JSON com as informações que você quer publicar. Veja abaixo um exemplo:

<pre class="lang-js">&lt;script type=“application/ld+json”&gt; 
{ 
  “@context” : “http://schema.org”, 
  “@type” : “Article”, 
  “name” : “Um pouco sobre imagens para Web”, 
  “author” : { “@type” : “Person”, 
  “name” : “por Diego Eis” }, 
  “datePublished” : “2016-07-05”, 
  “image” : “http://tableless.com.br/uploads/2016/07/image-format.jpg”, 
  “articleBody” : “Queria falar um pouco sobre alguns formatos de imagens que usamos todos os dias. Dar algumas informações que encontrei por aí. Vamos explorar as duas principais opções de formato gráfico que pode ser usado na Web para representar gráficos simples,  esquemas ou logotipos. Embora hoje possamos usar SVG em diversos momentos,  principalmente para ícones ou Logos, o PNG e o GIF ainda podem ser usadas. Depois falamos mais sobre o SVG.&lt;/P&gt;\n&lt;H3&gt;GIF&lt;/H3&gt;\n&lt;P&gt;GIF (sigla para Graphics Interchange Format) foi desenvolvido no final dos anos 1980 e ainda é amplamente utilizado. PNG (Portable Network Graphics) foi desenvolvido por volta de 1995, tornou-se uma recomendação W3C em 1996, e tem sido amplamente implementado na maioria dos navegadores da Web, logo em 1998.&lt;/P&gt;&lt;/p&gt;}
&lt;/script&gt;
</pre>

O Google tem uma ferramenta sensacional que te ajuda a criar marcação de dados estruturados direto na sua página. [Olha aqui][6]!

## Um pouco mais sobre Web Semântica

Essas coisas são as fundações do Linked Data. A Web Semântica é muito do que simplesmente organizar informação. Ela envolve também relacionar esses dados encontrados em diferentes pontos da internet, além de facilitar o consumo e a reutilização desses dados por máquinas e seres humanos.

O Tim Berners-Lee [fala sobre os quatro passos (ou regras)][7] para que os dados sejam interconectados na internet:

  1. Identificar as coisas com URIs. Se a forma de identificar os dados não usam o formato universal de símbolos de URI, nós não podemos chamar isso de Web Semântica.
  2. Usar URI pelo protocolo HTTP é totalmente aceitável pela web inteira. Existe uma tendência gigante da criação de novos esquemas de URI como LSIDs, XRIs etc, se baseando em algo totalmente novo, por fora do DNS, impossibilitando o consumo da informação via formato não popular.
  3. É necessário ter acesso à informação via URIs. Basicamente você precisa acessar uma URI e encontrar a informação ali, pronta para ser reutilizada.
  4. Usar links para relacionar dados pela web.

Veja as regras se baseiam em fundações fortes da web hoje. Talvez essas fundações mudem. Mas não vai ser fácil. Veja o trabalho que é fazer para implementar o HTTP/2. Por isso creio que essas regras valerão durante muito tempo e serão ainda nossa baliza para poder servir informação de forma livre pela internet.

### Para ler mais:

  * [Site oficial][8]
  * [JSON-LD and Why I Hate the Semantic Web][9]
  * [JSON-LD in Details][10]
  * [Vídeo em ingles sobre Linked Data][11]
  * [Repositório do JSON-LD no GitHub][12]
  * [Is RDF/XML Good For Anything?][13]

 [1]: http://diegoeis.com/organizando-a-informacao.html
 [2]: http://tableless.com.br/introducao-a-microdata-no-html5/
 [3]: https://www.w3.org/2001/sw/RDFCore/
 [4]: http://www.slideshare.net/diegoeis/a-verdadeira-semntica-do-html5
 [5]: http://schema.org/
 [6]: https://www.google.com/webmasters/markup-helper/u/0/
 [7]: https://www.w3.org/DesignIssues/LinkedData.html
 [8]: http://json-ld.org/
 [9]: http://manu.sporny.org/2014/json-ld-origins-2/
 [10]: https://thecustomizewindows.com/2014/08/json-ld-details/
 [11]: https://www.youtube.com/watch?v=4x_xzT5eF5Q
 [12]: https://github.com/json-ld/json-ld.org
 [13]: https://norman.walsh.name/2004/07/30/rdfxml