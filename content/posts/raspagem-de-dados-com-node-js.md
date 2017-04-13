---
title: Raspagem de dados com Node.js
author: Rennan Martini Rodrigues
type: post
date: 2015-08-12
url: /raspagem-de-dados-com-node-js/
categories:
  - JavaScript
  - Técnicas e Práticas
tags:
  - JavaScript
  - NodeJS
  - raspagem de dados

---
Raspagem de dados, ou _Web scraping_, é uma técnica de extração de dados onde é possível recuperar informações de websites.

Existem diversas maneiras de fazer raspagem de dados: pode ser feito manualmente copiando e colando, utilizando uma ferramenta online, usando uma extensão para o navegador Google Chrome (como o <a href="https://chrome.google.com/webstore/detail/web-scraper/jnhgnonknehpejjnehehllkliplmbmhn" target="_blank">Webscrapper</a>), etc. Neste artigo será mostrado um passo-a-passo de como fazer raspagem de dados no site Portal da Transparência. O site <a href="http://www.portaldatransparencia.gov.br/" target="_blank">Portal da Transparência</a> é mantido pelo Tribunal de Contas da União, órgão que fiscaliza as contas do governo. Informações de gastos com aquisição e contratação de obras e compras governamentais, diárias pagas, cartões de pagamento do Governo Federal, entre outras são exemplos que podem ser encontrado.

Para fazer a aplicação raspar dados, usaremos as seguintes ferramentas:

  * <a href="http://nodejs.org/" target="_blank">Node.js</a>
  * <a href="http://expressjs.com/" target="_blank">Express</a>
  * <a href="https://github.com/request/request" target="_blank">Request</a> &#8211; Para fazer chamadas HTTP
  * <a href="https://github.com/cheeriojs/cheerio" target="_blank">Cheerio</a> &#8211; Para acessar o DOM externo e extrair os dados

## Configuração

Primeiro devemos configurar as dependências necessárias no arquivo package.json:

<pre class="lang-javascript">{
{
    "name": "node-scrap-govbr",
    "repository": {
        "type": "git",
        "url": "git://github.com/rennan/node-scrap-govbr.git"
    },
    "version": "0.0.1",
    "description": "Exemplo simples de raspagem de dados em um site do Governo Federal Brasileiro com Node.js.",
    "main": "server.js",
    "author": "Rennan Martini ",
    "license": "MIT",
    "dependencies": {
        "express": "latest",
        "request": "latest",
        "cheerio": "latest"
    }
}
</pre>

Com o arquivo **package.json** pronto, é só instalar as dependências com o comando `npm install`.

Agora que as dependências foram instaladas, iremos definir o que deve ser criado. Neste exemplo, iremos fazer uma requisição na página de <a href="http://www.portaldatransparencia.gov.br/PortalComprasDiretasOEOrgaoSuperior.asp?Ano=2015&Valor=86726995548647&Pagina=1" target="_blank">Gastos Diretos por Órgão Executor</a>. Nesta página teremos acesso aos gastos que o governo teve em 2015, separado por Ministério. Uma vez que tivermos acesso a estas informações, podemos escolher o que salvar em um arquivo JSON no computador.

## A aplicação

O resumo da raspagem de dados funcionará da seguinte forma:

  1. Nossa app vai fazer uma requisição a URL que iremos raspar
  2. A requisição irá capturar o HTML da página e fornecer ele para o nosso server
  3. Pelo server, iremos acessar o DOM e extrair as informações específicas (no caso a tabela de gastos)
  4. Em seguida, nossa app vai criar um arquivo .json com os dados extraídos e salvar na pasta do projeto.

Toda a a estrutura lógica ficará em um arquivo **server.js**.

<pre class="lang-javascript">var express = require('express'),
    fs = require('fs'),
    request = require('request'),
    cheerio = require('cheerio'),
    app = express();

// Passo 1
app.get('/raspagem', function(req, res) {
    ...
})

app.listen('8081')
console.log('Executando raspagem de dados na porta 8081...');
exports = module.exports = app;
</pre>

## Fazendo a requisição

A requisição externa deve ser realizada dentro do escopo do método `app.get()` através da função `<b>request()</b>`. O método `request` deve receber dois parâmetros: a `url` e o `callback`. No parâmetro `url` colocamos a página do Portal da Transparência e no `callback` iremos declarar três novos parâmetros: `error`, `response` e o `html`.

<pre class="lang-javascript">app.get('/raspagem', function(req, res) {
    // Passo 2
    url = 'http://www.portaldatransparencia.gov.br/PortalComprasDiretasOEOrgaoSuperior.asp?Ano=2015&Valor=86726995548647&Pagina=1';
    request(url, function(error, response, html) {
        ...
    })
})
</pre>

## Acessando o DOM da URL externa

<img src="http://tableless.com.br/uploads/2015/07/DOM.gif" alt="DOM" width="1104" height="1040" class="alignleft size-full wp-image-50467" />

Inspecionamos o código-fonte para ver o seletor da tabela que iremos fazer a raspagem. O cheerio é uma biblioteca que nos dá permissão de manipular facilmente o DOM dos elementos da url. Se você já utilizou jQuery, está familiarizado com a estrutura dos seletores. Depois de encontrar o seletor, iremos manipular os elementos filhos da `div#listagem`, no caso a tabela. 

<pre class="lang-javascript">...
// Assegurar que não tenha erros para fazer a raspagem de dados com sucesso
if (!error) {
    var $ = cheerio.load(html);

    // Objeto que irá armazenar a tabela
    var resultado = [];

    // Passo 3
    // Manipulando o seletor específico para montar nossa estrutura
    // Escolhi não selecionar a primeira linha porque faz parte do header da tabela
    $('#listagem tr:not(:first-child)').each(function(i) {
        // Obtendo as propriedades da tabela. 
        // O método .trim() garante que irá remover espaço em branco
        var codigo = $(this).find('td').eq(0).text().trim(),
            orgao = $(this).find('td').eq(1).text().trim(),
            valorTotal = $(this).find('td').eq(2).text().trim();
        
        // Inserindo os dados obtidos no nosso objeto
        resultado.push({
            codigo: codigo,
            orgao: orgao,
            total: valorTotal
        });
    });
}
</pre>

## Formatando e Extraindo

Nós armazenamos os dados extraídos em uma variável chamada `resultado`. Agora é necessário colocar as mãos na API do NodeJS chamada **Fyle System**. Esta biblioteca nos dá acesso pra várias coisas legais, dentre elas a possibilidade de <a href="escrever arquivos" target="_blank">escrever arquivos</a>. No método `writeFile()` passaremos dois parâmetros: o **arquivo .json** que será gerado e o **objeto** que será exportado neste arquivo.

<pre class="lang-javascript">// Passo 4
fs.writeFile('resultado.json', JSON.stringify(resultado, null, 4), function(err) {
    console.log('JSON escrito com sucesso! O arquivo está na raiz do projeto.')
})
</pre>

Assim, quando executarmos o comando `node server.js` no terminal a nossa aplicação irá fazer a raspagem na URL e gerar o arquivo **resultado.json**.

<img src="http://tableless.com.br/uploads/2015/07/resultado.json_.png" alt="resultado.json" width="1110" height="974" class="alignleft size-full wp-image-50472" />

## Validando

É sempre importante validar o que você está fazendo. Podemos verificar se o nosso arquivo .json é válido com a ferramenta <a href="http://jsonlint.com/" target="_blank">JSONLint</a>:
  
<img src="http://tableless.com.br/uploads/2015/07/valid_json.png" alt="valid_json" width="961" height="631" class="alignleft size-full wp-image-50473" />

## Considerações finais

Vimos neste exemplo que o processo de raspagem de dados pode ser bem simples, porém é uma técnica poderosa que aliada a outros serviços é possível construir ótimas aplicações. O código completo utilizado como exemplo neste post está versionado no <a href="https://github.com/rennan/node-scrap-govbr/" target="_blank">GitHub do autor</a>.

### Porquê escolhi um site do governo

Decidi escolher um site do governo porquê trata-se de um Portal com todas informações disponíveis ao cidadão, que por uma série de fatores acaba passando despercebido. É importante evidenciar que o Governo incentiva o manuseio de suas informações com <a href="http://dados.gov.br/dados-abertos/" target="_blank">dados abertos</a>. Para se ter uma noção sobre esta iniciativa, existem <a href="http://br.okfn.org/projetos/" target="_blank">diversos projetos</a> que trabalham com os dados governamentais, através de raspagem e bots automatizadores de tarefas. O [DataBR][1], por exemplo, é um conjunto de API&#8217;s que possibilita desenvolvedores, jornalistas, analistas e demais interessados, trabalhar com dados governamentais brasileiros.

<p style="text-align: center">
  ***
</p>

Espero que tenha aproveitado a leitura.

 [1]: http://databr.io/