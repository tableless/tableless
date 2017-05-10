---
title: Fazendo uma faxina no seu CSS
author: Jhonathan Souza Soares
type: post
date: 2014-05-15
excerpt: |
  |
    Com apenas um teste rápido, você poderá fazer uma análise completa das suas folhas de estilo e remover os seletores não utilizados.
url: /fazendo-uma-faxina-seu-css/
dsq_thread_id: 2598345085
categories:
  - CSS
tags:
  - boas praticas
  - CSS

---
Sempre podemos discutir sobre como escrevemos CSS e também quais são as melhores práticas. Geralmente artigos sobre CSS agradam qualquer desenvolvedor independente da linguagem utilizada, já que é uma leitura fácil e o código costuma ser bem simples.

### A Origem de tudo

Já foi falado aqui no Tableless várias vezes sobre performance e velocidade de páginas. Um deles você encontra aqui no artigo que fala sobre a <a title="Performance CSS" href="http://tableless.com.br/melhorando-performance-css/" target="_blank">performance do seu CSS</a>

Um ponto que sempre ganha destaque, é a velocidade e a <a title="http://tableless.com.br/acelere-o-carregamento-de-suas-paginas/" href="http://tableless.com.br/acelere-o-carregamento-de-suas-paginas/" target="_blank">performance no carregamento dos sites</a>. Um dos principais pontos chaves para conseguir tal feito é diminuir ao máximo o tamanhos dos arquivos que são carregados no browser.

Acredito que a  performance de CSS não é a principal causa de gerar lentidão e demora de um carregamento em um site, mas sempre devemos buscar por melhorias, alternativas que nos auxiliam a otimizar o desenvolvimento e enriquecer a performance do usuário.

### Onde mora o problema

Mas quando o assunto não trata só de como você utiliza o seu CSS e sim quando o assunto é sobre desperdício de tempo e gerando arquivos de folhas de estilos com seletores que nunca serão utilizados ou estão diminuindo a performance do CSS devemos considerar a repensar no nosso estilo de programação.O pior de tudo é que as vezes estamos fazendo nossos milhões de visitantes via desktop ou móvel pagarem por nossa preguiça e erros.

Uma ótima ferramenta chamada **Helium** está disponível para ajudar os desenvolvedores a detectar seletores em suas folhas de estilo que não estão sendo utilizados ou ainda estão mal formados que acabam prejudicando o CSS.

### Vamos à parte prática :

Primeiramente você pode fazer o download dele aqui : <a title="https://github.com/geuis/helium-css" href="https://github.com/geuis/helium-css" target="_blank">https://github.com/geuis/helium-css</a>
  
Ao fazer download, você poderá notar que nele conterá 2 exemplos já implementados que são de fácil entendimento. Mas mesmo assim iremos colocar aqui de forma simplificada:

Comece incluindo um documento HTML em branco a referencia do script Helium para carregá-lo em sua página :

<pre class="lang-javascript">&lt;script type="text/javascript" src="../helium.js" onload="helium.init()" async&gt;&lt;/script&gt;</pre>

Pronto!
  
Repare que adicionei duas folhas de estilo na página pois a própria página que irei utilizar o Helium, será a página que utilizarei para testes.

Veja como ficou minha página:

<pre class="lang-html">&lt;!doctype&gt;
&lt;html&gt;
&lt;head&gt;

&lt;link href="style/estilo.css" media="all" rel="stylesheet" type="text/css"&gt;
&lt;link href="style/estilo2.css" media="all" rel="stylesheet" type="text/css"&gt;

&lt;script type="text/javascript" src="../helium.js" onload="helium.init()" async&gt;&lt;/script&gt;

&lt;/head&gt;
&lt;body&gt;
&lt;/body&gt;

&lt;/html&gt;</pre>

Realizando apenas estes dois passos você já configurou seu ambiente de testes e poderá executar a página no navegador. Assim que a página é carregada, é exibido ao usuário um textarea que pode ser utilizado como entrada de URL na qual ele deseja testar :

<div id="attachment_42093" style="width: 730px" class="wp-caption alignnone">
  <a href="http://tableless.com.br/uploads/2014/04/helium-passo-1.jpg"><img class="size-full wp-image-42093" alt="Helium" src="http://tableless.com.br/uploads/2014/04/helium-passo-1.jpg" width="720" height="257" srcset="uploads/2014/04/helium-passo-1.jpg 720w, uploads/2014/04/helium-passo-1-400x142.jpg 400w" sizes="(max-width: 720px) 100vw, 720px" /></a>
  
  <p class="wp-caption-text">
    Tela inicial Helium
  </p>
</div>

&nbsp;

Caso você queira testar a própria página que foi carregada, assim como neste exemplo, bastar clicar  em **‘Start’** que ele irá carregar os resultados :

<div id="attachment_42094" style="width: 730px" class="wp-caption alignnone">
  <a href="http://tableless.com.br/uploads/2014/04/helium-passo-2.jpg"><img class="size-full wp-image-42094" alt="Helium" src="http://tableless.com.br/uploads/2014/04/helium-passo-2.jpg" width="720" height="263" srcset="uploads/2014/04/helium-passo-2.jpg 720w, uploads/2014/04/helium-passo-2-400x146.jpg 400w" sizes="(max-width: 720px) 100vw, 720px" /></a>
  
  <p class="wp-caption-text">
    Tela de resultados Helium
  </p>
</div>

&nbsp;

Com isto você poderá analisar que :

  * Seletores na cor verde não estão sendo utilizados
  * Seletores na cor preta estão sendo utilizados
  * Seletores na cor azul, não puderam ser testados devido que eles só são ativados com alguma ação do usuário, por isto teste manualmente depois.
  * Seletores na cor vermelha estão mal formados e prejudicando seu CSS, por isso faça correção ou delete-os.

### Finalizando

A ferramenta apesar de ser bastante simples você pode testar inúmeras páginas e ganhar mais desempenho de carregamento dos seus sites melhorando a experiência do usuário.

Um ponto importante que podemos ressaltar da ferramenta, que ela além de otimizar o seu CSS ela também realiza um testes dos seletores contidos, fazendo assim um teste de semântica nas suas folhas de estilo, garantindo assim maior robustez do seu código.

Sempre podemos melhorar em algum ponto nossa escrita de código e talvez nessas ações simples que fazemos acabamos não só descobrindo possíveis melhorias no nosso código, mas também evoluímos profissionalmente conhecendo melhor a linguagem de estilos e seu comportamento na experiência do usuário.

Espero que tenham gostado!