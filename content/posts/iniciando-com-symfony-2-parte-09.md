---
title: Iniciando com Symfony 2 – Parte 09
author: Candido Souza
type: post
date: 2015-05-24
excerpt: Nesse tutorial, vamos instalar o bundle StofDoctrineExtensionsBundle, para fazermos os slugs de nossos posts.
url: /iniciando-com-symfony-2-parte-09/
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
No <a href="http://tableless.com.br/iniciando-com-symfony-2-parte-08/" title="tutorial anterior" target="_blank">tutorial anterior</a>, instalamos e configuramos o bundle Knp Paginator, para fazer a paginação de posts em nosso index, agora vamos instalar e configurar o Bundle StofDoctrineExtensionsBundle, para fazermos os slugs de nossos posts

## Instalação do bundle StofDoctrineExtensionsBundle

Para instalar o StofDoctrineExtensionsBundle, temos que adicioná-lo em nosso composer.json. Abra o arquivo composer.json e adicione a linha abaixo:

<pre class="lang-php">"stof/doctrine-extensions-bundle": "1.2.*@dev"
</pre>

Depois de adicionando o StofDoctrineExtensionsBundle no composer, vamos instalá- lo. Entre no terminal e digite:

<pre class="lang-bash">$ composer update
</pre>

Após o Download, o StofDoctrineExtensionsBundle está instalado em nossa aplicação.

## Configurando o StofDoctrineExtensionsBundle

A primeira configuração que devemos fazer, é registrar o novo bundle instalado, para isso entre no AppKernel, caminho: app/AppKernel.php

Adicione a linha abaixo no registro de bundles:

<pre class="lang-php">new Stof\DoctrineExtensionsBundle\StofDoctrineExtensionsBundle(),
</pre>

Veja na linha 17:

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
	    new Stof\DoctrineExtensionsBundle\StofDoctrineExtensionsBundle(),
        );

...

</pre>

Pronto, o StofDoctrineExtensionsBundle está registrado.
  
Agora vamos fazer as configurações no arquivo config.yml, caminho: app/config/config.yml

No final do arquivo adicione as configurações abaixo: 

<pre class="lang-php">stof_doctrine_extensions:
    orm:
        default:
            sluggable: true
</pre>

## Configurando a entidade Post

Temos que configurar nossa entidade post, para que a mesma receba os slugs. Entre na entidade post, caminho: src/Tableless/ModelBundle/Entity/Post.php

Vamos dar um use em Annotation, e apelidá-la de Gedmo veja abaixo:

<pre class="lang-php">use Gedmo\Mapping\Annotation as Gedmo;
</pre>

Agora vamos criar uma propriedade privada chamada slug, com as suas annotations correspondentes, veja:

<pre class="lang-php">/**
     * @var string
     *
     * @Gedmo\Slug(fields={"title"}, unique=false)
     * @ORM\Column(length=255)
     */
     private $slug;

...

</pre>

Temos que gerar os getters e setters, para isso vamos entrar no terminal e digitar:

<pre class="lang-bash">$ php app/console generate:doctrine:entities TablelessModelBundle:Post
</pre>

Pronto, em nossa entidade Post, temos os getters e setters, veja:

<pre class="lang-php">/**
     * Set slug
     *
     * @param string $slug
     *
     * @return Post
     */
    public function setSlug($slug)
    {
        $this-&gt;slug = $slug;

        return $this;
    }

    /**
     * Get slug
     *
     * @return string
     */
    public function getSlug()
    {
        return $this-&gt;slug;
    }

...
</pre>

## Configurando o Banco de Dados

Depois de nossa entidade configurada, temos que atualizar o banco de dados, porém se tivermos posts já criados, ocorrerá um erro em nosso blog. Caso não tenha nenhum post escrito poderá rodar o comando abaixo:

<pre class="lang-bash">$ php app/console doctrine:schema:update –force
</pre>

Caso tenha escrito algum post para exemplo, como no meu caso, vamos excluir o banco de dados, e criá lo novamente. Entre no terminal e digite:

Excluindo o banco de dados:

<pre class="lang-php">$ php app/console doctrine:database:drop --force
</pre>

Criando o banco de dados novamente:

<pre class="lang-bash">$ php app/console doctrine:database:create
</pre>

Criando as tabelas:

<pre class="lang-bash">$ php app/console doctrine:schema:create
</pre>

Obs: Caso tenha posts escritos, e não queria excluir o banco de dados, poderá apenas atualizá-lo, porém terá que adicionar manualmente, slug por slug em cada post no banco de dados, senão ocorrerá erro na aplicação.

Veja a estrutura do banco de dados:

[<img src="http://tableless.com.br/uploads/2015/05/01.png" alt="Banco de dados" width="750" height="403" class="alignnone size-full wp-image-48547" />][1]

## Configurando o Controller

Depois de termos feito as configurações citadas acima, vamos configurar nosso controller, para isso entre no IndexControlerController, caminho: src/Tableless/CoreBundle/Controller/IndexControlerController.php

No nosso método showAction, estamos passando por parâmetro o $id, no momento não queremos mais buscar nossos posts pelo id, e sim pelo slug, vamos alterar:

de:

<pre class="lang-php">public function showAction($id)
</pre>

para:

<pre class="lang-php">public function showAction($slug)
</pre>

Temos que mudar também a annotation da rota, veja:

de: 

<pre class="lang-php">* @Route("/show/{id}", name="show")
</pre>

para:

<pre class="lang-php">* @Route("/show/{slug}", name="show")
</pre>

Estamos passando para a variável $post, o método find, e recuperando o id, vamos mudar o find para findOneBy e passar um array de slug, veja:

<pre class="lang-php">...

$post = $em-&gt;getRepository('TablelessModelBundle:Post')-&gt;findOneBy([
            'slug' =&gt; $slug
        ]);

...

</pre>

Veja o método showAction pronto:

<pre class="lang-php">...

    /**
     * @Route("/post/{slug}", name="show")
     * @Template()
     */
    public function showAction($slug)
    {
        $em = $this-&gt;getDoctrine()-&gt;getManager();

        $post = $em-&gt;getRepository('TablelessModelBundle:Post')-&gt;findOneBy([
            'slug' =&gt; $slug
        ]);

        if (!$post) {
            throw $this-&gt;createNotFoundException('O post não existe! Volte para home!');
        }

        return [
            'post' =&gt; $post,
        ];
    }
 
    ...
</pre>

## Configurando o index

Em nossa index, estamos passando os links para que os posts sejam buscados pelo id, porém temos que alterá- los para que possamos buscar os posts pelo slug.
  
Entre no index.html.twig, caminho: src/Tableless/CoreBundle/Resources/views/IndexController/Index.html.twig

Vamos alterar os links:
  
No meu caso a linha 21, 29 e 35:

de:

<pre class="lang-html">&lt;a href="{{ path('show', { 'id': post.id }) }}"&gt;
</pre>

para:

<pre class="lang-html">&lt;a href="{{ path('show', { slug: post.slug }) }}"&gt;
</pre>

Testando nossa aplicação:

Caso tenham seguido o tutorial e excluído o bando de dados, que foi criado novamente, como no meu caso. Antes de criarmos um post, temos que criar os autores novamente, depois sim criarmos os posts. No meu caso vou criar apena um post para exemplo.
  
Depois do post criado, click no link e observe a url, verá o slug, que em nosso caso é o slug do titulo, veja:

[<img src="http://tableless.com.br/uploads/2015/05/02.png" alt="Urls" width="750" height="50" class="alignnone size-full wp-image-48548" />][2]

## Conclusão

Pronto, nosso simples projeto está retornando o slug dos post em nossa url.

Links dos tutoriais anteriores:
  
<a href="http://tableless.com.br/iniciando-com-symfony-2/" title="instalação" target="_blank">Iniciando com Symfony 2 – Instalação</a>
  
<a href="http://tableless.com.br/iniciando-com-symfony-2-parte-02/" title="parte 02" target="_blank">Iniciando com Symfony 2 – parte 02</a>
  
<a href="http://tableless.com.br/iniciando-com-symfony-2-parte-03/" title="parte 03" target="_blank">Iniciando com Symfony 2 – parte 03</a>
  
<a href="http://tableless.com.br/iniciando-com-symfony-2-parte-04/" title="parte 04" target="_blank">Iniciando com Symfony 2 – parte 04</a>
  
<a href="http://tableless.com.br/iniciando-com-symfony-2-parte-05/" title="parte 05" target="_blank">Iniciando com Symfony 2 – parte 05</a>
  
<a href="http://tableless.com.br/iniciando-com-symfony-2-parte-06/" title="parte 06" target="_blank">Iniciando com Symfony 2 – parte 06</a>
  
<a href="http://tableless.com.br/iniciando-com-symfony-2-parte-07/" title="parte 07" target="_blank">Iniciando com Symfony 2 – parte 07</a>
  
<a href="http://tableless.com.br/iniciando-com-symfony-2-parte-08/" title="parte 08" target="_blank">Iniciando com Symfony 2 – parte 08</a>

O projeto encontra-se no <a href="https://github.com/candidosouza/tableless" title="github do projeto" target="_blank">GitHub</a>!

 [1]: http://tableless.com.br/uploads/2015/05/01.png
 [2]: http://tableless.com.br/uploads/2015/05/02.png