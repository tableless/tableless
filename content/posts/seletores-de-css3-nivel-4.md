---
title: Seletores de CSS3 nível 4
author: Dani Guerrato
type: post
date: 2013-01-29
excerpt: Entenda como funcionarão os seletores de nível 4 do CSS. Mudanças drásticas para salver nossas vidas.
url: /seletores-de-css3-nivel-4/
dsq_thread_id: 1050089169
categories:
  - Código
  - CSS
  - CSS3
tags:
  - 2013
  - CSS
  - w3c

---
Desde setembro de 2011 a W3C vem trabalhando nos seletores de **CSS nível 4**. Calma! Isso não significa que eles estão criando o **CSS4**, já que nem finalizaram o **CSS3** ainda&#8230; Apenas que um novo pacote de pseudo-classes e classes que podem substituir as atuais, ou expandir o seu uso. Claro que, por ser algo recente, não são todos os browsers que dão suporte&#8230; Mas é bom tomar conhecimento. Afinal, é sempre bom estar um passo a frente do resto do mundo.

Como este conteúdo ainda está em discussão é bom sempre dar uma checada na documentação oficial da W3C de tempos e tempos para acompanhar o andamento do rascunho.

Vamos conhecer de perto alguns dos novos seletores de nível 4.

## !E

Este super seletor determina qual será o elemento estilizado em relação ao seu elemento filho. Pode ser usado em qualquer lugar. Ele irá marcar exatamente qual elemento nós queremos selecionar.

<pre class="lang-css">div.menu !ul li.selecionada { … }</pre>

Nesta declaração estou estilizando apenas a UL que está dentro da div &#8220;menu&#8221; e possui uma LI de classe &#8220;selecionada&#8221;. Ou seja, caso exista outra UL dentro da DIV de classe &#8220;menu&#8221; que não possua a LI &#8220;.selecionada&#8221;, esta UL não será estilizada.

<pre class="lang-css">ul &gt; !li &gt; p { … }</pre>

Aqui eu seleciono apenas as LI que tem um P como filho

<pre class="lang-css">!div ul.submenu { … }</pre>

Agora estou selecionando apenas as DIVs que tem uma UL com a classe submenu.

## Pseudo-Classe de Localização :local-link e :any-link

Estas pseudo-classes servem para identificar se os links são internos, ou seja, levam para o mesmo site, ou externos.

A **pseudo-classe :any-link** vai aplicar estilos a qualquer âncora do site, a:local-link seleciona os elementos que estão dentro do mesmo diretório e :local-link(0) vale para links dentro do mesmo host.
  
Uma forma de uso interessante é combinar os seletores, criando assim alvos mais complexos e precisos. É possível, por exemplo, juntar :any-link com a pseudo-classe :not() e criar um seletor apenas para links externos.

<pre class="lang-css">a:not(:local-link) {...}</pre>

## :not()

Por falar na pseudo-classe :not, já presente em versões mais antigas do CSS3, a novidade é que agora ela pode receber mais de um seletor.

<pre class="lang-css">div :not(a, ul) { … }</pre>

No exemplo acima, ele seleciona todos os elementos da DIV, menos o  <a>e o</a>

## Pseudo-classe linguísticas

#### :lang

Este seletor nos permite estilizar apenas os elementos de uma determinada língua. No exemplo abaixo selecionamos apenas páginas html em português brasileiro (pt-br).

<pre class="lang-css">html:lang(pt-br)</pre>

Podemos ainda combinar esta pseudo-classe com outros seletores. No exemplo abaixo selecionamos apenas citações em Alemão (de).

<pre class="lang-css">:lang(de) &gt; q</pre>

Obviamente é necessário, primeiramente, que a marcação de linguagem seja realizada no código html.

#### :dir()

Esta pseudo-classe identifica a direção de leitura do texto, normalmente aplicada pela classe dir no HTML ou direction no CSS.

Na pseudo classe :dir(rtl) iremos selecionar apenas os textos que estão com a sua leitura definida da direita para esquerda (rtl significa Right to Left) e podemos usar o :dir(ltr) para selecionar textos com a leitura da esquerda para direita.

Como estamos no ocidente e a maior parte dos textos (pra não dizer todos) são lidos da esquerda para a direita, acredito que isso pode ficar meio obscuro para nós. Mas, para o oriente ou países onde a leitura do texto se dá de maneira invertida parece ser uma pseudo-classe bem útil.

#### :matches()

Esta ótima pseudo-classe poupa muitas linhas de código. Ela seleciona vários elementos ao mesmo tempo. Por exemplo, podemos selecionar todos e dentro de uma mesma div.artigo.

Atualmente, nós fazemos assim:

<pre class="lang-css">div.artigo h1, div.artigo h2 { … }</pre>

Ou até mesmo escrevemos isso em linhas diferentes. Mas, com esta pseudo-classe podemos declarar tudo isso de uma vez:<

<pre class="lang-css">div.artigo :matches(h1, h2) { … }</pre>

Pronto! Selecionamos todas as H1 e H2 da div.artigo. Bem fácil e rápido.

## Pseudo-classes de tempo dimensional

São pseudo-classes que selecionam o elemento presente, passado ou futuro em um canvas de tempo multidimensional. O que este conjunto de pseudo-classes faz é te deixar controlar o elemento ativo atualmente, o que acabou de ser ativado e o próximo a ser ativado em uma timeline de renderização. Isto pode ser útil no caso de um software de leitura de tela, por exemplo.

(E não, infelizmente isto não te da super-poderes para alterar o tempo e o espaço&#8230;)

A pseudo-classe :current seleciona o elemento que está sendo lido no momento. Por exemplo:

<pre class="lang-css">:current(p, li) { … }</pre>

No código acima, estamos selecionando o parágrafo ou a lista que está sendo lida atualmente.

Sabendo disso, temos também a pseudo-classe :past e a :future que selecionam elementos que vem antes e depois da pseudo-classe :current

## Confira a tabela de seletores nível 4

Abaixo segue uma tabela completa com todos os seletores novos. A versão base deste artigo é a de 16 de janeiro de 2013.

**Obs. 1** &#8211; Quando existirem mais de dois números para o item &#8220;nível&#8221; é por que não se trata de um novo seletor e sim de uma modificação estrututural de um seletor mais antigo.

**Obs. 2** &#8211; &#8220;Foo&#8221; e &#8220;bar&#8221; são variável metasintáticas. Isto é um termo fresco pra dizer que não significam nada na realidade. Entenda por uma palavra qualquer a sua escolha que serve apenas de exemplo para o conteúdo real.

**Obs. 3** &#8211; Substitua E por qualquer elemento da sua escolha. S, S1 e S2 por sua vez são os seletores que você deseja aplicar.

**Obs. 4** &#8211; Não existe observação 4. 🙂

<table>
  <tr>
    <td>
      <strong>Padrão</strong>
    </td>
    
    <td>
      <strong>Significado</strong>
    </td>
    
    <td>
      <strong>Tipo</strong>
    </td>
    
    <td>
      <strong>Nível</strong>
    </td>
  </tr>
  
  <tr>
    <td>
      E:not(s1, s2)
    </td>
    
    <td>
      um elemento E que não corresponde ao seletor composto s1 e s2
    </td>
    
    <td>
      <a href="http://dev.w3.org/csswg/selectors4/#negation">Negation pseudo-class</a>
    </td>
    
    <td>
      3/4
    </td>
  </tr>
  
  <tr>
    <td>
      E:matches(s1, s2)
    </td>
    
    <td>
      um elemento E que corresponde ao seletor composto s1 e / ou s2
    </td>
    
    <td>
      <a href="http://dev.w3.org/csswg/selectors4/#matches">Matches-any pseudo-class</a>
    </td>
    
    <td>
      4
    </td>
  </tr>
  
  <tr>
    <td>
      E[foo=&#8221;bar&#8221; i]
    </td>
    
    <td>
      um elemento E cujo valor do atributo foo é exatamente igual ao do atributo bar em qualquer variação ASCII. (case-insensitive).
    </td>
    
    <td>
      <a href="http://dev.w3.org/csswg/selectors4/#attribute-case">Attribute selectors: Case-sensitivity</a>
    </td>
    
    <td>
      4
    </td>
  </tr>
  
  <tr>
    <td>
      E:dir(ltr)
    </td>
    
    <td>
      um elemento do tipo E na direção de leitura da esquerda para a direita
    </td>
    
    <td>
      <a href="http://dev.w3.org/csswg/selectors4/#dir-pseudo">The :dir() pseudo-class</a>
    </td>
    
    <td>
      4
    </td>
  </tr>
  
  <tr>
    <td>
      E:lang(zh, *-hant)
    </td>
    
    <td>
      um elemento do tipo E marcado como chinês ou escrito com caracteres chineses (pode ser susbtituido por qualquer outra linguagem)
    </td>
    
    <td>
      <a href="http://dev.w3.org/csswg/selectors4/#lang-pseudo">The :lang() pseudo-class</a>
    </td>
    
    <td>
      2/4
    </td>
  </tr>
  
  <tr>
    <td>
      E:any-link
    </td>
    
    <td>
      um elemento E que atua como âncora fonte de um hyperlink
    </td>
    
    <td>
      <a href="http://dev.w3.org/csswg/selectors4/#any-link-pseudo">The hyperlink pseudo-class</a>
    </td>
    
    <td>
      4
    </td>
  </tr>
  
  <tr>
    <td>
      E:local-link
    </td>
    
    <td>
      um elemento E que atua como âncora fonte de um hyperlink no documento atual
    </td>
    
    <td>
      <a href="http://dev.w3.org/csswg/selectors4/#local-pseudo">The local link pseudo-class</a>
    </td>
    
    <td>
      4
    </td>
  </tr>
  
  <tr>
    <td>
      E:local-link(0)
    </td>
    
    <td>
      um elemento E que atua como âncora fonte de um hyperlink no domínio atual
    </td>
    
    <td>
      <a href="http://dev.w3.org/csswg/selectors4/#local-pseudo">The local link pseudo-class</a>
    </td>
    
    <td>
      4
    </td>
  </tr>
  
  <tr>
    <td>
      E:scope
    </td>
    
    <td>
      um elemento E dentro de uma referência contextual. Se a referência estiver vazia :scope corresponde a :root
    </td>
    
    <td>
      <a href="http://dev.w3.org/csswg/selectors4/#scope-pseudo">The scope pseudo-class</a>
    </td>
    
    <td>
      4
    </td>
  </tr>
  
  <tr>
    <td>
      E:current
    </td>
    
    <td>
      um elemento E localizado no presente em um canvas de tempo dimensional
    </td>
    
    <td>
      <a href="http://dev.w3.org/csswg/selectors4/#time-pseudos">Time-dimensional Pseudo-classes</a>
    </td>
    
    <td>
      4
    </td>
  </tr>
  
  <tr>
    <td>
      E:current(s)
    </td>
    
    <td>
      um elemento E :current que corresponde ao seletor s
    </td>
    
    <td>
      <a href="http://dev.w3.org/csswg/selectors4/#time-pseudos">Time-dimensional Pseudo-classes</a>
    </td>
    
    <td>
      4
    </td>
  </tr>
  
  <tr>
    <td>
      E:past
    </td>
    
    <td>
      um elemento E localizado no passado em um canvas de tempo dimensional
    </td>
    
    <td>
      <a href="http://dev.w3.org/csswg/selectors4/#time-pseudos">Time-dimensional Pseudo-classes</a>
    </td>
    
    <td>
      4
    </td>
  </tr>
  
  <tr>
    <td>
      E:future
    </td>
    
    <td>
      um elemento E localizado no futuro em um canvas de tempo dimensional
    </td>
    
    <td>
      <a href="http://dev.w3.org/csswg/selectors4/#time-pseudos">Time-dimensional Pseudo-classes</a>
    </td>
    
    <td>
      4
    </td>
  </tr>
  
  <tr>
    <td>
      E:indeterminate
    </td>
    
    <td>
      um elemento E que esta em um estado indeterminado (não corresponde a checked ou unchecked)
    </td>
    
    <td>
      <a href="http://dev.w3.org/csswg/selectors4/#indeterminate">The indeterminate-value pseudo-class</a>
    </td>
    
    <td>
      4
    </td>
  </tr>
  
  <tr>
    <td>
      E:default
    </td>
    
    <td>
      um elemento da user interface E em seu estado padrão
    </td>
    
    <td>
      <a href="http://dev.w3.org/csswg/selectors4/#default-pseudo">The default option pseudo-class :default</a>
    </td>
    
    <td>
      3-UI/4
    </td>
  </tr>
  
  <tr>
    <td>
      E:in-range
    </td>
    
    <td>
      um elemento da user interface E dentro do seu alcance
    </td>
    
    <td>
      <a href="http://dev.w3.org/csswg/selectors4/#range-pseudos">The validity pseudo-classes</a>
    </td>
    
    <td>
      3-UI/4
    </td>
  </tr>
  
  <tr>
    <td>
      E:out-of-range
    </td>
    
    <td>
      um elemento da user interface E fora do seu alcance (como a letra Z em um menu com as escolhas A, B e C)
    </td>
    
    <td>
      <a href="http://dev.w3.org/csswg/selectors4/#range-pseudos">The validity pseudo-classes</a>
    </td>
    
    <td>
      3-UI/4
    </td>
  </tr>
  
  <tr>
    <td>
      E:required
    </td>
    
    <td>
      um elemento de formulário E obrigatório
    </td>
    
    <td>
      <a href="http://dev.w3.org/csswg/selectors4/#opt-pseudos">The optionality pseudo-classes</a>
    </td>
    
    <td>
      3-UI/4
    </td>
  </tr>
  
  <tr>
    <td>
      E:optional
    </td>
    
    <td>
      um elemento de formulário E opcional
    </td>
    
    <td>
      <a href="http://dev.w3.org/csswg/selectors4/#opt-pseudos">The optionality pseudo-classes</a>
    </td>
    
    <td>
      3-UI/4
    </td>
  </tr>
  
  <tr>
    <td>
      E:read-only
    </td>
    
    <td>
      um elemento da user interface E que pode ser apenas visualizado pelo usuário
    </td>
    
    <td>
      <a href="http://dev.w3.org/csswg/selectors4/#rw-pseudos">The mutability pseudo-classes</a>
    </td>
    
    <td>
      3-UI/4
    </td>
  </tr>
  
  <tr>
    <td>
      E:read-write
    </td>
    
    <td>
      um elemento da user interface E que pode ser alterado pelo usuário
    </td>
    
    <td>
      <a href="http://dev.w3.org/csswg/selectors4/#rw-pseudos">The mutability pseudo-classes</a>
    </td>
    
    <td>
      3-UI/4
    </td>
  </tr>
  
  <tr>
    <td>
      E:nth-match(n of <a href="http://dev.w3.org/csswg/selectors4/#selector">selector</a>)
    </td>
    
    <td>
      um elemento E que corresponde ao n-th sibling do seletor
    </td>
    
    <td>
      <a href="http://dev.w3.org/csswg/selectors4/#structural-pseudos">Structural pseudo-classes</a>
    </td>
    
    <td>
      4
    </td>
  </tr>
  
  <tr>
    <td>
      E:nth-last-match(nof <a href="http://dev.w3.org/csswg/selectors4/#selector">selector</a>)
    </td>
    
    <td>
      um elemento E que corresponde ao n-th sibling do seletor, contado a partir da última correspondência
    </td>
    
    <td>
      <a href="http://dev.w3.org/csswg/selectors4/#structural-pseudos">Structural pseudo-classes</a>
    </td>
    
    <td>
      4
    </td>
  </tr>
  
  <tr>
    <td>
      E:column(<a href="http://dev.w3.org/csswg/selectors4/#selector">selector</a>)
    </td>
    
    <td>
      um elemento E que representa uma célula em um grid/tabela pertencente a uma coluna correspondente ao seletor
    </td>
    
    <td>
      <a href="http://dev.w3.org/csswg/selectors4/#table-pseudos">Grid-Structural pseudo-classes</a>
    </td>
    
    <td>
      4
    </td>
  </tr>
  
  <tr>
    <td>
      E:nth-column(n)
    </td>
    
    <td>
      um elemento E que representa um célula pertencente a coluna de número nth em um grid/tabela
    </td>
    
    <td>
      <a href="http://dev.w3.org/csswg/selectors4/#table-pseudos">Grid-Structural pseudo-classes</a>
    </td>
    
    <td>
      4
    </td>
  </tr>
  
  <tr>
    <td>
      E:nth-last-column(n)
    </td>
    
    <td>
      um elemento E que representa uma céula pertencente a coluna de número nth em um grid/tabela, contando a partir da última correspondência
    </td>
    
    <td>
      <a href="http://dev.w3.org/csswg/selectors4/#table-pseudos">Grid-Structural pseudo-classes</a>
    </td>
    
    <td>
      4
    </td>
  </tr>
  
  <tr>
    <td>
      E /foo/ F
    </td>
    
    <td>
      um elemento F referenciado com ID através do atributo foo de um elemento E
    </td>
    
    <td>
      <a href="http://dev.w3.org/csswg/selectors4/#idref-combinators">Reference combinator</a>
    </td>
    
    <td>
      4
    </td>
  </tr>
  
  <tr>
    <td>
      E! > F
    </td>
    
    <td>
      um elemento E parent de um elemento F
    </td>
    
    <td>
      <a href="http://dev.w3.org/csswg/selectors4/#subject">Determining the subject of a selector</a> +<a href="http://dev.w3.org/csswg/selectors4/#child-combinators">Child combinator</a>
    </td>
    
    <td>
      4
    </td>
  </tr>
</table>

## Existe todo o futuro pela frente!

Vale lembrar que, embora tenha muita gente chamando isso de CSS4, estamos falando de CSS3. O que acontece é que o CSS3 está dividido em módulos, e este é o módulo nível 4.

Estes novos seletores de CSS3 ainda estão em fase inicial. Ou seja, ainda é um rascunho e muitas classes ainda não são suportadas pelos browsers atuais (se você quiser conferir quais já estão disponíveis para o seu navegador faça o [teste aqui][1])&#8230; Eu particularmente já estou ansiosa para utilizar alguns destes elementos. Agora o que nos resta é torcer para os browsers implementarem suporte rapidamente para testarmos na prática a utilidade cada um. É claro que muita coisa ainda pode ser modificada, mas quem estiver se preparando desde agora certamente estará ajudando a sedimentar o conhecimento do futuro.

Saiba mais:
  
[W3C][2]
  
[CSS4 Selectors][3]

 [1]: http://css4-selectors.com/browser-selector-test/
 [2]: http://dev.w3.org/csswg/selectors4/
 [3]: http://css4-selectors.com/