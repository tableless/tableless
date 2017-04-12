---
title: Teste automatizado de API com frisby e jasmine
author: rogerio dias moreira
type: post
date: 2015-08-27
url: /teste-automatizado-de-api-com-frisby-e-jasmine/
categories:
  - Back-end
  - JavaScript
tags:
  - frisby
  - gulp
  - jasmine
  - NodeJS
  - teste

---
O [Frisby][1] é um framework para teste de API REST que roda em cima do nodejs. Seu principal apelo é a facilidade em se fazer testes automatizados de API com o apoio do framework de teste BDD jasmine.

### Instalação:

Pré requisitos: nodejs, npm.

1) jasmine-node. Instalação global.

<pre class="lang-bash">sudo npm install -g jasmine-node</pre>

2) frisby. Instalação local no projeto.

<pre class="lang-bash">sudo nam install --save-dev frisby</pre>

### Hello, World!

Para o uso devemos instanciar seu módulo:

<pre class="lang-bash">var frisby = require ('frisby');</pre>

No seu uso mais básico, passamos como parâmetro a url a ser chamada e a resposta esperada.

<pre class="lang-bash">frisby.create('Teste BDD').get('http://www.teste.com/pessoa/1').expectStatus(200).toss();</pre>

Com o comando acima, estamos testando a API sendo que seu sucesso depende do código de retorno HTTP 200.

Por convenção devemos salvar este arquivo de teste com o sufixo &#8216;-spec.js&#8217;. Ex: &#8216;pessoa-spec.js&#8217;

Para execução do teste e para que o mesmo gere relatório no formato &#8216;junitreport&#8217; devemos executar o seguinte comando:

<pre class="lang-bash">jasmine-node pessoa-spec.js --junitreport --output specTestReportJasmine</pre>

Na prática apontamos para um pasta de teste para que todos sejam executados. Ex:

<pre class="lang-bash">jasmine-node spec/ --junitreport --output specTestReportJasmine</pre>

Já temos o essencial para integração do teste de api com alguma ferramenta de CI como o Jenkins(<https://jenkins-ci.org/>) com relatório padronizado.

### Hello, Universe!

O framework oferece alguns recursos interessantes e de fácil implementação para testar a resposta da API REST.

1) Testar se a resposta HTTP contém um cabeçalho específico.

<pre class="lang-javascript">frisby.create('Teste BDD').get('http://www.teste.com/pessoa/1')
   .expectStatus(200)
   .expectHeaderContains('Content-Type', 'json')
   .toss();

</pre>

2) Testar se a resposta HTTP contém um objeto com um conteúdo específico.

<pre class="lang-javascript">frisby.create('Teste BDD').get('http://www.teste.com/pessoa/1')
   .expectStatus(200)
   .expectHeaderContains('Content-Type', 'json')
   .expectJSON({codigo:1,nome:"fulano"})
   .toss();</pre>

3) Testar se a resposta HTTP contém um objeto com um tipo específico.

<pre class="lang-javascript">frisby.create('Teste BDD').get('http://www.teste.com/pessoa/1')
   .expectStatus(200)
   .expectHeaderContains('Content-Type', 'json')
   .expectJSONTypes({codigo: Number})
   .toss();</pre>

4) Realizar um teste que depende da conclusão de um teste anterior.

<pre class="lang-javascript">frisby.create('Teste BDD').get('http://www.teste.com/pessoa/1')
   .expectStatus(200)
   .expectHeaderContains('Content-Type', 'json')
   .expectJSONTypes({codigo: Number})
   .after(function(){
      frisby.create('Teste BDD').delete('http://www.teste.com/pessoa/1').expectStatus(200).toss();
   })
   .toss();</pre>

No teste acima, caso tenha sucesso ao obter informações de uma pessoa será feito um teste da exclusão da mesma.

#### Integração com GULP(Projetos em nodejs)

Quando a aplicação backend é feita em nodejs é interessante configurar o gulpjs(<http://gulpjs.com/>) para o gerenciamento dos testes. No exemplo abaixo o gulp é configurado para iniciar a aplicação backend, disparar os testes e finalizar a aplicação:

<pre class="lang-javascript">gulp.task('spec', function() {
   var jasmine = spawn('jasmine-node', ['spec/','--junitreport','--output','specTestReportJasmine']);
   var serverApp = require('./server');
   var resumeText = "";
 
   serverApp.init(8082);
 
   jasmine.stdout.on('data', function (data) {
      var texto = data.toString().trim();
      resumeText += texto;
   });
   jasmine.stderr.on('data', function (data) {
      console.log('erro: ' + data);
   });
   jasmine.on('close', function (code) {
      console.log('*********************\n' + resumeText);
      serverApp.close();
      process.exit();
   });
});</pre>

 [1]: http://frisbyjs.com/