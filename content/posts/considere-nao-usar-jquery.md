---
title: Considere não usar JQuery
author: Diego Eis
type: post
date: 2014-02-19
excerpt: Em projetos pequenos ou em projetos com pouco javascript, considere não usar JQuery.
url: /considere-nao-usar-jquery/
dsq_thread_id: 2279023221
titulo_personalizado:
  - 'E se você tentasse utilizar <strong>menos jQuery?</strong>'
categories:
  - JavaScript
  - JQuery
tags:
  - JavaScript
  - JQuery

---
Como todo novo começo, você aproveita para tentar fazer melhor e diferente. Com o novo design do Tableless, decidi tentar melhorar duas coisas: 1) a montagem do WordPress. 2) Fazer as funções JS sem o JQuery.

Na primeira opção (que também merece um post separado) comecei a usar melhor algumas features do WordPress. Isso me ajudou a melhorar a performance e a organizar mais o código:

  * Loops feitos com WP\_Query() e get\_posts().
  * get\_template\_part para separar a incluir partes de código.
  * wp\_enqueue\_script e wp\_enqueue\_style para distribuir os CSS e Javascripts necessários para cada tela. Isso ajuda a não carregar arquivos desnecessários em cada ela do site.

Depois faço um post explicando melhor cada ponto desse.

Outra decisão foi retirar o JQuery. O Tableless não tem comportamentos densos e difíceis de fazer. Ele não é um site com milhões de linhas de javascript. É um site relativamente pequeno. Não há tantos assets para gerenciar. Por todos esses motivos, não havia sentido eu carregar o JQuery simplesmente para fazer um toggleClass, addClass, click ou qualquer outro comportamento simples&#8230; Decidi então [retirar o JQuery e usar Javascript puro][1].

Confesso que o código aumentou bastante, mas por que usar o JQuery só para fazer um ToggleClass? Eu sei que o javascript do site não vai ficar gigante. O site do Tableless é tão pequeno que também nem vale a pena ter o trabalho de usar grunt/gulp para minificar e concatenar o código. Faço várias pequenas alterações o tempo todo nele. Isso iria dificultar o processo de atualização.

Com este novo design, o código JS ficou minúsculo. Basicamente só precisei usar os comandos **classList** e o **querySelector** do JS.

Para você ter uma ideia de como funciona o classList. Se eu quiser adicionar uma classe em todos os divs de uma página, faço assim:

<pre class="lang-javascript">var $div = document.querySelectorAll('div');

  for (var i = 0; i &lt; $div.length; i++) {
    $div[i].classList.add('classe1', 'classe2');
  }
</pre>

A única coisa que o JQuery facilitaria aqui, seria o tratamento da NodeList que o **querySelectorAll**. No caso aí de cima, tive que fazer manualmente com um **for**.

O [Pedro Rogério][2] [escreveu sobre sua decisão de tirar JQuery de coisas pequenas][3] também.

Muitos desenvolvedores tem se amarrado ao JQuery ficando 100% dependentes do framework. Eu confesso que o código um pouco menor com JQuery. Mesmo assim, por causa de algumas linhas a mais, você deixa de explorar as novas APIs do Javascript, que encurtam o código tanto quanto o JQuery.

Se você **não** for fazer um grande framework, ou sistema complexo, ou um site gigante, considere usar Javascript puro.

## Disclaimer

Não sou contra JQuery, de forma nenhuma. Você deve usá-lo sempre que julgar necessário. Em projetos grandes ou em lugares onde o Javascript vai se tornar complexos, ele é totalmente indicado.
  
Também não estou brigando por causa dos 100kb do framework. O Gzip nesse caso resolve o tamanho. Estou apenas fazendo você pensar duas vezes antes de usar um framework, qualquer um que seja, para fazer algo simples.

O Leo Balter [fez um post sensacional][4] sobre isso dando vários exemplos usando o próprio Tableless.

Lá ele pondera sobre vários pontos, alguns até que nem se aplicam ao Tableless, mas em projetos que talvez você possa estar envolvido, - como testes unitários, compatibilidade cross-browser e alguns outros - e que são muito relevantes quando tratados em websites com densos códigos de JS.

**Update:** Depois do artigo do Leo, aproveitei os pontos que ele citou lá e fiz umas modificações rápidas no Tableless. Ainda tenho várias coisas pra mudar, sabe comequié site novo. Ele fez um outro artigo mostrando uma melhora nos resultados depois dessas modificações. [Dá uma olhada][5].

 [1]: http://tableless.com.br/wp-content/themes/tableless-2014/js/scripts.js
 [2]: http://www.pinceladasdaweb.com.br
 [3]: http://bit.ly/1m8zH8e
 [4]: http://leobalter.github.io/pt-br/jquery/2014/02/19/o-hype-sobre-não-utilizar-jquery.html
 [5]: http://leobalter.github.io/pt-br/jquery/2014/02/19/o-entendimento-técnico-de-uma-cr%C3%ADtica.html