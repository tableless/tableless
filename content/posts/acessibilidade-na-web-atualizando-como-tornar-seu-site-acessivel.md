---
title: 'Acessibilidade na web: Como tornar seu site acessível.'
author: Thaiana Poplade
type: post
date: 2015-10-26
excerpt: |
  Há 5 anos atrás eu escrevi aqui no Tableless um artigo falando um pouco sobre acessibilidade na web.
  Cinco anos se passaram e os motivos para se ter esse cuidado ao desenvolver sua aplicação não mudaram, mas novas ferramentas surgiram para que você atenda cada vez mais às demandas dessa parcela da nossa sociedade que tem tanto direito de usufruir de seu website quanto as pessoas sem deficiência alguma.
url: /acessibilidade-na-web-atualizando-como-tornar-seu-site-acessivel/
categories:
  - Acessibilidade
  - Artigos
  - CSS
  - HTML
  - Semântica
  - Técnicas e Práticas
  - Web Semântica
tags:
  - acessibilidade
  - jaws
  - lynx

---
Você talvez esteja lendo essas primeiras linhas e pensando: por que tornar um site acessível? E por que me preocupar com isso quando meu prazo de entrega é tão curto?

Eu explico: acessibilidade na web é uma questão de boa prática. Além de você colaborar para que mais pessoas sejam impactadas pelo conteúdo disseminado em seu site, você ainda estará fazendo parte dos profissionais que conhecem e querem implementar cuidados básicos que geram imensos resultados à navegação diferenciada à que estamos habituados. Afinal, se você estudou e desgastou seu tempo resolvendo e entendendo todos os problemas que o crossbrowser causa na hora de escrever seu html, porque não ir um pouco além e construir algo que tenha significado também para outras pessoas?!

<a href="http://tableless.com.br/como-tornar-seu-website-acessivel/" target="_blank">Em 5 anos de um artigo para outro, pouco mudou, mas muito se atualizou.</a>

As recomendações da W3C em termos de tags foram ampliadas com chegada do HTML5 que colabora dizendo o que cada conteúdo representa em seu código e a web semântica atingiu outro nível após as recomendações de uso da WAI-ARIA que estende o significado das interações (<a href="http://tableless.com.br/wai-aria-estendendo-o-significado-das-interacoes/" target="_blank">como é colocado pelo Diego aqui no Tableless</a>).

As ferramentas se ampliaram em quantidade e utilidade. Agora, ficou ainda mais fácil testar se seu site corresponde às boas práticas com apenas um clique.

E não menos importante, as cores, contrastes e os elementos visuais também ganharam notoriedade com as novas ferramentas e dicas de boas aplicações quando buscamos assertividade na web acessível.

## Tags, HTML5, CSS e WAI-ARIA

Com a chegada do HTML5 e suas novas tags, muito da informação já ganhou um “nome e sobrenome” auxiliando aos leitores de tela, demais navegadores e motores de busca, uma compreensão da informação ali contida, mas em termos de acessibilidade a W3C vai um pouco além ressaltando a utilização da WAI-ARIA que pode dar significado à tags como div’s e listas não ordenadas, que não são parte da atualização HTML5. <a href="http://tableless.com.br/?s=wai-aria" target="_blank">Aqui no Tableless você consegue ter uma ideia bem legal com alguns artigos já publicados.</a>

Além disso, as indicações de preenchimentos mais completos dos “alts” [<img src=”” alt=”Texto complementar” />] das imagens e dos “titles” [<a href=”” title=”Texto complementar”></a>] dos hyperlinks continuam sendo relembradas como práticas indispensáveis para acessibilidade. Hoje, completando as indicações, o que vale ressaltar é o cuidado com textos alternativos em imagens decorativas como links com imagens de fundo ou sprites e com os labels em formulários.

Um bom código estruturado, com cuidados para melhores respostas em SEO e um css organizado e dividido por mídia (em caso de uma busca por páginas que possam ser impressas em braille ou para leitores de tela) já fazem do seu site uma aplicação com boas respostas para acessibilidade. Afinal é como eu mencionei, tudo resume-se à boas práticas que com o tempo, você desenvolve sem grandes impactos de tempo para entrega final.

## Ferramentas que auxiliam a construção de websites acessíveis

Saber como fazer e como fazer corretamente é uma das coisas que nos motivam no mundo front-end. As ferramentas a seguir, dão algumas respostas que ajudam a definir essas questões para construção da acessibilidade web de sua aplicação:

  * <a href="http://www.checkmycolours.com/" target="_blank">http://www.checkmycolours.com/</a> || Ferramenta utilizada para testar o contraste textual de seu website.
  * <a href="http://leaverou.github.io/contrast-ratio/" target="_blank">http://leaverou.github.io/contrast-ratio/</a> || Confira o contraste entre seu background e a cor de seu texto.
  * <a href="http://www.prodeaf.net/" target="_blank">http://www.prodeaf.net/</a> || Ferramenta que permite que você implemente um tradutor de libras para os textos de seu site.
  * <a href="https://chrome.google.com/webstore/detail/wave-evaluation-tool/jbbplnpkjmmeebjpijfedlgcdilocofh?utm_source=chrome-app-launcher-info-dialog" target="_blank">https://chrome.google.com/webstore/detail/wave-evaluation-tool/jbbplnpkjmmeebjpijfedlgcdilocofh?utm_source=chrome-app-launcher-info-dialog</a> Wave Evaluation Tool || Extensão do Chrome para teste de acessibilidade em websites.

## Navegadores textuais e leitores de tela

Nem que seja apenas por curiosidade, vale a pena navegar utilizando um desses navegadores e aprender um pouco mais como pessoas com deficiência “enxergam” a web e como muitas vezes um detalhe visual que amamos pode ser um terror para esses usuários :).

  * <a href="http://intervox.nce.ufrj.br/~hpdosvox/download.htm" target="_blank">Dosvox</a>
  * <a href="http://www.freedomscientific.com/Products/Blindness/JAWS" target="_blank">Jaws</a>
  * <a href="http://lynx.invisible-island.net/lynx2.8.7/index.html" target="_blank">Lynx</a>

## Outros artigos bacanudos e recheados de dicas

  * <a href="http://www.maujor.com/w3c/introwac.html" target="_blank">Introdução à Acessibilidade na Web</a>
  * <a href="http://blog.w3c.br/css-e-acessibilidade-na-web/" target="_blank">CSS e Acessibilidade na Web</a>
  * <a href="http://www.maujor.com/w3c/tec_css_acess.html" target="_blank">Técnicas CSS para acessibilidade a conteúdo web</a>
  * <a href="http://joeclark.org/book/sashay/serialization/" target="_blank">‘Building Accessible Websites’ serialization</a>
  * <a href="http://www.maujor.com/tutorial/acessibilidade/tentest.php" target="_blank">Dez testes rápidos para checar a acessibilidade ao seu web site</a>
  * <a href="http://www.acessibilidadelegal.com/33-leitores.php" target="_blank">Navegação Via Teclado e Leitores de Tela. </a>

Ficam aí as dicas. Bora fazer uma web mais acessível?

Até a próxima.