---
title: Upload de arquivos com PHP
author: Lucas Caprio
type: post
date: 2014-07-01
excerpt: Aprenda a fazer o upload de arquivos com PHP e AJAX, utilizando WideImage e Jquery Form Plugin.
url: /upload-de-arquivos-com-php/
dsq_thread_id: 2803009875
categories:
  - Back-end
  - PHP
tags:
  - AJAX
  - php
  - upload

---
Neste artigo vamos aprender como fazer upload de arquivos com PHP. Porém, com alguns recursos adicionais em cada exemplo.

No primeiro exemplo, iremos fazer um upload básico de apenas um arquivo, assim conseguimos pegar o jeito da coisa.

No segundo exemplo, vamos fazer um upload de múltiplas imagens, e utilizaremos a classe WideImage para tratá-las (redimensionar, cortar e salvar).

E por fim, no último exemplo, vamos fazer o upload por AJAX, utilizando o Jquery Form Plugin.

## Upload Básico

Primeiro vamos fazer um upload clássico e rápido de apenas um arquivo. Por ser apenas um exemplo, resolvi escrever o código php na mesma página do HTML, para ficar de simples compreensão, por isso, na **action** do formulário temos #.

Um dos atributos que não podemos esquecer para fazer upload, é o que seta o **enctype** ao nosso formulário.

<pre>&lt;html&gt;
&lt;head&gt;
   &lt;title&gt;Basic Upload&lt;/title&gt;
&lt;/head&gt;
&lt;body&gt;
   &lt;form action="#" method="POST" enctype="multipart/form-data"&gt;
      &lt;input type="file" name="fileUpload"&gt;
      &lt;input type="submit" value="Enviar"&gt;
   &lt;/form&gt;
&lt;/body&gt;
&lt;/html&gt;

&lt;?php
   if(isset($_FILES['fileUpload']))
   {
      date_default_timezone_set("Brazil/East"); //Definindo timezone padrão

      $ext = strtolower(substr($_FILES['fileUpload']['name'],-4)); //Pegando extensão do arquivo
      $new_name = date("Y.m.d-H.i.s") . $ext; //Definindo um novo nome para o arquivo
      $dir = 'uploads/'; //Diretório para uploads

      move_uploaded_file($_FILES['fileUpload']['tmp_name'], $dir.$new_name); //Fazer upload do arquivo
   }
?&gt;
</pre>

Agora passamos ao código PHP, primeiro verificamos se o arquivo foi enviado através do **isset**. Se sim, seguimos para o upload do arquivo.
  
Primeiro definimos o timezone da aplicação, para podemos usar a função date sem problemas.

Como &#8220;boa prática&#8221; definimos uma variável com o ano, mês, dia, hora, minuto e segundo e concatenamos com a extensão do arquivo pega acima.
  
Para finalmente fazer o upload do arquivo, usamos a função **move\_uploaded\_file**, passando dois parâmetros, primeiro o nome temporário do arquivo armazenado pelo servidor, e o novo nome do arquivo, já com diretório padrão.

Se você deseja pegar alguma outra informação do arquivo, a variável $_FILES contém algumas outras informações que não são usadas no exemplo, como:

**$_FILES\[&#8216;fileUpload&#8217;\]\[&#8216;name&#8217;\]** O nome original do arquivo no computador do usuário
  
**$_FILES\[&#8216;fileUpload&#8217;\]\[&#8216;type&#8217;\]** O tipo mime do arquivo, se o browser deu esta informação (ex.: &#8220;image/gif&#8221;)
  
**$_FILES\[&#8216;fileUpload&#8217;\]\[&#8216;size&#8217;\]** O tamanho, em bytes, do arquivo
  
**$\_FILES\[&#8216;fileUpload&#8217;\]\[&#8216;tmp\_name&#8217;\]** O nome temporário do arquivo, como foi guardado no servidor
  
**$_FILES\[&#8216;fileUpload&#8217;\]\[&#8216;error&#8217;\]** O código de erro associado a este upload de arquivo (adicionado no PHP 4.2.0)

## Upload Múltiplo

Para o segundo exemplo faremos o upload de múltiplas imagens. Porém, nesse exemplo utilizaremos a classe <a href="http://wideimage.sourceforge.net/" title="WideImage" target="_blank">WideImage</a>, para tratarmos as imagens que foram enviadas.

O segredo do múltiplo upload é a adição do atributo **multiple** à tag do input type=&#8221;file&#8221; e adicionar **[ ]** ao name da tag.

<pre>&lt;html&gt;
&lt;head&gt;
   &lt;title&gt;Multiple Upload&lt;/title&gt;
&lt;/head&gt;
&lt;body&gt;
   &lt;form action="#" method="POST" enctype="multipart/form-data"&gt;
      &lt;input type="file" name="fileUpload[]" multiple&gt;
      &lt;input type="submit" value="Enviar"&gt;
   &lt;/form&gt;
&lt;/body&gt;
&lt;/html&gt;

&lt;?php
   if(isset($_FILES['fileUpload']))
   {
      require 'WideImage/WideImage.php'; //Inclui classe WideImage à página

      date_default_timezone_set("Brazil/East");

      $name 	= $_FILES['fileUpload']['name']; //Atribui uma array com os nomes dos arquivos à variável
      $tmp_name = $_FILES['fileUpload']['tmp_name']; //Atribui uma array com os nomes temporários dos arquivos à variável

      $allowedExts = array(".gif", ".jpeg", ".jpg", ".png", ".bmp"); //Extensões permitidas

      $dir = 'uploads/';

      for($i = 0; $i &lt; count($tmp_name); $i++) //passa por todos os arquivos
      {
         $ext = strtolower(substr($name[$i],-4));

         if(in_array($ext, $allowedExts)) //Pergunta se a extensão do arquivo, está presente no array das extensões permitidas
         {
            $new_name = date("Y.m.d-H.i.s") ."-". $i . $ext;

            $image = WideImage::load($tmp_name[$i]); //Carrega a imagem utilizando a WideImage

            $image = $image-&gt;resize(170, 180, 'outside'); //Redimensiona a imagem para 170 de largura e 180 de altura, mantendo sua proporção no máximo possível
            $image = $image-&gt;crop('center', 'center', 170, 180); //Corta a imagem do centro, forçando sua altura e largura

            $image-&gt;saveToFile($dir.$new_name); //Salva a imagem
         }
      }
   }
?&gt;
</pre>

O código PHP deste exemplo muda um pouco comparado ao primeiro. Como neste exemplo estamos utilizando a classe WideImage, temos que inclui-la ao projeto. Em seguida, colocamos todos os nomes de arquivos enviados dentro da variável $name e todos os nomes temporários dentro da variável $tmp_name.

Para fazer a consistência que iremos salvar apenas imagens, criei uma array de possíveis extensões para imagens. Logo adiante, passamos por cada arquivo dentro do for, e realizamos a pergunta se a extensão do arquivo que estou pegando no for se encontra no array de extensões permitidas, se sim, continuaremos para salva-la no servidor, mas antes, redimensiono a mesma com o WideImage (sem perder a proporção), e depois corto a mesma para ter imagens apenas com as dimensões que forcei.

## Upload com AJAX

Neste último exemplo, vamos utilizar o mesmo código PHP de cima para salvar as imagens, porém, com alguns truques HTML e utilizando o <a href="http://malsup.com/jquery/form/" title="Jquery Form Plugin" target="_blank">Jquery Form Plugin</a> para fazer o upload via AJAX.

Não repare na utilização de css inline, ou javascript incorporado ao exemplo, procurei o máximo de agilidade possível e foco no ajax.

<pre>&lt;html&gt;
&lt;head&gt;
   &lt;title&gt;Multiple Upload Ajax&lt;/title&gt;
&lt;/head&gt;
&lt;body&gt;
   &lt;form id="formImage" style="display:none"&gt;
      &lt;input type="file" id="fileUpload" name="fileUpload[]" multiple onchange="saveImages()"&gt;
   &lt;/form&gt;

   &lt;div id="btnFake" style="background:#CCC; width:100px; height:100px; cursor:pointer;"&gt;&lt;/div&gt;

   &lt;script src="//ajax.googleapis.com/ajax/libs/jquery/2.1.1/jquery.min.js"&gt;&lt;/script&gt;
   &lt;script src="//malsup.github.io/jquery.form.js"&gt;&lt;/script&gt;

   &lt;script&gt;
      document.getElementById('btnFake').addEventListener('click', function(){
         document.getElementById('fileUpload').click();
      });

      function saveImages()
      {
         $('#formImage').ajaxSubmit({
            url  : 'multiple-upload-ajax.php',
            type : 'POST'
         });
      }
   &lt;/script&gt;
&lt;/body&gt;
&lt;/html&gt;
</pre>

Criei um botão &#8220;personalizado&#8221; para não ficarmos com aquele padrão do input type=&#8221;file&#8221;, que é muito feio, e escondi o form todo porque não usamos ele para mais nada além de fazer upload de imagens. Porém, no javascript eu adiciono um evento de click ao meu **btnFake**, para quando clicarmos nele, o fileUpload ser clicado também, assim mascaramos o nosso botão de upload.

Na tag do input type=&#8221;file&#8221; adicionei um novo atributo, o de **onchange**, para assim que selecionados os arquivos que desejo fazer upload, eles sejam enviados ao servidor, sem a necessidade de previamente clicarmos em outro botão para apenas enviar.

A função saveImages ativa a função ajaxSubmit do plugin jquery form, enviando o formulário completo (no caso o de id **formImage**), para uma url especificada e com um método de envio do tipo POST.

Como disse mais acima, o código PHP é o mesmo do exemplo anterior:

<pre>&lt;?php
   if(isset($_FILES['fileUpload']))
   {
      require 'WideImage/WideImage.php';

      date_default_timezone_set("Brazil/East");

      $name 	= $_FILES['fileUpload']['name'];
      $tmp_name = $_FILES['fileUpload']['tmp_name'];

      $allowedExts = array(".gif", ".jpeg", ".jpg", ".png", ".bmp");

      $dir = 'uploads/';

      for($i = 0; $i &lt; count($tmp_name); $i++)
      {
         $ext = strtolower(substr($name[$i],-4));

         if(in_array($ext, $allowedExts))
         {
            $new_name = date("Y.m.d-H.i.s") ."-". $i . $ext;

            $image = WideImage::load($tmp_name[$i]);

            $image = $image-&gt;resize(170, 180, 'outside');
            $image = $image-&gt;crop('center', 'center', 170, 180);

            $image-&gt;saveToFile($dir.$new_name);
         }
      }
   }
?&gt;
</pre>

Bom, é isso aí pessoal. Apesar de ser algo simples, muitos quando começam a conhecer PHP tem dúvidas desse tipo.

Espero que todos consigam. Bons estudos!