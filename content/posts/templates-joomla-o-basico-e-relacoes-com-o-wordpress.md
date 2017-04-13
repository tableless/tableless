---
title: 'Templates Joomla!: o básico e relações com o WordPress'
author: Wellyson Freitas
type: post
date: 2015-05-25
excerpt: Saiba como criar um template básico para o Joomla! e conheça as relações existentes com os temas do WordPress — os melhores CMS que existem atualmente.
url: /templates-joomla-o-basico-e-relacoes-com-o-wordpress/
categories:
  - CMS
  - Joomla
  - PHP
tags:
  - aprenda
  - cms
  - Extensions
  - joomla
  - Na Prática
  - php
  - Técnicas e Práticas
  - temas
  - Templates
  - Wordpress

---
Ao lado do WordPress, o Joomla! é sem dúvida um dos melhores CMS que existem atualmente. Como o amigo Girlan bem já escreveu <a title="Vamos falar de Joomla!?" href="http://tableless.com.br/vamos-falar-de-joomla/" target="_blank">noutro artigo</a>, o Joomla! tem se superado muito a cada versão&nbsp;e, desta perspectiva, torna-se mais que vantajoso ao desenvolvedor front-end dominar a criação de temas tanto para&nbsp;o WordPress quanto para o Joomla!.

A boa notícia é que se você já sabe&nbsp;criar temas para o WordPress, você praticamente já&nbsp;sabe criar&nbsp;templates para o Joomla! também. O objetivo deste artigo, portanto, não é embarcar naquela velha discussão <del>formada sobre tudo</del> de qual CMS é o melhor. Estamos mais interessados em criar um template básico (ou sandbox) para o Joomla! observando as relações existentes com&nbsp;o desenvolvimento de temas para o WordPress, despertando, quem sabe, novos joomlers pela comunidade Tableless!&nbsp;<img class="emoji" src="http://s.w.org/images/core/emoji/72x72/1f609.png" alt="😉" />

## Entendendo o Joomla!

Antes de criar um template para o Joomla!, primeiro precisamos entender, pelo menos superficialmente, como ele funciona.&nbsp;Em suma, podemos dizer que a principal função do&nbsp;Joomla! é reunir o conteúdo armazenado no banco de dados e gerenciado no painel de administração com ACL usando um&nbsp;template para produzir páginas HTML de forma dinâmica&nbsp;via PHP.

O Joomla! se&nbsp;assemelha ao WordPress em muitos aspectos. O&nbsp;conceito de artigo, por exemplo, se assemelha ao de post do WordPress: é a forma concebida ao conteúdo principal armazenado no banco de dados para ser&nbsp;gerenciado no painel de administração. O mesmo vale para os módulos e widgets, templates e temas, plugins, entre outras semelhanças — é claro que&nbsp;cada CMS apresenta as suas próprias especificidades, mas, por hora, vamos deixar assim.

Composto basicamente por um framework e suas extensões —&nbsp;analogamente a&nbsp;um sistema operacional e suas aplicações —, o diferencial do Joomla! está justamente nas extensões chamadas de **componentes**, que permitem desenvolver sites de todas as formas e tamanhos&nbsp;através de <a title="MVC – Afinal, é o quê ?" href="http://tableless.com.br/mvc-afinal-e-o-que/" target="_blank">arquitetura MVC</a>. No desenvolvimento de templates, só nos interessa a camada _view_ dos componentes, doravante chamada apenas de &#8220;componente&#8221;.

Vejamos mais sobre as extensões&#8230;

### As extensões do Joomla!

> Uma extensão é um pacote de programa que estende a instalação do Joomla! de diferentes maneiras.&nbsp;<cite>Documentação do Joomla!</cite>

Ainda segundo a documentação do Joomla!, as extensões podem ser classificadas basicamente em&nbsp;**componentes**, **módulos**, **plugins** e **templates**. Também os idiomas do Joomla! e os pacotes de extensões relacionadas, os&nbsp;packages, são consideradas extensões, assim como as bibliotecas que fornecem funções que podem ser usadas por outras extensões.

O Joomla! possui extensões nativas que se mostram&nbsp;suficientes na&nbsp;maioria dos nossos projetos, o que não nos&nbsp;impede de criar as nossas próprias extensões ou usar&nbsp;algumas das&nbsp;**9 mil extensões disponíveis** (e aumentando!) no <a title="Diretório de Extensões do Joomla!" href="http://extensions.joomla.org/" target="_blank">JED</a>, o&nbsp;diretório de extensões do Joomla!.

Para conhecer melhor o CMS, você pode&nbsp;<a title="Download da última versão do Joomla!" href="http://www.joomla.org/download.html" target="_blank">baixar a última versão do Joomla!</a>&nbsp;e instalar localmente ou <a title="Fazer test-drive rápido do Joomla!" href="http://demo.joomla.org/" target="_blank">fazer um test-drive rápido no Joomla.org</a>, que gera instantaneamente uma instalação remota todinha&nbsp;sua por 90 minutos. Aqui, nos referimos à versão 3.4.1 do Joomla! e, para comparação, à versão 4.2.2 do WordPress — as mais recentes até a&nbsp;publicação deste artigo.

Sem mais&nbsp;delongas, vamos ao que interessa!

## Criando um template para o Joomla!

Assim como, por padrão, os temas do WordPress ficam localizados no diretório _/wp-content/themes/_, os templates do Joomla! ficam localizados no diretório _/templates/_. Para começar, vamos criar um diretório chamado &#8220;meunovotemplate&#8221; com a seguinte estrutura básica de arquivos de todo template Joomla!:

<img class="alignnone size-full wp-image-49093" src="http://tableless.com.br/uploads/2015/05/estrutura-basica-de-arquivos-de-templates-joomla.png" alt="estrutura-basica-de-arquivos-de-templates-joomla" width="283" height="226" />

Adicionamos&nbsp;arquivos _index.html_&nbsp;em branco no&nbsp;diretório do template e em seus subdiretórios como&nbsp;medida adicional de segurança contra a exposição de informações da instalação por eventuais tentativas de&nbsp;acesso direto aos&nbsp;diretórios com permissões 775 de FTP — equivalente aos arquivos _index.php_&nbsp;&#8220;silence is golden&#8221; do WordPress.

### Definindo as informações do template

O arquivo _templateDetails.xml_&nbsp;é equivalente aos comentários iniciais do arquivo _style.css_ dos temas do WordPress&nbsp;(stylesheet header). Através de XML, são marcadas as informações do template para a instalação e, posteriormente, para serem exibidas no Gerenciador de Temas do painel de administração. Veja um&nbsp;exemplo:

<pre class="lang-php">&lt;?xml version="1.0" encoding="utf-8" ?&gt;
&lt;extension version="3.4.1" type="template"&gt;
  &lt;name&gt;Meu novo template&lt;/name&gt;
  &lt;creationDate&gt;25/05/2015&lt;/creationDate&gt;
  &lt;author&gt;Tableless&lt;/author&gt;
  &lt;authorEmail&gt;contato@tableless.com.br&lt;/authorEmail&gt;
  &lt;authorUrl&gt;http://www.tableless.com.br&lt;/authorUrl&gt;
  &lt;copyright&gt;© 2015 Tableless. Todos os direitos reservados.&lt;/copyright&gt;
  &lt;license&gt;GNU/GPL&lt;/license&gt;
  &lt;version&gt;1.0&lt;/version&gt;
  &lt;description&gt;Descrição do meu novo template.&lt;/description&gt;
  &lt;files&gt;
    &lt;folder&gt;css&lt;/folder&gt;
    &lt;folder&gt;images&lt;/folder&gt;
    &lt;filename&gt;index.php&lt;/filename&gt;
    &lt;filename&gt;templateDetails.xml&lt;/filename&gt;
    &lt;filename&gt;index.html&lt;/filename&gt;
  &lt;/files&gt;
  &lt;positions&gt;
    &lt;position&gt;breadcrumb&lt;/position&gt;
    &lt;position&gt;mainmenu&lt;/position&gt;
    &lt;position&gt;aside&lt;/position&gt;
  &lt;/positions&gt;
&lt;/extension&gt;</pre>

Na primeira linha, informamos&nbsp;a versão <abbr style="cursor: help" title="eXtensible Markup Language">XML</abbr> e o tipo de codificação do arquivo (recomenda-se&nbsp;o uso de&nbsp;<a title="HTML: Encode UTF-8" href="http://tableless.com.br/html-encode-utf-8/" target="_blank">UTF-8</a> sem BOM). Na segunda, informamos&nbsp;a versão da instalação do Joomla!&nbsp;e&nbsp;o tipo da extensão.&nbsp;A partir daí, as tags falam por si mesmas: as tags `<name>` informam o nome do template, as tags `<creationDate>` informam a data de criação do template e por aí vai&#8230;

As tags&nbsp;`<filemame>`&nbsp;e&nbsp;`<folder>`&nbsp;informam, respectivamente, os arquivos e os diretórios do template. Vale ressaltar que se já informamos algum diretório do template, não precisamos informar os arquivos e subdiretórios contidos nele (tome como exemplo o diretório para as folhas de estilo, cujos arquivos _style.css_ e _index.html_&nbsp;contidos nele não&nbsp;informamos&nbsp;diretamente). Assim, os únicos arquivos e diretórios&nbsp;que precisamos informar são os que se encontram **imediatamente** no diretório que criamos.

Já as&nbsp;tags `<positions>` informam os nomes das&nbsp;posições que os módulos poderão ocupar nas páginas do&nbsp;site&nbsp;—&nbsp;mas ainda não as posições em si, o que definiremos&nbsp;no modelo.

### Modelo:&nbsp;a&nbsp;estrutura do&nbsp;template

Ao contrário do que acontece no&nbsp;WordPress, em que a estrutura de um tema é&nbsp;dividida em <a title="Hierarquia de arquivos do WordPress" href="http://tableless.com.br/hierarquia-de-arquivos-do-wordpress/" target="_blank">vários arquivos</a>&nbsp;pela funcionalidade, a estrutura de um template do Joomla! normalmente&nbsp;se concentra em apenas um: o _index.php_. Com ele, nós criamos uma página genérica para todo o site, isto é, um **modelo** para todas as páginas específicas do site, incluindo declarações próprias&nbsp;do Joomla! que processarão o conteúdo dinâmico a cada requisição de página.

Entretanto, e como no WordPress, nós podemos implementar a página de erros e a do componente (para impressão)&nbsp;separadamente&nbsp;em&nbsp;arquivos semelhantes chamados de&nbsp;_error.php_ e _component.php_, respectivamente, mas aqui nos concentraremos no básico, ok?

O&nbsp;conteúdo dinâmico&nbsp;nada mais é do que o&nbsp;código&nbsp;HTML gerado pelo Joomla! para as partes do site que dependem das páginas específicas, ou seja, que podem mudar de uma página para outra. Ele&nbsp;pode ser:

  * o&nbsp;**componente**&nbsp;da página, isto é, o conteúdo principal da página;
  * o conteúdo padrão do **elemento `<head>`**&nbsp;da página, como folhas de estilos, scripts e meta elementos;
  * os **módulos**, de acordo com suas configurações de visibilidade;
  * as possíveis&nbsp;**mensagens** de sistema e de erros de&nbsp;requisição de página.

Por exemplo: através do Gerenciador de Menus do painel de administração, podemos&nbsp;criar uma página no menu principal&nbsp;para exibir um único artigo&nbsp;selecionando a opção &#8220;Artigos > Único Artigo&#8221; (componente nativo de conteúdo) como o tipo de item de menu. Ao acessar a página através do item correspondente no menu principal, o Joomla! processará o código HTML daquele componente na parte identificada para o processamento de&nbsp;componente no modelo —&nbsp;através daquelas declarações próprias&nbsp;do Joomla!. É assim que criamos páginas simples com o&nbsp;Joomla!.

Ou ainda,&nbsp;através do Gerenciador de Módulos, podemos criar um módulo para ocupar determinada&nbsp;posição&nbsp;nas páginas do site — também identificada por aquelas declarações próprias&nbsp;do Joomla! no&nbsp;modelo — e configurar sua visibilidade — o que é exclusividade dos módulos&nbsp;— apenas para a&nbsp;página inicial. Assim, ao&nbsp;acessar a página inicial,&nbsp;o Joomla! processará&nbsp;o código HTML daquele módulo naquela determinada posição, mas ao&nbsp;acessar as páginas internas, isso não acontecerá.&nbsp;Em outras palavras, o Joomla! só &#8220;carregará&#8221; o módulo na página inicial. Simples, não?

Mas&nbsp;afinal, o que&nbsp;são essas &#8220;declarações próprias do Joomla!&#8221;?

### As declarações JDOC

O Joomla! possui seus próprios métodos de processamento de conteúdo dinâmico chamados de&nbsp;**declarações JDOC**, que possuem mais ou menos essa cara:

<pre class="lang-php">&lt;jdoc:include type="component" /&gt;</pre>

Nas declarações JDOC, o&nbsp;uso das aspas duplas e do espaço antes do fechamento `/>`&nbsp;é obrigatório. Além disso, devemos sempre informar o tipo de conteúdo dinâmico a ser processado através do atributo `type`. No exemplo acima, o Joomla! processaria o componente das páginas específicas no lugar da declaração. Os possíveis valores para o atributo `type`&nbsp;são:

#### Component

Deve ser declarado apenas uma vez no elemento `<body>` do modelo&nbsp;para processar&nbsp;o conteúdo principal da página.

<pre class="lang-php">&lt;jdoc:include type="component" /&gt;</pre>

#### Head

Deve ser declarado apenas uma vez no elemento `<head>` do&nbsp;modelo&nbsp;para processar seu respectivo conteúdo padrão da página, como folhas de estilo, scripts e meta elementos.

<pre class="lang-php">&lt;jdoc:include type="head" /&gt;</pre>

#### Message

Deve ser declarado apenas uma vez no elemento `<body>` do modelo&nbsp;para processar as possíveis&nbsp;mensagens de sistema e de erros de requisição de página.

<pre class="lang-php">&lt;jdoc:include type="message" /&gt;</pre>

#### Module e modules

Pode ser declarado várias vezes no&nbsp;modelo&nbsp;para processar&nbsp;os módulos, de acordo com suas configurações de visibilidade. Aqui, também é obrigatório identificarmos aquelas posições que&nbsp;antecipamos pelo nome no arquivo&nbsp;_templateDetails.xml_ através do atributo `name`.

O tipo `module` define uma posição&nbsp;do modelo que poderá ser ocupada por um e apenas um módulo. Nesse caso, o atributo `title` se refere ao título atribuído&nbsp;para o módulo no Gerenciador de Módulos. Veja o&nbsp;exemplo para o módulo que exibe o menu:

<pre class="lang-php">&lt;jdoc:include type="module" name="mainmenu" title="Menu" /&gt;</pre>

Já o&nbsp;tipo `modules` define uma posição mais genérica do modelo que poderá ser ocupada por vários módulos —&nbsp;como uma sidebar, por exemplo. Nesse caso, o atributo `title` não é necessário.

Observe que para <a title="Criando Sidebar Dinâmica no WordPress" href="http://tableless.com.br/criando-sidebar-dinamica-no-wordpress/" target="_blank">criar&nbsp;uma sidebar dinâmica&nbsp;no WordPress</a>, normalmente&nbsp;registramos a posição&nbsp;no arquivo _functions.php_ e adicionamos&nbsp;o seguinte trecho em algum lugar do arquivo _sidebar.php_:

<pre class="lang-php">&lt;div id="sidebar" role="complementary"&gt;
  &lt;?php dynamic_sidebar( 'aside' ); ?&gt;
&lt;/div&gt;</pre>

No&nbsp;Joomla!, para a mesma finalidade, registramos&nbsp;a posição no arquivo _templateDetails.xml_ e adicionamos&nbsp;o seguinte trecho no&nbsp;modelo:

<pre class="lang-php">&lt;aside id="sidebar" role="complementary"&gt;
   &lt;jdoc:include type="modules" name="aside" /&gt;
&lt;/aside&gt;</pre>

#### Resumo das declarações JDOC

Podemos, então, esquematizar as declarações JDOC na seguinte tabela:

<table>
  <tr>
    <th style="text-align: left">
      Tipo
    </th>
    
    <th style="text-align: left">
      Função
    </th>
  </tr>
  
  <tr>
    <td>
      <code>component</code>
    </td>
    
    <td>
      Carrega o conteúdo principal da página.
    </td>
  </tr>
  
  <tr>
    <td>
      <code>head</code>
    </td>
    
    <td>
      Carrega folhas de estilo, scripts e meta elementos padrões da página.
    </td>
  </tr>
  
  <tr>
    <td>
      <code>message</code>
    </td>
    
    <td>
      Carrega, não necessariamente, mensagens de sistema e de erros de requisição de página.
    </td>
  </tr>
  
  <tr>
    <td>
      <code>module</code>
    </td>
    
    <td>
      Carrega, não necessariamente, um único módulo na posição e de título atribuídos.
    </td>
  </tr>
  
  <tr>
    <td>
      <code>modules</code>
    </td>
    
    <td>
      Carrega, não necessariamente, um ou vários módulos na posição atribuída.
    </td>
  </tr>
</table>

### Modelo básico

Apresentadas as declarações JDOC, já podemos implementar um&nbsp;modelo básico com&nbsp;marcação semântica sugerida:

<pre class="lang-php">&lt;?php defined('_JEXEC') or die('Acesso restrito!'); ?&gt;
&lt;!DOCTYPE html&gt;
&lt;html lang="&lt;?php echo $this-&gt;language; ?&gt;"&gt;
&lt;head&gt;
  &lt;jdoc:include type="head" /&gt;
  &lt;link rel="stylesheet" href="&lt;?php echo $this-&gt;baseurl; ?&gt;/templates/&lt;?php echo $this-&gt;template; ?&gt;/css/style.css" type="text/css" /&gt;
&lt;/head&gt;
&lt;body&gt;
  &lt;header&gt;
    &lt;h1&gt;&lt;?php echo $this-&gt;title; ?&gt;&lt;/h1&gt;
    &lt;nav&gt;&lt;jdoc:include type="module" name="mainmenu" title="Menu" /&gt;&lt;/nav&gt;
  &lt;/header&gt;
  &lt;section id="content"&gt;
     &lt;article role="main"&gt;
       &lt;jdoc:include type="message" /&gt;
       &lt;jdoc:include type="component" /&gt;
     &lt;/article&gt;
     &lt;aside role="complementary"&gt;
       &lt;jdoc:include type="modules" name="aside" /&gt;
     &lt;/aside&gt;
  &lt;/section&gt;
&lt;/body&gt;
&lt;/html&gt;</pre>

#### Proteção contra acesso direto

Na primeira linha, protegemos o arquivo contra o acesso direto. Funciona assim: o&nbsp;Joomla! define uma constante chamada **_JEXEC** que marca uma entrada segura de acesso aos arquivos através do _/index.php_&nbsp;na raiz da instalação; se, portanto, o arquivo&nbsp;_/templates/meunovotemplate/index.php_&nbsp;for&nbsp;acessado diretamente, o Joomla! verificará que a constante não foi definida e&nbsp;não exibirá informações em mensagens de erros que muito provavelmente ocorrerão&nbsp;e&nbsp;que podem expor a instalação para mal-intencionados de plantão — é exibida a mensagem &#8220;Acesso restrito!&#8221; que definimos.

Com o&nbsp;WordPress&nbsp;é quase a mesma coisa: a diferença é que a&nbsp;constante&nbsp;se chama&nbsp;**ABSPATH** e é&nbsp;definida mais especificamente no arquivo _/wp-load.php_ (o _/index.php_ inclui o _/wp-blog-header.php_, que por sua vez inclui o _/wp-load.php_&nbsp;— todos na raiz da instalação). A nível de curiosidade, aqui no Tableless não exibimos nenhuma mensagem para as tentativas de acesso direto aos arquivos.

#### Processando mais&nbsp;conteúdo dinâmico

Na&nbsp;terceira&nbsp;linha, definimos o idioma da página dinamicamente&nbsp;com o trecho&nbsp;`<?php echo $this->language; ?>`, que retorna via PHP o código HTML do idioma definido para&nbsp;o site no Gerenciador de Idiomas do painel de administração.&nbsp;Também utilizamos essa técnica para informar o endereço da folha de estilo _style.css_:

<pre class="lang-php">&lt;link rel="stylesheet" href="<strong>&lt;?php echo $this-&gt;baseurl; ?&gt;</strong>/templates/<strong>&lt;?php echo $this-&gt;template; ?&gt;</strong>/css/style.css" type="text/css" /&gt;</pre>

Assim, além das declarações JDOC, o Joomla! também processa essas&nbsp;propriedades do site disponíveis a partir do template, o que&nbsp;minimiza a sua manutenção —&nbsp;já que não precisamos ficar editando o modelo toda vez que mudarmos&nbsp;o título&nbsp;do site, ou o domínio, idioma, etc. Os nomes para retornar as propriedades mais importantes são:

  * **baseurl:**&nbsp;o domínio do&nbsp;site (ex.: http://www.tableless.com.br);
  * **language:**&nbsp;o código HTML do idioma definido para o site&nbsp;(ex.: pt-br);
  * **template:**&nbsp;o nome do diretório do template atual&nbsp;do site (ex.: meunovotemplate);
  * **title:**&nbsp;o título do site;
  * **description:**&nbsp;a descrição do site.

<a title="Propriedades do site Joomla! disponíveis a partir do template" href="https://docs.joomla.org/Objects,_methods_and_properties_available_from_your_template" target="_blank">Consulte a lista completa das propriedades disponíveis</a>.

Observe que as declarações JDOC somadas a&nbsp;essas propriedades&nbsp;estão para os templates do Joomla! assim como as **template tags**&nbsp;estão para os temas do WordPress. Bacana, né?

### Componente só nas páginas internas

Podemos ainda fazer com que o Joomla! processe apenas o componente das páginas internas&nbsp;com o auxílio de um módulo. O truque é definir sua visibilidade&nbsp;apenas para a&nbsp;página inicial&nbsp;e&nbsp;daí, através de operadores condicionais e do&nbsp;método `int countModules( $condition )`, que verifica a visibilidade do módulo na página, controlamos manualmente o que carregar na página inicial e o que carregar nas páginas internas. Segue uma sugestão de código:

<pre class="lang-php">&lt;article role="main"&gt;

  &lt;!-- conteúdo exibido em todas as páginas --&gt;

  &lt;?php if ($this-&gt;countModules( 'slideshow' )) :
  // se o módulo estiver visível na página ?&gt;

  &lt;div id="home"&gt;
    &lt;jdoc:include type="module" name="slideshow" title="Slideshow" /&gt;
    &lt;!-- conteúdo exibido somente na página inicial --&gt;
  &lt;/div&gt;

  &lt;?php endif; ?&gt;
  &lt;?php if (!$this-&gt;countModules( 'slideshow' )) :
  // se o módulo não estiver visível na página ?&gt;

  &lt;div id="inner"&gt;
    &lt;jdoc:include type="component" /&gt;
    &lt;!-- conteúdo exibido somente nas páginas internas --&gt;
  &lt;/div&gt;

  &lt;?php endif; ?&gt;

&lt;/article&gt;</pre>

No exemplo acima, com a&nbsp;configuração de visibilidade&nbsp;do módulo &#8220;slideshow&#8221; apenas para&nbsp;a página inicial, o componente da página inicial não será processado quando ela for&nbsp;acessada — embora o back-end do Joomla! ainda entenda que a página inicial se refere àquele&nbsp;componente. Mas lembre-se: a página inicial é a principal página do seu site e o componente, seu principal conteúdo. Pelo que você iria substituí-lo? Será que o Google e os seus coleguinhas iriam gostar?

## Instalando o template no Joomla!

Existem quatro&nbsp;formas de instalar extensões no Joomla!: pelo JED, enviando um pacote de arquivos, a partir do diretório da instalação ou&nbsp;a partir de um URL. Em&nbsp;nosso caso, optaremos por enviar&nbsp;um pacote de arquivos: é só compactar o conteúdo do diretório do template&nbsp;(_.zip_, _.tar.gz_ ou _tar.bz2_) e fazer o upload no Joomla! pelo Gerenciador de Extensões do painel de administração:

[<img class="alignnone size-full wp-image-48873" src="http://tableless.com.br/uploads/2015/05/instalacao-de-extensoes-no-joomla.png" alt="Instalação de extensões no Joomla!" width="900" height="500" />][1]

Os arquivos e subdiretórios do template serão colocados em um diretório com o mesmo nome do arquivo compactado em _/templates/_. Além disso,&nbsp;o template será listado no Gerenciador de Temas — com aquelas informações que informamos no arquivo&nbsp;_templateDetails.xml&nbsp;—,_&nbsp;em que&nbsp;deve ser definido&nbsp;como **tema padrão do site**.

Após a instalação, você ainda pode continuar editando&nbsp;o seu template sem nenhum problema. Considere, por exemplo, adicionar um script ao site: crie&nbsp;diretamente um diretório&nbsp;para scripts no diretório do template instalado&nbsp;(e não esqueça do _index.html_ em branco), informe-os no respectivo&nbsp;_templatesDetails.xml_ (como boa prática), adicione-os ao modelo&nbsp;e pronto!

Go ahead!&nbsp;Você é livre para editar o template e conferir o resultado em tempo real — inclusive editar a geração do código HTML pelo Joomla! para o conteúdo dinâmico com **overrides**, mas isso é assunto de&nbsp;outro artigo.

## Conclusão

A criação de&nbsp;um template básico para o Joomla!, como se vê, não&nbsp;é nenhuma novidade para quem já desenvolve temas para o WordPress.&nbsp;É claro que esta é&nbsp;apenas uma introdução aos templates do&nbsp;Joomla! e não aborda&nbsp;tudo o que podemos fazer. Podemos, por exemplo, manipular o conteúdo dinâmico do elemento `<head>`&nbsp;(como retirar scripts padrões desnecessários em alguns casos),&nbsp;definir parâmetros para&nbsp;o template configuráveis pelo&nbsp;painel de administração (como nos temas do WordPress a partir da versão 3.4), permitir a mudança de&nbsp;idioma do próprio modelo (para sites multilíngues) e muito mais! Aqui, porém, nos contentamos com a&nbsp;criação de um template que você poderá usar como base em&nbsp;seus próximos projetos com o Joomla!.

[Baixe o template][2].

E até a próxima pessoal!

### Referências

  * <a title="Documentação do Joomla!" href="http://docs.joomla.org" target="_blank">Documentação do Joomla!</a>
  * <a title="Documentação do WordPress" href="http://codex.wordpress.org" target="_blank">Documentação do WordPress</a>

 [1]: http://tableless.com.br/uploads/2015/05/instalacao-de-extensoes-no-joomla.png
 [2]: http://tableless.com.br/uploads/2015/05/template.zip