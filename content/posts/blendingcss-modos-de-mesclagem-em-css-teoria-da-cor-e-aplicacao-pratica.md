---
title: '#BlendingCSS – Modos de mesclagem em CSS: Teoria da Cor e Aplicação Prática'
author: Moisés Lopes Ferreira
type: post
date: 2016-11-01
url: /blendingcss-modos-de-mesclagem-em-css-teoria-da-cor-e-aplicacao-pratica/
titulo_personalizado:
  - 'Modos de mesclagem <strong>em CSS</strong>'
categories:
  - CSS
  - CSS3
tags:
  - blending modes
  - CSS
  - mesclagem de camadas

---
OBS:. o método abordado sobre Blending (mesclagem de cores e camadas) não é igual, mas não diferente do método abordado pela nossa colega [Dani Guerrato][1] no post [Modos de Mesclagem em CSS – Blend Mode CSS][2]

Diga-se de passagem nós abordaremos visões abrangentes e características técnicas do método de aplicação de Blending no CSS, mas se você quer dar uma previa nos conceitos de background css antes de ler esse post seria legal: [OBS:. o método abordado sobre Blending (mesclagem de cores e camadas) não é igual, mas não diferente do método abordado pela nossa colega [Dani Guerrato][1] no post [Modos de Mesclagem em CSS – Blend Mode CSS][2]

Diga-se de passagem nós abordaremos visões abrangentes e características técnicas do método de aplicação de Blending no CSS, mas se você quer dar uma previa nos conceitos de background css antes de ler esse post seria legal:][3] (tem imagens bem legais)

Ok, dados os avisos bora para o código!

Se você usa Photoshop pode estar familiarizado com o &#8220;Blending&#8221; (modos de mesclagem de camadas). 

Eles nós permitem que você combinar &#8220;camadas&#8221; ( ou layers ) de formas diferentes e eles são muito divertido para brincar. O Blending CSS (_modos de mistura em CSS_), no entanto,  infelizmente ainda não são suportados universalmente, mas logo estarão certamente no seu caminho.

Neste tutorial, vamos aprender como trabalhar com as diferentes maneiras que você pode implementar Blending CSS (modos de mistura) usados CSS.

## As noções básicas de Blending CSS

Se você nunca usou este recurso no Photoshop ou nunca ouviu falar dele, vamos te mostrar como Blending (modos de mistura), e suas formas e Formulas funcionam&#8230;  pode parecer um pouco confuso mas vamos dividi-lás em partes visuais para compreendermos melhor.

### O que realmente significa &#8220;Blending&#8221;?

Modos de Mesclagem (&#8220;Blending&#8221;) estão disponíveis no software de desenho já faz alguns anos, mas o conceito de Blending (&#8220;modos de mistura&#8221;) tem sido realmente usados por muito mais tempo, mesmo antes dos computadores fossem inventados.

O Blending é parte dos _modos de mesclagem,_ que refere-se a pegar duas cores e combiná-los de uma forma para fazer uma cor só. Mais precisamente, pegamos dois mapas pixel e misturámos eles juntos

É como um &#8220;Juicer&#8221; &#8211; centrifugas de suco, onde você coloca duas frutas de distintas cores numa ponta e tem um colorido suco misturado do outro lado da máquina.
  
<img class="size-full wp-image-56095 aligncenter" src="http://tableless.com.br/uploads/2016/10/Blender-Juicer-Vegetables-Fruits-Drink-777x437.jpg" alt="Blender-Juicer-Vegetables-Fruits-Drink-777x437" width="777" height="437" />

&nbsp;

_Como_ que a mistura ocorre é a parte &#8220;modo&#8221; de _modos_ de _mesclagem._ Como é que essas cores interagem? Porque estamos a trabalhar com o espaço digital, podemos tomar qualquer fórmula matemática e aplicá-lo às duas entradas para derivar uma saída.

&nbsp;<figure class="post_image"> 

<div style="width: 610px" class="wp-caption aligncenter">
  <img src="https://cms-assets.tutsplus.com/uploads/users/30/posts/25201/image/none.jpg" alt="Uma imagem não tratada de uma medusa" width="600" height="300" />
  
  <p class="wp-caption-text">
    Uma imagem não tratada de uma medusa
  </p>
</div></figure> <figure class="post_image"> 

<div style="width: 610px" class="wp-caption aligncenter">
  <img src="https://cms-assets.tutsplus.com/uploads/users/30/posts/25201/image/orange.jpg" alt=" A mesma água-viva com uma camada de laranja sólido (a &quot;fonte&quot;) colocado sobre ele" width="600" height="300" />
  
  <p class="wp-caption-text">
    A mesma água-viva com uma camada de laranja sólido (a &#8220;origem de mesclagem&#8221;) colocado sobre ele
  </p>
</div>

<img class="aligncenter" src="https://cms-assets.tutsplus.com/uploads/users/30/posts/25201/image/screen.jpg" alt=" Aqui está a nossa camada de origem com a &quot;tela&quot; modo de mesclagem aplicado" width="600" height="300" />Aqui está a nossa camada de origem de mesclagem com a &#8220;tela&#8221; com o Blending aplicado
  
</figure> 

### Você faz a matemática

Se você está se sentindo _realmente_ ambicioso, dê uma olhada através Task Force FX da W3C do <a href="https://translate.googleusercontent.com/translate_c?depth=1&hl=pt-BR&ie=UTF8&prev=_t&rurl=translate.google.com.br&sl=en&tl=pt-BR&u=https://drafts.fxtf.org/compositing/&usg=ALkJrhgP7Nj2SjD6ndaobz9HMCmWHLI_xg#blending" target="_self">documento de composição oficial</a> que explica as implementações matemáticas de cada um dos diferentes modos de blending. Demonstra uma fórmula usada para calcular mais modos de mesclagem .

<pre class="lang-javascript">Cm = B (Cb, Cs)</pre>

  * Aqui, `Cm` é a cor resultante após a mistura.
  * `B` refere-se à função de mistura.
  * O `Cb` variável é a cor de fundo.
  * E o `Cs` variável é a cor de origem.

[Todas as cores são baseados numa escala de 0-1, que mapeia diretamente para um valor 0-255 RGB.][4]

<img class="size-full wp-image-56099 aligncenter" src="http://tableless.com.br/uploads/2016/10/nee-nees-096-min-compressor.jpg" alt="nee-nees-096-min-compressor" width="3888" height="2592" />

Existem duas categorias de modos de Blending: não-separáveis e os separáveis.

Se um blending é considerada separável, ou não é determinado pelo algoritmo subjacente. Se o algoritmo trata cada um dos canais de cor separados (vermelho, verde e azul // RGB) de igual modo, considera-se inseparáveis. Se ele usa cada um dos canais de cor, individualmente, considera-se separável.

Todos os modos de mistura só pode voltar cores que estão dentro da gama de 0 a 255. Qualquer coisa para além desta gama em qualquer direção irá ser cortada para o intervalo. Quando você vê grandes áreas de branco ou preto em uma área mista, é provável porque essas áreas estão sendo cortadas.

## Tipos de modos de mesclagem Disponível em CSS

Blending CSS, onde são suportados, trabalha de duas maneiras diferentes. O primeiro tipo de modo de mistura é chamada `background-blend-mode` . Esta propriedade permite que você misturar todos os fundos dentro de um elemento com o outro.

Se você tiver definido, por exemplo, múltiplas imagens de fundo (<a href="https://translate.googleusercontent.com/translate_c?depth=1&hl=pt-BR&ie=UTF8&prev=_t&rurl=translate.google.com.br&sl=en&tl=pt-BR&u=http://caniuse.com/&usg=ALkJrhgJSpRt8OnTYOP3TYJm2Gf1tC3M-A#feat=multibackgrounds" target="_self">suportados em todos os navegadores além do IE8</a>), a primeira imagem de fundo será tratada como a camada de origem, e qualquer imagem adicionada posteriormente será tratada como a camada de fundo, encontrando-se por baixo.

Adicionando uma cor de fundo (que deve ser o último da lista) coloca mais uma camada na parte inferior. A cor será tratada como a camada de fundo, e as imagens como as camadas de origem. Veja o seguinte na regra de estilo, por exemplo:

<pre class="lang-css">div {
  background:
  url(img/pattern.png),
  url(img/jellyfish.jpg), 
  #f07e32;
}</pre>

Isso nos dá:<figure class="post_image">

<img class="aligncenter" src="https://cms-assets.tutsplus.com/uploads/users/30/posts/25201/image/multiple-backgrounds.jpg" alt="" /></figure> 

E nós pode então adicionar modos de Blending:

<pre class="lang-css">div {
  background:
  url(img/pattern.png),
  url(img/jellyfish.jpg), 
  #f07e32 ;
  background-blend-mode: screen;
}
</pre>

Aqui estão dois divs usando esses estilos, um sem o modo de mesclagem, o segundo com:

A mistura tipo de modo secundário, `mix-blend-mode` , permite elementos independentes a serem misturados. A especificação é mais específica sobre a implementação, mas a mistura ocorre em &#8220;contextos de empilhamento&#8221;.

Isto é o que acontece quando usamos `mix-blend-mode` , na tentativa de obter a imagem de fundo e cor dentro do mesmo elemento para misturar (uma sintaxe de código um pouco mais limpa):

<pre class="lang-css">.my-overlay-element {
  background-color: #f07e32;
  background-image: url(img/jellyfish.jpg); // Note: This image will not be blended with the background color.
  mix-blend-mode: color-dodge;
}
</pre>

Abaixo, você pode encontrar uma <a href="https://translate.googleusercontent.com/translate_c?depth=1&hl=pt-BR&ie=UTF8&prev=_t&rurl=translate.google.com.br&sl=en&tl=pt-BR&u=http://codepen.io/tutsplus/live/wMvoyj&usg=ALkJrhiUNiZymZ8tkzwi_FO6w2rqQj4-6g" target="_self">demonstração interativa</a> para explorar os efeitos de um determinado modo de mistura.

## Blend Modes separáveis

Vamos dar uma olhada nos modos de mesclagem (&#8220;Blending&#8221;) disponíveis, examinando a fórmula utilizada, e aplicando cada um para o círculo vermelho colocado acima da nossa água-viva.<figure class="post_image">

![][5]<figcaption> </figcaption></figure> 

#### Screen (tela): 

`B(Cb, Cs) = 1 - [(1 - Cb) x (1 - Cs)]`

Screen (ou tela) é nomeado após o conceito de projetar múltiplas exposições de fotografias, ao mesmo tempo em uma tela. A cor resultante é sempre pelo menos tão leve quanto uma das camadas combinadas.<figure class="post_image"> 

<div style="width: 610px" class="wp-caption aligncenter">
  <img src="https://cms-assets.tutsplus.com/uploads/users/30/posts/25201/image/j2.jpg" alt="o modo de blend da tela" width="600" height="300" />
  
  <p class="wp-caption-text">
    o modo de blend da tela
  </p>
</div></figure> 

#### Darken: 

`B(Cb, Cs) = min(Cb, Cs)`

Seleciona a mais escura das duas cores.<figure class="post_image"> 

<div style="width: 610px" class="wp-caption aligncenter">
  <img src="https://cms-assets.tutsplus.com/uploads/users/30/posts/25201/image/j-darken.jpg" alt="Darken Mode Blending" width="600" height="300" />
  
  <p class="wp-caption-text">
    Darken Mode Blending
  </p>
</div></figure> 

Lighten: `B(Cb, Cs) = max(Cb, Cs)`

Seleciona a mais clara das duas cores.<figure class="post_image"> 

<div style="width: 610px" class="wp-caption aligncenter">
  <img src="https://cms-assets.tutsplus.com/uploads/users/30/posts/25201/image/j-lighten.jpg" alt="Lighten blend mode" width="600" height="300" />
  
  <p class="wp-caption-text">
    Lighten blend mode
  </p>
</div></figure> 

#### Color Dodge:

<pre class="lang-js">if(Cb == 0)
    B(Cb, Cs) = 0
else if(Cs == 1)
    B(Cb, Cs) = 1
else
    B(Cb, Cs) = min(1, Cb / (1 - Cs))

</pre>

Color Dodge clareia a cor de fundo para refletir a cor de origem.<figure class="post_image"> 

<div style="width: 610px" class="wp-caption aligncenter">
  <img src="https://cms-assets.tutsplus.com/uploads/users/30/posts/25201/image/j-color-dodge.jpg" alt="blend mode Color Dodge" width="600" height="300" />
  
  <p class="wp-caption-text">
    blend mode Color Dodge
  </p>
</div><figcaption></figcaption></figure> 

#### Color Burn (cor queimada):

<pre class="lang-js">if(Cb == 1)
    B(Cb, Cs) = 1
else if(Cs == 0)
    B(Cb, Cs) = 0
else
    B(Cb, Cs) = 1 - min(1, (1 - Cb) / Cs)
</pre>

O Color Burn escurece a cor de fundo, aumentando o contraste entre a fonte e o fundo.<figure class="post_image"> 

<div style="width: 610px" class="wp-caption aligncenter">
  <img src="https://cms-assets.tutsplus.com/uploads/users/30/posts/25201/image/j-burn.jpg" alt="Modo de queimadura mistura Cor" width="600" height="300" />
  
  <p class="wp-caption-text">
    Color burn blend mode
  </p>
</div></figure> 

#### Hard light:

<pre class="lang-js">if(Cs &lt;= 0.5)
    B(Cb, Cs) = Multiply(Cb, 2 x Cs)
else
    B(Cb, Cs) = Screen(Cb, 2 x Cs -1)
</pre>

Aplica-se "multiply" em cores mais claras e "screen" em cores mais escuras. Essencialmente, "Hard light" é o oposto de "overlay", é que veremos a seguir.<figure class="post_image"> 

<div style="width: 610px" class="wp-caption aligncenter">
  <img src="https://cms-assets.tutsplus.com/uploads/users/30/posts/25201/image/j-hardl.jpg" alt="blend mode luz dura" width="600" height="300" />
  
  <p class="wp-caption-text">
    Hard light blend mode
  </p>
</div><figcaption></figcaption></figure> 

#### Overlay:

<div>
  <div id="highlighter_843579" class="syntaxhighlighter noskimlinks noskimwords bash">
    <table border="0" cellspacing="0" cellpadding="0">
      <tr>
        <td class="gutter">
          <div class="line number1 index0 alt2">
            1
          </div>
        </td>
        
        <td class="code">
          <div class="container">
            <div class="line number1 index0 alt2">
              <code>B(Cb, Cs) = HardLight(Cs, Cb)</code>
            </div>
          </div>
        </td>
      </tr>
    </table>
  </div>
</div>

Aplica-se "screen" em cores mais claras e "multiply" em cores mais escuras; escrito como o mesmo que "Hard light", exceto com os argumentos para a função inversa.<figure class="post_image"> 

<div style="width: 610px" class="wp-caption aligncenter">
  <img src="https://cms-assets.tutsplus.com/uploads/users/30/posts/25201/image/j-overlay.jpg" alt="modo de blend Overlay" width="600" height="300" />
  
  <p class="wp-caption-text">
    Overlay blend mode
  </p>
</div></figure> 

#### Soft Light:

<div>
  <div id="highlighter_522850" class="syntaxhighlighter noskimlinks noskimwords bash">
    <table border="0" cellspacing="0" cellpadding="0">
      <tr>
        <td class="gutter">
          <div class="line number1 index0 alt2">
            1
          </div>
          
          <div class="line number2 index1 alt1">
            2
          </div>
          
          <div class="line number3 index2 alt2">
            3
          </div>
          
          <div class="line number4 index3 alt1">
            4
          </div>
          
          <div class="line number5 index4 alt2">
            5
          </div>
          
          <div class="line number6 index5 alt1">
            6
          </div>
          
          <div class="line number7 index6 alt2">
            7
          </div>
          
          <div class="line number8 index7 alt1">
            8
          </div>
          
          <div class="line number9 index8 alt2">
            9
          </div>
        </td>
        
        <td class="code">
          <div class="container">
            <div class="line number1 index0 alt2">
              <code>if</code><code>(Cs &lt;= 0.5)</code>
            </div>
            
            <div class="line number2 index1 alt1">
              <code>        </code><code>B(Cb, Cs) = Cb - (1 - 2 x Cs) x Cb x (1 - Cb)</code>
            </div>
            
            <div class="line number3 index2 alt2">
              <code>    </code><code>else</code>
            </div>
            
            <div class="line number4 index3 alt1">
              <code>        </code><code>B(Cb, Cs) = Cb + (2 x Cs - 1) x (D(Cb) - Cb)</code>
            </div>
            
            <div class="line number5 index4 alt2">
              <code>with</code>
            </div>
            
            <div class="line number6 index5 alt1">
              <code>    </code><code>if</code><code>(Cb &lt;= 0.25)</code>
            </div>
            
            <div class="line number7 index6 alt2">
              <code>        </code><code>D(Cb) = ((16 * Cb - 12) x Cb + 4) x Cb</code>
            </div>
            
            <div class="line number8 index7 alt1">
              <code>    </code><code>else</code>
            </div>
            
            <div class="line number9 index8 alt2">
              <code>        </code><code>D(Cb) = sqrt(Cb)</code>
            </div>
          </div>
        </td>
      </tr>
    </table>
  </div>
</div>

Este modo de Blending aplica-se uma variante de "multiply" em valores escuros e uma variante da "screen" em valores mais leves (similar à screen).

Neste algoritmo, vemos uma função secundária `D` , que está situado no `with` cláusula com base no valor atual do azul (_**<span style="color: #ff0000">R-<span style="color: #00ff00">G-<span style="color: #0000ff">B</strong></em>) na cor. O resultado final é tipicamente um efeito muito mais suave do que "overlay".</p> <figure class="post_image"> 

<div style="width: 610px" class="wp-caption aligncenter">
  <img src="https://cms-assets.tutsplus.com/uploads/users/30/posts/25201/image/j-soft.jpg" alt="blend mode luz Sof" width="600" height="300" />
  
  <p class="wp-caption-text">
    Sof light blend mode
  </p>
</div></figure> 

<h4>
  Difference:
</h4>

<div>
  <div id="highlighter_841255" class="syntaxhighlighter noskimlinks noskimwords bash">
    <table border="0" cellspacing="0" cellpadding="0">
      <tr>
        <td class="gutter">
          <div class="line number1 index0 alt2">
            1
          </div>
        </td>
        
        <td class="code">
          <div class="container">
            <div class="line number1 index0 alt2">
              <code>B(Cb, Cs) = | Cb - Cs |</code>
            </div>
          </div>
        </td>
      </tr>
    </table>
  </div>
</div>

<p>
  Diferença pega o valor absoluto da diferença entre as duas cores, que tem o mesmo efeito de um negativo fotográfico.
</p><figure class="post_image"> 

<p>
  <div style="width: 610px" class="wp-caption aligncenter">
    <img src="https://cms-assets.tutsplus.com/uploads/users/30/posts/25201/image/j-difference.jpg" alt="blend mode diferença" width="600" height="300" />
    
    <p class="wp-caption-text">
      Difference blend mode
    </p>
  </div><figcaption></figcaption></figure> 
  
  <h4>
    Exclusion:
  </h4>
  
  <div>
    <div id="highlighter_276376" class="syntaxhighlighter noskimlinks noskimwords bash">
      <table border="0" cellspacing="0" cellpadding="0">
        <tr>
          <td class="gutter">
            <div class="line number1 index0 alt2">
              1
            </div>
          </td>
          
          <td class="code">
            <div class="container">
              <div class="line number1 index0 alt2">
                <code>B(Cb, Cs) = Cb + Cs - 2 x Cb x Cs</code>
              </div>
            </div>
          </td>
        </tr>
      </table>
    </div>
  </div>
  
  <p>
    O modo de exclusão tem o mesmo efeito de base como o modo "diferença", excepto que as cores semelhantes resultar num valor mais baixo do meio de contraste (ao invés de um valor mais escuro).
  </p><figure class="post_image"> 
  
  <div style="width: 610px" class="wp-caption aligncenter">
    <img src="https://cms-assets.tutsplus.com/uploads/users/30/posts/25201/image/j-exclusion.jpg" alt="blend mode Exclusão" width="600" height="300" />
    
    <p class="wp-caption-text">
      Exclusion blend mode
    </p>
  </div></figure> 
  
  <h2>
    Blend Modes não-separáveis
  </h2>
  
  <p>
    Os Blend Modes "não-separáveis" são modos de mesclagem utilizam algumas funções extras, incluindo as funções <code>ClipColor</code>, <code>SetLum</code>, e <code>Sat</code>.
  </p>
  
  <p>
    <b>Nota importante:</b> Nenhuma versão do Safari suporta blend modes "hue", "saturation", "color", ou "luminosity"  com <code>mix-blend-mode</code> ou <code>background-blend-mode</code> .
  </p>
  
  <div>
    <div id="highlighter_312047" class="syntaxhighlighter noskimlinks noskimwords bash">
      <table border="0" cellspacing="0" cellpadding="0">
        <tr>
          <td class="gutter">
            <div class="line number1 index0 alt2">
              01
            </div>
            
            <div class="line number2 index1 alt1">
              02
            </div>
            
            <div class="line number3 index2 alt2">
              03
            </div>
            
            <div class="line number4 index3 alt1">
              04
            </div>
            
            <div class="line number5 index4 alt2">
              05
            </div>
            
            <div class="line number6 index5 alt1">
              06
            </div>
            
            <div class="line number7 index6 alt2">
              07
            </div>
            
            <div class="line number8 index7 alt1">
              08
            </div>
            
            <div class="line number9 index8 alt2">
              09
            </div>
            
            <div class="line number10 index9 alt1">
              10
            </div>
            
            <div class="line number11 index10 alt2">
              11
            </div>
            
            <div class="line number12 index11 alt1">
              12
            </div>
            
            <div class="line number13 index12 alt2">
              13
            </div>
            
            <div class="line number14 index13 alt1">
              14
            </div>
            
            <div class="line number15 index14 alt2">
              15
            </div>
            
            <div class="line number16 index15 alt1">
              16
            </div>
            
            <div class="line number17 index16 alt2">
              17
            </div>
            
            <div class="line number18 index17 alt1">
              18
            </div>
            
            <div class="line number19 index18 alt2">
              19
            </div>
            
            <div class="line number20 index19 alt1">
              20
            </div>
            
            <div class="line number21 index20 alt2">
              21
            </div>
            
            <div class="line number22 index21 alt1">
              22
            </div>
            
            <div class="line number23 index22 alt2">
              23
            </div>
            
            <div class="line number24 index23 alt1">
              24
            </div>
            
            <div class="line number25 index24 alt2">
              25
            </div>
            
            <div class="line number26 index25 alt1">
              26
            </div>
            
            <div class="line number27 index26 alt2">
              27
            </div>
          </td>
          
          <td class="code">
            <div class="container">
              <div class="line number1 index0 alt2">
                <code>ClipColor(C)</code>
              </div>
              
              <div class="line number2 index1 alt1">
                <code>  </code><code>l = Lum(C)</code>
              </div>
              
              <div class="line number3 index2 alt2">
                <code>  </code><code>n = min(Cred, Cgreen, Cblue)</code>
              </div>
              
              <div class="line number4 index3 alt1">
                <code>  </code><code>x = max(Cred, Cgreen, Cblue)</code>
              </div>
              
              <div class="line number5 index4 alt2">
              </div>
              
              <div class="line number6 index5 alt1">
                <code>  </code><code>if</code> <code>n &lt; 0.0</code>
              </div>
              
              <div class="line number7 index6 alt2">
                <code>    </code><code>Cred = l + (((Cred - l) * l) / (l - n))</code>
              </div>
              
              <div class="line number8 index7 alt1">
                <code>    </code><code>Cgreen = l + (((Cgreen - l) * l) / (l - n))</code>
              </div>
              
              <div class="line number9 index8 alt2">
                <code>    </code><code>Cblue = l + (((Cblue - l) * l) / (l - n))</code>
              </div>
              
              <div class="line number10 index9 alt1">
              </div>
              
              <div class="line number11 index10 alt2">
                <code>  </code><code>if</code> <code>x &gt; 1.0</code>
              </div>
              
              <div class="line number12 index11 alt1">
              </div>
              
              <div class="line number13 index12 alt2">
                <code>    </code><code>Cred = l + (((Cred - l) * (1 - l)) / (x - l))</code>
              </div>
              
              <div class="line number14 index13 alt1">
                <code>    </code><code>Cgreen = l + (((Cgreen - l) * (1 - l)) / (x - l))</code>
              </div>
              
              <div class="line number15 index14 alt2">
                <code>    </code><code>Cblue = l + (((Cblue - l) * (1 - l)) / (x - l))</code>
              </div>
              
              <div class="line number16 index15 alt1">
              </div>
              
              <div class="line number17 index16 alt2">
                <code>  </code><code>return</code> <code>C</code>
              </div>
              
              <div class="line number18 index17 alt1">
              </div>
              
              <div class="line number19 index18 alt2">
                <code>SetLum(C, l)</code>
              </div>
              
              <div class="line number20 index19 alt1">
                <code>  </code><code>d = l - Lum(C)</code>
              </div>
              
              <div class="line number21 index20 alt2">
                <code>  </code><code>Cred = Cred + d</code>
              </div>
              
              <div class="line number22 index21 alt1">
                <code>  </code><code>Cgreen = Cgreen + d</code>
              </div>
              
              <div class="line number23 index22 alt2">
                <code>  </code><code>Cblue = Cblue + d</code>
              </div>
              
              <div class="line number24 index23 alt1">
              </div>
              
              <div class="line number25 index24 alt2">
                <code>  </code><code>return</code> <code>ClipColor(C)</code>
              </div>
              
              <div class="line number26 index25 alt1">
              </div>
              
              <div class="line number27 index26 alt2">
                <code>Sat(C) = max(Cred, Cgreen, Cblue) - min(Cred, Cgreen, Cblue)</code>
              </div>
            </div>
          </td>
        </tr>
      </table>
    </div>
  </div>
  
  <p>
    Observe o <code>min</code> , <code>mid</code> e <code>max</code> são funções de utilitária que consulta a valores máximos, médios e mínimos. (<em>Mid <strong>não </strong></em>é a média dos três valores.) Os valores <code>Cred</code> , <code>Cgreen</code> , e <code>Cblue</code> referem-se a valores de vermelho, verde e azul das cores presentes na <code>C</code> .
  </p>
  
  <p>
    Com estas definições alinhadas, podemos agora olhar para os blend modes não-separáveis.
  </p>
  
  <h4>
    <b>Hue</b> (<b>Matiz):</b>
  </h4>
  
  <div>
    <div id="highlighter_803107" class="syntaxhighlighter noskimlinks noskimwords bash">
      <table border="0" cellspacing="0" cellpadding="0">
        <tr>
          <td class="gutter">
            <div class="line number1 index0 alt2">
              1
            </div>
          </td>
          
          <td class="code">
            <div class="container">
              <div class="line number1 index0 alt2">
                <code>B(Cb, Cs) = SetLum(SetSat(Cs, Sat(Cb)), Lum(Cb))</code>
              </div>
            </div>
          </td>
        </tr>
      </table>
    </div>
  </div>
  
  <p>
    Este modo aplica-se a tonalidade da camada de fonte para a luminância e saturação da cor de fundo.
  </p><figure class="post_image"> 
  
  <div style="width: 610px" class="wp-caption aligncenter">
    <img src="https://cms-assets.tutsplus.com/uploads/users/30/posts/25201/image/j-hue.jpg" alt="blend mode Hue" width="600" height="300" />
    
    <p class="wp-caption-text">
      blend mode Hue
    </p>
  </div></figure> 
  
  <h4>
    Saturation (Saturação):
  </h4>
  
  <div>
    <div id="highlighter_173459" class="syntaxhighlighter noskimlinks noskimwords bash">
      <table border="0" cellspacing="0" cellpadding="0">
        <tr>
          <td class="gutter">
            <div class="line number1 index0 alt2">
              1
            </div>
          </td>
          
          <td class="code">
            <div class="container">
              <div class="line number1 index0 alt2">
                <code>B(Cb, Cs) = SetLum(SetSat(Cb, Sat(Cs)), Lum(Cb))</code>
              </div>
            </div>
          </td>
        </tr>
      </table>
    </div>
  </div>
  
  <p>
    Este modo faz a mesma coisa como o modo "hue", mas em vez disso se aplica a saturação do primeiro plano para a tonalidade e a luminância de fundo.
  </p><figure class="post_image"> 
  
  <div style="width: 610px" class="wp-caption aligncenter">
    <img src="https://cms-assets.tutsplus.com/uploads/users/30/posts/25201/image/j-sat.jpg" alt="modo de mistura de saturação" width="600" height="300" />
    
    <p class="wp-caption-text">
      Saturation blend mode
    </p>
  </div></figure> 
  
  <h4>
    Color (cor):
  </h4>
  
  <div>
    <div id="highlighter_88781" class="syntaxhighlighter noskimlinks noskimwords bash">
      <table border="0" cellspacing="0" cellpadding="0">
        <tr>
          <td class="gutter">
            <div class="line number1 index0 alt2">
              1
            </div>
          </td>
          
          <td class="code">
            <div class="container">
              <div class="line number1 index0 alt2">
                <code>B(Cb, Cs) = SetLum(Cs, Lum(Cb))</code>
              </div>
            </div>
          </td>
        </tr>
      </table>
    </div>
  </div>
  
  <p>
    Aplica-se o hue (matiz) e a saturação do primeiro plano para a luminância de fundo.
  </p><figure class="post_image"> 
  
  <div style="width: 610px" class="wp-caption aligncenter">
    <img src="https://cms-assets.tutsplus.com/uploads/users/30/posts/25201/image/j-color.jpg" alt="modo de mistura de cores" width="600" height="300" />
    
    <p class="wp-caption-text">
      Color blend mode
    </p>
  </div></figure> 
  
  <h4>
    Luminosity (Luminosidade):
  </h4>
  
  <div>
    <div id="highlighter_88781" class="syntaxhighlighter noskimlinks noskimwords bash">
      <table border="0" cellspacing="0" cellpadding="0">
        <tr>
          <td class="gutter">
            <div class="line number1 index0 alt2">
              1
            </div>
          </td>
          
          <td class="code">
            <div class="container">
              <div class="line number1 index0 alt2">
                <code>B(Cb, Cs) = SetLum(Cs, Lum(Cb))</code>
              </div>
            </div>
          </td>
        </tr>
      </table>
    </div>
  </div>
  
  <p>
    Este modo aplica-se a luminosidade da camada de origem com o hue (matiz) e a saturação da camada de fundo.
  </p><figure class="post_image"> 
  
  <p>
    <div style="width: 610px" class="wp-caption aligncenter">
      <img src="https://cms-assets.tutsplus.com/uploads/users/30/posts/25201/image/j-last.jpg" alt="blend mode Luminosidade" width="600" height="300" />
      
      <p class="wp-caption-text">
        Luminosity blend mode
      </p>
    </div><figcaption></figcaption></figure> 
    
    <div class="post-body view view--loaded">
      <div class="post-body__body">
        <div class="post-body__content">
          <h2>
            Conclusão
          </h2>
          
          <p>
            Modos de mistura  ("Blending Mode") em CSS fornece um nova e excitante flexibilidade para a concepção e experiências estéticas singulares. Entender a matemática e a teoria da cor que se aplica a cada um dos modos de blending ("mesclagem") disponíveis fornece-lhe um conjunto de ferramentas mais holística.
          </p>
          
          <p>
            O que você vai fazer com os navegadores quando eles adicionarem suporte para modos de mistura?
          </p>
          
          <h3>
            Links Relacionados
          </h3>
          
          <ul>
            <li>
              Confira o que os autores estão fazendo com <a href="https://translate.googleusercontent.com/translate_c?depth=1&hl=pt-BR&ie=UTF8&prev=_t&rurl=translate.google.com.br&sl=en&tl=pt-BR&u=https://graphicriver.net/tags/blend&usg=ALkJrhjVwZaYbKYEuiA9KqnWHPkBBv5XWg" target="_self">Photoshop acções e modos de mistura</a> ao longo de Mercado Envato
            </li>
            <li>
              Leia mais sobre <a href="https://translate.googleusercontent.com/translate_c?depth=1&hl=pt-BR&ie=UTF8&prev=_t&rurl=translate.google.com.br&sl=en&tl=pt-BR&u=https://developer.mozilla.org/en/docs/Web/CSS/blend-mode&usg=ALkJrhhucd1JKzMcPZ9w-dM4ZfOQEige2g" target="_self"><misturar-mode></a> no Mozilla Developer Network
            </li>
            <li>
              <a href="https://translate.googleusercontent.com/translate_c?depth=1&hl=pt-BR&ie=UTF8&prev=_t&rurl=translate.google.com.br&sl=en&tl=pt-BR&u=http://sarasoueidan.com/blog/compositing-and-blending-in-css/&usg=ALkJrhhERbYPRMYL0iPGDgy0A-JLD1MCFQ" target="_self">Composição e mistura Em CSS</a> por Sara Soueidan
            </li>
          </ul>
        </div>
      </div>
    </div>
    
    <div class="ad ad--publift">
    </div>
    
    <h3 class="ad ad--publift">
      Texto traduzido
    </h3>
    
    <div class="content-author">
      <div class="content-author__header">
        <p>
          <img class="content-author__image alignleft" src="https://cms-assets.tutsplus.com/uploads/users/50/profiles/917/profileImage/av-cutrell.jpg" alt="Av cutrell" width="215" height="215" />
        </p>
        
        <pre class="content-author__name"><em>Jonathan Cutrell</em></pre>
        
        <p>
          <span id="result_box" class="" lang="pt"><em><span style="text-decoration: underline">Diretor de Tecnologia da Whiteboard e apresentador do desenvolvedor Tea</em></p> </div> 
          
          <div class="content-author__header">
          </div>
          
          <div class="content-author__header">
            <span id="result_box" class="" lang="pt">Eu sou o Director <span class="">de Tecnologia da <span class="">Whiteboard, uma empresa de interação digital <span class="">com sede em <span class="">Chattanooga, Tennessee. <span class="">Tenho um mestrado em Mídia Digital da <span class="">Georgia Tech. I <span class="">escrever, ensinar e <span class="">falar sobre o código e as coisas que ele pode fazer possível.</div> </div> 
            
            <div class="content-author__header">
            </div>
            
            <div class="content-author__header">
              <a href="https://webdesign.tutsplus.com/tutorials/blending-modes-in-css-color-theory-and-practical-application--cms-25201">Link Original do Post retirado do blog Tutsplus<br /> </a>
            </div>

 [1]: http://tableless.com.br/?author=14
 [2]: http://tableless.com.br/modos-de-mesclagem-em-css/
 [3]: http://tableless.com.br/css3%E2%80%8A-%E2%80%8Atrabalhando-com-multiplas-imagens-background-images/
 [4]: http://tableless.com.br/rgb-e-hsl/
 [5]: https://cms-assets.tutsplus.com/uploads/users/30/posts/25201/image/j1.jpg