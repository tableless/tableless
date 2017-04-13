---
title: "Yii Framework - um framework PHP profissional, rápido e seguro!"
author: Diego do Nascimento
date: 2014-08-03
categories:
  - Artigos
  - Back-end
  - PHP

---
Todo desenvolvedor ao longo de sua carreira, em algum momento, faz o uso de frameworks para complementar seus projetos, reduzir tempo de produção e prover na maioria dos casos, um código limpo, profissional e de fácil manutenção.

Hoje lhes apresento o <a href="http://www.yiiframework.com/" target="_blank">Yii Framework</a>, um framework Open-Source PHP com alto poder de desempenho e escalabilidade.
  
Chegou a sua versão histórica Yii 1.0 em 2008 e, desde então, sua popularidade entre os desenvolvedores tem crescido cada vez mais.

O Framework possui um excelente suporte a MVC, DAO / Active Record, I18N (Internationalization) / L10N (Localization), Cache, Autenticação e Controle de acesso (RBAC), Testes unitários, Gerador de códigos automáticos, Skinning and Theming, Jquery / solicitações Ajax integrado aos widgets do Yii, Web Services (WSDL) e muito mais.

Sua documentação é bem rica e possui um fluxo expressivo de desenvolvedores em seu fórum.
  
Eis suas principais características:

### Rápido

A arquitetura do Yii permite que o mesmo carregue somente o necessário para aplicação no presente momento e, em conjunto com o suporte a cache (<a href="http://www.php.net/manual/pt_BR/book.apc.php" target="_blank">APC</a>), consegue um RPS (Requisição por Segundo) bastante interessante.

&nbsp;

<img class="aligncenter wp-image-43331 size-full" src="http://tableless.com.br/uploads/2014/07/performance-20090131.png" alt="PHP Framework Performance Comparison" width="769" height="484" srcset="uploads/2014/07/performance-20090131.png 769w, uploads/2014/07/performance-20090131-220x139.png 220w, uploads/2014/07/performance-20090131-400x251.png 400w" sizes="(max-width: 769px) 100vw, 769px" />

No site oficial do <a href="http://www.yiiframework.com/performance/" target="_blank">Yii</a> possui uma descrição mais detalhada sobre seu desempenho. Vale a pena dar uma olhada!

### Seguro

Um framework com um excelente desempenho não é nada se sua segurança é fraca, não é mesmo?

O Yii por padrão faz o tratamento/validações de entrada e saída de dados, oferece suporte a ataques SQL Injection, Cross-site scripting (XSS), CSRF (Cross-Site Request Forgery), Cookie Attack e entre outros.

### Profissional

Yii segue o padrão MVC em sua estrutura, garantindo a separação entre camadas lógicas e camadas de apresentação do projeto a ser desenvolvido. Ele auxilia o desenvolvedor a ter um código mais limpo e reutilizável (DRY &#8211; _Don&#8217;t repeat yourself_) sem grandes esforços, supre a elaboração de sites simples bem como aplicações extremamente complexas, sendo necessário se preocupar apenas com tarefas específicas do projeto.

Outro fator importante é que ele aceita muito bem integrações com códigos de terceiros, como por exemplo, PEAR, Codeigniter, Zend Framework&#8230;

Enfim, o Yii é uma excelente opção para quem esta buscando um framework intuitivo, flexível e profissional. Segundo o site oficial, <a href="http://www.yiiframework.com/about/" target="_blank"><i>&#8220;Yii helps Web developers build complex applications and deliver them on-time.&#8221;</i></a> traduzindo seria _&#8220;Yii ajuda os desenvolvedores a construir aplicações complexas e entregá-las no prazo.&#8221;_.

&nbsp;

## INSTALAÇÃO

Para instalar o Yii, faça o download do framework em sua versão estável no <a href="http://www.yiiframework.com/download/" target="_blank">site oficial</a>, descompacte os arquivos em um diretório acessível à Web ou em seu servidor local. O servidor deverá ter no mínimo a versão 5.1 do PHP instalada ou posterior.

Você poderá realizar o download da última versão do framework usando o repositório do GitHub através da URL:

<pre class="lang-html">git@github.com:yiisoft/yii.git</pre>

ou via SVN usando:

<pre class="lang-html">svn checkout https://github.com/yiisoft/yii/trunk/ yii</pre>

Após descompactar os arquivos, devemos verificar se o servidor, bem como sua configuração, atende os requisitos básicos para que o Yii funcione corretamente. Para isso, o Yii preparou um verificador de requisitos que emite o resultado final sobre as condições do ambiente em que o mesmo está instalado.

Você poderá acessar este verificador da seguinte forma:

Partindo o princípio que o Yii foi instalado em um servidor local, em seu navegador web, acesse a seguinte URL:

<pre class="lang-html">http://127.0.0.1/yii/requirements/</pre>

Ao acessar essa URL, o verificador de requisitos entrará em ação verificando se o servidor possui as configurações necessárias para que o Yii funcione adequadamente.

&nbsp;

## CRIANDO SUA PRIMEIRA APLICAÇÃO

Com o servidor devidamente configurado e validado pelo Yii, iremos criar nossa primeira aplicação.

O Yii possui um gerador de código muito poderoso que permite realizarmos algumas tarefas de maneira automatizada. Criaremos uma aplicação completa com controle de acesso e sem escrever uma linha de código PHP. Veja como:

Através da linha de comando iremos executar o arquivo &#8220;yiic.php&#8221;. Para quem está utilizando MAC OS, Unix ou Linux, execute a seguinte comando:

<pre class="lang-html">php caminho/para_a/pasta/do/yii/framework/yiic.php webapp caminho/para_a/nova/pasta/hello_world</pre>

Onde &#8220;/hello_world&#8221; seria o nome da pasta na qual irá conter os arquivos de nossa primeira aplicação web.

### Certo! Mas eu uso Windows? E agora?

Se você tentar executar este comando no prompt do Windows, o mesmo não irá reconhece-lo corretamente. Antes, devemos realizar algumas configurações necessárias para que o mesmo funcione.

Devemos adicionar à variável de ambiente do Windows, o caminho de instalação do PHP.

Por exemplo, caso tenha instalado o WampServer como seu ambiente de desenvolvimento, o caminho para a pasta de instalação do PHP seria semelhante ao seguinte diretório:

<pre class="lang-html">C:\wamp\bin\php\php5.3.13</pre>

Caso o ambiente de desenvolvimento seja o Xampp por exemplo, o caminho para a pasta seria semelhante a:

<pre class="lang-html">C:\xampp\php</pre>

O importante é encontrar o caminho correto até a pasta de instalação do PHP.

No Windows, em &#8220;Propriedades do Sistema” e com a aba &#8220;Avançado&#8221; ativa, clique no botão &#8220;Variáveis de Ambiente&#8230;&#8221;

<img class="alignnone wp-image-43327 size-full" src="http://tableless.com.br/uploads/2014/07/01.jpg" alt="Propriedades do Sistema" width="426" height="498" srcset="uploads/2014/07/01.jpg 426w, uploads/2014/07/01-118x139.jpg 118w, uploads/2014/07/01-400x467.jpg 400w" sizes="(max-width: 426px) 100vw, 426px" />

Na área &#8220;Variáveis do sistema&#8221;, editaremos a variável &#8220;Path&#8221;:

<img class="alignnone wp-image-43328 size-full" src="http://tableless.com.br/uploads/2014/07/02.jpg" alt="Variáveis do sistema" width="394" height="437" srcset="uploads/2014/07/02.jpg 394w, uploads/2014/07/02-125x139.jpg 125w" sizes="(max-width: 394px) 100vw, 394px" />

Adicione o caminho de instalação do PHP seguido de um ponto e vírgula &#8220;;&#8221; no final e confirme a edição. Veja:

<img class="alignnone wp-image-43329 size-full" src="http://tableless.com.br/uploads/2014/07/03.jpg" alt="Variáveis do sistema" width="357" height="154" srcset="uploads/2014/07/03.jpg 357w, uploads/2014/07/03-265x114.jpg 265w" sizes="(max-width: 357px) 100vw, 357px" />

Com esta alteração, basicamente estamos informando ao Windows onde ele irá localizar o arquivo php.exe. Confirme a edição, e abra o prompt de comando do Windows.

Caminhe até a pasta &#8220;framework&#8221; localizada dentro do diretório de instalação do Yii utilizando o comando &#8220;cd&#8221;:

<pre class="lang-html">cd caminho\para_a\pasta\do\yii\framework</pre>

Após estar dentro do diretório **&#8220;framework&#8221;**, digite a seguinte linha de comando no prompt do Windows:

<pre class="lang-html">yiic webapp caminho\para_a\nova\pasta\hello_world</pre>

Após a execução desta linha de comando, o Yii irá criar uma aplicação web completa na pasta **&#8220;/hello_world&#8221;** que poderá ser acessada em seu navegador web, por exemplo:

<pre class="lang-html">http://127.0.0.1/hello_world/</pre>

Veja como ficou a aplicação:

<img class="aligncenter wp-image-43330 size-full" src="http://tableless.com.br/uploads/2014/07/04.jpg" alt="Resultado final" width="1027" height="501" srcset="uploads/2014/07/04.jpg 1027w, uploads/2014/07/04-265x129.jpg 265w, uploads/2014/07/04-400x195.jpg 400w" sizes="(max-width: 1027px) 100vw, 1027px" />

## ESTRUTURA

Vamos agora analisar mais a fundo a estrutura de pastas da aplicação recentemente gerada:

<pre class="lang-html">hello_world/
   index.php                 Script de entrada da aplicação Web
   index-test.php            Script de entrada para os testes funcionais
   assets/                   Contém arquivos de recurso publicados
   css/                      Contém arquivos CSS
   images/                   Contém arquivos de imagem
   themes/                   Contém temas da aplicação
   protected/                Contém arquivos protegidos da aplicação
      yiic                   Script de linha de comando yiic
      yiic.bat               Script de linha de comando yiic para o Windows
      yiic.php               Script PHP de linha de comando yiic 
      commands/              Contém comandos 'yiic' customizados
         shell/              Contém comandos 'yiic shell' customizados
      components/            Contém componentes reutilizáveis do usuário
         Controller.php      A classe padrão para todos os controles
         UserIdentity.php    A classe 'UserIdentity' usada nas autenticações
      config/                Contém arquivos de configurações
         console.php         Configuração da aplicação console
         main.php            Configuração da aplicação Web
         text.php            Configuração para os testes funcionais
      controllers/           Contém arquivos das classes de controle
         SiteController.php  Classes de controle padrão
      data/                  Contém exemplos de banco de dados
         schema.mysql.sql    Esquemas de BD com o banco de amostra em MySQL
         schema.sqlite.sql   Esquemas de BD com o banco de amostra em SQLite
         testdrive.db        Arquivo do banco de dados de amostra do SQLite
      extensions/            Contém extensões de terceiros
      messages/              Contém mensagens traduzidas
      models/                Contém arquivos das classes de modelo
         LoginForm.php       Modelo do formulário para a ação 'login'
         ContactForm.php     Modelo do formulário para a ação 'contact'
      runtime/               Contém arquivos gerados temporariamente
      tests/                 Contém scripts para os testes
      views/                 Contém arquivos de visão dos controles e layouts
         layouts/            Contém arquivos de visão do layout
            main.php         O layout padrão para todas as páginas
            column1.php      O layout para páginas com coluna única
            column2.php      O layout para páginas com duas colunas
         site/               Contém arquivos de visão para o controle 'site'
            pages/           Contém páginas "estática"
               about.php     A visão para a página "about"
            contact.php      Visão para a ação 'contact'
            error.php        Visão para a ação 'error' (exibindo erros externos)
            index.php        Visão para a ação 'index' 
            login.php        Visão para a ação 'login' 
</pre>

Como podem notar, sua estrutura se assemelha bastante com outros frameworks MVC atuais.
  
Recomendo que explorem bem esta aplicação, pois ela demonstra o uso correto do framework.

Deem uma olhada no Controller **&#8220;SiteController.php&#8221;** localizado em **&#8220;/hello_world/protected/controllers/&#8221;**, através dele é possível entender o funcionamento completo da aplicação do início ao fim.

Para finalizar, deixo duas recomendações de livros que valem a pena a leitura:

<a href="http://www.amazon.com/dp/1849518726?tag=gii20f-20" target="_blank">Web Application Development with Yii and PHP</a>

<a href="http://www.amazon.com/dp/B00BKZHDGS?tag=gii20f-20" target="_blank">Yii Application Development Cookbook</a>