---
title: Ferramentas de diagnóstico
author: Diego Eis
type: post
date: 2011-04-11
excerpt: 'Quando algo de estranho acontece, é bom estar preparado. '
url: /ferramentas-de-diagnostico/
tweetbackscheck:
  - 1356470968
shorturls:
  - 'a:3:{s:9:"permalink";s:50:"http://tableless.com.br/ferramentas-de-diagnostico";s:7:"tinyurl";s:26:"http://tinyurl.com/3gkda78";s:4:"isgd";s:19:"http://is.gd/N1MZdH";}'
twittercomments:
  - 'a:3:{i:169918828178976768;s:7:"retweet";i:189804021823971328;s:7:"retweet";i:189803381789958144;s:7:"retweet";}'
tweetcount:
  - 3
dsq_thread_id: 503040204
categories:
  - Browsers
  - Código
  - CSS
  - HTML
tags:
  - 2011
  - Browsers
  - desenvolvimento
  - desenvolvimento web
  - firefox
  - internet explorer
  - Na Prática

---
Se você escreve CSS e HTML provavelmente tem problemas de compatibilidade e visualização. Isso é normal, acontece com os melhores desenvolvedores. Quando isso acontece, o melhor a se fazer é um trabalho investigativo. Esse trabalho normalmente é ingrato porque você demora horas investigando o seu código para encontrar o erro e geralmente esse erro é solucionado com uma linha de código. Para você descobrir qual é essa linha, você precisa de ferramentas que te ajudem a decifrar todo o problema. Vou indicar algumas aqui que você já deve conhecer.

#### Ferramentas de Inspeção

Hoje a maioria dos browsers tem sua própria ferramenta de inspeção. O Firefox incorporou a [Firebug][1], o IE tem a <a href="http://msdn.microsoft.com/en-us/library/dd565628(v=vs.85).aspx" rel="external">Developer Tool</a>, o Chrome e o Safari tem o [web inspector][2] do próprio Webkit. O Opera usa o [Dragonfly][3].

Com estas ferramentas você consegue facilmente encontrar o elemento, verificar o seu estilo CSS e entender qual das propriedades está causando o problema. Você consegue editar essas propriedades e ver o resultado ali mesmo.
  
Entenda que essas ferramentas não são utilizadas para salvar seu CSS diretamente servem apenas para fazer o trabalho investigativo.

Além de nos ajudar com HTML e CSS, os &#8220;inspectors&#8221; nos ajudam muito com debugging de Javascript. Você consegue localizar exatamente um determinado problema adicionando observer points para verificar o funcionamento de partes do script.

#### XRAY

O <a href="http://www.westciv.com/xray/" rel="external">XRAY</a> é um bookmarklet que te mostra as informações sobre um determinado elemento apenas clicando em cima dele. Você salva o bookmarklet e pronto. Clicando em qualquer elemento, você consegue informações como tamanho, nome da classe e do id, hierarquia, margens e qualquer outro estilo relacionado ao elemento.

#### SelectORacle

Você já deve ter visto algum seletor muito, mas muito complexo e difícil de se entender. Algo do tipo:

[cc lang=&#8221;css&#8221;]
  
body > ol > li p;
  
:not(a);
  
p:not(.section);
  
body > h2:not(:first-of-type):not(:last-of-type);
  
ul li:nth-child(2n+3):not(:last-child);
  
ol li:nth-child(-3n+9);
  
ol li:nth-child(7n-3);
  
button:not([DISABLED]);
  
html|*:not(:link);
  
[/cc]

Se você parar alguns preciosos minutos você consegue entender exatamente o que cada um dos seletores quer dizer. O <a href="http://gallery.theopalgroup.com/selectoracle/" rel="external">SelectORacle</a> te fala em segundos o que cada um dos seletores quer dizer, explicando em poucas palavras cada uma das funções.

#### Validadores de HTML e CSS

Validar seu HTML e CSS não é ponto crucial para a aprovação do código pelo cliente, mas ele validar o código é muito importante para que ele não vá para a produção com erros de sintaxe. Estes erros podem causar grande parte dos erros visuais de crossbrowser. Cada browser se comporta diferente ao encontrar uma tag aberta ou colocada no lugar errado. Se o IE quebra o layout porque a tag não está fechada da forma correta, mas nos outros browsers o visual da página aparece normalmente, você logo fará um Hack para consertar o problema no IE.
  
Por isso é interssante que antes de incluir um CSS Hack em seu código, procure a SOLUÇÃO do problema antes de fazer um &#8220;workaround&#8221;.

O W3C disponibiliza o <a href="http://validator.w3.org/" rel="external">validador de HTML</a>, que já está entendendo algumas coisas de HTML5. E o <a href="http://jigsaw.w3.org/css-validator/" rel="external">validador de CSS</a>, que ainda não entende CSS3.

 [1]: https://addons.mozilla.org/pt-br/firefox/addon/firebug/
 [2]: http://trac.webkit.org/wiki/WebInspector
 [3]: http://www.opera.com/dragonfly/