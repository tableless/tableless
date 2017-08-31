---
title: Parseando HTML com dados recebidos de um JSON ou Ajax
author: Fabiano Miranda
type: post
date: 2017-08-31
excerpt: Faça um grid (tabela) HTML com dados recebidos de um JSON para Websites, Web apps e conheça mais sobre o plugin jQuery miranda-js. 
categories:
  - Artigos
  - HTML
  - Ajax
  - Código
  - JavaScript
  - jQuery
  - Mobile
---

A muito tempo venho passando pelos mesmos problemas em todas as empresas em que trabalho, que é a integração entre front-end e back-end sem que um preciso trabalhar e entender o código do outro. Normalmente o programador back-end sempre precisar abrir o HTML e ficar programando e misturando os códigos. Quando não é assim, o front-end precisa aprender algum framework específico para camada de view.

Já existem no mercado alguns frameworks para facilitar essa integração, mas esse é muito simples e funcional para pequenas integrações. Trata-se de um plugin para jQuery chamado Miranda-JS.

## Trabalhando com o Miranda-JS

Primeiro passo é ter as dependências no seu código:
 - jQuery acima da versão 1.7
 - miranda.js

Ele interage com os nomes dos elementos JSON e os trata como chaves que você coloca no seu HTML.

JSON
> {titulo: "Tableless"}

HTML
> &lt;h1&gt;[[titulo]]&lt;/h1&gt;


Exemplo completo de um objeto na própria página
> &lt;script&gt;
          $( document ).ready(function() {
              var data = {&quot;name&quot;: &quot;Fabiano&quot;, &quot;lastname&quot;: &quot;Miranda&quot;};
              $(&quot;#boxPeople&quot;).mirandajs(data);
          });
  &lt;/script&gt;
  &lt;div id=&quot;boxPeople&quot; style=&quot;display: none;&quot;&gt;
      &lt;h1&gt;[[name]]&lt;/h1&gt;
      &lt;h2&gt; [[lastname]]&lt;/h2&gt;
  &lt;/div&gt;
							

O JSON pode ser um objeto na própria página ou ser carregado de uma URL por Ajax.


Outra função importante é a possibilidade de processar vários nós do JSON de uma vez configurando alguns parâmetros opcionais.

## Fontes e documentação

**Para saber mais sobre o plugin**

  * [Site do projeto][1]
  * [Projeto no GitHub][2]

 [1]: http://www.fabianomiranda.com.br/miranda-js/
 [2]: https://github.com/fabiano-miranda/miranda-js/
