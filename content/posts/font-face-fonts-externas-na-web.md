---
title: Propriedade @font-face CSS – Fonts externas na web
author: Diego Eis
type: post
date: 2010-03-30
excerpt: font-face possibilita utilizar fonts externas em websites. Você já pode utilizar essa regra agora.
url: /font-face-fonts-externas-na-web/
aktt_notify_twitter:
  - yes
tweetbackscheck:
  - 1356431818
shorturls:
  - 'a:3:{s:9:"permalink";s:55:"http://tableless.com.br/font-face-fonts-externas-na-web";s:7:"tinyurl";s:26:"http://tinyurl.com/3mnp6xu";s:4:"isgd";s:19:"http://is.gd/MQYurQ";}'
twittercomments:
  - 'a:2:{i:35040372405178368;s:6:"137018";i:48426092440190977;s:6:"137269";}'
tweetcount:
  - 2
dsq_thread_id: 503039406
categories:
  - CSS
  - Técnicas e Práticas
  - Tecnologia e Tendências
tags:
  - 2010
  - Browsers
  - CSS3
  - desenvolvimento
  - font
  - Na Prática
  - tecnicascss
  - tipografia
  - tutorial

---
Tipografia na web sempre foi um sonho para todo designer. Alguns designers que trabalharam durante muito tempo com impressão se sentem presos com web por conta da limitação de escolha das fonts. A tipografia é parte importante na criação de peças gráficas e na web isso não poderia ser diferente. Mesmo assim, não havia uma maneira &#8216;inteligente&#8217; de utilizar uma **fonts que não seja padrão do sistema** operacional do usuário na criação de layouts para web. Iniciativas como [TypeKit][1]e [Sifr][2] quebram o galho mas não são o ideal.

A **regra do CSS chamada @font-face** é uma das funcionalidades que foram mais aguardadas. Ela permite que você utilize famílias de fonts fora do padrão do sistema. Veja abaixo a sintaxe:

<pre class="lang-css">@font-face {
     font-family: helveticaneue;
     src: url('HelveticaNeueLTStd-UltLt.otf');
}
</pre>

Na primeira linha você define um nome para a font importada.
  
Na segunda linha, você inclue o endereço de onde a font se encontra. Para facilitar, crie uma pasta **font** dentro da pasta onde está o CSS.

Feito isso, você a utiliza como qualquer outra font:

<pre class="lang-css">p {
    font:36px helveticaneue, Arial, Tahoma, Sans-serif;
}
</pre>

Suponhamos que você queira oferecer a font para os usuário que não a possuem instalada, mas para aqueles usuários que tem a font em seus sistema, o browser utiliza a cópia local do usuário:

<pre class="lang-css">@font-face {
     font-family: helveticaneue;
     src: local(HelveticaNeueLTStd-UltLt.otf), url(HelveticaNeueLTStd-UltLt.otf);
}
</pre>

O valor **local()** faz com que o browser procure a font no computador do visitante antes de executar o download da que está no servidor.

Abaixo segue uma série de formatos que podem ser usados e que os browsers podem adotar:

<table>
  <tr>
    <th>
      Tipo da Font
    </th>
    
    <th>
      Formato
    </th>
    
    <th>
      Extensões
    </th>
  </tr>
  
  <tr>
    <th>
      &#8220;truetype&#8221;
    </th>
    
    <td>
      TrueType
    </td>
    
    <td>
      .ttf
    </td>
  </tr>
  
  <tr>
    <th>
      &#8220;opentype&#8221;
    </th>
    
    <td>
      OpenType
    </td>
    
    <td>
      .ttf, .otf
    </td>
  </tr>
  
  <tr>
    <th>
      &#8220;truetype-aat&#8221;
    </th>
    
    <td>
      TrueType with Apple Advanced Typography extensions
    </td>
    
    <td>
      .ttf
    </td>
  </tr>
  
  <tr>
    <th>
      &#8220;embedded-opentype&#8221;
    </th>
    
    <td>
      Embedded OpenType
    </td>
    
    <td>
      .eot
    </td>
  </tr>
  
  <tr>
    <th>
      &#8220;svg&#8221;
    </th>
    
    <td>
      SVG Font
    </td>
    
    <td>
      .svg, .svgz
    </td>
  </tr>
</table>

O código completo ficaria mais ou menos assim:

<pre class="lang-css">@font-face {
  font-family: 'NomeDaFont';
  src: url('nomedafont.eot');
  src: url('nomedafont?#iefix') format('embedded-opentype'),
    url('nomedafont.svg#Locaweb-Icons') format('svg'),
    url('nomedafont.ttf') format('truetype');
  font-weight: normal;
  font-style: normal;
}
</pre>

Nada muito complexo, não é?

Lembre-se de colocar o valor das propriedades **font-weight** e **font-style** de acordo com a font que você está importando. Assim o browser não tenta ficar emular o peso da font.

### Compatibilidade

A compatibilidade é melhor do que você pode imaginar. Mesmo assim há alguns entraves que chateiam.

As versões 7, 8 e 9 do Internet Explorer aceitam o @font-face apenas se a font for EOT. Você pode encontrar qualquer conversor online que esse problema é resolvido. Você pode converter suas fonts para EOT diretamente no [Font Squirrel][3]. O Safari, Firefox, Chrome e Opera aceitam fonts em TTF e OTF.

[Veja um exemplo pronto.][4]

### Fonts pagas

O principal problema com na utilização de **@font-face** é que arquivo da font é disponibilizado no servidor, de forma que qualquer um tem acesso. Se você estiver utilizando uma font paga, com direitos de copyright, o download desta font pode ser ilegal e você que está disponibilizando pode ser responsabilizado. Há uma série de fonts que são grátis, estas não há problema. Mas há uma outra grande parte que são pagas. O problema é que você tem a licensa de utilizar essa font nos seus projetos, mas não tem o direito de compartilhá-la ou dar para alguém. Quando você utiliza @font-face, você praticamente disponibiliza para o mundo o arquivo da font. Qualquer um pode fazer o download. Por isso, cuidado com a font que você utiliza. Certifique-se de que ela é uma font gratuita.

[Leia mais sobre @font-face direto do W3C.][5]

 [1]: http://typekit.com/
 [2]: http://www.mikeindustries.com/blog/archive/2004/12/sifr-2.0-release-candidate-2
 [3]: http://www.fontsquirrel.com/fontface/generator
 [4]: http://tableless.com.br/uploads/2010/03/fonface.html
 [5]: http://www.w3.org/TR/css3-fonts/#the-font-face-rule