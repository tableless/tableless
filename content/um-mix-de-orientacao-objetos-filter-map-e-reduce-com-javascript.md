---
title: Um mix de orientação a objetos + filter, map e reduce com Javascript.
author: itanor
type: post
date: 2015-03-24
url: /um-mix-de-orientacao-objetos-filter-map-e-reduce-com-javascript/
categories:
  - JavaScript

---
Criei alguns objetos simples mas com propriedades usadas no nosso dia-a-dia. Estes objetos estão armazenados num vetor de projetos. Cada objeto representa um projeto e tem as propriedades id, objeto, valorTotal e investido.

<pre class="lang-js">var projetos = [
	{id: 12, objeto: "revitalização da ponte abc", valorTotal: 220000.25, investido: 10000.00},
	{id: 14, objeto: "duplicação da rodovia br-101", valorTotal: 747800.50, investido: 35000.00},
	{id: 34, objeto: "aterramento localidade xyz", valorTotal: 635405.70, investido: 16500.00}
];</pre>

Aqui temos uma função que age como um construtor. O objeto tem a responsabilidade de realizar o somatório de um determinado valor do objeto projeto. Ela recebe como parâmetros um array de projetos (linhas) e uma propriedade escolhida para ser somada (coluna). Além desses atributos, uma função de filtro (funcaoFiltro) é utilizada. Mais adiante ela será explicada.

O método &#8216;total&#8217; realiza o somatório de determinada coluna do objeto projeto. Nele, temos o uso de algumas funções de Array, do Javascript: map, filter e reduce. Na primeira linha do método total é utilizada a função map, que a partir do array de projetos recebe um projeto e mapeia apenas determinada propriedade do projeto. Digo determinada por que ela é parametrizada com com &#8216;linha[coluna]&#8217;. Esta é uma forma dinâmica do Javascript acessar uma propriedade de um objeto. Desta forma, conseguimos parametrizar qual propriedade do objeto projeto queremos usar no somatório. Como resultado da aplicação de map no array de projetos temos um array de valores especificados pelo parâmetro &#8216;coluna&#8217;. 

Na segunda instrução do método total é verificada a existência da função de filtro, que é determinada pela variável &#8216;funcaoFiltro&#8217;. Para tal é disponibilizado um método aplicaFuncaoFiltro que recebe a função. Esta função será utilizada como parâmetro para a função filter, de Array. A instrução verifica se a função de filtro está definida, e se está é aplicada usando filter.

E, por último é utilizada a função reduce, também de Array. A partir dos valores mapeados e filtrados, a função passada para reduce realiza apenas a soma dos valores.

<pre class="lang-js">function SomadorDeColuna(linhas, coluna) {
	this.linhas = linhas;
	this.coluna = coluna;
	this.funcaoFiltro = undefined;
	this.total = function() {
	  var valores = this.linhas.map(function(linha) {
	return linha[coluna];
	});
this.funcaoFiltro && (valores = valores.filter(this.funcaoFiltro));

return valores.reduce(function(anterior, atual) {
	return anterior + atual;
});
};

this.aplicaFuncaoFiltro = function(funcao) {
	this.funcaoFiltro = funcao;
};
}</pre>

Os dois objetos &#8216;valorTotalAcimaDe500Mil&#8217; e &#8216;valorInvestidoAcimaDe15Mil&#8217; definidos acima
  
são usados para informar em qual propriedade será feito o somatório e qual função utilizar
  
como filtro.

Para o objeto valorTotalAcimaDe500Mil a propriedade a ser somada será
  
&#8216;valorTotal&#8217; e a função para filtrar os valores a serem somados é somente os acima de 500000.00.
  
Para o objeto valorInvestidoAcimaDe15Mil a propriedade a ser somada será &#8216;investido&#8217;
  
e a função para filtrar os valores a serem somados é somente os acima de 15000.00.

<pre class="lang-js">var valorTotalAcimaDe500Mil = {
	coluna: "valorTotal",
	funcao: function(valor) {return valor &gt; 500000.00;}
};</pre>

<pre class="lang-js">var valorInvestidoAcimaDe15Mil = {
	coluna: "investido",
	funcao: function(valor) {return valor &gt; 15000.00;}
};</pre>

Aqui temos uma instência de SomadorDeColuna usando o array projetos e a
  
coluna valorTotal para realizar o somatório. Na sequência, para o objeto
  
é informada a função de filtro. Ambos propriedade e função passados como
  
parâemtros são definidos nos objetos declarados acima. Por fim é impresso
  
o total invocando o método total, do objeto.

<pre class="lang-js">var somador = new SomadorDeColuna(projetos, valorTotalAcimaDe500Mil.coluna);
somador.aplicaFuncaoFiltro(valorTotalAcimaDe500Mil.funcao);
console.log(somador.total());</pre>

## Evoluindo o design para uso de Duck Typing.

Depois de implementar esta primeira versão, resolvi criar a ideia de regra de

filtro. Ao invés do construtor receber a coluna e a função de filtro ser
  
configurada em um método a parte, percebi que poderia usar a técnica de Duck Typing
  
para configurar a propriedade e a função de filtro ao mesmo tempo no objeto.

Abaixo está uma versão adaptada para usar a regra de filtro. A regra de filtro mantém
  
a propriedade e a função de filtro. Independente da propriedade e da função de filtro
  
que forem, o objeto SomadorDeColuna sabe aplicar a regra de filtro no somatório devido
  
ao &#8220;contrato&#8221; estabelecido para usar Duck Typing. Este contrato define que o objeto
  
para a regra de filtro deev definir um atributo &#8216;coluna&#8217; e um atributo &#8216;funcao&#8217;, que
  
representam a propriedade e a função, respectivamente.

<pre class="lang-js">var projetos = [
	{id: 12, objeto: "revitalização da ponte abc", valorTotal: 220000.25, investido: 10000.00},
	{id: 14, objeto: "duplicação da rodovia br-101", valorTotal: 747800.50, investido: 35000.00},
	{id: 34, objeto: "aterramento localidade xyz", valorTotal: 635405.70, investido: 16500.00}
];</pre>

<pre class="lang-js">function SomadorDeColuna(linhas, regraDeFiltro) {
this.linhas = linhas;</pre>

<pre class="lang-js">this.total = function() {
	var valores = this.linhas.map(function(linha) {
	return linha[regraDeFiltro.coluna];
});</pre>

<pre class="lang-js">var valoresFiltrados = valores.filter(regraDeFiltro.funcao);
return valoresFiltrados.reduce(function(anterior, atual) {
	return anterior + atual;
});
}</pre>

Caso não houver necessidade de possuir uma função de filtro, basta fornecer uma implementação que não filtra nenhum valor, ou seja, que retorne o próprio valor, na função de filtro. Os objetos &#8216;valorTotal&#8217; e &#8216;valorInvestido&#8217; explicitam esta ideia.

<pre class="lang-js">var valorTotalAcimaDe500Mil = {
	coluna: "valorTotal",
	funcao: function(valor) {return valor &gt; 500000.00;}
};
var valorTotal = {
	coluna: "valorTotal",
	funcao: function(valor) {return valor;}
};</pre>

<pre class="lang-js">var valorInvestidoAcimaDe15Mil = {
	coluna: "investido",
	funcao: function(valor) {return valor &gt; 15000.00;}
};
var valorInvestido = {
	coluna: "investido",
	funcao: function(valor) {return valor;}
};</pre>

<pre class="lang-js">var somador = new SomadorDeColuna(projetos, valorInvestido);
console.log(somador.total());</pre>

## Conclusão

Apensar da necessidade de somatório de diversos valores, não foi usado em nenhum momento o loop &#8216;for&#8217;. Reutilização de código sem introduzir possibilidade de novos bugs.

Uma modificação interessante para o objeto SomadorDeColuna seria incluir a desformatação de valores que estão representados como moeda (56.955,00) na tela. Uma boa biblioteca para isso é a [numeraljs][1].

Apesar de ser um objeto simples, tem muita utilidade em caso de somatórios no dia-a-dia.
  
É quase sempre inerente!

Valeu!

 [1]: http://numeraljs.com