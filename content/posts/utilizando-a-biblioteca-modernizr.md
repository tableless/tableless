---
title: Utilizando a Biblioteca Modernizr
author: Diego Eis
type: post
date: 2011-10-17
excerpt: Alguns browsers não aceitam as novas features de CSS3 e HTML5. Saiba como detectá-los e tratá-los com a biblioteca Modernizr.
url: /utilizando-a-biblioteca-modernizr/
tweetbackscheck:
  - 1356390410
shorturls:
  - 'a:3:{s:9:"permalink";s:31:"http://tableless.com.br/?p=4431";s:4:"isgd";s:19:"http://is.gd/mVMoin";s:7:"tinyurl";s:26:"http://tinyurl.com/3p4ogu9";}'
twittercomments:
  - 'a:0:{}'
dsq_thread_id: 503040422
categories:
  - Acessibilidade
  - Browsers
  - Código
  - CSS3
  - HTML
  - HTML5
  - JavaScript
  - Técnicas e Práticas
tags:
  - 2011
  - acessibilidade
  - aprenda
  - CSS3
  - html5
  - JavaScript
  - modernizr
  - tecnicascss

---
### Problemas de compatibilidade

Quando produzimos um site os problemas de compatibilidade fazem parte da regra do jogo. Para tentar contornar estes problemas utilizamos hacks, comentários condicionais, sniffing de browsers e outras coisas, que muitas vezes mais prejudicam do que ajudam.

Para ajudar mais ainda o CSS3 e o HTML5 apareceram derrubando tudo, e o problema de compatibilidade que já era chato, ficou mais chato que meia molhada. Embora os browsers estejam muito mais atuais e suportando propriedades avançadas de CSS3 e HTML5, não é garantia que todos eles suportem as mesmas propriedades. E é aqui que começamos a ter problemas novamente, como no passado. 

Como você consegue reconhecer quem um determinado browser suporta CSS Animation? Como você sabe que o browser conhece LocalStorage do HTML5? Você não vai ficar olhando numa tabelinha toda vez que tiver essas dúvidas para fazer um visual ou uma solução alternativa para tais browsers.

É por essas e outras que você utilizará a Modernizr.

### O que é a Modernizr

Modernizr é uma pequena biblioteca Javascript que detecta a disponibilidade das novas características do HTML5 e CSS3 nos browsers. Muitas destas características já estão implementadas nos browsers, mas é muito chato você decorar quais novidades os browsers já estão suportando. O que a Modernizr faz é simples: ela te diz quais features um determinado browser suporta e insere classes no HTML para que você possa utilizar para fazer uma versão alternativa de visual ou solução.

Entenda que a Modernizr não é um sniffing de browser. Ela é diferente. A Modernizr faz o trabalho de detectar das seguintes formas:

  * Ela testa 40 features de CSS3 e HTML5 em alguns milisegundos.
  * Depois ela cria objetos javascript que contém os resultados destes testes.
  * Aí são adicionadas classes no elemento HTML descrevendo exatamente quais propriedades e novidades são ou não nativamente suportadas.
  * Depois disso você consegue ter os resultados descritos nos navegadores dinamicamente e então pode tomar decisões criando alternativas para aquelas propriedades não suportadas pelos browsers antigos.

### Como funciona

É simples: primeiro você baixa a versão mais atual da biblioteca no endereço <http://www.modernizr.com/>. O interessante é que você tem a opção para personalizar a biblioteca, indicando quais features você quer que a Modernizr teste no seu projeto.

Depois você inclui esse pacote no seu HTML:

<pre class="lang-html">&lt;!DOCTYPE html&gt;

&lt;html lang="pt-br"&gt;
&lt;head&gt;
	&lt;meta charset="utf-8"&gt;
	&lt;title&gt;Teste de Modernizr&lt;/title&gt;
	&lt;script src="modernizr-2.0.6.js"&gt;&lt;/script&gt;
&lt;/head&gt;
&lt;body&gt;

&lt;/body&gt;
&lt;/html&gt;
</pre>

Feito isso, insira uma classe _no-js_ no elemento _HTML_:

<pre class="lang-html">&lt;html class="no-js" lang="pt-br"&gt;
</pre>

Quando a Modernizr rodar, ela irá substituir essa classe para uma _js_ se o browser estiver com o Javascript ligado, já te dando um feedback para tomar alguma atitude se o usuário estiver com o Javascript desligado.

Junto com essa mudança são adicionadas outras classes, indicando o que o browser aceita nativamente ou o que ele não aceita. Ficará algo parecido com isso:

<pre class="lang-html">&lt;html class=" js flexbox canvas canvastext webgl no-touch geolocation postmessage websqldatabase no-indexeddb hashchange history draganddrop websockets rgba hsla multiplebgs backgroundsize borderimage borderradius boxshadow textshadow opacity cssanimations csscolumns cssgradients cssreflections csstransforms csstransforms3d csstransitions fontface generatedcontent video audio localstorage sessionstorage webworkers applicationcache svg inlinesvg smil svgclippaths" lang="pt-br"&gt;
</pre>

O browser que eu utilizei é o Safari/Mac. Pelo visto ele aceita bastante coisa. 😉
  
O que o browser não aceita, a Modernizr insere uma classe com o prefixo **no-** antes da classe, por exemplo: no-boxshadow, no-geolocation, no-touch etc.

A Modernizr também cria um objeto Javascript contendo um valor booleano para cada uma dessas features, possibilitando a criação de testes. Um exemplo:

<pre class="lang-javascript">if (Modernizr.geolocation) {
       alert("Aceita")
} else {
       alert("Não Aceita")
}
</pre>

### Exemplos de utilidade

Exemplo bem básico: imagine que você queira utilizar o box-shadow em seu projeto. Browsers como o IE6,7,8 não reconhecem essa feature, então seria interessante darmos uma alternativa, como por exemplo, colocando uma borda em vez de sombra. Assim o elemento não fica tão diferente do que deveria.

Como a Modernizr colocou uma classe no elemento HTML referente a aceitação das features, podemos utilizá-la fazendo assim:

<pre class="lang-css">.loginBox {
	box-shadow:0 10px 10px rgba(0, 0, 0, 0.3);
}

.no-boxshadow .loginBox {
	border: 1px solid #CCC;
	border-bottom: 3px solid #CCC;
}
</pre>

Assim, se o browser não aceitar a propriedade box-shadow o usuário verá uma borda no lugar. Você pode fazer isso com praticamente qualquer nova feature do CSS3 e do HTML5. Uma [listagem completa dessas features suportadas está aqui][1].

Ah, mais uma coisa: provavelmente você já utiliza um scriptzinho _html5.js_ para fazer com o que os Internet Explorers reconheçam as tags do HTML5, correto? O Modernizr já faz isso automaticamente. Sugiro que pare de utilizar o html5.js e passe a utilizar a Modernizr somente.

A Modernizr facilita demais as coisas. A ideia é que você não prive seus projetos da utilização de features novas. A produção vai ficar mais eficaz e seu projeto sempre estará atualizado com as melhores práticas do mercado. Adote a Modernizr e seja feliz.

Sugiro que você [dê uma lida na documentação][2] da Modernizr. Tem bastante coisa interessante lá que você deveria saber.

 [1]: http://bit.ly/oA9jHu "link externo"
 [2]: http://www.modernizr.com/docs/ "link externo para a documentação da Modernizr"