---
title: Charsets e Encodes – Tabelas de caracteres
authors: Diego Eis
type: post
date: 2008-03-31
excerpt: Entenda como funciona a tabela de caracteres e encodes no HTML.
url: /charsets-e-encodes-tabelas-de-caracteres/
aktt_notify_twitter:
  - no
tweetbackscheck:
  - 1356404155
shorturls:
  - 'a:3:{s:9:"permalink";s:64:"https://tableless.com.br/charsets-e-encodes-tabelas-de-caracteres";s:7:"tinyurl";s:26:"https://tinyurl.com/3hyyf8w";s:4:"isgd";s:19:"https://is.gd/mUlA6o";}'
twittercomments:
  - 'a:0:{}'
dsq_thread_id: 503037999
categories:
  - Artigos
  - HTML
  - Técnicas e Práticas
tags:
  - 2008
  - Browsers
  - charsets
  - desenvolvimento web
  - encodes
  - metatags
  - utf
  - xhtml
  - xml

---
Quando você escreve um documento HTML (ou qualquer outra linguagem baseada em SGML) é necessário que especifiquemos o Charset utilizado. O **Charset é o conjunto de caracteres utilizados para escrever o documento**. Um jogo de caracteres consiste em ter 1) repertório com caracteres e 2) uma posição de referência para cada um dos caracteres no repertório. Cada caractere é identificado e localizado por este código de posição. Por exemplo, na tabela ASCII, as posições 65, 66 e 67 se referem às letras A, B e C respectivamente.<!--more--> Abaixo, veja a tabela de caracteres ASCII:

<table summary="tabela ASCII" width="100%">
  <tr>
    <td>
      <ul>
        <li>
          00 &#8211; (NUL)
        </li>
        <li>
          01 &#8211; (SOH)
        </li>
        <li>
          02 &#8211; (STX)
        </li>
        <li>
          03 &#8211; (ETX)
        </li>
        <li>
          04 &#8211; (EOT)
        </li>
        <li>
          05 &#8211; (ENQ)
        </li>
        <li>
          06 &#8211; (ACK)
        </li>
        <li>
          07 &#8211; (BEL)
        </li>
        <li>
          08 &#8211; (BS)
        </li>
        <li>
          09 &#8211; (HT)
        </li>
        <li>
          10 &#8211; (LF)
        </li>
        <li>
          11 &#8211; (VT)
        </li>
        <li>
          12 &#8211; (FF)
        </li>
        <li>
          13 &#8211; (CR)
        </li>
        <li>
          14 &#8211; (SO)
        </li>
        <li>
          15 &#8211; (SI)
        </li>
        <li>
          16 &#8211; (DLE)
        </li>
        <li>
          17 &#8211; (D1)
        </li>
        <li>
          18 &#8211; (D2)
        </li>
        <li>
          19 &#8211; (D3)
        </li>
        <li>
          20 &#8211; (D4)
        </li>
        <li>
          21 &#8211; (NAK)
        </li>
        <li>
          22 &#8211; (SYN)
        </li>
        <li>
          23 &#8211; (ETB)
        </li>
        <li>
          24 &#8211; (CAN)
        </li>
        <li>
          25 &#8211; (EM)
        </li>
      </ul>
    </td>
    
    <td>
      <ul>
        <li>
          26 &#8211; (SUB)
        </li>
        <li>
          27 &#8211; (ESC)
        </li>
        <li>
          28 &#8211; (FS)
        </li>
        <li>
          29 &#8211; (GS)
        </li>
        <li>
          30 &#8211; (RS)
        </li>
        <li>
          31 &#8211; (US)
        </li>
        <li>
          32 &#8211; (Espaço)
        </li>
        <li>
          33 &#8211; !
        </li>
        <li>
          34 &#8211; &#8220;
        </li>
        <li>
          35 &#8211; #
        </li>
        <li>
          36 &#8211; $
        </li>
        <li>
          37 &#8211; %
        </li>
        <li>
          38 &#8211; &
        </li>
        <li>
          39 &#8211; &#8216;
        </li>
        <li>
          40 &#8211; (
        </li>
        <li>
          41 &#8211; )
        </li>
        <li>
          42 &#8211; *
        </li>
        <li>
          43 &#8211; +
        </li>
        <li>
          44 &#8211; ,
        </li>
        <li>
          45 &#8211; &#8211;
        </li>
        <li>
          46 &#8211; .
        </li>
        <li>
          47 &#8211; /
        </li>
        <li>
          48 &#8211; 0
        </li>
        <li>
          49 &#8211; 1
        </li>
      </ul>
    </td>
    
    <td>
      <ul>
        <li>
          50 &#8211; 2
        </li>
        <li>
          51 &#8211; 3
        </li>
        <li>
          52 &#8211; 4
        </li>
        <li>
          53 &#8211; 5
        </li>
        <li>
          54 &#8211; 6
        </li>
        <li>
          55 &#8211; 7
        </li>
        <li>
          56 &#8211; 8
        </li>
        <li>
          57 &#8211; 9
        </li>
        <li>
          58 &#8211; :
        </li>
        <li>
          59 &#8211; ;
        </li>
        <li>
          60 &#8211; <
        </li>
        <li>
          61 &#8211; =
        </li>
        <li>
          62 &#8211; &gt/
        </li>
        <li>
          63 &#8211; ?
        </li>
        <li>
          64 &#8211; @
        </li>
        <li>
          65 &#8211; A
        </li>
        <li>
          66 &#8211; B
        </li>
        <li>
          67 &#8211; C
        </li>
        <li>
          68 &#8211; D
        </li>
        <li>
          69 &#8211; E
        </li>
        <li>
          70 &#8211; F
        </li>
        <li>
          71 &#8211; G
        </li>
        <li>
          72 &#8211; H
        </li>
        <li>
          73 &#8211; I
        </li>
        <li>
          74 &#8211; J
        </li>
        <li>
          75 &#8211; K
        </li>
      </ul>
    </td>
    
    <td>
      <ul>
        <li>
          76 &#8211; L
        </li>
        <li>
          77 &#8211; M
        </li>
        <li>
          78 &#8211; N
        </li>
        <li>
          79 &#8211; O
        </li>
        <li>
          80 &#8211; P
        </li>
        <li>
          81 &#8211; Q
        </li>
        <li>
          82 &#8211; R
        </li>
        <li>
          83 &#8211; S
        </li>
        <li>
          84 &#8211; T
        </li>
        <li>
          85 &#8211; U
        </li>
        <li>
          86 &#8211; V
        </li>
        <li>
          87 &#8211; W
        </li>
        <li>
          88 &#8211; X
        </li>
        <li>
          89 &#8211; Y
        </li>
        <li>
          90 &#8211; Z
        </li>
        <li>
          91 &#8211; [
        </li>
        <li>
          92 &#8211; \
        </li>
        <li>
          93 &#8211; ]
        </li>
        <li>
          94 &#8211; ^
        </li>
        <li>
          95 &#8211; _
        </li>
        <li>
          96 &#8211; `
        </li>
        <li>
          97 &#8211; a
        </li>
        <li>
          98 &#8211; b
        </li>
        <li>
          99 &#8211; c
        </li>
      </ul>
    </td>
    
    <td>
      <ul>
        <li>
          100 &#8211; d
        </li>
        <li>
          101 &#8211; e
        </li>
        <li>
          102 &#8211; f
        </li>
        <li>
          103 &#8211; g
        </li>
        <li>
          104 &#8211; h
        </li>
        <li>
          105 &#8211; i
        </li>
        <li>
          106 &#8211; j
        </li>
        <li>
          107 &#8211; k
        </li>
        <li>
          108 &#8211; l
        </li>
        <li>
          109 &#8211; m
        </li>
        <li>
          110 &#8211; n
        </li>
        <li>
          111 &#8211; o
        </li>
        <li>
          112 &#8211; p
        </li>
        <li>
          113 &#8211; q
        </li>
        <li>
          114 &#8211; r
        </li>
        <li>
          115 &#8211; s
        </li>
        <li>
          116 &#8211; t
        </li>
        <li>
          117 &#8211; u
        </li>
        <li>
          118 &#8211; v
        </li>
        <li>
          119 &#8211; w
        </li>
        <li>
          120 &#8211; x
        </li>
        <li>
          121 &#8211; y
        </li>
        <li>
          122 &#8211; z
        </li>
        <li>
          123 &#8211; {
        </li>
        <li>
          124 &#8211; |
        </li>
        <li>
          125 &#8211; }
        </li>
        <li>
          126 &#8211; ~
        </li>
        <li>
          127 &#8211; (DELETE)
        </li>
      </ul>
    </td>
  </tr>
</table>

A tabela de caracteres ASCII (Código Padrão Americano para Intercâmbio de Informações) foi a primeira tabela utilizada em larga escala. O computador foi desenvolvido nos Estados Unidos. No vocabulário americano, não existem acentos, além disso, era um código de 7 bits, e não 8. Ou seja, ao invés de 256 posições, a tabela ASCII tinha apenas 128 posições &#8211; como você sabe, tudo nos computadores são um grupo de zeros (0) e uns (1) chamados de bits. Esses zeros e uns formam grupos de oito em oito que chamados de bytes e representam um número entre 0 e 255. Como as imagens, áudio, vídeos, programas e tudo o que temos nos sistemas de hoje, os caracteres que aparecem na sua tela são grupos de zeros e uns.
  
O computador se popularizou e a necessidade de utilizar acentos e outros tipos de caracteres (Chineses, por exemplo) tornou-se um problema.
  
Hoje, a maioria das tabelas utilizadas foram criadas suprindo as necessidades de um idioma específico, por este motivo elas se tornaram muito limitadas.
  
Por exemplo, se você estiver escrevendo um documento utilizando a tabela de caracteres chinesa, você não poderá escrever algo em hebraico neste documento.
  
Por conta disso muitos problemas podem surgir, por exemplo, seria impossível criar um curso online de hebraico para chineses. Será também um problema se você tiver que fazer um site ou sistema com suporte a diversos idiomas. Por exemplo, um sistema de blog projetado para uso internacional. Isso por que a posição dos caracteres varia de tabela para tabela. Dois codificadores podem usar o mesmo número para dois caracteres diferentes ou usar números diferentes para o mesmo caractere.

### A tabela de caractéres Unicode &#8211; UTF-8

A Web é acessada por pessoas do mundo inteiro. Ter um sistema ou um site que limite o acesso e pessoas de outros países é algo que vai contra a tradição e os ideais da internet. Por isso, foi criado uma tabela que suprisse essas necessidades, essa tabela se chama Unicode. A tabela Unicode suporta algo em torno de um milhão de caracteres. Ao invés de cada região ter sua tabela de caracteres, é muito mais sensato haver uma tabela padrão com o maior número de caracteres possível. Atualmente a maioria dos sistemas e browsers utilizados por usuários suportam plenamente Unicode. Por isso, fazendo seu sistema Unicode você garante que ele será bem visualizado aqui, na China ou em qualquer outro lugar do mundo.
  
O que o Unicode faz é fornecer um único número para cada caractere, não importa a plataforma, nem o programa, nem a língua.

### Antes de começar, você precisa saber

Há algumas recomendações que você precisa saber antes de começar a mudar seu site para Unicode.
  
Existem três principais maneiras para você indicar a seu site qual tabela de caractere você está utilizando:

  1. **Cabeçalho HTTP Content-type** &#8211; Desta forma é necessário configurar o servidor web, algo que não é fácil nem para qualquer um. Dependendo de onde você trabalha, se for em um lugar grande, com vários sites neste mesmo servidor, pode ser a melhor maneira porque você terá que fazer isso uma vez. Caso for vários projetos com servidores diferentes isso pode ser uma dor de cabeça.
  2. **Metatag Content-type** &#8211; Colocando este código no HEAD de seu documento, ele avisará para o browser localmente e na hora da renderização do site qual Charset ele deve utilizar para exibir os caracteres. Esta é uma ótima escolha caso você não tenha acesso aos servidores. Certamente é a maneira mais simples de ser utilizada. ``Quando você escreve um documento HTML (ou qualquer outra linguagem baseada em SGML) é necessário que especifiquemos o Charset utilizado. O **Charset é o conjunto de caracteres utilizados para escrever o documento**. Um jogo de caracteres consiste em ter 1) repertório com caracteres e 2) uma posição de referência para cada um dos caracteres no repertório. Cada caractere é identificado e localizado por este código de posição. Por exemplo, na tabela ASCII, as posições 65, 66 e 67 se referem às letras A, B e C respectivamente.<!--more--> Abaixo, veja a tabela de caracteres ASCII:

<table summary="tabela ASCII" width="100%">
  <tr>
    <td>
      <ul>
        <li>
          00 &#8211; (NUL)
        </li>
        <li>
          01 &#8211; (SOH)
        </li>
        <li>
          02 &#8211; (STX)
        </li>
        <li>
          03 &#8211; (ETX)
        </li>
        <li>
          04 &#8211; (EOT)
        </li>
        <li>
          05 &#8211; (ENQ)
        </li>
        <li>
          06 &#8211; (ACK)
        </li>
        <li>
          07 &#8211; (BEL)
        </li>
        <li>
          08 &#8211; (BS)
        </li>
        <li>
          09 &#8211; (HT)
        </li>
        <li>
          10 &#8211; (LF)
        </li>
        <li>
          11 &#8211; (VT)
        </li>
        <li>
          12 &#8211; (FF)
        </li>
        <li>
          13 &#8211; (CR)
        </li>
        <li>
          14 &#8211; (SO)
        </li>
        <li>
          15 &#8211; (SI)
        </li>
        <li>
          16 &#8211; (DLE)
        </li>
        <li>
          17 &#8211; (D1)
        </li>
        <li>
          18 &#8211; (D2)
        </li>
        <li>
          19 &#8211; (D3)
        </li>
        <li>
          20 &#8211; (D4)
        </li>
        <li>
          21 &#8211; (NAK)
        </li>
        <li>
          22 &#8211; (SYN)
        </li>
        <li>
          23 &#8211; (ETB)
        </li>
        <li>
          24 &#8211; (CAN)
        </li>
        <li>
          25 &#8211; (EM)
        </li>
      </ul>
    </td>
    
    <td>
      <ul>
        <li>
          26 &#8211; (SUB)
        </li>
        <li>
          27 &#8211; (ESC)
        </li>
        <li>
          28 &#8211; (FS)
        </li>
        <li>
          29 &#8211; (GS)
        </li>
        <li>
          30 &#8211; (RS)
        </li>
        <li>
          31 &#8211; (US)
        </li>
        <li>
          32 &#8211; (Espaço)
        </li>
        <li>
          33 &#8211; !
        </li>
        <li>
          34 &#8211; &#8220;
        </li>
        <li>
          35 &#8211; #
        </li>
        <li>
          36 &#8211; $
        </li>
        <li>
          37 &#8211; %
        </li>
        <li>
          38 &#8211; &
        </li>
        <li>
          39 &#8211; &#8216;
        </li>
        <li>
          40 &#8211; (
        </li>
        <li>
          41 &#8211; )
        </li>
        <li>
          42 &#8211; *
        </li>
        <li>
          43 &#8211; +
        </li>
        <li>
          44 &#8211; ,
        </li>
        <li>
          45 &#8211; &#8211;
        </li>
        <li>
          46 &#8211; .
        </li>
        <li>
          47 &#8211; /
        </li>
        <li>
          48 &#8211; 0
        </li>
        <li>
          49 &#8211; 1
        </li>
      </ul>
    </td>
    
    <td>
      <ul>
        <li>
          50 &#8211; 2
        </li>
        <li>
          51 &#8211; 3
        </li>
        <li>
          52 &#8211; 4
        </li>
        <li>
          53 &#8211; 5
        </li>
        <li>
          54 &#8211; 6
        </li>
        <li>
          55 &#8211; 7
        </li>
        <li>
          56 &#8211; 8
        </li>
        <li>
          57 &#8211; 9
        </li>
        <li>
          58 &#8211; :
        </li>
        <li>
          59 &#8211; ;
        </li>
        <li>
          60 &#8211; <
        </li>
        <li>
          61 &#8211; =
        </li>
        <li>
          62 &#8211; &gt/
        </li>
        <li>
          63 &#8211; ?
        </li>
        <li>
          64 &#8211; @
        </li>
        <li>
          65 &#8211; A
        </li>
        <li>
          66 &#8211; B
        </li>
        <li>
          67 &#8211; C
        </li>
        <li>
          68 &#8211; D
        </li>
        <li>
          69 &#8211; E
        </li>
        <li>
          70 &#8211; F
        </li>
        <li>
          71 &#8211; G
        </li>
        <li>
          72 &#8211; H
        </li>
        <li>
          73 &#8211; I
        </li>
        <li>
          74 &#8211; J
        </li>
        <li>
          75 &#8211; K
        </li>
      </ul>
    </td>
    
    <td>
      <ul>
        <li>
          76 &#8211; L
        </li>
        <li>
          77 &#8211; M
        </li>
        <li>
          78 &#8211; N
        </li>
        <li>
          79 &#8211; O
        </li>
        <li>
          80 &#8211; P
        </li>
        <li>
          81 &#8211; Q
        </li>
        <li>
          82 &#8211; R
        </li>
        <li>
          83 &#8211; S
        </li>
        <li>
          84 &#8211; T
        </li>
        <li>
          85 &#8211; U
        </li>
        <li>
          86 &#8211; V
        </li>
        <li>
          87 &#8211; W
        </li>
        <li>
          88 &#8211; X
        </li>
        <li>
          89 &#8211; Y
        </li>
        <li>
          90 &#8211; Z
        </li>
        <li>
          91 &#8211; [
        </li>
        <li>
          92 &#8211; \
        </li>
        <li>
          93 &#8211; ]
        </li>
        <li>
          94 &#8211; ^
        </li>
        <li>
          95 &#8211; _
        </li>
        <li>
          96 &#8211; `
        </li>
        <li>
          97 &#8211; a
        </li>
        <li>
          98 &#8211; b
        </li>
        <li>
          99 &#8211; c
        </li>
      </ul>
    </td>
    
    <td>
      <ul>
        <li>
          100 &#8211; d
        </li>
        <li>
          101 &#8211; e
        </li>
        <li>
          102 &#8211; f
        </li>
        <li>
          103 &#8211; g
        </li>
        <li>
          104 &#8211; h
        </li>
        <li>
          105 &#8211; i
        </li>
        <li>
          106 &#8211; j
        </li>
        <li>
          107 &#8211; k
        </li>
        <li>
          108 &#8211; l
        </li>
        <li>
          109 &#8211; m
        </li>
        <li>
          110 &#8211; n
        </li>
        <li>
          111 &#8211; o
        </li>
        <li>
          112 &#8211; p
        </li>
        <li>
          113 &#8211; q
        </li>
        <li>
          114 &#8211; r
        </li>
        <li>
          115 &#8211; s
        </li>
        <li>
          116 &#8211; t
        </li>
        <li>
          117 &#8211; u
        </li>
        <li>
          118 &#8211; v
        </li>
        <li>
          119 &#8211; w
        </li>
        <li>
          120 &#8211; x
        </li>
        <li>
          121 &#8211; y
        </li>
        <li>
          122 &#8211; z
        </li>
        <li>
          123 &#8211; {
        </li>
        <li>
          124 &#8211; |
        </li>
        <li>
          125 &#8211; }
        </li>
        <li>
          126 &#8211; ~
        </li>
        <li>
          127 &#8211; (DELETE)
        </li>
      </ul>
    </td>
  </tr>
</table>

A tabela de caracteres ASCII (Código Padrão Americano para Intercâmbio de Informações) foi a primeira tabela utilizada em larga escala. O computador foi desenvolvido nos Estados Unidos. No vocabulário americano, não existem acentos, além disso, era um código de 7 bits, e não 8. Ou seja, ao invés de 256 posições, a tabela ASCII tinha apenas 128 posições &#8211; como você sabe, tudo nos computadores são um grupo de zeros (0) e uns (1) chamados de bits. Esses zeros e uns formam grupos de oito em oito que chamados de bytes e representam um número entre 0 e 255. Como as imagens, áudio, vídeos, programas e tudo o que temos nos sistemas de hoje, os caracteres que aparecem na sua tela são grupos de zeros e uns.
  
O computador se popularizou e a necessidade de utilizar acentos e outros tipos de caracteres (Chineses, por exemplo) tornou-se um problema.
  
Hoje, a maioria das tabelas utilizadas foram criadas suprindo as necessidades de um idioma específico, por este motivo elas se tornaram muito limitadas.
  
Por exemplo, se você estiver escrevendo um documento utilizando a tabela de caracteres chinesa, você não poderá escrever algo em hebraico neste documento.
  
Por conta disso muitos problemas podem surgir, por exemplo, seria impossível criar um curso online de hebraico para chineses. Será também um problema se você tiver que fazer um site ou sistema com suporte a diversos idiomas. Por exemplo, um sistema de blog projetado para uso internacional. Isso por que a posição dos caracteres varia de tabela para tabela. Dois codificadores podem usar o mesmo número para dois caracteres diferentes ou usar números diferentes para o mesmo caractere.

### A tabela de caractéres Unicode &#8211; UTF-8

A Web é acessada por pessoas do mundo inteiro. Ter um sistema ou um site que limite o acesso e pessoas de outros países é algo que vai contra a tradição e os ideais da internet. Por isso, foi criado uma tabela que suprisse essas necessidades, essa tabela se chama Unicode. A tabela Unicode suporta algo em torno de um milhão de caracteres. Ao invés de cada região ter sua tabela de caracteres, é muito mais sensato haver uma tabela padrão com o maior número de caracteres possível. Atualmente a maioria dos sistemas e browsers utilizados por usuários suportam plenamente Unicode. Por isso, fazendo seu sistema Unicode você garante que ele será bem visualizado aqui, na China ou em qualquer outro lugar do mundo.
  
O que o Unicode faz é fornecer um único número para cada caractere, não importa a plataforma, nem o programa, nem a língua.

### Antes de começar, você precisa saber

Há algumas recomendações que você precisa saber antes de começar a mudar seu site para Unicode.
  
Existem três principais maneiras para você indicar a seu site qual tabela de caractere você está utilizando:

  1. **Cabeçalho HTTP Content-type** &#8211; Desta forma é necessário configurar o servidor web, algo que não é fácil nem para qualquer um. Dependendo de onde você trabalha, se for em um lugar grande, com vários sites neste mesmo servidor, pode ser a melhor maneira porque você terá que fazer isso uma vez. Caso for vários projetos com servidores diferentes isso pode ser uma dor de cabeça.
  2. **Metatag Content-type** &#8211; Colocando este código no HEAD de seu documento, ele avisará para o browser localmente e na hora da renderização do site qual Charset ele deve utilizar para exibir os caracteres. Esta é uma ótima escolha caso você não tenha acesso aos servidores. Certamente é a maneira mais simples de ser utilizada.`` 
  3. **Através do prolog xml** &#8211; O prolog XML é utilizado em documentos XML ou XHTML para indicar a versão e a tabela de caracteres daquele documento. `<? xml version="1.0" encoding="UTF-8" ?>` Não é uma boa utilizar este prolog por conta do chaveamento do Internet Explorer 6 para Quirks Mode. Quando o prolog é utilizado, o Internet Explorer 6 renderiza os sites como o Internet Explorer 5, trazendo muitos problemas de compatibilidade. Não recomendo.

Outro ponto importante é não esquecer de salvar seu documento no formato da tabela que você indicou. Não adianta nada indicar que código que está utilizando a tabela de caracteres UTF-8 e seu editor salvar seus documentos com a tabela ISO-8859-1. Isso fará com que os caracteres de seu documento apareçam corrompidos. Por isso, ao definir qual será a tabela utilizada no projeto (recomendo sempre UTF-8), defina como seu editor irá salvar seus documentos. Todos os editores de código hoje em dia tem essa opção, basta procurar. Não adianta também você salvar seus arquivos em UTF-8 e o resto da equipe continuar utilizando ISO-8859-1. Os arquivos irão corromper da mesma maneira. É uma decisão que a equipe inteira deve tomar para não haver retrabalho e dor de cabeça.

Se um projeto já está no ar, é bom fazer uma análise para ter certeza se vale a pena ou não mudar a tabela de um projeto que já está no ar e funcionando. Recomendo que esse novo padrão sempre comece a ser utilizado em novos projetos. Mesmo assim, um bom programador pode fazer um script que converta a tabela de caracteres de um diretório inteiro.

O importante é garantir que seu site aqui seja visto da maneira correta em outros lugares do mundo. Isso é importante para você e seu cliente.

<!--object width="425" height="355"><embed src="https://www.youtube.com/v/SX5bCCtHYXo&hl=en" type="application/x-shockwave-flash" wmode="transparent" width="425" height="355"></embed></object-->