---
title: PHPUnit, como iniciar sem dores
author: Andre Cardoso
type: post
date: 2014-01-07
excerpt: Instalando o PHUnit utilizando o gerenciador de pacotes Composer.
url: /phpunit-como-iniciar-sem-dores/
categories:
  - PHP
  - Técnicas e Práticas
tags:
  - PHPUnit
  - tdd
  - testes automatizados
  - testes unitários

---
Como já mencionei em um artigo anterior, o <a title="Ir ao repositório do PHPUnit" href="https://github.com/sebastianbergmann/phpunit/" target="_blank">PHPUnit</a> é um framework de testes unitários para a linguagem PHP. Ele provê um ecossistema para a execução de testes de forma automatizada.

Neste artigo veremos a sua instalação utilizando o gerenciador de pacotes <a title="Ir à página oficial do Composer" href="http://getcomposer.org/" target="_blank">composer</a>, configuração e estrutura de pastas e alguns testes simples sem persistência de dados.

## Instalando o PHPUnit

Para iniciar a instalação do PHPUnit precisamos primeiramente de um diretório que será nosso diretório de trabalho neste exemplo. Após criado o diretório é necessário criar um arquivo chamado <a title="Ir ao modelo do arquivo composer.json" href="http://getcomposer.org/doc/04-schema.md" target="_blank"><i>composer</i><i>.json</i></a> para que seja definida a necessidade do PHP Unit no projeto. O arquivo _composer__.json_ é responsável por declarar todas as bibliotecas que serão necessárias para o projeto em questão, em suma todas soluções de terceiros, incluindo suas soluções genéricas que encontrem-se no <a title="Ir ao Packagist, repositório do composer" href="https://packagist.org/" target="_blank">repositório do composer</a> serão gerenciadas conforme a especificação do arquivo _composer.json._

O arquivo para este artigo deverá conter o seguinte conteúdo:

<pre class="lang-json">{
    "require-dev": {
        "phpunit/phpunit": "3.7.*"
    }
}</pre>

Isto quer dizer que estamos registrando como uma dependência de nosso projeto o PHPUnit em sua versão 3.7 sempre solicitando a última atualização. Para que sempre seja utilizada a última versão do PHPUnit basta remover a sequência &#8220;3.7.\*&#8221; por simplesmente &#8220;\*&#8221;. O mesmo é possível com qualquer biblioteca gerenciada pelo composer.

Agora já estão prontas as declarações de nossas dependências basta baixar o gerenciador de dependência <a title="Baixar o composer" href="http://getcomposer.org/download/" target="_blank">composer</a> e rodar o comando

<pre class="lang-shell">php composer.phar install.</pre>

Isto irá de maneira automática baixar todas as dependências que foram especificadas no arquivo composer.json, e neste exemplo trata-se apenas do PHPUnit no entanto o próprio PHP Unit requer algumas bibliotecas de terceiros então outras bibliotecas estarão disponíveis além do mesmo dentro da pasta _vendor_ que será criada.

<div id="attachment_40041" style="width: 407px" class="wp-caption aligncenter">
  <img class="size-medium wp-image-40041 " alt="PHPUnit - Instalação a partir do composer" src="http://tableless.com.br/uploads/2013/12/01-composer-install-397x310.png" width="397" height="310" srcset="uploads/2013/12/01-composer-install-397x310.png 397w, uploads/2013/12/01-composer-install-215x168.png 215w, uploads/2013/12/01-composer-install.png 881w" sizes="(max-width: 397px) 100vw, 397px" />
  
  <p class="wp-caption-text">
    Instalação a partir do composer
  </p>
</div>

<div id="attachment_40049" style="width: 394px" class="wp-caption aligncenter">
  <img class="size-medium wp-image-40049 " alt="PHPUnit - Estrutura de pastas" src="http://tableless.com.br/uploads/2013/12/02-estrutura-pastas-384x310.png" width="384" height="310" srcset="uploads/2013/12/02-estrutura-pastas-384x310.png 384w, uploads/2013/12/02-estrutura-pastas-208x168.png 208w, uploads/2013/12/02-estrutura-pastas.png 784w" sizes="(max-width: 384px) 100vw, 384px" />
  
  <p class="wp-caption-text">
    Estrutura de pastas
  </p>
</div>

> Existe uma convenção de padrões definidos pela <a title="Ir à página do Framework Interop Group" href="http://www.php-fig.org/" target="_blank">FIG</a> chamada <a title="Ver todas as PSRs" href="https://github.com/php-fig/fig-standards/tree/master/accepted" target="_blank">PSR (Proposal Standards Recommendation)</a>. Para facilitar será utilizada a definição do Autoloader para o exemplo que está descrito na PSR-0. Após a correta instalação via composer devem ser criadas os diretórios _src_ e dentro dele _Application_.

Com a definição do Autoloader a nova estrutura do composer é a seguinte:

<pre class="lang-json">{
    "autoload": {
        "psr-0": {"Application\\": "src/"}
    },
    "require-dev": {
        "phpunit/phpunit": "3.7.*"
    }
}</pre>

&nbsp;

No arquivo composer.json agora é dito que o autoloader deve reconhecer o namespace &#8220;Application&#8221; que encontra-se dentro do diretorio _src_.

&nbsp;

<div id="attachment_40044" style="width: 598px" class="wp-caption aligncenter">
  <img class="size-medium wp-image-40044 " alt="PHPUnit - Nova estrutura de pastas" src="http://tableless.com.br/uploads/2013/12/4-nova-estrutura-pastas-588x303.png" width="588" height="303" />
  
  <p class="wp-caption-text">
    Nova estrutura de pastas
  </p>
</div>

## Iniciando com um simples teste

Como o PHPUnit já está instalado corretamente no projeto agora vem a parte legal que é criar pequenos testes (unitários, obviamente) e colocar em prática o vermelho-verde-refatora já mencionado no meu post anterior [TDD, por que usar?][1].

Primeiramente deve ser criada a pasta _tests_ que servirá para acomodar todos os casos de teste a serem executados.

Começando com um teste simples, e na verdade este artigo somente mostrará o uso simplificado pois a finalidade do mesmo é apenas mostrar o caminho das pedras, como começar, instalar, configurar e rodar os primeiros testes. A partir daí cabe à necessidade de cada desenvolvedor.

> Aqui será criado um arquivo PHPNativeElements onde serão testados algumas funções nativas do PHP e seus comportamentos. Obviamente que este caso de teste calha somente em modo didático pois tais testes e classe testada terá muito mais de uma única responsabilidade, é somente em caráter demonstrativo.

Criado o arquivo _PHPNativeElementsTest.php_ dentro do diretório tests, siga o exemplo abaixo.

<div id="attachment_40045" style="width: 383px" class="wp-caption aligncenter">
  <img class="size-medium wp-image-40045  " alt="PHPUnit - Estrutura inicial do primeiro teste" src="http://tableless.com.br/uploads/2013/12/5-estrutura-primeiro-teste-373x310.png" width="373" height="310" srcset="uploads/2013/12/5-estrutura-primeiro-teste-373x310.png 373w, uploads/2013/12/5-estrutura-primeiro-teste-202x168.png 202w, uploads/2013/12/5-estrutura-primeiro-teste.png 738w" sizes="(max-width: 373px) 100vw, 373px" />
  
  <p class="wp-caption-text">
    Estrutura inicial do primeiro teste
  </p>
</div>

>  Para que seja reconhecido como um teste o arquivo deve conter a sufixo Test.

## Executando de forma simples

Como o PHPUnit foi instalado a partir do composer, é a partir da estrutura montada pelo mesmo que este será executado digitando no terminal

<pre class="lang-shell">./vendor/bin/phpunit</pre>

Com isto uma tela de ajuda deve aparecer com todas as opções disponíveis para a utilização do PHPUnit. Seguem as definições do comando que será executado neste primeiro momento.

<span style="color: #000080">./vendor/bin/phpunit</span> <span style="color: #333333">&#8211;colors</span> <span style="color: #008000">&#8211;debug</span> <span style="color: #800000">tests/PHPNativeElements </span>onde:

<span style="color: #000080">./vendor/bin/phpunit</span>: o próprio executável do PHPUnit

<span style="color: #333333">&#8211;colors</span>: habilita coloração ( assim podemos ver os estágios vermelho-verde de forma mais simples)

<span style="color: #008000">&#8211;debug</span>: habilita o modo debug para detalhamento das ações que estão sendo tomadas durante os testes – Esta ação serve como ótima documentação como já mencionado em meu artigo anterior.

<span style="color: #800000">tests/PHPNativeElements</span>: o nome da classe de testes a ser testada.

Ao rodarmos o comando acima a mensagem resultante deverá ser a de que não há testes disponíveis na classe testada.

<div id="attachment_40050" style="width: 484px" class="wp-caption aligncenter">
  <img class="size-medium wp-image-40050  " alt="PHPUnit - Falta de testes" src="http://tableless.com.br/uploads/2013/12/6-falta-de-testes-474x310.png" width="474" height="310" srcset="uploads/2013/12/6-falta-de-testes-474x310.png 474w, uploads/2013/12/6-falta-de-testes-256x168.png 256w, uploads/2013/12/6-falta-de-testes.png 881w" sizes="(max-width: 474px) 100vw, 474px" />
  
  <p class="wp-caption-text">
    Informação de que ainda não há testes
  </p>
</div>

&nbsp;

## Fazendo o primeiro teste passar

<!-- P { margin-bottom: 0.08in; }A:link {  } -->O TDD define que o desenvolvimento deve ser orientado a testes, com isso, criaremos primeiramente a expectativa na nossa classe de testes e em seguida a implementação no código de produção.

Após o método _tearDown_ que já encontra-se na classe _PHPNativeElementsTest_ crie um método chamado _testOperacaoMatematica_. Assim como a classe de teste possui uma convenção com os métodos também é necessário especificar qual trata-se de um teste a partir do prefixo _test._ Por este motivo nosso primeiro caso de teste se chamar testOperacaoMatematica. Caso não contenha o prefixo test e, não sendo os métodos setUp e tearDown, o PHPUnit simplesmente não executa o método.

Como estamos utilizando o Autoloader, em nossa classe de teste usaremos o namespace &#8220;_Application\__NativeElements\Math&#8221;_ para carregar a nossa classe que será testada a partir da classe de testes. Como atributo de nossa classe de teste adicionaremos &#8220;$math&#8221; e nele instanciaremos a classe _Application\__NativeElements\Math_ dentro do método _setUp_.

<div id="attachment_40052" style="width: 434px" class="wp-caption aligncenter">
  <img class="size-medium wp-image-40052 " alt="PHPUnit - Nova estrutura da classe de teste" src="http://tableless.com.br/uploads/2013/12/7-nova-estrutura-classe-de-testes1-424x310.png" width="424" height="310" srcset="uploads/2013/12/7-nova-estrutura-classe-de-testes1-424x310.png 424w, uploads/2013/12/7-nova-estrutura-classe-de-testes1-230x168.png 230w, uploads/2013/12/7-nova-estrutura-classe-de-testes1.png 804w" sizes="(max-width: 424px) 100vw, 424px" />
  
  <p class="wp-caption-text">
    Nova estrutura da classe de teste
  </p>
</div>

<!-- P { margin-bottom: 0.08in; }A:link {  } -->Ao rodarmos novamente o PHPUnit o teste simplesmente quebra. Isto porque a classe 

_Application\__NativeElements\Math_ ainda não existe. Este é o próximo passo, o código que fará o testes passar.

<div id="attachment_40053" style="width: 498px" class="wp-caption aligncenter">
  <img class="size-medium wp-image-40053 " alt="PHPUnit - Quebra do teste" src="http://tableless.com.br/uploads/2013/12/8-quebra-do-teste-488x310.png" width="488" height="310" srcset="uploads/2013/12/8-quebra-do-teste-488x310.png 488w, uploads/2013/12/8-quebra-do-teste-264x168.png 264w, uploads/2013/12/8-quebra-do-teste.png 875w" sizes="(max-width: 488px) 100vw, 488px" />
  
  <p class="wp-caption-text">
    Quebra do teste por não existir a classe testada
  </p>
</div>

<!-- P { margin-bottom: 0.08in; }A:link {  } -->Criamos o arquivo 

_Math.php_ dentro do diretório _Application/NativeElements_ e no mesmo a classe _Math_ definindo como namespace _Application\NativeElements_. Por hora nenhum método é criado nesta nova classe.

<div id="attachment_40056" style="width: 514px" class="wp-caption aligncenter">
  <img class="size-medium wp-image-40056 " alt="PHPUnit - Classe de produção, nela os problemas criados nos testes serão solucionados" src="http://tableless.com.br/uploads/2013/12/9-class-504x310.png" width="504" height="310" srcset="uploads/2013/12/9-class-504x310.png 504w, uploads/2013/12/9-class-273x168.png 273w, uploads/2013/12/9-class.png 955w" sizes="(max-width: 504px) 100vw, 504px" />
  
  <p class="wp-caption-text">
    Classe de produção, nela os problemas criados nos testes serão solucionados
  </p>
</div>

<!-- P { margin-bottom: 0.08in; }A:link {  } -->Rodando nosso teste novamente ele quebra mais uma vez. Agora o que está faltando é o método testado ( 

_sum_ ).

<div id="attachment_40057" style="width: 598px" class="wp-caption aligncenter">
  <img class="size-medium wp-image-40057 " alt="PHPUnit - Faltando método sum" src="http://tableless.com.br/uploads/2013/12/10-method-missing-588x289.png" width="588" height="289" srcset="uploads/2013/12/10-method-missing-588x289.png 588w, uploads/2013/12/10-method-missing-329x162.png 329w, uploads/2013/12/10-method-missing-628x310.png 628w, uploads/2013/12/10-method-missing.png 880w" sizes="(max-width: 588px) 100vw, 588px" />
  
  <p class="wp-caption-text">
    Faltando método sum
  </p>
</div>

<!-- P { margin-bottom: 0.08in; }A:link {  } -->Ao criar o método sum e sua lógica estando correta o teste atual passará, então passamos do estágio vermelho para o estágio verde. Como este exemplo é uma simples operação matemática muito provavelmente não será necessária uma refatoração. No entanto sendo um lógica mais complexa o ideal é que sempre comece testando pequenos passos, que são chamados de baby steps ou passos de bebê. Ao se deparar com uma situação complexa em que o resultado depende de N variáveis, trata-se sempre o meio mais simples e os testes passando passa-se a procurar solucionar uma nova condição para o resultado.

<div id="attachment_40058" style="width: 598px" class="wp-caption aligncenter">
  <img class="size-medium wp-image-40058 " alt="PHPUnit - Método com a lógica necessária e primeiro teste passando" src="http://tableless.com.br/uploads/2013/12/11-pass-588x262.png" width="588" height="262" srcset="uploads/2013/12/11-pass-588x262.png 588w, uploads/2013/12/11-pass-329x146.png 329w, uploads/2013/12/11-pass-660x294.png 660w, uploads/2013/12/11-pass.png 1364w" sizes="(max-width: 588px) 100vw, 588px" />
  
  <p class="wp-caption-text">
    Método com a lógica necessária e primeiro teste passando
  </p>
</div>

<!-- P { margin-bottom: 0.08in; }A:link {  } -->Agora basta adicionar os asserts para as demais operações matemáticas.

<div id="attachment_40059" style="width: 598px" class="wp-caption aligncenter">
  <img class="size-medium wp-image-40059 " alt="PHPUnit - Outros métodos de operações matemáticas simples" src="http://tableless.com.br/uploads/2013/12/12-other-methods-588x272.png" width="588" height="272" srcset="uploads/2013/12/12-other-methods-588x272.png 588w, uploads/2013/12/12-other-methods-329x152.png 329w, uploads/2013/12/12-other-methods-660x305.png 660w, uploads/2013/12/12-other-methods.png 1358w" sizes="(max-width: 588px) 100vw, 588px" />
  
  <p class="wp-caption-text">
    Outros métodos de operações matemáticas simples
  </p>
</div>

<!-- P { margin-bottom: 0.08in; }A:link {  } -->

> Como pode ser percebido, como terceiro parâmetro do assert foi adicionada uma mensagem opcional, isso para que ao dar erro da asserção tal mensagem seja exibida, conforme a imagem seguinte.

<div id="attachment_40060" style="width: 507px" class="wp-caption aligncenter">
  <img class="size-medium wp-image-40060 " alt="PHPUnit - Mensagem de erro de asserção" src="http://tableless.com.br/uploads/2013/12/13-message-497x310.png" width="497" height="310" srcset="uploads/2013/12/13-message-497x310.png 497w, uploads/2013/12/13-message-269x168.png 269w, uploads/2013/12/13-message.png 809w" sizes="(max-width: 497px) 100vw, 497px" />
  
  <p class="wp-caption-text">
    Mensagem de erro de asserção
  </p>
</div>

&nbsp;

## Refatorando

<!-- P { margin-bottom: 0.08in; }A:link {  } -->Agora voltando ao código originado na classe 

_Math_, dá pra perceber que há muita repetição pois todos os métodos recebem dois valores e retornam uma operação correspondente. Como utilizando TDD temos segurança em desenvolver, podemos tranquilamente remover tais repetições criando uma interface onde é previamente definida a operação a ser realizada e retorna o resultado desta operação. Obviamente com esta atitude o teste também sofrerá alterações e isso é algo comum pois uma aplicação está sempre evoluindo.

Frenta à necessidade de refatoração novamente começamos a partir do teste e ele fica como na imagem a seguir:

<div id="attachment_40061" style="width: 498px" class="wp-caption aligncenter">
  <img class="size-medium wp-image-40061 " alt="PHPUnit - Alterações na classe de teste" src="http://tableless.com.br/uploads/2013/12/14-test-refactor-488x310.png" width="488" height="310" srcset="uploads/2013/12/14-test-refactor-488x310.png 488w, uploads/2013/12/14-test-refactor-264x168.png 264w, uploads/2013/12/14-test-refactor.png 899w" sizes="(max-width: 488px) 100vw, 488px" />
  
  <p class="wp-caption-text">
    Alterações na classe de teste
  </p>
</div>

<!-- P { margin-bottom: 0.08in; }A:link {  } -->Com a refatoração nossa classe Math é modificada e criada uma interface:

<div id="attachment_40063" style="width: 598px" class="wp-caption aligncenter">
  <img class="size-medium wp-image-40063 " alt="PHPUnit - refatoração da classe Math" src="http://tableless.com.br/uploads/2013/12/15-refactor-588x284.png" width="588" height="284" srcset="uploads/2013/12/15-refactor-588x284.png 588w, uploads/2013/12/15-refactor-329x159.png 329w, uploads/2013/12/15-refactor-640x310.png 640w, uploads/2013/12/15-refactor.png 1354w" sizes="(max-width: 588px) 100vw, 588px" />
  
  <p class="wp-caption-text">
    Refatoração da classe Math
  </p>
</div>

<!-- P { margin-bottom: 0.08in; }A:link {  } -->E agora rodando novamente o teste após a refatoração, simplesmente continuamos com tudo verde, ou seja, alteramos muito a forma de implementação de uma classe e ela continua executando seu papel como deve.

<div id="attachment_40064" style="width: 587px" class="wp-caption aligncenter">
  <img class="size-medium wp-image-40064 " alt="PHPUnit - Teste passando após refatoração" src="http://tableless.com.br/uploads/2013/12/16-refactor-pass-577x310.png" width="577" height="310" srcset="uploads/2013/12/16-refactor-pass-577x310.png 577w, uploads/2013/12/16-refactor-pass-313x168.png 313w, uploads/2013/12/16-refactor-pass.png 818w" sizes="(max-width: 577px) 100vw, 577px" />
  
  <p class="wp-caption-text">
    Teste passando após refatoração
  </p>
</div>

<!-- P { margin-bottom: 0.08in; }A:link {  } -->

> Este é apenas um exemplo didático de refatoração, mas mesmo com ele dá pra perceber como houve a anulação de código repetido e para um futura manutenção basta que mexa-se em um local somente para que surta efeitos à todas as operações matemáticas.

## Finalizando

<!-- P { margin-bottom: 0.08in; }A:link {  } -->Neste artigo foi abordado apenas a instalação do PHPUnit e a execução de um teste muito simples. Para testes mais avançados serão criados novos artigos sempre em sequência para que o estudo de desenvolvimento orientado a testes siga um fluxo sadio. Já fora criado um artigo explicando os por ques de se utilizar e não se utilizar TDD que encontra-se neste 

[link][1] e é o primeiro artigo da sequência.

<!-- P { margin-bottom: 0.08in; }A:link {  } -->Os próximos artigos seguirão a sequência abaixo:

  * Configurações avançadas – Apenas uma breve abordagem de como realizar configurações avançadas na execução do PHPUnit gerando reports como coverage.
  * Persistência – Será utilizado o ORM Doctrine para complementarmos o projeto
  * Mockery – Utilizando objetos simulados para atender certos comportamentos

&nbsp;

Você pode baixar o código-fonte dos exemplos apresentados aqui no <a title="Ir para o repositório de exemplos desenvolvidos neste artigo" href="https://github.com/andrebian/phpunit-como-iniciar-sem-dores" target="_blank">github</a>.

 [1]: http://tableless.com.br/tdd-por-que-usar "Ler mais sobre TDD"