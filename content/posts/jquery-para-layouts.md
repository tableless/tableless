---
title: JQuery para produção de Layouts
authors: Diego Eis
type: post
date: 2010-12-15
excerpt: 'Quando falta a compatibilidade de algumas propriedades do CSS nos browsers ou porque quando não é possível  manipular o HTML manualmente para suprir suas necessidades, o JQuery poderá ajudar.'
url: /jquery-para-layouts/
categories:
  - Javascript
  - CSS
  - HTML
  - JQuery
  - Técnicas e Práticas
tags:
  - JQuery
  - 2010
  - aprenda
  - desenvolvimento web
  - web standards

---
O [JQuery][1] tem me dado um importante suporte para aqueles problemas que o CSS não consegue resolver por falta de compatibilidade em alguns browsers e também para evitar sujar o código HTML com elementos dispensáveis, em ocasiões comuns como no caso da criação de bordas arredondadas.
  
Nestes cenários, invarialmente temos que criar alguns elementos agregados que servirão para dar exclusivamente suporte visual para o layout.
  
Não é bom que sujemos nosso HTML com código que não carregue significado semântico nenhum, mas em alguns casos, como ao fazer bordas arredondadas, a criação destes elementos é necessária. É nesse ponto que o [JQuery][1] pode nos ajudar grandemente.

Se você é desenvolvedor client-side, tenha em mente que você não precisa saber programar para aprender [JQuery][1]. Sua sintaxe é muito simples e pode salvar sua vida quando ocorre problemas de compatibilidade entre browsers. É o que veremos a seguir: como o [JQuery][1] pode nos auxiliar em momentos da falta de suporte do CSS.

### Criando elementos dinamicamente

Suponha que você tenha um botão simples, onde as bordas são arredondadas. Para facilitar nosso exemplo esse botão não terá altura variável, apenas largura. Eu poderia fazer duas imagens: uma imagem seria a borda da esquerda e a outra imagem a borda da da direita. Se fôssemos fazer com HTML e CSS puro, o código seria esse:
  
[cc lang=&#8221;html&#8221;]
  
[texto do botão][2]{.btn}
  
[/cc]

O CSS:
  
[cc lang=&#8221;css&#8221;]
  
.btn {
    
border-radius:10px;
  
}
  
[/cc]

Talvez eu teria que colocar um prefixo para o Frefox (-moz-) entender a borda arredondada, mas vamos simplificar nosso exemplo.

Os IE7-8 não reconheceriam essa propriedade. Mas se seu cliente precisa de que o suporte seja estendido para esses browsers, não há outra escolha a não ser fazer as benditas bordas (ou qualquer outro problema) funcionar no IE.

Uma maneira simples de ser feita é colocando um backgrounds diretamente no LINK, pode ser a borda da esquerda e em outro elemento definiríamos a borda da direita. Criar um elemento para que sua única função seja manter o padrão visual vai de encontro contra toda a ideia de semântica. Fazendo isso também misturamos aquela teoria de separação de formatação com informação. Mesmo assim essa a única solução. É aí que o [JQuery][1] vem nos ajudar. O código HTML, caso fossemos criar um elemento extra, seria:

[cc lang=&#8221;html&#8221;][texto do botão <span class="borderdir"></span>][2]{.btn}[/cc]

Para mantermos a integridade do nosso HTML, criaremos esse elemento via [JQuery][1] da seguinte forma utilizando a função <a href="https://api.[JQuery][1].com/append/&#8221;>append</a>:

[cc lang=&#8221;javascript&#8221;]$(document).ready(function(){
	  
$(&#8216;.btn&#8217;).append(&#8216;<span class="borderdir" />&#8216;);
  
});[/cc]

Já que estes elementos são cridos dinamicamente, os leitores de tela e os indexadores de busca não os leem, logo, o código HTML não fica poluído e você não perde com SEO. A manutenção fica simples de ser mantida e o HTML, se já estiver sob programação server-side não precisará ser modificado manualmente.

### Escolhendo elementos específicos

Outro problema muito comum é a necessidade de ter que escolher elementos específicos no Layout sem ter que adicionar manualmente classes ou tendo que fazer uma condição maluca para ter que capturar tais elementos. Isso seria muito simples se utilizássemos o pseudo-elemento **nth-child** do CSS. O **nth-child** seleciona determinados elementos em uma árvore de elementos. Por exemplo, você tem uma lista e quer pegar o terceiro ítem da lista, você utilizaria algo assim:

[cc lang=&#8221;css&#8221;]ul li:nth-child(3n) {
	  
color:red;
  
}[/cc]

O problema? Nada disso funciona nos IEs. Mas isso é extremamente útil e com [JQuery][1] você pode adicionar uma classe nestes elementos para formatar com CSS.
  
A Home deste site foi feita desta forma. O conteúdo foi criado com um simples LOOP do WordPress que joga o HTML do conteúdo em uma única página. Veja que cada um blocos de texto desta home é diferente. Sem poder utilizar o **nth-child** eu utilizei a função <a href="https://api.[JQuery][1].com/slice/&#8221;>slice</a> do [JQuery][1]:

[cc lang=&#8221;javascript&#8221;]
  
$(document).ready(function(){
	  
$(&#8216;.homeposts article&#8217;).slice(1, 3).addClass(&#8216;destaqueprincipal&#8217;);
	  
$(&#8216;.homeposts article&#8217;).slice(3, 6).addClass(&#8216;destaquethird&#8217;);
	  
$(&#8216;.homeposts article&#8217;).slice(6, 10).addClass(&#8216;destaques&#8217;);
	  
$(&#8216;.homeposts article&#8217;).slice(10, 12).addClass(&#8216;chamadas&#8217;);
  
});
  
[/cc]

Por exemplo, note essa linha:
  
[cc lang=&#8221;javascript&#8221;]
  
$(document).ready(function(){
	  
$(&#8216;.homeposts article&#8217;).slice(1, 3).addClass(&#8216;destaqueprincipal&#8217;);
  
});
  
[/cc]

Aqui eu digo que o primeiro, segundo e terceiro e **elemento article** de **.homeposts** terão uma classe adicional chamada _destaqueprincipal_. E a mesma lógica foi aplicada para os elementos posteriores.

### Utilizando seletores complexos

Outro problema é a inserção de classes em elementos do mesmo gênero mas com funções diferentes, como os campos de formulários. Normalmente, quando produzimos um formulário de contato, por exemplo, precisamos diferenciar os inputs de texto, inputs de checkbox, inputs de radio, inputs de submit etc. Pode ser que estes inputs sejam criados dinamicamente pelo framework utilizado para auxiliar na programação back-end. Nesse caso não temos controle manual nenhum.
  
No melhor dos mundos utilizaríamos [seletores complexos][3] para aplicar um estilo específico para um dos elementos. A sintaxe em CSS ficaria mais ou menos assim:

[cc lang=&#8221;css&#8221;]
  
input[type=&#8221;text&#8221;] {
	  
border:1px solid gray;
  
}
  
[/cc]

O código acima define uma borda preta para os elementos **input** que tenham o atributo **type** cujo valor seja **text**. Você faria isso para cada um dos tipos dos inputs que você gostaria de formatar:

[cc lang=&#8221;css&#8221;]
  
input[type=&#8221;text&#8221;] {border:1px solid gray;}
  
input[type=&#8221;checkbox&#8221;] {border:1px solid green;}
  
input[type=&#8221;submit&#8221;] {border:1px solid red;}
  
input[type=&#8221;radio&#8221;] {border:1px solid yellow;}
  
[/cc]

Esse código pode não funcionar em <span title="leia-se Internet Explorer">alguns browsers</span>, por isso faremos com a ajuda de [JQuery][1].
  
O código é muito simples e na realidade não foge muito da sintaxe do CSS. Adicionaremos uma classe para cada um destes elementos possibilitando a estilização via CSS por meio dessa classe. O código ficaria assim:

[cc lang=&#8221;javascript&#8221;]
  
$(document).ready(function(){
	  
$(&#8216;input[type=&#8221;text&#8221;]&#8217;).addClass(&#8216;inputText&#8217;);
	  
$(&#8216;input[type=&#8221;checkbox&#8221;]&#8217;).addClass(&#8216;inputCheckbox&#8217;);
	  
$(&#8216;input[type=&#8221;submit&#8221;]&#8217;).addClass(&#8216;inputSubmit&#8217;);
	  
$(&#8216;input[type=&#8221;radio&#8221;]&#8217;).addClass(&#8216;inputRadio&#8217;);
  
});
  
[/cc]

Com as classes atribuídas, podemos temos controle total via CSS.

### Conclusão

Estas pequenas dicas contribuem para soluções sustentáveis para seu código. Com um pouco de planejamento você conseguirá manter o controle total do seu código e um alto índice de compatibilidade com os browsers atuais no mercado. A diminuição de hacks no CSS também diminui bastante já que com uma mesma solução, você abrange até os browsers mais antigos.

 [1]: https://tableless.com.br/categoria/client-side/jquery/ "artigos sobre JQuery"
 [2]: #
 [3]: https://tableless.com.br/seletores-complexos-do-css "Introdução aos Seletores complexos"