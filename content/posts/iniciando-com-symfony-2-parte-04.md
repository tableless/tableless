---
title: Iniciando com Symfony 2 – Parte 04
author: Candido Souza
type: post
date: 2015-03-04
excerpt: Nesse tutorial vamos criar uma entidade Author e fazer o relacionamento com a entidade Post criada anteriormente, usando o componente Console do Symfony em conjundo com Doctrine ORM.
url: /iniciando-com-symfony-2-parte-04/
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
Anteriormente, <a href="http://tableless.com.br/iniciando-com-symfony-2-parte-03/" title="Iniciando com symfony - parte-03" target="_blank">criamos a entidade Post</a>, vamos dar continuidade ao nosso simples projeto, criando uma entidade Author, faremos o relacionamento para que cada autor fique ligado ao post que criou.

## Criando a entidade Author

Vamos criar a entidade Author, entre no terminal e digite:

<pre class="lang-bash">$ php app/console generate:doctrine:entity
</pre>

Vamos digitar o nome da entidade como : TablelessModelBundle:Author.

<pre class="lang-bash">$ The Entity shortcut name: TablelessModelBundle:Author
</pre>

Vamos mapeá-la usando annotation. Apenas damos enter.

<pre class="lang-bash">$ Configuration format (yml, xml, php, or annotation) [annotation]:
</pre>

O assistente nos pergunta: Qual será o nome do nosso campo?
  
Digitamos &#8220;name&#8221; e damos enter.

<pre class="lang-bash">$ New field name (press  to stop adding fields): name
</pre>

Será do tipo string.

<pre class="lang-bash">$ Field type [string]:
</pre>

Com o tamanho de 100.

<pre class="lang-bash">$ Field length [255]: 100
</pre>

Quando o assistente nos perguntar novamente: Qual será o novo campo? Damos enter para entrarmos no processo de finalização. E nos pergunta, se queremos criar uma classe de repositório, ele nos indica não, vamos apenas dar um enter.

<pre class="lang-bash">Do you want to generate an empty repository class [no]?
</pre>

E para finalizar, o assistente pergunta se realmente queremos gerar a entidade. Como queremos, digitamos apenas enter.

<pre class="lang-bash">$ Do you confirm generation [yes]?
</pre>

Nossa entidade Author está pronta.

Ao entrarmos na pasta src/Tableless/ModelBundle/Entity/ vamos encontrá-la.

[<img src="http://tableless.com.br/uploads/2015/03/02.png" alt="Entidade Author criada" width="750" height="403" class="alignnone size-full wp-image-47412" srcset="uploads/2015/03/02.png 750w, uploads/2015/03/02-259x139.png 259w, uploads/2015/03/02-400x215.png 400w" sizes="(max-width: 750px) 100vw, 750px" />][1]

Agora devemos adicionar a annotations, @ORM\Table(name=&#8221;author&#8221;) para o nome da nossa tabela, veja na linha 10:

Veja toda a entidade Author:

<pre class="lang-php">&lt;?php 

namespace Tableless\ModelBundle\Entity; 

use Doctrine\ORM\Mapping as ORM; 

/** 
 * Author 
 * 
 * @ORM\Table(name="author")
 * @ORM\Entity 
 */ 
class Author 
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
     * @ORM\Column(name="name", type="string", length=100) 
     */ 
    private $name; 

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
     * Set name 
     * 
     * @param string $name 
     * @return Author 
     */ 
    public function setName($name) 
    { 
        $this-&gt;name = $name; 
        return $this; 
    } 

    /** 
     * Get name 
     * 
     * @return string 
     */ 
    public function getName() 
    { 
        return $this-&gt;name; 
    } 
} 
</pre>

## Configurando o projeto

Nesse momento vamos criar uma classe abstrata com o nome Timestampable, para que não fiquemos repetindo código, pois entidade Author também receberá uma data de criação e data de atualização.

Vamos lá!

Entre na pasta src/Tableless/ModelBundle/Entity/, e vamos criar uma classe abstrata com o nome Timestampable, para que possamos mapeá lá vamos usar a classe do Doctrine Mapping e vamos dar um apelido de ORM, e fazer as annotations correspondentes.

Nesse momento, ficar explicando detalhe por detalhe levará muito tempo, e o tutorial ficará extenso, veja a classe Timestampable pronta abaixo:

<pre class="lang-php">&lt;?php 

namespace Tableless\ModelBundle\Entity; 

use Doctrine\ORM\Mapping as ORM; 
use Symfony\Component\Validator\Constraints as Assert; 

/** 
 * Timestampable abstract class 
 * @ORM\MappedSuperclass 
 */ 
abstract class Timestampable 
{ 
    /** 
     * @var \DateTime 
     * 
     * @ORM\Column(name="created_at", type="datetime") 
     * @Assert\NotBlank 
     */ 
    private $createdAt; 

    /** 
     * @var \DateTime 
     * 
     * @ORM\Column(name="updated_at", type="datetime") 
     * @Assert\NotBlank 
     */ 
    private $updatedAt; 

    /** 
     * Construct 
     */ 
    public function __construct() 
    { 
        $this-&gt;createdAt = new \DateTime(); 
        $this-&gt;updatedAt = new \DateTime(); 
    } 

    /** 
     * Set createdAt 
     * 
     * @param $createdAt 
     */ 
    public function setCreatedAt($createdAt) 
    { 
        $this-&gt;createdAt = $createdAt; 
    } 

    /** 
     * Get CreatedAt 
     * 
     * @return \DateTime 
     */ 
    public function getCreatedAt() 
    { 
        return $this-&gt;createdAt; 
    } 

    /** 
     * Set UpdatedAt 
     * 
     * @param \DateTime $updatedAt 
     */ 
    public function setUpdatedAt($updatedAt) 
    { 
        $this-&gt;updatedAt = $updatedAt; 
    } 
    /** 
     * Get UpdateAt 
     * 
     * @return \DateTime 
     */ 
    public function getUpdatedAt() 
    { 
        return $this-&gt;updatedAt; 
    } 
}
</pre>

Vamos estender essa classe na entidade Author, veja abaixo na linha 13:

<pre class="lang-php">&lt;?php 

namespace Tableless\ModelBundle\Entity; 

use Doctrine\ORM\Mapping as ORM; 

/** 
 * Author 
 * 
 * @ORM\Table(name="author")
 * @ORM\Entity 
 */ 
class Author extends Timestampable 
{ 
…
</pre>

Temos que validar os campos da entidade Author, vamos dar um use em Constraints e apelidá-la como Assert:

<pre class="lang-php">use Symfony\Component\Validator\Constraints as Assert;
</pre>

vamos validar o campo name com @Assert\NotBlank, veja abaixo:

<pre class="lang-php">/** 
* @var string 
* 
* @ORM\Column(name="name", type="string", length=100) 
* @Assert\NotBlank 
*/ 
private $name; 
</pre>

Veja a entidade Author depois da configuração:

<pre class="lang-php">&lt;?php 

namespace Tableless\ModelBundle\Entity; 

use Doctrine\ORM\Mapping as ORM; 
use Symfony\Component\Validator\Constraints as Assert; 

/** 
 * Author 
 * 
 * @ORM\Table(name="author")
 * @ORM\Entity 
 */ 
class Author extends Timestampable 
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
     * @ORM\Column(name="name", type="string", length=100) 
     * @Assert\NotBlank 
     */ 
    private $name; 


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
     * Set name 
     * 
     * @param string $name 
     * @return Author 
     */ 
    public function setName($name) 
    { 
        $this-&gt;name = $name; 
 
        return $this; 
    } 

    /** 
     * Get name 
     * 
     * @return string 
     */ 
    public function getName() 
    { 
        return $this-&gt;name; 
    } 
} 
</pre>

## Configurando a entidade Post

Como criamos um classe abstrata, vamos alterar a entidade Post para que ela estenda a entidade Timestampable.

Exclua os atributos $createdAt e $updatedAt e os métodos setCreatedAt(), getCreatedAt(), setUpdatedAt(), getUpdatedAt() e o __contruct(), e vamos estender a classe Timestampable, depois de configurada, a entidade Post ficará assim:

<pre class="lang-php">&lt;?php 

namespace Tableless\ModelBundle\Entity; 

use Doctrine\ORM\Mapping as ORM; 
use Symfony\Component\Validator\Constraints as Assert; 

/** 
 * Post 
 * 
 * @ORM\Table(name="post") 
 * @ORM\Entity 
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
} 
</pre>

## Atualizando o banco de dados

Geramos a entidade Author e alteramos a entidade Post, dessa forma devemos atualizar nosso banco, para que o mesmo fique configurado de acordo com as entidades.

Vamos ao terminal, e para atualizar o banco de dados vamos digitar o código:

<pre class="lang-bash">$ php app/console doctrine:schema:update --force
</pre>

Teremos o resultado:

<pre class="lang-bash">Updating database schema... 
 Database schema updated successfully! "1" queries were execute
</pre>

Entrando no banco de dados vamos perceber que a tabela author criada:

[<img src="http://tableless.com.br/uploads/2015/03/03.png" alt="Tabela Author" width="750" height="403" class="alignnone size-full wp-image-47434" srcset="uploads/2015/03/03.png 750w, uploads/2015/03/03-259x139.png 259w, uploads/2015/03/03-400x215.png 400w" sizes="(max-width: 750px) 100vw, 750px" />][2]

## Criando o CRUD da entidade Author

Depois da configuração das nossa entidade, vamos gerar o CRUD da entidade Author. Vamos digitar no console:

<pre class="lang-bash">$ php app/console generate:doctrine:crud
</pre>

Digitamos TablelessModelBundle:Author:

<pre class="lang-bash">$ The Entity shortcut name: TablelessModelBundle:Author
</pre>

O assistente nos pergunta se queremos gerar as ações de gravação, digitamos: yes.

<pre class="lang-bash">$ Do you want to generate the "write" actions [no]? Yes
</pre>

Como vamos configurar? Vamos deixar como está, annotation, e damos enter

<pre class="lang-bash">$ Configuration format (yml, xml, php, or annotation) [annotation]:
</pre>

Como será a rota? Vamos deixar como ele nos indica, damos enter.

<pre class="lang-bash">$ Routes prefix [/author]:
</pre>

Vamos confirmar a geração desse CRUD dando enter.

<pre class="lang-bash">$ Do you confirm generation [yes]?
</pre>

Prontinho nosso CRUD da entidade Author está pronto, vamos testar.

Inicie o servidor:

<pre class="lang-bash">$ php app/console server:run
</pre>

entre na url:

http://127.0.0.1:8000/author/

Vamos criar um autor com o nome Tableless

## Relacionamento com Doctrine

Vamos fazer um relacionamento no banco de dados, pois queremos que, ao criarmos um post, o mesmo esteja relacionado com o autor que o criou. Não entraremos em detalhes sobre relacionamento, caso tenha dúvidas, <a href="http://doctrine-orm.readthedocs.org/en/latest/reference/association-mapping.html" title="Documentação de relacionamento com Doctrine" target="_blank">consulte a documentação</a>.

Vamos configurar novamente as entidades para que o relacionamento possa acontecer.

Entre na entidade Post e acrescente o atributo $author com as seguintes annotations:

<pre class="lang-php">/** 
     * @var Author 
     * 
     * @ORM\ManyToOne(targetEntity="Author", inversedBy="posts") 
     * @ORM\JoinColumn(name="author_id", referencedColumnName="id", nullable=false) 
     * @Assert\NotBlank 
     */ 
    private $author;
</pre>

Entre na entidade Author e acrescente o atributo $post, com as seguintes annotations:

<pre class="lang-php">/** 
     * @var ArrayCollection 
     * 
     * @ORM\OneToMany(targetEntity="Post", mappedBy="author", cascade={"remove"}) 
     */ 
    private $post;
</pre>

Precisamos também dar um use na classe ArrayCollection, do Doctrine, pois um autor terá vários posts, e os posts serão buscados como array, insira o código:

<pre class="lang-php">use Doctrine\Common\Collections\ArrayCollection;
</pre>

Vamos criar um construtor, porém a entidade Timestampable já tem um construtor, para resolver esse problema, vamos adicionar um parent::__construct(), veja abaixo:

<pre class="lang-php">/** 
     * Constructor 
     */ 
    public function __construct() 
    { 
         parent::__construct();
	
        $this-&gt;post = new ArrayCollection(); 
    }
</pre>

Agora vamos gerar os métodos necessários da entidade Author, entre no console e digite:

<pre class="lang-bash">$ php app/console generate:doctrine:entities TablelessModelBundle:Author
</pre>

Temos que gerar também para a entidade Post:

<pre class="lang-bash">$ php app/console generate:doctrine:entities TablelessModelBundle:Post
</pre>

Entre novamente na entidade Author e acrescente o método abaixo no final da entidade:

<pre class="lang-php">/** 
     * @return string 
     */ 
    public function __toString() 
    { 
        return $this-&gt;getName(); 
    }
</pre>

Veja como ficou a entidade Author depois de configurarmos:

<pre class="lang-php">&lt;?php 

namespace Tableless\ModelBundle\Entity; 

use Doctrine\ORM\Mapping as ORM; 
use Symfony\Component\Validator\Constraints as Assert; 
use Doctrine\Common\Collections\ArrayCollection; 

/** 
 * Author 
 * 
 * @ORM\Table(name="author") 
 * @ORM\Entity 
 */ 
class Author extends Timestampable 
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
     * @ORM\Column(name="name", type="string", length=100) 
     * @Assert\NotBlank 
     */ 
    private $name; 

    /** 
     * @var ArrayCollection 
     * 
     * @ORM\OneToMany(targetEntity="Post", mappedBy="author", cascade={"remove"}) 
     */ 
    private $post; 

    /** 
     * Constructor 
     */ 
    public function __construct() 
    { 
         parent::__construct();

        $this-&gt;post = new ArrayCollection(); 
    } 

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
     * Set name 
     * 
     * @param string $name 
     * @return Author 
     */ 
    public function setName($name) 
    { 
        $this-&gt;name = $name; 

        return $this; 
    } 

    /** 
     * Get name 
     * 
     * @return string

    */ 
    public function getName() 
    { 
        return $this-&gt;name; 
    } 

    /** 
     * Add post 
     * 
     * @param \Tableless\ModelBundle\Entity\Post $post 
     * @return Author 
     */ 
    public function addPost(\Tableless\ModelBundle\Entity\Post $post) 
    { 
        $this-&gt;post[] = $post; 

        return $this; 
    } 

    /** 
     * Remove post 
     * 
     * @param \Tableless\ModelBundle\Entity\Post $post 
     */ 
    public function removePost(\Tableless\ModelBundle\Entity\Post $post) 
    { 
        $this-&gt;post-&gt;removeElement($post); 
    } 

    /** 
     * Get post 
     * 
     * @return \Doctrine\Common\Collections\Collection 
     */ 
    public function getPost() 
    { 
        return $this-&gt;post; 
    } 

    /** 
     * @return string 
     */ 
    public function __toString() 
    { 
        return $this-&gt;getName(); 
    } 
} 

</pre>

Veja a entidade Post, após a configuração:

<pre class="lang-php">&lt;?php 

namespace Tableless\ModelBundle\Entity; 

use Doctrine\ORM\Mapping as ORM; 
use Symfony\Component\Validator\Constraints as Assert; 

/** 
 * Post 
 * 
 * @ORM\Table(name="post") 
 * @ORM\Entity 
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
} 
</pre>

Agora vamos atualizar o banco de dados para gerar o relacionamento, para isso apague todo o conteúdo das tabelas do banco de dados, caso não o faça, ocorrerá erro,

Após apagar o conteúdo do banco, rode o comando no console:

<pre class="lang-bash">$ php app/console doctrine:schema:update --force
</pre>

## Corrigindo os formulários

Entre na classe PostType, caminho: src/Tableless/ModelBundle/Form/PostType, e acrescente a linha abaixo, no método buildForm:

<pre class="lang-php">-&gt;add('author')
</pre>

Também vamos apagar as linhas:

<pre class="lang-php">-&gt;add('createdAt') 
 -&gt;add('updatedAt') 
</pre>

Pois não precisamos inserir as datas, em que o post foi criado, ou alterado, isso acontecerá automaticamente!

Depois das modificações, o método formBuilder ficará como abaixo:

<pre class="lang-php">/** 
     * @param FormBuilderInterface $builder 
     * @param array $options 
     */ 
    public function buildForm(FormBuilderInterface $builder, array $options) 
    { 
        $builder 
            -&gt;add('title') 
            -&gt;add('content') 
            -&gt;add('author') 
        ; 
    }
</pre>

Tudo configurado para que possamos criar nossos posts.
  
Para verificarmos se está tudo correto, precisamos criar primeiramente um autor, depois criamos um post, onde teremos que selecionar um autor, para o mesmo.

Veja abaixo:

[<img src="http://tableless.com.br/uploads/2015/03/04.png" alt="autor" width="750" height="403" class="alignnone size-full wp-image-47469" srcset="uploads/2015/03/04.png 750w, uploads/2015/03/04-259x139.png 259w, uploads/2015/03/04-400x215.png 400w" sizes="(max-width: 750px) 100vw, 750px" />][3]

Lembrando que a url de autor é:

http://127.0.0.1:8000/author/

e a url de post é:

http://127.0.0.1:8000/post/

## Conclusão

Vamos terminar este tutorial, pois seu conteúdo está muito extenso, no próximo, vamos fazer as configurações necessárias em nossa simples aplicação, e vamos criar um index, para mostrar nossos posts, que configuraremos com o Bootstrap, e com o template engine twig. O projeto <a href="https://github.com/candidosouza/tableless" title="GitHub do projeto" target="_blank">encontra-se no GitHub</a>!

 [1]: http://tableless.com.br/uploads/2015/03/02.png
 [2]: http://tableless.com.br/uploads/2015/03/03.png
 [3]: http://tableless.com.br/uploads/2015/03/04.png