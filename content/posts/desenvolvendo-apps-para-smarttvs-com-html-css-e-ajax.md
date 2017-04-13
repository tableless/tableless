---
title: Desenvolvendo apps para SmartTVs com HTML, CSS e Ajax
author: WillBliner
type: post
date: 2015-08-03
excerpt: Entenda como funciona o básico do desenvolvimento pra SmartTVs.
url: /desenvolvendo-apps-para-smarttvs-com-html-css-e-ajax/
titulo_personalizado:
  - 'O básico sobre desenvolvimento para <strong>SmtartTVs</strong>'
categories:
  - Código
  - HTML
  - JavaScript
tags:
  - smarttv

---
Hoje em dia, as Smart TVs estão cada vez mais presentes no dia a dia. E muito por isso, gosto de pesquisar e aprender formas de programar sua interface e até criar apps que rodassem em seu ambiente. Nessas pesquisas, descobri que é fácil e simples o desenvolvimento para Smart TV, veja só:

**1º** Para criar apps para Smart TV você usará em primeiro lugar HTML, CSS e Ajax/JavaScript.

**2º** O modelo que vou usar será o da Samsung (que é a TV que mais tem suporte para o desenvolvimento). Você usará Eclipse para criação de suas apps e [baixará o SDK no próprio site da Samsung Developers][1].

**3º** A instalação do SDK e dos emuladores para Smart TVs é bem fácil, mas você precisa ter a máquina virtual Java em seu PC.

## Iniciando

**1º** Execute o Eclipse como administrador para facilitar a execução do emulador quando você rodar o app..

[<img class="alignnone size-full wp-image-49972" src="http://tableless.com.br/uploads/2015/07/imagem0.png" alt="imagem0" width="500" height="169" />][2]

**2º** quando o Eclipse estiver aberto você irá em File > New > Project para criar um novo projeto.

[<img class="alignnone size-full wp-image-49973" src="http://tableless.com.br/uploads/2015/07/imagem00.png" alt="imagem00" width="615" height="552" />][3]

**3º** Ai então você vai selecionar a opção de &#8220;Samsung Smart TV JavaScript App Project&#8221; porque essa opção permite que você crie apps com Ajax(Javacript) para o comportamento de sua app e CSS + HTML para interface.

[<img class="alignnone size-full wp-image-49962" src="http://tableless.com.br/uploads/2015/07/imagem-03.png" alt="imagem 03" width="642" height="601" />][4]

**4º** Em seguida dê nome para sua app, e escolha a resolução da tela.

[<img class="alignnone size-full wp-image-49964" src="http://tableless.com.br/uploads/2015/07/imagem04.png" alt="imagem04" width="703" height="607" />][5]

**5º** Pronto, se conseguiu fazer tudo direitinho você já pode começar a desenvolver sua app, no lado esquerdo você irá se deparar com as seguintes pastas, essas pastas são responsáveis pela organização do conteúdo de sua app, as mais importantes são &#8220;app&#8221; e &#8220;index.html&#8221;.

[<img class="alignnone size-full wp-image-49965" src="http://tableless.com.br/uploads/2015/07/imagem05.png" alt="imagem05" width="265" height="257" />][6]

**6º** Na pasta &#8220;app&#8221; ficam as pastas &#8220;stylesheets&#8221; e &#8220;javascript&#8221; com os arquivos &#8220;Main.css&#8221; e &#8220;Main.js&#8221; respectivamente. Em Main.css fica o conteúdo de CSS da app (responsável pelo estilo da app) e em Main.js fica o desenvolvimento lógico (programação) do comportamento da app, onde você usa Ajax para definir as ações da app, e em &#8220;index.html&#8221; fica os componentes em html para você dar vida a sua app. Na pasta icon é onde você armazena os ícones usados.

[<img class="alignnone size-full wp-image-49966" src="http://tableless.com.br/uploads/2015/07/imagem06.png" alt="imagem06" width="317" height="313" />][7]

**7º** Então vamos a nossa demo básica: dê um duplo clique em &#8220;index.html&#8221;. Insira seu código HTML nesse local. Vamos dar um &#8220;Hello World&#8221; apenas, somente para que vocês peguem noção.

[<img class="alignnone size-full wp-image-49967" src="http://tableless.com.br/uploads/2015/07/imagem07.png" alt="imagem07" width="800" height="330" />][8]

**8º** então nesse trecho insira o seguinte código:

[<img class="alignnone size-full wp-image-49975" src="http://tableless.com.br/uploads/2015/07/imagem007.png" alt="imagem007" width="705" height="156" />][9]

<pre class="lang-html">&lt;div id="label"&gt;
  &lt;h1&gt;Olá, esse é meu 1º artigo no Tableless!!&lt;/h1&gt;
&lt;/div&gt;
</pre>

**9º** Então você vai dar um duplo clique no arquivo Main.css para estilizar a escrita, e inserir o seguinte trecho:

<pre class="lang-css">#texto{
  width: 500px;
  heightt: 300px;
  position: absolute;
  top: 50%;
  left: 50%;
  margin-top: -150px;
  margin-left: -250px;
  color: #fff;
}
</pre>

(você usa a #label para pegar os elementos html e manipula-los com CSS)

[<img class="alignnone size-full wp-image-49976" src="http://tableless.com.br/uploads/2015/07/imagem008.png" alt="imagem008" width="415" height="239" />][10]

**10º** Feito isso agora você irá salvar e executar, com o botão direito você clica na pasta raiz do projeto e segue em &#8220;Samsung Smart TV SDK&#8221; e depois em &#8220;Run&#8221;.

[<img class="alignnone size-full wp-image-49970" src="http://tableless.com.br/uploads/2015/07/imagem10.png" alt="imagem10" width="664" height="144" />][11]

**11º** Irá levar um tempo se for a primeira vez, mas ao terminar você verá essa tela:

[<img class="alignnone size-full wp-image-49971" src="http://tableless.com.br/uploads/2015/07/imagem11.png" alt="imagem11" width="1209" height="686" />][12]

Agora você pode usar sua imaginação e criar a App que desejar apenas com HTML, CSS e Ajax, no próximo tutorial irei introduzir como usar Ajax no desenvolvimento da App.

 [1]: http://developer.samsung.com/home.do
 [2]: http://tableless.com.br/uploads/2015/07/imagem0.png
 [3]: http://tableless.com.br/uploads/2015/07/imagem00.png
 [4]: http://tableless.com.br/uploads/2015/07/imagem-03.png
 [5]: http://tableless.com.br/uploads/2015/07/imagem04.png
 [6]: http://tableless.com.br/uploads/2015/07/imagem05.png
 [7]: http://tableless.com.br/uploads/2015/07/imagem06.png
 [8]: http://tableless.com.br/uploads/2015/07/imagem07.png
 [9]: http://tableless.com.br/uploads/2015/07/imagem007.png
 [10]: http://tableless.com.br/uploads/2015/07/imagem008.png
 [11]: http://tableless.com.br/uploads/2015/07/imagem10.png
 [12]: http://tableless.com.br/uploads/2015/07/imagem11.png