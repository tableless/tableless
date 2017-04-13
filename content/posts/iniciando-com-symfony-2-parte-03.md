---
title: Iniciando com Symfony 2 – Parte 03
author: Candido Souza
type: post
date: 2015-02-18
excerpt: Nesse tutorial vamos criar uma entidade e fazer o CRUD para nossa aplicação, e para agilizar nosso processo, continuaremos a usar o componente Console do Symfony 2, porém, em conjundo com Doctrine ORM.
url: /iniciando-com-symfony-2-parte-03/
categories:
  - Back-end
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
<a href="http://tableless.com.br/iniciando-com-symfony-2-parte-02/" title="Iniciando com Symfony - parte 2" target="_blank">Dando continuidade ao tutorial anterior</a>, vamos continuar usando o componente console do Symfony, agora criaremos uma entidade, para acessar o banco de dados, usando o Doctrine ORM.

## Banco de dados com Doctrine ORM

Quando falamos de banco de dados em projetos com Symfony, estamos falando de Doctrine ORM (Object Relational Mapper), onde criamos uma camada de persistência entre a aplicação e um banco de dados, que mapeia nossas tabelas com entidades, para que possamos acessar o banco.

Não vou me aprofundar sobre Doctrine, porém, o que você precisa saber é que o Doctrine é um projeto espetacular e grandioso, muito usado pela comunidade, para projetos robustos.

## Iniciando com Doctrine ORM

O Doctrine já vem instalado e configurado no Symfony. Lembrando que você pode instalá-lo <a href="https://packagist.org/packages/doctrine/orm" title="Doctrine ORM" target="_blank">separadamente via Composer</a>. <a href="http://tableless.com.br/iniciando-com-symfony-2/" title="Instalação do Symfony" target="_blank">No primeiro post que escrevi</a> sobre a instalação do Symfony, nós configuramos as opções de banco de dados, o host, usuário e senha. Vale lembrar que são de configuração pessoais, configuradas em sua máquina.
  
No meu caso, configurei de acordo com minhas configurações do MySQL. Também demos um nome para o banco de dados que vamos utilizar agora e que foi configurado com o nome “symfony”. Porém este não está criado, vamos criá-lo neste momento usando o componente console do Symfony em conjunto com o Doctrine.

Vamos digitar no terminal para criar nosso banco:

<pre class="lang-bash">$ php app/console doctrine:database:create
</pre>

E obteremos a resposta: Banco de dados criado para a conexão, com o nome &#8216;symfony&#8217;.

<pre class="lang-bash">$ Created database for connection named 'symfony'
</pre>

## Gerando Entidades

Agora que nosso banco foi gerado, vamos iniciar criando uma entidade. No Doctrine são objetos leves que contêm propriedades persistentes, que são salvos e recuperados do banco de dados por recursos de mapeamento de dados.

Para gerarmos uma entidade vamos digitar no terminal:

<pre class="lang-bash">$ php app/console generate:doctrine:entity
</pre>

Neste momento o console nos dá a dica do que devemos fazer:

&#8220;Em primeiro lugar, você precisa dar o nome para a entidade que pretende gerar.
  
Você deve usar a notação de atalho como AcmeBlogBundle:Post.&#8221;

Em nosso caso vamos digitar &#8220;TablelessModelBundle:Post&#8221;, para criar a entidade Post no bundle TablelessModelBundle.

<pre class="lang-bash">$ TablelessModelBundle:Post
</pre>

Feito isso, o console nos pergunda: Qual o formato que vamos usar para obter as informações de mapeamento? Por padrão ele nos indica annotation, vamos deixar como está e damos enter.

<pre class="lang-bash">$ Configuration format (yml, xml, php, or annotation) [annotation]:
</pre>

As annotations são usadas pelo Doctrine para mapear as entidades, e obter informações por meio delas.

Após darmos o enter, o console nos indica a inserir novos campos, (Obs: automaticamente, já foi gerado o &#8220;id&#8221; como primary key), e nos pergunta qual o nome do novo campo que vamos criar:

<pre class="lang-bash">$ New field name (press  to stop adding fields):
</pre>

Você pode interromper, apenas dando um enter, em nosso caso vamos continuar, digitando o nosso primeiro campo que será &#8220;title&#8221;, o titulo de nosso post, damos enter.

<pre class="lang-bash">$ New field name (press  to stop adding fields):title
</pre>

Nos pergunta qual o tipo, que vamos usar nesse campo, e ele nos indica “string”, vamos deixar como está, apenas damos um enter.

<pre class="lang-bash">$ Field type [string]:
</pre>

A próxima pergunta é: Qual o comprimento desse campo? E por padrão nos indica &#8220;255&#8221;, você pode deixar assim, em nosso caso vamos digitar &#8220;150&#8221;, como é um título, para esse projeto não vejo necessidade de mais, damos enter.

<pre class="lang-bash">$ Field length [255]:150
</pre>

Criamos nosso primeiro campo na entidade, como é um post, vamos precisar além do titulo, um conteúdo, quando o post foi criado, e quando foi atualizado, então vamos criar nosso próximo campo, digitamos &#8220;content&#8221;.

<pre class="lang-bash">$ New field name (press  to stop adding fields): content
</pre>

O tipo deste campo será um texto, digitamos &#8220;text&#8221;.

<pre class="lang-bash">$ Field type [string]:text
</pre>

Automaticamente, o console não nos pede o tamanho, pois é um campo do tipo text. Vamos para o nosso próximo campo, por convenção digitamos createdAt.

<pre class="lang-bash">$ New field name (press  to stop adding fields): createdAt
</pre>

O tipo será uma data, então digitamos &#8220;datetime&#8221;.

<pre class="lang-bash">$ Field type [string]: datetime
</pre>

Vamos para o próximo campo. Nosso post, pode ser atualizado, e para sabermos qual foi a data de atualização vamos criar um campo para isso, digitamos &#8220;updatedAt&#8221;, também com o tipo &#8220;datetime&#8221;.

<pre class="lang-bash">$ New field name (press  to stop adding fields): updatedAt
</pre>

Tipo

<pre class="lang-bash">$ Field type [string]: datetime
</pre>

Como vamos criar um simples blog, e não vamos fazer nada complexo, deixaremos somente estes campos, você pode criar mais campos como texto de introdução, etc, nesse momento vamos deixar assim, e quando o console nos perguntar novamente sobre um novo campo, não vamos digitar nada, apena vamos dar um enter, para entrarmos no processo de finalização.

<pre class="lang-bash">$ New field name (press  to stop adding fields):
</pre>

Após o enter, ele nos pergunta se queremos criar uma classe de repositório vazia para a nossa entidade Post, e por padrão, nos indica [não], no momento não vamos usar repositórios, abordaremos isso mais pra frente, novamente damos enter.

<pre class="lang-bash">$ Do you want to generate an empty repository class [no]?
</pre>

Nesse momento o console nos pergunta, se confirmamos a geração da nossa entidade, por padrão ele nos indica [Sim], como queremos, damos enter.

<pre class="lang-bash">$ Do you confirm generation [yes]? 
</pre>

Pronto, nossa primeira entidade está criada!
  
Ao entrarmos em nosso projeto, notaremos que uma pasta &#8220;Entity&#8221; foi criada, e nela teremos nossa entidade &#8220;Post&#8221;.

[<img src="http://tableless.com.br/uploads/2015/02/011.png" alt="Criando entidades no symfony" width="750" height="403" class="alignnone size-full wp-image-46965" srcset="uploads/2015/02/011.png 750w, uploads/2015/02/011-259x139.png 259w, uploads/2015/02/011-400x215.png 400w" sizes="(max-width: 750px) 100vw, 750px" />][1]

Nossa entidade Post criada:

<pre class="lang-php">&lt;?php

namespace Tableless\ModelBundle\Entity;

use Doctrine\ORM\Mapping as ORM;

/**
 * Post
 *
 * @ORM\Table()
 * @ORM\Entity
 */
class Post
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
     */
    private $title;

    /**
     * @var string
     *
     * @ORM\Column(name="content", type="text")
     */
    private $content;

    /**
     * @var \DateTime
     *
     * @ORM\Column(name="createdAt", type="datetime")
     */
    private $createdAt;

    /**
     * @var \DateTime
     *
     * @ORM\Column(name="updatedAt", type="datetime")
     */
    private $updatedAt;


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
     * Set createdAt
     *
     * @param \DateTime $createdAt
     * @return Post
     */
    public function setCreatedAt($createdAt)
    {
        $this-&gt;createdAt = $createdAt;

        return $this;
    }

    /**
     * Get createdAt
     *
     * @return \DateTime 
     */
    public function getCreatedAt()
    {
        return $this-&gt;createdAt;
    }

    /**
     * Set updatedAt
     *
     * @param \DateTime $updatedAt
     * @return Post
     */
    public function setUpdatedAt($updatedAt)
    {
        $this-&gt;updatedAt = $updatedAt;

        return $this;
    }

    /**
     * Get updatedAt
     *
     * @return \DateTime 
     */
    public function getUpdatedAt()
    {
        return $this-&gt;updatedAt;
    }
}

</pre>

## Configurando a entidade

Vamos fazer algumas modificações.
  
Daremos o nome &#8220;post&#8221; pra nossa tabela quando ela for criada, para isso temos que configurar via annotation para que o Doctrine saiba. Para fazer isso vamos adicionar na linha 10 a annotation correspondente:
  
Obs: As annotations do Doctrine, começam com &#8220;@ORM\&#8221;, o restante é documentação…
  
Verifique a alteração na linha 10, vamos inserir: (name=”post”).
  
Caso não façamos essa alteração, não ocorrerá erro, porém por padrão o Doctrine criará uma tabela com o nome da classe &#8220;Post&#8221;, com a letra “P” maiúscula.

<pre class="lang-php">/**
 * Post
 *
 * @ORM\Table(name="post")
 * @ORM\Entity
 */
class Post
{
...
</pre>

Mudaremos também o nome da coluna &#8220;createdAt&#8221; para &#8220;creadet_at&#8221; na linha 41 de nossa entidade, no caso do código abaixo, a linha 4.

<pre class="lang-php">/**
 * @var \DateTime
 *
 * @ORM\Column(name="created_at", type="datetime")
 */
 private $createdAt;
...
</pre>

E a linha 48, de &#8220;updatedAt&#8221; para &#8220;updated_at&#8221;, no código abaixo a linha 4.

<pre class="lang-php">/**
 * @var \DateTime
 *
 * @ORM\Column(name="updated_at", type="datetime")
 */
 private $updatedAt;
...
</pre>

Precisamos que, ao criarmos nosso post, seja inserido automaticamente a data de criação, e a data de atualização, para isso vamos criar um método construtor em nossa entidade, veja abaixo:

<pre class="lang-php">/**
 * Construct
 */
 public function __construct()
 {
    $this-&gt;createdAt = new \DateTime();
    $this-&gt;updatedAt = new \DateTime();
 }
</pre>

## Validando

Agora vamos fazer uma validação, para que nossos campos &#8220;title&#8221; e &#8220;content&#8221;, não aceitem conteúdos nulos, em brancos. Para isso chamaremos a classe Constraints do Symfony, dando um &#8220;use&#8221; nesse objeto em nossa entidade, por padrão daremos o apelido de Assert para Constraints. Veja na linha 06:

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
class Post
{
</pre>

Para que a validação seja feita colocaremos a annotation &#8220;@Assert\NotBlank&#8221; nos campos que queremos, veja na linha 5 e na linha 13:

<pre class="lang-php">/**
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
</pre>

Pronto! Nossa entidade Post está criada e configurada, porém faremos modificações no fututo para que ela se adeque melhor em nosso projeto.

## Gerando CRUD com Doctrine ORM

Agora que nossa entidade está concluída, vamos fazer um CRUD, para que possamos inserir, atualizar, visualizar e deletar nossos posts.
  
Porém antes, precisamos criar nossas tabelas, para fazer isso, vamos voltar para o terminal e digitar:

<pre class="lang-bash">$ php app/console doctrine:schema:create
</pre>

Receberemos a resposta do console:
  
&#8220;ATENÇÃO: Esta operação não deve ser executado em um ambiente de produção.
  
Criação de esquema de banco de dados&#8230;
  
Esquema de banco de dados criado com sucesso!&#8221;

<pre class="lang-bash">ATTENTION: This operation should not be executed in a production environment.

Creating database schema...
Database schema created successfully!
</pre>

Vamos ao CRUD! Para fazer um CRUD com Doctrine, é extremamente fácil, vamos digitar no terminal:

<pre class="lang-bash">$ php app/console generate:doctrine:crud
</pre>

Ao digitarmos o comando acima e darmos o enter, entramos no assistente para criarmos nosso CRUD, e ele nos pede para que informemos a entidade que queremos criar o CRUD, então digitamos: TablelessModelBundle:Post

<pre class="lang-bash">$ The Entity shortcut name: TablelessModelBundle:Post
</pre>

Logo após, nos pergunta se queremos gerar as ações de &#8220;gravação&#8221;, ele nos indica [não], porém nós queremos, então digitamos &#8220;yes&#8221;.

<pre class="lang-bash">$ Do you want to generate the "write" actions [no]? yes
</pre>

Nos pergunta como vamos configurar nosso CRUD, e nos indica [annotation], só damos um enter para prosseguir.

<pre class="lang-bash">$ Configuration format (yml, xml, php, or annotation) [annotation]:
</pre>

Após o enter, nos pergunta como vai ser a rota que vamos usar, e nos indica [/post], vamos usar essa mesma, damos um enter.

<pre class="lang-bash">$ Routes prefix [/post]:
</pre>

Nos pergunta se confirmamos a geração, e nos indica [yes], sim queremos, damos enter para prosseguir.

<pre class="lang-bash">$ Do you confirm generation [yes]?
</pre>

Pronto! CRUD criado, simples não!

Nesse momento vamos fazer uma configuração somente para vermos nossa aplicação rodando, porém não vamos usar essa rota, é somente para vermos se está tudo certo. Entre no arquivo app/config/route.yml e vamos adicionar a rota desse CRUD:

<pre class="lang-php">tableless_model:
    resource: "@TablelessModelBundle/Controller/"
    type:     annotation
    prefix:   /
</pre>

Agora vamos rodar nosso aplicação pelo console:

<pre class="lang-bash">$ php app/console server:run
</pre>

E vamos entrar no navegador com a url:

http://127.0.0.1:8000/post/

Para inserirmos um novo post, é só dar um clique, em &#8220;Create a new entry&#8221;.
  
Eu inseri um post, com um texto “Lorem Ipsum”, apenas para reprodução das páginas, veja o resultado abaixo:

Lista de posts = url: http://127.0.0.1:8000/post/
  
Novo post = url: http://127.0.0.1:8000/post/new
  
Ver o post = url: http://127.0.0.1:8000/post/1
  
Editar post = url: http://127.0.0.1:8000/post/1/edit

[<img src="http://tableless.com.br/uploads/2015/02/031.png" alt="Páginas criadas" width="750" height="403" class="alignnone size-full wp-image-47111" srcset="uploads/2015/02/031.png 750w, uploads/2015/02/031-259x139.png 259w, uploads/2015/02/031-400x215.png 400w" sizes="(max-width: 750px) 100vw, 750px" />][2]

Ao navegar pelas páginas, verificará, que não tem estilização, porém está funcional, vamos fazer isso mais tarde, poderá verificar também seu banco de dados, e verá que foi criado um banco de dados com o nome &#8220;symfony&#8221;, nesse banco, encontrará a tabela &#8220;post&#8221; que criamos.

[<img src="http://tableless.com.br/uploads/2015/02/021.png" alt="Table post no banco de dados" width="750" height="403" class="alignnone size-full wp-image-47098" srcset="uploads/2015/02/021.png 750w, uploads/2015/02/021-259x139.png 259w, uploads/2015/02/021-400x215.png 400w" sizes="(max-width: 750px) 100vw, 750px" />][3]

## Concluindo

Uma observação importante, estamos criando nossos códigos por linha de comando usando o console, é uma forma de mostrar a agilidade e produtividade, que o Symfony e o Doctrine nos permite, porém para entender o mínimo, o funcionamento do Symfony, ou de qualquer outro framework PHP, é de extrema importância saber PHP Orientado a Objetos, padrão MVC e outros Design Patterns. Fazer a reprodução codificando, sem usar o console, é uma boa forma de aprender e entender o funcionamento do Symfony.

Este projeto <a href="https://github.com/candidosouza/tableless" title="GitHub do projeto" target="_blank">encontra-se no gitHub</a>.

 [1]: http://tableless.com.br/uploads/2015/02/011.png
 [2]: http://tableless.com.br/uploads/2015/02/031.png
 [3]: http://tableless.com.br/uploads/2015/02/021.png