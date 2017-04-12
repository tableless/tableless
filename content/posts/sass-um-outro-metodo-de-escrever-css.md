---
title: O que é Sass? Entenda esse outro método de escrever CSS
author: Thaiana Poplade
type: post
date: 2013-06-11
excerpt: Quando pensamos em produtividade, logo nos perguntamos e pesquisamos como aumentá-la sem grandes impactos. Então, os pré-processadores e frameworks para CSS vem suprir essa necessidade. Com vocês, um pouco de Sass.
url: /sass-um-outro-metodo-de-escrever-css/
categories:
  - Artigos
  - CSS
  - CSS3
  - HTML
  - Técnicas e Práticas
tags:
  - CSS
  - frameworks

---
Se você é um desenvolvedor front-end que está atualmente no mercado, já ouviu/leu palavrinhas como <a href="http://lesscss.org/" target="_blank">LESS</a>, <a href="http://foundation.zurb.com/" target="_blank">Foundation</a> e <a href="http://sass-lang.com" target="_blank">Sass</a>. Alguns sabem do que estou falando, outros não, mas o fato que é que esses nomes foram dados à pré-processadores e frameworks de folhas de estilo para auxiliar na produtividade de códigos, principalmente no que diz respeito a repetição de uma mesma ação, diversas vezes.

Quantas vezes você se pegou copiando e colando aquele monte de classes _identadas_ com mais de 15 linhas repetidamente e pensou: podia existir uma maneira mais rápida de fazer isso.

Agora eu te digo: tem!

Eu conversei com alguns amigos desenvolvedores e fui saber quais dessas novidades têm sido mais usada, e a disputa ficou bastante acirrada entre os pré-processadores preferidos e os frameworks mais utilizados. Ainda assim, na mesma semana acabei lendo um artigo técnico sobre o uso do Sass e por isso resolvi também testá-lo para entender como ele funciona.

Basicamente você começa “instalando” ele em sua máquina. Para os usuários de MAC é bem mais tranquilo que para os usuários de PC, porque para o Sass “rodar“ precisamos que o  <a href="http://pt.wikipedia.org/wiki/Ruby_%28linguagem_de_programa%C3%A7%C3%A3o%29" target="_blank">Ruby</a> também esteja instalado e isso já é nativo no MAC. De qualquer forma, não é nenhuma experiência traumática. <a href="http://sass-lang.com/download.html" target="_blank">No próprio site do Sass você encontra os dois métodos de instalação.</a>

Eu uso MAC e escolhi instalar o Sass através do Git.

Após clonar o repositório, criei no diretório escolhido um novo arquivo com o nome de “**style.scss**”. Neste arquivo de folha de estilo, escrevi as seguintes linhas de código:

<pre>.content {
backgoround: #000;
font-family: Arial;
font-size: 15px;
p{ line-height: 20px;}
}</pre>

Depois abri o terminal, no diretório onde o arquivo .scss foi salvo e digitei:
  
`sass --watch style.scss:style.css`

Pronto! A mágica está feita.

Este comando cria um novo arquivo **style.css** no mesmo diretório traduzindo as linhas digitadas acima em:

<pre>.content {
  backgoround: #000;
  font-family: Arial;
  font-size: 15px; }
    .content p {
   line-height: 20px;
}</pre>

Neste momento você pode estar pensando: Ah, é legal, mas não vi tanta mágica assim.

Então vamos incrementar um pouco as coisas.

Digite em seu arquivo **.scss**:

<pre>.varios-elementos{
       background:#ccc;
       p{ color:red}
       a{ color:pink}
       input{
         -moz-border-radius: 20px;
         border-radius: 20px;
         -webkit-border-radius: 20px;
         border-left:solid 1px #eaeaeb;
         border-right:solid 1px #eaeaeb;
         border-bottom:solid 1px #eaeaeb; 
         border-top:solid 3px #ccc;
       }
    }</pre>

Salve e em seguida seu arquivo **style.css** estará com:

<pre>.varios-elementos {
  background: #ccc; }
  .varios-elementos p {
    color: red; }
  .varios-elementos a {
    color: pink; }
  .varios-elementos input {
    -moz-border-radius: 20px;
    border-radius: 20px;
    -webkit-border-radius: 20px;
    border-left: solid 1px #eaeaeb;
    border-right: solid 1px #eaeaeb;
    border-bottom: solid 1px #eaeaeb;
    border-top: solid 3px #ccc; }</pre>

Percebeu? “.vários-elementos“ foi a classe que criamos, em seguida começamos a escrever as características desta classe e dos elementos que nela continham, de forma bastante intuitiva e direta.

Não tem muito segredo né?

O Sass também permite o **uso de variáveis**. Por exemplo:

<pre>$main-color: #d5d5d5

.botao{
   background: $main-color;
}</pre>

**O uso de pseudo-elementos**:

<pre>a {
   color: #ce4dd6;
   &:hover { color: #ffb3ff;}
   &:visited { color: #c458cb; }
  }</pre>

**O uso de Operações e Funções**

<pre>#navbar {
        $navbar-width: 800px;
        $items: 5;
        width: $navbar-width;
        li {
            float: left;
            width: $navbar-width/$items - 10px;
            }
        }</pre>

E o **uso de interpolação**: você pode utilizar variáveis não apenas para valores, mas também propriedades ou seletores:

<pre>$vert: top;
$horz: left;
$radius: 10px;
.rounded-#{$vert}-#{$horz} {
       border-#{$vert}-#{$horz}-radius: $radius;
       -moz-border-radius-#{$vert}#{$horz}: $radius;
       -webkit-border-#{$vert}-#{$horz}-radius: $radius;
    }</pre>

Também é permitido importar outros arquivos, como já é possível nos arquivos CSS tradicionais e também o uso da diretiva **“@mixin”** que é umas das _features_ mais valorizadas do Sass, onde você pode aproveitar pedaços de códigos com elementos, seletores ou propriedades, simplesmente importando através diretiva “@include“ no arquivo .scss:

<pre>@mixin rounded-top-left {
        $vert: top;
        $horz: left;
        $radius: 10px;
        border-#{$vert}-#{$horz}-radius: $radius;
        -moz-border-radius-#{$vert}#{$horz}: $radius;
        -webkit-border-#{$vert}-#{$horz}-radius: $radius;
}
#navbar li { @include rounded-top-left; }
#footer { @include rounded-top-left; }</pre>

Legal né?

Pois então, enquanto eu testava o Sass me perguntava: vale a pena aprender um novo jeito de escrever CSS? E a resposta foi: vale, dependendo do seu objetivo.

Se o tempo para o desenvolvimento for curto, o ideal é manter-se no que você já conhece e sabe fazer. Experimentar, pode dar muito certo e te fazer adquirir ainda mais conhecimento, mas também pode dar errado e você não ter tempo de arrumar, além de atrasar seu cronograma.

Pondere isso, mas não deixe de estudar. Quem sabe numa tarde sem muito job você pode usar o Sass, aprender a aplicá-lo em sua plenitude e dar tudo muito certo quando você for desenvolver projetos a valer.

😉

Até a próxima.

&nbsp;

OBS: Pessoal, conforme o comentário abaixo do Duke, existe uma correção a ser feita no que diz respeito à &#8220;dependência&#8221; do Ruby para a instalação do Sass:<header>

[Duke:][1]</header> 

<div>
  <div>
    <div>
      <p>
        O SASS de forma alguma depende do Ruby On Rails, o SASS assim como o Ruby On Rails são gem(plugins) do Ruby, o Mac OS não vem com o Ruby on Rails instalado e sim com o Ruby. Veja no proprio link que você colocou da Wikipedia está lá &#8220;Escrito em: Ruby&#8221; ou seja Ruby On Rails está para Ruby assim como CakePHP está para PHP, Django está para Python.
      </p>
      
      <p>
        &nbsp;
      </p>
      
      <p>
        É isso aí ;).
      </p>
      
      <p>
        &nbsp;
      </p>
    </div>
  </div>
</div>

 [1]: http://tableless.com.br/sass-um-outro-metodo-de-escrever-css/#