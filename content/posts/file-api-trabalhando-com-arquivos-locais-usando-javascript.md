---
title: File API – Trabalhando com Arquivos Locais Usando Javascript
author: Bruno Ruiz
type: post
date: 2014-04-08
excerpt: Trabalhar com arquivos no lado do cliente antes do HTML5 era dificultoso e e tinha pouco suporte. Com o File API, agora é possível capturar informações e ler o conteúdo de arquivos usando apenas o navegador por meio do javascript.
url: /file-api-trabalhando-com-arquivos-locais-usando-javascript/
dsq_thread_id: 2594877912
categories:
  - HTML
  - HTML5
  - JavaScript
tags:
  - boas praticas
  - JavaScript
  - loca files

---
A atividade exercida localmente para a leitura de arquivos fornecidos pelo cliente na web sempre foi a de selecionar o arquivo e enviá-los ao servidor para que este possa, de alguma forma, fazer a leitura e retornar os dados de leitura para o cliente. Esta é a prática usual. Mas o HTML5 veio com suas API para desmistificar o usual.

A File API desmitifica a prática de enviar um arquivo para o servidor para que ele possa ser lido. Sim, você pode ler arquivos no navegador, usando a capacidade processamento do cliente, e liberando seu servidor para executar atividades que somente ele possa executar.

Mas, afinal, como funciona esta tal de File API? Bem, ela provê um padrão para executar as seguintes atividades:

  * Selecionar arquivos ou uma lista de arquivos;
  * Ler alguns atributos dos arquivos selecionados, e;
  * Ler o conteúdo dos arquivos selecionados.

Bem, mas você pode estar imaginando que agora é possível criar uma aplicação que irá, ao ser carregado no navegador, fazer a leitura de arquivos do usuário  fazendo aquilo para o qual foi construído. Infelizmente não, mas felizmente no que se diz respeito a segurança. Você só poderá manipular arquivos locais que o usuário prover acesso conscientemente, única e exclusivamente por este meio.

### Selecionar Arquivos e Ler Seus Atributos

Para selecionarmos um arquivo podemos criar um elemento _input_ com a propriedade _type_ igual a _file. _Com isto o usuário poderá escolher o arquivo que será selecionado. Vamos exibir os atributos do arquivo selecionado em um parágrafo.

<pre class="lang-html"> &lt;input id="inputFile" type="file"&gt;
 &lt;p id="atributos"&gt;&lt;/p&gt;</pre>

Agora que podemos selecionar o arquivo, vamos pegar alguns atributos. É possível pegar os  seguintes atributos do arquivo selecionado: nome, tipo de arquivo e tamanho do arquivo. Como fazer isto? Veja abaixo:

<pre class="javascript">function pegarArquivo(arquivoSelecionado) {
	if(arquivoSelecionado.files){
	   var file = arquivoSelecionado.files[0];
	   document.getElementById('atributos').innerHTML =
                             '  nome do arquivo: '+file.name +
                             ';  tipo do arquivo: '+file.type +
                             ';  tamanho do arquivo: '+file.size + ' bytes'
				   }   
                                          }</pre>

O que estamos fazendo acima é pegar o arquivo selecionado no elemento _input_, verificar se tem algum arquivo selecionado e pegar os atributos de nome, tipo e  tamanho do arquivo no índice zero. Em seguida estes são exibidos no parágrafo com o _id_ atributos.

É claro que pegar as propriedades de um arquivo pode ser útil para muitas atividades. Mas o que mais impressiona na File API é possibilidade de leitura do conteúdo de arquivos. Vamos ver como isto é possível?

### FileReader

É possível ler arquivos na memória do cliente por meio de uma interface da File API chamada FileReader. A FileReader fornece métodos, atributos e eventos que permitem a leitura de arquivos de forma assíncrona.

<pre class="lang-html">&lt;input id="inputImage" type="file" onchange="pegaArquivo(this.files)"&gt;
&lt;div id="imgLocal"&gt;&lt;/div&gt;</pre>

Os elementos acima possibilitam a seleção de uma imagem para carregamento no navegador. Posteriormente as imagens serão exibidas na _div_ mostrada acima.

O script para carregar a imagem selecionada e exibi-la para o usuário, utiliza o método onload do objeto FileReader , conforme mostra o código abaixo:

<pre class="javascript">function pegaArquivo(files){
    var imgLoca = document.getElementById('imgLocal')
    var file = files[0];
    var img = document.createElement("img");
        img.file = file;

        imgLocal.appendChild(img)

    var reader = new FileReader();
        reader.onload = (function(aImg) {return function(e) {aImg.src = e.target.result;};})(img);
        reader.readAsDataURL(file);
}</pre>

Primeiro, nós lemos os atributos de um arquivo, agora nós carregamos um arquivo de imagem. Mas na verdade o que eu quero mostrar para vocês é a capacidade de leitura de um arquivo csv. Um arquivo do tipo csv pode conter dados, que quando carregados, possibilita a geração de tabelas, gráficos e todas as formas de exibição de dados possíveis. Novamente digo que isto poderia ser feito pelo servidor, mas não queremos consumir ciclos do servidor desnecessariamente.

<pre class="lang-html">&lt;input type="file" id="inputCSV" onchange="pegaCSV(this)"&gt;
&lt;div id="CSVsaida"&gt;&lt;/div&gt;</pre>

Acima nós criamos uma tag input com type file para carregarmos o nosso arquivo csv. No evento onchage estamos executando uma função que irá fazer a mágica para nós. Em seguida temo uma tag onde serão exibidos os dados do csv após carregado.

<pre class="javascript">var leitorDeCSV = new FileReader()
window.onload = function init() {
    leitorDeCSV.onload = leCSV;
}</pre>

Acima nós criamos uma variável do tipo FileReader logo na sequência atribuímos a função leCSV ao evento de onload. Sendo assim, no momento em que o arquivo csv for carregado ele disparará a função leCSV.

<pre class="javascript">function pegaCSV(inputFile) {
     var file = inputFile.files[0];
     leitorDeCSV.readAsText(file);
}</pre>

Agora nós contruímos a função que será executada para selecionar o arquivo csv.

<pre class="javascript">function leCSV(evt) {

  var fileArr = evt.target.result.split('\n');
  var strDiv = '&lt;table&gt;';

  for (var i=0; i&lt;fileArr.length; i++) {
       strDiv += '&lt;tr&gt;';
       var fileLine = fileArr[i].split(',');
           for (var j=0; j&lt;fileLine.length; j++) {
                strDiv += '&lt;td&gt;'+fileLine[j].trim()+'&lt;/td&gt;';
      }
      strDiv += '&lt;/tr&gt;';
  }

      strDiv += '&lt;/table&gt;';
      var CSVsaida = document.getElementById('CSVsaida');
      CSVsaida.innerHTML = strDiv;
}</pre>

Quando o evento de onload for disparado ele executará a função acima, nela o arquivo csv lido será usado para contruir tabelas com suas linhas e colunas e o resultado final será inserido na tag CSVsaida.

Com este <a title="CSV File API" href="http://jsfiddle.net/bruiz/273dC/3/embedded/result/" target="_blank">EXEMPLO</a>, não temos dúvidas do poder deste padrão web. De fato poderemos simplificar muito o trabalho de leitura de arquivos. Agora fica por sua curiosidade e necessidade explorar a File API.

<span style="line-height: 1.5em">Bons estudos e bom trabalho!</span>