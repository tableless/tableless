---
title: E-mail Newsletter Responsivo
author: Dani Guerrato
type: post
date: 2013-01-03
excerpt: Entenda como funciona e como fazer um email marketing responsivo.
url: /e-mail-newsletter-responsivo/
tweetbackscheck:
  - 1356383143
shorturls:
  - 'a:3:{s:9:"permalink";s:31:"http://tableless.com.br/?p=7611";s:7:"tinyurl";s:26:"http://tinyurl.com/bsd5wcu";s:4:"isgd";s:19:"http://is.gd/WI4pk0";}'
twittercomments:
  - 'a:0:{}'
dsq_thread_id: 992364554
categories:
  - Acessibilidade
  - Artigos
  - Código
  - HTML
  - Técnicas e Práticas
tags:
  - 2013
  - email marketing
  - responsive
  - resposivo

---
## Design Responsivo

Um assunto que ganhou muita evidência este ano no mundo do design digital é o desenvolvimento de sites responsivos. O termo, emprestado da arquitetura, surgiu em um post do blog [A List Apart][1]. Em resumo, são técnicas de design e CSS que, visando a usabilidade e a acessibilidade do conteúdo, fazem com que um site se adapte ao dispositivo do usuário. Parece mágico, mas na verdade é uma combinação de folhas de estilo engenhosas, matemática e um pouco de bom senso. O design responsivo utiliza elementos como o tipo de midia, resolução da tela, largura do viewport, densidade de pixels e medidas relativas para garantir uma melhor experiência de navegação independente do dispositivo que o usuário está utilizando. Design responsivo é design sustentavel e universal.

Se você for procurar na internet, encontrará discussões bem calorosas sobre o que é melhor: fazer uma versão mobile ou design responsivo. Mas o foco deste artigo não é levantar esta discussão, mas sim dar um passo além com o desenvolvimento responsivo e mostrar que ele não é limitado apenas a sites. Algumas técnicas podem ser aplicadas a newsletters e tornar o seu e-mail newsletter mais atrativo para dispositivos móveis. E impressionar o seu chefe, cliente e / ou mãe

Este post pressupõe que você já conheça o básico sobre o assunto. Mas não se desespere, pequeno Padawan. Para quem não sabe nada sobre o tema existem diversos artigos interessantes aqui no próprio [Tableless][2] ou você pode ainda conferir [aqui][3], [aqui][4] e [aqui][5] a série de textos escritos por mim para o BlogUp.

## As vezes é preciso sujar as mãos

Fazer um e-mail newsletter usando HTML é montar um código de maneira antiga, usando técnicas ultrapassadas e não muito semânticas. Isso porque muitos leitores de e-mail não lêem corretamente alguns parâmetros de CSS, ou seja, a recomendação aqui é realmente cometer algumas heresias como colocar estilos direto no HTML e utilizar (argh) tabelas para dados não tabulares.

Para montar um projeto de e-mail newsletter responsivo nós continuaremos desenvolvendo o código desta maneira antiga, infelizmente.

## Media Queries salvam o dia

A parte divertida é que diversos dispositivos mobile aceitam Media Queries e interpretam o CSS de uma maneira bem mais lógica. E isso nos permite criar estilos mais avançados usando o !important no CSS para sobrepor os parâmetros de estilo que determinamos no HTML. Ou seja, dá para aplicar aqui o principio de progressive enhancement.

É claro que não são todos os programas e dispositivos que aceitam Media Queries e parâmetros de CSS mais atuais. Para estes dispositivos, o seu e-mail terá o mesmo layout determinado para desktops.

Veja abaixo a lista de dispositivos que aceitam Media Queries em seu leitor de e-mail padrão.

**Aplicativos de leitura de emails nativos**

<table>
  <tr>
    <td>
      <strong>Cliente</strong>
    </td>
    
    <td>
      <strong>Suporta Media Querie?</strong>
    </td>
  </tr>
  
  <tr>
    <td>
      Amazon Kindle Fire
    </td>
    
    <td>
      Sim
    </td>
  </tr>
  
  <tr>
    <td>
      Amazon Kindle Fire HD
    </td>
    
    <td>
      Sim
    </td>
  </tr>
  
  <tr>
    <td>
      Android 2.1 Eclair
    </td>
    
    <td>
      Não
    </td>
  </tr>
  
  <tr>
    <td>
      Android 2.2+
    </td>
    
    <td>
      Sim
    </td>
  </tr>
  
  <tr>
    <td>
      Apple iPhone
    </td>
    
    <td>
      Sim
    </td>
  </tr>
  
  <tr>
    <td>
      Apple iPad
    </td>
    
    <td>
      Sim
    </td>
  </tr>
  
  <tr>
    <td>
      Apple iPod Touch
    </td>
    
    <td>
      Sim
    </td>
  </tr>
  
  <tr>
    <td>
      BlackBerry OS 5
    </td>
    
    <td>
      Sim
    </td>
  </tr>
  
  <tr>
    <td>
      BlackBerry OS 6+
    </td>
    
    <td>
      Sim
    </td>
  </tr>
  
  <tr>
    <td>
      BlackBerry Playbook
    </td>
    
    <td>
      Sim
    </td>
  </tr>
  
  <tr>
    <td>
      Microsoft Windows Mobile 6.1
    </td>
    
    <td>
      Não
    </td>
  </tr>
  
  <tr>
    <td>
      Microsoft Windows Phone 7
    </td>
    
    <td>
      Não
    </td>
  </tr>
  
  <tr>
    <td>
      Microsoft Windows Phone 7.5+
    </td>
    
    <td>
      Sim
    </td>
  </tr>
  
  <tr>
    <td>
      Microsoft Surface
    </td>
    
    <td>
      Não
    </td>
  </tr>
  
  <tr>
    <td>
      Palm Web OS 4.5
    </td>
    
    <td>
      Sim
    </td>
  </tr>
</table>

**Aplicativos de leitura de email não nativos**

<table>
  <tr>
    <td>
      <strong>Cliente</strong>
    </td>
    
    <td>
      <strong>Suporta Media Querie</strong>
    </td>
  </tr>
  
  <tr>
    <td>
      Microsoft Outlook Exchange 3rd party app (Android)
    </td>
    
    <td>
      Não
    </td>
  </tr>
  
  <tr>
    <td>
      Gmail mobile app (todas as plataformas)
    </td>
    
    <td>
      Não
    </td>
  </tr>
  
  <tr>
    <td>
      Yahoo! Mail mobile app (todas as plataformas)
    </td>
    
    <td>
      Não
    </td>
  </tr>
</table>

## Algumas dicas práticas para o Layout

Para desenvolver, não apenas um template de e-mail em HTML, mas qualquer projeto de design responsivo é necessário ter em mente que o seu trabalho será acessado pelos mais diferentes tipos de usuário. Não existem apenas iPhones e iPads&#8230; Qualquer modelo de dispositivo móvel vendido atualmente, até o tablet chinês que meu sobrinho ganhou em seu aniversário de 6 anos, tem um leitor de e-mails. O ideal aqui é é englobar o maior número de dispositivos possíveis.

Para garantir uma boa user experience, precisamos levar em consideração alguns pontos:

**Tamanho mínimo do texto**
  
&#8211; Em muitos aplicativos de leitura de e-mail, como o do iPhone, o tamanho mínimo da fonte é de 13px. Isso significa que, se você utilizar um tamanho menor, ele irá converter o texto automaticamente para 13px.

**Não faça algo menor que a ponta de um dedo**
  
&#8211; Recomenda-se que para ícones clicáveis uma área mínima de 44&#215;44 pixels. Este tamanho irá facilitar o usuário de acessar o item com o dedo sem clicar acidentalmente em outros ícones.

**Medidas relativas sempre**
  
&#8211; Prefira usar medidas em porcentagem para as larguras dos elementos. Isso pode garantir que ele seja acessível em dispositivos com a tela em tamanhos não previstos nos seus media queries.

**Evite layouts em colunas**
  
&#8211; Em se tratando de desktops, a largura recomendável de um e-mail template é 640px. Neste caso é possível dividir o layout em colunas pois o espaçamento e as margens de um leitor de e-mails em um computador são grandes o suficiente para uma leitura confortável. Já em um smartphone não é recomendável o uso de um layout com várias colunas pois o tamanho reduzido da tela contribui pra uma sensação claustrofóbica, fazendo os elementos parecerem aglomerados.

**Crie uma experiência única**
  
&#8211; Apesar da alta resolução da atual geração de smartphones, como é o caso do o iPhone 5 (568px em formato landscape), é interessante pensar em um design diferenciado, já que a experiência do usuário ao interagir com um layout muda completamente só pelo fato de estar em um dispositivo com tela sensível ao toque.

**Go mobile**
  
A maior parte dos clientes de e-mail para desktop não são adaptáveis para tamanhos de tela menores que 960px. Basta tentar redimensionar a janela do Gmail, por exemplo, para verificar que este é o último ponto de quebra disponível para computadores. Nosso foco aqui será, portanto, apenas os dispositivos móveis. Sendo assim, o media querie que utilizaremos é @media only screen and (max-device-width: [insira a largura maxima aqui]) . Isso fará com que as mudanças de layout sejam vistas apenas em dispositivos móveis.

**Tudo é !important**
  
Clientes de e-mail antigos não entendem CSS. Por isto é necessário determinar um conjunto de estilos básicos no próprio HTML. Nosso CSS ficará para os softwares e aplicativos mais modernos, capazes de entender media queries. Portanto não se esqueça da tag !important. para os estilos que você deseja sobrescrever.

## Construindo o código

A principal regra no desenvolvimento de e-mails newsletter é a de sempre preferir aplicar os estilos diretamente no HTML de maneira inteligente visando a adaptação mais rápida dos elementos para uma largura menor no CSS.

Vamos começar pelo layout para desktops. Para a nossa demo vamos considerar uma tabela com uma largura de 640px, dividida em duas colunas com 320px cada. Para fazer o distanciamento dessas colunas vamos trabalhar com o parâmetro cellpadding. Uma outra opção seria o cellspacing, mas neste caso o espaço a mais entre as células da tabela faria com que ela ficasse maior do que 640px e desalinharia o layout. Já quando usamos cellpadding, o espaço é adicionado internamente nas células, sem aumentar o tamanho final da tabela.

<img class="alignnone size-full wp-image-7628" alt="Screenshot Demo E-mail Newsletter" src="http://tableless.com.br/uploads/2012/12/screenshot-demo-email-newsl.jpg" width="720" height="760" srcset="uploads/2012/12/screenshot-demo-email-newsl.jpg 720w, uploads/2012/12/screenshot-demo-email-newsl-284x300.jpg 284w" sizes="(max-width: 720px) 100vw, 720px" />

Ainda pensando na versão desktop, para alinhar em duas colunas usaremos o aling=left diretamente na tabela. Isso equivaleria ao float:left do CSS. Mas, se aplicar o float:left você poderia ter problemas com alguns leitores de e-mails desktop, como o outlook 2007.

## A estrutura basica do layout

<pre>&lt;!--tabela principal, com a largura do documento--&gt;
&lt;table width="640" border="0" cellpadding="0" cellspacing="0" class=”conteudo”&gt;
&lt;tr&gt;
&lt;td&gt;
&lt;!--tabela que equivale ao conteúdo da coluna da esquerda. Tem 320px de largura, 20 de cellpading e align left, para se posicionar a esquerda da tabela seguinte--&gt;
&lt;table width="320" border="0" cellspacing="0" cellpadding="20" align="left" class=”esquerdaCol”&gt;
&lt;tr&gt;
&lt;td&gt;&lt;p&gt;Coluna da esquerda&lt;/p&gt;&lt;/td&gt;
&lt;/tr&gt;
&lt;/table&gt;
&lt;!--Tabela que seria a coluna da direita. Note que aqui não é necessário utilizar o parametro align.--&gt;
&lt;table width="320" border="0" cellspacing="0" cellpadding="20" class=”direitaCol”&gt;
&lt;tr&gt;
&lt;td&gt;&lt;p&gt;Coluna da direita&lt;/p&gt;&lt;/td&gt;
&lt;/tr&gt;
&lt;/table&gt;
&lt;/td&gt;
&lt;/tr&gt;
&lt;/table&gt;</pre>

Agora vamos ao CSS! Antes de tudo, nós vamos colocar os media queries no inicio do nosso código. Isso irá evitar algum acidente caso o leitor de e-mails da pessoa resolva ler seus media queries mesmo que você não queira. É raro, mas acontece&#8230; E, se acontecer, o código a seguir, que é o da versão desktop, irá sobrescrever o código do Media Querie evitando que carregue parâmetros específicos para o smartphone na versão desktop do site.

<img class="alignnone size-full wp-image-7631" alt="Screenshot E-mail Newsletter Mobile" src="http://tableless.com.br/uploads/2012/12/screenshot-newsletter-mobil.jpg" width="720" height="760" srcset="uploads/2012/12/screenshot-newsletter-mobil.jpg 720w, uploads/2012/12/screenshot-newsletter-mobil-284x300.jpg 284w" sizes="(max-width: 720px) 100vw, 720px" />

Para transformar o código acima, que é de duas colunas, em um código de uma coluna basta eu mandar a tabela principal, com 640px de largura, ficar com menos que isso. As colunas internas, que tem 320px cada irão se manter deste mesmo tamanho e “cair” uma para baixo da outra quando a tabela principal passar a ser menor. Não se esqueça de usar o !important para sobrepor os estilos do HTML.

O código ficaria assim:

<pre>&lt;style type="text/css"&gt;
@media only screen and (max-device-width: 480px) {
table[class=conteudo] {
width:320px !important;
}
}
&lt;/style&gt;</pre>

Basta então alterar a largura das colunas para o valor desejado. Não se esquecendo, é claro, do valor do cellpading declarado.

## Trabalhando com Imagens

Como, no caso de templates para e-mails, é bom evitar o uso de CSS, o ideal é determinamos a largura e altura de imagens na própria tag  <img alt="" />dentro das tabelas. Isso garante a visualização correta das figuras. Porém, quando redimensionarmos a tabela para dispositivos menores, é provável que imagens grandes desalinhem o layout.

Existem duas soluções para este problema. É possível utilizar o parâmetro display:none para a imagem maior e carregar a menor por background-image. O lado negativo aqui é que o usuário acaba realizando o download de duas imagens diferentes&#8230; A segunda solução é forçar a imagem a se redimensionar e utilizar o parâmetro !important para sobrescrever o tamanho original do arquivo, mas é necessário um cuidado aqui para manter a proporção correta e não distorcer a imagem.

<pre>@media only screen and (max-device-width: 480px) {
td[class="header"] {
background-image: url(images/header-325.png);
width: 325px !important;
height: 115px !important;
}
td[class="header"] img {
display: none;
}
}</pre>

Estamos colocando um background na TD de classe “header”, e mandando ele esconder a  <img alt="" />dentro desta

usando o display:none.

Veja o HTML:

<pre>&lt;table width="640" border="0" cellspacing="0" cellpadding="0"&gt;
&lt;tr&gt;
&lt;td class="header"&gt;
&lt;img src="images/header.png" border="0" width="640" /&gt;
&lt;/td&gt;
&lt;/tr&gt;
&lt;/table&gt;</pre>

Uma outra solução é trabalhar com imagens que fluem de acordo com o tamanho da célula utilizando o parâmetro background-size:cover. Esta solução não é compatível com browsers antigos.

<pre>@media only screen and (max-device-width: 480px) {
td[class="headercell"] {
background-image: url(images/header-480.png) !important;
background-size: cover;
}
td[class="headercell"] img {
display: none;
}
}</pre>

Uma boa pratica é determinar o valor da largura em porcentagem. Se for fazer isso, não se esqueça de usar o !important e determinar a altura como automática, garantido que a imagem se redimensione corretamente.

<pre>@media only screen and (max-device-width: 480px) {
td[class=header] img {
height:auto !important;
width:100% !important;
}
}</pre>

## Retina Display

Design responsivo não é apenas redimensionar alguns elementos do layout. A ideia principal aqui é criar uma experiência do usuário própria para cada tipo de mídia. Com o surgimento das telas de alta definição como a Retina Display da Apple, é interessante oferecer imagens com a qualidade superior. Para isto basta utilizar um media querie específico para dispositivos com maior densidade de pixels.

<pre>@media all and (min-device-pixel-ratio : 1.5)</pre>

## Considerações Finais e downloads de exemplos

Já faz tempo que a internet não está mais apenas nos computadores. Smartphones, tablets, televisores e videogames portáteis são dispositivos comuns no dia-a-dia dos usuários. E ler e-mails é uma das atividades mais corriqueiras. É bem difícil prever quais serão os tipos de midia do futuro, mas o fato é que não podemos mais considerar a web como algo restrito a uma caixinha com 1024 pixels de largura. Apresentar um layout adequado para cada tipo de mídia deixa de ser um luxo e passa a ser uma obrigação. A minha aposta é que com o tempo seja tão essencial como desenvolver códigos semânticos, por exemplo.

Da mesma forma que acontece com os browsers, a medida que os clientes de e-mail antigos passam a ser abandonados as opções de estilização ficam cada vez mais interessantes. A tendência é que as novas tecnologias leiam códigos cada vez mais complexos. É nossa responsabilidade, portanto, oferecer aos usuários sempre a melhor opção de usabilidade e acessibilidade. Em telas grandes e pequenas. Em sites e emails.

[Download de exemplo][6]

####  Leia mais sobre o assunto:

&#8211; [Responsive Email Design][7]
  
&#8211; [Responsive Email Templates][8]
  
&#8211; [Email newsletter mobile responsivo][9]

 [1]: http://www.alistapart.com/articles/responsive-web-design/ "Responsive Web Design"
 [2]: http://tableless.com.br/?s=design+responsivo "Design Responsivo no Tableless"
 [3]: http://blog.popupdesign.com.br/design-responsivo-i-o-que-e-e-por-que-usar/ "Design Responsivo 1"
 [4]: http://blog.popupdesign.com.br/design-responsivo-grids-e-texto/ "Design Responsivo 2"
 [5]: http://blog.popupdesign.com.br/design-responsivo-iii-media-queries-e-compatibilidade/ "Design Responsivo 3"
 [6]: http://tableless.com.br/uploads/2012/12/exemplo_newsletter_responsiva.rar "Exemplo de Newsletter Responsiva"
 [7]: http://www.campaignmonitor.com/guides/mobile/ "Responsive Email Design"
 [8]: http://www.zurb.com/playground/responsive-email-templates "Responsive Email Templates"
 [9]: http://sergiolopes.org/email-newsletter-mobile-responsivo/ "Email Newsletter Mobile Responsivo"