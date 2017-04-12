---
title: JAVA – Tipos de dados
author: Fellipe Filgueiras
type: post
date: 2015-05-11
url: /java-tipos-de-dados/
categories:
  - Geral

---
No Java, existem algumas palavras reservadas para a representação dos tipos de dados básicos que precisam ser manipulados para a construção de programas. Estes tipos de dados são conhecidos como tipos primitivos.

Pode-se dividir os tipos primitivos suportados pelo Java em função da natureza de seu conteúdo. Há quatro tipos primitivos para a representação de números inteiros, dois tipos primitivos para a representação de números fracionários, um tipo primitivo para representação de caracteres e um tipo primitivo para representação dos valores booleanos.

Existem milhares de classes disponíveis na API do Java e todas são tipos de dados, porém uma classe pode armazenar diversos dados ao mesmo tempo em seus atributos, e realizar tarefas através de seus métodos. Um tipo primitivo por outro lado, só armazena um único dado e não contém quaisquer métodos para realizar tarefas.

Já para representar textos o Java não possui um tipo primitivo, ele possui uma classe chamada String, que serve para esse propósito, essa classe pode ser usada de modo semelhante a um tipo primitivo e ainda conta com diversos métodos disponíveis nessa classe para realizar diversas operações com o dado armazenado.

Também existem classes para representar cada um dos tipos primitivos. Sempre que for preciso realizar uma operação mais complexa com algum dado, você poderá armazená-la em um objeto da classe correspondente ao invés de utilizar um tipo primitivo. Assim, poderá fazer uso dos métodos disponíveis nessa classe para realizar diversas operações com o dado armazenado.

**DADOS NUMÉRICOS**

Tipos Inteiros:

<table>
  <tr>
    <td width="64">
      Tipo
    </td>
    
    <td width="142">
      Memória consumida
    </td>
    
    <td width="189">
      Valor Mínimo
    </td>
    
    <td width="187">
      Valor Máximo
    </td>
  </tr>
  
  <tr>
    <td width="64">
      byte
    </td>
    
    <td width="142">
      1 byte
    </td>
    
    <td width="189">
      -128
    </td>
    
    <td width="187">
      127
    </td>
  </tr>
  
  <tr>
    <td width="64">
      short
    </td>
    
    <td width="142">
      2 byte
    </td>
    
    <td width="189">
      -32.768
    </td>
    
    <td width="187">
      32.767
    </td>
  </tr>
  
  <tr>
    <td width="64">
      int
    </td>
    
    <td width="142">
      4 bytes
    </td>
    
    <td width="189">
      -2.147.483.648
    </td>
    
    <td width="187">
      2.147.483.647
    </td>
  </tr>
  
  <tr>
    <td width="64">
      long
    </td>
    
    <td width="142">
      8 bytes
    </td>
    
    <td width="189">
      -9.223.372.036.854.775.808
    </td>
    
    <td width="187">
      9.223.372.036.854.775.807
    </td>
  </tr>
</table>

_Obs: A declaração de um número inteiro longo deve ser feita utilizando-se a letra L como sufixo. _

&nbsp;

Números que podem conter partes fracionárias podem ser representados por dois tipos:

<table>
  <tr>
    <td width="83">
      Tipo
    </td>
    
    <td width="148">
      Memória Consumida
    </td>
    
    <td width="115">
      Valor mínimo
    </td>
    
    <td width="115">
      Valor máximo
    </td>
    
    <td width="115">
      Precisão
    </td>
  </tr>
  
  <tr>
    <td width="83">
      float
    </td>
    
    <td width="148">
      4 bytes
    </td>
    
    <td width="115">
      -3,4028E + 38
    </td>
    
    <td width="115">
      3,4028E + 38
    </td>
    
    <td width="115">
      6 – 7 dígitos
    </td>
  </tr>
  
  <tr>
    <td width="83">
      double
    </td>
    
    <td width="148">
      8 bytes
    </td>
    
    <td width="115">
      -1,7976E + 308
    </td>
    
    <td width="115">
      1,7976E + 308
    </td>
    
    <td width="115">
      15 dígitos
    </td>
  </tr>
</table>

Apesar de o tipo float ocupar metade da memória consumida por um tipo double, ele é menos utilizado. Ele sofre de uma limitação que compromete seu uso em determinadas situações: somente mantém uma precisão decimal entre 6 e 7 dígitos.

_Obs: A declaração de um número como um float, deve ser feito utilizando a letra F como sufixo. _

**DADOS TEXTUAIS**

É possível representar dois tipos de elementos textuais em Java: caracteres e textos. A representação de um caractere solitário é feita pelo tipo char e a representação de textos é feita pela classe String.

Enquanto o tipo de char representa apenas um caractere, a representação de textos deverá ser feita pela classe String. Essa classe pode ser utilizada de forma similar aos tipos primitivos, mais os valores literais desse tipo são transcritos entre aspas e não entre apóstrofos.

**DADOS LÓGICOS**

O tipo lógico é representado, em Java, pelo tipo booleano. Este tipo pode armazenar um de dois valores possíveis: true ou false. Ele é empregado para realizar testes lógicos em conjunto com operadores relacionais e dentro de estruturas de decisão e repetição. O tipo boolean do Java equivale ao tipo boolean do Pascal.

**VARIÁVEIS**

Uma variável representa a unidade básica de armazenamento temporário de dados e compõe-se de um tipo, um identificador e um escopo. Seu objetivo é armazenar um dado de determinado tipo primitivo para que possa ser recuperado e aplicado em operações posteriores.

Para compreender como funciona o uso de variáveis é preciso analisar como elas são criadas, de que modo recebem e armazenam dados e como estes são recuperados. Também é importante entender onde <span style="text-decoration: underline">elas</span> podem ser declaradas e onde podem ser utilizadas, tendo em vista seu escopo.

**CONSTANTES**

As constantes são unidades básicas de armazenamento de dados que não devem sofrer alterações ao longo da execução do aplicativo. O uso de constantes é menos frequente que o uso de variáveis. No entanto, há situações em que elas são requeridas e, por isso, é indispensável entender o que são, para que servem e como podem ser utilizadas.

A declaração de uma constante contém apenas um elemento a mais que a declaração de uma variável: a palavra reservada final. Assim como as variáveis, as constantes compõem-se de um tipo, um identificador e um escopo. Veja a sintaxe que determina como declarar e inicializar uma constante:

**final < tipo > < identificador > = < valor >;**

Mas enquanto a declaração e a inicialização de variáveis podem ser feitas em instruções distintas, toda constante deve ser declarada e inicializada em uma única instrução e, depois disso, não lhe pode ser atribuído outro valor.

Além de tudo que foi dito sobre constantes, é importante observar uma convenção no momento de declará-las: devem ser utilizadas somente letras maiúsculas para seu identificador. A aderência a essa convenção torna o código-fonte muito mais legível, facilitando a distinção entre variáveis e constantes.