---
title: Imagens Responsivas de Alta Performance
author: Dani Guerrato
type: post
date: 2014-03-31
excerpt: 'Saiba como escolher a melhor solução para lidar com imagens responsivas em larga escala sem sacrificar a performance. '
url: /imagens-responsivas-de-alta-performance/
dsq_thread_id: 2465226163
categories:
  - Responsive Web Design (RWD)
tags:
  - densidade de pixels
  - design responsivo
  - imagens responsivas

---
Desenvolver sites responsivos muitas vezes é como fazer malabarismo. São muitas bolas para manter no ar: largura do viewport, medidas relativas, velocidade da conexão, densidade de pixel e experiência do usuário. Lidar com o peso de tudo isto sem quebrar o layout é um objetivo bem difícil de atingir e por isto, muitos desenvolvedores, clientes e consequentemente usuários se afastam da ideia. No artigo de hoje vamos conhecer algumas técnicas de design responsivo para otimização de imagens que ajudam a reduzir (e muito) o peso final dos sites responsivos e equilibrar as bolas no ar.

## A raíz do problema

Esta técnica é simples e didática e, provavelmente, foi a primeira que você aprendeu quando começou seus estudos de Design Responsivo. Basta declarar no CSS que todas as imagens tenham largura máxima de 100% que todas as figuras do seu layout vão se redimensionar automaticamente e proporcionalmente &#8211; de acordo com a largura do container pai.

<pre class="lang-css">img {
  max-width:100%;
}</pre>

Isto aparentemente funciona e bem. Mas, se fosse o caminho ideal, o nosso artigo terminaria por aqui, certo? Vamos ver os principais problemas:

  1. O pepino principal aqui é a performance. Você está essencialmente fazendo um usuário de um dispositivo móvel baixar arquivos muito mais pesados do que ele realmente precisa… Para que usar uma imagem gigante de 2560x1600px se ela será vista em um celular de 320x480px? Isto pode ser passável se existirem poucas imagens no seu layout. Mas multiplique isto por dezenas e uma breve visita ao seu site pode muito bem esgotar o plano de dados de alguém.
  2. Você necessariamente precisa de um container. Pode ser uma div, um figure ou até mesmo um span mas a imagem precisa **estar dentro de alguma coisa**. E isto pode acrescentar diversas linhas a mais de código que não seriam realmente necessárias.
  3. As vezes o ideal não é encolher uma imagem e sim substituí-la. Pode ser que o seu banner &#8220;hero&#8221; tenha um texto aplicado ou que a imagem simplesmente perca os detalhes em um tamanho menor. Neste caso você poderia deixar duas imagens no código e usar um display:none no CSS para esconder e mostrar as imagens certas através de media queries. Mas o resultado em performance será ainda mais desastroso pois você está fazendo o usuário baixar DUAS imagens no lugar de uma. Imagine a bagunça se o designer inventar de ter uma imagem para tablets, para televisão, para console portátil….

## O dilema

Esta é a hora que eu gostaria de escrever que existe uma solução perfeita para este problema. Mas vou ser direta e objetiva com vocês: não existe (ainda). O que nós temos são várias tentativas de contornar o problema, cada uma focada em um aspecto… Algumas das ferramentas que eu vou mostrar a seguir resolvem bem o lado da direção de arte, mas deixam a desejar em semântica e performance, por exemplo. Outras tem o código mais enxuto, mas a implementação depende de uma programação específica server-side. A minha sugestão é: conheça e explore todas elas. Assim vocês saberão os pontos fortes e fracos e qual combina melhor com cada projeto.

Bem, para escolher qual solução funciona melhor para o seu projeto você precisa se fazer algumas perguntas:

  * Direção de arte é importante para o seu caso (por exemplo: imagens diferentes / cropadas para cada largura)?
  * Você está começando do zero ou possui um código legado para dar suporte?
  * Você se importa de utilizar JavaScript ou bibliotecas como jQuery?
  * Testar a velocidade da conexão do usuário é algo importante?
  * Você está utilizando conteúdo dinâmico?
  * Você se importa de lidar com aspectos server side?
  * Qual é a importância que você dá para semântica?
  * Qual é a importância que você dá para validação?
  * O seu cliente vai ter que por a mão ali?
  * Você se importa de escrever HTML extra?

Se isto fosse um daqueles antigos livros de RPG cada uma destas perguntas estaria acompanhado de um &#8220;vá para a página 42&#8221; ou algo do tipo. Pois sim, basicamente você vai ter que escolher entre o caminho menos mal ou sofrer com a performance. Mas, para trazer um pouco de esperança e restaurar a fé na humanidade, vamos dar uma espiadinha no futuro.

## O Futuro (com o Elemento Picture)

Através do picture é possível declarar diversas fontes para uma única imagem no seu HTML e controlar qual deve ser apresentada utilizando media queries. Isto é feito utilizando a tag picture em conjunto com o parâmetro source. Desta forma é possível especificar imagens diferentes de acordo com a largura e altura da janela do browser, orientação do dispositivo, densidade de pixels, layout para a impressão, etc. Obviamente devemos utilizar esta especificação apenas quando existir mais de uma imagem, optando pelo bom e velho img quando tiver apenas uma figura. O img também serve de fallback para browsers que não aceitam o picture.

<pre class="lang-html">&lt;picture&gt;
    &lt;source srcset="pic1x.jpg 1x, pic2x.jpg 2x, pic4x.jpg 4x"&gt;
    &lt;img alt="descrição da imagem" src="pic1x.jpg" width="500" height="500"&gt;
&lt;/picture&gt;</pre>

Reparem que 3 endereços foram especificados no source srcset: pix1x, pic2x e pix4x. Os atributos seguintes (1x, 2x e 4x) são &#8220;dicas&#8221; para o user agent trocar a imagem de acordo com a densidade de pixels da tela. Sendo que 1x é a padrão, 2x o dobro da densidade, etc. Mas, em muitos casos, isto não é específico o suficiente. Podemos então acrescentar um valor Xw e Xh referente a altura e largura do viewport.

<pre class="lang-html">&lt;picture&gt;
    &lt;source sizes="100%" srcset="pic400.jpg 400w, pic800.jpg 800w, pic1600.jpg 1600w"&gt;
    &lt;img src="pic400.jpg" alt="descrição da imagem"&gt;
&lt;/picture&gt;</pre>

Ou trabalhar em conjunto com media queries.

<pre class="lang-html">&lt;picture&gt;
    &lt;source media="(min-width: 45em)" srcset="grande.jpg"&gt;
    &lt;source media="(min-width: 18em)" srcset="media.jpg"&gt;
    &lt;img src="pequena.jpg" alt="descrição da imagem"&gt;
&lt;/picture&gt;</pre>

Os pontos positivos são muitos. A solução já tem um [rascunho &#8220;oficial&#8221; na W3C][1], é semântica, versátil e permite direção de arte. Se eu pudesse apostar em um padrão seria neste. O problema é que nenhum browser atual aceita esta solução. Nenhunzinho mesmo. Ela está prevista no roadmap do Firefox, e provavelmente, será implantada em breve nos outros browsers mais moderninhos. Por enquanto é possível testar a implementação apenas em versões de testes. Mas vale consultar o site do grupo [ResponsiveImages.org][2]  de tempos em tempos e ficar de olho no sinal verde para colocar em prática. Outro ponto contra é que esta solução exige acrescentar código extra o que pode ser inviável se você já possui um site implantado com milhares de imagens para editar manualmente. Para saber mais basta consultar a [documentação oficial][3] ou o [repositório no GitHub.][4]

## A imitação do picture (com Picturefill)

Bem, vamos conversar sobre o que podemos fazer hoje! O picturefill.js através dos poderes mágicos do JavaScript imita a funcionalidade do elemento picture. A solução é bem leve: 498bytes &#8211; o que francamente já compensa o peso de qualquer imagem. O mark-up fica assim:

<pre class="lang-html">&lt;span data-picture data-alt="Descrição da imagem"&gt;
   &lt;span data-src="pequena.jpg"&gt;&lt;/span&gt;
   &lt;span data-src="media.jpg"     data-media="(min-width: 400px)"&gt;&lt;/span&gt;
   &lt;span data-src="grande.jpg"      data-media="(min-width: 800px)"&gt;&lt;/span&gt;
   &lt;span data-src="extragrande.jpg" data-media="(min-width: 1000px)"&gt;&lt;/span&gt;

   &lt;!-- Fallback para quando o JavaScript estiver desativado. --&gt;
   &lt;noscript&gt;
      &lt;img src="small.jpg" alt="Descrição da imagem"&gt;
   &lt;/noscript&gt;
&lt;/span&gt;</pre>

Bem, basicamente ele utiliza spans (que sozinhos não possuem valor semântico) no lugar do picture. E, através dos atributos data-src e data-media, especifica respectivamente o endereço e largura do viewport. Note também que existe um fallback para browsers mobile antigos / ambientes sem JavaScript dentro da tag .

É possível incluir no data-media qualquer media-querie, ou seja, facilmente podemos adaptar este código para densidade de pixel diferente, outros tipos de dispositivos, etc.

<pre class="lang-html">&lt;span data-picture data-alt="Descrição da imagem"&gt;
   &lt;span data-src="imagem.jpg"&gt;&lt;/span&gt;
   &lt;span data-src="imagem_x2.jpg" data-media="(min-device-pixel-ratio: 2.0)"&gt;&lt;/span&gt;
&lt;/span&gt;</pre>

Como o IE8 e versões anteriores não trabalham com media queries, ele ficará com a primeira imagem com atributo data-src (ou com a última imagem se nenhuma especificar este atributo). Alternativamente você pode utilizar comentários condicionais para servir outra figura.

<pre class="lang-html">&lt;!--[if (lt IE 9) & (!IEMobile)]&gt;
    &lt;span data-src="imagem.jpg"&gt;&lt;/span&gt;
&lt;![endif]--&gt;</pre>

Você pode checar a [demo online][5] para ver a bruxaria acontecer. Ou dar uma olhadinha no [GitHub do projeto][6] para ler a documentação completa.

A sintaxe obviamente não vai validar. Isto não é exatamente um sinal de um código bom ou rum, mas se você está em uma situação onde isto é vital (pressão e um cliente, por exemplo) é melhor optar por outro caminho. Como esta solução é baseada no funcionamento do picture os mesmos contras se aplicam: linhas de código a mais e consequente dificuldade de implantação se o seu legado for grande, com o agravante extra de depender de JavaScript. Mas se estes pontos não forem problemáticos para você, vá fundo e tenha imagens responsivas de alta performance hoje mesmo!

## A detecção de banda (com Foresight.js)

O Foresight.js funciona de maneira um pouco diferente das soluções apresentadas até aqui. Ele basicamente testa a velocidade da conexão do usuário antes de realizar a requisição da imagem no servidor. Isto é ótimo pois vai um pouco contra o mito de que se um usuário está em um dispositivo móvel automaticamente a internet é lenta. Eu utilizo tablets no wi-fi o dia todo em casa e por aqui a conexão é de 100mb, enquanto a internet na casa dos meus pais que serve os computadores desktops é provavelmente mais lenta que o meu 3G. Testar a velocidade da banda é a maneira mais efetiva de verificar quem de fato pode se dar ao luxo de baixar imagens pesadas ou não. O foresight também detecta automaticamente a densidade de pixels do dispositivo, permite as imagens serem controladas por CSS (inclusive com background images), impede requisições múltiplas e não depende de user agents.

Infelizmente isto tem um preço: uma imagem de 50k é baixada para testar a velocidade da conexão, bloqueando o download de outras imagens até o teste ser completo. Portanto, utilize esta solução apenas quando o carregamento de todas as imagens realmente for fazer a diferença na performance. Ou você estará tampando o sol com uma peneira.

Na prática funciona da seguinte maneira: depois de apontar para o arquivo js no seu HTML você determina uma classe para a sua imagem. Ah, e lembre-se de utilizar o noscript como fallback.

<pre class="lang-html">&lt;img data-src="imagem.w320.jpg" data-width="320" data-height="212" class="fs-img"&gt;
&lt;noscript&gt;
   &lt;img src=imagem-fallback.jpg"&gt;
&lt;/noscript&gt;</pre>

Depois é só especificar a classe no CSS, substituindo w320 por quaisquer resoluções que você desejar.

<pre class="lang-css">font-family: 'image-set( url(w320|w{requestWidth}) 2x high-bandwidth )';
display:none;</pre>

Repare que isto é feito através do atributo font-family o que é basicamente dar uma voadora na cara da semântica. Eu sei. Isto me faz ranger os dentes. Mas talvez seja uma boa maneira de pressionar os browsers e orgãos responsáveis a aprovarem mais depressa um padrão oficial para imagens responsivas, como o elemento picture. A reação pode ser algo do tipo &#8220;Oh meu deus! Eles estão utilizando font-family para isto. Devem mesmo estar desesperados!&#8221;. Sem contar que tudo é resolvido apenas por CSS, não requerendo nenhum HTML extra o que é ótimo para conteúdos dinâmicos. E, por incrível, que pareça esta gambiarra valida. Mais uma prova que validação é diferente de semântica. Cabe a você decidir o que é mais importante: semântica ou performance? Apenas me prometa que, se você decidir por utilizar algo assim, vai voltar e deixar tudo bonitinho assim que um padrão bacana for aprovado.

Saiba mais na [Documentação Oficial][7], no [GitHub do Foresight][8] ou de uma olhada nas [demos do projeto][9]. Lembre-se de utilizar diversos dispositivos ou você não verá nada de diferente acontecendo.

## A saga mobile first (com HISRC)

Esta solução é um pouco parecida com o Foresight, com a diferença que ao invés de detectar a velocidade através de um placeholder, o HiSRC baixa sempre a imagem mobile primeiro. Se o usuário estiver em uma conexão lenta a imagem mobile fica lá bonitona. Já se a conexão for rápida a versão @1x é baixada. Se a internet for rápida E o dispositivo tiver alta densidade de pixels a versão @2x da imagem é entregue. Isto significa na prática que sim, mais de uma imagem pode ser baixada em uma banda larga. Mas se é para &#8220;punir&#8221; alguém, que seja quem tem menos a perder, certo?

Para implantar primeiro é necessário chamar o arquivo jQuery e depois configura-lo para as classes de imagens que serão responsivas.

<pre class="lang-javascript">$(document).ready(function(){
  $(".hisrc img").hisrc();
  $(".hisrc img+img").hisrc({
  useTransparentGif: true,
  speedTestUri: '50K.jpg'
});
})</pre>

Depois utilize as suas imagens em uma div com a mesma classe. A primeira imagem é a mobile (first, lembra?), a com o atributo data-1x é para conexões rápidas de definição normal e com data-2x é para imagens com o dobro da densidade de pixels (para telas como retina display da Apple, por exemplo).

<pre class="lang-html">&lt;div class="hisrc"&gt;
  &lt;img src="imagem.jpg" data-1x="imagem@1x.jpg" data-2x="imagem@2x.jpg"&gt;
&lt;/div&gt;</pre>

Simples e prático de implementar de maneira dinâmica. Como pontos contra além do download duplo, temos a dependência do jQuery e impossibilidade de direção de arte pois não existe controle nenhum do tamanho do viewport ou de media queries (afinal tudo é determinado a partir da velocidade da internet).

Se você se interessou confira a documentação completa no [GitHub do projeto][10].

## A Solução server side (com Adaptive Images)

Se você tem um zillhão de linhas de código para readaptar pode não ser nada prático revisar imagem por imagem para adicionar atributos extras. Ou talvez você tenha um cliente que vai administrar sozinho um website sem possuir um designer na equipe para cropar e otimizar todas as versões possíveis de imagens responsivas. Em ambos os casos uma solução server side pode ser mais interessante.

Para estes casos eu indicaria o Adaptive Images. Ele basicamente intercepta os pedidos por imagens no servidor e redimensiona automaticamente as imagens para os breakpoints que você especificou. Além do zero de trabalho extra uma vez que o setup for feito, a solução é bem semântica e não requer marcação extra.

O contra? Você vai precisar de PHP 5x (com Apache2 / nginx e GD lib), já que o processo é realizado a partir do arquivo .htacess. Este arquivo basicamente diz para o servidor dar uma olhadinha no adaptive-images.php antes de pegar qualquer imagem jpg, gif ou png. Ou seja, se você estiver utilizando alguma outra linguagem como Ruby on Rails ou ASP é melhor buscar outro caminho. Também não é possível fazer direção de arte pois o arquivo é simplesmente redimensionado. Se estes pontos não forem um problema esta é uma solução prática, rápida e efetiva. Outra questão que pode ser vista como um &#8220;defeito&#8221; é, como o adaptative images verifica o viewport através de cookies + cache, as imagens não vão ser servidas se um usuário ficar brincando de aumentar e diminuir a janelinha do browser. Mas acredito que isto pode ser contornado pelo bom e velho max-width 100% como um fallback.

Para documentação e dicas de implementação dê uma olhada no [site do projeto][11] e no [GitHub][12].

## O caminho do WordPress (com múltiplos plugins)

Se você utiliza o CMS WordPress em seus projetos pode estar com sorte. Como a ferramenta já lida com uma biblioteca de mídia e versões de tamanhos diferentes para imagens existem diversos plugins que facilitam o trabalho de desenvolvimento para a plataforma.

[Mobble][13]
  
Funções condicionais para detectar smartphones e tablets.

[Picturefill WP][14]
  
Baseado no picturefill.js

[Simple responsive images][15]
  
Redimensiona as imagens para os breakpoints que você escolher.

[PB Responsive Images][16]
  
Baseado na tag picture

## A lista de alternativas

Encontrar uma solução definitiva para a performance de imagens tem sido uma verdadeira caça ao tesouro do design responsivo. Fora as ferramentas que eu já apresentei existem diversas outras iniciativas bacanas bacanas que valem a visita.

[Sencha.IO][17]
  
Solução third-party que funciona como um proxy para imagens responsivas. Possui planos pagos e gratuitos.

[Interchange][18]
  
Desenvolvido pela Zurb e integrado ao frameworkd Foundation.

[ReSRC][19]
  
Solução de proxy com algumas outras funções interessantes extras como filtros, crop, integração com sliders e plugins. É cobrada uma mensalidade nos planos avançados.

[Riloadr][20]
  
Framework de imagens responsivas baseado apenas em HTML, CSS e JavaScript.

Se você ainda está um pouco perdido [esta tabela][21] criada pelos desenvolvedores Chris Coyier e Christopher Schmitt compara algumas das soluções mencionadas neste artigo em critérios como dependência de JavaScript, validação, download de imagens adicionais, direção de arte, etc.

Conhece alguma outra ferramenta legal? Deixe a referência nos comentários que eu atualizarei esta lista sempre que possível.

### Saiba mais

 [Choosing a responsive image solution][22]
  
[Which responsive images solution should you use][23]
  
[Responsive images right now][24]

 [1]: http://www.w3.org/TR/html-picture-element/ "W3C - HTML picture element"
 [2]: http://responsiveimages.org/ "ResponsiveImages.org"
 [3]: http://picture.responsiveimages.org/ "ResonsiveImages"
 [4]: https://github.com/ResponsiveImagesCG/picture-element "GithHub - ResponsiveImages"
 [5]: http://scottjehl.github.io/picturefill/ "Picturefill"
 [6]: https://github.com/scottjehl/picturefill "GitHub - Picturefill"
 [7]: http://www.cdnconnect.com/docs/foresightjs "Foresight.js"
 [8]: https://github.com/adamdbradley/foresight.js "GitHub - Foresight"
 [9]: http://www.cdnconnect.com/docs/foresightjs/demos "Foresight - Demos"
 [10]: https://github.com/teleject/hisrc "GitHub - HiSRC"
 [11]: http://adaptive-images.com/ "Adaptive Images"
 [12]: https://github.com/MattWilcox/Adaptive-Images "Adaptive Images - GitHub"
 [13]: http://wordpress.org/plugins/mobble/ "Mobble"
 [14]: http://wordpress.org/plugins/picturefillwp/ "Picturefill WP"
 [15]: http://wordpress.org/plugins/simple-responsive-images/ "Simple responsive images"
 [16]: http://wordpress.org/plugins/pb-responsive-images/ "PB Responsive Images"
 [17]: http://www.sencha.com/products/space/ "Sencha.io"
 [18]: http://zurb.com/playground/foundation-interchange "Interchange"
 [19]: http://www.resrc.it/ "ReSRC"
 [20]: https://github.com/tubalmartin/riloadr "Riloadr"
 [21]: https://docs.google.com/spreadsheet/ccc?key=0Al0lI17fOl9DdDgxTFVoRzFpV3VCdHk2NTBmdVI2OXc#gid=0
 [22]: http://mobile.smashingmagazine.com/2013/07/08/choosing-a-responsive-image-solution/ "Choosing a responsive image solution"
 [23]: http://css-tricks.com/which-responsive-images-solution-should-you-use/ "Which responsive images solution should you use"
 [24]: http://csswizardry.com/2011/07/responsive-images-right-now/ "Responsive images right now"