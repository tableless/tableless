---
title: Web Speech API – Reconhecimento de voz com JavaScript
author: Clovis Neto
type: post
date: 2014-10-06
excerpt: Imagine websites onde os usuários podem navegar pelas páginas ou preencher campos de formulário usando a sua voz e até mesmo interagir com a página enquanto dirige, sem tirar os olhos da estrada.
url: /web-speech-api-reconhecimento-de-voz-com-javascript/
categories:
  - JavaScript
tags:
  - reconhecedor de voz javascript
  - Web Speech API

---
O reconhecimento de voz tem várias aplicações no mundo real. Muitas pessoas tornaram-se familiarizadas com este conceito graças a softwares como o Siri e S-Voice. Esta aplicação pode melhorar drasticamente a usabilidade dos websites, principalmente para deficientes visuais. Imagine websites onde os usuários podem navegar pelas páginas ou preencher campos de formulário usando a sua voz e até mesmo interagir com a página enquanto dirige, sem tirar os olhos da estrada.

# O que é Web Speech API?

A Web Speech API foi lançada no final de 2012 e permite que os desenvolvedores forneçam a entrada de voz e recursos de saída de texto-para-voz em um navegador web. Esta API cuida da privacidade dos usuários, pois antes de deixar o site para acessar a voz através do microfone, o usuário deve explicitamente conceder a permissão. Curiosamente, o pedido de autorização é o mesmo que a API getUserMedia, apesar de não precisar da webcam. Se a página que executa esta API usa o protocolo HTTPS, o navegador solicita a permissão apenas uma vez.

Então veremos logo abaixo, um exemplo básico de como podemos implementar esta nova API aos nossos projetos:

# Criando a primeira página com reconhecimento de voz:

## Passo 1 &#8211; Estrutura HTML:

A estrutura HTML é bem simples, vejamos a marcação abaixo:

<pre class="lang-html">&lt;p id="ola"&gt;Olá tableless, você falou:&lt;/p&gt;

&lt;div id="transcription"&gt;&lt;/div&gt;

&lt;button id="rect"&gt;Gravar&lt;/button&gt;

&lt;span id="unsupported" class="hidden"&gt;API not supported&lt;/span&gt;
</pre>

**Onde:**

  * **Transcription &#8211;** Onde se encontrará o texto informando oque o usuário falou
  * **Rect &#8211;** Botão para reconhecer a voz do usuário
  * **unsupported &#8211;** Caso a API não seja suportada pelo browser

## Passo 2 &#8211; Testando

Como qualquer API, temos que verificar primeiramente se o browser suporta SpeechRecognition:

<pre class="lang-javascript">// Test browser support
window.SpeechRecognition = window.SpeechRecognition ||
window.webkitSpeechRecognition ||
null;

//caso não suporte esta API DE VOZ            
if (window.SpeechRecognition === null) {
	document.getElementById('unsupported').classList.remove('hidden');
}else {
	//......
}
</pre>

## Passo 3 &#8211; Métodos e propriedades

Depois de testar a compatibilidade da API, iremos instanciar o reconhecedor de  voz, usando o speechRecognition(). Como o código listado abaixo:

<pre class="lang-javascript">var recognizer = new window.SpeechRecognition();
</pre>

Este objeto expõe os seguintes métodos:

  * **onstart:** Define um callback que é disparado quando o serviço de reconhecimento começou a ouvir o áudio com a intenção de reconhecer.
  * **onResult:** Define um callback que é disparado quando o reconhecedor de voz retorna um resultado.
  * **onerror:** Define um callback que é acionado quando ocorre um erro de reconhecimento de voz.
  *  **onend:** Define um callback que é disparado quando o serviço foi desligado. O evento deve sempre ser gerado quando a sessão termina, não importa o que a razão.

Iremos criar uma varável que será responsável por exibir o texto que o usuário falou e também iremos definir a propriedade **continuous = <span style="color: #3366ff">true</span>**, que faz com que o reconhecedor de voz não pare de ouvir, mesmo que tenha pausas do usuário.

<pre class="lang-html">var transcription = document.getElementById("transcription");

        	//Para o reconhecedor de voz, não parar de ouvir, mesmo que tenha pausas no usuario
        	recognizer.continuous = true;
</pre>

Agora iremos definir a função &#8220;onresult&#8221; que define um callback que é disparado quando o reconhecedor de voz retorna um resultado.

<pre class="lang-javascript">recognizer.onresult = function(event){
        		transcription.textContent = "";
        		for (var i = event.resultIndex; i &lt; event.results.length; i++) {
        			if(event.results[i].isFinal){
        				transcription.textContent = event.results[i][0].transcript+' (Taxa de acerto [0/1] : ' + event.results[i][0].confidence + ')';
        			}else{
		            	transcription.textContent += event.results[i][0].transcript;
        			}
        		}
        	}
</pre>

Vamos analisar este código um pouco mais detalhadamente:
  
**transcription.textContent = &#8220;&#8221;;    **Faz com que limpe o texto que se encontra dentro da &#8220;<div id=&#8221;transcription&#8221;>&#8221;

**for (var i = event.resultIndex; i < event.results.length; i++) { ** Loop que pecorre o evento que contém o texto que o usuário falou.

Note que dentro deste loop, há uma condição, que verifica se o evento se encontra na última posição (**event.results[i].isFinal**), caso seja verdadeira, ele irá imprimir todo o texto, junto com a taxa de acerto, que vai de &#8220;0&#8221; até &#8220;1&#8221;. Caso seja falsa, ele vai adicionar mais texto na nossa div

## Passo 4 &#8211; Anexando o evento de click

Agora iremos anexar um evento de click, ao nosso botão, segue 0 código abaixo :

<pre class="lang-javascript">document.querySelector("#rect").addEventListener("click",function(){
        		try {
		            recognizer.start();
		          } catch(ex) {
		          	alert("error: "+ex.message);
		          }
        	});
</pre>

#### Onde:

**recognizer.start(); &#8211; **Inicia o record ( a gravação );

**catch(ex) {**
  
 **alert(&#8220;error: &#8220;+ex.message);**
  
 **} &#8211; ** tratamento de log, caso exista, algum erro de gravação

> É importante observarmos que o reconhecedor demora um pouco para poder interpretar a sua voz, mais ou menos uns 3 à 4 segundos, esta API ainda está em teste e que infelizmente até agora, só é  suportada no chrome,

# Finalizando

Bem pessoal, essa foi uma breve introdução sobre Web Speech API. Futuramente irei trazer mais artigo

Disponibilizei o código no github e também disponibilizei uma demo.

<a title="View Demo " href="http://clovisdasilvaneto.github.io/speechRecognition/" target="_blank">Clique aqui para ver a demo online</a>

<a title="ver o código completo" href="https://github.com/clovisdasilvaneto/speechRecognition/blob/master/meu_artigo.html" target="_blank">Clique aqui, para ir ao código completo.</a>