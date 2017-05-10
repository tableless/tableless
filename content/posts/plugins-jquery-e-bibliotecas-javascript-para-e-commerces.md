---
title: Plugins jQuery e bibliotecas JavaScript para e-commerces
author: Davi Ferreira
type: post
date: 2013-02-26
excerpt: Usabilidade não é o forte da maioria dos e-commerces nacionais. Conheça alguns plugins que podem facilitar (e muito) a vida dos usuários da sua loja virtual.
url: /plugins-jquery-e-bibliotecas-javascript-para-e-commerces/
dsq_thread_id: 1104038002
categories:
  - JavaScript
  - JQuery
tags:
  - bibliotecas
  - frameworks
  - JavaScript
  - JQuery

---
## jQuery.payment

[https://stripe.com/blog/jquery-payment][1]

O plugin jQuery.payment valida o número dos principais cartões do mercado. Desenvolvido pelo pessoal da [Stripe][2], empresa especializada em uma solução de pagamento para desenvolvedores de e-commerces, o plugin conta com validadores para números de cartão de crédito, data de validade e código de segurança.

Exemplos de uso:

<pre class="lang-jquery">$('.numero-cartao').payment('formatCardNumber');
$('.expiracao-cartao').payment('formatCardExpiry');
$('.codigo-cartao').payment('formatCardCVC');
$('.numerico').payment('restrictNumeric');</pre>

É possível também tirar proveito de alguns utilitários que acompanham o plugin e executar tarefas de validação, além de retornar informações do cartão baseado no número e a data de validade como um objeto:

<pre class="lang-jquery">$.payment.validateCardNumber('4242 4242 4242 4242'); //=&gt; true
$.payment.validateCardExpiry('05', '05'); //=&gt; false
$.payment.validateCardCVC('12344'); //=&gt; false
$.payment.cardType('4242 4242 4242 4242'); //=&gt; 'visa'
$.payment.cardExpiryVal('05 / 04'); //=&gt; {month: 5, year: 2004}</pre>

O código-fonte, em CoffeeScript, está disponível no GitHub: [https://github.com/stripe/jquery.payment][3].

## accounting.js

[http://josscrowcroft.github.com/accounting.js/][4]

Accounting.js é uma biblioteca JavaScript com funções utilitárias para formatar números e valores monetários.

Além de formatar números, extrair valores e converter números decimais, a biblioteca implementa uma função bem interessante para padronizar a exibição de números em colunas de uma tabela.

Exemplos de uso:

<pre class="lang-jquery">accounting.formatMoney(1337.99, "R$", 2, ".", ","); // R$1.337,99
accounting.formatColumn([99.9, 12.39, 44.33, 84950, -22], "R$");
// ["R$    99.90", "R$    12.39", "R$    44.33", "R$84,950.00", "R$   -22.00"]
accounting.formatNumber(86960, 2, ".", ","); // "86.960,00"
(0.932).toFixed(2); // "0.93"
accounting.unformat("R$ 29.443,32", ","); // 29443.32</pre>

Para padronizar o formato em todas as funções, sem a necessidade de utilizar parâmetros extras em suas chamadas, basta atualizar o objeto _accounting.settings_:

<pre class="lang-jquery">accounting.settings = {
  currency: {
	  symbol : "R$",
	  decimal : ",",
	  thousand: ".",
	  precision : 2 
  }
}</pre>

## Masked Input

[http://digitalbush.com/projects/masked-input-plugin/][5]

Ainda falando de formatação, temos o plugin MaskedInput, responsável por formatar qualquer _input_ em formulários, garantindo assim uma maior integridade dos dados digitados.

Exemplos de uso:

<pre class="lang-jquery">$(".cnpj").mask("99.999.999/9999-99");
$(".cpf").mask("999.999.999-99");
$(".telefone").mask("(99) 9999-9999");
$(".cep").mask("99.999-999");</pre>

É importante lembrar que esses tipos de formatação e validação não devem ser realizados apenas no cliente &#8211; devem ser processados também no servidor.

## Ideal Forms

[http://elclanrs.github.com/jq-idealforms/][6]

Formulários são uma parte importante de qualquer e-commerce e, geralmente, são a parte mais chata para o usuário: os cadastros tendem a ser tediosos, com campos desnecessários, validações mal-feitas e falta de informações.

O plugin Ideal Forms é uma ferramenta completa para a criação de formulários intuitivos e visualmente atraentes. Seus recursos incluem _inputs_ customizáveis (_select_, _radio_, _checkbox_ e arquivo), validação _on-the-fly_ e um layout totalmente responsivo.

A validação pode ser feita utilizando o atributo _data-ideal_, como no exemplo abaixo:

<pre class="lang-html">&lt;div&gt;&lt;label&gt;Usuário:&lt;/label&gt;&lt;input type="text" name="username" data-ideal="required username"/&gt;&lt;/div&gt;
&lt;div&gt;&lt;label&gt;Senha:&lt;/label&gt;&lt;input type="text" name="password" data-ideal="required pass"/&gt;&lt;/div&gt;
</pre>

Outra opção é utilizar parâmetros na inicialização do plugin. O Ideal Forms utiliza o atributo _name_ dos campos para configurações específicas:

<pre class="lang-jquery">$('#form-cadastro').idealforms({
	inputs: {
	  'idade': {
	    filters: 'required min',
	    data: { min: 18 },
	    errors: { min: 'Você precisa ter 18 anos para comprar nesse site' }
	  }
	}
});</pre>

Ainda é possível dividir um formulário em passos, recurso indicado para o cadastro e o registro de um pedido em um e-commerce. Para isso, basta adicionar mais de um elemento _section_ dentro do seu formulário.

A documentação do projeto é bem completa e está disponível no [GitHub][7].

## Filtrify

[http://luis-almeida.github.com/filtrify/][8]

Filtrify é um plugin jQuery que habilita filtros em tempo real, ideal para páginas de produtos em uma loja online. Basedo no atributo _data_ de elementos HTML, o Filtrify gera uma lista, possibilitando selecionar apenas elementos de um determinado filtro.

O plugin recebe dois elementos: um _container_ para os filtros e outro para os elementos a serem filtrados. No exemplo abaixo temos uma lista de produtos (notem as categorias no atributo _data_):

<div id="filtros">
</div>

<pre class="lang-html">&lt;div id="filtros"&gt;&lt;/div&gt;

&lt;ul id="produtos"&gt;
    &lt;li data-categoria="informática, eletrônicos, computadores"&gt;Desktop Core i7&lt;/li&gt;
    &lt;li data-genre="informática, acessórios, impressoras"&gt;Impressora HP Deskjet&lt;/li&gt;
    &lt;li data-genre="informática, acessórios, tablets"&gt;iPad&lt;/li&gt;
    &lt;li data-genre="telefonia, celular, apple"&gt;iPhone&lt;/li&gt;
    &lt;li data-genre="informática, laptops"&gt;Notebook Positivo&lt;/li&gt;
&lt;/ul&gt;</pre>

A inicialização fica assim:

<pre class="lang-jquery">$.filtrify("produtos", "filtros");</pre>

E o resultado:

<img src="http://tableless.com.br/uploads/2013/02/filtrify.jpg" alt="filtrify" width="378" height="333" class="alignnone size-full wp-image-10921" srcset="uploads/2013/02/filtrify.jpg 378w, uploads/2013/02/filtrify-190x168.jpg 190w, uploads/2013/02/filtrify-351x310.jpg 351w" sizes="(max-width: 378px) 100vw, 378px" />

## jQuery Zoom

[http://www.jacklmoore.com/zoom][9]

O plugin jQuery Zoom habilita o recurso de zoom em imagens com interações do mouse. A inicialização do plugin cria elementos novos para o efeito de zoom, portanto, deve ser aplicada em um elemento capaz de receber outros elementos (não pode ser aplicada em um elemento img).

Exemplos de uso:

<pre class="lang-jquery">$('a.foto-produto').zoom(); 
$('a.foto-produto-grab').zoom({ on:'grab' });</pre>

As opções do plugin incluem os seguintes parâmetros: _url_ da imagem maior, _on_ (_mouseover_, _grab_, _click_ ou _toggle_), _duration_ (velocidade do zoom) e _callback_.

## Bônus: Carrinho de compras com drag and drop

[http://tableless.com.br/carrinho-de-compras-com-drag-and-drop/][10]

Há mais ou menos dois anos escrevi um tutorial aqui no Tableless mostrando como implementar um carrinho com funções de _drag and drop_. 

Utilizando os métodos _draggable_ e _droppable_ da biblioteca jQueryUI, ao final do tutorial você tem um carrinho drag and drop completamente funcional, pronto para ser implementado no seu e-commerce.

[Clique aqui][11] para visualizar o exemplo do tutorial no navegador.

 [1]: https://stripe.com/blog/jquery-payment "https://stripe.com/blog/jquery-payment"
 [2]: https://stripe.com/ "https://stripe.com/"
 [3]: https://github.com/stripe/jquery.payment "https://github.com/stripe/jquery.payment"
 [4]: http://josscrowcroft.github.com/accounting.js/ "http://josscrowcroft.github.com/accounting.js/"
 [5]: http://digitalbush.com/projects/masked-input-plugin/ "http://digitalbush.com/projects/masked-input-plugin/"
 [6]: http://elclanrs.github.com/jq-idealforms/ "http://elclanrs.github.com/jq-idealforms/"
 [7]: https://github.com/elclanrs/jq-idealforms "https://github.com/elclanrs/jq-idealforms"
 [8]: http://luis-almeida.github.com/filtrify/ "http://luis-almeida.github.com/filtrify/"
 [9]: http://www.jacklmoore.com/zoom "http://www.jacklmoore.com/zoom"
 [10]: http://tableless.com.br/carrinho-de-compras-com-drag-and-drop/ "http://tableless.com.br/carrinho-de-compras-com-drag-and-drop/"
 [11]: http://tableless.github.com/exemplos/carrinho-compras/ "http://tableless.github.com/exemplos/carrinho-compras/"