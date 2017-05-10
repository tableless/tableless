---
title: CSS3 – Texturizando textos
author: Thaiana Poplade
type: post
date: 2012-02-23
excerpt: Com funcionalidades que apoiam resultados visuais exclusivamente à folhas de estilo, o CSS3 está sendo criado para otimizar fluxo e ritmo de trabalho, além de aproximar ainda mais Designers de Interfaces à profissionais Front-End. Com vocês, a texturização de textos via CSS3.
url: /css3-texturizando-textos/
tweetbackscheck:
  - 1356415575
shorturls:
  - 'a:3:{s:9:"permalink";s:31:"http://tableless.com.br/?p=5542";s:7:"tinyurl";s:26:"http://tinyurl.com/7evv8xy";s:4:"isgd";s:19:"http://is.gd/TBTIPr";}'
twittercomments:
  - 'a:0:{}'
dsq_thread_id: 586505255
categories:
  - CSS
  - CSS3
  - HTML
  - HTML5
  - Técnicas e Práticas
tags:
  - 2012
  - html. css3
  - Na Prática
  - tecnicascss

---
Com o uso da versão 3, já podemos tornar possível a criação de sombra em textos e boxes, arredondamento de bordas, múltiplos backgrounds, etc; objetivando reduzir o tempo de carregamento da página e estimulando o cuidado na utilização de códigos e textos limpos que servirão de comunicação para robôs de busca ou favorecerão a acessibilidade do website.

A exemplo de mais uma das vantagens do CSS3, vamos conhecer melhor como aplicar uma imagem de textura ao preenchimento de um texto, utilizando apenas declarações &#8220;fonts&#8221; na folha de estilo.

Vale ressaltar que o exemplo abaixo funcionará, neste momento, exclusivamente no Chrome e no Safari em suas últimas versões. E antes que você pense: “então, não poderei aplicar aos meus projetos&#8230;”, te tranquilizo; talvez você não possa aplicar aos projetos para web em desktop e diversos tipos de outros navegadores, mas você poderá aplicar a seus projetos mobile ou para tablets.  Pense nisso! 😉

Então, vamos lá!

Crie um novo documento html com a seguinte marcação:
  
[cc lang=&#8221;css&#8221;]</p> <header> 

# Wood</header> 

</body>[/cc]

Após, adicione as características de estilo (uso aqui a aplicação incorporada para facilitar os testes):
  
[cc lang=&#8221;css&#8221;]body{background:#fff}
  
h1{      
  
font:72px bold &#8220;Arial Black&#8221;, Gadget, sans-serif;     
  
color:#930;     
  
text-transform:uppercase;     
  
border:solid 20px #930;     
  
padding:10px;
  
}[/cc]

A princípio, seu texto está assim:

[<img class="alignnone size-medium wp-image-5549" src="http://tableless.com.br/uploads/2012/02/img1.png" alt="" width="300" height="151" />][1]

Agora, vamos abrir um dos editores de imagem – Photoshop ou Fireworks – e criar uma **imagem PNG** com a nossa textura. Em meu teste inicial, eu utilizei uma imagem de textura pronta, mas o resultado não ficou como esperado, então aconselho colocar seus dotes de criação em atividade e realmente criar a textura.
  
Abaixo uma breve explicação da textura que criei no Fireworks.

Utilizando o Fireworks, crie um novo documento (1900&#215;200), selecione a ferramenta pincel, depois aplique as seguintes características (barra de ferramentas inferior): **Tip size – 300 | Stroke Category – Pencil Pixel Soft | Texture – Line vertical e Burlap.**

**[<img class="size-medium wp-image-5550 alignleft" style="margin-right: 10px" src="http://tableless.com.br/uploads/2012/02/img2.png" alt="" width="300" height="269" />][2]**

Na hora de escolher a melhor forma de exportar sua imagem, o cuidado com o peso em kb continua valendo. Em se tratando de PNG, é muito fácil um simples arquivo ficar com mais de 500kb, por isso, em meus testes observei que exportando em PNG8 você vai ter um arquivo de 52kb com uma qualidade visual menor, mas que dependendo do estilo de textura é perfeitamente aplicável, ou exportando em PNG32 você preza por uma qualidade visual melhor, mas ao custo de um arquivo de 200kb. A escolha vai depender da velocidade de conexão ao qual você vai estabelecer para esta aplicação e do resultado visual que você julgar aceitável.

Criada a imagem, vamos incluir ao style do texto o atributo **“mask-image”** que definem a textura no texto.
  
[cc lang=&#8221;css&#8221;]h1{      
  
font:72px bold &#8220;Arial Black&#8221;, Gadget, sans-serif;     
  
color:#930;
  
text-transform:uppercase;     
  
border:solid 20px #930;     
  
padding:10px;     

-webkit-mask-image: url(text2.png);
  
-o-mask-image: url(text2.png);
  
-moz-mask-image: url(text2.png);
  
mask-image: url(text2.png);
  
}[/cc]
  
Reload no navegador&#8230; e voilá! Um texto com um preenchimento texturizado.

[<img class="alignnone size-medium wp-image-5553" src="http://tableless.com.br/uploads/2012/02/img3.png" alt="" width="300" height="117" />][3]

Daí para frente você pode incrementar utilizando <a title="Propriedade @font-face CSS – Fonts externas na web" href="http://tableless.com.br/font-face-fonts-externas-na-web/" target="_blank">font-face</a>, <a title="CSS3 – Sombras em textos e elementos" href="http://tableless.com.br/css3-sombras-em-textos-e-elementos/" target="_blank">text-shadow</a> ou outras texturas. Fica a critério da sua criatividade.

Até a próxima!

😉

 [1]: http://tableless.com.br/uploads/2012/02/img1.png
 [2]: http://tableless.com.br/uploads/2012/02/img2.png
 [3]: http://tableless.com.br/uploads/2012/02/img3.png