---
title: Child Themes – O que é, como fazer e quando usar
author: Breno Alves
type: post
date: 2013-07-04
excerpt: Muitas vezes o volume de trabalho é maior do que você ou sua empresa pode suportar, mas há um jeito de tornar o desenvolvimento dos seus projetos em Wordpress ainda mais rápidos.
url: /child-themes-o-que-e-como-fazer-e-quando-usar/
dsq_thread_id: 1458678157
categories:
  - Artigos
  - Wordpress
tags:
  - child
  - childthemes
  - filho
  - temas
  - themes
  - Wordpress

---
Acredito que o **Child Theme**, ou “tema filho”, ****é um dos melhores recursos do WordPress. Com ele você pode adicionar ou alterar estilos, funções, templates de páginas e etc. sem a necessidade de mexer nos arquivos core do seu tema.

Ao criar um child theme você herda todas as funcionalidades de outro tema e pode modificá-las através de um novo arquivo totalmente independente.

Neste artigo vou mostrar como é fácil criar, ativar e fazer uma alteração no seu tema com o uso de um child theme e mostrar quais são os prós e contras em usá-lo.

## Vamos começar!

Primeiramente precisamos criar um diretório para o seu child theme na pasta de temas do wordpress (wp-content/themes) .

[<img class="alignnone size-full wp-image-37984" alt="criar" src="http://tableless.com.br/uploads/2013/07/criar.jpg" width="294" height="174" srcset="uploads/2013/07/criar.jpg 294w, uploads/2013/07/criar-283x168.jpg 283w" sizes="(max-width: 294px) 100vw, 294px" />][1]

Você pode dar qualquer nome a este diretório, mas o [codex do WordPress][2] recomenda que você use o nome do tema pai sucedido de “-child” apenas por uma questão de organização.

Em seguida devemos criar dentro do diretório do child theme um arquivo **style.css** que é o único arquivo obrigatório para que ele funcione.

<pre class="lang-css">/*
Theme Name:     Twenty Twelve Child
Theme URI:      http://www.tableless.com.br/
Description:    Tutorial de Child Theme para o Tableless
Author:         Tableless
Author URI:     http://www.tableless.com.br/
Template:       twentytwelve                             
Version:        1.0
*/</pre>

A única diferença do arquivo **style.css** de um child theme para o de um tema comum é a presença do nome do template pai, que em nosso caso é o “twentytwelve”.
  
Agora só falta ativarmos o tema no painel do wordpress.

[<img class="alignnone size-full wp-image-37989" alt="ativar" src="http://tableless.com.br/uploads/2013/07/ativar.png" width="328" height="344" srcset="uploads/2013/07/ativar.png 328w, uploads/2013/07/ativar-160x168.png 160w, uploads/2013/07/ativar-295x310.png 295w" sizes="(max-width: 328px) 100vw, 328px" />][3]

## Como funciona?

Pronto, agora que criamos o nosso child theme vamos entender como ele funciona.
  
Após ativar o tema, nosso site deverá aparecer assim (sem estilos aplicados):

[<img class="alignnone size-full wp-image-37991" style="border: 1px solid #333" alt="theme-zero" src="http://tableless.com.br/uploads/2013/07/theme-zero.png" width="468" height="380" srcset="uploads/2013/07/theme-zero.png 468w, uploads/2013/07/theme-zero-206x168.png 206w, uploads/2013/07/theme-zero-381x310.png 381w" sizes="(max-width: 468px) 100vw, 468px" />][4]

Isso ocorre pois o WordPress desativa a folha de estilos padrão (do tema pai) ao ativar o tema filho. Logo precisamos adicionar uma nova folha de estilos ao nosso tema.

<pre class="lang-php">&lt;?php
/*
 * Você deve usar o hook wp_enqueue_scripts para 
 * inserir arquivos CSS e JS no seu tema corretamente.
 */
function child_theme_scripts() {
  // O id abaixo deve mudar de acordo com o tema pai.
  wp_enqueue_style( &#039;twentytwelve-style&#039; );
}
add_action( &#039;wp_enqueue_scripts&#039;, &#039;child_theme_scripts&#039; );
</pre>

Pronto, no código acima estamos importando a folha de estilos do nosso tema pai. Agora seu site deve estar com os estilos funcionando perfeitamente e você poderá adicionar ou alterar qualquer estilo por este arquivo.

O seu child theme depois de criado, herda automaticamente todos os templates e funcionalidades do tema pai. Você só precisará adicionar na pasta do child theme os arquivos que você deseja alterar.

Por exemplo, se você quiser criar um novo rodapé para o seu site, basta criar um novo footer.php e colocá-lo na pasta do seu child theme, que ele irá substituir o footer.php do tema pai, sem que você precise modificá-lo diretamente.

## Na prática

Vamos alterar a cor do título da página e adicionar um subtítulo para demonstrar como funcionam as modificações em estilos. Para isso é só adicionar um novo estilo, na nossa folha de estilos do child theme.

<pre>article h1 {
	font-family: Georgia, Geneva, serif;
	font-size: 20px;
	color: #FF0000;
}</pre>

Pronto, no código acima estamos importando a folha de estilos do nosso tema pai. Agora seu site deve estar com os estilos funcionando perfeitamente e você poderá adicionar ou alterar qualquer estilo por este arquivo.

Antes

[<img class="alignnone size-full wp-image-37998" alt="antes" src="http://tableless.com.br/uploads/2013/07/antes.png" width="355" height="200" srcset="uploads/2013/07/antes.png 355w, uploads/2013/07/antes-298x168.png 298w" sizes="(max-width: 355px) 100vw, 355px" />][5]

Depois&#8230;

[<img alt="depois" src="http://tableless.com.br/uploads/2013/07/depois.png" width="355" height="200" />][6]

Pronto! Assim as alterações em estilos são bem simples de ser feitas, basta saber as classes do tema pai e um pouco de [efeito cascata, herança e especificidade do CSS][7].

Este recurso também facilita muito o estudo para quem está começando na criação de temas para WP e para quem trabalha sozinho, ou tem uma pequena empresa, ganhar tempo no desenvolvimento de novos sites.

Trabalho numa empresa pequena onde somos poucos desenvolvedores (dois) então o que mais fazemos é comprar um tema com funcionalidades básicas prontas (slider, carousel e etc.) e apenas estilizá-lo pelo child theme, fazendo pouquíssimas modificações no core. Até porque quando se tem um sistema pago, a frequência de atualizações é maior, aumentando o risco de surgirem problemas a cada versão. E ninguém quer deixar o seu cliente na mão, certo? 😉

É claro, como tudo na vida, nada é perfeito e há sim uma perda na velocidade de carregamento nas páginas, afinal ao importarmos os estilos e optarmos por evitar mexer no core, acabamos sobrescrevendo algumas classes com nossos novos estilos. Mas se essa não for a maior das prioridades no seu projeto, como no nosso caso, é uma excelente solução!

Espero que tenham gostado e qualquer dúvida postem nos comentários!
  
Abraço!

 [1]: http://tableless.com.br/uploads/2013/07/criar.jpg
 [2]: http://codex.wordpress.org/Child_Themes
 [3]: http://tableless.com.br/uploads/2013/07/ativar.png
 [4]: http://tableless.com.br/uploads/2013/07/theme-zero.png
 [5]: http://tableless.com.br/uploads/2013/07/antes.png
 [6]: http://tableless.com.br/uploads/2013/07/depois.png
 [7]: http://www.tableless.com.br/efeito-cascata-e-especificidade-do-css/