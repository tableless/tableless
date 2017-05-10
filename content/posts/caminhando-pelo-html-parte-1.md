---
title: Caminhando pelo HTML – parte 1
author: Elcio Ferreira
type: post
date: 2006-12-11
url: /caminhando-pelo-html-parte-1/
tweetbackscheck:
  - 1355138632
shorturls:
  - 'a:3:{s:9:"permalink";s:52:"http://tableless.com.br/caminhando-pelo-html-parte-1";s:7:"tinyurl";s:26:"http://tinyurl.com/3lfwu8x";s:4:"isgd";s:19:"http://is.gd/nlRiOm";}'
twittercomments:
  - 'a:0:{}'
dsq_thread_id: 503036279
categories:
  - Artigos
  - Geral
  - Técnicas e Práticas

---
Vou publicar aqui a série de artigos sobre HTML que escrevi para a revista Webdesign. É uma série de 5 e vai sair um a cada 15 dias. Segue o primeiro:

<!--more-->

Este mês vamos iniciar uma série de estudos sobre HTML. Alguns podem estranhar o fato de ocuparmos espaço nesta revista para falarmos sobre um assunto tão comum e uma linguagem tão simples. Por isso, vou começar explicando o que me motivou a escrever esta série.

### Simples e Importante

HTML é uma linguagem bastante simples, mas muito importante. Praticamente tudo na web é feito com HTML ou depende dela de alguma maneira. Até um site todo em Flash é publicado num arquivo HTML.

Este primeiro artigo pode parecer muito básico. Não se engane, há muita coisa importante a aprender nos fundamentos do HTML. Às vezes o que nos faz falta é mesmo o conhecimento inicial, e tenho visto muita gente tropeçar nas coisas simples. Vejo muitas &#8220;soluções&#8221; inventadas com CSS e Javascript para resolver problemas que o HTML resolve sozinho. Tenho visto também muita gente que faz um trabalho limitado simplesmente porque não conhece os recursos disponíveis na linguagem.

Outro motivo para escrever é o fato de que tenho visto muita gente capaz, habilitada a trabalhar com layouts CSS ou programação Javascript/AJAX, perdendo seu tempo com problemas simples de HTML.

### Eliminar o medo

Nossa primeira tarefa é perder o medo do HTML. Se você trabalhou com HTML sem CSS, ou com pouco CSS, com código baseado em tabelas ou gerado automaticamente pelo editor visual, tem boas razões para ter medo de HTML. Se, como eu, teve que fazer seu HTML funcionar nos velhos Netscape 4 e Internet Explorer 4, deve mesmo ficar apavorado.

Deixe-me avisá-lo, não é daquele velho HTML complicado que estamos falando. Pretendo mostrar-lhe que, trabalhando com padrões web, HTML é uma linguagem realmente simples, e muito poderosa.

### Recursos únicos

HTML é uma linguagem com recursos únicos, feita para ser usada na construção duma Internet aberta e acessível. Conhecê-la pode tornar seu site mais acessível e muito flexível. Foi feita para que seu site funcione em qualquer navegador, em qualquer plataforma. Para que ele seja acessível em seu celular, e apareça bem no Google. Os primeiros artigos desta série vão falar sobre isso.

Além disso, é uma linguagem extensível. Os últimos artigos vão falar de microformatos, GeoURL e outras maneiras de se estender o HTML, e mostrar algumas aplicações que estão surgindo baseadas nisso. Este é um excelente motivo para escrever sobre HTML. Você vai gostar de conhecer os novos usos que estão sendo dados à linguagem e as extensões do HTML que você pode usar em seu site.

HTML é a própria base da construção de sites com padrões web. Antes da formatação CSS, de um elegante javascript baseado em DOM ou um poderoso Ajax, todo site baseado em padrões começa com HTML e é impossível trabalhar com padrões web sem saber HTML.

### A idéia básica: texto simples

A idéia básica por trás do HTML é muito simples: ele é um arquivo de texto. Isso mesmo, texto puro, como o que você pode escrever no bloco de notas. Essa é a natureza fundamental do HTML, e que o torna acessível em qualquer plataforma e em qualquer dispositivo. Embora existam plataformas de software que não suportem imagens, sons ou flash, não há sistema que não suporte texto.

### XML

Um daqueles fundamentos que muita gente ignora é o fato de a linguagem HTML tem versões. Neste tutorial trabalharemos com a versão XHTML 1.0. XHTML é uma versão da linguagem HTML que é compatível com XML. Na prática, para quem escreve o HTML, isso significa ter uma meia dúzia de regras simples ao escrever, poder usar validadores automáticos muito poderosos em seu código e produzir código preparado para as aplicações que estão surgindo e ainda vão surgir baseadas em XML.

Quando abordarmos os microformatos, no final dessa série, isso vai ficar mais claro. Por hora, basta saber que seguindo o padrão XHTML você vai estar pronto para o que vamos fazer depois.

### tags

O texto HTML é muito simples, é quase como texto comum. A principal diferença é que há pequenas marcas que podemos colocar no texto para indicar suas partes. Por exemplo, digamos que determinada palavra no texto precise de um destaque especial, você pode fazer isso assim:

`Um <strong>diamante</strong> é um pedaço de carvão que se saiu bem sob pressão.`

O código <strong> indica o início do texto destacado, e o código </strong> o seu final. A esses pequenos marcadores damos o nome de tags (etiquetas) porque servem justamente para marcar trechos do texto. Veja um trecho típico de código HTML:

`<h1>PASSAREDO</h1><br />
<p>Cuidado, homem que (se) mata! Quem é que você mata se mata a mata, que não a si mesmo?!</p><br />
<p>O poema de Luiz Angelo Vilela Tannus dá o triste aviso: Cuidado, existência! O homem pode acabar com você...</p>`

Temos aqui um título (h1) e dois parágrafos (p) de texto. Código simples, tanto de se escrever quanto de se ler.

### atributos

Nem todos os parágrafos são iguais. O mesmo com os títulos, imagens, links, listas, menus e formulários. Muitas vezes uma tag não é o suficiente para representar o que você quer dizer em determinado trecho de código. Por exemplo, ao inserir um link, é preciso dizer para onde esse link aponta, e muitas vezes você quer indicar também qual será o texto da tooltip que aparecerá quando o cursor estiver sobre o link. Logo, você tem um link assim:

`Isto é um link: <a xhref="http://tableless.com.br"     >Tableless</a>.`

E com o texto da tooltip:

`Isto é um link: <a xhref="http://tableless.com.br"      title="Tableless: web standards">Tableless</a>.`

Os atributos são sempre usados para definir características das tags, como o endereço de uma imagem ou o tipo de um campo de formulário. Um documento HTML é basicamente composto desses três elementos: texto, tags e atributos. Simples, não?

### semântica e significado

Você deve ter notado uma característica interessante do HMTL: cada tag significa alguma coisa. Assim, usa-se a tag strong (forte) para destacar trechos de texto, p para fazer parágrafos, h1 para títulos e a para links, para citar as que já usamos. É importante usar a tag certa para cada tarefa, e este é um dos principais segredos do trabalho com HTML. A boa notícia é que a quantidade de tags é pequena e você logo saberá de cor todos as possibilidades.

Muita gente tem escrito HTML, seja em editores de código ou em editores WYSIWYG, quebrando essa regra básica. Ao observar o resultado em seu navegador, parece tudo bem. Mas quando você avalia o mesmo site num navegador simplificado, como os de dispositivos móveis, percebe a falta que fazem as tags em seus lugares exatos.

A essa característica do código, de usar a tag certa para cada tarefa, damos o nome de semântica. Ou seja, significado. Cada tag tem um significado, e você não pode usar uma tag de título para fazer um parágrafo de texto comum ou uma tag de endereço para fazer um menu.

É sobre esse significado que estão sendo construídas uma série de aplicações interessantes. Há leitores de tela para cegos que, baseados na semântica do documento, auxiliam o usuário em sua navegação. Ele pode, por exemplo, ouvir apenas os títulos da página para encontrar com facilidade o conteúdo que o interessa. Robôs de busca como o Google parecem entender a semântica do documento ao pontuar as páginas. E os microformatos são construídos em cima da semântica.

### Nosso caminho

Espero ter lhe vendido meu peixe. Nos próximos três artigos vamos falar sobre a estrutura básica do HTML, a construção do código, as tags disponíveis, as informações relacionadas, como a página de código usada (se você tem problemas com acentos, precisa ler este artigo) e as folhas de estilo relacionadas. E no final dessa série daremos o passo além falando sobre os microformatos e como você pode aumentar as funcionalidades disponíveis em seu HTML. Até!