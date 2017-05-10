---
title: 'Underscore.js: cinto de utilidades JavaScript'
author: Davi Ferreira
type: post
date: 2012-09-19
excerpt: Conheça esta biblioteca JavaScript que apresenta um conjunto sólido de utilitários para manipular listas e estruturas de dados.
url: /underscore-js-cinto-de-utilidades-javascript/
tweetbackscheck:
  - 1356409409
shorturls:
  - 'a:3:{s:9:"permalink";s:31:"http://tableless.com.br/?p=6829";s:7:"tinyurl";s:26:"http://tinyurl.com/8pyjd3k";s:4:"isgd";s:19:"http://is.gd/gw4KmR";}'
twittercomments:
  - 'a:0:{}'
dsq_thread_id: 849528670
categories:
  - JavaScript
tags:
  - JavaScript
  - underscorejs

---
Underscore.js é uma pequena biblioteca de códigos utilitários voltados principalmente para a manipulação de estrutura de dados.

Por míseros 4kb você ganha funcionalidades como _map_, _select_ e _invoke_, além de uma engine de _templating_ que, por si só, já faz valer o uso da biblioteca.

Outro ponto legal é que os scripts procuram sempre utilizar recursos nativos do navegador, ou seja, em browsers modernos a biblioteca tira proveito das implementações de _forEach_, _map_, _indexOf_, _filter_ etc.

## Utilizando

O processo é simples e conhecido. Basta fazer o [download do código-fonte][1] e incluir o script em sua página/aplicação. Todas as novas funcionalidades ficam disponíveis através do objeto global da biblioteca, o caractere underscore: _. Funciona basicamente como o $ do jQuery.

Vejamos agora algumas das principais funções disponibilizadas.

## Coleções (arrays e objetos)

### each

Este método varre uma lista de elementos e retorna a chave (quando houver) e o valor para uma função pré-determinada.

[cce lang=&#8221;javascript&#8221;]
  
_.each([&#8216;BA&#8217;, &#8216;MT&#8217;, &#8216;RJ&#8217;, &#8216;RN&#8217;, &#8216;RS&#8217;], function (estado) { console.log(estado); });

_.each({RJ: &#8216;Rio de Janeiro&#8217;, SP: &#8216;São Paulo&#8217;, RS: &#8216;Rio Grande do Sul&#8217;}, function (estado, sigla) { console.log(estado + &#8216;/&#8217; + sigla); });
  
[/cce]

### map

A função **map** retorna uma nova lista de elementos criada a partir de uma função executada em cada um dos itens da lista original.

[cce lang=&#8221;javascript&#8221;]
  
var times = [&#8216;Flamengo&#8217;, &#8216;Fluminense&#8217;, &#8216;Vasco&#8217;, &#8216;Botafogo&#8217;];

_.map(times, function (time) { return time + &#8216;-RJ&#8217;; });
  
// [&#8220;Flamengo-RJ&#8221;, &#8220;Fluminense-RJ&#8221;, &#8220;Vasco-RJ&#8221;, &#8220;Botafogo-RJ&#8221;]
  
[/cce]

### filter

O utilitário **filter** busca por elementos que retornem verdadeiro no teste especificado.

[cce lang=&#8221;javascript&#8221;]
  
var multiplosDeTres = _.filter([1, 2, 3, 4, 5, 6, 7, 8, 9], function(num){ return num % 3 == 0; });
  
// [3, 6, 9]
  
[/cce]

### find

Diferentemente do método **\_filter\_**, o **\_find\_** retorna apenas o primeiro elemento que passe no teste especificado.

[cce lang=&#8221;javascript&#8221;]
  
var primeiroMultiploDeTres = _.find([1, 2, 3, 4, 5, 6, 7, 8, 9], function(num){ return num % 3 == 0; });
  
// 3
  
[/cce]

### pluck

O método **_pluck** é uma versão muito usada do utilitário **\_map\_** que retorna uma lista formada por valores de uma propriedade específica.

[cce lang=&#8221;javascript&#8221;]
  
var estados = [{sigla: &#8216;RJ&#8217;, nome: &#8216;Rio de Janeiro&#8217;},
                 
{sigla: &#8216;SP&#8217;, nome: &#8216;São Paulo&#8217;},
                 
{sigla: &#8216;RS&#8217;, nome: &#8216;Rio Grande do Sul&#8217;}],
      
nomes = _.pluck(estados, &#8216;nome&#8217;);
  
// [&#8220;Rio de Janeiro&#8221;, &#8220;São Paulo&#8221;, &#8220;Rio Grande do Sul&#8221;]
  
[/cce]

### max, min

Os métodos **max** e **min** retornam os maiores e menores valores em uma lista. Estes valores podem ser tanto os números em uma lista simples, como valores de propriedades de um objeto quando você especifica uma função.

[cce lang=&#8221;javascript&#8221;]
  
var numeros = [100, 32, 29, 105, 30];
  
_.min(numeros);
  
// 29
  
_.max(numeros);
  
// 105

var times = [{nome: &#8216;Flamengo&#8217;, titulos: 6},
               
{nome: &#8216;Fluminense&#8217;, titulos: 2},
               
{nome: &#8216;Vasco&#8217;, titulos: 4},
               
{nome: &#8216;Botafogo&#8217;, titulos: 1}];
  
_.max(times, function (time) { return time.titulos });
  
// {nome: &#8220;Flamengo&#8221;, titulos: 6}
  
[/cce]

### sortBy

Este método ordena uma lista do maior para o menor valor. O parâmetro de ordenação pode ser uma propriedade comum dos objetos ou uma função comparativa.

[cce lang=&#8221;javascript&#8221;]
  
// usando a mesma variável times acima 🙂
  
_.sortBy(times, &#8216;titulos&#8217;).reverse();
  
// [{nome: &#8220;Flamengo&#8221;, titulos: 6}, {nome: &#8220;Vasco&#8221;, titulos: 4}, {nome: &#8220;Fluminense&#8221;, titulos: 2}, {nome: &#8220;Botafogo&#8221;, titulos: 1}]
  
[/cce]

## Arrays

### first, last

Os métodos **first** e **last** retornam, respectivamente, os primeiros e os últimos elementos de um array. Você pode especificar, como segundo parâmetro, a quantidade de itens a ser retornada.

[cce lang=&#8221;javascript&#8221;]
  
var linguagens = [&#8216;ruby&#8217;, &#8216;python&#8217;, &#8216;php&#8217;, &#8216;java&#8217;];
  
_.first(linguagens, 2);
  
// [&#8220;ruby&#8221;, &#8220;python&#8221;]
  
_.last(linguagens);
  
// java
  
[/cce]

### union

O método **union** retorna uma lista com os elementos únicos de dois ou mais arrays.

[cce lang=&#8221;javascript&#8221;]
  
_.union([1, 2, 3], [4, 3], [10, 2, 9])
  
// [1, 2, 3, 4, 10, 9]
  
[/cce]

### difference

O utilitário **difference** retorna elementos de um array que não estão presentes em outros arrays.

[cce lang=&#8221;javascript&#8221;]
  
var times = [&#8216;Flamengo&#8217;, &#8216;Vasco&#8217;, &#8216;Botafogo&#8217;, &#8216;Fluminense&#8217;];
  
var segundaDivisao = [&#8216;Vasco&#8217;, &#8216;Botafogo&#8217;];
  
var terceiraDivisao = [&#8216;Fluminense&#8217;];
  
_.difference(times, segundaDivisao, terceiraDivisao);
  
// [&#8220;Flamengo&#8221;]
  
[/cce]

### indexOf

O método **indexOf** retorna o índice de um elemento no array especificado.

[cce lang=&#8221;javascript&#8221;]
  
var times = [&#8216;Flamengo&#8217;, &#8216;Vasco&#8217;, &#8216;Botafogo&#8217;, &#8216;Fluminense&#8217;];
  
_.indexOf(times, &#8216;Vasco&#8217;);
  
// 1
  
[/cce]

## Funções

### bind

Não confunda o **bind** do Underscore.js com o **bind** do jQuery. Aqui, este método associa um objeto a uma função, ou seja, o **this** no contexto da função será o objeto informado. Você ainda pode passar valores para os parâmetros da função.

[cce lang=&#8221;javascript&#8221;]
  
var retornaTotalArtigos = function () { return this.nome + &#8216;: &#8216; + this.totalArtigos };
  
retornaTotalArtigos = _.bind(retornaTotalArtigos, {nome: &#8216;Davi Ferreira&#8217;, totalArtigos: 12});
  
retornaTotalArtigos();
  
// Davi Ferreira: 12
  
[/cce]

### once

O método **once** cria uma função que só pode ser executada uma única vez. As próximas chamadas da função vão sempre retornar o valor da primeira execução.

[cce lang=&#8221;javascript&#8221;]
  
var dataCarregamentoInicial = function () { return +new Date; };
  
dataCarregamentoInicial = _.once(dataCarregamentoInicial);
  
dataCarregamentoInicial();
  
dataCarregamentoInicial();
  
// as duas chamadas vão retornar sempre o mesmo timestamp
  
[/cce]

## Objetos

### keys, values

Os métodos acima retornam, respectivamente, os nomes e os valores das propriedades de um objeto.

[cce lang=&#8221;javascript&#8221;]
  
_.keys({RJ: &#8216;Rio de Janeiro&#8217;, SP: &#8216;São Paulo&#8217;, RS: &#8216;Rio Grande do Sul&#8217;});
  
// [&#8220;RJ&#8221;, &#8220;SP&#8221;, &#8220;RS&#8221;]
  
_.values({RJ: &#8216;Rio de Janeiro&#8217;, SP: &#8216;São Paulo&#8217;, RS: &#8216;Rio Grande do Sul&#8217;});
  
// [&#8220;Rio de Janeiro&#8221;, &#8220;São Paulo&#8221;, &#8220;Rio Grande do Sul&#8221;]
  
[/cce]

### clone

Este método clona um objeto, mantendo suas referências.

[cce lang=&#8221;javascript&#8221;]
  
_.clone({RJ: &#8216;Rio de Janeiro&#8217;, SP: &#8216;São Paulo&#8217;, RS: &#8216;Rio Grande do Sul&#8217;});
  
// {RJ: &#8216;Rio de Janeiro&#8217;, SP: &#8216;São Paulo&#8217;, RS: &#8216;Rio Grande do Sul&#8217;}
  
[/cce]

### funções verificadoras

A biblioteca Underscore.js oferece uma vasta gama de funções verificadoras para objetos, entre elas: **isEqual**, **isEmpty**, **isFunction** e **isNull**.

[cce lang=&#8221;javascript&#8221;]
  
var obj = {},
      
obj2 = {};
  
_.isEmpty(obj);
  
// true
  
obj = {site: &#8216;Tableless&#8217;, categorias: [&#8216;JavaScript&#8217;. &#8216;jQuery&#8217;, &#8216;HTML5&#8217;]};
  
obj2 = {site: &#8216;Tableless&#8217;, categorias: [&#8216;JavaScript&#8217;. &#8216;jQuery&#8217;, &#8216;HTML5&#8217;]};
  
_.isEqual(obj, obj2);
  
// true
  
obj = function () { console.log(&#8216;Sou uma funcção!&#8217;); };
  
_.isFunction(obj);
  
// true
  
[/cce]

## Utilitários

### mixin

Este método permite a criação de suas próprias funções utilitárias no objeto Underscore.

[cce lang=&#8221;javascript&#8221;]
  
_.mixin({
    
isEven : function(number) {
      
return number % 2 ? false : true;
    
}
  
});
  
_.isEven(3);
  
// false
  
_.isEven(10);
  
// true
  
[/cce]

### escape

O método **escape** transforma caracteres como &#8220;&&#8221; e &#8220;/&#8221; para utilização dentro de um bloco HTML.

[cce lang=&#8221;javascript&#8221;]
  
_.escape(&#8216;

Tableless: JavaScript, HTML & CSS

&#8216;);
  
// <p>Tableless: JavaScript, HTML & CSS<&#x2F;p>
  
[/cce]

### template

Por fim, um método para aplicar templates em seu código JavaScript:

[cce lang=&#8221;javascript&#8221;]
  
var times = [{nome: &#8216;Flamengo&#8217;, titulos: 6},
               
{nome: &#8216;Fluminense&#8217;, titulos: 2},
               
{nome: &#8216;Vasco&#8217;, titulos: 4},
               
{nome: &#8216;Botafogo&#8217;, titulos: 1}],
      
tpl = &#8220;<% _.each(times, function(time) { %> <li><%= time.nome %> &#8211; <%= time.titulos %> título(s)</li> <% }); %>&#8221;;
  
_.template(tpl, {times: times});
  
// <li>Flamengo &#8211; 6 título(s)</li> <li>Fluminense &#8211; 2 título(s)</li> <li>Vasco &#8211; 4 título(s)</li> <li>Botafogo &#8211; 1 título(s)</li>
  
[/cce]

Para facilitar e aumentar a legibilidade, o seu template pode ser declarado em uma tag script separada:

[cce lang=&#8221;html&#8221;]
  
<script type=&#8221;text/html&#8221; id=&#8221;tplTimes&#8221;>
  
<% _.each(times, function(time) { %>
    
<li><%= time.nome %> &#8211; <%= time.titulos %> título(s)</li>
  
<% }); %>
  
</script>

<script>
  
var times = [{nome: &#8216;Flamengo&#8217;, titulos: 6},
               
{nome: &#8216;Fluminense&#8217;, titulos: 2},
               
{nome: &#8216;Vasco&#8217;, titulos: 4},
               
{nome: &#8216;Botafogo&#8217;, titulos: 1}],
      
tpl = $(&#8216;#tplTimes&#8217;).html();
  
_.template(tpl, {times: times});
  
</script>
  
[/cce]

Estes foram apenas alguns exemplos de métodos e funções utilitárias presentes na biblioteca Underscore.js. Para saber mais sobre o projeto, visite o [site oficial][2].

 [1]: http://underscorejs.org/ ""
 [2]: http://underscorejs.org/