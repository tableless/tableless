---
title: Tabelas semânticas
author: Diego Eis
type: post
date: 2008-10-27
url: /tabelas-semanticas/
aktt_tweeted:
  - 1
aktt_notify_twitter:
  - no
tweetbackscheck:
  - 1356471808
shorturls:
  - 'a:3:{s:9:"permalink";s:42:"http://tableless.com.br/tabelas-semanticas";s:7:"tinyurl";s:26:"http://tinyurl.com/3mswgau";s:4:"isgd";s:19:"http://is.gd/ZXl31A";}'
twittercomments:
  - 'a:0:{}'
dsq_thread_id: 503038586
categories:
  - Artigos
  - CSS
  - HTML
  - Técnicas e Práticas
tags:
  - CSS
  - desenvolvimento
  - padroes web
  - Semântica
  - tabelas
  - tableless

---
Você já deve saber que o desenvolvimento utilizando Padrões Web preza pela Semântica no código. Todo código que você escrever deve dar algum significado ao conteúdo. E toda tag sem sua função específica e te ajuda a formar um código mais esperto e legível.
  
Alguns elementos por dependerem de várias tags para ter um funcionamento pleno, acabam sofrendo com o desinteresse dos desenvolvedores em entender melhor os diversos objetos que compoem um determinado elemento. Um caso bastante comum, [além dos Formulários][1], é a formação das TABLES.<!--more-->


  
Normalmente, escrevemos uma tabela mais ou menos assim:

<pre lang="html" line="1"><table>
  <tr>
    <td>
      Produto
    </td>
    
    
    <td>
      Descrição
    </td>
    
    
    <td>
      Valor
    </td>
    
  </tr>
  
  
  <tr>
    <td>
      Tênis
    </td>
    
    
    <td>
      Tênis com amortecedor, tecido vermelho com cadarço preto.
    </td>
    
    
    <td>
      R$350,00
    </td>
    
  </tr>
  
  
  <tr>
    <td>
      Camiseta
    </td>
    
    
    <td>
      Tamanho GG, cor preta e uma estampa nas costas.
    </td>
    
    
    <td>
      R$55,00
    </td>
    
  </tr>
  
  
  <tr>
    <td>
      Calça
    </td>
    
    
    <td>
      Tecido Jeans, azul claro, com botão duplo.
    </td>
    
    
    <td>
      R$105,00
    </td>
    
  </tr>
  
</table>
</pre>

Para nós que enxergamos bem e conseguimos fazer uma breve interpretação de texto, conseguimos entender na maioria das vezes qual o assunto das tabelas na página.

Mas e o Google? E o leitor de tela do cego?

Por isso, a tabela tem algumas tags que ajudam o desenvolvedor a dar mais informação sobre o conteúdo daquela tabela.

Há algumas tags que iremos acrescentar em nossa tabela para dar essa informação extra ao visitante, seja ele ser humano ou robô.

### SUMMARY &#8211; Dizendo do que se trata a tabela

O atributo **summary** é colocado na tag TABLE. Ela serve para indicar do que se trata aquela tabela, dizendo sua utilidade e que tipo de informação está descrevendo.

<pre lang="html" line="1"><table summary="Lista de produtos em promoção">
  </pre>
  
  
  <h3>
    TH &#8211; Table Header
  </h3>
  
  
  <p>
    Considerando o código que colocamos mais acima, há os títulos de células PRODUTO, DESCRIÇÃO e VALOR. Esses títulos, devem ser destacados como título, não apenas modificando seu visual pelo CSS, mas também destacando-os pelo código. Para fazermos isso, iremos utizar a tag TH.
  </p>
  
  
  <p>
    Essa tag irá indicar que tais células são títulos.  O nosso código ficará assim:
  </p>
  
  
  <pre lang="html" line="1">


<table summary="Lista de produtos em promoção">
  <tr>
    <th>
      Produto
    </th>
    
    
    <th>
      Descrição
    </th>
    
    
    <th>
      Valor
    </th>
    
  </tr>
  
  
  <tr>
    <td>
      Tênis
    </td>
    
    
    <td>
      Tênis com amortecedor, tecido vermelho com cadarço preto.
    </td>
    
    
    <td>
      R$350,00
    </td>
    
  </tr>
  
  
  <tr>
    <td>
      Camiseta
    </td>
    
    
    <td>
      Tamanho GG, cor preta e uma estampa nas costas.
    </td>
    
    
    <td>
      R$55,00
    </td>
    
  </tr>
  
  
  <tr>
    <td>
      Calça
    </td>
    
    
    <td>
      Tecido Jeans, azul claro, com botão duplo.
    </td>
    
    
    <td>
      R$105,00
    </td>
    
  </tr>
  
</table>
</pre>
  
  
  <h3>
    THEAD &#8211; Cabeçalho da Tabela
  </h3>
  
  
  <p>
    Normalmente as tabelas tem sempre uma linha de títulos, como a nossa tabela acima. Precisamos informar então, que essa linha é um cabeçalho, que contém os títilos das colunas ou linhas. Para isso, envolveremos a TR que contém as THs com a tag THEAD. Nosso código ficará dessa forma:
  </p>
  
  
  <pre lang="html" line="1">


<table summary="Lista de produtos em promoção">
  
  
  
  <tr>
    <th>
      Produto
    </th>
    
    
    <th>
      Descrição
    </th>
    
    
    <th>
      Valor
    </th>
    
  </tr>
  
  
  
  <tr>
    <td>
      Tênis
    </td>
    
    
    <td>
      Tênis com amortecedor, tecido vermelho com cadarço preto.
    </td>
    
    
    <td>
      R$350,00
    </td>
    
  </tr>
  
  
  <tr>
    <td>
      Camiseta
    </td>
    
    
    <td>
      Tamanho GG, cor preta e uma estampa nas costas.
    </td>
    
    
    <td>
      R$55,00
    </td>
    
  </tr>
  
  
  <tr>
    <td>
      Calça
    </td>
    
    
    <td>
      Tecido Jeans, azul claro, com botão duplo.
    </td>
    
    
    <td>
      R$105,00
    </td>
    
  </tr>
  
</table>
</pre>
  
  
  <h3>
    TFOOT &#8211; Indicando o rodapé da tabela
  </h3>
  
  
  <p>
    Logo após o THEAD, iremos indicar quais informações irão no rodapé do documento, utilizando a tag <strong>TFOOT</strong>. Aqui, iremos colocar as mesmas informações do THEAD, supondo que a tabela é muito grande e queremos que o usuário, ao chegar no rodape, não se perca com a identificação das colunas. Nosso código fica assim:
  </p>
  
  
  <pre lang="html" line="1">


<table summary="Lista de produtos em promoção">
  
  
  
  <tr>
    <th>
      Produto
    </th>
    
    
    <th>
      Descrição
    </th>
    
    
    <th>
      Valor
    </th>
    
  </tr>
  
  
  
  
  <tr>
    <th>
      Produto
    </th>
    
    
    <th>
      Descrição
    </th>
    
    
    <th>
      Valor
    </th>
    
  </tr>
  
  
  
  <tr>
    <td>
      Tênis
    </td>
    
    
    <td>
      Tênis com amortecedor, tecido vermelho com cadarço preto.
    </td>
    
    
    <td>
      R$350,00
    </td>
    
  </tr>
  
  
  <tr>
    <td>
      Camiseta
    </td>
    
    
    <td>
      Tamanho GG, cor preta e uma estampa nas costas.
    </td>
    
    
    <td>
      R$55,00
    </td>
    
  </tr>
  
  
  <tr>
    <td>
      Calça
    </td>
    
    
    <td>
      Tecido Jeans, azul claro, com botão duplo.
    </td>
    
    
    <td>
      R$105,00
    </td>
    
  </tr>
  
</table>
</pre>
  
  
  <h3>
    TBODY &#8211; Indicando o corpo da tabela
  </h3>
  
  
  <p>
    Se há um cabeçalho e um rodapé na tabela, é mais do que normal haver um BODY, apresentando as informações que de fato interessam ao usuário.<br />
    O <strong>TBODY</strong> deve ir logo após a tag TFOOT. Sinceramente, não sei porque a tag TFOOT não vem após a TBODY, já que é o código de Rodapé. Se você souber, por favor, me diga!
  </p>
  
  
  <p>
    Nosso código fica dessa forma:
  </p>
  
  
  <pre lang="html" line="1">


<table summary="Lista de produtos em promoção">
  
  
  
  <tr>
    <th>
      Produto
    </th>
    
    
    <th>
      Descrição
    </th>
    
    
    <th>
      Valor
    </th>
    
  </tr>
  
  
  
  
  <tr>
    <th>
      Produto
    </th>
    
    
    <th>
      Descrição
    </th>
    
    
    <th>
      Valor
    </th>
    
  </tr>
  
  
  
  
  <tr>
    <td>
      Tênis
    </td>
    
    
    <td>
      Tênis com amortecedor, tecido vermelho com cadarço preto.
    </td>
    
    
    <td>
      R$350,00
    </td>
    
  </tr>
  
  
  <tr>
    <td>
      Camiseta
    </td>
    
    
    <td>
      Tamanho GG, cor preta e uma estampa nas costas.
    </td>
    
    
    <td>
      R$55,00
    </td>
    
  </tr>
  
  
  <tr>
    <td>
      Calça
    </td>
    
    
    <td>
      Tecido Jeans, azul claro, com botão duplo.
    </td>
    
    
    <td>
      R$105,00
    </td>
    
  </tr>
  
  
</table>
</pre>
  
  
  <h3>
    CAPTION &#8211; Título do Cabeçalho
  </h3>
  
  
  <p>
    A tag <strong>CAPTION</strong> define um título para o cabeçalho da tabela. Esse título vai apresentar a tabela para o usuário. Ele deve ser colocado logo antes da tag THEAD e logo após tag TABLE.
  </p>
  
  
  <pre lang="html" line="1">


<table summary="Lista de produtos em promoção">
  &lt;caption>Produtos em Promoção&lt;/caption>
  
  
  
  <tr>
    <th>
      Produto
    </th>
    
    
    <th>
      Descrição
    </th>
    
    
    <th>
      Valor
    </th>
    
  </tr>
  
  
  
  
  <tr>
    <th>
      Produto
    </th>
    
    
    <th>
      Descrição
    </th>
    
    
    <th>
      Valor
    </th>
    
  </tr>
  
  
  
  
  <tr>
    <td>
      Tênis
    </td>
    
    
    <td>
      Tênis com amortecedor, tecido vermelho com cadarço preto.
    </td>
    
    
    <td>
      R$350,00
    </td>
    
  </tr>
  
  
  <tr>
    <td>
      Camiseta
    </td>
    
    
    <td>
      Tamanho GG, cor preta e uma estampa nas costas.
    </td>
    
    
    <td>
      R$55,00
    </td>
    
  </tr>
  
  
  <tr>
    <td>
      Calça
    </td>
    
    
    <td>
      Tecido Jeans, azul claro, com botão duplo.
    </td>
    
    
    <td>
      R$105,00
    </td>
    
  </tr>
  
  
</table>
</pre>
  
  
  <p>
    Já com essas tags diferenciadas, o trabalho que teríamos para formatar o cabeçalho, título e conteúdo da tabela ficou mais leve. Em vez de colocar class em tudo quanto é TR para diferenciar as partes da tabela, conseguimos formatar cada um desses grupos sem encostar no código HTML. Claro, que se você quiser fazer algo mais rebuscado, a modificação do código HTML será inevitável. Mas, com esse pouco código que escrevemos, já procrastinamos essa necessidade.
  </p>

 [1]: http://tableless.com.br/formulario-basico-em-8-minutos