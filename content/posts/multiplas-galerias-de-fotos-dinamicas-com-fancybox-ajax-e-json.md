---
title: Múltiplas galerias de fotos dinâmicas com Fancybox, Ajax e JSON
author: pdechery
type: post
date: 2015-02-27
excerpt: Transferindo dados entre o PHP e Javascript do jeito certo.
url: /multiplas-galerias-de-fotos-dinamicas-com-fancybox-ajax-e-json/
categories:
  - AJAX
  - JavaScript
  - PHP
tags:
  - AJAX
  - fancybox
  - JavaScript
  - js
  - php

---
### Introdução

Ano passado trabalhei em um projeto que era um concurso de fotografia online, o <a href="http://www.prixphotoaliancafrancesa.com.br" target="_blank">Prix Photo Web</a>, onde cada fotógrafo podia se cadastrar, fazer upload de suas fotos e concorrer a um prêmio.

O site tinha uma página de galeria, onde se podia ver os diversos trabalhos publicados a partir de _thumbnails_.

Eu havia pego o código já quase todo pronto, mas resolvi atualizar algumas coisas e uma delas foi a tal galeria.

No decorrer do processo acabei tendo que usar o **JSON** para trocar informações entre scripts PHP e JavaScript, e achei muito interessante a maneira como isso aconteceu.

O resultado final pode ser conferido <a href="http://www.prixphotoaliancafrancesa.com.br/galeria" target="_blank">aqui</a>, e a seguir vou descrever o passo a passo do processo que percorri.

### Escopo

O conteúdo do site era totalmente dinâmico, ou seja, vinha de consultas ao banco de dados feitas no carregamento da página. Veja abaixo como ficou a página da galeria, com os _thumbnails_ clicáveis:

[<img class=" wp-image-43 size-large aligncenter" src="http://www.decheryweb.com.br/blog/uploads/galeria-prix-1-1024x550.png" alt="galeria-prix-1" width="660" height="354" />][1]

Ao dar o clique em um dos _thumbs_ se abria uma galeria de fotos em _lightbox_, usando o _plugin_ jQuery <a href="http://fancyapps.com/fancybox/" target="_blank"><em>fancybox</em> </a>(um velho favorito meu):

[<img class=" size-large wp-image-42 aligncenter" src="http://www.decheryweb.com.br/blog/uploads/galeria-prix-2-1024x550.png" alt="galeria-prix-2" width="660" height="354" />][2]

#### O problema

Eu já tinha toda a lógica para exibir os _thumbnails_ na página e também as galerias em _lightbox_, mas achei o código meio &#8216;macarrônico&#8217; e me questionei se não podia ser mais simples e limpo.

Para demonstrar o funcionamento do sistema existente de carregamento das galerias, segue um diagrama:

[<img class=" size-full wp-image-68 aligncenter" src="http://www.decheryweb.com.br/blog/uploads/diagrama-prix.png" alt="diagrama-prix" width="361" height="536" />][3]

Trata-se de um exemplo básico de uso de Ajax, aonde temos:

  1. **Página HTML**: Renderiza a galeria de _thumbnails_ e as galerias de fotos em _lightbox_.
  2. **Script JS**: Ativado a cada clique em um _thumbnail_, faz a requisição de um arquivo PHP através de _Ajax_.
  3. **Arquivo PHP**: Faz as consultas no banco de dados para pegar todas os dados necessários para exibição da galeria, e devolve estes dados ao script, que finalmente vai exibir a galeria, usando o plugin _fancybox_.

O sistema como um todo funcionava, mas faltava um toque de agilidade, que foi dado ao acrescentar o JSON no sistema.

Vamos então ver agora como isso foi feito.

### O código

O HTML da galeria era mais ou menos assim:

<pre class="lang-html">&lt;div class="projetos"&gt;
	&lt;a id="10"&gt;
		&lt;img src="dir/nome-img.jpg"&gt;
	&lt;/a&gt;
	&lt;a id="11"&gt;
		&lt;img src="dir/nome-img.jpg"&gt;
	&lt;/a&gt;
&lt;/div&gt;</pre>

E abaixo o código JS (usando jQuery) que fazia acontecer a mágica a cada clique nos _thumbnails_:

<pre class="lang-javascript">$(document).ready(function(){
	$('.projetos &gt; a').click(function(){
		var id = $(this).attr('id');
		$.post('ajax-projetos.php',{'idp':id}, function(data){
			fancyPrix(data);
		},'text');
	});
});</pre>

Observando o script, vemos que ele aplica algumas ações ao evento _click_ nos links, conforme indicado neste trecho: `$('.projetos > a').click(function(){`

As ações basicamente são: a requisição do arquivo `ajax-projetos.php` usando o método do jQuery $.`post` (método do jQuery para chamadas Ajax), passando como parâmetro a variável `id`, cujo valor vem de um atributo em cada link. O retorno dado pelo arquivo php, representado na variável `data`, era em seguida passado pela função `fancyPrix`.

Se ficou com dúvidas examine novamente o script até entender todo o processo.

### Usando o JSON

Agora que ficou claro (espero) o importante papel do script JS, vamos ao arquivo `ajax-projetos.php`. Como explicado no diagrama apresentado anteriormente, este arquivo fazia a consulta no banco de dados entregando ao final um _array_ contendo os dados necessários para a renderização da galeria de imagens em _lightbox_.

Ao final do processo, o array produzido tinha a seguinte estrutura:

<pre class="lang-javascript">$proj = array (
	"candidato" =&gt; "Felisbério dos Santos",
	"imgs"  =&gt; array ( 
		0 =&gt; "http://localhost/projeto/diretorio/nome-arquivo.jpg",
		1 =&gt; "http://localhost/projeto/diretorio/nome-arquivo.jpg",
		2 =&gt; "http://localhost/projeto/diretorio/nome-arquivo.jpg",
	),
	"projeto" =&gt; "Sombras Negras"
);</pre>

Como se pode ver, o _array_ tinha todos os dados necessários para criação da galeria: nome do candidato, nome do projeto e as imagens, como um _sub-array_.

No código original, a grande falha no entanto era a forma como esses dados eram devolvidos ao script JS. Havia uma mistura de código JS como variáveis do php dentro do mesmo script que tornava tudo confuso e difícil de manter.

Porque não passar o _array_ de volta como um objeto **JSON**, que pode ser interpretado dentro do script JS original, abolindo assim o uso de código php macarrônico?

Isto foi feito simplesmente adicionando-se ao código esta linha:

<pre class="lang-php">echo json_encode($proj);</pre>

A função nativa do PHP &#8216;<a href="http://php.net/manual/pt_BR/function.json-encode.php" target="_blank">json_encode</a>&#8216;, como diz o nome, converte o _array_ `$proj` para um objeto JSON, que ficará assim:

<pre class="lang-javascript">{
	"candidato":"Felisbério dos Santos",
	"imgs":[
		"http://path/da/imagem/136/000-1.jpg",
		"http://path/da/imagem/136/000-2.jpg",
		"http://path/da/imagem/136/000-3.jpg"
		],
	"nome":"Sombras Negras"
 }</pre>

Este objeto pode ser passado tranquilamente pela script JS, aonde será usado na já citada função `fancyPrix()`, que é quem vai pegar cada informação do objeto JSON e aplicar no _plugin <a href="http://fancyapps.com/fancybox/" target="_blank">fancybox</a>_, da seguinte maneira:

<pre class="lang-javascript">function fancyPrix(projeto) {
	$.fancybox.open(projeto.imgs, {
		padding: 0,
		maxWidth : '680px',
		maxHeight : '660px',
		title: projeto.nome + " - "+ projeto.candidato,
		loop : 'false',
		prevEffect : 'none',
		nextEffect : 'none'
	});
}</pre>

Vemos que o plugin _fancybox_ possui um método que permite trabalhar com objetos JSON, o `fancybox.open`.

Repare como foram passadas as imagens logo no início do código: `$.fancybox.open(projeto.imgs, {`. Com a simples propriedade `projeto.imgs` conseguimos passar **todas** as imagens que fazem parte da galeria. O restante das propriedades são usadas como opções dentro do plugin, como mostrado acima.

Relembrando o script jQuery original podemos ver como a galeria toda é criada em apenas uma linha de código.

<pre class="lang-javascript">$(document).ready(function(){
	$('.projetos a').click(function(){
		var id = $(this).attr('id');
		$.post('ajax-projetos.php',{'idp':id}, function(data){
			<strong>fancyPrix(data);</strong>
		},'text');
	});
});</pre>

### Conclusão

Quando apliquei esta solução e vi tudo funcionando o orgulho (e o alívio) foram grandes, mas maior ainda foi a sensação de &#8216;uau&#8217; ao ver as diferentes linguagens da web conversando juntas e de maneira tão integrada.

 [1]: http://www.decheryweb.com.br/blog/uploads/galeria-prix-1.png
 [2]: http://www.decheryweb.com.br/blog/uploads/galeria-prix-2.png
 [3]: http://www.decheryweb.com.br/blog/uploads/diagrama-prix.png