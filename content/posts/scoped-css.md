---
title: Scoped CSS
authors: Almir Filho
type: post
date: 2012-09-13
excerpt: Scoped CSS é um novo recurso do HTML5 nos permite definir estilos que serão aplicados apenas em um determinado escopo de marcação.
url: /scoped-css/
dsq_thread_id: 832493549
categories:
  - CSS
  - HTML
  - HTML5
  - Mercado
  - Tecnologia e Tendências
tags:
  - CSS
  - desenvolvimento web
  - html5
  - Na Prática
---

Scoped CSS é uma pequena novidade no HTML5 que nos permite inserir estilos CSS que sejam apenas aplicado em um determinado lugar de uma página, de modo que os estilos restantes da mesma página não sejam afetados. Para isso, foi definido um novo atributo **scoped** que deve ser utilizado na _tag_ **&lt;style&gt;**.

Pela definição da especificação:

> O atributo **scoped** é um atributo _booleano_. Se for setado, indica que os estilos (da tag) serão aplicados apenas na sub-árvore do elemento pai deste mesmo elemento, ao contrário de todo o documento.
> — WHATWG

## Antes de tudo

Se você quiser testar os exemplos mostrados neste post no browser, terá que usar o Google Chrome versão 20 ou superior, pois é o único que já dá suporte a **scoped CSS**. Com seu Chrome aberto, digite na barra de endereços: **chrome://flags**. Vai abrir a tela de configurações das _flags_ do Chrome, procure por **Enable <style scoped&gt;**, e ative a opção (se já não estiver ativada). Agora o reinicie e é só mandar ver.

## Show me the <del>money</del> code

Para entendermos melhor, vamos a parte boa, nerds! No trecho de HTML abaixo, temos um cenário bem simples: 2 parágrafos soltos e 2 parágrafos agrupados em uma **&lt;div&gt;**. Dentro da **&lt;div&gt;** há também um elemento **&lt;style&gt;** que define a cor vermelha para os parágrafos (**&lt;p&gt;**):

<pre class="lang-html">&lt;p&gt;I was crowned with a spike right thru my head.&lt;/p&gt;
&lt;p&gt;But it's all right now, in fact, it's a gas!&lt;/p&gt;
&lt;div&gt;
    &lt;style&gt;
        p { color: red } /* parágrafos vermelhos */
    &lt;/style&gt;
    &lt;p&gt;But it's all right, Im jumpin jack flash,&lt;/p&gt;
    &lt;p&gt;Its a gas! gas! gas!&lt;/p&gt;
&lt;/div&gt;
</pre>

OK, do jeito como está no código acima, o navegador aplicará os estilos de **&lt;style&gt;** em **toda a página**, ou seja, todos os parágrafos (**&lt;p&gt;**) serão da cor vermelha:

<div class="exemplo-almir" style="border: 1px solid #ddd;background: #eee;padding: 10px;margin-bottom: 10px;color: red">
  I was crowned with a spike right thru my head.<br /> But it&#8217;s all right now, in fact, it&#8217;s a gas!</p> 
  
  <div>
    But it&#8217;s all right, Im jumpin jack flash,<br /> Its a gas! gas! gas!
  </div>
</div>

Aplicando o atributo **scoped** em **&lt;style&gt;**, os estilos apenas serão aplicados ao mesmo escopo, ou seja, nos dois últimos parágrafos:

<pre class="lang-html">&lt;p&gt;I was crowned with a spike right thru my head.&lt;/p&gt;
&lt;p&gt;But it's all right now, in fact, it's a gas!&lt;/p&gt;
&lt;div&gt;
    &lt;!-- aplicando atributo scoped --&gt;
    &lt;style scoped&gt;
        p { color: red }
    &lt;/style&gt;
    &lt;p&gt;But it's all right, Im jumpin jack flash,&lt;/p&gt;
    &lt;p&gt;Its a gas! gas! gas!&lt;/p&gt;
&lt;/div&gt;
</pre>

E o resultado será:

<div class="exemplo-almir" style="border: 1px solid #ddd;background: #eee;padding: 10px;margin-bottom: 10px">
  I was crowned with a spike right thru my head.<br /> But it&#8217;s all right now, in fact, it&#8217;s a gas!</p> 
  
  <div style="color: red">
    But it&#8217;s all right, Im jumpin jack flash,<br /> Its a gas! gas! gas!
  </div>
</div>

## Grande coisa&#8230;

É isso que você deve estar pensando agora. &#8220;Grande coisa, não precisamos disso, apenas podemos definir uma **classe** ou **id** e estilizá-los _like the old times_&#8220;. Eu concordo que devemos utilizar determinadas soluções apenas quando for realmente necessário, eu mesmo não sairia por ai inserindo estilos **&lt;style scoped&gt;** em tudo quanto é lugar. Iria ser uma zona.

## O pulo do gato

Algumas aplicações podem acrescentar elementos **&lt;style&gt;** programaticamente a uma página. Nestes casos, há o perigo de que as novas regras afetem o conteúdo da página de forma não intencional. Ao utilizar o atributo **scoped**, as aplicações podem impedir que este infeliz efeito colateral aconteça.

Sendo assim, utilizar **scoped** em estilos pode ser uma solução elegante para a **componentização** de aplicações _web_ de terceiros. Hoje em dia (quase) todo mundo faz uso de _plugins_ de _widgets_ e de diversos tipos em suas aplicações, e muita gente faz <a title="Mashup (Wikipedia)" href="https://pt.wikipedia.org/wiki/Mashup_(aplica%C3%A7%C3%A3o_web)" target="_blank"><em>mashups</em></a> com várias dessas aplicações, misturando tudo em uma única solução. Isto não é nenhuma novidade – há muito tempo.

Então, o que acontece? Sabendo que muitas pessoas reutilizarão um determinado _plugin_, são usados diversos nomes de classes CSS de uma maneira a evitar conflitos com os estilos de outros _sites_ – onde farão uso desses _plugins_.

Um ótimo exemplo é o [Disqus][1]. Para usar o Disqus, apenas precisamos inserir um pequeno _script_ na nossa página, e ele cuidará de todo o resto. Ao visitar uma página que utiliza o Discus, esse _script_ incluirá as marcações necessárias para os comentários já inseridos e seu formulário, além de seus estilos CSS, imagens, e até mesmo outros _scripts_. Ou seja, é um exemplo completo de aplicação de terceiros rodando em sites do mundo inteiro. Agora, se formos analisar os códigos HTML que são inseridos, teremos nomes de classes CSS como: **dsq-comments**, **dsq-comments-head**, **dsq-comments-body**, **dsq-comments-message**, **dsq-comments-eu-gosto-de-rolling-stones**, **dsq-comments-tudo-o-que-der-na-telha**, etc. Como seria legal se esses nomes super extensos não fossem mais necessários, hein?

## Problemas

Em meus testes, encontrei alguns empecilhos. Tentei utilizar **scoped** primeiramente em elementos que já tinham sido estilizados – não deu certo –, depois tentei aninhar estilos **scoped** e também não funcionou – francamente, não sei se é certo/possível fazer isto, e mesmo assim, penso que isso não serviria pra nada, é o tipo de coisa que só iria complicar a nossa vida (e de complexidade, já basta ser desenvolvedor web nos dias atuais), mas, pelo bem da ciência, realizei esse teste (aparentemente) inútil.

#### Aplicando _scoped_ a elementos já estilizados

Quando a página já possuía estilos – por exemplo, no **&lt;head&gt;** – as propriedades que já tinham sido definidas não eram modificadas pelos estilos **scoped**, apenas aquelas que ainda não tinham sido alteradas por nenhum CSS. Por exemplo:

<pre class="lang-html">&lt;head&gt;
    &lt;style&gt;
        p { color: gray }
    &lt;/style&gt;
&lt;/head&gt;
&lt;body&gt;
    &lt;p&gt;I was crowned with a spike right thru my head.&lt;/p&gt;
    &lt;p&gt;But it's all right now, in fact, it's a gas!&lt;/p&gt;
    &lt;div&gt;
        &lt;style scoped&gt;
            p {
                color: red;
                font-size: 1.4em;
            }
        &lt;/style&gt;
        &lt;p&gt;But it's all right, Im jumpin jack flash,&lt;/p&gt;
        &lt;p&gt;Its a gas! gas! gas!&lt;/p&gt;
    &lt;/div&gt;
&lt;/body&gt;
</pre>

Se tentarmos fazer como acima, o resultado será:

<div class="exemplo-almir" style="border: 1px solid #ddd;background: #eee;padding: 10px;margin-bottom: 10px;color: gray">
  I was crowned with a spike right thru my head.<br /> But it&#8217;s all right now, in fact, it&#8217;s a gas!</p> 
  
  <div style="color: gray;font-size: 1.4em">
    But it&#8217;s all right, Im jumpin jack flash,<br /> Its a gas! gas! gas!
  </div>
</div>

Perceba que o único estilo de escopo que foi aplicado foi a regra **font-size: 1.4em** e a cor vermelha simplesmente foi ignorada. Sinceramente eu não faço a mínima ideia do porquê disto, também não vejo muito sentido – poderia até ser um erro de implementação do navegador, mas não posso afirmar isto com tanta veemência.

#### A pseudo-classe :scope

Depois de muito pesquisar, achei uma &#8220;solução&#8221;, por assim dizer. Eis que existe uma **pseudo-classe **:scope**! Se usarmos esse cara como seletor das regras, tudo funciona perfeitamente. No exemplo acima, só faríamos:</p> 

<pre class="lang-html">&lt;style scoped&gt;
    /* adicionando a pseudo-classe :scope */
    :scope p {
        color: red;
        font-size: 1.4em;
    }
&lt;/style&gt;
</pre>

Agora sim, tudo como esperado:

<div class="exemplo-almir" style="border: 1px solid #ddd;background: #eee;padding: 10px;margin-bottom: 30px;color: gray">
  I was crowned with a spike right thru my head.<br /> But it&#8217;s all right now, in fact, it&#8217;s a gas!</p> 
  
  <div style="color: red;font-size: 1.4em">
    But it&#8217;s all right, Im jumpin jack flash,<br /> Its a gas! gas! gas!
  </div>
</div>

#### Aninhando estilos _scoped_

Tentei também aninhar estilos **scoped**, mas parece que isso não funciona legal, e acredito que seja proposital. Mas essa parte eu deixo com vocês 😉 Testem colocar um **&lt;style scoped&gt;** dentro de outro. Aqui mesmo eu não consegui muito resultado, ocorre o mesmo problema com as propriedades CSS que já foram definidas – são ignoradas e não funcionam nem mesmo adicionando a pseudo-classe **:scoped**. Se alguém obtiver algum resultado diferente do meu, comenta ai!

## Suporte

No momento, apenas Google Chrome versão 20+.

 [1]: https://disqus.com "Disqus"