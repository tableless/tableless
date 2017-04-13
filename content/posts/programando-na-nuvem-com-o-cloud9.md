---
title: Programando na nuvem com o cloud9
author: Daniel Schmitz
type: post
date: 2015-10-01
url: /programando-na-nuvem-com-o-cloud9/
categories:
  - PHP

---
Durante muito tempo, tive a necessidade de programar em qualquer lugar – seja em casa, trabalho ou em uma viagem. Sempre consegui suprir essa necessidade através de um terminal/console – nada que um ssh não resolvesse. Mas após conhecer a plataforma de desenvolvimento &#8220;cloud9&#8221; muitas funcionalidades foram otimizadas e, após usá-la por mais de 6 meses, tive que compartilhar com todas as suas vantagens.

O cloud9 é basicamente uma IDE de desenvolvimento 100% na Web, que possui diversas tecnologias previamente instaladas: _php, mysql, python, rails, ruby, node,_ entre outras. Através do seu navegador é possível entrar na IDE e começar a programar na sua linguagem preferida, executar e debugar os programas criados. Além disso, você pode instalar outras tecnologias através do **apt-get**, já que você está operando, na verdade, um sistema Linux – Ubuntu.

# Quanto custa?

O cloud9 é gratuito se você desenvolver sozinho e não necessitar de recursos avançados. Após 6 meses utilizando o cloud9, ainda não tive a necessidade de migrar para um plano pago. Você também poderá testar o quanto quiser no plano free e poderá migrar para algo melhor, caso precise.

O plano gratuito é baseado em um conceito chamado **sessão**, onde as páginas que você acessa, estão disponíveis enquanto você estiver logado. Quando você sair ou após algumas horas sem logar, a sua sessão é fechada e as páginas que antes poderiam ser acessadas através de uma URL, não estarão mais disponíveis. O que isso significa? Se você criar uma página web para ser exibida à outra pessoa externa (um cliente por exemplo), esta página poderá não estar acessível no momento em que o seu cliente acessá-la. Lembre-se que o cloud9 é uma ferramenta de desenvolvimento web, e não um servidor de aplicações. Use-o para desenvolver e/ou aprender uma tecnologia; para deploy, certamente, você usará um outro servidor.

# Recursos

Vamos enumerar a seguir os recursos disponíveis do cloud9:

  * **Linguagens suportadas**: Apache httpd (PHP), Node, Python, Ruby, Rails, Go, CofeeScript, Julia, Mocha, Shell script;
  * **Banco de dados**: MySql, MongoDB, CouchDB, PostgreSQL, Redis, SQLite;
  * **Frameworks**:     AngularJS, Bootstrap, Django, Express, Ghost, Hadoop, Ionic, jQuery, Jekyll, KoaJS, Laravel, Meteor, Symfony, Drupal, Joomla, WordPress;
  * **Browser**: Chrome, IE, Firefox, Opera e outros – Existem diversos browsers para que você possa testar a sua aplicação sem a necessidade de instalar cada um deles;
  * **Terminal/console/bash**: pode-se abrir um terminal e executar comandos que você usaria em um terminal linux. Pode-se utilizar apt-get para instalar outros programas;
  * **Recursos da IDE**: Além de dezenas de linguagens suportadas, os mesmos recursos de uma IDE comum estão disponíveis na IDE virtual. Funcionalidades como complementação de código, pular para definição, busca por classes e refatoração estão disponíveis. A IDE lembra muito o sublime text, com dezenas de recursos como temas, split view, alterar cores e definir macros, snippets. A IDE possui recursos do zen coding também;
  * **Debugger**: É possível debugar Javascript. Outras linguagens não são suportadas, infelizmente;
  * **Atalhos**: Pode-se utilizar os atalhos do teclado para operar a IDE. Lembra do poderoso CTRL+P do Sublime Text? Ele está presente aqui também! É possísvel, por exemplo, emular o VIM para edição, ou emular outra editor como o emacs.

# Como criar uma conta no cloud9

Acesse a url <a href="https://c9.io/" target="_blank" rel="nofollow">https://c9.io/</a> e clique no botão SIGN UP, preenchendo o formulário com o seu login, nome, senha e e-mail. Após criar a conta, clique no link “<a class="dashboardLink" href="https://c9.io/dashboard.html" target="_blank" rel="nofollow">Go to your dashboard</a>” e clique no recém criado _workspace_ (área de trabalho). Quando você iniciar o workspace “demo-project”, uma área de trabalho conforme a figura a seguir é criada:

[<img class="alignnone size-full wp-image-51096" src="http://tableless.com.br/uploads/2015/09/AAEAAQAAAAAAAAa1AAAAJDMwYTdiNWNjLTM1NmQtNDFlMy05YWMyLWYzMmNhZTViOWM1NA.png" alt="AAEAAQAAAAAAAAa1AAAAJDMwYTdiNWNjLTM1NmQtNDFlMy05YWMyLWYzMmNhZTViOWM1NA" width="800" height="580" />][1]

Em 1, temos a área destinada a abrir arquivos e navegadores, conforme a necessidade. Pode-se, inclusive, “desgrudar” a aba da barra e arrastá-la para o canto da tela, forma a produzir uma nova área de abas. Em 2 temos a árvore de arquivos do seu _workspace_. Perceba que temos pastas “PHP”, “Ruby” etc. Estas pastas apenas indicam que podemos trabalhar com diversas tecnologias ao mesmo tempo. Não é necessário, por exemplo, colocar todos os seus arquivos PHP na pasta. Em 3 temos um menu horizontal com diversas opções, dentre elas o botão “run”, usado para executar projetos e arquivos. Em 4 temos algumas configurações em relação ao tema, layout entre outras opções.

# Testando o cloud9

Após a instalação, vamos testar um arquivo PHP já existente no workspace. Para isso, abra a pasta “php” e clique duas vezes no arquivo index.php. Ele será aberto como uma aba na IDE. Após abrir o arquivo, você verá algo do tipo:

[<img class="alignnone size-full wp-image-51097" src="http://tableless.com.br/uploads/2015/09/2015-09-03-19_47_05-Email.png" alt="2015-09-03 19_47_05-Email" width="885" height="442" />][2]

Após o apache iniciar, uma URL surge na qual você pode clicá-la. Com isso, uma nova aba será aberta e você poderá conferir o resultado do código PHP gerado. Como tarefa, crie um novo arquivo na pasta PHP chamado “phpinfo.php”, e adicione o seguinte conteúdo:

<pre>&lt;?php
phpinfo();
</pre>

[<img class="alignnone size-full wp-image-51098" src="http://tableless.com.br/uploads/2015/09/AAEAAQAAAAAAAAYLAAAAJDFmZGM4MDllLWViMTYtNDAyOC1iZDY0LTc3OTQ3NDM0NWViNA.png" alt="AAEAAQAAAAAAAAYLAAAAJDFmZGM4MDllLWViMTYtNDAyOC1iZDY0LTc3OTQ3NDM0NWViNA" width="800" height="458" />][3]

# Utilizando o console/bash

Na parte inferior da IDE existe uma aba chamada _bash,_ a qual você pode utilizar para realizar as mais diferentes ações. A maioria dos comandos Linux que você utiliza em uma shell no seu computador também pode ser usado aqui, conforme o exemplo a seguir:

[<img class="alignnone size-full wp-image-51099" src="http://tableless.com.br/uploads/2015/09/AAEAAQAAAAAAAANpAAAAJGRmODIzMTQ5LTg2NTgtNDliMC04NDAyLTc5Njk1ZTk4MGRmYg.png" alt="AAEAAQAAAAAAAANpAAAAJGRmODIzMTQ5LTg2NTgtNDliMC04NDAyLTc5Njk1ZTk4MGRmYg" width="800" height="638" />][4]

# Diversas tecnologias prontas para uso

Uma das vantagens do cloud9, além de você ter uma IDE nativa em qualquer lugar do mundo (basta apenas ter acesso à Internet), é poder utilizar diversas tecnologias prontas para uso. Por exemplo, enjoou do PHP e quer testar o Rails? Basta abrir o terminal e criar o seu projeto:

[<img class="alignnone size-full wp-image-51100" src="http://tableless.com.br/uploads/2015/09/AAEAAQAAAAAAAALfAAAAJDg2ZTA0ZTQyLWIwMjctNGVjMi1iNWFjLWUzM2FkZmFjZTQ5NQ.png" alt="AAEAAQAAAAAAAALfAAAAJDg2ZTA0ZTQyLWIwMjctNGVjMi1iNWFjLWUzM2FkZmFjZTQ5NQ" width="630" height="367" />][5]

# Para saber mais:

O cloud9 tem uma boa documentação neste endereço:<a href="https://docs.c9.io/v1.0/docs" target="_blank" rel="nofollow">https://docs.c9.io/v1.0/docs</a>. Caso tenha alguma dúvida, deixe um comentário!

&nbsp;

&nbsp;

&nbsp;

&nbsp;

&nbsp;

 [1]: http://tableless.com.br/uploads/2015/09/AAEAAQAAAAAAAAa1AAAAJDMwYTdiNWNjLTM1NmQtNDFlMy05YWMyLWYzMmNhZTViOWM1NA.png
 [2]: http://tableless.com.br/uploads/2015/09/2015-09-03-19_47_05-Email.png
 [3]: http://tableless.com.br/uploads/2015/09/AAEAAQAAAAAAAAYLAAAAJDFmZGM4MDllLWViMTYtNDAyOC1iZDY0LTc3OTQ3NDM0NWViNA.png
 [4]: http://tableless.com.br/uploads/2015/09/AAEAAQAAAAAAAANpAAAAJGRmODIzMTQ5LTg2NTgtNDliMC04NDAyLTc5Njk1ZTk4MGRmYg.png
 [5]: http://tableless.com.br/uploads/2015/09/AAEAAQAAAAAAAALfAAAAJDg2ZTA0ZTQyLWIwMjctNGVjMi1iNWFjLWUzM2FkZmFjZTQ5NQ.png