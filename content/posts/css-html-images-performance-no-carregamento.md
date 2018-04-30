---
title: CSS, HTML e Imagens  - Performance no carregamento
authors: Morais Junior
type: post
image: https://www.globaldots.com/wordpress/wp-content/uploads/2016/11/speed-analysis.jpg
date: 2018-04-29
excerpt: Neste artigo farei um apanhado de várias técnicas utilizadas :)
categories:
  - Browsers
  - CSS
  - HTML
tags:
  - Performance
  - CSS
  - HTML
---
Sabemos que performance é o principal ponto quando trabalhamos com WEB, porém esse assunto passa por vários tópicos, temos performance no carregamento, na renderização, no processamento e etc. Muito já foi dito sobre o assunto porém neste artigo farei um apanhado geral de várias técnicas amplamente utilizadas :)

# CSS

Quando falamos em arquivos CSS, temos um dos principais gargalos no carregamento de uma página, por dois pontos, um é a posição e o outro é o tamanho.

Na posição deve ter muito cuidado com os arquivos que estão sendo declarados dentro da tag head, essas chamadas bloqueiam a renderização dos elementos, fazendo com que o HTML só seja mostrado pelo navegador após o carregamento, por tanto deixe no head somente os CSS necessários, e nesses arquivos **SOMENTE** os seletores correspondentes para a primeira tela de visualização do usuário (normalmente os primeiros 1000px), todos os outros arquivos devem ir para o final do documento.

Para separar os seletores correspondentes ao carregamento mencionados, você pode utilizar as ferramentas  [Dust-Me Selectors](https://addons.mozilla.org/en-US/firefox/addon/dust-me-selectors/ "Dust-Me Selectors") e [CSS Stress Test](https://andy.edinborough.org/CSS-Stress-Testing-and-Performance-Profiling "CSS Stress Test")

O tamanho do arquivo é um ponto preocupante, para cada requisição temos uma janela http e o arquivo deve caber em uma única "viagem" nessa janela, por tanto, evite muitos arquivos pequenos assim como deve ser evitado arquivos grandes, agrupe os arquivos menores para que todos tenham a mesma média de tamanho (preferencialmente algo em torno de 14kb)

Limpe o arquivo CSS, para isso existem várias ferramentas, uma delas é o [CSS Compressor](https://csscompressor.com/ "CSS Compressor")

Habilite o Cache, Gzip e Deflate para a requisição nesses arquivos, para cada infraestrutura existe uma técnica diferente, uma boa alternativa é o [Gulp](https://gulpjs.com/ "Gulp"), mais a baixo colocarei um código em php que cuida desse processo, não entrarei em detalhes pois isso merece um artigo só para ele.


```php
<?php
//define cache
header('Expires: ' . gmdate( "D, d M Y H:i:s", time() + 31536000 ) . ' GMT');
header("Cache-Control: public, max-age=31536000");

///recebe o arquivo pelo ?file=arquivo.css
$file = explode("/", $_GET['file']);
$file = $file[count($file) -1];

$ext = explode(".", $_GET['file']);
$ext = $ext[count($ext) -1];

$out = file_get_contents($file);

$mimeTypes = array(
	'pdf' => 'application/pdf',
	'txt' => 'text/plain',
	'html' => 'text/html',
	'exe' => 'application/octet-stream',
	'zip' => 'application/zip',
	'doc' => 'application/msword',
	'xls' => 'application/vnd.ms-excel',
	'ppt' => 'application/vnd.ms-powerpoint',
	'gif' => 'image/gif',
	'png' => 'image/png',
	'jpeg' => 'image/jpg',
	'jpg' => 'image/jpg',
	'css' => 'text/css',
	'js' => 'application/x-javascript',
	'php' => 'text/plain'
);

header('Content-Type: ' . $mimeTypes[$ext]);

if ( !ini_get('zlib.output_compression') && 'ob_gzhandler' != ini_get('output_handler') && isset($_SERVER['HTTP_ACCEPT_ENCODING']) ) {
	header('Vary: Accept-Encoding');
	if ( false !== stripos($_SERVER['HTTP_ACCEPT_ENCODING'], 'deflate') && function_exists('gzdeflate')) {
		header('Content-Encoding: deflate');
		$out = gzdeflate( $out, 3 );
	} elseif ( false !== stripos($_SERVER['HTTP_ACCEPT_ENCODING'], 'gzip') && function_exists('gzencode') ) {
		header('Content-Encoding: gzip');
		$out = gzencode( $out, 3 );
	}
}

echo $out;
?>
```
Sempre que possivel utilize [CDN's](https://pt.wikipedia.org/wiki/Rede_de_fornecimento_de_conte%C3%BAdo "CDN's"), existem varias ferramentas para isso como [Cloudflare](https://www.cloudflare.com/br/cdn/ "Cloudflare"), [Amazon CloudFront](https://aws.amazon.com/pt/cloudfront/ "Amazon CloudFront"), entre outros.

#HTML
Assim como o css, mantenha o HTML limpo :)

Evite, css in-line, se o arquivo for muito grande divida o em partes, e retire os espaços desnecessários, abaixo vou passar um código em php que faz esta remoção porém também pode ser feita com o gulp.

```php
<?php
    ob_start();
	
	  ///seu código aqui
	
    $content = ob_get_contents();
    ob_end_clean();
  
    $content = preg_replace('/\s+/', ' ', $content); 
	echo $content;
?>
```
#Imagens
Para as imagens devemos ter outros cuidados além dos já descritos:

Utilize formatos que tenham o menor tamanho possível como [webp](https://pt.wikipedia.org/wiki/WebP "webp")

Comprima as imagens para retirar o tamanho desnecessário, para isso existem várias ferramentas porém a principal é o [TinyPNG](https://tinypng.com/ "TinyPNG"), com o Gulp você pode automatizar esse processo, em outra artigo falaremos somente sobre o Gulp, caso queira você pode utilizar o PHP, enviando a imagem para a API do TinyPNG e guardando o retorno já comprimido, segue um exemplo:

```php
<?php
//conprimindo no tiny
$key = "xxx"; //// sua chave para a api do tiny
if($ext = 'jpg') $ext = 'jpeg';
$f = 'imagem.jpg';

$result = fopen("https://api.tinify.com/shrink", "r", false, stream_context_create(array(
"http" => array(
"method" => "POST",
"header" => array(
"Content-type: image/".$ext,
"Authorization: Basic " . base64_encode("api:".$key)
),
"content" => file_get_contents($f)
),
"ssl" => array(
"cafile" => __DIR__ . "/cacert.pem",
"verify_peer" => true
)
)));			    

if ($result) {
foreach ($http_response_header as $header) { 
if (substr($header, 0, 10) === "Location: ") {
file_put_contents($f, fopen(substr($header, 10), "rb", false));
}
}
}
?>
```
# Ferramentas
Além de todas as recomendações citadas, é imprescindível que você teste sua página, para isso temos várias ferramentas: [PageSpeed Insights](https://developers.google.com/speed/pagespeed/insights/ "PageSpeed Insights"), [thinkwithgoogle](https://testmysite.thinkwithgoogle.com/intl/pt-br "thinkwithgoogle") e [WebPageTest](https://www.webpagetest.org/ "WebPageTest")
