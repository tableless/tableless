---
title: Entendendo os valores ‘initial’ e ‘inherit’ do CSS
author: João Guilherme
type: post
date: 2015-07-21
excerpt: "Qual a razão da existência dos valores 'initial' e 'inherit' na maioria dos atributos do CSS? Suas propriedades tem bastante significado, confira e entenda."
url: /entendendo-os-valores-initial-e-inherit-do-css/
categories:
  - Browsers
  - CSS
  - CSS3
  - Técnicas e Práticas
  - Traduções
tags:
  - CSS

---
Algum tempo atrás, se alguém me perguntasse qual a diferença entre os valores `initial` e `inherit` do CSS eu responderia:

_&#8211; Existe alguma diferença?_

Trabalho com CSS por mais de 5 anos e de algum jeito faltou entender o significado do que exatamente `initial` é e faz. Pode chamar isso de ignorância, preguiça, burrice ou sorte, mas nunca pensei em olhar ao redor e tentar entender fixamente o comportamento que `inherit` poderia fazer. Foi quando descobri, inclusive, que `inherit` poderia ser substituído pelo `initial`.

Neste artigo, pretendo compartilhar o que aprendi repassando o aprendizado a quem interessar e tiver necessidade.

### O que `initial` significa?

A especificação oficial nos ajuda a entender a diferença entre as _keywords_ `initial` e `inherit`.

  * <a href="http://dev.w3.org/csswg/css-cascade/#initial" target="_blank">Initial <em>keyword</em></a>: Se o valor no CSS da propriedade é &#8216;`initial`&#8216;, o valor inicial da propriedade se torna o oficial.
  * <a href="http://dev.w3.org/csswg/css-cascade/#initial-value" target="_blank">Initial <em>value</em></a>: Cada propriedade tem um valor inicial, estipulado na tabela de definição da propriedade do navegador. Se o valor da propriedade do objeto não tem um valor herdado e a cascata não resulta em um valor oficial, o valor especificado da propriedade é o `initial`.

Isto significa que, se o valor `initial `for definido aqui:

<pre class="lang-css">.modulo {
	color: initial;
}
</pre>

O valor provavelmente retornará **preto**, caso a cor padrão do navegador seja preta para tal propriedade.

### Quão diferente `initial` é de `inherit`?

Se você deduz que isto é <a href="http://www.w3.org/TR/CSS2/cascade.html#value-def-inherit" target="_blank">questão de herança</a>, você está certo.

Mas `initial` e `inherit` são diferentes quando entendemos que o `inherit` checa se existem outras propriedades no pai que poderão ser utilizadas ou afetadas, antes que seja atribuído o valor inicial. Antes que o navegador decida renderizar o valor herdado, ele deve varrer a cascata de valores acima da propriedade definida e avaliar o possível valor inicial do elemento. Vai depender do que é atribuído no pai mais próximo do elemento:

[<img class="alignnone wp-image-50137 size-full" src="http://tableless.com.br/uploads/2015/07/example1-initial-inherit-joao-guilherme.png" alt="" width="727" height="285" />][1]

`H1` está herdando o valor da cor do elemento mais próximo, encontrando a propriedade incluída no elemento `body`.

[<img class="alignnone wp-image-50138 size-full" src="http://tableless.com.br/uploads/2015/07/example2-initial-inherit-joao-guilherme.png" alt="" width="727" height="285" />][2]

Desta vez, utilizando o valor inicial, `H1` ignora o valor que poderia ser herdado do elemento `body`, e mantém o valor atribuído pelo navegador, isto é, a raiz responsável por renderizar o HTML.

[Exemplo de inherit e initial no CodePen][3].

No exemplo acima, as propriedades na caixa da esquerda são todas definidas e herdadas da classe `.modulo`, já que a caixa é filha do _modulo_ anteriormente estilizado. Na caixa da direita, as propriedades são atribuídas de acordo com o padrão do navegador, que, por sua vez, é _&#8220;zerado&#8221;_ através do atributo inserido.

### Quando usar  `initial`

Podemos pensar em `initial` como um jeito de _&#8220;zerar&#8221;_ o conteúdo. Para não confundir abstrações e heranças, usar `initial` é uma maneira de limpar os atributos e propriedades do elemento, deixando mais claro a volta do elemento ao seu estilo natural do estado de início.

`Initial` não é uma bala de prata para _resets_. Valores iniciais ainda são sujeitos aos padrões dos navegadores, e que sabemos, podem [variar de navegador para navegador.][4] Se você usa _CSS resets_, serão utilizados os valores iniciais.

Por exemplo, para destruir completamente todos os estilos herdados de um elemento, você pode usar `initial;` para ter certeza que o elemento copia uma determinada propriedade do seu elemento pai mais próximo, use `inherit` .

## Exemplo prático

Recentemente, tive um problema em um projeto ao usar o elemento `video` 100% em relação ao tamanho do navegador. Ele deveria encaixar tanto na largura como na altura da _div_ de uma _single page_.

Na primeira versão abaixo, a propriedade **_object-fit_** foi definida com o valor **_contain_**, que era o valor padrão e específico para este elemento no Chrome.

<img class="alignnone" src="http://tableless.com.br/uploads/2015/07/BJLyIvi.jpg" alt="Exemplo do uso do elemento video no Chrome com a propriedade initial" width="1234" height="585" />

Já neste segundo exemplo, deixamos o valor definido como `initial`: ele preencheu o espaço que faltava para o vídeo ocupar 100% em relação à página, utilizando o valor inicial do navegador:

<img class="alignnone" src="http://tableless.com.br/uploads/2015/07/e8owgRc1.png" alt="Exemplo do uso do elemento video no Chrome sem a propriedade initial" width="1200" height="583" />

### O suporte dos browsers

Segundo os dados do <a href="https://developer.mozilla.org/pt-BR/#" target="_blank">MDN</a>, segue uma tabela simplificada de suporte às propriedades `initial` e `inherit`. Observe a ausência do IE para suporte ao `initial:`

  * **<a href="https://developer.mozilla.org/en-US/docs/Web/CSS/initial/" target="_blank">initial</a>**

<table class="tb-table browser-support-table" style="height: 62px;" width="739">
  <tr>
    <th class="chrome">
      Chrome
    </th>
    
    <th class="safari">
      Safari
    </th>
    
    <th class="firefox">
      Firefox
    </th>
    
    <th class="opera">
      Opera
    </th>
    
    <th class="ie">
      IE
    </th>
    
    <th class="android">
      Android
    </th>
    
    <th class="iOS">
      iOS
    </th>
  </tr>
  
  <tr>
    <td class="yep">
      Sim
    </td>
    
    <td class="yep">
      Sim
    </td>
    
    <td class="yep">
      19 up
    </td>
    
    <td class="yep">
      15 up
    </td>
    
    <td class="nope">
      <span style="color: #ff0000;">Não</span>
    </td>
    
    <td class="yep">
      Sim
    </td>
    
    <td class="yep">
      Sim
    </td>
  </tr>
</table>

  * **<a href="https://developer.mozilla.org/en-US/docs/Web/CSS/inherit" target="_blank">inherit</a>**

<table class="tb-table browser-support-table" style="height: 62px;" width="739">
  <tr>
    <th class="chrome">
      Chrome
    </th>
    
    <th class="safari">
      Safari
    </th>
    
    <th class="firefox">
      Firefox
    </th>
    
    <th class="opera">
      Opera
    </th>
    
    <th class="ie">
      IE
    </th>
    
    <th class="android">
      Android
    </th>
    
    <th class="iOS">
      iOS
    </th>
  </tr>
  
  <tr>
    <td class="yep">
      Claro
    </td>
    
    <td class="yep">
      Sim
    </td>
    
    <td class="yep">
      Sim
    </td>
    
    <td class="yep">
      4 up
    </td>
    
    <td class="nope">
      8 up
    </td>
    
    <td class="yep">
      Sim
    </td>
    
    <td class="yep">
      Sim
    </td>
  </tr>
</table>

<p style="font-size: 12px;">
  Texto traduzido e adaptado da fonte: <a href="https://css-tricks.com/getting-acquainted-with-initial/">Getting acquainted with initial</a>
</p>

 [1]: http://tableless.com.br/uploads/2015/07/example1-initial-inherit-joao-guilherme.png
 [2]: http://tableless.com.br/uploads/2015/07/example2-initial-inherit-joao-guilherme.png
 [3]: http://codepen.io/guicheffeR/pen/jPxKqQ
 [4]: http://tableless.com.br/querido-usuario-atualize-seu-browser/