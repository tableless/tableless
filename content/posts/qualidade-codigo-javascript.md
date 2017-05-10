---
title: Assegurando a qualidade do seu código JavaScript
author: Davi Ferreira
type: post
date: 2012-07-09
excerpt: Conheça ferramentas de análise de código que ajudam a manter a qualidade e o padrão de suas aplicações javascript.
url: /qualidade-codigo-javascript/
tweetbackscheck:
  - 1356399448
shorturls:
  - 'a:3:{s:9:"permalink";s:31:"http://tableless.com.br/?p=6380";s:7:"tinyurl";s:26:"http://tinyurl.com/872wb4u";s:4:"isgd";s:19:"http://is.gd/uZXMuA";}'
twittercomments:
  - 'a:0:{}'
dsq_thread_id: 757524617
categories:
  - JavaScript
  - JQuery
  - Técnicas e Práticas
tags:
  - 2012
  - codigo
  - JavaScript
  - js
  - jslint

---
Enquanto <a href="http://tableless.com.br/testando-seu-codigo-jquery-com-jasmine-parte-1/" target="_blank">testes automatizados</a> asseguram o funcionamento de suas aplicações e, portanto, também a qualidade, algumas ferramentas atuam em outra área importante do seu código: a sintaxe.

Ferramentas de lint são scripts que interpretam seus arquivos javascript e buscam erros como varáveis não utilizadas, espaços em branco no final de linha, ausência de ponto-e-vírgula (um ponto polêmico) entre outros.

Abaixo você encontra alguns utilitários que buscam garantir melhor qualidade e padrão para seus códigos.

É importante ressaltar que esse tipo de ferramenta _não_ garante que seu código está funcionando, que a lógica está correta, garante apenas a presença de boas práticas de desenvolvimento.

## JSLint

<a href="http://www.jslint.com/" target="_blank">http://www.jslint.com/</a>

Desenvolvida por ninguém menos do que Douglas Crockford, pai do famoso &#8220;The Good Parts&#8221;, esta ferramenta busca tanto erros de sintaxe, como erros estruturais.

As regras e convenções utilizadas na análise podem ser encontradas no site <a href="http://javascript.crockford.com/code.html" target="_blank">javascript.crockford.com/code.html</a>.

Você pode utilizar a <a href="http://www.jslint.com/" target="_blank">versão online da ferramenta</a>, ou então instalar o script através do gerenciador de pacotes do NodeJS (npm). O código-fonte está <a href="https://github.com/douglascrockford/JSLint" target="_blank">disponível no GitHub</a>.

<img src="http://tableless.com.br/uploads/2012/07/gjslint.jpg" alt="" width="605" height="439" class="alignnone size-full wp-image-6383" srcset="uploads/2012/07/gjslint.jpg 605w, uploads/2012/07/gjslint-300x217.jpg 300w" sizes="(max-width: 605px) 100vw, 605px" />

## JSHint

<a href="http://www.jshint.com/" target="_blank">http://www.jshint.com/</a>

A ferramenta JSHint teve início como um _fork_ da JSLint, visando uma maior flexibilidade, permitindo configurações de acordo com necessidades específicas.

A documentação do projeto inclui uma <a href="http://www.jshint.com/options/" target="_blank">página de opções disponíveis</a> para essa personalização.

Assim como a JSLint, a JSHint pode <a href="http://www.jshint.com/" target="_blank">analisar seu código online</a> ou pode ser instalada via NPM.

<img src="http://tableless.com.br/uploads/2012/07/jshint.jpg" alt="" width="770" height="361" class="alignnone size-full wp-image-6385" srcset="uploads/2012/07/jshint.jpg 770w, uploads/2012/07/jshint-300x140.jpg 300w" sizes="(max-width: 770px) 100vw, 770px" />

## Closure Linter

<a href="https://developers.google.com/closure/utilities/" target="_blank">https://developers.google.com/closure/utilities/</a>

Diferentemente das ferramentas anteriores, a Closure Linter obriga o uso do estilo JavaScript defendido pela Google. É utilizada em todos os projetos da empresa, incluindo Gmail, Docs e Reader.

Também diferentemente das anteriores, a Closure Linter vem acompanhada de um script para corrigir os erros encontrados. Ou seja, ela não apenas indica o que está errado, como também oferece uma maneira de &#8220;corrigir&#8221; seu código automaticamente.

Os utilitários podem ser baixados na <a href="https://developers.google.com/closure/utilities/" target="_blank">página do projeto no Google Code</a>. O script _gjslint_ é o responsável pela análise de código enquanto o _fixjsstyle_ corrige os erros encontrados.

<img src="http://tableless.com.br/uploads/2012/07/gjslint.jpg" alt="" width="605" height="439" class="alignnone size-full wp-image-6383" srcset="uploads/2012/07/gjslint.jpg 605w, uploads/2012/07/gjslint-300x217.jpg 300w" sizes="(max-width: 605px) 100vw, 605px" />

## jQuery Lint

<a href="http://james.padolsey.com/javascript/jquery-lint/" target="_blank">http://james.padolsey.com/javascript/jquery-lint/</a>

Para finalizar, uma ferramenta para os fãs de jQuery que analisa a sintaxe e a estrutura. Ela funciona de forma diferente das demais: sua aplicação é feita na página, ou seja, o script deve ser chamado após o código da sua aplicação, A resposta é enviada para o console do navegador.

<pre class="lang-html">&lt;script src="aplicacao.js"&gt;&lt;/script&gt;
&lt;script src="jquery.lint.js"&gt;&lt;/script&gt;
</pre>

É altamente configurável e pode ser adaptada para os padrões de desenvolvimento do seu projeto.

<img src="http://tableless.com.br/uploads/2012/07/jquerylint.jpg" alt="" width="366" height="149" class="alignnone size-full wp-image-6384" srcset="uploads/2012/07/jquerylint.jpg 366w, uploads/2012/07/jquerylint-300x122.jpg 300w" sizes="(max-width: 366px) 100vw, 366px" />

O código-fonte do projeto está disponível no GitHub: <a href="https://github.com/padolsey/jQuery-Lint" target="_blank">github.com/padolsey/jQuery-Lint</a>