---
title: Como schema pode te ajudar em SEO
author: Daniel Marcos
type: post
date: 2013-02-01
excerpt: Schema são tags padrões que foram adicionadas ao HTML afim de facilitar o entendimento de determinada informação pelos buscadores.
url: /como-schema-pode-te-ajudar-em-seo/
dsq_thread_id: 1059043609
categories:
  - Acessibilidade
  - HTML
tags:
  - 2013
  - html
  - schema
  - SEO

---
Já imaginou chegar em um corredor com 5 portas iguais, mas precisa decidir em qual delas é mais relevante. Qual critério usaria para decidir qual escolher ? Muitas vezes fazemos assim em nossos códigos quando colocamos no ar nossos sites. Por mais que os buscadores sejam capazes de identificar informações contidas no site, é possível deixar o trabalho deles ainda mais fácil usando schema.

Schema são tags padrões que foram adicionadas ao HTML afim de facilitar o entendimento de determinada informação pelos buscadores.

Existe schema para produtos, reviews, endereços e outras informações. Você utilizando o padrão de Schema correto para cada tipo de informação, facilita a leitura dos crawlers (robôs de busca) e consegue ainda criar o que chamamos de Rich Snippet (aqueles resultados do Google que tem rating de estrelas de review, por exemplo).

Neste [vídeo Matt Cutts][1] fala das diferentes formas que o Google faz para indentificar um conteúdo. Eu creio que em um futuro próximo seja a semântica que vai ditar as regras, e isso já começou desde o inicio da popularização do tableless. Precisamos encontrar formas de ajudar o Google indexar mais e melhor nosso site. E umas dessas forma sem dúvida é usando schema.

## Usando o schema

Para usar em seu conteúdo basta apenas fazer marcações no código onde passa ao buscador o que é exatamente determinada informação que está sendo exibida. EX: Digamos estamos em uma página de produto, veja como ficará a marcação.

<pre class="lang-html">&lt;!--// Iniciamos o bloco do c&oacute;digo informando qual tag iremos utilizar, neste caso &eacute; a Product--&gt;
&lt;div itemscope itemtype="http://schema.org/Product"&gt;

&lt;!--// Informamos a URL e o nome do produto--&gt;
&lt;a itemprop="url" href="www.url-sua-loja-online.com.br"&gt;

&lt;div itemprop="name"&gt;&lt;strong&gt;Tv Led 50 Polegadas&lt;/strong&gt;&lt;/div&gt;&lt;/a&gt;

&lt;!--// Inserimos a descri&ccedil;&atilde;o da nossa televis&atilde;o de exemplo--&gt;
&lt;div itemprop="description"&gt;Lorem Ipsum is simply dummy text of the printing and typesetting industry. Lorem Ipsum has been the industry's standard dummy text ever since the 1500s&lt;/div&gt;

&lt;!--// J&aacute; mudamos de tag, agora iremos usar a Organization--&gt;
&lt;div itemprop="brand" itemscope itemtype="http://schema.org/Organization"&gt;

&lt;span itemprop="name"&gt;Samsumg&lt;/span&gt;&lt;/div&gt;

&lt;div&gt;Product ID: &lt;span itemprop="productID"&gt;985&lt;/span&gt;&lt;/div&gt;

&lt;!--// Alteramos mais uma vez, desta vez iremos para AggregateRating--&gt;
&lt;div itemprop="aggregateRating" itemscope itemtype="http://schema.org/AggregateRating"&gt;

&lt;span itemprop="ratingValue"&gt;80&lt;/span&gt; based on &lt;span itemprop="reviewCount"&gt;125&lt;/span&gt; reviews&lt;/div&gt;

&lt;!--// E finalizamos com Offer e NewCondition--&gt;
&lt;div itemprop="offers" itemscope itemtype="http://schema.org/Offer"&gt;

&lt;span itemprop="price"&gt;236.63&lt;/span&gt;

&lt;link itemprop="itemCondition" href="http://schema.org/NewCondition" /&gt;New&lt;/div&gt;&lt;/div&gt;
</pre>

Não precisa ser páginas apenas de produtos, mas também um evento, filme ou pessoas. O que importa é que seu código vai ficar semanticamente organizado para quando o buscador chegar e identificar as informações contidas no conteúdo. Veja o exemplo como se fosse uma página falando de um filme.

<pre class="lang-html">&lt;div itemscope itemtype ="http://schema.org/Movie"&gt;

  &lt;h1 itemprop="name"&gt;Avatar&lt;/h1&gt;

  &lt;span&gt;Director: &lt;span itemprop="director"&gt;James Cameron&lt;/span&gt; (born August 16, 1954)&lt;/span&gt;

  &lt;span itemprop="genre"&gt;Science fiction&lt;/span&gt;

  &lt;a href="../movies/avatar-theatrical-trailer.html" itemprop="trailer"&gt;Trailer&lt;/a&gt;

&lt;/div&gt;
</pre>

## Obtendo informações e suporte

O Google disponibilizou um [artigo no suporte][2] com exemplos sobre o assunto e pode ser usado como referência e consultas de determinadas tags para suas páginas e ainda pode fazer a validação através da [ferramenta oficial do Google][3].

Você pode fazer o acompanhamento através do Google Web Master Tools no menu Otimização > Dados estruturados você terá as seguinte tela, onde terá todas as tag encontradas.

<img src="http://tableless.com.br/uploads/2013/02/image00.jpg" alt="image00" class="alignnone size-full wp-image-8102" srcset="uploads/2013/02/image00.jpg 480w, uploads/2013/02/image00-329x113.jpg 329w" sizes="(max-width: 480px) 100vw, 480px" />

É importante esse acompanhamento para identificar o que está dando resultado. O seu código organizado semânticamente não é um fator direto de melhor posicionamento, mas contribue muito para organizar as informações e fazendo as boas práticas de outras técnicas você pode ganhar bons resultados do Google

## Testar é preciso

Os testes são importantes para alcançar um bom resultado. Lembrando que é importante o acompanhamento da performance das páginas como velocidade de abertura, peso das imagens e atributos dos links. Para isso você pode usar a ferramenta do Google Page Speed. Procure entender o que a concorrência está fazendo e acompanhe o que dizem os profissionais de SEO. Uma boa forma de identificar resultados de testes é acompanhar os participantes do desafio de SEO que acontece em Janeiro e Fevereiro com o termo Eletrikus Brasiliensis. Estou participando com o blog [eletrikusbrasiliensis-site.com.br][4]. O desafio vai até dia 20 de fevereiro. É uma oportunidade de verificar quais técnicas está dando certo com mais forças que outras.

## Não é um fator de rankeamento direto

Outra coisa importante a ser observado. Quando usar schema em suas páginas, os seus resultado na **SERP do Google** não terá uma melhora por causa do código, mas é algo que chama tanta atenção que praticamente pede o nosso clique. E quanto mais pessoas clicarem no mesmo resultado, haverá uma melhora no posicionamento. Então é um fator que influência decisões de pessoas e o clique dessas pessoas influência no Google.

<img src="http://tableless.com.br/uploads/2013/02/image01.jpg" alt="image01" width="533" height="93" class="alignnone size-full wp-image-8103" srcset="uploads/2013/02/image01.jpg 533w, uploads/2013/02/image01-329x57.jpg 329w" sizes="(max-width: 533px) 100vw, 533px" />

Veja neste exemplo como é algo que chama atenção. Use isso ao seu favor!!

 [1]: http://www.youtube.com/watch?v=IZF13_4obbQ
 [2]: http://support.google.com/webmasters/bin/answer.py?hl=en&answer=146750&topic=1088474&ctx=topic
 [3]: http://www.google.com/webmasters/tools/richsnippets
 [4]: http://eletrikusbrasiliensis-site.com.br/