---
title: Estruturando o código CSS
author: Diego Eis
type: post
date: 2007-02-22
url: /estruturando-o-codigo-css/
tweetbackscheck:
  - 1356404816
shorturls:
  - 'a:3:{s:9:"permalink";s:49:"http://tableless.com.br/estruturando-o-codigo-css";s:7:"tinyurl";s:26:"http://tinyurl.com/4yphvyu";s:4:"isgd";s:19:"http://is.gd/kUcZwK";}'
twittercomments:
  - 'a:0:{}'
dsq_thread_id: 503036720
categories:
  - Artigos
  - Tecnologia e Tendências
tags:
  - cotidiano
  - Técnicas e Práticas

---
Este era um assunto que eu queria falar aqui a muito tempo. Vi [este link][1] no [URL Sinistras][2] e me animei a escrever sobre.

Estruturar o código CSS de uma maneira simples e intuitiva ajuda muito no desenvolvimento. Já vi várias pessoas fazendo códigos mirabolantes e depois perdendo tempo porque havia problemas de conflito no CSS.

Vou falar aqui como eu monto meu CSS ou como pelo menos eu tento montá-lo. Estes hábitos são algumas coisas que me torna produtivo quando preciso executar alguma modificação no layout.

### Formatando de fora pra dentro

Muita gente não tem uma regra de onde começa a formatar e de onde termina. Isso ajuda a organizar seu código CSS de uma maneira tão lógica quanto uma estrutura HTML.

Formate seu código começando dos elementos mais amplos para os mais específicos. Comece pela tag HTML (se tiver formatação para ela), depois passe para o BODY, logo após para o div que envolve todo o site (eu costumo chamar de #geral) e assim para os elementos que dividem as seções do site (normalmente: cabecalho, coluna da esquerda, colunas da direita, colunas do meio, rodape etc). Logo após, passe para os elementos que ficam dentro destas divisões e formate-os individualmente.

Veja o seguinte código HTML:

`<html><br />
<body><br />
<div id="geral"><br />
<div id="topo"><br />
<h1><a href="#">Logo do Site</a></h1><br />
<div class="menu"><br />
<ul><br />
<li><a href="#">Home</a></li><br />
<li><a href="#">Produtos</a></li><br />
<li><a href="#">Serviços</a></li><br />
<li><a href="#">Contato</a></li><br />
</ul><br />
</div><br />
</div><br />
</div><br />
</body><br />
</html>`

Código CSS:

``Este era um assunto que eu queria falar aqui a muito tempo. Vi [este link][1] no [URL Sinistras][2] e me animei a escrever sobre.

Estruturar o código CSS de uma maneira simples e intuitiva ajuda muito no desenvolvimento. Já vi várias pessoas fazendo códigos mirabolantes e depois perdendo tempo porque havia problemas de conflito no CSS.

Vou falar aqui como eu monto meu CSS ou como pelo menos eu tento montá-lo. Estes hábitos são algumas coisas que me torna produtivo quando preciso executar alguma modificação no layout.

### Formatando de fora pra dentro

Muita gente não tem uma regra de onde começa a formatar e de onde termina. Isso ajuda a organizar seu código CSS de uma maneira tão lógica quanto uma estrutura HTML.

Formate seu código começando dos elementos mais amplos para os mais específicos. Comece pela tag HTML (se tiver formatação para ela), depois passe para o BODY, logo após para o div que envolve todo o site (eu costumo chamar de #geral) e assim para os elementos que dividem as seções do site (normalmente: cabecalho, coluna da esquerda, colunas da direita, colunas do meio, rodape etc). Logo após, passe para os elementos que ficam dentro destas divisões e formate-os individualmente.

Veja o seguinte código HTML:

`<html><br />
<body><br />
<div id="geral"><br />
<div id="topo"><br />
<h1><a href="#">Logo do Site</a></h1><br />
<div class="menu"><br />
<ul><br />
<li><a href="#">Home</a></li><br />
<li><a href="#">Produtos</a></li><br />
<li><a href="#">Serviços</a></li><br />
<li><a href="#">Contato</a></li><br />
</ul><br />
</div><br />
</div><br />
</div><br />
</body><br />
</html>`

Código CSS:

`` 

Tente seguir a estrutura HTML como referência. Mantendo essa organização, fica simples encontrar os elementos no código CSS.

### Coloque informação importante nos comentários

Comentar qualquer código é sempre uma boa pedida. Em vez de fazer comentários sucintos e que não dizem nada além do nome do div, faça comentários que contenham informação sobre aquela parte específica do layout.

`/* #topo - Div que contém LOGO, #menu e #busca - Elemento Pai é o #geral */`

Isso se torna uma referência para profissionais que farão modificações posteriores em seu código.

### Caminhos completos em seletores

Sempre use os caminhos inteiros nos seletores. Isso evita erros de conflito no arquivo CSS. Sendo específico você mantém corretamente as heranças dos elementos e consegue ter mais controle sobre seu código.

`div#topo div#menu ul li a {...}`

### Ids e classes, use com moderação

Já vi muita gente fazendo isso:
  
```Este era um assunto que eu queria falar aqui a muito tempo. Vi [este link][1] no [URL Sinistras][2] e me animei a escrever sobre.

Estruturar o código CSS de uma maneira simples e intuitiva ajuda muito no desenvolvimento. Já vi várias pessoas fazendo códigos mirabolantes e depois perdendo tempo porque havia problemas de conflito no CSS.

Vou falar aqui como eu monto meu CSS ou como pelo menos eu tento montá-lo. Estes hábitos são algumas coisas que me torna produtivo quando preciso executar alguma modificação no layout.

### Formatando de fora pra dentro

Muita gente não tem uma regra de onde começa a formatar e de onde termina. Isso ajuda a organizar seu código CSS de uma maneira tão lógica quanto uma estrutura HTML.

Formate seu código começando dos elementos mais amplos para os mais específicos. Comece pela tag HTML (se tiver formatação para ela), depois passe para o BODY, logo após para o div que envolve todo o site (eu costumo chamar de #geral) e assim para os elementos que dividem as seções do site (normalmente: cabecalho, coluna da esquerda, colunas da direita, colunas do meio, rodape etc). Logo após, passe para os elementos que ficam dentro destas divisões e formate-os individualmente.

Veja o seguinte código HTML:

`<html><br />
<body><br />
<div id="geral"><br />
<div id="topo"><br />
<h1><a href="#">Logo do Site</a></h1><br />
<div class="menu"><br />
<ul><br />
<li><a href="#">Home</a></li><br />
<li><a href="#">Produtos</a></li><br />
<li><a href="#">Serviços</a></li><br />
<li><a href="#">Contato</a></li><br />
</ul><br />
</div><br />
</div><br />
</div><br />
</body><br />
</html>`

Código CSS:

``Este era um assunto que eu queria falar aqui a muito tempo. Vi [este link][1] no [URL Sinistras][2] e me animei a escrever sobre.

Estruturar o código CSS de uma maneira simples e intuitiva ajuda muito no desenvolvimento. Já vi várias pessoas fazendo códigos mirabolantes e depois perdendo tempo porque havia problemas de conflito no CSS.

Vou falar aqui como eu monto meu CSS ou como pelo menos eu tento montá-lo. Estes hábitos são algumas coisas que me torna produtivo quando preciso executar alguma modificação no layout.

### Formatando de fora pra dentro

Muita gente não tem uma regra de onde começa a formatar e de onde termina. Isso ajuda a organizar seu código CSS de uma maneira tão lógica quanto uma estrutura HTML.

Formate seu código começando dos elementos mais amplos para os mais específicos. Comece pela tag HTML (se tiver formatação para ela), depois passe para o BODY, logo após para o div que envolve todo o site (eu costumo chamar de #geral) e assim para os elementos que dividem as seções do site (normalmente: cabecalho, coluna da esquerda, colunas da direita, colunas do meio, rodape etc). Logo após, passe para os elementos que ficam dentro destas divisões e formate-os individualmente.

Veja o seguinte código HTML:

`<html><br />
<body><br />
<div id="geral"><br />
<div id="topo"><br />
<h1><a href="#">Logo do Site</a></h1><br />
<div class="menu"><br />
<ul><br />
<li><a href="#">Home</a></li><br />
<li><a href="#">Produtos</a></li><br />
<li><a href="#">Serviços</a></li><br />
<li><a href="#">Contato</a></li><br />
</ul><br />
</div><br />
</div><br />
</div><br />
</body><br />
</html>`

Código CSS:

`` 

Tente seguir a estrutura HTML como referência. Mantendo essa organização, fica simples encontrar os elementos no código CSS.

### Coloque informação importante nos comentários

Comentar qualquer código é sempre uma boa pedida. Em vez de fazer comentários sucintos e que não dizem nada além do nome do div, faça comentários que contenham informação sobre aquela parte específica do layout.

`/* #topo - Div que contém LOGO, #menu e #busca - Elemento Pai é o #geral */`

Isso se torna uma referência para profissionais que farão modificações posteriores em seu código.

### Caminhos completos em seletores

Sempre use os caminhos inteiros nos seletores. Isso evita erros de conflito no arquivo CSS. Sendo específico você mantém corretamente as heranças dos elementos e consegue ter mais controle sobre seu código.

`div#topo div#menu ul li a {...}`

### Ids e classes, use com moderação

Já vi muita gente fazendo isso:
  
``` 

Essa maneira torna o código HTML muito complicado e seu código fica maior sem necessidade. Quando você coloca classes ou ids nos elementos &#8220;pais&#8221;, você controla seus &#8220;filhos&#8221; sem problema algum. Não coloque classes ou ids se você não tiver uma necessidade especifica.

### Identifique o Body

Muitas vezes o designer precisa que alguns detalhes diferentes em diferentes páginas do site. Para facilitar sua vida, coloque uma identificação na tag BODY. Assim você pode mudar os detalhes que precisar de cada página individualmente.
  
````Este era um assunto que eu queria falar aqui a muito tempo. Vi [este link][1] no [URL Sinistras][2] e me animei a escrever sobre.

Estruturar o código CSS de uma maneira simples e intuitiva ajuda muito no desenvolvimento. Já vi várias pessoas fazendo códigos mirabolantes e depois perdendo tempo porque havia problemas de conflito no CSS.

Vou falar aqui como eu monto meu CSS ou como pelo menos eu tento montá-lo. Estes hábitos são algumas coisas que me torna produtivo quando preciso executar alguma modificação no layout.

### Formatando de fora pra dentro

Muita gente não tem uma regra de onde começa a formatar e de onde termina. Isso ajuda a organizar seu código CSS de uma maneira tão lógica quanto uma estrutura HTML.

Formate seu código começando dos elementos mais amplos para os mais específicos. Comece pela tag HTML (se tiver formatação para ela), depois passe para o BODY, logo após para o div que envolve todo o site (eu costumo chamar de #geral) e assim para os elementos que dividem as seções do site (normalmente: cabecalho, coluna da esquerda, colunas da direita, colunas do meio, rodape etc). Logo após, passe para os elementos que ficam dentro destas divisões e formate-os individualmente.

Veja o seguinte código HTML:

`<html><br />
<body><br />
<div id="geral"><br />
<div id="topo"><br />
<h1><a href="#">Logo do Site</a></h1><br />
<div class="menu"><br />
<ul><br />
<li><a href="#">Home</a></li><br />
<li><a href="#">Produtos</a></li><br />
<li><a href="#">Serviços</a></li><br />
<li><a href="#">Contato</a></li><br />
</ul><br />
</div><br />
</div><br />
</div><br />
</body><br />
</html>`

Código CSS:

``Este era um assunto que eu queria falar aqui a muito tempo. Vi [este link][1] no [URL Sinistras][2] e me animei a escrever sobre.

Estruturar o código CSS de uma maneira simples e intuitiva ajuda muito no desenvolvimento. Já vi várias pessoas fazendo códigos mirabolantes e depois perdendo tempo porque havia problemas de conflito no CSS.

Vou falar aqui como eu monto meu CSS ou como pelo menos eu tento montá-lo. Estes hábitos são algumas coisas que me torna produtivo quando preciso executar alguma modificação no layout.

### Formatando de fora pra dentro

Muita gente não tem uma regra de onde começa a formatar e de onde termina. Isso ajuda a organizar seu código CSS de uma maneira tão lógica quanto uma estrutura HTML.

Formate seu código começando dos elementos mais amplos para os mais específicos. Comece pela tag HTML (se tiver formatação para ela), depois passe para o BODY, logo após para o div que envolve todo o site (eu costumo chamar de #geral) e assim para os elementos que dividem as seções do site (normalmente: cabecalho, coluna da esquerda, colunas da direita, colunas do meio, rodape etc). Logo após, passe para os elementos que ficam dentro destas divisões e formate-os individualmente.

Veja o seguinte código HTML:

`<html><br />
<body><br />
<div id="geral"><br />
<div id="topo"><br />
<h1><a href="#">Logo do Site</a></h1><br />
<div class="menu"><br />
<ul><br />
<li><a href="#">Home</a></li><br />
<li><a href="#">Produtos</a></li><br />
<li><a href="#">Serviços</a></li><br />
<li><a href="#">Contato</a></li><br />
</ul><br />
</div><br />
</div><br />
</div><br />
</body><br />
</html>`

Código CSS:

`` 

Tente seguir a estrutura HTML como referência. Mantendo essa organização, fica simples encontrar os elementos no código CSS.

### Coloque informação importante nos comentários

Comentar qualquer código é sempre uma boa pedida. Em vez de fazer comentários sucintos e que não dizem nada além do nome do div, faça comentários que contenham informação sobre aquela parte específica do layout.

`/* #topo - Div que contém LOGO, #menu e #busca - Elemento Pai é o #geral */`

Isso se torna uma referência para profissionais que farão modificações posteriores em seu código.

### Caminhos completos em seletores

Sempre use os caminhos inteiros nos seletores. Isso evita erros de conflito no arquivo CSS. Sendo específico você mantém corretamente as heranças dos elementos e consegue ter mais controle sobre seu código.

`div#topo div#menu ul li a {...}`

### Ids e classes, use com moderação

Já vi muita gente fazendo isso:
  
```Este era um assunto que eu queria falar aqui a muito tempo. Vi [este link][1] no [URL Sinistras][2] e me animei a escrever sobre.

Estruturar o código CSS de uma maneira simples e intuitiva ajuda muito no desenvolvimento. Já vi várias pessoas fazendo códigos mirabolantes e depois perdendo tempo porque havia problemas de conflito no CSS.

Vou falar aqui como eu monto meu CSS ou como pelo menos eu tento montá-lo. Estes hábitos são algumas coisas que me torna produtivo quando preciso executar alguma modificação no layout.

### Formatando de fora pra dentro

Muita gente não tem uma regra de onde começa a formatar e de onde termina. Isso ajuda a organizar seu código CSS de uma maneira tão lógica quanto uma estrutura HTML.

Formate seu código começando dos elementos mais amplos para os mais específicos. Comece pela tag HTML (se tiver formatação para ela), depois passe para o BODY, logo após para o div que envolve todo o site (eu costumo chamar de #geral) e assim para os elementos que dividem as seções do site (normalmente: cabecalho, coluna da esquerda, colunas da direita, colunas do meio, rodape etc). Logo após, passe para os elementos que ficam dentro destas divisões e formate-os individualmente.

Veja o seguinte código HTML:

`<html><br />
<body><br />
<div id="geral"><br />
<div id="topo"><br />
<h1><a href="#">Logo do Site</a></h1><br />
<div class="menu"><br />
<ul><br />
<li><a href="#">Home</a></li><br />
<li><a href="#">Produtos</a></li><br />
<li><a href="#">Serviços</a></li><br />
<li><a href="#">Contato</a></li><br />
</ul><br />
</div><br />
</div><br />
</div><br />
</body><br />
</html>`

Código CSS:

``Este era um assunto que eu queria falar aqui a muito tempo. Vi [este link][1] no [URL Sinistras][2] e me animei a escrever sobre.

Estruturar o código CSS de uma maneira simples e intuitiva ajuda muito no desenvolvimento. Já vi várias pessoas fazendo códigos mirabolantes e depois perdendo tempo porque havia problemas de conflito no CSS.

Vou falar aqui como eu monto meu CSS ou como pelo menos eu tento montá-lo. Estes hábitos são algumas coisas que me torna produtivo quando preciso executar alguma modificação no layout.

### Formatando de fora pra dentro

Muita gente não tem uma regra de onde começa a formatar e de onde termina. Isso ajuda a organizar seu código CSS de uma maneira tão lógica quanto uma estrutura HTML.

Formate seu código começando dos elementos mais amplos para os mais específicos. Comece pela tag HTML (se tiver formatação para ela), depois passe para o BODY, logo após para o div que envolve todo o site (eu costumo chamar de #geral) e assim para os elementos que dividem as seções do site (normalmente: cabecalho, coluna da esquerda, colunas da direita, colunas do meio, rodape etc). Logo após, passe para os elementos que ficam dentro destas divisões e formate-os individualmente.

Veja o seguinte código HTML:

`<html><br />
<body><br />
<div id="geral"><br />
<div id="topo"><br />
<h1><a href="#">Logo do Site</a></h1><br />
<div class="menu"><br />
<ul><br />
<li><a href="#">Home</a></li><br />
<li><a href="#">Produtos</a></li><br />
<li><a href="#">Serviços</a></li><br />
<li><a href="#">Contato</a></li><br />
</ul><br />
</div><br />
</div><br />
</div><br />
</body><br />
</html>`

Código CSS:

`` 

Tente seguir a estrutura HTML como referência. Mantendo essa organização, fica simples encontrar os elementos no código CSS.

### Coloque informação importante nos comentários

Comentar qualquer código é sempre uma boa pedida. Em vez de fazer comentários sucintos e que não dizem nada além do nome do div, faça comentários que contenham informação sobre aquela parte específica do layout.

`/* #topo - Div que contém LOGO, #menu e #busca - Elemento Pai é o #geral */`

Isso se torna uma referência para profissionais que farão modificações posteriores em seu código.

### Caminhos completos em seletores

Sempre use os caminhos inteiros nos seletores. Isso evita erros de conflito no arquivo CSS. Sendo específico você mantém corretamente as heranças dos elementos e consegue ter mais controle sobre seu código.

`div#topo div#menu ul li a {...}`

### Ids e classes, use com moderação

Já vi muita gente fazendo isso:
  
``` 

Essa maneira torna o código HTML muito complicado e seu código fica maior sem necessidade. Quando você coloca classes ou ids nos elementos &#8220;pais&#8221;, você controla seus &#8220;filhos&#8221; sem problema algum. Não coloque classes ou ids se você não tiver uma necessidade especifica.

### Identifique o Body

Muitas vezes o designer precisa que alguns detalhes diferentes em diferentes páginas do site. Para facilitar sua vida, coloque uma identificação na tag BODY. Assim você pode mudar os detalhes que precisar de cada página individualmente.
  
```` 
  
`````Este era um assunto que eu queria falar aqui a muito tempo. Vi [este link][1] no [URL Sinistras][2] e me animei a escrever sobre.

Estruturar o código CSS de uma maneira simples e intuitiva ajuda muito no desenvolvimento. Já vi várias pessoas fazendo códigos mirabolantes e depois perdendo tempo porque havia problemas de conflito no CSS.

Vou falar aqui como eu monto meu CSS ou como pelo menos eu tento montá-lo. Estes hábitos são algumas coisas que me torna produtivo quando preciso executar alguma modificação no layout.

### Formatando de fora pra dentro

Muita gente não tem uma regra de onde começa a formatar e de onde termina. Isso ajuda a organizar seu código CSS de uma maneira tão lógica quanto uma estrutura HTML.

Formate seu código começando dos elementos mais amplos para os mais específicos. Comece pela tag HTML (se tiver formatação para ela), depois passe para o BODY, logo após para o div que envolve todo o site (eu costumo chamar de #geral) e assim para os elementos que dividem as seções do site (normalmente: cabecalho, coluna da esquerda, colunas da direita, colunas do meio, rodape etc). Logo após, passe para os elementos que ficam dentro destas divisões e formate-os individualmente.

Veja o seguinte código HTML:

`<html><br />
<body><br />
<div id="geral"><br />
<div id="topo"><br />
<h1><a href="#">Logo do Site</a></h1><br />
<div class="menu"><br />
<ul><br />
<li><a href="#">Home</a></li><br />
<li><a href="#">Produtos</a></li><br />
<li><a href="#">Serviços</a></li><br />
<li><a href="#">Contato</a></li><br />
</ul><br />
</div><br />
</div><br />
</div><br />
</body><br />
</html>`

Código CSS:

``Este era um assunto que eu queria falar aqui a muito tempo. Vi [este link][1] no [URL Sinistras][2] e me animei a escrever sobre.

Estruturar o código CSS de uma maneira simples e intuitiva ajuda muito no desenvolvimento. Já vi várias pessoas fazendo códigos mirabolantes e depois perdendo tempo porque havia problemas de conflito no CSS.

Vou falar aqui como eu monto meu CSS ou como pelo menos eu tento montá-lo. Estes hábitos são algumas coisas que me torna produtivo quando preciso executar alguma modificação no layout.

### Formatando de fora pra dentro

Muita gente não tem uma regra de onde começa a formatar e de onde termina. Isso ajuda a organizar seu código CSS de uma maneira tão lógica quanto uma estrutura HTML.

Formate seu código começando dos elementos mais amplos para os mais específicos. Comece pela tag HTML (se tiver formatação para ela), depois passe para o BODY, logo após para o div que envolve todo o site (eu costumo chamar de #geral) e assim para os elementos que dividem as seções do site (normalmente: cabecalho, coluna da esquerda, colunas da direita, colunas do meio, rodape etc). Logo após, passe para os elementos que ficam dentro destas divisões e formate-os individualmente.

Veja o seguinte código HTML:

`<html><br />
<body><br />
<div id="geral"><br />
<div id="topo"><br />
<h1><a href="#">Logo do Site</a></h1><br />
<div class="menu"><br />
<ul><br />
<li><a href="#">Home</a></li><br />
<li><a href="#">Produtos</a></li><br />
<li><a href="#">Serviços</a></li><br />
<li><a href="#">Contato</a></li><br />
</ul><br />
</div><br />
</div><br />
</div><br />
</body><br />
</html>`

Código CSS:

`` 

Tente seguir a estrutura HTML como referência. Mantendo essa organização, fica simples encontrar os elementos no código CSS.

### Coloque informação importante nos comentários

Comentar qualquer código é sempre uma boa pedida. Em vez de fazer comentários sucintos e que não dizem nada além do nome do div, faça comentários que contenham informação sobre aquela parte específica do layout.

`/* #topo - Div que contém LOGO, #menu e #busca - Elemento Pai é o #geral */`

Isso se torna uma referência para profissionais que farão modificações posteriores em seu código.

### Caminhos completos em seletores

Sempre use os caminhos inteiros nos seletores. Isso evita erros de conflito no arquivo CSS. Sendo específico você mantém corretamente as heranças dos elementos e consegue ter mais controle sobre seu código.

`div#topo div#menu ul li a {...}`

### Ids e classes, use com moderação

Já vi muita gente fazendo isso:
  
```Este era um assunto que eu queria falar aqui a muito tempo. Vi [este link][1] no [URL Sinistras][2] e me animei a escrever sobre.

Estruturar o código CSS de uma maneira simples e intuitiva ajuda muito no desenvolvimento. Já vi várias pessoas fazendo códigos mirabolantes e depois perdendo tempo porque havia problemas de conflito no CSS.

Vou falar aqui como eu monto meu CSS ou como pelo menos eu tento montá-lo. Estes hábitos são algumas coisas que me torna produtivo quando preciso executar alguma modificação no layout.

### Formatando de fora pra dentro

Muita gente não tem uma regra de onde começa a formatar e de onde termina. Isso ajuda a organizar seu código CSS de uma maneira tão lógica quanto uma estrutura HTML.

Formate seu código começando dos elementos mais amplos para os mais específicos. Comece pela tag HTML (se tiver formatação para ela), depois passe para o BODY, logo após para o div que envolve todo o site (eu costumo chamar de #geral) e assim para os elementos que dividem as seções do site (normalmente: cabecalho, coluna da esquerda, colunas da direita, colunas do meio, rodape etc). Logo após, passe para os elementos que ficam dentro destas divisões e formate-os individualmente.

Veja o seguinte código HTML:

`<html><br />
<body><br />
<div id="geral"><br />
<div id="topo"><br />
<h1><a href="#">Logo do Site</a></h1><br />
<div class="menu"><br />
<ul><br />
<li><a href="#">Home</a></li><br />
<li><a href="#">Produtos</a></li><br />
<li><a href="#">Serviços</a></li><br />
<li><a href="#">Contato</a></li><br />
</ul><br />
</div><br />
</div><br />
</div><br />
</body><br />
</html>`

Código CSS:

``Este era um assunto que eu queria falar aqui a muito tempo. Vi [este link][1] no [URL Sinistras][2] e me animei a escrever sobre.

Estruturar o código CSS de uma maneira simples e intuitiva ajuda muito no desenvolvimento. Já vi várias pessoas fazendo códigos mirabolantes e depois perdendo tempo porque havia problemas de conflito no CSS.

Vou falar aqui como eu monto meu CSS ou como pelo menos eu tento montá-lo. Estes hábitos são algumas coisas que me torna produtivo quando preciso executar alguma modificação no layout.

### Formatando de fora pra dentro

Muita gente não tem uma regra de onde começa a formatar e de onde termina. Isso ajuda a organizar seu código CSS de uma maneira tão lógica quanto uma estrutura HTML.

Formate seu código começando dos elementos mais amplos para os mais específicos. Comece pela tag HTML (se tiver formatação para ela), depois passe para o BODY, logo após para o div que envolve todo o site (eu costumo chamar de #geral) e assim para os elementos que dividem as seções do site (normalmente: cabecalho, coluna da esquerda, colunas da direita, colunas do meio, rodape etc). Logo após, passe para os elementos que ficam dentro destas divisões e formate-os individualmente.

Veja o seguinte código HTML:

`<html><br />
<body><br />
<div id="geral"><br />
<div id="topo"><br />
<h1><a href="#">Logo do Site</a></h1><br />
<div class="menu"><br />
<ul><br />
<li><a href="#">Home</a></li><br />
<li><a href="#">Produtos</a></li><br />
<li><a href="#">Serviços</a></li><br />
<li><a href="#">Contato</a></li><br />
</ul><br />
</div><br />
</div><br />
</div><br />
</body><br />
</html>`

Código CSS:

`` 

Tente seguir a estrutura HTML como referência. Mantendo essa organização, fica simples encontrar os elementos no código CSS.

### Coloque informação importante nos comentários

Comentar qualquer código é sempre uma boa pedida. Em vez de fazer comentários sucintos e que não dizem nada além do nome do div, faça comentários que contenham informação sobre aquela parte específica do layout.

`/* #topo - Div que contém LOGO, #menu e #busca - Elemento Pai é o #geral */`

Isso se torna uma referência para profissionais que farão modificações posteriores em seu código.

### Caminhos completos em seletores

Sempre use os caminhos inteiros nos seletores. Isso evita erros de conflito no arquivo CSS. Sendo específico você mantém corretamente as heranças dos elementos e consegue ter mais controle sobre seu código.

`div#topo div#menu ul li a {...}`

### Ids e classes, use com moderação

Já vi muita gente fazendo isso:
  
``` 

Essa maneira torna o código HTML muito complicado e seu código fica maior sem necessidade. Quando você coloca classes ou ids nos elementos &#8220;pais&#8221;, você controla seus &#8220;filhos&#8221; sem problema algum. Não coloque classes ou ids se você não tiver uma necessidade especifica.

### Identifique o Body

Muitas vezes o designer precisa que alguns detalhes diferentes em diferentes páginas do site. Para facilitar sua vida, coloque uma identificação na tag BODY. Assim você pode mudar os detalhes que precisar de cada página individualmente.
  
````Este era um assunto que eu queria falar aqui a muito tempo. Vi [este link][1] no [URL Sinistras][2] e me animei a escrever sobre.

Estruturar o código CSS de uma maneira simples e intuitiva ajuda muito no desenvolvimento. Já vi várias pessoas fazendo códigos mirabolantes e depois perdendo tempo porque havia problemas de conflito no CSS.

Vou falar aqui como eu monto meu CSS ou como pelo menos eu tento montá-lo. Estes hábitos são algumas coisas que me torna produtivo quando preciso executar alguma modificação no layout.

### Formatando de fora pra dentro

Muita gente não tem uma regra de onde começa a formatar e de onde termina. Isso ajuda a organizar seu código CSS de uma maneira tão lógica quanto uma estrutura HTML.

Formate seu código começando dos elementos mais amplos para os mais específicos. Comece pela tag HTML (se tiver formatação para ela), depois passe para o BODY, logo após para o div que envolve todo o site (eu costumo chamar de #geral) e assim para os elementos que dividem as seções do site (normalmente: cabecalho, coluna da esquerda, colunas da direita, colunas do meio, rodape etc). Logo após, passe para os elementos que ficam dentro destas divisões e formate-os individualmente.

Veja o seguinte código HTML:

`<html><br />
<body><br />
<div id="geral"><br />
<div id="topo"><br />
<h1><a href="#">Logo do Site</a></h1><br />
<div class="menu"><br />
<ul><br />
<li><a href="#">Home</a></li><br />
<li><a href="#">Produtos</a></li><br />
<li><a href="#">Serviços</a></li><br />
<li><a href="#">Contato</a></li><br />
</ul><br />
</div><br />
</div><br />
</div><br />
</body><br />
</html>`

Código CSS:

``Este era um assunto que eu queria falar aqui a muito tempo. Vi [este link][1] no [URL Sinistras][2] e me animei a escrever sobre.

Estruturar o código CSS de uma maneira simples e intuitiva ajuda muito no desenvolvimento. Já vi várias pessoas fazendo códigos mirabolantes e depois perdendo tempo porque havia problemas de conflito no CSS.

Vou falar aqui como eu monto meu CSS ou como pelo menos eu tento montá-lo. Estes hábitos são algumas coisas que me torna produtivo quando preciso executar alguma modificação no layout.

### Formatando de fora pra dentro

Muita gente não tem uma regra de onde começa a formatar e de onde termina. Isso ajuda a organizar seu código CSS de uma maneira tão lógica quanto uma estrutura HTML.

Formate seu código começando dos elementos mais amplos para os mais específicos. Comece pela tag HTML (se tiver formatação para ela), depois passe para o BODY, logo após para o div que envolve todo o site (eu costumo chamar de #geral) e assim para os elementos que dividem as seções do site (normalmente: cabecalho, coluna da esquerda, colunas da direita, colunas do meio, rodape etc). Logo após, passe para os elementos que ficam dentro destas divisões e formate-os individualmente.

Veja o seguinte código HTML:

`<html><br />
<body><br />
<div id="geral"><br />
<div id="topo"><br />
<h1><a href="#">Logo do Site</a></h1><br />
<div class="menu"><br />
<ul><br />
<li><a href="#">Home</a></li><br />
<li><a href="#">Produtos</a></li><br />
<li><a href="#">Serviços</a></li><br />
<li><a href="#">Contato</a></li><br />
</ul><br />
</div><br />
</div><br />
</div><br />
</body><br />
</html>`

Código CSS:

`` 

Tente seguir a estrutura HTML como referência. Mantendo essa organização, fica simples encontrar os elementos no código CSS.

### Coloque informação importante nos comentários

Comentar qualquer código é sempre uma boa pedida. Em vez de fazer comentários sucintos e que não dizem nada além do nome do div, faça comentários que contenham informação sobre aquela parte específica do layout.

`/* #topo - Div que contém LOGO, #menu e #busca - Elemento Pai é o #geral */`

Isso se torna uma referência para profissionais que farão modificações posteriores em seu código.

### Caminhos completos em seletores

Sempre use os caminhos inteiros nos seletores. Isso evita erros de conflito no arquivo CSS. Sendo específico você mantém corretamente as heranças dos elementos e consegue ter mais controle sobre seu código.

`div#topo div#menu ul li a {...}`

### Ids e classes, use com moderação

Já vi muita gente fazendo isso:
  
```Este era um assunto que eu queria falar aqui a muito tempo. Vi [este link][1] no [URL Sinistras][2] e me animei a escrever sobre.

Estruturar o código CSS de uma maneira simples e intuitiva ajuda muito no desenvolvimento. Já vi várias pessoas fazendo códigos mirabolantes e depois perdendo tempo porque havia problemas de conflito no CSS.

Vou falar aqui como eu monto meu CSS ou como pelo menos eu tento montá-lo. Estes hábitos são algumas coisas que me torna produtivo quando preciso executar alguma modificação no layout.

### Formatando de fora pra dentro

Muita gente não tem uma regra de onde começa a formatar e de onde termina. Isso ajuda a organizar seu código CSS de uma maneira tão lógica quanto uma estrutura HTML.

Formate seu código começando dos elementos mais amplos para os mais específicos. Comece pela tag HTML (se tiver formatação para ela), depois passe para o BODY, logo após para o div que envolve todo o site (eu costumo chamar de #geral) e assim para os elementos que dividem as seções do site (normalmente: cabecalho, coluna da esquerda, colunas da direita, colunas do meio, rodape etc). Logo após, passe para os elementos que ficam dentro destas divisões e formate-os individualmente.

Veja o seguinte código HTML:

`<html><br />
<body><br />
<div id="geral"><br />
<div id="topo"><br />
<h1><a href="#">Logo do Site</a></h1><br />
<div class="menu"><br />
<ul><br />
<li><a href="#">Home</a></li><br />
<li><a href="#">Produtos</a></li><br />
<li><a href="#">Serviços</a></li><br />
<li><a href="#">Contato</a></li><br />
</ul><br />
</div><br />
</div><br />
</div><br />
</body><br />
</html>`

Código CSS:

``Este era um assunto que eu queria falar aqui a muito tempo. Vi [este link][1] no [URL Sinistras][2] e me animei a escrever sobre.

Estruturar o código CSS de uma maneira simples e intuitiva ajuda muito no desenvolvimento. Já vi várias pessoas fazendo códigos mirabolantes e depois perdendo tempo porque havia problemas de conflito no CSS.

Vou falar aqui como eu monto meu CSS ou como pelo menos eu tento montá-lo. Estes hábitos são algumas coisas que me torna produtivo quando preciso executar alguma modificação no layout.

### Formatando de fora pra dentro

Muita gente não tem uma regra de onde começa a formatar e de onde termina. Isso ajuda a organizar seu código CSS de uma maneira tão lógica quanto uma estrutura HTML.

Formate seu código começando dos elementos mais amplos para os mais específicos. Comece pela tag HTML (se tiver formatação para ela), depois passe para o BODY, logo após para o div que envolve todo o site (eu costumo chamar de #geral) e assim para os elementos que dividem as seções do site (normalmente: cabecalho, coluna da esquerda, colunas da direita, colunas do meio, rodape etc). Logo após, passe para os elementos que ficam dentro destas divisões e formate-os individualmente.

Veja o seguinte código HTML:

`<html><br />
<body><br />
<div id="geral"><br />
<div id="topo"><br />
<h1><a href="#">Logo do Site</a></h1><br />
<div class="menu"><br />
<ul><br />
<li><a href="#">Home</a></li><br />
<li><a href="#">Produtos</a></li><br />
<li><a href="#">Serviços</a></li><br />
<li><a href="#">Contato</a></li><br />
</ul><br />
</div><br />
</div><br />
</div><br />
</body><br />
</html>`

Código CSS:

`` 

Tente seguir a estrutura HTML como referência. Mantendo essa organização, fica simples encontrar os elementos no código CSS.

### Coloque informação importante nos comentários

Comentar qualquer código é sempre uma boa pedida. Em vez de fazer comentários sucintos e que não dizem nada além do nome do div, faça comentários que contenham informação sobre aquela parte específica do layout.

`/* #topo - Div que contém LOGO, #menu e #busca - Elemento Pai é o #geral */`

Isso se torna uma referência para profissionais que farão modificações posteriores em seu código.

### Caminhos completos em seletores

Sempre use os caminhos inteiros nos seletores. Isso evita erros de conflito no arquivo CSS. Sendo específico você mantém corretamente as heranças dos elementos e consegue ter mais controle sobre seu código.

`div#topo div#menu ul li a {...}`

### Ids e classes, use com moderação

Já vi muita gente fazendo isso:
  
``` 

Essa maneira torna o código HTML muito complicado e seu código fica maior sem necessidade. Quando você coloca classes ou ids nos elementos &#8220;pais&#8221;, você controla seus &#8220;filhos&#8221; sem problema algum. Não coloque classes ou ids se você não tiver uma necessidade especifica.

### Identifique o Body

Muitas vezes o designer precisa que alguns detalhes diferentes em diferentes páginas do site. Para facilitar sua vida, coloque uma identificação na tag BODY. Assim você pode mudar os detalhes que precisar de cada página individualmente.
  
```` 
  
````` 

### Organize as propriedades

Existem diversas propriedades do CSS e cada uma delas modifica uma característica dos elementos. Há propriedades que formatam o visual do elemento (display, border, background, color, font, text etc&#8230;), há outras propriedades que modificam medidas e distâncias (margin, padding, width, height, min-width, min-height etc&#8230;) e outras propriedades que posicionam os elementos (float, position).

Eu organizo primeiro propriedades controlam o visual, depois as propriedades de distâncias e medidas e logo após propriedades de posicionamento.

``````Este era um assunto que eu queria falar aqui a muito tempo. Vi [este link][1] no [URL Sinistras][2] e me animei a escrever sobre.

Estruturar o código CSS de uma maneira simples e intuitiva ajuda muito no desenvolvimento. Já vi várias pessoas fazendo códigos mirabolantes e depois perdendo tempo porque havia problemas de conflito no CSS.

Vou falar aqui como eu monto meu CSS ou como pelo menos eu tento montá-lo. Estes hábitos são algumas coisas que me torna produtivo quando preciso executar alguma modificação no layout.

### Formatando de fora pra dentro

Muita gente não tem uma regra de onde começa a formatar e de onde termina. Isso ajuda a organizar seu código CSS de uma maneira tão lógica quanto uma estrutura HTML.

Formate seu código começando dos elementos mais amplos para os mais específicos. Comece pela tag HTML (se tiver formatação para ela), depois passe para o BODY, logo após para o div que envolve todo o site (eu costumo chamar de #geral) e assim para os elementos que dividem as seções do site (normalmente: cabecalho, coluna da esquerda, colunas da direita, colunas do meio, rodape etc). Logo após, passe para os elementos que ficam dentro destas divisões e formate-os individualmente.

Veja o seguinte código HTML:

`<html><br />
<body><br />
<div id="geral"><br />
<div id="topo"><br />
<h1><a href="#">Logo do Site</a></h1><br />
<div class="menu"><br />
<ul><br />
<li><a href="#">Home</a></li><br />
<li><a href="#">Produtos</a></li><br />
<li><a href="#">Serviços</a></li><br />
<li><a href="#">Contato</a></li><br />
</ul><br />
</div><br />
</div><br />
</div><br />
</body><br />
</html>`

Código CSS:

``Este era um assunto que eu queria falar aqui a muito tempo. Vi [este link][1] no [URL Sinistras][2] e me animei a escrever sobre.

Estruturar o código CSS de uma maneira simples e intuitiva ajuda muito no desenvolvimento. Já vi várias pessoas fazendo códigos mirabolantes e depois perdendo tempo porque havia problemas de conflito no CSS.

Vou falar aqui como eu monto meu CSS ou como pelo menos eu tento montá-lo. Estes hábitos são algumas coisas que me torna produtivo quando preciso executar alguma modificação no layout.

### Formatando de fora pra dentro

Muita gente não tem uma regra de onde começa a formatar e de onde termina. Isso ajuda a organizar seu código CSS de uma maneira tão lógica quanto uma estrutura HTML.

Formate seu código começando dos elementos mais amplos para os mais específicos. Comece pela tag HTML (se tiver formatação para ela), depois passe para o BODY, logo após para o div que envolve todo o site (eu costumo chamar de #geral) e assim para os elementos que dividem as seções do site (normalmente: cabecalho, coluna da esquerda, colunas da direita, colunas do meio, rodape etc). Logo após, passe para os elementos que ficam dentro destas divisões e formate-os individualmente.

Veja o seguinte código HTML:

`<html><br />
<body><br />
<div id="geral"><br />
<div id="topo"><br />
<h1><a href="#">Logo do Site</a></h1><br />
<div class="menu"><br />
<ul><br />
<li><a href="#">Home</a></li><br />
<li><a href="#">Produtos</a></li><br />
<li><a href="#">Serviços</a></li><br />
<li><a href="#">Contato</a></li><br />
</ul><br />
</div><br />
</div><br />
</div><br />
</body><br />
</html>`

Código CSS:

`` 

Tente seguir a estrutura HTML como referência. Mantendo essa organização, fica simples encontrar os elementos no código CSS.

### Coloque informação importante nos comentários

Comentar qualquer código é sempre uma boa pedida. Em vez de fazer comentários sucintos e que não dizem nada além do nome do div, faça comentários que contenham informação sobre aquela parte específica do layout.

`/* #topo - Div que contém LOGO, #menu e #busca - Elemento Pai é o #geral */`

Isso se torna uma referência para profissionais que farão modificações posteriores em seu código.

### Caminhos completos em seletores

Sempre use os caminhos inteiros nos seletores. Isso evita erros de conflito no arquivo CSS. Sendo específico você mantém corretamente as heranças dos elementos e consegue ter mais controle sobre seu código.

`div#topo div#menu ul li a {...}`

### Ids e classes, use com moderação

Já vi muita gente fazendo isso:
  
```Este era um assunto que eu queria falar aqui a muito tempo. Vi [este link][1] no [URL Sinistras][2] e me animei a escrever sobre.

Estruturar o código CSS de uma maneira simples e intuitiva ajuda muito no desenvolvimento. Já vi várias pessoas fazendo códigos mirabolantes e depois perdendo tempo porque havia problemas de conflito no CSS.

Vou falar aqui como eu monto meu CSS ou como pelo menos eu tento montá-lo. Estes hábitos são algumas coisas que me torna produtivo quando preciso executar alguma modificação no layout.

### Formatando de fora pra dentro

Muita gente não tem uma regra de onde começa a formatar e de onde termina. Isso ajuda a organizar seu código CSS de uma maneira tão lógica quanto uma estrutura HTML.

Formate seu código começando dos elementos mais amplos para os mais específicos. Comece pela tag HTML (se tiver formatação para ela), depois passe para o BODY, logo após para o div que envolve todo o site (eu costumo chamar de #geral) e assim para os elementos que dividem as seções do site (normalmente: cabecalho, coluna da esquerda, colunas da direita, colunas do meio, rodape etc). Logo após, passe para os elementos que ficam dentro destas divisões e formate-os individualmente.

Veja o seguinte código HTML:

`<html><br />
<body><br />
<div id="geral"><br />
<div id="topo"><br />
<h1><a href="#">Logo do Site</a></h1><br />
<div class="menu"><br />
<ul><br />
<li><a href="#">Home</a></li><br />
<li><a href="#">Produtos</a></li><br />
<li><a href="#">Serviços</a></li><br />
<li><a href="#">Contato</a></li><br />
</ul><br />
</div><br />
</div><br />
</div><br />
</body><br />
</html>`

Código CSS:

``Este era um assunto que eu queria falar aqui a muito tempo. Vi [este link][1] no [URL Sinistras][2] e me animei a escrever sobre.

Estruturar o código CSS de uma maneira simples e intuitiva ajuda muito no desenvolvimento. Já vi várias pessoas fazendo códigos mirabolantes e depois perdendo tempo porque havia problemas de conflito no CSS.

Vou falar aqui como eu monto meu CSS ou como pelo menos eu tento montá-lo. Estes hábitos são algumas coisas que me torna produtivo quando preciso executar alguma modificação no layout.

### Formatando de fora pra dentro

Muita gente não tem uma regra de onde começa a formatar e de onde termina. Isso ajuda a organizar seu código CSS de uma maneira tão lógica quanto uma estrutura HTML.

Formate seu código começando dos elementos mais amplos para os mais específicos. Comece pela tag HTML (se tiver formatação para ela), depois passe para o BODY, logo após para o div que envolve todo o site (eu costumo chamar de #geral) e assim para os elementos que dividem as seções do site (normalmente: cabecalho, coluna da esquerda, colunas da direita, colunas do meio, rodape etc). Logo após, passe para os elementos que ficam dentro destas divisões e formate-os individualmente.

Veja o seguinte código HTML:

`<html><br />
<body><br />
<div id="geral"><br />
<div id="topo"><br />
<h1><a href="#">Logo do Site</a></h1><br />
<div class="menu"><br />
<ul><br />
<li><a href="#">Home</a></li><br />
<li><a href="#">Produtos</a></li><br />
<li><a href="#">Serviços</a></li><br />
<li><a href="#">Contato</a></li><br />
</ul><br />
</div><br />
</div><br />
</div><br />
</body><br />
</html>`

Código CSS:

`` 

Tente seguir a estrutura HTML como referência. Mantendo essa organização, fica simples encontrar os elementos no código CSS.

### Coloque informação importante nos comentários

Comentar qualquer código é sempre uma boa pedida. Em vez de fazer comentários sucintos e que não dizem nada além do nome do div, faça comentários que contenham informação sobre aquela parte específica do layout.

`/* #topo - Div que contém LOGO, #menu e #busca - Elemento Pai é o #geral */`

Isso se torna uma referência para profissionais que farão modificações posteriores em seu código.

### Caminhos completos em seletores

Sempre use os caminhos inteiros nos seletores. Isso evita erros de conflito no arquivo CSS. Sendo específico você mantém corretamente as heranças dos elementos e consegue ter mais controle sobre seu código.

`div#topo div#menu ul li a {...}`

### Ids e classes, use com moderação

Já vi muita gente fazendo isso:
  
``` 

Essa maneira torna o código HTML muito complicado e seu código fica maior sem necessidade. Quando você coloca classes ou ids nos elementos &#8220;pais&#8221;, você controla seus &#8220;filhos&#8221; sem problema algum. Não coloque classes ou ids se você não tiver uma necessidade especifica.

### Identifique o Body

Muitas vezes o designer precisa que alguns detalhes diferentes em diferentes páginas do site. Para facilitar sua vida, coloque uma identificação na tag BODY. Assim você pode mudar os detalhes que precisar de cada página individualmente.
  
````Este era um assunto que eu queria falar aqui a muito tempo. Vi [este link][1] no [URL Sinistras][2] e me animei a escrever sobre.

Estruturar o código CSS de uma maneira simples e intuitiva ajuda muito no desenvolvimento. Já vi várias pessoas fazendo códigos mirabolantes e depois perdendo tempo porque havia problemas de conflito no CSS.

Vou falar aqui como eu monto meu CSS ou como pelo menos eu tento montá-lo. Estes hábitos são algumas coisas que me torna produtivo quando preciso executar alguma modificação no layout.

### Formatando de fora pra dentro

Muita gente não tem uma regra de onde começa a formatar e de onde termina. Isso ajuda a organizar seu código CSS de uma maneira tão lógica quanto uma estrutura HTML.

Formate seu código começando dos elementos mais amplos para os mais específicos. Comece pela tag HTML (se tiver formatação para ela), depois passe para o BODY, logo após para o div que envolve todo o site (eu costumo chamar de #geral) e assim para os elementos que dividem as seções do site (normalmente: cabecalho, coluna da esquerda, colunas da direita, colunas do meio, rodape etc). Logo após, passe para os elementos que ficam dentro destas divisões e formate-os individualmente.

Veja o seguinte código HTML:

`<html><br />
<body><br />
<div id="geral"><br />
<div id="topo"><br />
<h1><a href="#">Logo do Site</a></h1><br />
<div class="menu"><br />
<ul><br />
<li><a href="#">Home</a></li><br />
<li><a href="#">Produtos</a></li><br />
<li><a href="#">Serviços</a></li><br />
<li><a href="#">Contato</a></li><br />
</ul><br />
</div><br />
</div><br />
</div><br />
</body><br />
</html>`

Código CSS:

``Este era um assunto que eu queria falar aqui a muito tempo. Vi [este link][1] no [URL Sinistras][2] e me animei a escrever sobre.

Estruturar o código CSS de uma maneira simples e intuitiva ajuda muito no desenvolvimento. Já vi várias pessoas fazendo códigos mirabolantes e depois perdendo tempo porque havia problemas de conflito no CSS.

Vou falar aqui como eu monto meu CSS ou como pelo menos eu tento montá-lo. Estes hábitos são algumas coisas que me torna produtivo quando preciso executar alguma modificação no layout.

### Formatando de fora pra dentro

Muita gente não tem uma regra de onde começa a formatar e de onde termina. Isso ajuda a organizar seu código CSS de uma maneira tão lógica quanto uma estrutura HTML.

Formate seu código começando dos elementos mais amplos para os mais específicos. Comece pela tag HTML (se tiver formatação para ela), depois passe para o BODY, logo após para o div que envolve todo o site (eu costumo chamar de #geral) e assim para os elementos que dividem as seções do site (normalmente: cabecalho, coluna da esquerda, colunas da direita, colunas do meio, rodape etc). Logo após, passe para os elementos que ficam dentro destas divisões e formate-os individualmente.

Veja o seguinte código HTML:

`<html><br />
<body><br />
<div id="geral"><br />
<div id="topo"><br />
<h1><a href="#">Logo do Site</a></h1><br />
<div class="menu"><br />
<ul><br />
<li><a href="#">Home</a></li><br />
<li><a href="#">Produtos</a></li><br />
<li><a href="#">Serviços</a></li><br />
<li><a href="#">Contato</a></li><br />
</ul><br />
</div><br />
</div><br />
</div><br />
</body><br />
</html>`

Código CSS:

`` 

Tente seguir a estrutura HTML como referência. Mantendo essa organização, fica simples encontrar os elementos no código CSS.

### Coloque informação importante nos comentários

Comentar qualquer código é sempre uma boa pedida. Em vez de fazer comentários sucintos e que não dizem nada além do nome do div, faça comentários que contenham informação sobre aquela parte específica do layout.

`/* #topo - Div que contém LOGO, #menu e #busca - Elemento Pai é o #geral */`

Isso se torna uma referência para profissionais que farão modificações posteriores em seu código.

### Caminhos completos em seletores

Sempre use os caminhos inteiros nos seletores. Isso evita erros de conflito no arquivo CSS. Sendo específico você mantém corretamente as heranças dos elementos e consegue ter mais controle sobre seu código.

`div#topo div#menu ul li a {...}`

### Ids e classes, use com moderação

Já vi muita gente fazendo isso:
  
```Este era um assunto que eu queria falar aqui a muito tempo. Vi [este link][1] no [URL Sinistras][2] e me animei a escrever sobre.

Estruturar o código CSS de uma maneira simples e intuitiva ajuda muito no desenvolvimento. Já vi várias pessoas fazendo códigos mirabolantes e depois perdendo tempo porque havia problemas de conflito no CSS.

Vou falar aqui como eu monto meu CSS ou como pelo menos eu tento montá-lo. Estes hábitos são algumas coisas que me torna produtivo quando preciso executar alguma modificação no layout.

### Formatando de fora pra dentro

Muita gente não tem uma regra de onde começa a formatar e de onde termina. Isso ajuda a organizar seu código CSS de uma maneira tão lógica quanto uma estrutura HTML.

Formate seu código começando dos elementos mais amplos para os mais específicos. Comece pela tag HTML (se tiver formatação para ela), depois passe para o BODY, logo após para o div que envolve todo o site (eu costumo chamar de #geral) e assim para os elementos que dividem as seções do site (normalmente: cabecalho, coluna da esquerda, colunas da direita, colunas do meio, rodape etc). Logo após, passe para os elementos que ficam dentro destas divisões e formate-os individualmente.

Veja o seguinte código HTML:

`<html><br />
<body><br />
<div id="geral"><br />
<div id="topo"><br />
<h1><a href="#">Logo do Site</a></h1><br />
<div class="menu"><br />
<ul><br />
<li><a href="#">Home</a></li><br />
<li><a href="#">Produtos</a></li><br />
<li><a href="#">Serviços</a></li><br />
<li><a href="#">Contato</a></li><br />
</ul><br />
</div><br />
</div><br />
</div><br />
</body><br />
</html>`

Código CSS:

``Este era um assunto que eu queria falar aqui a muito tempo. Vi [este link][1] no [URL Sinistras][2] e me animei a escrever sobre.

Estruturar o código CSS de uma maneira simples e intuitiva ajuda muito no desenvolvimento. Já vi várias pessoas fazendo códigos mirabolantes e depois perdendo tempo porque havia problemas de conflito no CSS.

Vou falar aqui como eu monto meu CSS ou como pelo menos eu tento montá-lo. Estes hábitos são algumas coisas que me torna produtivo quando preciso executar alguma modificação no layout.

### Formatando de fora pra dentro

Muita gente não tem uma regra de onde começa a formatar e de onde termina. Isso ajuda a organizar seu código CSS de uma maneira tão lógica quanto uma estrutura HTML.

Formate seu código começando dos elementos mais amplos para os mais específicos. Comece pela tag HTML (se tiver formatação para ela), depois passe para o BODY, logo após para o div que envolve todo o site (eu costumo chamar de #geral) e assim para os elementos que dividem as seções do site (normalmente: cabecalho, coluna da esquerda, colunas da direita, colunas do meio, rodape etc). Logo após, passe para os elementos que ficam dentro destas divisões e formate-os individualmente.

Veja o seguinte código HTML:

`<html><br />
<body><br />
<div id="geral"><br />
<div id="topo"><br />
<h1><a href="#">Logo do Site</a></h1><br />
<div class="menu"><br />
<ul><br />
<li><a href="#">Home</a></li><br />
<li><a href="#">Produtos</a></li><br />
<li><a href="#">Serviços</a></li><br />
<li><a href="#">Contato</a></li><br />
</ul><br />
</div><br />
</div><br />
</div><br />
</body><br />
</html>`

Código CSS:

`` 

Tente seguir a estrutura HTML como referência. Mantendo essa organização, fica simples encontrar os elementos no código CSS.

### Coloque informação importante nos comentários

Comentar qualquer código é sempre uma boa pedida. Em vez de fazer comentários sucintos e que não dizem nada além do nome do div, faça comentários que contenham informação sobre aquela parte específica do layout.

`/* #topo - Div que contém LOGO, #menu e #busca - Elemento Pai é o #geral */`

Isso se torna uma referência para profissionais que farão modificações posteriores em seu código.

### Caminhos completos em seletores

Sempre use os caminhos inteiros nos seletores. Isso evita erros de conflito no arquivo CSS. Sendo específico você mantém corretamente as heranças dos elementos e consegue ter mais controle sobre seu código.

`div#topo div#menu ul li a {...}`

### Ids e classes, use com moderação

Já vi muita gente fazendo isso:
  
``` 

Essa maneira torna o código HTML muito complicado e seu código fica maior sem necessidade. Quando você coloca classes ou ids nos elementos &#8220;pais&#8221;, você controla seus &#8220;filhos&#8221; sem problema algum. Não coloque classes ou ids se você não tiver uma necessidade especifica.

### Identifique o Body

Muitas vezes o designer precisa que alguns detalhes diferentes em diferentes páginas do site. Para facilitar sua vida, coloque uma identificação na tag BODY. Assim você pode mudar os detalhes que precisar de cada página individualmente.
  
```` 
  
`````Este era um assunto que eu queria falar aqui a muito tempo. Vi [este link][1] no [URL Sinistras][2] e me animei a escrever sobre.

Estruturar o código CSS de uma maneira simples e intuitiva ajuda muito no desenvolvimento. Já vi várias pessoas fazendo códigos mirabolantes e depois perdendo tempo porque havia problemas de conflito no CSS.

Vou falar aqui como eu monto meu CSS ou como pelo menos eu tento montá-lo. Estes hábitos são algumas coisas que me torna produtivo quando preciso executar alguma modificação no layout.

### Formatando de fora pra dentro

Muita gente não tem uma regra de onde começa a formatar e de onde termina. Isso ajuda a organizar seu código CSS de uma maneira tão lógica quanto uma estrutura HTML.

Formate seu código começando dos elementos mais amplos para os mais específicos. Comece pela tag HTML (se tiver formatação para ela), depois passe para o BODY, logo após para o div que envolve todo o site (eu costumo chamar de #geral) e assim para os elementos que dividem as seções do site (normalmente: cabecalho, coluna da esquerda, colunas da direita, colunas do meio, rodape etc). Logo após, passe para os elementos que ficam dentro destas divisões e formate-os individualmente.

Veja o seguinte código HTML:

`<html><br />
<body><br />
<div id="geral"><br />
<div id="topo"><br />
<h1><a href="#">Logo do Site</a></h1><br />
<div class="menu"><br />
<ul><br />
<li><a href="#">Home</a></li><br />
<li><a href="#">Produtos</a></li><br />
<li><a href="#">Serviços</a></li><br />
<li><a href="#">Contato</a></li><br />
</ul><br />
</div><br />
</div><br />
</div><br />
</body><br />
</html>`

Código CSS:

``Este era um assunto que eu queria falar aqui a muito tempo. Vi [este link][1] no [URL Sinistras][2] e me animei a escrever sobre.

Estruturar o código CSS de uma maneira simples e intuitiva ajuda muito no desenvolvimento. Já vi várias pessoas fazendo códigos mirabolantes e depois perdendo tempo porque havia problemas de conflito no CSS.

Vou falar aqui como eu monto meu CSS ou como pelo menos eu tento montá-lo. Estes hábitos são algumas coisas que me torna produtivo quando preciso executar alguma modificação no layout.

### Formatando de fora pra dentro

Muita gente não tem uma regra de onde começa a formatar e de onde termina. Isso ajuda a organizar seu código CSS de uma maneira tão lógica quanto uma estrutura HTML.

Formate seu código começando dos elementos mais amplos para os mais específicos. Comece pela tag HTML (se tiver formatação para ela), depois passe para o BODY, logo após para o div que envolve todo o site (eu costumo chamar de #geral) e assim para os elementos que dividem as seções do site (normalmente: cabecalho, coluna da esquerda, colunas da direita, colunas do meio, rodape etc). Logo após, passe para os elementos que ficam dentro destas divisões e formate-os individualmente.

Veja o seguinte código HTML:

`<html><br />
<body><br />
<div id="geral"><br />
<div id="topo"><br />
<h1><a href="#">Logo do Site</a></h1><br />
<div class="menu"><br />
<ul><br />
<li><a href="#">Home</a></li><br />
<li><a href="#">Produtos</a></li><br />
<li><a href="#">Serviços</a></li><br />
<li><a href="#">Contato</a></li><br />
</ul><br />
</div><br />
</div><br />
</div><br />
</body><br />
</html>`

Código CSS:

`` 

Tente seguir a estrutura HTML como referência. Mantendo essa organização, fica simples encontrar os elementos no código CSS.

### Coloque informação importante nos comentários

Comentar qualquer código é sempre uma boa pedida. Em vez de fazer comentários sucintos e que não dizem nada além do nome do div, faça comentários que contenham informação sobre aquela parte específica do layout.

`/* #topo - Div que contém LOGO, #menu e #busca - Elemento Pai é o #geral */`

Isso se torna uma referência para profissionais que farão modificações posteriores em seu código.

### Caminhos completos em seletores

Sempre use os caminhos inteiros nos seletores. Isso evita erros de conflito no arquivo CSS. Sendo específico você mantém corretamente as heranças dos elementos e consegue ter mais controle sobre seu código.

`div#topo div#menu ul li a {...}`

### Ids e classes, use com moderação

Já vi muita gente fazendo isso:
  
```Este era um assunto que eu queria falar aqui a muito tempo. Vi [este link][1] no [URL Sinistras][2] e me animei a escrever sobre.

Estruturar o código CSS de uma maneira simples e intuitiva ajuda muito no desenvolvimento. Já vi várias pessoas fazendo códigos mirabolantes e depois perdendo tempo porque havia problemas de conflito no CSS.

Vou falar aqui como eu monto meu CSS ou como pelo menos eu tento montá-lo. Estes hábitos são algumas coisas que me torna produtivo quando preciso executar alguma modificação no layout.

### Formatando de fora pra dentro

Muita gente não tem uma regra de onde começa a formatar e de onde termina. Isso ajuda a organizar seu código CSS de uma maneira tão lógica quanto uma estrutura HTML.

Formate seu código começando dos elementos mais amplos para os mais específicos. Comece pela tag HTML (se tiver formatação para ela), depois passe para o BODY, logo após para o div que envolve todo o site (eu costumo chamar de #geral) e assim para os elementos que dividem as seções do site (normalmente: cabecalho, coluna da esquerda, colunas da direita, colunas do meio, rodape etc). Logo após, passe para os elementos que ficam dentro destas divisões e formate-os individualmente.

Veja o seguinte código HTML:

`<html><br />
<body><br />
<div id="geral"><br />
<div id="topo"><br />
<h1><a href="#">Logo do Site</a></h1><br />
<div class="menu"><br />
<ul><br />
<li><a href="#">Home</a></li><br />
<li><a href="#">Produtos</a></li><br />
<li><a href="#">Serviços</a></li><br />
<li><a href="#">Contato</a></li><br />
</ul><br />
</div><br />
</div><br />
</div><br />
</body><br />
</html>`

Código CSS:

``Este era um assunto que eu queria falar aqui a muito tempo. Vi [este link][1] no [URL Sinistras][2] e me animei a escrever sobre.

Estruturar o código CSS de uma maneira simples e intuitiva ajuda muito no desenvolvimento. Já vi várias pessoas fazendo códigos mirabolantes e depois perdendo tempo porque havia problemas de conflito no CSS.

Vou falar aqui como eu monto meu CSS ou como pelo menos eu tento montá-lo. Estes hábitos são algumas coisas que me torna produtivo quando preciso executar alguma modificação no layout.

### Formatando de fora pra dentro

Muita gente não tem uma regra de onde começa a formatar e de onde termina. Isso ajuda a organizar seu código CSS de uma maneira tão lógica quanto uma estrutura HTML.

Formate seu código começando dos elementos mais amplos para os mais específicos. Comece pela tag HTML (se tiver formatação para ela), depois passe para o BODY, logo após para o div que envolve todo o site (eu costumo chamar de #geral) e assim para os elementos que dividem as seções do site (normalmente: cabecalho, coluna da esquerda, colunas da direita, colunas do meio, rodape etc). Logo após, passe para os elementos que ficam dentro destas divisões e formate-os individualmente.

Veja o seguinte código HTML:

`<html><br />
<body><br />
<div id="geral"><br />
<div id="topo"><br />
<h1><a href="#">Logo do Site</a></h1><br />
<div class="menu"><br />
<ul><br />
<li><a href="#">Home</a></li><br />
<li><a href="#">Produtos</a></li><br />
<li><a href="#">Serviços</a></li><br />
<li><a href="#">Contato</a></li><br />
</ul><br />
</div><br />
</div><br />
</div><br />
</body><br />
</html>`

Código CSS:

`` 

Tente seguir a estrutura HTML como referência. Mantendo essa organização, fica simples encontrar os elementos no código CSS.

### Coloque informação importante nos comentários

Comentar qualquer código é sempre uma boa pedida. Em vez de fazer comentários sucintos e que não dizem nada além do nome do div, faça comentários que contenham informação sobre aquela parte específica do layout.

`/* #topo - Div que contém LOGO, #menu e #busca - Elemento Pai é o #geral */`

Isso se torna uma referência para profissionais que farão modificações posteriores em seu código.

### Caminhos completos em seletores

Sempre use os caminhos inteiros nos seletores. Isso evita erros de conflito no arquivo CSS. Sendo específico você mantém corretamente as heranças dos elementos e consegue ter mais controle sobre seu código.

`div#topo div#menu ul li a {...}`

### Ids e classes, use com moderação

Já vi muita gente fazendo isso:
  
``` 

Essa maneira torna o código HTML muito complicado e seu código fica maior sem necessidade. Quando você coloca classes ou ids nos elementos &#8220;pais&#8221;, você controla seus &#8220;filhos&#8221; sem problema algum. Não coloque classes ou ids se você não tiver uma necessidade especifica.

### Identifique o Body

Muitas vezes o designer precisa que alguns detalhes diferentes em diferentes páginas do site. Para facilitar sua vida, coloque uma identificação na tag BODY. Assim você pode mudar os detalhes que precisar de cada página individualmente.
  
````Este era um assunto que eu queria falar aqui a muito tempo. Vi [este link][1] no [URL Sinistras][2] e me animei a escrever sobre.

Estruturar o código CSS de uma maneira simples e intuitiva ajuda muito no desenvolvimento. Já vi várias pessoas fazendo códigos mirabolantes e depois perdendo tempo porque havia problemas de conflito no CSS.

Vou falar aqui como eu monto meu CSS ou como pelo menos eu tento montá-lo. Estes hábitos são algumas coisas que me torna produtivo quando preciso executar alguma modificação no layout.

### Formatando de fora pra dentro

Muita gente não tem uma regra de onde começa a formatar e de onde termina. Isso ajuda a organizar seu código CSS de uma maneira tão lógica quanto uma estrutura HTML.

Formate seu código começando dos elementos mais amplos para os mais específicos. Comece pela tag HTML (se tiver formatação para ela), depois passe para o BODY, logo após para o div que envolve todo o site (eu costumo chamar de #geral) e assim para os elementos que dividem as seções do site (normalmente: cabecalho, coluna da esquerda, colunas da direita, colunas do meio, rodape etc). Logo após, passe para os elementos que ficam dentro destas divisões e formate-os individualmente.

Veja o seguinte código HTML:

`<html><br />
<body><br />
<div id="geral"><br />
<div id="topo"><br />
<h1><a href="#">Logo do Site</a></h1><br />
<div class="menu"><br />
<ul><br />
<li><a href="#">Home</a></li><br />
<li><a href="#">Produtos</a></li><br />
<li><a href="#">Serviços</a></li><br />
<li><a href="#">Contato</a></li><br />
</ul><br />
</div><br />
</div><br />
</div><br />
</body><br />
</html>`

Código CSS:

``Este era um assunto que eu queria falar aqui a muito tempo. Vi [este link][1] no [URL Sinistras][2] e me animei a escrever sobre.

Estruturar o código CSS de uma maneira simples e intuitiva ajuda muito no desenvolvimento. Já vi várias pessoas fazendo códigos mirabolantes e depois perdendo tempo porque havia problemas de conflito no CSS.

Vou falar aqui como eu monto meu CSS ou como pelo menos eu tento montá-lo. Estes hábitos são algumas coisas que me torna produtivo quando preciso executar alguma modificação no layout.

### Formatando de fora pra dentro

Muita gente não tem uma regra de onde começa a formatar e de onde termina. Isso ajuda a organizar seu código CSS de uma maneira tão lógica quanto uma estrutura HTML.

Formate seu código começando dos elementos mais amplos para os mais específicos. Comece pela tag HTML (se tiver formatação para ela), depois passe para o BODY, logo após para o div que envolve todo o site (eu costumo chamar de #geral) e assim para os elementos que dividem as seções do site (normalmente: cabecalho, coluna da esquerda, colunas da direita, colunas do meio, rodape etc). Logo após, passe para os elementos que ficam dentro destas divisões e formate-os individualmente.

Veja o seguinte código HTML:

`<html><br />
<body><br />
<div id="geral"><br />
<div id="topo"><br />
<h1><a href="#">Logo do Site</a></h1><br />
<div class="menu"><br />
<ul><br />
<li><a href="#">Home</a></li><br />
<li><a href="#">Produtos</a></li><br />
<li><a href="#">Serviços</a></li><br />
<li><a href="#">Contato</a></li><br />
</ul><br />
</div><br />
</div><br />
</div><br />
</body><br />
</html>`

Código CSS:

`` 

Tente seguir a estrutura HTML como referência. Mantendo essa organização, fica simples encontrar os elementos no código CSS.

### Coloque informação importante nos comentários

Comentar qualquer código é sempre uma boa pedida. Em vez de fazer comentários sucintos e que não dizem nada além do nome do div, faça comentários que contenham informação sobre aquela parte específica do layout.

`/* #topo - Div que contém LOGO, #menu e #busca - Elemento Pai é o #geral */`

Isso se torna uma referência para profissionais que farão modificações posteriores em seu código.

### Caminhos completos em seletores

Sempre use os caminhos inteiros nos seletores. Isso evita erros de conflito no arquivo CSS. Sendo específico você mantém corretamente as heranças dos elementos e consegue ter mais controle sobre seu código.

`div#topo div#menu ul li a {...}`

### Ids e classes, use com moderação

Já vi muita gente fazendo isso:
  
```Este era um assunto que eu queria falar aqui a muito tempo. Vi [este link][1] no [URL Sinistras][2] e me animei a escrever sobre.

Estruturar o código CSS de uma maneira simples e intuitiva ajuda muito no desenvolvimento. Já vi várias pessoas fazendo códigos mirabolantes e depois perdendo tempo porque havia problemas de conflito no CSS.

Vou falar aqui como eu monto meu CSS ou como pelo menos eu tento montá-lo. Estes hábitos são algumas coisas que me torna produtivo quando preciso executar alguma modificação no layout.

### Formatando de fora pra dentro

Muita gente não tem uma regra de onde começa a formatar e de onde termina. Isso ajuda a organizar seu código CSS de uma maneira tão lógica quanto uma estrutura HTML.

Formate seu código começando dos elementos mais amplos para os mais específicos. Comece pela tag HTML (se tiver formatação para ela), depois passe para o BODY, logo após para o div que envolve todo o site (eu costumo chamar de #geral) e assim para os elementos que dividem as seções do site (normalmente: cabecalho, coluna da esquerda, colunas da direita, colunas do meio, rodape etc). Logo após, passe para os elementos que ficam dentro destas divisões e formate-os individualmente.

Veja o seguinte código HTML:

`<html><br />
<body><br />
<div id="geral"><br />
<div id="topo"><br />
<h1><a href="#">Logo do Site</a></h1><br />
<div class="menu"><br />
<ul><br />
<li><a href="#">Home</a></li><br />
<li><a href="#">Produtos</a></li><br />
<li><a href="#">Serviços</a></li><br />
<li><a href="#">Contato</a></li><br />
</ul><br />
</div><br />
</div><br />
</div><br />
</body><br />
</html>`

Código CSS:

``Este era um assunto que eu queria falar aqui a muito tempo. Vi [este link][1] no [URL Sinistras][2] e me animei a escrever sobre.

Estruturar o código CSS de uma maneira simples e intuitiva ajuda muito no desenvolvimento. Já vi várias pessoas fazendo códigos mirabolantes e depois perdendo tempo porque havia problemas de conflito no CSS.

Vou falar aqui como eu monto meu CSS ou como pelo menos eu tento montá-lo. Estes hábitos são algumas coisas que me torna produtivo quando preciso executar alguma modificação no layout.

### Formatando de fora pra dentro

Muita gente não tem uma regra de onde começa a formatar e de onde termina. Isso ajuda a organizar seu código CSS de uma maneira tão lógica quanto uma estrutura HTML.

Formate seu código começando dos elementos mais amplos para os mais específicos. Comece pela tag HTML (se tiver formatação para ela), depois passe para o BODY, logo após para o div que envolve todo o site (eu costumo chamar de #geral) e assim para os elementos que dividem as seções do site (normalmente: cabecalho, coluna da esquerda, colunas da direita, colunas do meio, rodape etc). Logo após, passe para os elementos que ficam dentro destas divisões e formate-os individualmente.

Veja o seguinte código HTML:

`<html><br />
<body><br />
<div id="geral"><br />
<div id="topo"><br />
<h1><a href="#">Logo do Site</a></h1><br />
<div class="menu"><br />
<ul><br />
<li><a href="#">Home</a></li><br />
<li><a href="#">Produtos</a></li><br />
<li><a href="#">Serviços</a></li><br />
<li><a href="#">Contato</a></li><br />
</ul><br />
</div><br />
</div><br />
</div><br />
</body><br />
</html>`

Código CSS:

`` 

Tente seguir a estrutura HTML como referência. Mantendo essa organização, fica simples encontrar os elementos no código CSS.

### Coloque informação importante nos comentários

Comentar qualquer código é sempre uma boa pedida. Em vez de fazer comentários sucintos e que não dizem nada além do nome do div, faça comentários que contenham informação sobre aquela parte específica do layout.

`/* #topo - Div que contém LOGO, #menu e #busca - Elemento Pai é o #geral */`

Isso se torna uma referência para profissionais que farão modificações posteriores em seu código.

### Caminhos completos em seletores

Sempre use os caminhos inteiros nos seletores. Isso evita erros de conflito no arquivo CSS. Sendo específico você mantém corretamente as heranças dos elementos e consegue ter mais controle sobre seu código.

`div#topo div#menu ul li a {...}`

### Ids e classes, use com moderação

Já vi muita gente fazendo isso:
  
``` 

Essa maneira torna o código HTML muito complicado e seu código fica maior sem necessidade. Quando você coloca classes ou ids nos elementos &#8220;pais&#8221;, você controla seus &#8220;filhos&#8221; sem problema algum. Não coloque classes ou ids se você não tiver uma necessidade especifica.

### Identifique o Body

Muitas vezes o designer precisa que alguns detalhes diferentes em diferentes páginas do site. Para facilitar sua vida, coloque uma identificação na tag BODY. Assim você pode mudar os detalhes que precisar de cada página individualmente.
  
```` 
  
````` 

### Organize as propriedades

Existem diversas propriedades do CSS e cada uma delas modifica uma característica dos elementos. Há propriedades que formatam o visual do elemento (display, border, background, color, font, text etc&#8230;), há outras propriedades que modificam medidas e distâncias (margin, padding, width, height, min-width, min-height etc&#8230;) e outras propriedades que posicionam os elementos (float, position).

Eu organizo primeiro propriedades controlam o visual, depois as propriedades de distâncias e medidas e logo após propriedades de posicionamento.

`````` 

A única dificuldade que tenho é de aplicar essas sugestões. 😉 A pressa me vence sempre e muitas vezes eu me &#8220;esqueço&#8221; de aplicar uma dessas sugestões. O código CSS é a base do site inteiro, ele precisa ter uma bela organização, ser legível. Ter controle sobre o arquivo CSS é tudo. Você fica muito mais produtivo. Mas tem que se habituar, se acostumar com essas novas regrinhas.

 [1]: http://friendlybit.com/css/how-to-structure-large-css-files/
 [2]: http://sinistras.aranha.com.br/2007/02/css-2/