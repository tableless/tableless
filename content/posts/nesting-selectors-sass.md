---
title: Usando seletores aninhados do SASS com cuidado
author: Diego Eis
type: post
date: 2014-09-22
excerpt: Cuidado com o pesadelo das nesting selectors dos pré-processadores.
url: /nesting-selectors-sass/
categories:
  - CSS
  - SASS
tags:
  - CSS
  - SASS

---
Não é só por que você está usando um pré-processador que as boas práticas de escrita de CSS devem ser ignoradas. Imagine o código abaixo:

<pre class="lang-html">&lt;main class="wrap"&gt;
	&lt;div class="content"&gt;
		&lt;article&gt;
			&lt;p&gt;Lorem &lt;strong&gt;ipsum dolor sit amet&lt;/strong&gt;. Officia rem sed fuga consequatur rerum.&lt;/p&gt;
		&lt;/article&gt;
	&lt;/div&gt;
&lt;/main&gt;
</pre>

E você já deve ter visto um seletor desse tipo:

<pre class="lang-css">.wrap .content article p strong {
  color: #ccc;
}
</pre>

Escrever seletores assim é um tiro no pé. O CSS fica ruim de entender e o trabalho de cascata do CSS &#8211; que é o que faz o CSS tão especial &#8211; pode se perder, já que você vai precisar fazer um outro seletor, mais específico, para sobreescrever essa formatação caso necessário.

Há outro exemplo mais comum, que é muito visto quando tentamos separar a estrutura e o estilo visual dos elementos. Fica algo assim:

<pre class="lang-html">&lt;div class="features"&gt;
  &lt;div class="box rounded bordered bg-blue"&gt;
    &lt;h1&gt;Título&lt;/h1&gt;
    &lt;p&gt;Lorem &lt;strong&gt;ipsum dolor sit amet&lt;/strong&gt;. Officia rem sed fuga consequatur rerum.&lt;/p&gt;
  &lt;/div&gt;
  &lt;div class="box rounded bordered bg-blue"&gt;
    &lt;h1&gt;Título&lt;/h1&gt;
    &lt;p&gt;Lorem &lt;strong&gt;ipsum dolor sit amet&lt;/strong&gt;. Officia rem sed fuga consequatur rerum.&lt;/p&gt;
  &lt;/div&gt;
  &lt;div class="box rounded bordered bg-blue"&gt;
    &lt;h1&gt;Título&lt;/h1&gt;
    &lt;p&gt;Lorem &lt;strong&gt;ipsum dolor sit amet&lt;/strong&gt;. Officia rem sed fuga consequatur rerum.&lt;/p&gt;
  &lt;/div&gt;
&lt;/div&gt;
</pre>

É claro que é muito difícil escrever um seletor e um código HTML dessa forma consciente. Você vai perceber que está fazendo alguma burrice e vai pensar duas vezes antes de continuar. Assim espero. Mas quando usamo um pré-processador, é bastante comum nessa armadilha por causa dos seletores aninhados, ou em um termo mais bonito em inglês **nested selectors**.

Veja um exemplo de **nested selector**:

<pre class="lang-sass">.features {
  background-color: #cccccc;
  .box {
    border-radius: 3px;
    border: 1px solid #666666;
    background-color: white;
    p {
      font-size: 1rem;
      line-height: 1.2;
      color: #333333;
    }
  }
}
</pre>

Coisa linda. Não é necessário repetir o início do seletor a cada elemento que você quer formatar dentro de `.features`, o SASS fará isso pra você. Veja o output desse código:

<pre class="lang-css">.features {
  background-color: #ccc;
}
.features .box {
  border-radius: 3px;
  border: 1px solid #666;
  background-color: white;
}
.features .box p {
  font-size: 1rem;
  line-height: 1.2;
  color: #333;
}
</pre>

Até aqui tudo gerenciável. Mas suponha que você tenha o código abaixo:

<pre class="lang-html">&lt;div class="container"&gt;
  &lt;div class="content"&gt;
    &lt;div class="features"&gt;
      &lt;div class="box rounded bordered bg-blue"&gt;
        &lt;h1&gt;T&iacute;tulo&lt;/h1&gt;
        &lt;p&gt;Lorem &lt;strong&gt;ipsum dolor sit amet&lt;/strong&gt;. Officia rem sed fuga consequatur rerum.&lt;/p&gt;
      &lt;/div&gt;
      &lt;div class="box rounded bordered bg-blue"&gt;
        &lt;h1&gt;T&iacute;tulo&lt;/h1&gt;
        &lt;p&gt;Lorem &lt;strong&gt;ipsum dolor sit amet&lt;/strong&gt;. Officia rem sed fuga consequatur rerum.&lt;/p&gt;
      &lt;/div&gt;
      &lt;div class="box rounded bordered bg-blue"&gt;
        &lt;h1&gt;T&iacute;tulo&lt;/h1&gt;
        &lt;p&gt;Lorem &lt;strong&gt;ipsum dolor sit amet&lt;/strong&gt;. Officia rem sed fuga consequatur rerum.&lt;/p&gt;
      &lt;/div&gt;
    &lt;/div&gt;
  &lt;/div&gt;
&lt;/div&gt;
</pre>

Aí você faça algo assim usando SASS:

<pre class="lang-scss">.container {
  max-width: 1200px;
  margin: 0 auto;

  .content {
    padding: 0 20px;

    .features {
      background-color: #ccc;

      .box {
        border-radius: 5px;

        p {
          color: #333;

          strong {
            background-color: #fff;
          }
        }
      }
    }
  }
}
</pre>

O código final será desse jeito:

<pre class="lang-css">.container {
  max-width: 1200px;
  margin: 0 auto;
}

.container .content {
  padding: 0 20px;
}

.container .content .features {
  background-color: #ccc;
}

.container .content .features .box {
  border-radius: 5px;
}

.container .content .features .box p {
  color: #333;
}

.container .content .features .box p strong {
  background-color: #fff;
}
</pre>

Não é incomum acontecer isso quando você está aprendendo a usar pré-processadores, mas isso pode acontecer facilmente em grandes projetos. Existem muitos problemas ao produzirmos código assim, mas os principais motivos são a geração de código inútil, aumentando o tamanho do seu arquivo final e principalmente a quebra da especificidade e a herança do código CSS. A briga de `!important` vai acontecer e você vai passar a metade do tempo resolvendo conflitos de formatação. Isso pode sempre ficar pior conforme você aninha cada vez mais os seletores. **O segredo aqui é usar no máximo 3 aninhamentos**. Há lugares que [aconselham até 4 aninhamentos][1], mas aí eu acho muito. Um código bem feito naturalmente vai ter entre 2 ou 3 aninhamentos. Você não precisa começar a formatar os elementos iniciando seu seletor sempre do elemento pai. No nosso exemplo, tudo ficaria mais higienizado se fizessemos um código assim:

<pre class="lang-scss">.container {
  max-width: 1200px;
  margin: 0 auto;
}
.content {
  padding: 0 20px;
}

.features {
  background-color: #ccc;

  .box {
    border-radius: 5px;

    p {
      color: #333;

      strong {
        background-color: #fff;
      }
    }
  }
}
</pre>

O código gerado ficaria assim: 

<pre class="lang-css">.container {
  max-width: 1200px;
  margin: 0 auto;
}

.content {
  padding: 0 20px;
}

.features {
  background-color: #ccc;
}

.features .box {
  border-radius: 5px;
}

.features .box p {
  color: #333;
}

.features .box p strong {
  background-color: #fff;
}
</pre>

Dependendo do caso, talvez até daria para tirar o aninhamento de `.features`. Ficaria assim:

<pre class="lang-scss">.container {
  max-width: 1200px;
  margin: 0 auto;
}

.content {
  padding: 0 20px;
}

.features {
  background-color: #ccc;
}

.box {
  border-radius: 5px;

  p {
    color: #333;

    strong {
      background-color: #fff;
    }
  }
}
</pre>

Se você seguir as boas práticas de CSS que já falamos [aqui][2] e [aqui][3] você estará a salvo.

Sugiro duas ferramentas interessantes para testar códigos SASS. Um deles é o [SaasMeister][4], que converte código SASS em código CSS normal. E o outro é o [ScssConverter][5], que converte código SASS para SCSS.

 [1]: http://thesassway.com/beginner/the-inception-rule
 [2]: http://tableless.com.br/oocss-smacss-bem-dry-css-afinal-como-escrever-css/ "OOCSS, SMACSS, BEM, DRY CSS: afinal, como escrever CSS?"
 [3]: http://tableless.com.br/6-estrategias-para-melhorar-a-organizacao-do-seu-css-2/ "6 estratégias para melhorar a organização do seu CSS"
 [4]: http://sassmeister.com/
 [5]: http://sasstoscss.com/