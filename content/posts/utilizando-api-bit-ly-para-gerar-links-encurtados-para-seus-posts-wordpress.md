---
title: Utilizando a API do bit.ly para gerar links encurtados para seus posts WordPress
author: Léo Juoli
type: post
date: 2015-07-29
url: /utilizando-api-bit-ly-para-gerar-links-encurtados-para-seus-posts-wordpress/
categories:
  - CMS
  - Geral
  - PHP
  - Wordpress
tags:
  - bit.ly
  - permalinks
  - php
  - temas em wordpress
  - Wordpress

---
Todo mundo sabe que é fundamental criar links de compartilhamento no seu artigo, só que no Twitter isso se restringe a 140 caracteres, e ao enviar o título do seu artigo, URL e seu usuário no Twitter pode faltar espaço. E para economizar espaço fazemos o quê? Uma das táticas é utilizar links curtos através de serviços como o [bit.ly][1]. Como tudo na programação, criamos uma maneira de automatizar nossas ações e para isso vamos ao código!

Primeiramente precisamos entender como a API do bit.ly funciona. Podemos fazer uma requisição via URL e a mesma nos retornará um arquivo XML:

http://api.bit.ly/shorten?version=**[VERSÃO]**&longUrl=**[URL]**&login=**[LOGIN]**&apiKey=**[API]**&format=**[FORMATO]**

**[VERSÃO]** &#8211; A versão do XML

**[URL]** &#8211; A URL a ser encurtada

**[LOGIN]** &#8211; Seu login no bit.ly

**[API]** &#8211; Seu código de API no bit.ly

**[FORMATO]** &#8211; O formato de retorno (no nosso caso vamos usar XML)

Basta substituir os dados pelos seus e a requisição retornará um arquivo XML com as informações que precisamos. Veja um exemplo:

<img class="alignnone wp-image-50423 size-full" src="http://tableless.com.br/uploads/2015/07/XML2.png" alt="" width="879" height="288" />

Bom, visto isso vamos aos códigos! Primeiramente criaremos uma função no **functions.php** do seu tema, substituindo LOGIN e API por seus respectivos dados:

<pre>function make_bitly_url($url,$format = 'xml',$version = '2.0.1')
{
  //Set up account info
  $bitly_login = 'LOGIN';
  $bitly_api = 'API';
  //create the URL
  $bitly = 'http://api.bit.ly/shorten?version='.$version.'&longUrl='.urlencode($url).'&login='.$bitly_login.'&apiKey='.$bitly_api.'&format='.$format;
  $xml = simplexml_load_file($bitly) -&gt; results;
  foreach($xml -&gt; nodeKeyVal as $nodeKeyVal) {
    return (string)$nodeKeyVal -&gt; shortUrl;
  }
}</pre>

Vamos às explicações: o código acima é basicamente um leitor de XML, e informando os seus dados ele vai formar uma URL que vai fazer uma requisição ao serviço do bit.ly e retornar o **XML** que será lido pela função **simplexml_load** e armazenado como um vetor na variável** $xml**. Depois fazemos um loop com o **foreach** por todos os itens **nodeKeyVal** e retornamos a tag **shortUrl** para a função que vamos chamar depois. Repare que colocamos uma (string) antes de puxar o **$nodeKeyVal -> shortUrl**; isso é pra transformá-la em um valor retornável.

Como quase toda API, a do bit.ly tem limitação de requisições. Por isso precisamos armazenar as URLs encurtadas em nosso banco de dados. Vamos ao código de novo; dessa vez você vai colocar logo após iniciar o seu loop no **single.php**:

<pre>&lt;?php
global $short_url;
// Checar se ja existe um URL encurtado armazenado no banco de dados
if(get_post_meta($post-&gt;ID, "short_url", true) != ""){
  //Short URL already exists, pull from post meta
  $short_url = get_post_meta($post-&gt;ID, "short_url", true);
}
else {
  // Caso não tenha, vamos criar uma
  $full_url = get_permalink();
  $short_url = make_bitly_url($full_url);
  // Salvar no port_meta
  add_post_meta($post-&gt;ID, 'short_url', $short_url, true);
}
?&gt;</pre>

O código já está comentado mas vale explicar algumas coisas: usamos um condicional para checar se no nosso **post_meta** existe uma tag **short_url** diferente de um valor nulo; caso já exista ele vai pegá-la e armazenar na variável **$short_url**. Caso não exista, iremos criar uma chamando a função **make\_bitly\_url,** armazenando na variável **$short_url** e depois adicionando-a ao **post_meta.**

Pronto! Isso é quase o fim, agora só precisamos imprimir a variável **$short_url**. É importante dizer que se você tentar imprimi-la antes do código que cria a variável obviamente isso não vai dar certo. Basicamente a função abaixo deve ficar depois da função acima, veja:

<pre>&lt;?php echo $short_url; ?&gt;</pre>

Bom, agora você pode usar como quiser: imprimi-la no seu artigo, criar um botão de compartilhamento, etc. Recomendo que você, depois de testar, tente implementar outras APIs e ver o resultado. Caso dê algo errado, tente habilitar o error_reporting do PHP porque vai ajudar bastante você descobrir onde está o erro. Você pode usar os comentários para me perguntar algo, será um prazer responder.

 [1]: http://bit.ly