---
title: Iniciando com Symfony 2 – Parte 07
author: Candido Souza
type: post
date: 2015-04-10
excerpt: 'Nesse tutorial, vamos usar um componente do Symfony, o http-foundation,  para usar  UploadedFile, onde criaremos um upload de imagens para que possamos incluir em nossos posts.'
url: /iniciando-com-symfony-2-parte-07/
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
No <a href="http://tableless.com.br/iniciando-com-symfony-2-parte-06/" title="Iniciando com Symfony" target="_blank">tutorial anterior</a>, estilizamos nossas páginas, index e show, e incluímos um imagem para apresentar nossos posts no index, porém colocamos esta imagem pelo código fonte, agora vamos fazer algumas configurações, para que, na criação dos posts, tenha a opção de fazer o upload de uma imagem, para ser apresentada como capa de nossos posts.

## Configurando a entidade Post

Para criarmos um upload de imagem, vamos usar o componente http-foundation do Symfony, e usar sua classe UploadedFile em nossa entidade Post. 

Para isso, vamos entrar em nossa entidade Post, caminho: src/Tableless/ModelBundle/Entity/Post.php.
  
Com a entidade Post aberta vamos dar um use em UploadedFile, veja na linha 7:

<pre class="lang-php">&lt;?php 

namespace Tableless\ModelBundle\Entity; 

use Doctrine\ORM\Mapping as ORM; 
use Symfony\Component\Validator\Constraints as Assert; 
use Symfony\Component\HttpFoundation\File\UploadedFile; 


/** 
 * Post 
 * 
 * @ORM\Table(name="post")
…

</pre>

Precisamos criar dois atributos privados, $cover, e $file , e inserir as annotations correspondentes, o atributo $cover, receberá o nome da imagem, e o $file o aquivo com um limite de tamanho, veja abaixo:

<pre class="lang-php">/** 
     * @var string 
     * 
     * @ORM\Column(name="cover", type="string", length=255, nullable=true) 
     */ 
    private $cover; 
    
    /** 
     * @Assert\File(maxSize="1000000") 
     */ 
    private $file;

    ...
</pre>

Vamos fazer os Getters and Setters desses atributos.
  
O setFile receberá um parâmetro $file, esse parâmetro será do tipo UploadedFile, e caso não passamos uma imagem, poderá ser nulo, veja os getters and setters criados:

<pre class="lang-php">...

    /** 
     * Get cover 
     * 
     * @return string 
     */ 
    public function getCover() 
    { 
        return $this-&gt;cover; 
    } 

    /** 
     * Set cover 
     * 
     * @param string $cover 
     * @return Image 
     */ 
    public function setCover($cover) 
    { 
        $this-&gt;cover = $cover; 
    } 

    /** 
     * Get file. 
     * 
     * @return UploadedFile 
     */ 
    public function getFile() 
    { 
        return $this-&gt;file; 
    } 

    /** 
     * Set file. 
     * 
     * @param UploadedFile $file 
     */ 
    public function setFile(UploadedFile $file = null) 
    { 
        $this-&gt;file = $file; 
    }

    ...
</pre>

Precisamos obter o caminho relativo do upload, ou seja, a pasta para onde as imagens serão enviadas; para isso vamos criar o método protegido getUploadPath(), que nos retornará essa pasta. Veja abaixo:

<pre class="lang-php">...

    /** 
     * Relative path. 
     * Get web path to upload directory. 
     * 
     * @return string 
     */ 
    protected function getUploadPath() 
    { 
        return 'uploads/covers'; 
    }

    ...

</pre>

Temos que obter o caminho absoluto, para fazer o upload de nossas imagens, que ficará na pasta web, para isso vamos criar o método protegido getUploadAbsolutePath(), que nos retornará o caminho absoluto, e para chegarmos na pasta &#8220;uploads/covers&#8221;, vamos concatenar com o método getUploadPath() criado acima, veja:

<pre class="lang-php">...

    /** 
     * Absolute path. 
     * Get absolute path to upload directory. 
     * 
     * @return string 
     */ 
    protected function getUploadAbsolutePath() 
    { 
        return __DIR__ . '/../../../../web/' . $this-&gt;getUploadPath(); 
    }

    ...

</pre>

Agora precisamos apresentar o caminho de nossas imagens para as views, vamos criar o método público getCoverWeb(), caso tenhamos uma imagem, ou seja, caso a imagem não seja nula, apresentamos a imagem nas views, para isso usaremos o método getUploadPath(), concatenado com o nome de nossa imagem, ou seja o método getCover(), veja:

<pre class="lang-php">...

    /** 
     * Relative path. 
     * Get web path to a cover. 
     * 
     * @return null|string 
     */ 
    public function getCoverWeb() 
    { 
        return null === $this-&gt;getCover() 
            ? null 
            : $this-&gt;getUploadPath() . '/' . $this-&gt;getCover(); 
    }

    ...

</pre>

Podemos precisar do caminho absoluto de nossa imagem, para isso vamos criar o método getCoverAbsolute(), para obtermos esse caminho quando precisarmos, veja:

<pre class="lang-php">...

    /** 
     * Get path on disk to a cover. 
     * 
     * @return null|string 
     *   Absolute path. 
     */ 
    public function getCoverAbsolute() 
    { 
        return null === $this-&gt;getCover() 
            ? null 
            : $this-&gt;getUploadAbsolutePath() . '/' . $this-&gt;getCover(); 
    }

    ...
</pre>

Agora temos que criar um método que fará o upload da imagem, para isso criaremos um método como nome upload(), caso a imagem não seja nula, ele fará o upload usando alguns métodos prontos da classe UploadedFile, para mover a imagens, veja:

<pre class="lang-php">... 
  
    /** 
     * Upload a cover file. 
     */ 
    public function upload() 
    { 
        if (null === $this-&gt;getFile()) { 
            return; 
        } 
        $filename = $this-&gt;getFile()-&gt;getClientOriginalName(); 
        $this-&gt;getFile()-&gt;move($this-&gt;getUploadAbsolutePath(), $filename); 
        $this-&gt;setCover($filename); 
        $this-&gt;setFile(); 
    }


    ...

</pre>

Pronto, nossa entidade Post, agora está recebendo um upload de imagem.
  
Veja o entidade Post pronta:

<pre class="lang-php">&lt;?php

namespace Tableless\ModelBundle\Entity;

use Doctrine\ORM\Mapping as ORM;
use Symfony\Component\Validator\Constraints as Assert;
use Symfony\Component\HttpFoundation\File\UploadedFile;


/**
 * Post
 *
 * @ORM\Table(name="post")
 * @ORM\Entity(repositoryClass="Tableless\ModelBundle\Repository\PostRepository")
 */
class Post extends Timestampable
{
    /**
     * @var integer
     *
     * @ORM\Column(name="id", type="integer")
     * @ORM\Id
     * @ORM\GeneratedValue(strategy="AUTO")
     */
    private $id;

    /**
     * @var string
     *
     * @ORM\Column(name="title", type="string", length=255)
     * @Assert\NotBlank
     */
    private $title;

    /**
     * @var string
     *
     * @ORM\Column(name="content", type="text")
     * @Assert\NotBlank
     */
    private $content;

    /**
     * @var Author
     *
     * @ORM\ManyToOne(targetEntity="Author", inversedBy="posts")
     * @ORM\JoinColumn(name="author_id", referencedColumnName="id", nullable=false)
     * @Assert\NotBlank
     */
    private $author;

    /**
     * @var string
     *
     * @ORM\Column(name="cover", type="string", length=255, nullable=true)
     */
    private $cover;

    /**
     * @Assert\File(maxSize="1000000")
     */
    private $file;


    /**
     * Get id
     *
     * @return integer 
     */
    public function getId()
    {
        return $this-&gt;id;
    }

    /**
     * Set title
     *
     * @param string $title
     * @return Post
     */
    public function setTitle($title)
    {
        $this-&gt;title = $title;

        return $this;
    }

    /**
     * Get title
     *
     * @return string 
     */
    public function getTitle()
    {
        return $this-&gt;title;
    }

    /**
     * Set content
     *
     * @param string $content
     * @return Post
     */
    public function setContent($content)
    {
        $this-&gt;content = $content;

        return $this;
    }

    /**
     * Get content
     *
     * @return string 
     */
    public function getContent()
    {
        return $this-&gt;content;
    }

    /**
     * Set author
     *
     * @param \Tableless\ModelBundle\Entity\Author $author
     * @return Post
     */
    public function setAuthor(\Tableless\ModelBundle\Entity\Author $author)
    {
        $this-&gt;author = $author;

        return $this;
    }

    /**
     * Get author
     *
     * @return \Tableless\ModelBundle\Entity\Author 
     */
    public function getAuthor()
    {
        return $this-&gt;author;
    }

    // métodos criados

    /**
     * Get cover
     *
     * @return string
     */
    public function getCover()
    {
        return $this-&gt;cover;
    }


    /**
     * Set cover
     *
     * @param string $cover
     * @return Image
     */
    public function setCover($cover)
    {
        $this-&gt;cover = $cover;
    }

    /**
     * Get file.
     *
     * @return UploadedFile
     */
    public function getFile()
    {
        return $this-&gt;file;
    }

    /**
     * Sets file.
     *
     * @param UploadedFile $file
     */
    public function setFile(UploadedFile $file = null)
    {
        $this-&gt;file = $file;
    }

    /**
     * Relative path.
     * Get web path to upload directory.
     *
     * @return string
     */
    protected function getUploadPath()
    {
        return 'uploads/covers';
    }

    /**
     * Absolute path.
     * Get absolute path to upload directory.
     *
     * @return string
     */
    protected function getUploadAbsolutePath()
    {
        return __DIR__ . '/../../../../web/' . $this-&gt;getUploadPath();
    }

    /**
     * Relative path.
     * Get web path to a cover.
     *
     * @return null|string
     */
    public function getCoverWeb()
    {
        return null === $this-&gt;getCover()
            ? null
            : $this-&gt;getUploadPath() . '/' . $this-&gt;getCover();
    }

    /**
     * Get path on disk to a cover.
     *
     * @return null|string
     *   Absolute path.
     */
    public function getCoverAbsolute()
    {
        return null === $this-&gt;getCover()
            ? null
            : $this-&gt;getUploadAbsolutePath() . '/' . $this-&gt;getCover();
    }

    /**
     * Upload a cover file.
     */
    public function upload()
    {
        if (null === $this-&gt;getFile()) {
            return;
        }
        $filename = $this-&gt;getFile()-&gt;getClientOriginalName();
        $this-&gt;getFile()-&gt;move($this-&gt;getUploadAbsolutePath(), $filename);
        $this-&gt;setCover($filename);
        $this-&gt;setFile();
    }
}
</pre>

## Configurando o controller

Para que nossos formulários de posts tenham acesso ao upload, temos que configurar o controller PostController.
  
Entre no PostController, caminho: src/Tableless/CoreBundle/Controller/PostController.php, e no método createAction, insira o código $entity->upload(); veja na linha 15:

<pre class="lang-php">/** 
     * Creates a new Post entity. 
     * 
     * @Route("/", name="post_create") 
     * @Method("POST") 
     * @Template("TablelessCoreBundle:Post:new.html.twig") 
     */ 
    public function createAction(Request $request) 
    { 
        $entity = new Post(); 
        $form = $this-&gt;createCreateForm($entity); 
        $form-&gt;handleRequest($request); 

        if ($form-&gt;isValid()) { 
            $entity-&gt;upload(); 
            $em = $this-&gt;getDoctrine()-&gt;getManager(); 
            $em-&gt;persist($entity); 
            $em-&gt;flush(); 

            return $this-&gt;redirect($this-&gt;generateUrl('post_show', array('id' =&gt; $entity-&gt;getId()))); 
        } 

        return array( 
            'entity' =&gt; $entity, 
            'form'   =&gt; $form-&gt;createView(), 
        ); 
    }
</pre>

Temos que fazer o mesmo procedimento com o método updateAction na linha 23, veja:

<pre class="lang-php">/** 
     * Edits an existing Post entity. 
     * 
     * @Route("/{id}", name="post_update") 
     * @Method("PUT") 
     * @Template("TablelessModelBundle:Post:edit.html.twig") 
     */ 
    public function updateAction(Request $request, $id) 
    { 
        $em = $this-&gt;getDoctrine()-&gt;getManager(); 

        $entity = $em-&gt;getRepository('TablelessModelBundle:Post')-&gt;find($id); 

        if (!$entity) { 
            throw $this-&gt;createNotFoundException('Unable to find Post entity.'); 
        } 

        $deleteForm = $this-&gt;createDeleteForm($id); 
        $editForm = $this-&gt;createEditForm($entity); 
        $editForm-&gt;handleRequest($request); 

        if ($editForm-&gt;isValid()) { 
            $entity-&gt;upload(); 
            $em-&gt;flush(); 

            return $this-&gt;redirect($this-&gt;generateUrl('post_edit', array('id' =&gt; $id))); 
        } 

        return array( 
            'entity'      =&gt; $entity, 
            'edit_form'   =&gt; $editForm-&gt;createView(), 
            'delete_form' =&gt; $deleteForm-&gt;createView(), 
        ); 
    } 

</pre>

## Configurando os formulários

Pronto, nossa entidade e controller de posts, estão configurados para receberem o upload, porém temos que configurar nossos formulários. Entre no PostType.php, para fazermos as configurações necessárias, caminho: src/Tableless/ModelBundle/Form/PostType, e no método buildForm adicione o &#8216;file&#8217;, veja na linha 10.

<pre class="lang-php">/** 
     * @param FormBuilderInterface $builder 
     * @param array $options 
     */ 
    public function buildForm(FormBuilderInterface $builder, array $options) 
    { 
        $builder 
            -&gt;add('title') 
            -&gt;add('content') 
            -&gt;add('file') 
            -&gt;add('author') 
        ; 
    }
</pre>

## Atualizando o banco de dados

Para vermos a mágica acontecer, só precisamos, atualizar nosso banco, para isso entre no terminal e digite:

<pre class="lang-bash">$ php app/console doctrine:schema:update --force 
</pre>

Pronto! Nosso upload de imagem, está pronto, veja a imagem:

[<img src="http://tableless.com.br/uploads/2015/04/01.png" alt="Botão de upload no formulário no symfony" width="750" height="403" class="alignnone size-full wp-image-48201" />][1]

## Configurando as views

Agora temos que configurar nossas views para que as mesmas apresentem as imagens. Entre na view index.html.twig, caminho: src/Tablesless/CoreBundle/Resources/views/IndexController/index.html.twig, mude a linha 21.

mude de:

<pre class="lang-php">&lt;img class="img-responsive" src="{{ asset('logo-tableless.png') }}" alt="img" title="img"/&gt;
</pre>

para:

<pre class="lang-php">&lt;img class="img-responsive" src="{{ asset(post.getCoverWeb) }}" alt="{{ post.cover }}" title="{{ post.cover }}"/&gt;
</pre>

Vamos entrar em nossa view show.html.twig, caminho: caminho: src/Tablesless/CoreBundle/Resources/views/IndexController/show.html.twig, e vamos acrescentar a mesma linha acima do título, ou onde acharem melhor, veja:

<pre class="lang-php">&lt;article class="col-lg-12" &gt;

&lt;img class="img-responsive" src="{{ asset(post.getCoverWeb) }}" alt="{{ post.cover }}" title="{{ post.cover }}"/&gt;

&lt;h1&gt;{{ post.title }}&lt;/h1&gt;
</pre>

Vamos fazer os testes, criando um novo post, e inserindo uma imagem.
  
Observe a imagem na pasta web/uploads/cover.

[<img src="http://tableless.com.br/uploads/2015/04/02.png" alt="Pasta de upload no symfony" width="750" height="403" class="alignnone size-full wp-image-48205" />][2]

## Conclusão

Pronto, nosso simples projeto está fazendo upload de imagens para cada post, no próximo tutorial vamos aprender a configurar um Bundle pronto, disponibilizado pela comunidade, onde faremos a paginação de resultados para nossa página index.

Links dos tutoriais anteriores:
  
<a href="http://tableless.com.br/iniciando-com-symfony-2/" title="instalação" target="_blank">Iniciando com Symfony 2 – Instalação</a>
  
<a href="http://tableless.com.br/iniciando-com-symfony-2-parte-02/" title="parte 02" target="_blank">Iniciando com Symfony 2 – parte 02</a>
  
<a href="http://tableless.com.br/iniciando-com-symfony-2-parte-03/" title="parte 03" target="_blank">Iniciando com Symfony 2 – parte 03</a>
  
<a href="http://tableless.com.br/iniciando-com-symfony-2-parte-04/" title="parte 04" target="_blank">Iniciando com Symfony 2 – parte 04</a>
  
<a href="http://tableless.com.br/iniciando-com-symfony-2-parte-05/" title="parte 05" target="_blank">Iniciando com Symfony 2 – parte 05</a>
  
<a href="http://tableless.com.br/iniciando-com-symfony-2-parte-06/" title="parte 06" target="_blank">Iniciando com Symfony 2 – parte 06</a>

O projeto encontra-se no <a href="https://github.com/candidosouza/tableless" title="GitHub do projeto" target="_blank">GitHub</a>!

 [1]: http://tableless.com.br/uploads/2015/04/01.png
 [2]: http://tableless.com.br/uploads/2015/04/02.png