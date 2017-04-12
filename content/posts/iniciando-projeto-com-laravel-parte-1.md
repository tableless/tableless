---
title: Iniciando projeto com laravel – parte 1
author: Tailo Mateus Gonsalves
type: post
date: 2017-04-04
stick: yes
excerpt: Iniciando um projeto com Laravel
categories:
  - Código
---


Seja bem vindo a série Iniciando projeto com laravel, na primeira parte veremos como criar um projeto, as principais pastas da estrutura e configuração do banco de dados.

## CONFIGURAÇÕES GERAIS

Para iniciarmos precisamos configurar algumas coisas.

Como o foco não é banco de dados, utilizaremos o xampp. Você pode baixá-lo aqui: <a href="https://www.apachefriends.org/pt_br/download.html">https://www.apachefriends.org/pt_br/download.html</a>

Para configurar o laravel:

Windows: <a href="https://gist.github.com/Turini/4949f23350ae2297c933">https://gist.github.com/Turini/4949f23350ae2297c933</a>
Linux: <a href="https://gist.github.com/Turini/843fa49af3ada5599c69">https://gist.github.com/Turini/843fa49af3ada5599c69</a>
Mac: <a href="https://gist.github.com/Turini/94ed27b4f169c66349d2">https://gist.github.com/Turini/94ed27b4f169c66349d2</a>

## CRIANDO O PROJETO

Muito bem, agora que tudo esta configurado, abra seu terminal. Digite laravel new NomeProjeto. Pronto, isso mesmo, seu projeto já esta criado. Para testá-lo, inicie seu apache do xampp e digite no terminal php artisan serve, nesse momento já pode testar sua aplicação em localhost.

<img class="alignnone wp-image-57488" src="uploads/2017/03/Sem-título.png" alt="" width="648" height="297" />

Mas o que é esse artisan? Bom, ele é uma ferramenta de linha de comando, inclusa no framework.

Maiores informações sobre o artisan e os comandos inclusos, pode consultar <a href="https://laravel.com/docs/5.4/artisan">https://laravel.com/docs/5.4/artisan</a>

## ESTRUTURAS DE PASTAS

Após criar o projeto, várias pastas foram criadas, vou comentar sobre as mais importantes.

app: Aqui fica o código principal da sua aplicação, seus modelos e controllers.

config: Nessa pasta fica toda a configuração, como, banco de dados, e-mails, entre outros.

public: Geralmente aqui fica seu arquivo index.php, as imagens, css e o js.

vendor: Possui o source code do laravel, plugins e dependências. Tudo que for usado de terceiros, como, frameworks e bibliotecas devem ficar aqui.

Você pode descobrir mais sobre a estrutura aqui <a href="https://laravel.com/docs/5.4/structure">https://laravel.com/docs/5.4/structure</a>

## BANCO DE DADOS

O laravel tem interações possíveis com 4 bancos de dados, entre eles, MySQL, Postgres, SQLite, SQL Server. Na versão atual 5.4, o default é o MySQL. Toda a configuração fica na pasta config e no arquivo database.php. E tudo fica em um array como este:

<pre class="lang-php">
'mysql' =&gt; [
'driver' =&gt; 'mysql',
'host' =&gt; env('DB_HOST', 'localhost'),
'database' =&gt; env('DB_DATABASE', 'NomeDoBanco'),
'username' =&gt; env('DB_USERNAME', 'root'),
'password' =&gt; env('DB_PASSWORD', ''),
]
</pre>

Basicamente, é aqui que você deve inserir os seus dados. Além dessas chaves, é possível configurar outras, que não serão mencionadas nesse artigo, mas que podem ser vistas aqui <a href="https://laravel.com/docs/5.4/database">https://laravel.com/docs/5.4/database</a>

OBS: Em um projeto real, o ideal é colocar as configurações do banco de dados no arquivo .env, esse arquivo é mantido fora do controle de versão. Dessa forma, cada desenvolvedor vai possuir seu próprio arquivo e mantém as configurações do servidor em produção de forma sigilosa.

Para saber mais: <a href="https://laravel.com/docs/5.4/configuration">https://laravel.com/docs/5.4/configuration</a>

## CONCLUSÃO

Para iniciar um projeto é muito simples, com poucos passos já esta tudo configurado. Ele facilita muito o desenvolvimento, deixando o processo mais veloz. Nada impede de fazer com php puro, mas caso queira economizar algum tempo, esse framework se torna uma boa forma, nas referências, deixo algumas razões para usá-lo. Ficamos por aqui, nas próximas partes veremos como configurar e manipular as rotas, detalhar como funciona o padrão MVC (Model, View, Controller) no laravel.

## PARA SABER MAIS:

Criando um projeto: <a href="http://laravel-recipes.com/recipes/30/creating-a-laravel-project">http://laravel-recipes.com/recipes/30/creating-a-laravel-project</a>

Documentação do framework: <a href="https://laravel.com/docs/5.4">https://laravel.com/docs/5.4</a>

O que é o laravel: <a href="https://code.tutsplus.com/tutorials/getting-started-with-laravel--cms-25386">https://code.tutsplus.com/tutorials/getting-started-with-laravel--cms-25386</a>

10 razões para usar laravel: <a href="http://acadtec.com.br/site/blog/item/61-10-razoes-para-usar-laravel.html">http://acadtec.com.br/site/blog/item/61-10-razoes-para-usar-laravel.html</a>

Arquivo .env: <a href="http://pt.stackoverflow.com/questions/156660/laravel-5-arquivo-env">http://pt.stackoverflow.com/questions/156660/laravel-5-arquivo-env</a>