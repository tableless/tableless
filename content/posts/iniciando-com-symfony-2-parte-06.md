---
title: Iniciando com Symfony 2 – Parte 06
author: Candido Souza
type: post
date: 2015-04-01
excerpt: Nesse tutorial vamos estruturar e estilizar nossas páginas com Bootstrap e com o mecanismo de template para PHP, o Twig.
url: /iniciando-com-symfony-2-parte-06/
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
[<img src="http://tableless.com.br/uploads/2015/03/capa.png" alt="Symfony e Twig" width="750" height="403" class="alignnone size-full wp-image-47950" />][1]

No <a href="http://tableless.com.br/iniciando-com-symfony-2-parte-05/" title="iniciando com symfony 2 - parte 05" target="_blank">tutorial anterior</a>, configuramos nosso projeto e criamos nossas páginas, home e show, porém as mesmas se encontram sem estilização, neste tutorial, vamos apenas estruturar nossas páginas de um modo simples e básico, porém funcional. Não entrarei em detalhes sobre o Bootstrap, não é meu objetivo, porém para iniciantes, recomendo a <a href="http://getbootstrap.com/css/" title="Doc. Bootstrap" target="_blank">documentação</a>.
  
Sobre o Twig, falarei o básico do básico, somente o que vamos usar. Lembrando que ele já vem instalado e configurado no Symfony, porém podemos instalá-lo separadamente <a href="https://packagist.org/packages/twig/twig" title="Pacote do Twig" target="_blank">via Composer</a> e configurá- lo em outros projetos, usando ou não outros frameworks.

## Instalando e configurando o Twitter Bootstrap no Symfony

Vamos iniciar com a configuração do bootstrap.
  
Temos algumas formas de instalar e configurar o arquivo css no symfony, em nosso caso vamos fazer uma configuração simples apenas para a didática, caso queiram se aprofundar mais no assunto, aconselho a <a href="http://symfony.com/doc/current/cookbook/assetic/asset_management.html#including-css-stylesheets" title="Assets no Symfony" target="_blank">documentação</a>.

Primeiramente vamos criar uma pasta dentro da pasta Resource do bundle CoreBundle, caminho: src/Tableless/CoreBundle/Resouces, com o nome public, e dentro dessa nova pasta, vamos criar outra pasta com o nome css.

<a href="http://getbootstrap.com/getting-started/#download" title="Download do bootstrap" target="_blank">Baixe o bootstrap</a>, e copie o arquivo bootstrap.min.css para a pasta css/, veja a imagem abaixo para comparação:

[<img src="http://tableless.com.br/uploads/2015/03/011.png" alt="Pasta para bootstrap" width="750" height="403" class="alignnone size-full wp-image-47951" />][2]

Caso queiram, podem usar o arquivo bootstrap.css, em nosso caso vamos usar o .min.css.

Para que o bootstrap seja carregado vamos entrar no terminal, e digitar:

<pre class="lang-bash">$ php app/console assets:install --symlink
</pre>

Desse forma estamos criando um link simbólico do arquivo na pasta web, veja:

[<img src="http://tableless.com.br/uploads/2015/03/022.png" alt="Link simbólico" width="750" height="403" class="alignnone size-full wp-image-47952" />][3]

Agora devemos carregar o aquivo bootstrap em nossa aplicação. Vamos entrar no arquivo base.html.twig, caminho: app/Resources/views/base.html.twig, e carregar o bootstrap, no bloco stylesheets, veja na linha 7.

<pre class="lang-html">&lt;!DOCTYPE html&gt; 
&lt;html&gt; 
    &lt;head&gt; 
        &lt;meta charset="UTF-8" /&gt;
        &lt;title&gt;{% block title %}Welcome!{% endblock %}&lt;/title&gt;
        {% block stylesheets %} 
                &lt;link rel="stylesheet" type="text/css" href="{{ asset('bundles/tablelesscore/css/bootstrap.min.css') }}" /&gt;
        {% endblock %} 
        &lt;link rel="icon" type="image/x-icon" href="{{ asset('favicon.ico') }}" /&gt;
    &lt;/head&gt; 
    &lt;body&gt; 
        {% block body %}{% endblock %} 
        {% block javascripts %}{% endblock %} 
   &lt;/body&gt; 
&lt;/html&gt;
</pre>

## Iniciando com Twig

Pronto, o bootstrap está instalado e configurado.
  
Neste momento vou criar quatro posts em off, apenas para visualização, recomendo que façam o mesmo, pois assim ficará fácil para estilizar.

Vamos iniciar nossos trabalhos com o Twig.
  
Ainda com o arquivo base.html.twig aberto, vamos fazer algumas configurações.

O twig trabalha com blocos, que podem ser herdados pelas templates filhas, em nosso caso vamos criar um bloco com o nome &#8220;content&#8221;, para que nossas templates possam herdar. Para criar um bloco é bem simples, veja abaixo:

Abre o bloco:

<pre class="lang-html">{% block nome-do-bloco %} 
</pre>

Fecha o bloco:

<pre class="lang-html">{% endblock %}
</pre>

Ok! Vamos criar nosso bloco, que ficará dentro de outro bloco já existente no arquivo base.html.twig, veja abaixo na linha 15.

<pre class="lang-html">&lt;!DOCTYPE html&gt;
&lt;html&gt;
&lt;head&gt;
    &lt;meta charset="UTF-8" /&gt;
    &lt;title&gt;{% block title %}Welcome!{% endblock %}&lt;/title&gt;
{% block stylesheets %}
        &lt;link rel="stylesheet" type="text/css" href="{{ asset('bundles/tablelesscore/css/bootstrap.min.css') }}" /&gt;
    {% endblock %}
    &lt;link rel="icon" type="image/x-icon" href="{{ asset('favicon.ico') }}" /&gt;
&lt;/head&gt;
&lt;body&gt;
{% block body %}

    {# Novo bloco criado #}
    {% block content %}{% endblock %}
    
{% endblock %}
{% block javascripts %}{% endblock %}
&lt;/body&gt;
&lt;/html&gt;
</pre>

Agora para concluirmos esse arquivo, vamos estruturar o html, já incluindo as classes do bootstrap, veja abaixo o arquivo base.html.twig pronto:

<pre class="lang-html">&lt;!DOCTYPE html&gt; 
&lt;html&gt; 
    &lt;head&gt; 
        &lt;meta charset="UTF-8" /&gt;
        &lt;title&gt;{% block title %}Welcome!{% endblock %}&lt;/title&gt; 
        {% block stylesheets %} 
                &lt;link rel="stylesheet" type="text/css" href="{{ asset('bundles/tablelesscore/css/bootstrap.min.css') }}" /&gt;
        {% endblock %} 
        &lt;link rel="icon" type="image/x-icon" href="{{ asset('favicon.ico') }}" /&gt; 
    &lt;/head&gt; 
    &lt;body&gt; 
        {% block body %} 
        &lt;div class="container"&gt; 
            &lt;header class="row"&gt; 
                &lt;div class="col-lg-6"&gt; 
                    &lt;h1&gt;Simples Blog&lt;/h1&gt; 
                    &lt;a href="#" title=""&gt;Home&lt;/a&gt; | 
                    &lt;a href="#" title=""&gt;administração&lt;/a&gt;
                &lt;/div&gt; 
            &lt;/header&gt; 
        {% block content %} 
        {% endblock %} 
            &lt;footer class="col-lg-12"&gt; 
                &lt;p&gt;&copy; 2015 Tableless - Todos os direitos reservados&lt;/p&gt; 
            &lt;/footer&gt;
        &lt;/div&gt; 

        {% endblock %} 
        {% block javascripts %}{% endblock %} 
    &lt;body&gt; 
&lt;/html&gt;
</pre>

Podemos perceber que os links estão sem caminho, para passarmos um link no Symfony precisamos do nome de nossas rotas, e para pegar esses nomes, vamos entrar no terminal.

Abra o terminal e digite:

<pre class="lang-bash">$ php app/console router:debug
</pre>

Vamos ter uma lista dos nomes de nossas rotas, a primeira que vamos usar é a rota da home &#8220;/&#8221; , veja a imagem:

[<img src="http://tableless.com.br/uploads/2015/03/032.png" alt="Rotas" width="750" height="403" class="alignnone size-full wp-image-47953" />][4]

Percebemos que o nome dessa rota, está muito extenso, vamos mudar isso, deixando o nome dessa rota e da rota de visualização do post, um pouco mais curto.

Para isso, devemos entrar no controller indexController, caminho: src/Tableless/CoreBunde/ IndexControlerController.php
  
Abra o arquivo, e nas annotations dos métodos indexAction e showAction, vamos colocar os nomes que queremos para nossas rotas. Exemplo: @Route(&#8220;/&#8221;, name=&#8221;index&#8221;)

Veja o exemplo na linha 2 e na linha 9 do código abaixo:

<pre class="lang-html">/** 
     * @Route("/", name="index") 
     * @Template() 
     */ 
    public function indexAction() 
    .... 

    /** 
     * @Route("/show/{id}", name="show") 
     * @Template() 
     */ 
    public function showAction($id) 
    ...
</pre>

Agora nossas rotas estão com os nomes mais curtos.
  
Para vermos novamente entre no terminal e digite:

<pre class="lang-html">$ php app/console router:debug
</pre>

Veja:
  
[<img src="http://tableless.com.br/uploads/2015/03/042.png" alt="Rotas" width="750" height="403" class="alignnone size-full wp-image-47976" />][5]

Pronto! Agora podemos inserir nossos links.

Para pegarmos o link da home, digitamos: {{ path(&#8216;index&#8217;) }}, e para o link da administração vou pegar o link da lista de post.

Veja o arquivo base.html.twig pronto, os links estão na linha 17 e 18.

<pre class="lang-html">&lt;!DOCTYPE html&gt; 
&lt;html&gt; 
    &lt;head&gt; 
        &lt;meta charset="UTF-8" /&gt;
        &lt;title&gt;{% block title %}Welcome!{% endblock %}&lt;/title&gt; 
        {% block stylesheets %} 
                &lt;link rel="stylesheet" type="text/css" href="{{ asset('bundles/tablelesscore/css/bootstrap.min.css') }}" /&gt;
        {% endblock %} 
        &lt;link rel="icon" type="image/x-icon" href="{{ asset('favicon.ico') }}" /&gt; 
    &lt;/head&gt; 
    &lt;body&gt; 
        {% block body %} 
        &lt;div class="container"&gt; 
            &lt;header class="row"&gt; 
                &lt;div class="col-lg-6"&gt; 
                    &lt;h1&gt;Simples Blog&lt;/h1&gt; 
                    &lt;a href="{{ path('index') }}" title="Home"&gt;Home&lt;/a&gt; | 
                    &lt;a href="{{ path('post') }}" title="Administração"&gt;administração&lt;/a&gt;
                &lt;/div&gt; 
            &lt;/header&gt; 
        {% block content %} 
        {% endblock %} 
            &lt;footer class="col-lg-12"&gt; 
                &lt;p&gt;&copy; 2015 Tableless - Todos os direitos reservados&lt;/p&gt; 
            &lt;/footer&gt;
        &lt;/div&gt; 

        {% endblock %} 
        {% block javascripts %}{% endblock %} 
    &lt;body&gt; 
&lt;/html&gt;
</pre>

## Estruturando e estilizando o index

Nossa base está pronta, vamos agora para o arquivo index.html.twig, que é o index de nosso blog.
  
Caminho: src/Tableless/CoreBundle/Resources/views/IndexController/index.html.twig

Abra o arquivo para que possamos estruturá- lo.

Podemos perceber que na primeira linha, nosso arquivo está estendendo o arquivo base.html.twig, que acabamos de estruturar.
  
Em primeiro lugar vamos criar um título para nossa página.
  
Para isso, digitamos o título que queremos dentro do bloco title.
  
Para que nosso conteúdo, posicione- se no lugar correto, vamos renomear o bloco body, para content, que criamos no arquivo base, o h1 e dump, vamos excluir, veja nosso arquivo:

<pre class="lang-html">{% extends "::base.html.twig" %} 

{% block title %}Simples Blog{% endblock %} 

{% block content %} 
    
{% endblock %}
</pre>

Nosso Controller IndexController está retornando um array de posts, através do método indexAction, para recuperarmos esse array via Twig, devemos fazer um &#8220;for&#8221; para recuperar cada dado do post.

Obs: Se tivéssemos usando o php para recuperar esses dados, passaríamos um foreach, no caso do Twig para fazermos esse mesmo processo, usamos um for, veja abaixo o exemplo:

<pre class="lang-html">{% for valor in array %}

{% endfor %}
</pre>

Para entender melhor o funcionamento do for, recomendo a <a href="http://twig.sensiolabs.org/doc/tags/for.html" title="twig for" target="_blank">documentação</a>. 

Vamos entender melhor

Nosso método indexAction, do controller indexController, está nos retornando um array, veja na linha 7.

<pre class="lang-php">public function indexAction() 
    { 
        $em = $this-&gt;getDoctrine()-&gt;getManager(); 

        $posts = $em-&gt;getRepository('TablelessModelBundle:Post')-&gt;findAllInOrder(); 

        return [ 
            'posts' =&gt; $posts, 
        ]; 
    } 

</pre>

Para recuperarmos esses dados no twig, vamos fazer:

<pre class="lang-html">{% for post in posts %}

	{{ post.title }}
	{{ post.author.name }}
	{{ post.content | slice(0, 45) }}

{% endfor %}
</pre>

Perceba que ao recuperarmos o post.content, que é o conteúdo do nosso post, vamos passar um &#8220;slice&#8221;, que serve para cortar o texto, começando do 0 até 45 caracteres. Caso queiram mais de 45 caracteres, é só aumentar esse valor.

Também, temos que estruturar nossa página com html, incluir as classes do bootstrap e criar os links. Em relação aos links, para acessarmos um post, temos que passar o &#8220;id&#8221; desse post no link.

Vamos colocar uma imagem, escolham uma imagem, e coloque na pasta web, caminho: web/

Para recuperarmos essa imagem, vamos usar o asset.
  
Veja abaixo o exemplo do asset para imagem:

<pre class="lang-html">&lt;img src="{{ asset('imagem.png') }}" /&gt; 
</pre>

Veja o index.html.twig pronto:

<pre class="lang-html">{% extends "::base.html.twig" %} 

{% block title %}Simples Blog{% endblock %} 

{% block content %} 

    &lt;div class="container"&gt; 

        &lt;div class="row"&gt; 
 
            &lt;div class="col-lg-12"&gt;

                {% for post in posts %} 

                    &lt;article class="col-lg-4"&gt;

                        &lt;div class="thumbnail"&gt;

                            &lt;a href="{{ path('show', { 'id': post.id }) }}"&gt;

                                &lt;img class="img-responsive" src="{{ asset('logo-tableless.png') }}" alt="img" title="img"/&gt;

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

    &lt;/div&gt;

{% endblock %}
</pre>

Vamos entrar no terminal, e subir nosso servidor.

<pre class="lang-bash">$ php app/console server:run
</pre>

Entre na url: http://127.0.0.1:8000/

Nossa home está pronto, veja:

[<img src="http://tableless.com.br/uploads/2015/03/051.png" alt="blog" width="750" height="403" class="alignnone size-full wp-image-47980" />][6]

## Estruturando e estilizando o show

Vamos estruturar o show.html.twig, que é responsável pela visualização de cada post.

Abra o arquivo, caminho: src/Tableless/CoreBundle/Resources/views/IndexController/ show.html.twig, e vamos estruturá lo.

Vamos colocar um título no bloco &#8220;title&#8221;, renomear o bloco body para content, fazer a estruturação com o html e passar as classes do bootstrap. Perceba que nesse caso não precisamos fazer um &#8220;for&#8221; com o twig, pois estamos recebendo somente um array, ou seja, um post.
  
Temos que dar uma atenção para a data de criação, e a data de atualização, não estamos recebendo essas datas no formato correto. Para que possamos apresentar as datas, temos que passar um date() no twig, veja o exemplo abaixo

<pre class="lang-html">{{ post.createdAt | date('d/m/Y - H:m:s') }}
</pre>

Veja o arquivo show.html.twig pronto:

<pre class="lang-html">{% extends "::base.html.twig" %} 

{% block title %}Blog - {{ post.title }}{% endblock %} 

{% block content %} 

&lt;div class="container"&gt; 

    &lt;div class="row"&gt; 

        &lt;article class="col-lg-12"&gt; 

            &lt;h1&gt;{{ post.title }}&lt;/h1&gt; 

            &lt;p&gt;Escrito por: {{ post.author.name }}&lt;/p&gt;

            &lt;p&gt;Postado em: {{ post.createdAt | date('d/m/Y - H:m:s') }}&lt;/p&gt;

            &lt;p&gt;{{ post.content }}&lt;/p&gt; 

        &lt;/article&gt; 

    &lt;/div&gt; 
    
&lt;/div&gt; 

{% endblock %}
</pre>

Imagem da página pronta:

[<img src="http://tableless.com.br/uploads/2015/03/061.png" alt="Show post" width="750" height="403" class="alignnone size-full wp-image-47981" />][7]

## Conclusão

Nossa página de visualização de post, e nossa home, está estruturada e estilizada, temos que fazer a parte administrativa, tanto a administração de post, quanto de autores. Vou fazer essa parte em off. Os arquivos, encontram- se no github, os caminhos são:

src/Tableless/CoreBundle/Resources/views/Author/
  
src/Tableless/CoreBundle/Resources/views/Posts/

Links dos tutoriais anteriores:
  
<a href="http://tableless.com.br/iniciando-com-symfony-2/" title="instalação" target="_blank">Iniciando com Symfony 2 – Instalação</a>
  
<a href="http://tableless.com.br/iniciando-com-symfony-2-parte-02/" title="pt 02" target="_blank">Iniciando com Symfony 2 – parte 02</a>
  
<a href="http://tableless.com.br/iniciando-com-symfony-2-parte-03/" title="pt 3" target="_blank">Iniciando com Symfony 2 – parte 03</a>
  
<a href="http://tableless.com.br/iniciando-com-symfony-2-parte-04/" title="pt 4" target="_blank">Iniciando com Symfony 2 – parte 04</a>
  
<a href="http://tableless.com.br/iniciando-com-symfony-2-parte-05/" title="pt 5" target="_blank">Iniciando com Symfony 2 – parte 05</a>

O projeto <a href="https://github.com/candidosouza/tableless" title="Github do projeto" target="_blank">encontra-se no GitHub</a>!

 [1]: http://tableless.com.br/uploads/2015/03/capa.png
 [2]: http://tableless.com.br/uploads/2015/03/011.png
 [3]: http://tableless.com.br/uploads/2015/03/022.png
 [4]: http://tableless.com.br/uploads/2015/03/032.png
 [5]: http://tableless.com.br/uploads/2015/03/042.png
 [6]: http://tableless.com.br/uploads/2015/03/051.png
 [7]: http://tableless.com.br/uploads/2015/03/061.png