---
title: Iniciando com Symfony 2 – Parte Final
author: Candido Souza
type: post
date: 2015-06-16
excerpt: Nesse tutorial, vamos instalar o bundle FOSUserBundle, para fazermos a autenticação para a área administrativa do nosso blog.
url: /iniciando-com-symfony-2-parte-final/
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
Chegamos ao final da nossa série sobre Symfony. Se você não leu os outros, no final do artigo há uma [listagem com todos os artigos][1] já publicados dessa série.

No <a href="http://tableless.com.br/iniciando-com-symfony-2-parte-09/" target="_blank">tutorial anterior</a>, instalamos e configuramos o bundle StofDoctrineExtensionsBundle, para fazermos os slugs de nossos posts, agora vamos instalar e configurar o Bundle FOSUserBundle, para fazer a autenticação da área administrativa do nosso blog.

## Instalação do bundle FOSUserBundle.

Para instalar o FOSUserBundle, temos que adicioná-lo em nosso composer.json. Abra o arquivo composer.json e adicione a linha abaixo:

<pre class="lang-html">"friendsofsymfony/user-bundle": "1.3.*"
</pre>

Depois de adicionando o FOSUserBundle no composer, vamos instalá- lo. Entre no terminal e digite:

<pre class="lang-bash">$ composer update
</pre>

Após o Download, o FOSUserBundle está instalado em nossa aplicação.

## Configurando o FOSUserBundle.

A primeira configuração que devemos fazer, é registrar o novo bundle instalado, para isso entre no AppKernel, caminho: app/AppKernel.php

Adicione a linha abaixo no registro de bundles:

<pre class="lang-php">new FOS\UserBundle\FOSUserBundle(),
</pre>

Veja na linha 18:

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
	     new FOS\UserBundle\FOSUserBundle(),
        );

...
</pre>

Pronto, o FOSUserBundle está registrado. 

Agora vamos fazer as configurações no arquivo config.yml, caminho: app/config/config.yml.

Para que o sistema de login venha traduzido, devemos descomentar a linha translator em framework, veja na linha 3 do código abaixo:

De:

<pre class="lang-php">framework:
    #esi:             ~
    #translator:      { fallback: "%locale%" }
</pre>

Para:

<pre class="lang-php">framework:
    #esi:             ~
    translator:      { fallback: "%locale%" }
</pre>

No final do arquivo adicione as configurações abaixo: 

<pre class="lang-html"># FOSUser
fos_user:
    db_driver: orm # other valid values are 'mongodb', 'couchdb' and 'propel'
    firewall_name: main
    user_class: Tableless\UserBundle\Entity\User
</pre>

Perceba que na configuração acima, estamos indicando uma entidade User, porém ainda não existente, vamos criá-la.

## Criando o bundle UserBundle.

Continuando com nossas configurações, podemos criar um novo bundle para que o mesmo fique responsável pelo gerenciamento dos usuários, em nosso caso, vamos criar o bundle, porém só vamos usar para configurar a entidade User, caso queiram fazer outras configurações, o bundle já está criado.
  
Entre no terminal e digite:

<pre class="lang-bash">$ php app/console generate:bundle
</pre>

Digitamos a namespace:

<pre class="lang-bash">Bundle namespace: Tableless/UserBundle
</pre>

O console nos sugere um nome, vamos deixar como está, apenas damos enter:

<pre class="lang-bash">Bundle name [TablelessUserBundle]:
</pre>

No caminho, apenas damos enter:

<pre class="lang-bash">Target directory [/media/candidosouza/Development/GITHUB/tableless/symfony/src]:
</pre>

Usaremos annotation para configurações:

<pre class="lang-bash">Configuration format (yml, xml, php, or annotation): annotation
</pre>

Não vamos querer a geração de toda a estrutura de um bundle, apenas damos enter:

<pre class="lang-bash">Do you want to generate the whole directory structure [no]? 
</pre>

Vamos confirmar a geração do novo bundle, damos enter:

<pre class="lang-bash">Do you confirm generation [yes]? 
</pre>

E vamos registrar esse bundle, somente enter:

<pre class="lang-bash">Confirm automatic update of your Kernel [yes]?
</pre>

E gerar as rotas, damos enter:

<pre class="lang-bash">Confirm automatic update of the Routing [yes]?
</pre>

Pronto, nosso bundle UserBundle está criado, veja:

[<img src="http://tableless.com.br/uploads/2015/06/01.png" alt="pasta" width="750" height="403" class="alignnone size-full wp-image-49557" />][2]

Nosso bundle está criado, vamos criar nossa entidade User.

## Criando a Entidade User.

Vamos entrar no bundle UserBundle, caminho src/Tableless/UserBundle/, e vamos criar uma pasta chamada Entity. Nessa pasta vamos criar uma classe User, que será nossa entidade, veja:

[<img src="http://tableless.com.br/uploads/2015/06/02.png" alt="Entidade User" width="750" height="403" class="alignnone size-full wp-image-49558" />][3]

A nossa entidade User tem que estender a entidade User do FOSUserBundle, vamos dar um use nessa classe e vamos apelida lá de BaseUser, veja:

<pre class="lang-php">use FOS\UserBundle\Entity\User as BaseUser;
</pre>

Também temos que passar as configurações (mapear nossa entidade) via annotation, vamos dar um use na classe Mapping do Doctrine e apelida lá de ORM, veja:

<pre class="lang-php">use Doctrine\ORM\Mapping as ORM;
</pre>

Nossa Entidade terá apenas um atributo id, e um método construtor que chamará construtor pai de entidade BaseUser, juntamente com as respectivas annotations, veja nossa entidade User pronta:

<pre class="lang-php">&lt;?php

namespace Tableless\UserBundle\Entity;

use FOS\UserBundle\Entity\User as BaseUser;
use Doctrine\ORM\Mapping as ORM;

/**
 * @ORM\Entity
 * @ORM\Table(name="fos_user")
 */
class User extends BaseUser
{
    /**
     * @ORM\Id
     * @ORM\Column(type="integer")
     * @ORM\GeneratedValue(strategy="AUTO")
     */
    protected $id;

    public function __construct()
    {
        parent::__construct();
    }
}
</pre>

## Configurações de segurança.

Para configurar a parte de segurança, temos que editar o arquivo security.yml, responsável pela parte de segurança do Symfony, abra o arquivo, caminho: app/config/security.yml.
  
Abrindo o arquivo, vamos perceber que o Symfony está configurando o provider via memória, vamos alterar o provider.

De:

<pre class="lang-php">providers:
    in_memory:
        memory: ~
</pre>

Para:

<pre class="lang-php">providers:
    fos_userbundle:
        id: fos_user.user_provider.username
</pre>

Para criptografar a senha do usuário vamos configurar um encoder, incluindo o código abaixo, que usará o algoritmo sha512, veja:

<pre class="lang-php">encoders:
        FOS\UserBundle\Model\UserInterface: sha512
</pre>

Agora vamos configurar a parte de firewalls, onde estabeleceremos o pattern para ativação do firewalls, que pelo acesso da url será ativado, e qual o tipo de provider que será usado para o processo de autenticação, também passaremos o processo de autenticação apenas pelo formulário, não permitindo outro tipo de requisição, usando o csrf_provider. Vamos permitir o logout, e usuários anônimos nas áreas não restritas, veja:

<pre class="lang-php">firewalls:
        main:
            pattern: ^/
            form_login:
                provider: fos_userbundle
                csrf_provider: form.csrf_provider
            logout:       true
            anonymous:    true
</pre>

Temos que passar qual o tipo de acesso o usuário terá que ter, para acessar determinadas urls, ex: o usuário anônimo, só poderá acessar as urls: qualquer-url/login, qualquer-url/register, e qualquer-url/resetting, e apenas usuários administradores, poderão acessar a url: qualquer-url/admin/, para isso passaremos a configuração de controle de acesso, veja:

<pre class="lang-php">access_control:
        - { path: ^/login$, role: IS_AUTHENTICATED_ANONYMOUSLY }
        - { path: ^/register, role: IS_AUTHENTICATED_ANONYMOUSLY }
        - { path: ^/resetting, role: IS_AUTHENTICATED_ANONYMOUSLY }
        - { path: ^/admin/, role: ROLE_ADMIN }
</pre>

Temos que configurar a hierarquia de usuários cadastrados, onde o admin, poderá ser qualquer usuário cadastrado, e o super admin, será o administrador com total acesso, veja:

<pre class="lang-php">role_hierarchy:
        ROLE_ADMIN:       ROLE_USER
        ROLE_SUPER_ADMIN: ROLE_ADMIN
</pre>

Veja o arquivo security.yml pronto:

<pre class="lang-php">security:
    providers:
        fos_userbundle:
            id: fos_user.user_provider.username

    encoders:
        FOS\UserBundle\Model\UserInterface: sha512

    firewalls:
        main:
            pattern: ^/
            form_login:
                provider: fos_userbundle
                csrf_provider: form.csrf_provider
            logout:       true
            anonymous:    true

    access_control:
        - { path: ^/login$, role: IS_AUTHENTICATED_ANONYMOUSLY }
        - { path: ^/register, role: IS_AUTHENTICATED_ANONYMOUSLY }
        - { path: ^/resetting, role: IS_AUTHENTICATED_ANONYMOUSLY }
        - { path: ^/admin/, role: ROLE_ADMIN }

    role_hierarchy:
        ROLE_ADMIN:       ROLE_USER
        ROLE_SUPER_ADMIN: ROLE_ADMIN
</pre>

Pronto as configurações de segurança, estão prontas.
  
E para finalizar as configurações, temos que passar as rotas do FOSUserBundle onde ficarão registradas no sistema, para isso abra o arquivo routing.yml, caminho: app/config/routing.yml.
  
Com o arquivo aberto vamos inserir as rotas abaixo:

<pre class="lang-php"># FOSUser
fos_user_security:
    resource: "@FOSUserBundle/Resources/config/routing/security.xml"

fos_user_profile:
    resource: "@FOSUserBundle/Resources/config/routing/profile.xml"
    prefix: /profile

fos_user_register:
    resource: "@FOSUserBundle/Resources/config/routing/registration.xml"
    prefix: /register

fos_user_resetting:
    resource: "@FOSUserBundle/Resources/config/routing/resetting.xml"
    prefix: /resetting

fos_user_change_password:
    resource: "@FOSUserBundle/Resources/config/routing/change_password.xml"
    prefix: /profile
</pre>

Para que tudo ocorra bem, temos que atualizar o banco de dados, para criar a tabela dos usuários, entre no terminal e digite:

<pre class="lang-bash">php app/console doctrine:schema:update --force
</pre>

veja:

[<img src="http://tableless.com.br/uploads/2015/06/03.png" alt="Tabela do banco de dados" width="750" height="403" class="alignnone size-full wp-image-49559" />][4]

## Estilizando as templates do FOSUserBundle.

O FOSUserBundle está configurado e instalado em nosso sistema, para que possamos testá-lo, entre no terminal e digite:

<pre class="lang-bash">php app/console router:debug
</pre>

E veremos todas as rotas criadas em nosso sistema através FOSUserBundle, veja:

[<img src="http://tableless.com.br/uploads/2015/06/04.png" alt="Router Debug" width="750" height="403" class="alignnone size-full wp-image-49561" />][5]

Podemos entrar em todas as rotas, e perceberemos que está sem estilização, por exemplo: a rota /register/, se acessamos no navegador essa rota: url: http://127.0.0.1:8000/register/ veja:

[<img src="http://tableless.com.br/uploads/2015/06/05.png" alt="tela de registro" width="750" height="403" class="alignnone size-full wp-image-49562" />][6]

Está funcionando perfeitamente, porém sem estilização. Vou explicar como fazer para melhorarmos isso, porém não vou me aprofundar.
  
As templates do FOSUserBundle estão todas na pasta friendsofsymfony dentro do diretório vendor/, porém, sabemos que nunca devemos mexer em nada no diretório vendor, entretanto podemos sobrescrever essas templates principais do FOSUserBundle, para isso vamos criar uma pasta chamada FOSUserBundle em app/Resources, e dentro da pasta criada, vamos criar outra pasta chamada views, veja:

[<img src="http://tableless.com.br/uploads/2015/06/06.png" alt="Pasta views" width="750" height="403" class="alignnone size-full wp-image-49563" />][7]

O FOSUserBundle, trabalha com um layout principal, para que possamos sobrescrevê-lo, dentro da pasta views, vamos criar um arquivo chamado layout.html.twig e estender a nossa template base já criada anteriormente. A tamplate layout.html.twig ficará dessa forma, veja:

<pre class="lang-php">{% extends '::base.html.twig' %}

{% block title %}Blog Administração{% endblock %}

{% block content %}
    {% block fos_user_content %}{% endblock %}
{% endblock %}
</pre>

Pronto, se acessarmos novamente o url: http://127.0.0.1:8000/register/, teremos o resultado:

[<img src="http://tableless.com.br/uploads/2015/06/07.png" alt="Tela de registro pronta" width="750" height="403" class="alignnone size-full wp-image-49564" />][8]

Pronto, ficou melhor que anteriormente, porém podemos melhorar essa estilização, em meu caso vou deixar como está, mas caso queiram, é só criar um arquivo css com as devidas estilizações, e chamá- lo no base.html.twig que configuramos no <a href="http://tableless.com.br/iniciando-com-symfony-2-parte-06/" target="_blank">tutorial 06</a>, ou usar o próprio bootstrap, e fazer as alterações nos arquivos.
  
Obs: Podemos sobrescrever todos os arquivos do FOSUserBundle, porém temos que criar os arquivos e as estruturas de pastas, como no original. <a href="https://github.com/FriendsOfSymfony/FOSUserBundle/tree/1.3.x/Resources/views" target="_blank" rel="nofollow">Veja o original</a>.

Dessa forma podemos usar as classes do bootstrap para a estilização nos arquivos sobrescritos que foram criados, caso queiram ter uma base, tem um projeto em meu Github, que foi criado dessa forma, <a href="https://github.com/candidosouza/management-cars/tree/master/app/Resources/FOSUserBundle/views/Registration" target="_blank" rel="nofollow">veja</a>. 

## Criando um Administrador

Podemos criar os usuários pela url: http://127.0.0.1:8000/register/, porém os usuários criados serão usuários normais do sistema, para criar um super administrador entre no terminal, e digite:

<pre class="lang-bash">php app/console
</pre>

Podemos perceber que agora temos mais opções, pois instalamos o FOSUserBundle, veja:

[<img src="http://tableless.com.br/uploads/2015/06/08.png" alt="Novos comandos" width="750" height="403" class="alignnone size-full wp-image-49565" />][9]

E para criar um usuário administrador digitamos:

<pre class="lang-bash">php app/console fos:user:create
</pre>

damos um nome, um e-mail e senha, veja:

[<img src="http://tableless.com.br/uploads/2015/06/09.png" alt="Criando usuário" width="750" height="150" class="alignnone size-full wp-image-49566" />][10]

Porém o usuário criado, ainda é um usuário normal, vamos torná-lo um administrador, ainda no terminal, digite:

<pre class="lang-bash">php app/console fos:user:promote
</pre>

Escolhemos o usuário que no meu caso é admin.
  
Digitamos o Role que queremos, no meu caso ROLE_ADMIN
  
E pronto, já temos um administrador do sistema.

## Restringindo o acesso no sistema.

Para que um usuário anônimo não tenha acesso a administração, ( em nosso caso a administração de autores e administração de posts), vamos entrar novamente em security.yml, caminho: app/config/security.yml, e vamos alterar o controle de acesso, dizendo que todo o usuário que entrar na rota /post/ e /author/ deverá ser um usuário cadastrado, veja na linha 5 e 6:

<pre class="lang-php">access_control:
        - { path: ^/login$, role: IS_AUTHENTICATED_ANONYMOUSLY }
        - { path: ^/register, role: IS_AUTHENTICATED_ANONYMOUSLY }
        - { path: ^/resetting, role: IS_AUTHENTICATED_ANONYMOUSLY }
        - { path: ^/author/, role: ROLE_USER }
        - { path: ^/post/, role: ROLE_USER }
        - { path: ^/admin/, role: ROLE_ADMIN }
</pre>

Pronto, dessa forma todos os usuários que acessarem as urls: http://127.0.0.1:8000/post/ e http://127.0.0.1:8000/author/
  
deverão ser cadastrados como usuários, como autores do blog ou administradores.
  
Obs: Quando o usuário anônimo acessar as urls citadas acima, serão redirecionados para a tela de login.

Podemos fazer várias restrições, exemplo: vamos dizer que o usuário autor, pode: visualizar, criar, editar, e deletar um post, porém, ele não pode: criar, nem editar, menos ainda deletar outro autor, para isso entre no AuthorController, caminho: src/Tableless/CoreBundle/Controller/AuthorController.php

Primeiramente damos um use em AccessDeniedException, na classe AuthorController, veja.

<pre class="lang-php">use Symfony\Component\Security\Core\Exception\AccessDeniedException;
</pre>

Nos métodos createAction, newAction, editAction, updateAction e deleteAction, vamos restringir o acesso do usuário normal, onde verificaremos se ele é um administrador, e caso não seja, vamos gerar um erro, veja o código de verificação abaixo, onde introduziremos em todos os métodos citados acima, :

<pre class="lang-php">$securityContext = $this-&gt;get('security.context');

        if (!$securityContext-&gt;isGranted('ROLE_ADMIN')) {
            throw new AccessDeniedException(" Somente o administrador pode acessar! ");
        }
</pre>

Exemplo no createAction, nos demais métodos serão iguais, veja:

<pre class="lang-php">/**
* Creates a new Author entity.
*
* @Route("/", name="author_create")
* @Method("POST")
* @Template("TablelessCoreBundle:Author:new.html.twig")
*/
public function createAction(Request $request)
{
   $securityContext = $this-&gt;get('security.context');

   if (!$securityContext-&gt;isGranted('ROLE_ADMIN')) {
      throw new AccessDeniedException(" Somente o administrador pode acessar! ");
   }

    $entity = new Author();
    $form = $this-&gt;createCreateForm($entity);
    $form-&gt;handleRequest($request);

    if ($form-&gt;isValid()) {
        $em = $this-&gt;getDoctrine()-&gt;getManager();
        $em-&gt;persist($entity);
        $em-&gt;flush();

     return $this-&gt;redirect($this-&gt;generateUrl('author_show', array('id' =&gt; $entity&gt; getId())));
   }

   return array(
   'entity' =&gt; $entity,
       'form'   =&gt; $form-&gt;createView(),
   );
}
</pre>

Veja o erro caso o usuário não tenha acesso:

[<img src="http://tableless.com.br/uploads/2015/06/10.png" alt="Erro de usuário não autorizado" width="750" height="403" class="alignnone size-full wp-image-49583" />][11]

Pronto!
  
Podemos fazer outros tipos de restrições, podemos melhorar a segurança em nosso blog, porém no meu caso vou parar por aqui, com o exemplo acima, acredito que temos uma base de como fazer as demais restrições.

## Dicas:

Nos tutoriais abordei o básico de como trabalhar com o Symfony 2. Recomendo sempre a documentação para auxílio.
  
Gostaria de deixar algumas dicas para estudos, que não foram abordados:

<a href="http://symfony.com/doc/current/book/service_container.html" target="_blank">Services</a>
  
<a href="http://symfony.com/doc/current/book/performance.html" target="_blank">Performance</a>
  
<a href="http://symfony.com/doc/current/book/testing.html" target="_blank">Testing</a>
  
<a href="http://symfony.com/doc/current/book/http_cache.html" target="_blank">HTTP Cache:</a>
  
<a href="http://symfony.com/doc/current/book/translation.html" target="_blank">Translation:</a>

## Conclusão. {#other-posts-symfony}

Esta é a última parte da série “Iniciando com Symfony 2”, espero ter sido útil.
  
Bons estudos!

Links dos tutoriais anteriores:
  
<a href="http://tableless.com.br/iniciando-com-symfony-2/" target="_blank">Iniciando com Symfony 2 – Instalação</a>
  
<a href="http://tableless.com.br/iniciando-com-symfony-2-parte-02/" target="_blank">Iniciando com Symfony 2 – parte 02</a>
  
<a href="http://tableless.com.br/iniciando-com-symfony-2-parte-03/" target="_blank">Iniciando com Symfony 2 – parte 03</a>
  
<a href="http://tableless.com.br/iniciando-com-symfony-2-parte-04/" target="_blank">Iniciando com Symfony 2 – parte 04</a>
  
<a href="http://tableless.com.br/iniciando-com-symfony-2-parte-05/" target="_blank">Iniciando com Symfony 2 – parte 05</a>
  
<a href="http://tableless.com.br/iniciando-com-symfony-2-parte-06/" target="_blank">Iniciando com Symfony 2 – parte 06</a>
  
<a href="http://tableless.com.br/iniciando-com-symfony-2-parte-07/" target="_blank">Iniciando com Symfony 2 – parte 07</a>
  
<a href="http://tableless.com.br/iniciando-com-symfony-2-parte-08/" target="_blank">Iniciando com Symfony 2 – parte 08</a>
  
<a href="http://tableless.com.br/iniciando-com-symfony-2-parte-09/" target="_blank">Iniciando com Symfony 2 – parte 09</a>
  
O projeto encontra-se no <a href="https://github.com/candidosouza/tableless" target="_blank">GitHub</a>!

 [1]: #other-posts-symfony
 [2]: http://tableless.com.br/uploads/2015/06/01.png
 [3]: http://tableless.com.br/uploads/2015/06/02.png
 [4]: http://tableless.com.br/uploads/2015/06/03.png
 [5]: http://tableless.com.br/uploads/2015/06/04.png
 [6]: http://tableless.com.br/uploads/2015/06/05.png
 [7]: http://tableless.com.br/uploads/2015/06/06.png
 [8]: http://tableless.com.br/uploads/2015/06/07.png
 [9]: http://tableless.com.br/uploads/2015/06/08.png
 [10]: http://tableless.com.br/uploads/2015/06/09.png
 [11]: http://tableless.com.br/uploads/2015/06/10.png