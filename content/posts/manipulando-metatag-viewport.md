---
title: Manipulando a metatag Viewport
author: Diego Eis
type: post
date: 2011-04-18
excerpt: Aprenda a manipular o viewport de mobiles e outros dispositivos com a metatag Viewport do HTML.
url: /manipulando-metatag-viewport/
tweetbackscheck:
  - 1356397672
shorturls:
  - 'a:3:{s:9:"permalink";s:52:"http://tableless.com.br/manipulando-metatag-viewport";s:7:"tinyurl";s:26:"http://tinyurl.com/3odakfo";s:4:"isgd";s:19:"http://is.gd/bKHkmh";}'
twittercomments:
  - 'a:10:{i:127188376863518722;s:7:"retweet";i:126465282385522690;s:7:"retweet";i:126348029631533056;s:7:"retweet";i:126347228095848448;s:7:"retweet";i:126345823905783808;s:7:"retweet";i:126341375041085440;s:7:"retweet";i:155242144943190018;s:7:"retweet";i:155229542263422976;s:7:"retweet";i:160165094976798720;s:7:"retweet";i:169916451069763584;s:7:"retweet";}'
tweetcount:
  - 21
dsq_thread_id: 503027964
categories:
  - Acessibilidade
  - Browsers
  - Mobile
  - Técnicas e Práticas
tags:
  - 2011
  - acessibilidade
  - Browsers
  - internetmovel
  - Mobile
  - mobilidade
  - Na Prática
  - padroes web

---
O viewport é a área onde seu website aparece. É a área branca da janela quando você abre o browser. O viewport sempre vai ter o tamanho da janela. Mas a forma como os elementos são renderizados vai depender bastante do dispositivo. Em máquinas desktop nós não precisamos nos preocupar muito, já estamos acostumados com um determinado tamanho de tela e resolução média utilizada pelos usuários. Mas quando começamos a variar muito o tamanho das telas, a largura do viewport começa a ser uma preocupação porque afeta diretamente a forma como o usuário utiliza seu website. O ponto é que em uma tela pequena, com uma resolução muito grande, por exemplo como as telas dos iPhone e da maioria dos smartphones de hoje, o conteúdo pode aparecer muito, muito pequeno. Imagine uma resolução FULL HD dentro de uma tela bem menor que uma TV&#8230; Por isso precisamos fazer com que o viewport mostre o conteúdo se baseando pelo tamanho da tela e não da resolução.

Hoje existe uma gama muito grande de aparelhos com telas de tamanhos variados. Comece a pensar pelos notebooks de 11 ou 10 polegadas. Depois vá diminuindo até chegar em um smartphone popular como iPhone e os Samsungs da vida. A variação de tamanho de tela é muito grande. Lembrando que o tamanho da tela é uma coisa e a resolução de tela é outra. Nunca confunda os dois. A largura da tela do iPhone 5s na posição retrato é de 320px. Mas sua resolução padrão é 980px. Isso quer dizer que se você fizer um HTML simples, colocar uma imagem de 980px de largura e visualizar no iPhone, não existirá barra de rolagem. Obviamente a imagem ficará miniaturizada, como mostra abaixo:

![][1]

Isso é interessante porque possibilita a boa visualização de websites que não estão preparados para mobiles. Vemos o site inteiro miniaturizado, com possibilidade de fazer zoom em qualquer parte do layout.

### A tag meta viewport

Mesmo assim os smartphones tem telas pequenas podem dificultar a leitura se fizermos um sistema planejado para grandes resoluções. Por isso é interessante que possamos customizar o viewport para que ele se adeque a realidade desses dispositivos. É aí que entra a metatag viewport.
  
Com essa metatag iremos customizar a resolução inicial que o browser deve renderizar do viewport do dispositivo. Dessa forma, podemos preparar websites com resoluções personalizadas para smartphones e outros aparelhos.

A sintaxe é muito simples e deve ser colocada, como sempre, na tag **head**:

<pre class="lang-html">&lt;meta name="viewport" content=""&gt;
</pre>

Os valores de content são os que seguem abaixo:

| Valor         | Descrição                                                                                                                                                                    |
| ------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| width         | Define uma largura para o viewport. Os valores podem ser em PX ou &#8220;device-width&#8221;, que determina automaticamente um valor igual a largura da tela do dispositivo. |
| height        | Define uma altura para o viewport. Os valores podem ser em PX ou &#8220;device-height&#8221;, que determina automaticamente um valor igual a altura da tela do dispositivo.  |
| initial-scale | Define a escala inicial do viewport.                                                                                                                                         |
| user-scalable | Define a possibilidade de o usuário fazer &#8220;zoom&#8221; em um determinado lugar da tela. É ativado quando o usuário bate duas vezes com o dedo em um lugar da tela.     |

### Como usar

A tela abaixo não tem nenhuma tag de viewport definida. 

![][2]

Veja que o texto do elemento está bem pequeno. Isso é porque estamos visualizando-o em 980px de resolução em uma tela de smartphone.
  
Vou acrescentar a seguinte linha:

<pre class="lang-html">&lt;meta name="viewport" content="width=320px"&gt;
</pre>

Define que a largura do viewport será 320px. O resultado está abaixo:

![][3]

Se inserirmos uma imagem ou um objeto maior que a largura do viewport, uma barra de rolagem é criada. Não precisa se preocupar com o espaço da barra, já que pelo menos nos OSs de smartphones novos, como iPhone e Android, a barra fica invisível e só aparece pro cima dos elementos.

![][4]

Adicionando o **initial-scale** com o valor de 1.5, temos um aumento na escala da visualização. Abaixo segue um exemplo comparativo. A imagem inserida tem 320px de largura, logo ela ficará bem justa na tela quando a escala é 1.0, e um pouco estourada quando a escala é 1.5 ou maior. Veja:

![][5]

Agora com escala de 1.5:

![][6]

Agora com escala de 2:
  
![][7]

E agora com texto, nas mesmas proporções:

![][8]
  
![][9]
  
![][10]

Se colocarmos o **user-scalable** como NO, desabilitamos a possibilidade do usuário de fazer zoom quando ele bate duas vezes com o dedo. Deixar habilitado o zoom é interessante utilizar quando o viewport não está sendo customizado. No nosso caso aqui, isso não iria adiantar muita coisa, já que todos os elementos estão com o tamanho natural, por isso vamos desabilitá-lo.

<pre class="lang-html">&lt;meta name="viewport" content="width=320px, user-scalable=no"&gt;
</pre>

Atente-se para o detalhe de colocar , (vírgula) entre um valor e outro.
  
Veja um [exemplo aqui][11]. Tente ver com um smartphone como o iPhone, Android, etc.

Manipular o Viewport nos dá possibilidades para personalizar o visual de qualquer site para praticamente qualquer dispositivo, não importa sua resolução ou seu tamanho de tela. Quando unimos isso às [media queries][12], temos um outro mundo de possibilidades.

 [1]: http://tableless.com.br/uploads/2011/04/980px.png
 [2]: http://tableless.com.br/uploads/2011/04/viewport-980.png
 [3]: http://tableless.com.br/uploads/2011/04/viewport-320px.png
 [4]: http://tableless.com.br/uploads/2011/04/rolagem.png
 [5]: http://tableless.com.br/uploads/2011/04/initi-scale1.png
 [6]: http://tableless.com.br/uploads/2011/04/init-scale15.png
 [7]: http://tableless.com.br/uploads/2011/04/init-scale2.png
 [8]: http://tableless.com.br/uploads/2011/04/scale1-text.png
 [9]: http://tableless.com.br/uploads/2011/04/scale15-text.png
 [10]: http://tableless.com.br/uploads/2011/04/scale2-text.png
 [11]: http://tableless.github.com/exemplos/viewport/viewport.html
 [12]: http://tableless.com.br/introducao-sobre-media-queries