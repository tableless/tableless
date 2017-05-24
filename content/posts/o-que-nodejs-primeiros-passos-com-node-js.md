---
title: O que é Node.js e saiba os primeiros passos
author: Cosme Lopes
type: post
date: 2014-07-28
excerpt: Da instalação ao seu primeiro web server com JavaScript.
url: /o-que-nodejs-primeiros-passos-com-node-js/
dsq_thread_id: 2877932820
categories:
  - nodejs
  - Back-end
  - Código
  - JavaScript
tags:
  - js
  - Node
  - tutorial

---
## O que é Node.js?

<a href="http://www.nodejs.org/" rel="noreferrer">Node.js</a> é uma plataforma para desenvolvimento de aplicações _server-side_ baseadas em rede utilizando **JavaScript** e o **V8 JavaScript Engine**, ou seja, com **Node.js** podemos criar uma variedade de aplicações _Web_ utilizando apenas código em **JavaScript**.

Em uma primeira análise essa informação pode não parecer tão interessante, uma vez que existem diversas outras maneiras em que esses tipos de serviços podem ser implementados. Mas se pensarmos um pouco mais sobre as demandas de aplicações na internet e o modo em que o código em **JavaScript** pode ser estruturado, vamos nos deparar com uma gama de novas possibilidades para desenvolvimento _Web_, e provavelmente nos juntar à crescente comunidade que tem adotado essa plataforma.

Uma importante diferença está no fato do Node ser _single threaded_. Embora isso possa parecer uma desvantagem em um primeiro momento, o que percebemos ao desenvolver com **Node.js** é que isso simplifica extremamente a construção da aplicação, e por **Node.js** utilizar uma abordagem não obstrutiva, essa diferença vai ser imperceptível na maioria dos casos.

### V8 JavaScript Engine

É o interpretador de **JavaScript** open source implementado pelo **Google** em **C++** e utilizado pelo **Chrome**. O que sem dúvidas gera uma grande expectativa em relação ao desempenho do **Node.js**.

## Instalando o Node.js

A instalação do **Node.js** é extremamente simples graças ao fato de o **V8 JavaScript Engine** ser completamente multi-plataforma, tudo que você precisa fazer é visitar a <a href="http://www.nodejs.org/" rel="noreferrer">página oficial do Node.js</a>, clicar em &#8220;INSTALL&#8221; e seguir as instruções.

<img style="width: 100%" src="http://tableless.com.br/uploads/2014/07/node_2.png" alt="img node 2" />

Após a instalação, basta executar o seguinte comando no seu terminal para verificar se foi instalado corretamente:

<pre class="lang-plain">$ node -v
&gt; v0.10.26
</pre>

deve retornar a versão do node que foi instalada, como por exemplo _v0.10.26_.

## O web server &#8216;Olá mundo!’

Ok, então vamos construir alguma coisa.

Nosso primeiro exemplo é um servidor que retorna a string &#8216;Olá mundo&#8217; para qualquer requisição. Para fazer isso utilizando Node você vai precisar de criar um arquivo **JavaScript** que pode ser chamado _olanode.js_ e de três minutos do seu tempo.

Escreva o seguinte código no seu arquivo:

<pre class="lang-javascript">var http = require('http');
http.createServer(function(req,res) {
  res.writeHead(200, { 'Content-Type': 'text/plain; charset=utf-8' });
  res.end('Olá mundo!');
}).listen(3000);
console.log('Servidor iniciado em localhost:3000. Ctrl+C para encerrar…');
</pre>

Para executar o seu programa Node basta o seguinte comando no seu terminal:

<pre class="lang-plain">$ node olanode.js
</pre>

Para testar seu servidor você pode acessar _localhost:3000_ no seu navegador ou utilizar linha de comando com o comando `curl` (em uma nova instância do terminal) como mostrado a seguir:

<pre class="lang-plain">$ curl http://0.0.0.0:3000/
&gt; Olá mundo!
</pre>

Caso você prefira retornar algum _html_ válido para o navegador, basta alterar `'text/plain'` para `'text/html'` no código acima e utilizar uma _tag html_ legal como `<h2>`, como foi feito a seguir:

<pre class="lang-javascript">var http = require('http');

http.createServer(function(req,res) { 
  res.writeHead(200, { 'Content-Type': 'text/html; charset=utf-8' });
  res.end('&lt;h2&gt; Olá mundo! &lt;/h2&gt;');
}).listen(3000);

console.log('Servidor iniciado em localhost:3000. Ctrl+C para encerrar…’);
</pre>

<img style="width: 100%" src="http://tableless.com.br/uploads/2014/07/node_1.png" alt="img node 1" />

Agora basta voltar ao seu navegador e ver o resultado.

## Orientado a eventos e não obstrutivo

### Orientado a eventos

Vamos aproveitar este momento de euforia após a construção do seu primeiro servidor para aprender um pouco mais sobre **Node.js**.

Quando estamos desenvolvendo com **Node.js** devemos utilizar uma abordagem orientada a eventos, isso quer dizer que o desenvolvedor precisa conhecer os eventos que serão emitidos em diferentes momentos da execução e também saber como ouvi-los para executar as operações necessárias.

Um bom exemplo de orientação a eventos está na construção de interfaces de usuário. Muitas vezes utilizamos elementos como por exemplo os botões que ao serem clicados emitem um evento do tipo _click_ ao qual podemos ouvir e executar alguma operação.

No nosso exemplo anterior utilizamos esse conceito quando chamamos método `listen` do objeto do tipo _web server_ e passamos como parâmetro a porta 3000, com isso fizemos que a nossa aplicação ouvisse ao evento que é emitido sempre que alguém faz uma requisição no `localhost:3000` e a nossa resposta foi servir a string ou a página html. Este evento é chamado _request_.

Para ilustrar estes conceitos, podemos escrever o nosso exemplo anterior em uma sintaxe alternativa da seguinte forma:

<pre class="lang-javascript">var http = require('http');

var server = http.createServer();

server.on('request', function(req,res) { 
  res.writeHead(200, { 'Content-Type': 'text/html; charset=utf-8' });
  res.end('&lt;h2&gt; Olá mundo! &lt;/h2&gt;');
});

server.listen(3000);

console.log('Servidor iniciado em localhost:3000. Ctrl+C para encerrar…’);
</pre>

Dessa forma podemos ver claramente a maneira em que o **Node.js** opera para servir a sua página. Utilizamos o método `on` do nosso objeto _server_ para ouvir ao evento _request_ e fazer as operações. E definimos que estamos servindo na porta 3000.

### Não obstrutivo

Todos os recursos presentes no **Node.js** e também a maioria das bibliotecas feitas para ele adotaram um padrão não obstrutivo de escrever código, isso quer dizer que em **Node.js** você geralmente vai conseguir estruturar seu código de uma maneira que operações que não dependem de nada que está sendo executado possam ser executadas de forma independente.

Para mostrar um pouco como isso funciona, vamos um programa que escreve duas frases no terminal, porém uma dessas frases precisa ser carregada da memória antes de ser impressa.

<pre class="lang-javascript">var frase;

carregaFrase = function (callback) {
  setTimeout(function() {
    //Simula leitura da frase no banco de dados.
    frase = "Minha frase obstrutiva";
    callback();
  }, 3000)
}

imprimeFrase = function () {
  console.log(frase);
}

carregaFrase(imprimeFrase);

console.log(“Olá");
</pre>

Nesse exemplo foi criada uma função chamada `carregaFrase` cujo objetivo é ler uma determinada frase de uma fonte de dados, e uma outra função chamada `imprimeFrase` que imprime o valor de uma determinada variável no console. Como dependemos da leitura da frase na fonte de dados para imprimir o valor, passamos a função que imprime como parâmetro para a função de leitura para que possamos executar essa função quando a leitura for concluída. Esse tipo de função que é passada como parâmetro dessa maneira é chamada de _callback_.

Ao executar este exemplo com **Node.js** ou qualquer mecanismo **JavaScript** você vai perceber que a frase &#8220;Olá&#8221; será impressa antes da outra frase mesmo estando posicionada depois no código, isso se deve ao fato de sua execução não depender de nada enquanto a execução da outra frase depende de uma operação que leva 3 segundos.

Este é um exemplo extremamente simples de como criar um código não obstrutivo, portanto use sua imaginação para imaginar cenários em que isso pode ser útil.

Observe que no nosso primeiro exemplo com **Node.js** tanto a função `on` quanto a função `createServer` podem receber uma função de _callback_.

## Conclusão

Espero que este tutorial tenha sido o suficiente para provocar o seu interesse em aprender mais sobre **Node.js**. Portanto visite a <a href="http://nodejs.org/api/" rel="noreferrer">documentação do Node.js</a> para obter mais informações e exemplos de aplicações dessa plataforma e também a página da <a href="https://www.joyent.com" rel="noreferrer">Joyent</a>, patrocinadora oficial do projeto.

E finalmente, **Node.js** é um projeto _open source_, portanto você pode visualizar o código fonte e contribuir no <a href="https://github.com/joyent/node" rel="noreferrer">repositório do Node.js no GitHub</a>.
