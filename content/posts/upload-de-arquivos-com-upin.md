---
title: Upload de Arquivos com a Upin
author: Gabriel Carvalho
type: post
date: 2016-11-12
excerpt: Criar sistemas de uploads pode ser uma tarefa não só complicado como também irritante. Temos que fazer diversas validações, entre elas, de tamanho, extensão do arquivo, etc. Pensando nisso foi criada uma biblioteca em PHP que inclui a função de uploads. Chama-se Upin.
url: /upload-de-arquivos-com-upin/
categories:
  - PHP
tags:
  - php
  - Uploads

---
A Upin é uma biblioteca para manipulação de arquivos em PHP Orientado a Objetos, que visa facilitar a vida de programadores iniciantes ou até profissionais. Afinal, tempo é dinheiro não é mesmo?

Para começar você deve baixar a versão mais atualizada da biblioteca [nesta página][1].

Após ter realizado o download da biblioteca copie a pasta `class` para dentro do diretório do seu projeto.

Agora, com os arquivos da biblioteca em seu projeto, você deverá criar um formulário de upload semelhante ao abaixo:

<pre class="lang-html">&lt;form action="upload.php" method="post" enctype="multipart/form-data"&gt;
 &lt;strong&gt;Envie uma foto:&lt;/strong&gt; &lt;input type="file" name="photos[]" /&gt;
 &lt;br /&gt;
 &lt;input type="submit" /&gt;
&lt;/form&gt;
</pre>

Algumas coisas na hora da criação do formulário são obrigatórias, são elas:

  * O atributo `enctype` cujo valor é `multipart/form-data` (<a href="http://www.w3schools.com/tags/att_form_enctype.asp" target="_blank">Leia sobre</a>)
  * No atributo name do `input file` é necessário dois couchettes ( `[]` ) após o nome.
  * E uma pequena observação: Para permitir múltiplos uploads você deve adicionar o atributo `multiple.`

Tendo as informações acima em mente, e criadas, vamos para o arquivo que você definiu no atributo `action` da sua tag `form` (no meu caso o arquivo **upload.php**).

<pre class="lang-php">&lt;?php
 require_once("class/Upload.class.php");
 #Instanciamos a classe Upload:
 $Upin = new Upload;
 
 $Upin-&gt;get(
  "imagens/", //Pasta de uploads (previamente criada)
  $_FILES["photos"]["name"], //Pega o nome dos arquivos, altere apenas "photos"
  10, //Tamanho máximo
  "jpeg,png,jpg,gif", //Extensões permitidas
  "photos", //Atributo name do input file
  1 //Mudar o nome? 1 = sim, 0 = não
 );
 $Upin-&gt;run();
 
 #Vamos usar o callback para mostrar as imagens enviadas.
 if($Upin-&gt;res == true){
  foreach($Upin-&gt;json as $arr){
    echo "&lt;img width=200 height=180 src='perfil/".$arr."' /&gt;";
  }
 }
</pre>

Imagine você, neste exato momento, criando um sistema de múltiplos uploads do zero. Bem chato, não? Então use e abuse da Upin!

 [1]: http://upin.scriptadores.com/download/