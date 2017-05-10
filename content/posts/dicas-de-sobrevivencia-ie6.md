---
title: Dicas de sobrevivência em uma era pós o IE6
author: Diego Eis
type: post
date: 2012-04-09
excerpt: Confira algumas propriedades importantes do CSS que você não podia usar no IE6, mas pode usar hoje no IE7 ou superior.
url: /dicas-de-sobrevivencia-ie6/
tweetbackscheck:
  - 1356425875
shorturls:
  - 'a:3:{s:9:"permalink";s:31:"http://tableless.com.br/?p=5864";s:7:"tinyurl";s:26:"http://tinyurl.com/89d4ltm";s:4:"isgd";s:19:"http://is.gd/sD7pF1";}'
twittercomments:
  - 'a:0:{}'
dsq_thread_id: 642091069
categories:
  - Browsers
  - Código
  - CSS
  - HTML
  - Técnicas e Práticas
tags:
  - 2012
  - Browsers
  - CSS
  - desenvolvimento
  - desenvolvimento web
  - ie
  - internet explorer

---
Nós ficamos mal acostumados com o Internet Explorer 6&#8230; Digo isso por que tinhamos tantos problemas e limitações no tempo em que precisávamos suportá-lo, que até hoje nos privamos de algumas técnicas e propriedades do CSS que funcionam plenamente no IE8 e nos IEs mais novos. Quero confessar que eu estava até esses dias eu era prisioneiro da sombra do IE6.

Por isso, aqui vão algumas dicas de propriedades que você já deve conhecer, mas que não usa ainda por que acha que todos os IEs são iguais ao maldito IE6.

### :after

Você deve usar alguma técnica de **clearfix** que você criou ou que você pegou de algum lugar. Eu usava muito jquery para criar um elemento vazio dinamicamente no final do elemento que necessita do clearfix para fazê-lo parar de sofrer influência dos floats dos elementos. Essa técnica aqui pode salvar sua vida:

<pre class="lang-css">div:after {
    content:" ";
    display:block;
    clear:both;
}
</pre>

O **content** pode ser usado para uma série de outras coisas, como por exemplo inserir um ícone, objeto ou até texto depois de um determinado elemento.

Nesse caso o IE7 fica de fora.

### first-child

Sim. O First-child funciona no IE7 ou superior. Mas o last-child não. Sem chance.
  
Isso já acaba com aqueles problemas de alinhamento de elementos em linha, onde você precisa tirar a margin, padding ou border do último (ou o primeiro) elemento para que eles fiquem alinhados corretamente.

<pre class="lang-css">div:first-child {
    margin-left:0;
    padding-left:0;
    border-left:none;
}
</pre>

### Seletores complexos

Olha só que maravilha, o IE7+ já suporta alguns <a href="http://tableless.com.br/seletores-complexos-do-css/" target="_blank">seletores complexos</a> como os descritos abaixo:

<table summary="lista de seletores complexos">
  <tr>
    <th>
      Seletor
    </th>
    
    <th>
      Descrição
    </th>
  </tr>
  
  <tr>
    <td>
      input[type=&#8221;text&#8221;]
    </td>
    
    <td>
      Seleciona o elemento INPUT com o atributo TYPE cujo valor seja exatamente o valor TEXT
    </td>
  </tr>
  
  <tr>
    <td>
      a[title]
    </td>
    
    <td>
      Seleciona o elemento <strong>a</strong> que contenha o atributo <strong>type</strong>não importando o valor.
    </td>
  </tr>
  
  <tr>
    <td>
      a[href$=html]
    </td>
    
    <td>
      Seleciona elementos com atributos cujo seu valor temine com… Por exemplo, você poderia querer selecionar todos os links que apotam para um arquivo .pdf, ou .php etc.
    </td>
  </tr>
  
  <tr>
    <td>
      a[href^=&#8221;http://tableless.com.br/&#8221;]
    </td>
    
    <td>
      Seleciona elementos com o atributos que comecem com… Você pode querer selecionar apenas os links que apontem para um site específico, por exemplo.
    </td>
  </tr>
  
  <tr>
    <td>
      a[title~=&#8221;tableless&#8221;]
    </td>
    
    <td>
      Seleciona os elementos cujo o atributo tenha um valor que seja separado por espaços. No exemplo acima ele seleciona um link que contenha o atributo title e que em seu valor tenha a palavra “tableless” no meio.
    </td>
  </tr>
  
  <tr>
    <td>
      a[hreflang|=&#8221;pt&#8221;]
    </td>
    
    <td>
      Seleciona o elemento <strong>a</strong> cujo o valor do atributo <strong>hreflang</strong> comece com PT. Ou seja valores como “pt-br” serão encontrados.
    </td>
  </tr>
  
  <tr>
    <td>
      a[href=&#8221;http://tableless.com.br/&#8221;]
    </td>
    
    <td>
      Seleciona o elemento <strong>a</strong> cujo o valor do atributo <strong>href</strong> seja exatamente <b>http://tableless.com.br/</b>.
    </td>
  </tr>
  
  <tr>
    <td>
      a[title*=&#8221;artigo&#8221;]
    </td>
    
    <td>
      Seleciona os elementos <strong>a</strong> cujo o valor tenha pelo menos uma ocorrência com a palavra “artigo”.
    </td>
  </tr>
</table>

Todos eles funcionam no IE7 ou superior. Só com estes seletores já economizamos uma penca de código Javascript.

### :first-letter e :first-line

Formatar a primeira letra do parágrafo ou a primeira linha. Coisa linda.

<pre class="lang-css">p:first-letter {font-size:30px; color:red;}
p:first-line {font-weight:bold;}
</pre>

### word-wrap

Essa propriedade é utilíssima. Você já deve ter escrito uma palavra muito grande ou uma URL, que geralmente não tem espaços, o que ocasionou da string ultrapassar a largura do objeto. A propriedade **word-wrap** faz com que essas strings muito grandes quebrem de linha assim que atingirem o limite do objeto.

<pre class="lang-css">p {word-wrap: break-word;}
</pre>

Essa propriedade funciona desde o IE5. O.o

### max-height/width e min-height/width

Essas aqui são essências para produzirmos layouts fluidos e responsivos. Funcionam a partir do IE7.

<pre class="lang-css">div {
    min-width:200px; /** largura mínima **/
    max-width:500px; /** largura máxima **/
    min-height:150px;  /** altura mínima **/
    max-height:300px; /** altura máxima **/
}
</pre>

## Tabela de referência

O MSDN guarda uma <a href="http://msdn.microsoft.com/en-us/library/cc351024(v=vs.85).aspx#elementselectors" target="_blank">tabela de compatibilidade muito completa com propriedades do CSS</a> que os IEs suportam ou não. Vale a pena dar uma olhada e entender melhor o que você já pode usar nativamente do CSS em vez de sair escrevendo loucamente soluções JQuery.