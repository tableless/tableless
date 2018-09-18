---
title: PHPUnit – persistência e configurações avançadas
authors: Andre Cardoso
type: post
date: 2014-05-08
excerpt: Utilizando o PHPUnit para realizar testes com persistência de dados.
url: /phpunit-persistencia-e-configuracoes-avancadas/
dsq_thread_id: 2342343412
categories:
  - PHP
  - Técnicas e Práticas
tags:
  - composer
  - Coverage
  - Doctrine
  - PHPUnit
  - tdd
  - xml
  - Zend Framework

---
Neste artigo você verá como utilizar o <a title="PHPUnit - site oficial" href="https://phpunit.de/" target="_blank">PHPUnit</a> para realizar testes com persistência de dados utilizando o <a title="Projeto Doctrine" href="https://www.doctrine-project.org/" target="_blank">Doctrine</a> um <a title="O que é um ORM?" href="https://pt.wikipedia.org/wiki/Mapeamento_objeto-relacional" target="_blank">ORM</a> open-source e como definir configurações avançadas para personalizar sua suíte de testes e gerar relatórios de testes executados bem como cobertura do código de produção.

##  Começando

Para começar o projeto crie um arquivo chamado _composer.json_. Nele listaremos todos os pacotes/bibliotecas de terceiros que utilizaremos. Para este post utilizaremos o Doctrine e vários elementos do Zend Framework 2 além de é claro o próprio PHPUnit. Abaixo segue a lista de todas as bibliotecas que serão utilizadas.

<pre class="lang-php"> "require" : {
    "doctrine/common" : "*",
    "doctrine/dbal": "*",
    "doctrine/orm" : "*",
    "phpunit/phpunit": "3.7.*",
    "zendframework/zend-stdlib": "2.3.*@dev",
    "zendframework/zend-filter": "2.3.*@dev",
    "zendframework/zend-servicemanager": "2.3.*@dev",
    "zendframework/zend-crypt": "2.3.*@dev",
    "zendframework/zend-math": "2.3.*@dev"
 }</pre>

Seguindo as recomendações da <a title="FIG" href="https://www.php-fig.org/" target="_blank">FIG</a>, utilizaremos a <a title="PSR-0" href="https://www.php-fig.org/psr/psr-0/" target="_blank">PSR-0</a> que trata sobre a forma de carregarmento de classes na aplicação que estamos desenvolvendo. Com isso trabalharemos com namespaces e não precisaremos utilizar require ou include nas classes que utilizaremos. Para que o projeto tenha suas classes carregadas conforme a PSR-0 podemos informar isso no arquivo _composer.json_.

<pre class="lang-php"> "autoload" : {
    "psr-0": {
        "Tableless\\": "src/"
    }
 }</pre>

Isto nos diz que o namespace “Tableless” estará presente na pasta _src_ e para isto se faz necessária a criação da pasta _src_ e dentro da mesma a pasta _Tableless_. Há outra maneira de registrar o namespace através do _boostrap.__php_ que seria algo como:

<pre class="lang-php"> $load = require __DIR__ . '/vendor/autoload.php';
 $load-&gt;add('Tableless', __DIR__ . '/src');</pre>

> <p class="lang-php">
>   O arquivo <em>bootstrap.php </em>é comumente utilizado para realizar as configurações iniciais em vários frameworks. Basicamente ele inclui o <em>autoload.php</em> gerado pelo composer e podem ser definidas as mais diversas configurações globais de sua aplicação no mesmo.
> </p>

Feito isso baixamos o composer utilizando o comando **curl -sS https://getcomposer.org/installer | php** e em seguida instalamos as dependências através do comando **php composer.phar install**.

<img class="aligncenter size-medium wp-image-41342" src="https://raw.githubusercontent.com/diegoeis/tableless-static-images/master/2014/03/02-instalando-composer-e-dependencias-403x310.png" alt="Instalando composer e dependências" width="403" height="310" srcset="uploads/2014/03/02-instalando-composer-e-dependencias-403x310.png 403w, uploads/2014/03/02-instalando-composer-e-dependencias-218x168.png 218w, uploads/2014/03/02-instalando-composer-e-dependencias.png 791w" sizes="(max-width: 403px) 100vw, 403px" />

Com a instalação das dependências agora temos a nova estrutura contendo uma pasta _vendor_ contendo todas as bibliotecas de terceiros, um novo arquivo _composer.lock_ e _composer.phar_ os quais já foram descritos em outro artigo sobre PHPUnit com composer e que pode ser acessado [aqui][1].

<img class="aligncenter size-medium wp-image-41343" src="https://raw.githubusercontent.com/diegoeis/tableless-static-images/master/2014/03/03-nova-estrutura-490x310.png" alt="Nova Estrutura" width="490" height="310" srcset="uploads/2014/03/03-nova-estrutura-490x310.png 490w, uploads/2014/03/03-nova-estrutura-265x168.png 265w, uploads/2014/03/03-nova-estrutura-400x252.png 400w, uploads/2014/03/03-nova-estrutura.png 1086w" sizes="(max-width: 490px) 100vw, 490px" />

## Próximo passo

Agora temos de criar um arquivo que será o pontapé inicial da aplicação, arquivo este comumente nomeado de bootstrap conforme já mencionado anteriormente. Nele são configurados onde se encontram as entidades – que serão explicadas mais a frente deste tutorial, configuração do banco de dados entre outras configurações. Como neste exemplo será utilizado o Doctrine, precisamos configurar o mesmo.

Crie um arquivo chamado _bootstrap.php_ na raiz de seu projeto, o fonte do _bootstrap.php_ está comentado para melhor entendimento.

<pre class="lang-php">&lt;?php
// Carregando o autoload que o composer gerou
require __DIR__ . '/vendor/autoload.php';
// indicando tudo que usaremos no bootstrap
use Doctrine\ORM\EntityManager;
use Doctrine\ORM\Tools\Setup;
use Doctrine\ORM\Mapping\Driver\AnnotationDriver;
use Doctrine\Common\Annotations\AnnotationReader;
use Doctrine\Common\Annotations\AnnotationRegistry;
/**
* Definindo se é modo desenvolvimento
* 
* Caso true: o cache do Doctrine é realizado em formato de array
* Caso false: o cache é conforme configuração (memcache, APC..)
* 
* Somente trabalharemos aqui com o modo TRUE, cache em array
*/
$config = Setup::createConfiguration( true );
// pasta onde encontram-se nossas entidades
$entitypath = array( __DIR__ . '/src/Tableless/Entity' );
// registrando as entidades
$driver = new AnnotationDriver(new AnnotationReader(), $entitypath);
$config->setMetadataDriverImpl($driver);
/**
* indicando que trabalharemos com o modo annotations para
* as entidades. Pode ser também via arquivo yaml e xml
* 
*/
AnnotationRegistry::registerFile(__DIR__ 
. '/vendor/doctrine/orm/lib/Doctrine/ORM/Mapping/Driver/DoctrineAnnotations.php');
// configurando a conexão com o banco de dados
$conn = array(
    'driver' => 'pdo_mysql',    
    'user' => 'root',
    'password' => 'root',
    'dbname' => 'tableless_tdd',
);
// E finalmente criando o manipulador de entidades
$entityManager = EntityManager::create($conn, $config);</pre>

> Até agora você viu várias vezes a palavra “Entidade” mas o que ela significa? Entidade é um objeto que tem um significado conceitual dentro de um domínio. Em outras palavras, cada entidade no Doctrine é a representação de uma tabela no banco de dados e cada registro é uma instância desta entidade. A entidade não manipula o banco de dados, apenas representa-o.

Pronto, a nível de produção já temos a configuração, agora criaremos a estrutura e configurações para testes.

Na raiz de seu projeto crie uma pasta chamada _tests_, dentro dela uma pasta chamada _src_ e dentro da src uma pasta chamada _Tableless_. Perceba que o namespace ficará na mesma estrutura do código de produção, desta forma para utilizarmos uma entidade chamada _User_ por exemplo, usaremos a seguinte declaração: **use Tableless\Entity\User;**. Para a classe de testes de User se for necessária declarar em algum lugar será desta forma: **use Tableless\Entity\UserTest;**.

<img class="aligncenter size-medium wp-image-41345" src="https://raw.githubusercontent.com/diegoeis/tableless-static-images/master/2014/03/04-estrutura-inicial-testes-398x310.png" alt="Estrutura inicial testes" width="398" height="310" srcset="uploads/2014/03/04-estrutura-inicial-testes-398x310.png 398w, uploads/2014/03/04-estrutura-inicial-testes-215x168.png 215w, uploads/2014/03/04-estrutura-inicial-testes-400x311.png 400w, uploads/2014/03/04-estrutura-inicial-testes.png 542w" sizes="(max-width: 398px) 100vw, 398px" />

Após a criação das pastas necessárias falta a criação do bootstrap de testes e de um arquivo de configurações de execução do PHPUnit.

Começando com o bootstrap, o código novamente está comentado explicando porque determinadas coisas estão sendo feitas. Crie o arquivo _bootstrap.php_ dentro da pasta de testes (_tests_).

<pre class="lang-php"><?php
// utilizando o bootstrap de produção
require __DIR__ . '/../bootstrap.php';
use Doctrine\ORM\EntityManager;
/*
* Sobrescrevendo a conexão com banco de dados.
* 
* Isto faz-se necessário para que ao rodar os testes 
* o banco de produção não sofra alterações
*/
$conn = array(
    'driver' => 'pdo_sqlite',
    'dbname' => ':memory:',
);
return $entityManager = EntityManager::create($conn, $config);
</pre>

> O bootstrap de testes se faz necessário para sobrescrever a conexão com o banco de dados, caso contrário, todos os testes realizariam alterações no banco de dados de produção e isto jamais deve acontecer.

Feito isto agora é o momento de criar o arquivo xml de configurações do PHPUnit. Crie um arquivo chamado <i style="font-family: Arial, sans-serif;line-height: 1.5em">phpunit.xm</i>l dentro de sua pasta <i style="font-family: Arial, sans-serif;line-height: 1.5em">tests</i> e adicione o conteúdo abaixo.

<pre class="lang-xml">&lt;?xml version="1.0" encoding="UTF-8"?&gt;
&lt;phpunit colors="true" bootstrap="bootstrap.php"&gt;

&lt;!-- Indicando qual é o diretório onde as classes de teste se encontram --&gt;
    &lt;testsuites&gt;
        &lt;testsuite name="Tableless TDD Test Suite"&gt;
            &lt;directory suffix=".php"&gt;src/&lt;/directory&gt;
        &lt;/testsuite&gt;
    &lt;/testsuites&gt;

&lt;!-- Adicionando filtros, basicamente whitelist (diretórios que serão executados), 
dentro temos o exclude (diretórios que não serão executados pelos testes) --&gt;

&lt;filter&gt;
    &lt;whitelist&gt;
        &lt;directory suffix=".php"&gt;../src/&lt;/directory&gt;
        &lt;exclude&gt;
            &lt;directory suffix=".php"&gt;./vendor/&lt;/directory&gt;
        &lt;/exclude&gt;
    &lt;/whitelist&gt;
&lt;/filter&gt;
&lt;/phpunit&gt;</pre>

Quase pronto, se rodarmos o comando **./vendor/bin/phpunit -c tests/phpunit.xml** dentro da raiz do projeto teremos a mensagem de que nenhum teste foi executado como na imagem abaixo.

<img class="aligncenter size-medium wp-image-41346" src="https://raw.githubusercontent.com/diegoeis/tableless-static-images/master/2014/03/05-nenhum-teste-490x310.png" alt="Nenhum Teste" width="490" height="310" srcset="uploads/2014/03/05-nenhum-teste-490x310.png 490w, uploads/2014/03/05-nenhum-teste-265x168.png 265w, uploads/2014/03/05-nenhum-teste-400x253.png 400w, uploads/2014/03/05-nenhum-teste.png 803w" sizes="(max-width: 490px) 100vw, 490px" />

>  Como estamos trabalhando com um arquivo de configurações, para rodarmos o phpunit seguindo as definições do arquivo precisamos utilizar o parâmetro **-c** seguido do nome do arquivo.

Obviamente que nenhum teste ainda foi executado porque não temos nenhuma classe de testes. Vamos começar então. Crie uma pasta _Entity_ dentro de _tests/src_. Dentro desta pasta crie um arquivo chamado _UsertTest.php_. A nova estrutura de testes deve estar como na imagem abaixo.

<img class="aligncenter size-medium wp-image-41347" src="https://raw.githubusercontent.com/diegoeis/tableless-static-images/master/2014/03/06-nova-estrutura-de-testes-379x310.png" alt="Nova estrutura de testes" width="379" height="310" srcset="uploads/2014/03/06-nova-estrutura-de-testes-379x310.png 379w, uploads/2014/03/06-nova-estrutura-de-testes-205x168.png 205w, uploads/2014/03/06-nova-estrutura-de-testes-400x326.png 400w, uploads/2014/03/06-nova-estrutura-de-testes.png 695w" sizes="(max-width: 379px) 100vw, 379px" />

No arquivo _UserTest.php_ adicione o namespace do mesmo que é Tableless\Entity.

<pre class="lang-php">namespace Tableless\Entity;</pre>

Agora definimos quais classes utilizaremos para este teste. Como estamos testando a entidade _User_ precisaremos utilizar o Tableless\Entity\User.

<pre>use Tableless\Entity\User;</pre>

No entanto aí tem um detalhe. A entidade User ainda não existe, mas a criaremos dentro de instantes pois ainda temos uma classe que devemos criar antes mesmo da _User_. Ela se chama _TestCase_ e deve estar no namespace Tableless\Test. Crie em _src/Tableless_ (não em tests/src/Tableless) uma pasta chamada Test e dentro dela um arquivo chamado _TestCase.php_.

<img class="aligncenter size-medium wp-image-41348" src="https://raw.githubusercontent.com/diegoeis/tableless-static-images/master/2014/03/07-criando-test-case-426x310.png" alt="Criando o TestCase" width="426" height="310" srcset="uploads/2014/03/07-criando-test-case-426x310.png 426w, uploads/2014/03/07-criando-test-case-230x168.png 230w, uploads/2014/03/07-criando-test-case-400x291.png 400w, uploads/2014/03/07-criando-test-case.png 602w" sizes="(max-width: 426px) 100vw, 426px" />

Neste arquivo copie e cole o código abaixo que está comentado para melhor entendimento.

<pre class="lang-php">&lt;?php
namespace Tableless\Test;

use Doctrine\ORM\Tools\SchemaTool;
use PHPUnit_Framework_TestCase as PHPUnit;

abstract class TestCase extends PHPUnit
{
    protected $entityManager = null;

    /**
    * Executado antes de cada teste unitário
    */
    public function setup() 
    {
        $entityManager = $this-&gt;getEntityManager(); 
        $tool = new SchemaTool($entityManager);

        //Obtem informações das entidades que encontrar em Tableless\Entity
        $classes = $entityManager-&gt;getMetadataFactory()-&gt;getAllMetadata();

        // Cria a base de dados necessária com suas determinadas tabelas
        $tool-&gt;createSchema($classes);

        parent::setup();
    } 

    /**
    * Executado após a execução de cada um dos testes unitários
    */
    public function tearDown() 
    {
        $entityManager = $this-&gt;getEntityManager(); 
        $tool = new SchemaTool($entityManager);

        //Obtem informações das entidades que encontrar em Tableless\Entity
        $classes = $entityManager-&gt;getMetadataFactory()-&gt;getAllMetadata();

        // Desfaz o banco criado no setUp
        $tool-&gt;dropSchema($classes);

        parent::tearDown();
    }

    /**
    * 
    * @return \Doctrine\ORM\EntityManager
    */
    public function getEntityManager() 
    {
        if (! $this-&gt;entityManager) {
            $this-&gt;entityManager = require __DIR__ . '/../../../tests/bootstrap.php';
        } 
        return $this-&gt;entityManager; 
    } 
}</pre>

Pronto, já estamos com tudo o que precisamos para começar escrever os testes. Detalhe que esta configuração foi criada para que fosse possível utilizar e testar a persistência de dados utilizando o Doctrine. Para demais testes em controllers, services, views, forms ou o que mais você desejar esta configuração realizada até o momento permanece podendo ser acrescida de novos elementos, tudo depende da necessidade.

## Criando o primeiro teste

No arquivo _tests/src/Tableless/Entity/UserTest.php_ começaremos a definir nossos testes. Lembre-se que a ideia do TDD é que o teste seja criado antes do código de produção, e assim faremos.

Pra início de conversa utilizaremos a classe _TestCase_ previamente criada e a entidade User.

<pre>use Tableless\Entity\User;
use Tableless\Test\TestCase;</pre>

A classe de testes atual (UserTest) extende de TestCase e adicionaremos o atributo protegido $entity.

<pre>class UserTest extends TestCase
{
    protected $entity;
}</pre>

Assim como a classe TestCase, nossa classe UserTest também possuirá um métdo setUp e um tearDown que servirão para as configurações da mesma. De momento apenas setaremos o valor default do atributo entity no setUp.

<pre>public function setUp()
{
    $this-&gt;entity = 'Tableless\Entity\User';
};</pre>

Agora segue o nosso primeiro teste: Novamente há comentários explicando cada ação.

<pre>public function testIfIsSavingAsExpected()
{
    // Criando os dados necessários para salvar o usuário
    $userData = array(
        'id' =&gt; 1,
        'name' =&gt; 'Nome do usuário',
        'email' =&gt; 'usuario@dominio.com',
        'password' =&gt; 'xpto',
        'profilePic' =&gt; 'image.png'
    );
    /* o Id é gerado automaticamente pelo Doctrine, neste caso estou forçando
    * um Id desejado, mas somente para o teste, para o código de produção
    * isto não se faz necessário
    */

    // Instanciando a entidade usuário definindo todos os atributos à ela
    $user = new User( $userData );

    // salvando o usuário no banco de dados
    $this-&gt;getEntityManager()-&gt;persist( $user );
    $this-&gt;getEntityManager()-&gt;flush();

    // Obtendo o usuário salvo
    $registeredUser = $this-&gt;getEntityManager()
            -&gt;getRepository($this-&gt;entity)
            -&gt;findOneBy(array('email' =&gt; 'usuario@dominio.com'));

    // Garantindo que tudo funcionou conforme o esperado
    $this-&gt;assertInstanceOf($this-&gt;entity, $registeredUser);
    $this-&gt;assertEquals($userData['name'], $registeredUser-&gt;getName());
}</pre>

Se rodarmos o comando **./vendor/bin/phpunit -c tests/phpunit.xml** da raiz de nosso projeto deveremos ver o seguinte erro: “PHP Fatal error: Class &#8216;Tableless\Entity\User &#8230;&#8217;” isto porque ainda não existe a entidade _User_ pois realizamos o primeiro passo do TDD, o “Red”. Em seguida realizaremos o passo “Green” que consiste em criarmos o código que faça o teste passar e por último o passo “Refactor” que é onde faremos algumas melhorias no código. No código exemplo não existirá duplicidade e/ou partes inconsistentes com isso o Refactor realizará apenas algumas pequenas melhorias, nada mais.

Crie na pasta _src_ (não em tests/src) uma pasta chamada _Entity_ e dentro dela um arquivo chamado _User.php_. Eis a estrutura da entidade _User_. Por ser um arquivo muito extenso, colocarei apenas o link do mesmo que encontra-se no github. <a title="Tableless\Entity\user" href="https://gist.github.com/andrebian/11389706" target="_blank">Tableless\Entity\User</a>

Perceba que existem comentários acima de cada um dos atributos da classe. Isto se dá por estarmos utilizando o Annotations do Doctrine para que os mesmos sejam lidos e mapeados no banco de dados. Em outras palavras, o Doctrine lê a anotação e cria a estrutura da tabela conforme as definições nos comentários. Há a possibilidade de realizar tais definições via xml e também via yaml o que não veremos neste tutorial.

Agora se rodarmos nosso teste novamente o mesmo passará. Ou seja, já temos um código minimamente testado com um início de noção de persistência de dados, veremos uma pequena melhora no código agora e em seguida algumas configurações para a execução dos testes.

**./vendor/bin/phpunit -c tests/phpunit.xml**

<img class="aligncenter size-medium wp-image-41349" src="https://raw.githubusercontent.com/diegoeis/tableless-static-images/master/2014/03/08-primeiro-teste-passando-575x310.png" alt="Primeiro teste passando" width="575" height="310" srcset="uploads/2014/03/08-primeiro-teste-passando-575x310.png 575w, uploads/2014/03/08-primeiro-teste-passando-312x168.png 312w, uploads/2014/03/08-primeiro-teste-passando-400x215.png 400w, uploads/2014/03/08-primeiro-teste-passando.png 797w" sizes="(max-width: 575px) 100vw, 575px" />

## Definindo hash para senha

Primeiramente no teste adicionaremos uma asserção de que a senha do usuário registrado não é igual a senha que definimos, em string pura. Adicione o trecho de código abaixo em seu teste logo após $this->assertEquals($userData[&#8216;name&#8217;], $registeredUser->getName());

<pre class="lang-php">// verificando se hash de senha funcionou
$this-&gt;assertNotEquals($userData['password'], $registeredUser-&gt;getPassword());</pre>

Ao rodarmos o teste o mesmo deve quebrar pois ainda não criamos um hash para a senha, desta forma a senha fornecida está em string pura no banco de dados.

** ./vendor/bin/phpunit -c tests/phpunit.xml**

<img class="aligncenter size-medium wp-image-41350" src="https://raw.githubusercontent.com/diegoeis/tableless-static-images/master/2014/03/09-teste-falhando-hash-523x310.png" alt="Teste falhando hash" width="523" height="310" srcset="uploads/2014/03/09-teste-falhando-hash-523x310.png 523w, uploads/2014/03/09-teste-falhando-hash-283x168.png 283w, uploads/2014/03/09-teste-falhando-hash-400x237.png 400w, uploads/2014/03/09-teste-falhando-hash.png 800w" sizes="(max-width: 523px) 100vw, 523px" />

Agora, na classe Tableless\Entity\User usaremos as seguintes classes do Zend:

<pre>use Zend\Math\Rand;
use Zend\Crypt\Key\Derivation\Pbkdf2;</pre>

em setPassword deixaremos adicionaremos a chamada ao método encryptPassword

<pre>public function setPassword( $password )
{
    $this-&gt;password = $this-&gt;encryptPassword($password);
    return $this;
}</pre>

E criaremos o método encryptPassword.

<pre>public function encryptPassword( $password )
{
   return base64_encode(
    Pbkdf2::calc('sha256', $password, $this-&gt;salt, 
            10000, strlen($password*2)));
}</pre>

Agora rodando **./vendor/bin/phpunit -c tests/phpunit.xml** o teste passa novamente.

<img class="aligncenter size-medium wp-image-41351" src="https://raw.githubusercontent.com/diegoeis/tableless-static-images/master/2014/03/10-teste-passando-hash-375x310.png" alt="teste passando hash" width="375" height="310" srcset="uploads/2014/03/10-teste-passando-hash-375x310.png 375w, uploads/2014/03/10-teste-passando-hash-203x168.png 203w, uploads/2014/03/10-teste-passando-hash-400x330.png 400w, uploads/2014/03/10-teste-passando-hash.png 795w" sizes="(max-width: 375px) 100vw, 375px" />

Assim finalizamos o básico da realização de testes utilizando persitência de dados. A partir de agora veremos algumas configurações avançadas que lhe ajudarão muito no feedback dos testes.

## Algumas configurações avançadas

Através do arquivo _phpunit.xml_ podemos definir algumas configurações avançadas para a execução dos testes. Começando pela declaração <phpunit>. Atualmente encontra-se desta forma:

<pre class="lang-xml">&lt;phpunit colors="true" bootstrap="bootstrap.php"&gt;</pre>

Isto quer dizer que utilizaremos um arquivo de bootstrap e dizemos qual arquivo é e também que queremos coloração no output. Caso colors=”true” não estivesse presente nossa visão ficaria desta forma.

<img class="aligncenter size-medium wp-image-41352" src="https://raw.githubusercontent.com/diegoeis/tableless-static-images/master/2014/03/11-colors-482x310.png" alt="Colors" width="482" height="310" srcset="uploads/2014/03/11-colors-482x310.png 482w, uploads/2014/03/11-colors-261x168.png 261w, uploads/2014/03/11-colors-400x257.png 400w, uploads/2014/03/11-colors.png 806w" sizes="(max-width: 482px) 100vw, 482px" />

Podemos definir erros e avisos sendo tratados como exceções.

<pre>&lt;phpunit 
    convertErrorsToExceptions="true" 
    convertNoticesToExceptions="true"
    convertWarningsToExceptions="true"
    colors="true"
    bootstrap="bootstrap.php"
&gt;</pre>

E muitas outras opções. Para conhecer todas as opções de configurações acesse <a title="Visualizar as configurações do PHPUnit" href="https://phpunit.de/manual/3.7/pt_br/appendixes.configuration.html" target="_blank">este link</a>.

Certamente que a configuração a seguir é uma que empolga muitos desenvolvedores, logs e coverage. Com logs e coverage você identifica quais testes passaram, quais tiveram exceções, quais não passaram e o mais legal de tudo, o percentual de cobertura de testes que há em seu código de produção. Basicamente ao rodar um teste unitário, ele cobre uma pequena parte de seu código de produção, habilitando coverage você pode verificar quais linhas estão realmente garantidas por testes e quais você ainda tem de trabalhar mais tempo para garantir um mínimo de cobertura necessário para perfeito funcionamento mas principalmente para garantia de evolução de seu software.

Para criar logs utilizamos a tag logging no arquivo _phpunit.xml_ logo após o fechamento da tag </filter>.

<pre>&lt;logging&gt;
    &lt;log type="testdox-text" target="data/testdox.txt" /&gt;
&lt;/logging&gt;</pre>

O log acima está gravando em formato de texto um checklist dos testes que existem em todas as classes de teste dentro da suite de testes marcando com x os que foram executados.

Rodando **./vendor/bin/phpunit -c tests/phpunit.xml** será criada a pasta _tests/data_ contento o arquivo _testdox.txt_ O nome do arquivo é de sua escolha.

<img class="aligncenter size-medium wp-image-41353" src="https://raw.githubusercontent.com/diegoeis/tableless-static-images/master/2014/03/12-testdox-569x310.png" alt="Testdox" width="569" height="310" srcset="uploads/2014/03/12-testdox-569x310.png 569w, uploads/2014/03/12-testdox-308x168.png 308w, uploads/2014/03/12-testdox-400x217.png 400w, uploads/2014/03/12-testdox.png 891w" sizes="(max-width: 569px) 100vw, 569px" />

Também é possível gerar o testdox em formato html, basta alterar testdox-text para testdox-html e testdox.txt para testdox.html mas o mais comum é ser utilizado em formato txt mesmo.

Existe também a possibilidade de habilitar o testdox em tempo de execução. Basta apenas adicionar o parâmetro &#8211;testdox ao rodar os testes. O resultado será como abaixo.

<pre class="lang-shell">$ ./vendor/bin/phpunit -c tests/phpunit.xml --testdox
PHPUnit 3.7.35 by Sebastian Bergmann.
Configuration read from /home/andre/Documents/Posts/tableless/phpunit-persistencia-de-dados-e-configuracoes-avancadas/sources/tests/phpunit.xml
Tableless\Entity\User
  [x] If is saving as expected
Generating code coverage report in HTML format ... done</pre>

## Agrupamento de testes

Por certas vezes necessitamos agrupar testes para que rodemos somente determinada sequência sem que os demais sejam executados. Isto é útil para quando temos de realizar uma pequena alteração e não se faça necessário a execução de todos os testes já criados tornando o feedback mais rápido. Comumente isto é utilizado quando se deseja realizar um ajuste pontual e ao ser finalizado todos os testes são executados novamente.

O PHPUnit nos permite trabalhar com grupos os quais veremos sua definição a seguir.

Crie uma pasta chamada _Filter_ em _tests/src/Tableless_ e dentro dela um arquivo chamado _CurrencyTest.php_. O conteúdo deste arquivo está abaixo.

<pre>&lt;?php
namespace Tableless\Filter;
use Tableless\Test\TestCase;
/**
* @group Filter
*/
class CurrencyTest extends TestCase 
{
    public function testIfClassExists()
    {
        $this-&gt;assertTrue(class_exists('Tableless\Filter\Currency'));
    }
}</pre>

Perceba que antes de ser declarado o nome da classe existe uma anotação @group Filter. É isto que define o grupo ao qual este teste pertence. Faça o mesmo para o teste já existente (tests/src/Tableless/Entity/UserTest.php) anotando-o como @group Entity.

<pre>...
/**
* @group Entity
*/
class UserTest extends TestCase
...</pre>

Agora que temos a definição dos grupos podemos rodar nossos testes somente de 1 grupo, de um conjunto de grupos ou de todos os grupos sem distinção. Existem duas formas de rodar os testes por grupos, através de parâmetro informado no momento da execução dos testes ou através do arquivo xml de configurações do PHPUnit, veremos ambas.

### Via parâmetro

#### Somente um grupo

<pre>$ ./vendor/bin/phpunit -c tests/phpunit.xml --group Entity
</pre>

#### Mais de um grupo

<pre>$ ./vendor/bin/phpunit -c tests/phpunit.xml --group Entity,Filter
</pre>

Para que todos os grupos de testes sejam executados basta que não seja informado o parâmetro &#8211;group.

### Via arquivo de configuração

No arquivo tests/phpunit.xml adicione uma tag <groups> e dentro dela liste os grupos desejados.

<pre class="lang-php">&lt;groups&gt;
    &lt;include&gt;
        &lt;group&gt;Entity&lt;/group&gt;
    &lt;/include&gt;
&lt;/groups&gt;</pre>

Você deve estar imaginando, se existe uma tag **include **deve existir uma tag **exclude **também. Imaginou certo! Dentro de include você adiciona todos os grupos que deseja que sejam executados nos testes já em exclude, todos que NÃO devem ser executados. O excclude é ideal para testes que foram marcados como incompletos ou pulados (skipped).

Após adicionar as tags referentes aos grupos de testes no arquivo xml de configurações não se faz mais necessário informar o parâmetro  &#8211;group, basta rodar normalmente.

<pre>$ ./vendor/bin/phpunit -c tests/phpunit.xml</pre>

## Agora sim, o mais legal de todos, Coverage em Html!

Dentro de <logging> adicione uma nova tag chamada <log> conforme o exemplo abaixo.

<pre>&lt;log 
    type="coverage-html" 
    target="data/coverage" 
    charset="UTF-8" 
    yui="true" 
    highlight="true"
    lowUpperBound="35"
    highUpperBound="70" /&gt;</pre>

Basicamente estamos definindo que o coverage será em formato html, que o considerado baixo coverage será de 35% e um bom coverage se dará a partir de 70%. O highlight serve para destacar as linhas que foram cobertas com verde, não cobertas com vermelho e ignoradas permanecem com a cor padrão. Rode o teste novamente.

Agora no browser entre em seu localhost na pasta do projeto em que está trabalhando. Em seguida entre na pasta _tests_, após isto em _data_ e por último em coverage. Surpreenda-se!

<img class="aligncenter size-medium wp-image-41354" src="https://raw.githubusercontent.com/diegoeis/tableless-static-images/master/2014/03/13-coverage-588x223.png" alt="Coverage" width="588" height="223" srcset="uploads/2014/03/13-coverage-588x223.png 588w, uploads/2014/03/13-coverage-329x125.png 329w, uploads/2014/03/13-coverage-660x251.png 660w, uploads/2014/03/13-coverage-400x152.png 400w, uploads/2014/03/13-coverage.png 1324w" sizes="(max-width: 588px) 100vw, 588px" />

Navegando pelos arquivos você identificará o que já está bom e o que precisa ser mais testado. Neste nosso caso chegar a 100% é muito fácil, basta lermos todos os dados do usuário.

No arquivo _tests/src/Tableless/Entity/UserTest.php_, dentro do único teste que temos adicione os seguintes asserts:

<pre>$this-&gt;assertEquals(1, $registeredUser-&gt;getId());
$this-&gt;assertEquals('usuario@dominio.com', $registeredUser-&gt;getEmail());
$this-&gt;assertNotNull($registeredUser-&gt;getSalt());
$this-&gt;assertEquals('image.png', $registeredUser-&gt;getProfilePic());</pre>

Rode os testes novamente e corra pro abraço!

<img class="aligncenter size-medium wp-image-41355" src="https://raw.githubusercontent.com/diegoeis/tableless-static-images/master/2014/03/14-coverage-100-588x237.png" alt="Coverage 100%" width="588" height="237" srcset="uploads/2014/03/14-coverage-100-588x237.png 588w, uploads/2014/03/14-coverage-100-329x132.png 329w, uploads/2014/03/14-coverage-100-660x266.png 660w, uploads/2014/03/14-coverage-100-400x161.png 400w, uploads/2014/03/14-coverage-100.png 1303w" sizes="(max-width: 588px) 100vw, 588px" />

Lembrando novamente que para entendimento deste tutorial se faz necessário a leitura dos conteúdos anteriores sobre o tema, sendo eles [TDD, por que usar?][2]  e [PHPUnit, como iniciar sem dores][1].

## Bonus.

O que fizemos até o momento foi preparar o ambiente de testes e executá-los mas este ambiente ainda não está totalmente pronto para o código de produção pois precisamos de conexão com um banco de dados além de mais uma configuração do Doctrine para que possamos criar o banco de dados a partir de nossas entidades. Ou seja, lembra daquele processo de criar o banco de dados, definir as tabelas e relacionamentos todos antes do código? Com o Doctrine isto não se faz mais necessário, pode ser feito da forma descrita (e tradicional) mas há outra forma bem legal que é uma mão na roda e que mostrarei agora.

Primeiramente precisamos criar um arquivo de configuração para o cli (Command Line Interface) do Doctrine. Na pasta raiz de sua aplicação crie um arquivo chamado _cli-config.php_ e cole o seguinte conteúdo:

<pre>//cli-config.php
require 'bootstrap.php';

return \Doctrine\ORM\Tools\Console\ConsoleRunner::createHelperSet($entityManager);</pre>

<div id="LC3">
  Após a criação deste arquivo podemos rodar o seguinte comando <b>./vendor/bin/doctrine</b>
</div>

Aparecerão várias opções de uso que vão desde checagem de status de conexão, validação das entidades, além de outras funcionalidades. Uma coisa que o doctrine não faz realmente é criar a base de dados pois isto depende de cada base pois Mysql é de um jeito, Postgres é de outro, SQL Server é de outro ainda, então esta tarefa ainda é manual.

Para fins didáticos criei uma base chamada tableless_tdd no mysql como definido no arquivo bootstrap.php da raiz do projeto. Você pode alterar o nome se quiser, bem como o próprio banco, experimente o Sqlite se quiser.

Com a base criada rode o comando **./vendor/bin/doctrine orm:validate-schema**. Se estiver tudo ok aparecerá algo como a imagem abaixo. Nela informa que o mapeamento das entidades está correto mas o banco ainda não está sincronizado, para sincronizar rode o comando **./vendor/bin/doctrine orm:schema-tool:create**. Isto lerá todas as entidades contidas em src/Tableless/Entity e criará a estrutura de tabelas a partir delas.

**./vendor/bin/doctrine orm:validate-schema**

<img class="aligncenter size-medium wp-image-41356" src="https://raw.githubusercontent.com/diegoeis/tableless-static-images/master/2014/03/15-doctrine-validate-500x310.png" alt="Doctrine Validate Schema" width="500" height="310" srcset="uploads/2014/03/15-doctrine-validate-500x310.png 500w, uploads/2014/03/15-doctrine-validate-271x168.png 271w, uploads/2014/03/15-doctrine-validate-400x247.png 400w, uploads/2014/03/15-doctrine-validate.png 797w" sizes="(max-width: 500px) 100vw, 500px" />

**./vendor/bin/doctrine orm:schema-tool:create**

<img class="aligncenter size-medium wp-image-41357" src="https://raw.githubusercontent.com/diegoeis/tableless-static-images/master/2014/03/16-doctrine-create-validate-459x310.png" alt="Doctrine create validate" width="459" height="310" srcset="uploads/2014/03/16-doctrine-create-validate-459x310.png 459w, uploads/2014/03/16-doctrine-create-validate-249x168.png 249w, uploads/2014/03/16-doctrine-create-validate-400x269.png 400w, uploads/2014/03/16-doctrine-create-validate.png 820w" sizes="(max-width: 459px) 100vw, 459px" />

Atualmente possuímos somente a entidade User que indica que uma tabela users será criada no banco de dados. Após a finalização da execução do comando anterior seu banco de dados já estará com a nova estrutura. Ao realizar qualquer alteração na entidade User ou mesmo criar novas entidades você precisará rodar o comando **./vendor/bin/doctrine orm:schema-tool:update** com isso aparecerá uma mensagem informando que já há uma estrutura no banco de dados e lhe pede confirmação sobre o que fazer. Você pode ignorar, ver as alterações ou forçar se tiver certeza do que está fazendo ou mesmo se já visualizou as alterações que serão realizadas e está ciente de que está tudo certo. Basta ler as intruções que o próprio Doctrine fornece que você saberá o que fazer, é muito intuitivo.

## Finalizando

Agora que você já configurou o Doctrine, já conhece como criar testes unitários resta apenas aperfeiçoar a cada dia. Não existe uma receita, tudo requer empenho e dedicação mas que no final quando você ver aquelas barrinhas verdes mostrando 100% de cobertura se sentirá cada vez mais empolgado e com um código mais estável mas o principal, com um código que pode facilmente evoluir.

Para baixar o código-fonte gerado neste artigo acesse este link do <a title="Baixar o código-fonte" href="https://github.com/andrebian/tdd-persistencia-de-dados" target="_blank">Github</a>.

 [1]: https://tableless.com.br/phpunit-como-iniciar-sem-dores/ "PHPUnit, como iniciar sem dores"
 [2]: https://tableless.com.br/tdd-por-que-usar/ "TDD, por que usar?"