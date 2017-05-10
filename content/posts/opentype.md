---
title: Um pouco sobre OpenType
author: Fabiano de Lima Abreu
type: post
date: 2014-06-28
excerpt: Como adicionar tipografia à web com recursos OpenType.
url: /opentype/
dsq_thread_id: 2793098100
categories:
  - CSS3
  - Técnicas e Práticas
tags:
  - ligaduras
  - opentype
  - suporte
  - tipografia

---
Com tantos elementos que se movem e mudam de uma tela para a outra, uma boa tipografia é uma das únicas coisas que funcionam bem em qualquer dispositivo (exceto os que usam o Opera Mini).

As palavras possuem significado, mas as letras demonstram emoção. O OpenType é um formato de fontes multiplataforma desenvolvido pela Adobe e Microsoft. Oferece grande profundidade e variedade  ao expandir os conjuntos de fontes tradicionais ao acrescentar recursos como ligaduras, ornamentos, glifos alternativos e kerning real.

## **Contextualizando os recursos**

Kerning basicamente, se trata de ajustar os espaços entre os caracteres de maneira que a leitura seja mais funcional e agradável. Em outras palavras, é um processo de adicionar ou remover espaço entre pares de caracteres, ou seja, mexe-se no espaçamento existente apenas entre uma ou outra letra, algumas letras, mas não em tudo, como funciona a propriedade letter-spacing do css.

**Traking** trata-se de um processo de adicionar ou remover espaço em todo um bloco de texto, ou seja, mexe-se no espaçamento existente em todo o conjunto de letras por igual, seja uma única palavra, frase, parágrafo inteiro.

**Ligaduras** são combinações de caracteres que historicamente tendem a se unir ao serem posicionados lado a lado, como ff, ffl, fi ou fj.

<div id="attachment_43150" style="width: 337px" class="wp-caption alignnone">
  <a href="http://tableless.com.br/uploads/2014/06/ligaduras.jpg"><img class="wp-image-43150" src="http://tableless.com.br/uploads/2014/06/ligaduras-265x132.jpg" alt="ligaduras" width="327" height="163" srcset="uploads/2014/06/ligaduras-265x132.jpg 265w, uploads/2014/06/ligaduras-400x200.jpg 400w, uploads/2014/06/ligaduras.jpg 558w" sizes="(max-width: 327px) 100vw, 327px" /></a>
  
  <p class="wp-caption-text">
    No texto magenta, não há ligaduras. Veja a diferença na terceira linha ao usar &#8216;ffl&#8217; e &#8216;ffi&#8217;
  </p>
</div>

Além dos recursos citados acima, ainda temos recursos que incluem os glifos alternativos e opções para numerais, incluindo frações e números tabulares e muitos outros.

Só isso já justificaria o uso de OpenType, já que os navegadores tendem a fazer um péssimo trabalho ao distribuir o espaço entre as letras na tela.

## Um pouco de história

Esses caracteres e recursos existem há séculos, mas apenas recentemente tornaram-se usáveis na web.

Com o advento dos tipos móveis, as ligaduras foram usadas para melhorar o espaçamento entre letras e para otimizar a distribuição dos tipos.

Assim como tudo na web, o uso desses recursos depende do suporte dos navegadores, mas felizmente o nível de suporte é alto o suficiente para usá-lo.

## Qual é a diferença entre fontes TrueType, PostScript e OpenType?

Se você lida frequentemente com fontes já viu pelo menos dois desses termos, mas afinal oque são  fontes TrueType, OpenType e Postscript?

As fontes **TrueType** são mais comuns, sendo a maioria das fontes gratuitas ou mais baratas. Foram criadas nos anos 80 pela Apple e posteriormente implementadas no windows 3.1 pela microsoft. Podem ter seu fator de escala definido para qualquer tamanho, são legíveis em vários tamanhos e é possível envia-las para qualquer dispositivo de saída. São recomendadas quando é preciso uma fonte leve, mas que imprima bem e tenha uma boa qualidade em monitores; sua extensão é “.ttf”.

O formato **OpenType** foi desenvolvido pela microsoft em 1994 baseado no TrueType. Primeiramente foi chamado de TrueType Open, nome este que foi alterado para o atual após a entrada da Adobeno projeto, incorporando tecnologias próprias do PostScript Type 1. O OpenType tem as mesmas características de seu antecessor e mais algumas vantagens; ele pode incorporar uma extensão maior do conjunto de caracteres, dá suporte a várias linguagens num só arquivo e possibilita tratamentos tipográficos complexos de algumas linguagens, como ligaduras entre caracteres. É recomendado quando é necessário abranger um certo idioma e uma tipografia mais detalhada; sua extensão é “.otf”.

As chamadas **PostScript** foram as primeiras a surgir pelas mãos da Adobe. Com o intuito de serem usadas para imprimir documentos complexos em impressoras digitais, atualmente são suportadas por quase todas as impressoras laser, tendo uma ótima qualidade e sendo bem harmoniosas. São recomendadas para impressões de alta qualidade, como revistas e publicações. As fontes PostScript para windows são formadas por 4 arquivos com as seguintes extensões: “.afm”, “.pfb”, “.pfm” e “.inf”.

## Suporte

Hoje o único navegador que não oferece suporte ao OpenType é o Opera Mini. Veja a lista de navegadores com suporte, abaixo: (disponível em: <a href="http://caniuse.com/#search=woff" target="_blank">http://caniuse.com/#search=woff</a>)

[<img class="alignnone wp-image-43155 size-full" src="http://tableless.com.br/uploads/2014/06/support.png" alt="suporte" width="930" height="351" srcset="uploads/2014/06/support.png 930w, uploads/2014/06/support-265x100.png 265w, uploads/2014/06/support-400x150.png 400w" sizes="(max-width: 930px) 100vw, 930px" />][1]

## Por que usar?

A leitura se dá por grupos de formas, e não letras individuais. Assim, quanto mais suave for o fluxo, mais fácil será apreender grupos de letras e interpretá-las como palavras ou frases, e mais rápido o usuário compreenderá a mensagem que virá com estilo.

## Detalhes de uso

Ao incluir uma fonte com recursos OpenType em seu site, o uso via CSS é bem simples. A sintaxe oficial do CSS3 é assim:

<pre class="lang-html">p{
  font-feature-settings:"frac" 1;
}</pre>

Este código habilita as frações, se estiverem disponíveis na fonte. Devido às variações de sintaze, o modo mais seguro de incluir o código acima é assim:

<pre class="lang-html">p{
  -moz-font-feature-settings:"frac" 1; 
  -moz-font-feature-settings:"frac=1"; 
  -ms-font-feature-settings:"frac" 1; 
  -o-font-feature-settings:"frac" 1; 
  -webkit-font-feature-settings:"frac" 1; 
  font-feature-settings:"frac" 1;
}

</pre>

Você pode ver o código acima funcionando através do seguinte codepen: <a href="http://codepen.io/Fabiano/pen/zFdka" target="_blank">http://codepen.io/Fabiano/pen/zFdka</a>

Aqui está uma lista completa dos recursos existentes e como usá-los.

  * “c2sc”: caixa alta em small caps
  * “calt”: tipos alternativos por contexto
  * “clig”: ligaduras contextuais
  * “dlig”: ligaduras discricionárias
  * “hist”: tipos alternativos históricos
  * “hlig”: ligaduras históricas
  * “kern”: habilita o uso da tabela interna de kerning
  * “liga”: ligaduras comuns
  * “nalt”: formas anotadas alternativas
  * “salt”: alternativas de estilo
  * “smcp”: small caps
  * “ss01”: conjunto de estilo alternativo 1
  * “ss02”: conjunto de estilo alternativo 2
  * “ss03”: conjunto de estilo alternativo 3
  * “ss04”: conjunto de estilo alternativo 4
  * “ss05”: conjunto de estilo alternativo 5
  * “swsh”: ornamentos
  * “zero”: zero cruzado

**Números**:

“lnum”: alinhados ou “onum”: “oldstyle”

**Espaçamento de números:**

“pnum”: proporcional ou “tnum”: tabular (monoespaçados, úteis para tabulações)

**Frações:**

“frac”: normais ou “afrc”: alternativas

## Uma Abordagem razoável

Uma das vantagens dos recursos OpenType é que eles mostram o texto normal caso não haja o suporte ao recurso, por isso não há problemas em adicioná-los ao seu projeto, que terá um nível de acabamento mais refinado.

Com a grande ênfase em legibilidade, aumento na densidade de pixels e qualidade de telas, cada vez mais usuários lêem conteúdos mais longos on-line. Isso significa que os benefícios de legibilidade obtidos com uma melhor tipografia podem ser traduzidos em maior legibilidade e usabilidade percebida pelos seus usuários.

## Saiba mais:

**Fonts.com**

O serviço Monotype permite pesquisar fontes por nível de recursos OpenType suportados: <a href="http://www.fonts.com/support/faq/opentype-features-tab" target="_blank">http://www.fonts.com/support/faq/opentype-features-tab</a>. Também possui um sistema para gerar o código CSS para seu site.

**Typography.com**

A H&FJ também suporta recursos OpenType em suas fontes, com os mais extensos e detalhados controles sobre os recursos a serem usados, oferecendo mais controle sobre o tamanho do download. Veja a ótima documentação de uso em: <a href="http://www.typography.com/cloud/user-guide/font-features" target="_blank">http://www.typography.com/cloud/user-guide/font-features</a>

**A ferramenta de Rich Rutter**

O cofundador da Fontdeck criou uma ferramenta para lidar com recursos OpenType, permitindo habilitar e desabilitar as diferentes funções. Você pode testar fontes variadas e analisar o CSS resultante: <a href="http://clagnut.com/sandbox/css3/" target="_blank">http://clagnut.com/sandbox/css3/</a>

## Referências

Há um PDF muito bom direto do site da Adobe que aborda como o OpenType funciona e alguns detalhes bem interessantes:

DESCONHECIDO. Can I Use. Support tables for HTML5, CSS3, etc. **Can I Use**, 2014. Disponivel em: <http://caniuse.com/#search=woff>. Acesso em: 9 Junho 2014.

DESCONHECIDO. Qual é a diferença entre fontes TrueType, PostScript e OpenType? **Windows**. Disponivel em: <http://windows.microsoft.com/pt-br/windows/difference-truetype-postscript-opentype-fonts#1TC=windows-7>. Acesso em: 9 Junho 2014.

MOTA, H. O que são fontes TrueType, OpenType e PostScript? **Design Culture**, 13. Disponivel em: <http://www.designculture.com.br/o-que-sao-fontes-truetype-opentype-e-postscript/>. Acesso em: 16 Junho 2014.

PAMENTAL, J. Domine o OpenType. **Revista W**, São Paulo, n. 167, p. 62-66, Junho 2014.

SANGIOVANNI, C. Rapidinha:O que é Kerning. **Choco La Design**, 2011. Disponivel em: <http://chocoladesign.com/rapidinha-o-que-e-kerning>. Acesso em: 9 Junho 2014.

 [1]: http://tableless.com.br/uploads/2014/06/support.png