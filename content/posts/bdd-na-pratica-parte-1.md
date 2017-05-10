---
title: BDD na prática – Parte 1
author: Jefersson Nathan
type: post
date: 2014-04-09
excerpt: Sinta o gostinho do BDD em um simples hello world
url: /bdd-na-pratica-parte-1/
dsq_thread_id: 2592146000
categories:
  - Geral

---
Se você não sabe o que é **Behavior driven development,** para ter um melhor proveito desse artigo,  leia uma [introdução ao BDD][1] antes de prosseguir.

Para começo de conversa, estaremos fazendo uma abordagem prática sobre testes de comportamento. Para isso, utilizaremos a biblioteca para testes [behat][2]. Vamos ao nosso arquivo `composer.json:`

<pre class="lang-javascript">{
    "require-dev": {
        "behat/behat": "2.4.*@stable"
    },
    "config": {
        "bin-dir": "bin/"
    }
}</pre>

Se ainda não estiver familiarizado com o uso do **composer** para gerenciamento de dependências de seus projetos em php, vale a pena dar uma olhada em [composer para iniciantes][3].

Agora, basta instalar nossas dependências com o seguinte comando:

<pre class="lang-sh">$ composer install</pre>

<img class="size-full wp-image-42015 aligncenter" alt="Captura de tela 2014-04-06 13.52.43" src="http://tableless.com.br/uploads/2014/04/Captura-de-tela-2014-04-06-13.52.43.png" width="684" height="816" srcset="uploads/2014/04/Captura-de-tela-2014-04-06-13.52.43.png 684w, uploads/2014/04/Captura-de-tela-2014-04-06-13.52.43-400x477.png 400w" sizes="(max-width: 684px) 100vw, 684px" />
  
De forma alternativa, você poderá fazer uma instalação global baixando o arquivo `behat.phar` e deixando acessível de seu sistema operacional, geralmente esse processo é simples, e basta criar um link simbólico em `/usr/local/bin` para o arquivo que deseja executar.

## Como funciona?

Se dermos uma olhada na estrutura que o _**composer**_ criou para a gente, notaremos que um diretório **_feature_** foi criado. Nesse diretório criaremos os arquivos ***.feature** que descreverão um conjunto de ações para atingir um determinado objetivo.

Para começar criaremos o arquivo **example.feature**.

<img class="size-full wp-image-42019 aligncenter" alt="Estrutura de diretórios" src="http://tableless.com.br/uploads/2014/04/Captura-de-tela-2014-04-06-14.25.49.png" width="407" height="95" srcset="uploads/2014/04/Captura-de-tela-2014-04-06-14.25.49.png 407w, uploads/2014/04/Captura-de-tela-2014-04-06-14.25.49-400x93.png 400w" sizes="(max-width: 407px) 100vw, 407px" />

Se você estiver usando o **Sublime Text**, instale essa extensão [https://github.com/omissis/sublime-behat-syntax][4] que provê highlight em arquivos *.feature

No nosso arquivo **example.feature**, iremos descrever nosso cenário, o que queremos _testar._

<img class="alignnone size-full wp-image-42024" alt="Captura de tela 2014-04-06 14.54.18" src="http://tableless.com.br/uploads/2014/04/Captura-de-tela-2014-04-06-14.54.18.png" width="609" height="474" srcset="uploads/2014/04/Captura-de-tela-2014-04-06-14.54.18.png 609w, uploads/2014/04/Captura-de-tela-2014-04-06-14.54.18-400x311.png 400w" sizes="(max-width: 609px) 100vw, 609px" />

Com uma **feature** já escrita, iremos executar o _behat_ para nos dar a descrição e métodos dessa feature em PHP, daí prosseguiremos com a implementação dos métodos que eles nos forneceu. Para isso basta executarmos o arquivo **behat**, dentro da pasta **bin** que foi criada pelo _composer_.

<pre class="lang-sh">$ bin/behat features/example.feature</pre>

<img class="alignnone size-full wp-image-42029" alt="Behat feature" src="http://tableless.com.br/uploads/2014/04/Captura-de-tela-2014-04-06-15.07.06.png" width="684" height="620" srcset="uploads/2014/04/Captura-de-tela-2014-04-06-15.07.06.png 684w, uploads/2014/04/Captura-de-tela-2014-04-06-15.07.06-400x362.png 400w" sizes="(max-width: 684px) 100vw, 684px" />

Assim, o **behat** cospe pra nos um código PHP para que coloquemos na classe de feature. E aí começaremos a _codar_ os cenários. No arquivo `features/bootstrap/FeatureContext.php` colaremos o código que foi fornecido pelo **behat**.

<pre class="lang-php">&lt;?php

use Behat\Behat\Context\BehatContext;

class FeatureContext extends BehatContext
{
    /** @Given /^some step with "([^"]*)" argument$/ */
    public function someStepWithArgument($argument1)
    {
        return $argument1;
    }

    /** @Given /^number step with (\d+)$/ */
    public function numberStepWith($argument1)
    {
        return $argument1;
    }
}</pre>

Aqui temos uma classe simples, que **não testa nada**, mais é um bom ponto de partidada para entender como funciona a ferramenta e o esquema de testes de comportamento. Pois _codar_ os cenários deve ser a parte mais fácil do processo, se você tem **steps** bem definidos.

para rodar esse testes execute o seguinte comando.

<pre class="lang-sh">$ bin/behat features/example.feature</pre>

## Hello world

Agora que temos uma ideia de como o **behat** trabalha, faremos o clássico **hello world**.
  
Em nosso arquivo `example.feature` descreveremos o seguinte cenário:

<img class="alignnone size-full wp-image-42040" alt="Hello world feature behat" src="http://tableless.com.br/uploads/2014/04/Captura-de-tela-2014-04-06-16.53.08.png" width="605" height="333" srcset="uploads/2014/04/Captura-de-tela-2014-04-06-16.53.08.png 605w, uploads/2014/04/Captura-de-tela-2014-04-06-16.53.08-400x220.png 400w" sizes="(max-width: 605px) 100vw, 605px" />

Nesse cenário estaremos testando que quando passarmos a string **Hello world,** nossa classe tem que concatenar nossa string a uma exclamação. Com isso já poderemos escrever nossa classe PHP para testar essa **feature.**

<pre class="lang-php">&lt;?php

use Behat\Behat\Context\BehatContext;

class FeatureContext extends BehatContext
{
    private $_string;

    /** @Given /^some step with "([^"]*)" argument$/ */
    public function someStepWithArgument($string)
    {
        $this-&gt;_string = strtolower($string);
    }

    /**
     * @Then /^i have "([^"]*)"$/
     */
    public function iHave($expected)
    {
        if (0 !== strcmp(strtolower($expected), $this-&gt;_string.'!'))
            throw new Exception('Wrong "hello world" received: '.$this-&gt;_string );

        return $expected;
    }
}</pre>

Se executarmos o teste com o **behat**, poderemos ver como está o nosso cenário.

&nbsp;

<img class="alignnone size-full wp-image-42045" alt="Behat hello world execution" src="http://tableless.com.br/uploads/2014/04/Captura-de-tela-2014-04-06-17.16.30.png" width="740" height="494" srcset="uploads/2014/04/Captura-de-tela-2014-04-06-17.16.30.png 740w, uploads/2014/04/Captura-de-tela-2014-04-06-17.16.30-400x267.png 400w" sizes="(max-width: 740px) 100vw, 740px" />

## Conclusão

Escrever testes de comportamento é sempre bom, e podemos consulta-los sempre, seja pra esclarecer uma regra de negócio ou para integrar novas pessoas ao time de desenvolvimento. Vendo os cenários sabemos exatamente o que uma classe/entidade deve fazer. Seu objetivo e contexto ficam claros. Os incentivo fortemente a implantar uma cultura de testes de software em sua empresa e projetos. Você tem muito a ganhar a longo prazo.

 [1]: http://tableless.com.br/introducao-ao-behavior-driven-development/
 [2]: http://behat.org/
 [3]: http://tableless.com.br/composer-para-iniciantes/
 [4]: https://www.dropbox.com/s/xb6mmsxy5qdtjja/Captura%20de%20tela%202014-04-06%2014.47.25.png