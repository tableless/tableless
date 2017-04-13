---
title: Iniciando com Symfony 2 – Parte 08
author: Candido Souza
type: post
date: 2015-04-28
excerpt: Nesse tutorial, vamos instalar e configurar o bundle Knp Paginator, para fazermos a paginação de nossos posts.
url: /iniciando-com-symfony-2-parte-08/
categories:
  - Back-end
  - O Básico
  - PHP
  - Técnicas e Práticas
tags:
  - desenvolvimento
  - framework
  - php
  - phpOO
  - Symfony
  - Symfony2
  - tutorial

---
No <a href="http://tableless.com.br/iniciando-com-symfony-2-parte-07/" title="Parte 07" target="_blank">tutorial anterior</a>, criamos um upload de imagens para servirem de capa para nossos posts, agora vamos instalar e configurar um Bundle, disponibilizado pela comunidade, para fazer a paginação de nossa página index. Para isso temos que instalar o Knp Paginator em nossa aplicação.

## Instalação do Knp Paginator

Para instalar o Knp Paginator, temos que adicioná-lo em nosso composer.json. Abra o arquivo composer.json e adicione a linha abaixo:

<pre class="lang-php">"knplabs/knp-paginator-bundle": "2.4.*@dev"
</pre>

Caso não o conheça, ou tenha dúvidas, leia este post (<a href="http://tableless.com.br/composer-um-pouco-alem-basico/" title="Composer" target="_blank">Composer para iniciantes</a>).
  
Depois de adicionado o Knp Paginator no composer, vamos instalá- lo. Entre no terminal e digite:

<pre class="lang-bash">$ composer update
</pre>

Após o Download, o Knp Paginator está instalado em nossa aplicação.

## Configurando o Knp Paginator

A primeira configuração que devemos fazer, é registrar o novo bundle instalado, para isso entre no AppKernel, caminho: app/AppKernel.php

Adicione a linha abaixo no registro de bundles:

<pre class="lang-php">new Knp\Bundle\PaginatorBundle\KnpPaginatorBundle(),
</pre>

Veja na linha 16:

<pre class="lang-php">class AppKernel extends Kernel
{
    public function registerBundles()
    {
        $bundles = array(
            new Symfony\Bundle\FrameworkBundle\FrameworkBundle(),
            new Symfony\Bundle\SecurityBundle\SecurityBundle(),
            new Symfony\Bundle\TwigBundle\TwigBundle(),
            new Symfony\Bundle\MonologBundle\MonologBundle(),
            new Symfony\Bundle\SwiftmailerBundle\SwiftmailerBundle(),
            new Symfony\Bundle\AsseticBundle\AsseticBundle(),
            new Doctrine\Bundle\DoctrineBundle\DoctrineBundle(),
            new Sensio\Bundle\FrameworkExtraBundle\SensioFrameworkExtraBundle(),
            new Tableless\CoreBundle\TablelessCoreBundle(),
            new Tableless\ModelBundle\TablelessModelBundle(),
	    new Knp\Bundle\PaginatorBundle\KnpPaginatorBundle(),
        );
...
</pre>

Pronto o Knp Paginator está registrado.
  
Agora vamos fazer as configurações padrões no Knp, para isso entre no arquivo config.yml, caminho: app/config/config.yml

No final do arquivo adicione as configurações abaixo: 

<pre class="lang-yml">knp_paginator:
    page_range: 5                      # default page range used in pagination control
    default_options:
        page_name: page                # page query parameter name
        sort_field_name: sort          # sort field query parameter name
        sort_direction_name: direction # sort direction query parameter name
        distinct: true                 # ensure distinct results, useful when ORM queries are using GROUP BY statements
    template:
        pagination: KnpPaginatorBundle:Pagination:sliding.html.twig     # sliding pagination controls template
        sortable: KnpPaginatorBundle:Pagination:sortable_link.html.twig # sort link template
</pre>

Essas configurações foram tiradas da <a href="https://github.com/KnpLabs/KnpPaginatorBundle#configuration-example" title="Documentação Knp Paginator" target="_blank">documentação do Knp Paginator</a>

## Configurando o Controller

Depois de termos feito as configurações de instalação do Knp Paginator, vamos configurar nosso controller, para isso entre no IndexControlerController, caminho: src/Tableless/CoreBundle/Controller/IndexControlerController.php

Primeiramente para pegar o número de páginas, de acordo com a quantidade de posts temos que usar o request do symfony, então vamos dar um use em Request, veja na linha 8:

<pre class="lang-php">&lt;?php

namespace Tableless\CoreBundle\Controller;

use Symfony\Bundle\FrameworkBundle\Controller\Controller;
use Sensio\Bundle\FrameworkExtraBundle\Configuration\Route;
use Sensio\Bundle\FrameworkExtraBundle\Configuration\Template;
use Symfony\Component\HttpFoundation\Request;

...
</pre>

Em nossa indexAction temos que pegar a biblioteca do paginador, passar nosso posts, pegar as páginas via request, e quantidade de posts que queremos por páginas, e retorná- los em forma de array para que nossa view possa apresentar. Em meu caso vou usar apenas três posts por página.

Veja:

<pre class="lang-php">/**
     * @Route("/", name="index")
     * @Template()
     */
    public function indexAction(Request $request)
    {
        $em = $this-&gt;getDoctrine()-&gt;getManager();

        $posts = $em-&gt;getRepository('TablelessModelBundle:Post')-&gt;findAllInOrder();

        /** @var  $paginator */
        $paginator  = $this-&gt;get('knp_paginator');
        $pagination = $paginator-&gt;paginate($posts, $request-&gt;query-&gt;get('page', 1), 3);

        return [
            'pagination' =&gt; $pagination,
        ];
    }

…
</pre>

## Configurando a View

Nosso controller está configurado, agora temos que configurar nossa view, para que a mesma apresente os posts, com a paginação.
  
Entre na view index.html.twig, caminho: src/Tableless/CoreBundle/Resources/views/IndexController/index.html.twig

Em nossa index, temos um for, que está recebendo a variável posts, vamos trocar a variável posts por pagination, que foi a variável que passamos em nosso controller, veja: 

de:

<pre class="lang-php">{% for post in posts %}
</pre>

troque por:

<pre class="lang-php">{% for post in pagination %}
</pre>

E onde queremos que nossa paginação fique, vamos colocar o código abaixo:

<pre class="lang-php">{{ knp_pagination_render(pagination) }}
</pre>

Veja nossa index.html.twig pronta

<pre class="lang-php">{% extends "::base.html.twig" %}

{% block title %}Simples Blog{% endblock %}

{% block content %}

    &lt;div class="container"&gt;

        &lt;div class="row"&gt;

            {{ knp_pagination_render(pagination) }}

            &lt;div class="col-lg-12"&gt;


            {% for post in pagination %}

                &lt;article class="col-lg-4"&gt;

                    &lt;div class="thumbnail"&gt;

                        &lt;a href="{{ path('show', { 'id': post.id }) }}"&gt;

                            &lt;img class="img-responsive" src="{{ asset(post.getCoverWeb) }}" alt="{{ post.cover }}" title="{{ post.cover }}"/&gt;

                        &lt;/a&gt;

                        &lt;div class="caption"&gt;

                            &lt;h3&gt;&lt;a href="{{ path('show', { 'id': post.id }) }}"&gt;{{ post.title }}&lt;/a&gt;&lt;/h3&gt;

                            &lt;p&gt;Escrito por: {{ post.author.name }}&lt;/p&gt;

                            &lt;p&gt;{{ post.content|slice(0, 45) }} ...&lt;/p&gt;

                            &lt;p&gt;&lt;a href="{{ path('show', { 'id': post.id }) }}"&gt;Leia mais...&lt;/a&gt;&lt;/p&gt;

                        &lt;/div&gt;

                    &lt;/div&gt;

                &lt;/article&gt;

            {% endfor %}

        &lt;/div&gt;
    &lt;/div&gt;
        {{ knp_pagination_render(pagination) }}

    &lt;/div&gt;

{% endblock %}

</pre>

Rode o servidor:

<pre class="lang-bash">$ php app/console server:run
</pre>

Entre na url:
  
http://127.0.0.1:8000

Veja a imagem:

[<img src="http://tableless.com.br/uploads/2015/04/011.png" alt="Paginação" width="750" height="403" class="alignnone size-full wp-image-48300" />][1]

## Estilizando a paginação

Podemos perceber, que a paginação está sem estilização, porém como estamos utilizando o bootstrap, vamos entrar no arquivo config.yml, caminho: app/config/config.yml

E vamos alterar o pagination da tamplete do knp_paginator

de:

<pre class="lang-php">pagination: KnpPaginatorBundle:Pagination:sliding.html.twig
</pre>

para:

<pre class="lang-php">pagination: KnpPaginatorBundle:Pagination:twitter_bootstrap_v3_pagination.html.twig
</pre>

Atualize a página, e pronto, veja:

[<img src="http://tableless.com.br/uploads/2015/04/021.png" alt="Paginação estilizada" width="750" height="403" class="alignnone size-full wp-image-48301" />][2]

## Conclusão

Pronto, nosso simples projeto está fazendo a paginação de posts, no próximo tutorial vamos configurar outro Bundle, onde faremos o slug para nossos posts, para que nossas urls, fiquem um pouco mais amigáveis.

Links dos tutoriais anteriores:
  
<a href="http://tableless.com.br/iniciando-com-symfony-2/" title="part 01" target="_blank">Iniciando com Symfony 2 – Instalação</a>
  
<a href="http://tableless.com.br/iniciando-com-symfony-2-parte-02/" title="parte 02" target="_blank">Iniciando com Symfony 2 – parte 02</a>
  
<a href="http://tableless.com.br/iniciando-com-symfony-2-parte-03/" title="parte 03" target="_blank">Iniciando com Symfony 2 – parte 03</a>
  
<a href="http://tableless.com.br/iniciando-com-symfony-2-parte-04/" title="parte 04" target="_blank">Iniciando com Symfony 2 – parte 04</a>
  
<a href="http://tableless.com.br/iniciando-com-symfony-2-parte-05/" title="parte 05" target="_blank">Iniciando com Symfony 2 – parte 05</a>
  
<a href="http://tableless.com.br/iniciando-com-symfony-2-parte-06/" title="parte 06" target="_blank">Iniciando com Symfony 2 – parte 06</a>
  
<a href="http://tableless.com.br/iniciando-com-symfony-2-parte-07/" title="parte 07" target="_blank">Iniciando com Symfony 2 – parte 07</a>

O projeto encontra-se no <a href="https://github.com/candidosouza/tableless" title="GitHub do projeto" target="_blank">GitHub</a>!

 [1]: http://tableless.com.br/uploads/2015/04/011.png
 [2]: http://tableless.com.br/uploads/2015/04/021.png