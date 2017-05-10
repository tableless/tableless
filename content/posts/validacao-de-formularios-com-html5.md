---
title: Validação de formulários com HTML5
author: Raphael Fabeni
type: post
date: 2014-07-01
excerpt: Validar formulários sempre demandou algum tempo e dependências como bibliotecas JavaScript. Com HTML5 podemos passar essa responsabilidade para o navegador, ganhando tempo de desenvolvimento e economizando no peso da página.
url: /validacao-de-formularios-com-html5/
dsq_thread_id: 2792655271
categories:
  - HTML
  - Traduções
tags:
  - formularios
  - html5

---
O HTML5 trouxe diversas possibilidades e, principalmente facilidades para os desenvolvedores. Uma delas é relacionada a validação de formulários. O que antes era feito com algum tempo e JavaScript, hoje pode ser feito diretamente no HTML e em um tempo muito menor. Por isso, navegando pela internet achei no [SitePoint][1] esse [artigo][2] do [<span style="text-decoration: underline">A</span>gbonghama Collins][3], um desenvolvedor nigeriano, que escreveu de forma rápida e direta alguns pontos da validação de formulários utilizando HTML5 e, resolvi traduzi-lo para nós.

—

Quando contruímos aplicações web, é importante levarmos a segurança a sério, especialmente quando essa precisa coletar dados dos usuários.

Não confiar em ninguém, é uma norma máxima de segurança, portanto, nunca confie que o usuário vá inserir valores corretos e válidos no formulário. Por exemplo, em um campo de e-mail, em vez de inserir um endereço de e-mail válido, o usuário pode digitar um e-mail inválido ou dados mal-intencionados, obviamente, ignorando a indicação da requisição do campo.

Quando se trata de validar valores de campos de formulários, isso pode ser feito no _lado do cliente_ (navegador) e no _lado do servidor_ (usando a linguagem que preferir).

No passado, validações no _client-side_ só podiam ser feitas usando JavaScript ou algumas bibliotecas de _frameworks_ (como o [plugin jQuery validation][4]). Mas isso está mudando, ou melhor, já mudou, porque a validação agora pode ser feita usando **HTML5**, sem a necessidade de escrever um código complexo de JavaScript para isso.

## Validação de formulário com HTML5

HTML5 inclui um mecanismo bastante sólido na validação de formulários com base nos atributos da tag `input`:  _type_, _pattern_ e _require_. Graças a esses novos atributos, você pode delegar algumas funções de verificação de dados para o navegador.

Vamos examinar esse atributos para ver como eles podem nos ajudar na validação de um formulário.

## O atributo `type`

Esse atributo indica o tipo de controle de entrada de dados como o popular `<input type="text">` para manipulação de dados de texto simples.

Alguns controles de formulários herdam sistemas de validação sem a necessidade de escrever qualquer código. Por exemplo, `<input type="email">` valida o campo para garantir que o dado digitado seja de fato um endereço de e-mail válido. Se o campo tiver um dado inválido, o formulário não vai poder ser submetido até que esse erro seja corrigido.

<img class="alignnone size-full wp-image-42961" src="http://tableless.com.br/uploads/2014/06/validacao-email.png" alt="Imagem mostrando a validação client-side em um campo de formulário" width="297" height="100" />

[Teste o exemplo nesse link][5] digitando um endereço de e-mail válido ([Link do CodePen original][6]).

Há também o `<input type="number">`, `<input type="url">` e `<input type="tel">` para validar números, URLs e telefones respectivamente.

**Nota:** Os formatos de números de telefone variam de país para país devido à inconsistência nos tamanhos e formatos. Como resultado, a especificação não define um algoritmo para validá-los, portanto não é suportado nos navegadores web no momento da escrita.

Lembre-se, a validação pode ser feita para o campo telefone em conjunto com o atributo `pattern` que aceita uma _expressão regular_, e que veremos a seguir.

## O atributo `pattern`

O atributo `pattern` vai deixar os desenvolvedores felizes, principalmente aqueles que trabalham com front-end. Este atributo especifica um formato (na forma de expressão regular do JavaScript) em que o valor do campo é testado.

Expressões regulares são uma linguagem usada para analisar e manipular texto. Elas são frequentemente utilizadas para executar operações complexas de _search-and-replace_, e para garantir que os dados de texto estão corretos.

Hoje em dia, as expressões regulares estão incluídas na maioria das linguagens de programação, assim como em muitas linguagens de script, editores, aplicações, bancos de dados e ferramentas de linha de comando.

Expressões regulares (_RegEX_) oferecem um poderoso, conciso e flexível meio para encontrar _string_ ou textos com caracteres particulares, palavras ou padrões de caracteres.

Ao passarmos uma _string RegEX_ como valor para o atributo `pattern`, conseguimos definir qual valor é aceitável pelo campo do formulário e também informar ao usuário de possíveis erros.

Vamos ver alguns exemplos de como usar expressões regulares para validação de dados em campos de formulário.

### Números de telefone

Como mencionado, o `input` tel não é totalmente suportado pelos navegadores web devido à inconsistência no formato dos números de telefone em diferentes países.

Por exemplo, no meu país, a Nigéria, o formato do telefone é _xxxx-xxx-xxxx_, que seria algo como _0803-555-8205_.

A _RegEX_ `^\d{4}-\d{3}-\d{4}$` corresponde ao formato, portanto, o HTML ficaria assim:

<pre class="lang-html prettyprint linenums">&lt;label for="phonenum"&gt;Número de telefone:&lt;/label&gt;
&lt;input pattern="^\d{4}-\d{3}-\d{4}$" type="tel"&gt;
</pre>

[Veja aqui um exemplo][7]. ([Link do CodePen original][8]).

### Valores alfanuméricos

O exemplo a seguir corresponde a caracteres alfanuméricos (combinações de letras do alfabeto e números).

<pre class="lang-html prettyprint linenums">&lt;input pattern="[a-zA-Z0-9]+" type="text"&gt;</pre>

[Veja aqui um exemplo][9]. ([Link do CodePen original][10]).

### Usuário do twitter

Essa expressão regular corresponde a um usuário do Twitter com o símbolo `@`. Por exemplo: @tech3sky

<pre class="lang-html prettyprint linenums">&lt;input pattern="^@[A-Za-z0-9_]{1,15}$" type="text"&gt;</pre>

[Veja aqui um exemplo][11]. ([Link do CodePen original][12]).

### Modo de cor HEX

Esse corresponde a cores hexadecimais. Por exemplo #3b5998 ou #000.

<pre class="lang-html prettyprint linenums">&lt;input pattern="^#+([a-fA-F0-9]{6}|[a-fA-F0-9]{3})$" type="text"&gt;</pre>

[Veja aqui um exemplo][13]. ([Link do CodePen original][14]).

### Dando algumas dicas

Para fornecer ao usuário uma descrição da `pattern`, ou um erro reportando que o valor inserido está inválido, você pode utilizar o atributo `title`, dessa maneira:

<img class="alignnone size-full wp-image-42964" src="http://tableless.com.br/uploads/2014/06/validacao-title.png" alt="Imagem mostra o atributo title de um campo de formulário ao usuário deixar o mouse sob ele" width="273" height="100" />

<img class="alignnone size-full wp-image-42965" src="http://tableless.com.br/uploads/2014/06/validacao-erro.png" alt="Imagem mostra erro devido à entrada de dados inválidos em um campo de formuláriop" width="269" height="100" />

[Veja aqui um exemplo][15]. ([Link para o CodePen original][16]).

Se você é novo com expressões regulares, você pode [consultar esse documento no WebPlatform para lhe dar uma ajuda inicial][17]. No entanto, na maioria dos casos, você pode usar o Google para ajudar a procurar a expressão regular que você quer, ou até mesmo [utilizar uma ferramenta para ajudá-lo][18].

## O atributo `required`

Esse é um atributo _booleano_ usado para indicar que um determinando campo de formulário é obrigatório para o envio do mesmo. Ao adicionar esse atributo a um campo de formulário, o navegador obriga o usuário a inserir dados naquele campo antes de enviar o formulário.

Essa validação substitui a validação básica de formulário implementada com JavaScript, tornando as coisas um pouco mais úteis e nos poupando algum tempo de desenvolvimento.

Exemplo: `<input name="my_name" required="" type="text">` ou `<input name="my_name" required="required" type="text">` para compatibilidade XHTML.

<img class="alignnone size-full wp-image-42966" src="http://tableless.com.br/uploads/2014/06/validacao-required.png" alt="Imagem mostra erro da validação HTML5 em um campo de formulário que é obrigatório." width="208" height="150" />

Todos os links de exemplos acima utilizam o atributo `required`, assim você pode testá-los tentando submetê-los sem digitar nada nos campos.

## Resumo

O suporte dos navegadores para as _features_ de validação de formulários é bem grande, e você pode utilizar _polyfills_ quando necessário.

Vale a pena lembrar que confiar apenas no navegador (_client-side_) para a validação pode ser perigoso, pois isso pode ser contornado por um usuário mal-intencionado ou por _bots_.

Nem todos os navegadores suportam HTML5 e nem toda entrada de texto enviada para seu script virá do formulário. Isso significa que validação do lado do servidor também deve estar antes do envio dos dados para o processamento do servidor.

—

Texto traduzido e adaptado do [artigo][2] escrito pelo [Agbonghama Collins][3] em 06 de junho de 2014. Tradução autorizada pelo autor.

Dei um _fork_ em todos os exemplos do CodePen colocando o texto em português, mas mantive os links para os originais também.

Qualquer erro ou sugestão de melhoria na tradução, é bem vinda! 🙂

 [1]: http://www.sitepoint.com/
 [2]: http://www.sitepoint.com/client-side-form-validation-html5/
 [3]: https://twitter.com/tech4sky
 [4]: http://jqueryvalidation.org/
 [5]: http://codepen.io/raphaelfabeni/pen/hLcxn
 [6]: http://codepen.io/SitePoint/pen/BFwhz
 [7]: http://codepen.io/raphaelfabeni/pen/vDIor
 [8]: http://codepen.io/SitePoint/pen/Eambf
 [9]: http://codepen.io/raphaelfabeni/pen/Lgsdk
 [10]: http://codepen.io/SitePoint/pen/nptlf
 [11]: http://codepen.io/raphaelfabeni/pen/GBFkJ
 [12]: http://codepen.io/SitePoint/pen/nKGro
 [13]: http://codepen.io/raphaelfabeni/pen/ifvFI
 [14]: http://codepen.io/SitePoint/pen/ejqig
 [15]: http://codepen.io/raphaelfabeni/pen/ifsje
 [16]: http://codepen.io/SitePoint/pen/hbuxg
 [17]: http://docs.webplatform.org/wiki/concepts/programming/javascript/regex
 [18]: https://www.google.com.br/?gfe_rd=cr&ei=lkiWU4S-Momk8weRlIBw#q=regular+expression+tool