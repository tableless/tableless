---
title: Iniciando com Symfony 2 – Parte 02
author: Candido Souza
type: post
date: 2015-02-09
excerpt: Neste tutorial veremos como o Symfony facilita nosso processo de desenvolvimento e produtividade com o seu componete console.
url: /iniciando-com-symfony-2-parte-02/
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
  - Symfony2 tutorial

---
[<img src="http://tableless.com.br/uploads/2015/02/symfony-logo-tableless.png" alt="Symfony logo" width="720" height="450" class="alignnone size-full wp-image-46879" srcset="uploads/2015/02/symfony-logo-tableless.png 720w, uploads/2015/02/symfony-logo-tableless-222x139.png 222w, uploads/2015/02/symfony-logo-tableless-400x250.png 400w" sizes="(max-width: 720px) 100vw, 720px" />][1]

Depois de já instalado o Symfony 2, como postado no <a title="Iniciando com Symfony2" href="http://tableless.com.br/iniciando-com-symfony-2/" target="_blank">artigo anterior que escrevi</a>, vamos avançar nosso processo criando um simples blog.
  
É claro que o Symfony é para projetos maiores, mas para efeito de didática, achei um bom começo, espero que gostem.

## Bundle o coração do symfony

O Symfony trabalha com bundle (pacote), que é um conjunto de códigos que pode ser reutilizado em outros projetos. Simplificando: são componentes prontos, que facilitam nossa vida na hora de desenvolver. Podemos criar um bundle do zero, como vamos fazer aqui, ou configurar um já pronto.

Antes de criarmos de nosso primeiro bundle, vamos fazer uma pequena modificação no projeto. Não vamos precisar do bundle AppBundle, só usamos para a introdução.

Exclua a pasta AppBundle como mostrado na imagem, caminho src/AppBundle.

[<img src="http://tableless.com.br/uploads/2015/02/01.png" alt="Imagem pastas app/AppBundle" width="750" height="403" class="alignnone size-full wp-image-46808" srcset="uploads/2015/02/01.png 750w, uploads/2015/02/01-259x139.png 259w, uploads/2015/02/01-400x215.png 400w" sizes="(max-width: 750px) 100vw, 750px" />][2]

Vamos apagar o registro desse bundle que acabamos de excluir, pois todos os bundles são registrados no AppKernel para que possamos usá-los.

Entre no arquivo app/AppKernel.php e apague a linha &#8220;new AppBundle\AppBundle()&#8221;, no meu caso a linha 19.

<pre class="lang-php">&lt;?php

use Symfony\Component\HttpKernel\Kernel;
use Symfony\Component\Config\Loader\LoaderInterface;

class AppKernel extends Kernel
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
//apague    new AppBundle\AppBundle(),    caso contrário acarretará em erro...
        );

        if (in_array($this-&gt;getEnvironment(), array('dev', 'test'))) {
            $bundles[] = new Symfony\Bundle\DebugBundle\DebugBundle();
            $bundles[] = new Symfony\Bundle\WebProfilerBundle\WebProfilerBundle();
            $bundles[] = new Sensio\Bundle\DistributionBundle\SensioDistributionBundle();
            $bundles[] = new Sensio\Bundle\GeneratorBundle\SensioGeneratorBundle();
        }

        return $bundles;
    }

    public function registerContainerConfiguration(LoaderInterface $loader)
    {
        $loader-&gt;load(__DIR__.'/config/config_'.$this-&gt;getEnvironment().'.yml');
    }
}

</pre>

Também devemos excluir a rota desse bundle.
  
Entre no arquivo app/config/routing.yml e apague as linhas abaixo:

<pre class="lang-yml">app:
    resource: @AppBundle/Controller/
    type:     annotation
</pre>

Cuidado caso tenha feito alguma modificação desde a instalação, no meu caso, estou dando continuidade a partir da instalação, e apagando as linhas acima, meu arquivo routing.yml, ficou vazio.

## Criando um bundle utilizando o componente console do Symfony

Vamos criar nosso bundle! Podemos fazer isso codificando, porém o Symfony 2 nos traz um ferramenta poderosa e fantástica, o componente cosole, que já vem instalado em nossa aplicação, ou podemos instalá-lo separadamente pelo <a href="https://packagist.org/packages/symfony/console" title="Symfony Console" target="_blank">packagist</a>, via composer.

Vamos lá.
  
Entre na pasta do projeto pelo terminal:

<pre class="lang-bash">$ cd symfony
</pre>

Primeiramente, para vermos o que o console do symfony é capaz, vamos digitar no terminal:

<pre class="lang-bash">$ php app/console
</pre>

Com este comando seremos apresentados à uma lista de comandos que podemos efetuar em nossa aplicação pelo componente console do Symfony. Se instalarmos alguns componentes adicionais do symfony, essa lista pode aumentar, mas não é nosso caso agora, vamos dar continuidade!

Para criarmos nosso bunble, digitamos no terminal:

<pre class="lang-bash">$ php app/console generate:bundle
</pre>

Após darmos o enter aparecerá a seguinte tela, que é um assistente do Symfony para nos ajudar na geração do bundle:
  
[<img src="http://tableless.com.br/uploads/2015/02/02.png" alt="Criando bundle pelo symfony console" width="750" height="403" class="alignnone size-full wp-image-46838" srcset="uploads/2015/02/02.png 750w, uploads/2015/02/02-259x139.png 259w, uploads/2015/02/02-400x215.png 400w" sizes="(max-width: 750px) 100vw, 750px" />][3]

O symfony nos pede para digitarmos nossa namespace, que é o caminho completo do nosso bundle, primeiramente, temos que dar um nome para nosso vendor, caso não entenda, sugiro a <a href="http://www.php-fig.org/psr/psr-4/" title="PSR-04" target="_blank">leitura da PSR-4</a>, em meus projetos particulares, coloco a sigla do meu nome como vendor &#8220;CJSN&#8221;, porém você pode colocar o nome do seu projeto, do seu cliente, etc&#8230; Aqui vamos colocar Tableless, em seguida o nome de nosso bundle.

Então digitamos

<pre class="lang-bash">$ Bundle namespace: Tableless/CoreBundle
</pre>

Ao darmos enter, o Symfony nos pergunta como esse bundle vai ser reconhecido em nosso projeto e nos sugere um nome: TablelessCoreBundle

<pre class="lang-bash">$ Bundle name [TablelessCoreBundle]:
</pre>

Você pode simplificar digitando apenas CoreBundle, em meu caso vou deixar como está, gosto assim em meus projetos, deixando-os padrão.
  
E damos enter.

Agora a pergunta é: Qual o caminho que queremos instalar nosso bundle?
  
Por padrão vamos deixá-lo na pasta src/, somente damos enter.

<pre class="lang-bash">$ Target directory [/home/candidosouza/tableless/symfony/src]:
</pre>

Como vamos fazer a configuração de nosso bundle?
   
Digitamos annotation e enter:

<pre class="lang-bash">$ Configuration format (yml, xml, php, or annotation): annotation
</pre>

A próxima pergunta é: Se queremos que ele gere toda a estrutura de diretórios de um bundle? Não, apenas damos um enter.

<pre class="lang-bash">$ Do you want to generate the whole directory structure [no]?
</pre>

Nos pergunta sobre a confirmação de geração do bundle, damos enter.

<pre class="lang-bash">$ Do you confirm generation [yes]? 
</pre>

Desejamos adicionar as configurações no AppKernel? Sim queremos, somente digitamos enter.

<pre class="lang-bash">$ Confirm automatic update of your Kernel [yes]?
</pre>

E pergunta se queremos inserir rotas para esse bundle, digitamos enter.

<pre class="lang-bash">$ Confirm automatic update of the Routing [yes]? 
</pre>

E pronto, nosso bundle está criado, veja as imagems abaixo para comparação.
  
[<img src="http://tableless.com.br/uploads/2015/02/03.png" alt="Finalizando criação de bundle" width="750" height="403" class="alignnone size-full wp-image-46843" srcset="uploads/2015/02/03.png 750w, uploads/2015/02/03-259x139.png 259w, uploads/2015/02/03-400x215.png 400w" sizes="(max-width: 750px) 100vw, 750px" />][4]

[<img src="http://tableless.com.br/uploads/2015/02/03-1.png" alt="Imagem finalizada CoreBundle" width="750" height="403" class="alignnone size-full wp-image-46875" srcset="uploads/2015/02/03-1.png 750w, uploads/2015/02/03-1-259x139.png 259w, uploads/2015/02/03-1-400x215.png 400w" sizes="(max-width: 750px) 100vw, 750px" />][5]

Para vermos se está tudo certo, podemos entrar em nosso navegador e digitar a rota exemplo criada pelo Symfony: @Route(&#8220;/hello/{name}&#8221;), então digitamos a url no navegador: http://127.0.0.1:8000/hello/Tableless
  
Lembrando que o servidor deve estar iniciado, você pode ver isso no tutorial anterior. Aparecerá a mensagem &#8220;Hello Tableless!&#8221;, se você notar, verá que a debug toolbar, a barra de ferramentas do Symfony, não está aparecendo, mas não vamos nos preocupar com isso, pois não usaremos essa rota, ela é gerada apenas para exemplo.

Após a crianção do nosso bundle, o CoreBundle, vamos repetir a operação, e criar um novo bundle, agora com o nome ModelBundle.

Novamente digitamos

<pre class="lang-bash">$ php app/console generate:bundle
</pre>

em seguida:

<pre class="lang-bash">$ Tableless/ModelBundle
</pre>

E todo o processo anteriormente feito&#8230;

A primeira coisa a fazer depois de criarmos o ModelBundle, é excluir a rota gerada pelo Symfony, é claro que poderíamos ter feito isso na hora da criação, pelo terminal, quando ele nos faz a última pergunta: Confirmar atualização automática das Rotas[sim]?

<pre class="lang-bash">$ Confirm automatic update of the Routing [yes]? 
</pre>

Era só termos digitado &#8220;no&#8221;, mas para efeito de didática, e para não ficarmos duplicando código nesse tutorial, preferi deixar assim.

Vamos entrar no arquivo app/config/route.yml e vamos apagar a rota gerada para esse bundle.
  
Apague as linhas abaixo:

<pre class="lang-bash">tableless_model:
    resource: "@TablelessModelBundle/Controller/"
    type:     annotation
    prefix:   /
</pre>

Deixando somente a rota do CoreBundle criada anteriormente.

Vamos excluir também, as pastas Controller, e views, pois não vamos usar esses arquivos nesse bundle.
  
Caminhos das pastas a serem excluidas:
  
src/Tableless/ModelBundle/Controller
  
src/Tableless/ModelBundle/Resources/views

[<img src="http://tableless.com.br/uploads/2015/02/04.png" alt="Excluindo pastas" width="750" height="403" class="alignnone size-full wp-image-46859" srcset="uploads/2015/02/04.png 750w, uploads/2015/02/04-259x139.png 259w, uploads/2015/02/04-400x215.png 400w" sizes="(max-width: 750px) 100vw, 750px" />][6]

## Concluindo

Pronto, nosso simples projeto, está configurado e pronto para darmos inicio aos demais processos, neste momento em que se encontra o mesmo, vou comitar, e subir o projeto para o <a href="https://github.com/candidosouza/tableless" title="GitHub do projeto" target="_blank">GitHub</a>. No próximo tutorial veremos como criar entidades com o Doctrine ORM em conjunto com o Symfony, para inserirmos nossos posts no banco de dados.
  
Para finalizarmos, recomendo novamente a <a href="http://symfony.com/doc/current/index.html" title="Documentação do Symfony" target="_blank">documentação do Symfony</a>, caso queiram fazer testes, estudar, se aprofundar mais no assunto!

 [1]: http://tableless.com.br/uploads/2015/02/symfony-logo-tableless.png
 [2]: http://tableless.com.br/uploads/2015/02/01.png
 [3]: http://tableless.com.br/uploads/2015/02/02.png
 [4]: http://tableless.com.br/uploads/2015/02/03.png
 [5]: http://tableless.com.br/uploads/2015/02/03-1.png
 [6]: http://tableless.com.br/uploads/2015/02/04.png