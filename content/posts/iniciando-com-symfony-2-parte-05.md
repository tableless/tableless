---
title: Iniciando com Symfony 2 – Parte 05
author: Candido Souza
type: post
date: 2015-03-19
excerpt: 'Nesse tutorial vamos configurar nosso projeto, e criar a página index, para que nossos posts,  sejam visualizados pelos usuários.'
url: /iniciando-com-symfony-2-parte-05/
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
No <a href="http://tableless.com.br/iniciando-com-symfony-2-parte-04/" title="Iniciando com symfony2 - parte 4" target="_blank">tutorial anterior</a>, criamos a entidade Author, e fizemos o relacionamento com os posts, neste tutorial vamos fazer as configurações adequadas para que possamos deixar nossa aplicação estruturada corretamente, e vamos criar e configurar a página index, onde os usuários terão acesso para visualizar e ler os posts.

## Configurando

Vamos começar com as configurações.
  
Entrando no bundle CoreBundle, caminho: src/Tableless/CoreBundle, exclua a pasta Controller.
  
[<img src="http://tableless.com.br/uploads/2015/03/021.png" alt="Excluindo a pasta controller" width="750" height="403" class="alignnone size-full wp-image-47743" />][1]

Ainda neste mesmo bundle vamos excluir a pasta view, caminho: src/Tableless/CoreBundle/Resources/view.

[<img src="http://tableless.com.br/uploads/2015/03/031.png" alt="Excluindo a pasta view" width="750" height="403" class="alignnone size-full wp-image-47744" />][2]

Agora vamos entrar no bundle ModelBundle, caminho: src/Tableless/ModelBundle.
  
E vamos mover a pasta Controller desse bundle para o bundle CoreBundle

Vamos mover também a pasta view do ModelBundle para o bundle CoreBundle.

Depois das mudanças, nossa estrutura de pastas ficará como na imagem abaixo:
  
[<img src="http://tableless.com.br/uploads/2015/03/041.png" alt="Estrutura de pastas pronta" width="750" height="403" class="alignnone size-full wp-image-47746" />][3]

## Configurando os Controllers

Vamos continuar nossas configurações, agora vamos alterar nossos controllers para que os mesmos fiquem de acordo com a estrutura de pasta atual.

Primeiramente, vamos excluir a rota do ModelBundle, pois não vamos usá-la.
  
Entre no arquivo app/config/routing.yml e exclua as linhas abaixo:

<pre class="lang-yml">tableless_model:
    resource: "@TablelessModelBundle/Controller/"
    type:     annotation
    prefix:   /
</pre>

Deixando somente a rota tableless_core como mostrado na imagem abaixo:

[<img src="http://tableless.com.br/uploads/2015/03/05.png" alt="Arquivo routing.yml" width="750" height="403" class="alignnone size-full wp-image-47747" />][4]

Agora vamos excluir o DefaultController.php, pois não vamos usar esse controller.

Abra o arquivo AuthorController.php, caminho: src/Tableless/CoreBundle/Controller/AuthorController.php

Na linha 3, mude o namespace.
  
De: Tableless\ModelBundle\Controller;
  
Para: Tableless\CoreBundle\Controller;

Na linha 43, mude a annotation:
  
De: @Template(&#8220;TablelessModelBundle:Author:new.html.twig&#8221;)
  
Para: @Template(&#8220;TablelessCoreBundle:Author:new.html.twig&#8221;)

Agora vamos configurar o controller PostController, caminho: src/Tableless/CoreBundle/Controller/PostController.php, vamos fazer a mesma alteração.

Na linha 3, mude o namespace.
  
De: Tableless\ModelBundle\Controller;
  
Para: Tableless\CoreBundle\Controller;

Na linha 43, mude a annotation:
  
De: @Template(&#8220;TablelessModelBundle:Post:new.html.twig&#8221;)
  
Para: @Template(&#8220;TablelessCoreBundle:Post:new.html.twig&#8221;)

Para verificarmos se correu tudo bem, vamos fazer o teste.
  
Rode o servidor

<pre class="lang-bash">$ app/console server:run
</pre>

Entre nas urls:
  
http://127.0.0.1:8000/post/
  
http://127.0.0.1:8000/author/

Se tudo foi configurado corretamente, nossa aplicação voltará a funcionar perfeitamente, veja:

[<img src="http://tableless.com.br/uploads/2015/03/06.png" alt="Página index, e show" width="750" height="403" class="alignnone size-full wp-image-47751" />][5]

## Criando um Controller

Nesse momento vamos criar um index, para nossa aplicação, para que seja nossa pagina principal, e possamos visualizar os posts de forma correta.
  
Podemos criar o controller codificando, porém para efeito de didática vamos criar através do console.

Entre no terminal e digite:

<pre class="lang-bash">$ php app/console generate:controller
</pre>

Ao digitarmos o comando acima e darmos enter, entramos no assistente do console do Symfony e ele nos comunica: Primeiro, você precisa dar o nome do controlador que você deseja gerar. Você deve usar a notação de atalho como AcmeBlogBundle:Post

Nesse momento digitamos:

<pre class="lang-bash">$ Controller name: TablelessCoreBundle:IndexControler
</pre>

Ao darmos o nome do nosso controller e darmos enter, o assistente nos pergunta: Qual o formato que vamos configurar a nossa rota?
  
E nos indica annotation, vamos deixar como está, e apenas damos enter:

<pre class="lang-php">$ Routing format (php, xml, yml, annotation) [annotation]:
</pre>

A próxima pergunta é:
  
Qual o formato que vamos usar para template?
  
Ele mesmo nos indica o twig. Apenas damos enter.

<pre class="lang-php">$ Template format (twig, php) [twig]:
</pre>

Após o enter ele nos pede o nome de nossas ações, que são os métodos que vamos criar para o nosso controller.
  
A primeira ação (método) vamos chamar de indexAction, e damos enter.

<pre class="lang-bash">$ New action name (press  to stop adding actions): indexAction
</pre>

O assistente nos pede a rota, vamos digitar “/” e damos enter.

<pre class="lang-bash">$ Action route [/index]: /
</pre>

Nos pergunta o caminho da nossa template, e ele nos indica um caminho, vamos deixar como está e apenas damos enter.

<pre class="lang-bash">$ Templatename (optional) [TablelessCoreBundle:IndexControler:index.html.twig]:
</pre>

Novamente o assistente nos pede para darmos um nome para uma nova ação (método), essa nova ação fará com que o post seja visualizado para a leitura, vamos dar o nome de showAction.

<pre class="lang-bash">$ New action name (press  to stop adding actions): showAction
</pre>

O assistente nos pede a rota, e nos indica como “/show”, vamos deixar como está e damos enter.

<pre class="lang-bash">$ Action route [/show]:
</pre>

Nos pergunta sobre caminho da template, e ele nos indica um caminho, vamos deixar como está e apenas damos enter.

<pre class="lang-bash">$ Templatename (optional) [TablelessCoreBundle:IndexControler:show.html.twig]:
</pre>

Ao darmos enter, entramos no modo de criação de uma nova ação, porém não queremos nenhuma outra ação, então apenas damos um enter, para entrarmos no processo de finalização.

<pre class="lang-bash">$ New action name (press  to stop adding actions):
</pre>

Ao entramos no processo de finalização o assistente nos pergunta se queremos confirmar a geração desse controller, ele nos indica sim, como queremos, apenas damos enter.

<pre class="lang-bash">$ Do you confirm generation [yes]?
</pre>

Pronto! Nosso controller IndexController está criado, juntamente com suas templates, veja a imagem abaixo:
  
[<img src="http://tableless.com.br/uploads/2015/03/07.png" alt="Index controller" width="750" height="403" class="alignnone size-full wp-image-47775" />][6]

Ao entrarmos na url: http://127.0.0.1:8000/, vamos entrar no nosso index, e receberemos a mensagem abaixo:

Welcome to the IndexControler:index page

## Criando um repositório

Se entrarmos em nosso controller IndexController, caminho: src/Tableless/CoreBunde/ IndexController.php, vamos perceber que nossos métodos estão criados, porém não estão implementados, vamos implementá-los, mas queremos que nosso index apresente para o usuário os últimos posts escritos, para que sempre o post mais atual seja apresentado em primeiro lugar, para isso devemos criar um repositório para nossa entidade Post.

Para isso, vamos entrar no bundle ModelBundle e crie uma pasta com o nome de Repository, dentro dessa pasta crie uma classe com o nome PostRepository.

Com a classe PostRepository aberta, adicione o nemspace dessa classe, e de um extends na classe EntityRepository do Doctrine, não se esquecendo de dar um use nessa classe.

use Doctrine\ORM\EntityRepository;

Crie um método privado com o nome getQueryBuilder e acrescente a EntityManager para que possamos usar nossa entidade Post, veja abaixo:

<pre class="lang-php">private function getQueryBuilder()
{
    $em = $this-&gt;getEntityManager();

    $queryBuilder = $em-&gt;getRepository('TablelessModelBundle:Post')
    -&gt;createQueryBuilder('p');

    return $queryBuilder;
 }
</pre>

Agora vamos criar um método publico chamado findAllInOrder, e vamos chamar o método getQueryBuilder(), para ordená-lo da forma que queremos, para que seja mostrado o último post postado primeiro. Veja abaixo:

<pre class="lang-php">public function findAllInOrder()
{
    $qb = $this-&gt;getQueryBuilder()
    -&gt;orderBy('p.createdAt', 'desc');

    return $qb-&gt;getQuery()-&gt;getResult();
}
</pre>

Veja a classe PostRepository pronta:

<pre class="lang-php">&lt;?php

namespace Tableless\ModelBundle\Repository;

use Doctrine\ORM\EntityRepository;

class PostRepository extends EntityRepository
{
    private function getQueryBuilder()
    {
        $em = $this-&gt;getEntityManager();
        $queryBuilder = $em-&gt;getRepository('TablelessModelBundle:Post')
            -&gt;createQueryBuilder('p');
        return $queryBuilder;
    }

     public function findAllInOrder()
    {
        $qb = $this-&gt;getQueryBuilder()
            -&gt;orderBy('p.createdAt', 'desc');

        return $qb-&gt;getQuery()-&gt;getResult();
    }
} 

</pre>

Agora temos que indicar para a entidade Post via annotation, onde está a classe PostRepository, para isso vamos abrir a entidade Post, caminho:src/Tableless/ModelBundle/Entity/Post.php, e acrescentar a annotation (repositoryClass=&#8221;Tableless\ModelBundle\Repository\PostRepository&#8221;) na linha 12 de sua entidade, veja:

<pre class="lang-php">/**
 * Post
 *
 * @ORM\Table(name="post")
 * @ORM\Entity(repositoryClass="Tableless\ModelBundle\Repository\PostRepository")
 */
class Post extends Timestampable
{
    ...
</pre>

## Implementando o controller

Vamos voltar para nosso IndexController, para que possamos implementá- lo. Abra o IndexController , e no método indexAction() temos que chamar nossa entidade Post, para que através dela chamemos o método findAllInOrder() da classe PostRepository, e retornar o resultado em forma de array, veja abaixo:

<pre class="lang-php">public function indexAction()
    {
        $em = $this-&gt;getDoctrine()-&gt;getManager();

        $posts = $em-&gt;getRepository('TablelessModelBundle:Post')-&gt;findAllInOrder();

        return [
            'posts' =&gt; $posts,
        ];
    } 
</pre>

Também vamos implementar o método showAction(), para que seja buscado apena o post clickado pelo usuário, para isso devemos passar um parâmetro id, tanto no método, quanto na annotation para rota, para que seja buscado somente o post solicitado. Temos que chamar nossa entidade Post novamente, para que através dela chamemos o método find(), que já vem pré configurado pelo Doctrine, porém se o usuário requisitar um post que não existe, temos que passar uma mensagem de erro, para informá- lo, veja abaixo:

<pre class="lang-php">/**
     * @Route("/show/{id}")
     * @Template()
     */
    public function showAction($id)
    {
        $em = $this-&gt;getDoctrine()-&gt;getManager();

        $post = $em-&gt;getRepository('TablelessModelBundle:Post')-&gt;find($id);

        if (!$post) {
            throw $this-&gt;createNotFoundException('O post não existe! Volte para home!');
        }

        return [
            'post' =&gt; $post,
        ];
    }
</pre>

Veja o IndexController pronto:

<pre class="lang-php">&lt;?php

namespace Tableless\CoreBundle\Controller;

use Symfony\Bundle\FrameworkBundle\Controller\Controller;
use Sensio\Bundle\FrameworkExtraBundle\Configuration\Route;
use Sensio\Bundle\FrameworkExtraBundle\Configuration\Template;

class IndexControlerController extends Controller
{
     /**
     * @Route("/")
     * @Template()
     */
    public function indexAction()
    {
        $em = $this-&gt;getDoctrine()-&gt;getManager();

        $posts = $em-&gt;getRepository('TablelessModelBundle:Post')-&gt;findAllInOrder();

        return [
            'posts' =&gt; $posts,
        ];
    }

     /**
     * @Route("/show/{id}")
     * @Template()
     */
    public function showAction($id)
    {
        $em = $this-&gt;getDoctrine()-&gt;getManager();

        $post = $em-&gt;getRepository('TablelessModelBundle:Post')-&gt;find($id);

        if (!$post) {
            throw $this-&gt;createNotFoundException('O post não existe! Volte para home!');
        }

        return [
            'post' =&gt; $post,
        ];
    }
}

</pre>

Para vemos como está ficando nossa aplicação, abra a index.html.twig, do IndexController, caminho: src/Tableless/CoreBundle/Resouces/views/IndexController/index.html.twig e vamos dar um dump em posts, veja abaixo, vamos adicionar a linha 8:

<pre class="lang-twig">{% extends "::base.html.twig" %}

{% block title %}TablelessCoreBundle:IndexControler:index{% endblock %}

{% block body %}
Welcome to the IndexControler:index page

    {{ dump(posts) }}
    
{% endblock %}
</pre>

Vamos fazer a mesma modificação para o arquivo show.html.twig no mesmo diretório, porém ao em vez de dar um dump em posts, vamos dar um dump em post, sem o “s” no final, veja:

<pre class="lang-html">{% extends "::base.html.twig" %}

{% block title %}TablelessCoreBundle:IndexControler:show{% endblock %}

{% block body %}
Welcome to the IndexControler:show page

    {{ dump(post) }}
    
{% endblock %}
</pre>

Para vemos o resultado, entre nas urls:

http://127.0.0.1:8000/
  
http://127.0.0.1:8000/show/{o id do seu post}

Veja as imagens para comparação:

index &#8211; url: http://127.0.0.1:8000/
  
[<img src="http://tableless.com.br/uploads/2015/03/08.png" alt="index" width="750" height="403" class="alignnone size-full wp-image-47767" />][7]

Pagina show – url: http://127.0.0.1:8000/show/4 -> {o id do seu post} no meu caso 4.
  
[<img src="http://tableless.com.br/uploads/2015/03/09.png" alt="show" width="750" height="403" class="alignnone size-full wp-image-47768" />][8]

## Conclusão

No tutorial anterior, eu comentei que iriamos configurar nosso projeto e começarmos a trabalhar com o Twig, porém nossa configuração e a criação do index, deixou este tutorial extenso, mas no próximo tutorial, vamos trabalhar com o bootstrap e com o twig para que possamos visualizar nossos post em nossa home da forma adequada e bonita.

Links dos tutoriais anteriores:
  
<a href="http://tableless.com.br/iniciando-com-symfony-2/" title="instalação" target="_blank">Iniciando com Symfony 2 &#8211; Instalação</a>
  
<a href="http://tableless.com.br/iniciando-com-symfony-2-parte-02/" title="parte 02" target="_blank">Iniciando com Symfony 2 &#8211; parte 02</a>
  
<a href="http://tableless.com.br/iniciando-com-symfony-2-parte-03/" title="parte 03" target="_blank">Iniciando com Symfony 2 &#8211; parte 03</a>
  
<a href="http://tableless.com.br/iniciando-com-symfony-2-parte-04/" title="parte 04" target="_blank">Iniciando com Symfony 2 &#8211; parte 04</a>

O projeto <a href="https://github.com/candidosouza/tableless" title="Git do projeto" target="_blank">encontra-se no GitHub</a>!

 [1]: http://tableless.com.br/uploads/2015/03/021.png
 [2]: http://tableless.com.br/uploads/2015/03/031.png
 [3]: http://tableless.com.br/uploads/2015/03/041.png
 [4]: http://tableless.com.br/uploads/2015/03/05.png
 [5]: http://tableless.com.br/uploads/2015/03/06.png
 [6]: http://tableless.com.br/uploads/2015/03/07.png
 [7]: http://tableless.com.br/uploads/2015/03/08.png
 [8]: http://tableless.com.br/uploads/2015/03/09.png