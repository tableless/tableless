---
title: Composer – um pouco além do básico
author: Andre Cardoso
type: post
date: 2014-04-01
excerpt: 'Este post visa explicar algumas funcionalidades mais avançadas do composer, se você ainda não conhece o composer por favor leia <a title="Composer para iniciantes" href="http://tableless.com.br/composer-para-iniciantes/">Composer para iniciantes</a> antes de prosseguir.'
url: /composer-um-pouco-alem-basico/
dsq_thread_id: 2470206369
categories:
  - PHP
  - Técnicas e Práticas
tags:
  - composer
  - php

---
No post anterior expliquei o que vem a ser o composer, como baixar, criar o arquivo de configurações e instalar pacotes ou bibliotecas. Agora veremos algumas questões um pouco mais avançadas sobre o uso do composer.

## Instalação global

O composer suporta instalação global para que seja utilizado apenas um &#8220;executável&#8221; para todo e qualquer projeto. Usei o termo executável pois refere-se ao composer.phar, que como explicado no post anterior é uma forma de empacotamento no PHP que transforma a aplicação toda em um único arquivo que é facilmente executável em qualquer local de seu sistema operacional.

O processo de instalação global do composer se dá das mesmas formas que a instalação já mostrada no post anterior com uma pequena diferença, selecionamos um diretório para manter o composer e quando utilizarmos, utilizamos sempre a partir deste diretório.

Mãos na massa!

> Todos os exemplos aqui criados foram realizados em ambiente Linux. No Mac OS X é semelhante e no Windows há algumas pequenas diferenças com relação à execução do PHP, com isso sugiro que leia a <a title="Documentação oficial do composer" href="https://getcomposer.org/doc/" target="_blank">documentação oficial</a> do composer para maiores detalhes.

Instalarei o composer no diretório /opt de meu Linux, você pode selecionar o diretório de sua preferência pois funcionará da mesma forma, desde que você tenha o PHP instalado é claro.

<pre class="lang-json">$ cd /opt && mkdir composer && cd composer</pre>

O comando acima em 3 passos (separados por **&&**). No passo 1, entro no diretório /opt. No passo 2 crio uma pasta chamada composer e no passo 3 entro na pasta _composer_ recém criada.

> Lembrando que você deve possuir permissão de escrita no diretório que pretende instalar o composer globalmente.

Agora dentro da pasta /opt/composer basta que baixemos o composer através de uma das opções abaixo:

<pre>curl -sS https://getcomposer.org/installer | php</pre>

ou

<pre>php -r "readfile('https://getcomposer.org/installer');" | php</pre>

Com isso dentro da pasta /opt/composer deve agora existir o arquivo _composer.phar_. Os passos descritos até aqui são ilustrados na imagem abaixo.

<img class="aligncenter" src="https://raw.githubusercontent.com/andrebian/posts/master/tableless/composer-um-pouco-alem-do-basico/images/01-download-do-composer.jpg" alt="Download do composer" width="1320" height="621" />

Ainda dentro de _/opt/composer_ rodamos o comando **php composer.phar**, é exibido o menu de ajuda do composer indicando que foi instalado corretamente.

### Utilizando o composer global em um projeto

Criamos um projeto qualquer em um diretório de sua escolha. Farei o mesmo em meu Desktop em uma pasta chamada _composer-alem-do-basico_. Dentro desta pasta crio um arquivo chamado _composer.json_ adicionando a seguinte estrutura:

<pre class="lang-json">{
    "authors": [
        {
            "name": "Seu nome",
            "email": "seu email"
        }
    ],
    "require": {
        "php": "&gt;=5.2.8",
    }
}</pre>

Perceba que não temos nenhum pacote de terceiro como dependência ainda, somente definimos que a versão mínima do PHP para rodarmos a aplicação é a 5.2.8, deixaremos esta versão por enquanto e adicionaremos em &#8220;require&#8221; o <a title="ORM Doctrine" href="http://www.doctrine-project.org/" target="_blank">ORM Doctrine</a>. Não será criado nenhum código utilizando o Doctrine, apenas está sendo incluso por ser um projeto que não possui muitas dependências fazendo a instalação ser mais rápida. Então nosso require agora fica assim:

<pre class="lang-json">"require": {
    "php": "&gt;=5.2.8",
    "doctrine/orm" : "2.4.*"
}</pre>

Note que na versão desejada do Doctrine informei 2.4.\*, isto significa que sempre será utilizada a versão mais recente dentro do release 2.4. Caso você queira estar sempre com a mais atual possível basta remover a numeração da versão e adicionar somente &#8220;\*&#8221;, desta forma nosso require no _composer.json_ tem esta estrutura:

<pre class="lang-json">"require": {
    "php": "&gt;=5.2.8",
    "doctrine/orm" : "*"
}</pre>

Agora que está configurada nossa primeira dependência do projeto basta que rodemos o comando **php /opt/composer/composer.phar install**. Atenção ao caminho de onde está sendo rodado o composer, perceba que é a pasta que instalamos ele anteriormente. Com isso não preciso ficar para cada projeto baixando o _composer.phar_.

<img class="aligncenter" src="https://raw.githubusercontent.com/andrebian/posts/master/tableless/composer-um-pouco-alem-do-basico/images/02-instalando-primeiras-dependencias.jpg" alt="instalação via composer" width="877" height="692" />

O Doctrine assim como todas as suas dependências são instaladas e temos agora esta estrutura dentro de nosso projeto:

<img class="aligncenter" src="https://raw.githubusercontent.com/andrebian/posts/master/tableless/composer-um-pouco-alem-do-basico/images/03-nova-estrutura-vendor.jpg" alt="Estrutura inicial" width="791" height="615" />

&nbsp;

## Qual a vantagem do composer com instalação global?

Apesar de muitos pensarem e economia de espaço isso é irrelevante pois o _composer.phar_ &#8220;pesa&#8221; apenas 1MB aproximadamente. Há a vantagem que o composer sempre estará disponível para qualquer aplicação eliminando possíveis erros de tentar rodar o comando **php composer.phar alguma-coisa** e o composer.phar não estar presente, ou seja, basicamente a vantagem em possuir uma instalação global é você nunca esquecer de instalá-lo para cada aplicação sua.

No demais não há vantagens pois para cada aplicação o composer realizará o download de todas suas dependências individualmente para cada aplicação, ou seja, se você possuir 3 aplicações, o _composer.phar_ será somente 1 (na pasta /opt/composer/composer.phar) no entanto os vendors serão específicos para cada aplicação como mostra a imagem abaixo:

<img class="aligncenter" src="https://raw.githubusercontent.com/andrebian/posts/master/tableless/composer-um-pouco-alem-do-basico/images/04-dois-projetos-com-vendors-distintos.jpg" alt="Vendors" width="792" height="465" />

## 

## Errata

Conforme mencionado em um cometário pelo Marcel dos Santos o correto para a instalação ser de fato global seria que o composer estivesse em _/usr/local/bin_. Você pode simplesmente mover o composer.phar que atualmente encontra-se em _/opt/composer_ para a pasta _/usr/local/bin_ e para que seja executado basta em seu terminal digitar **composer.phar** em qualquer ponto do seu sistema operacional.

## 

## Direcionamento de vendors

Por padrão o composer entende que as bibliotecas de terceiros devem ficar dentro do diretório _vendor_ mas é possível alterar. Pense em uma situação em que você está trabalhando com algum framework que fornece uma estrutura de diferente da estabelecida pelo composer, o CakePHP por exemplo, por padrão neste framework as bibliotecas de terceiros são instaladas em _vendors_ (no plural mesmo).

Isto é facilmente configurado através do arquivo _composer.json_. Decalararei que minhas bibliotecas de terceiros serão acondicionadas em _3rdparty_ apenas para fins didáticos. Para direcionar os vendors do composer precisamos adicionar a informação de onde nossos vendors serão acondicionados:

<pre class="lang-json">....
"require": {
    "php": "&gt;=5.2.8",
    "doctrine/orm": "*"
},
"config": {
    "vendor-dir": "3rdparty"
}
.....</pre>

Feito isto basta rodar o comando **php /opt/composer/composer.phar install** caso não tenha instalado ainda ou **php /opt/composer/composer.phar update** caso já tenha realizado alguma instalação anteriormente.

> Caso você execute o update do composer ( &#8230; composer.phar update) e alterou a pasta de vendors, esteja ciente de que a pasta que existia antes permanecerá em sua aplicação e você terá de removê-la manualmente pois o composer perdeu a referência da mesma a partir do momento que você alterou o &#8220;vendor-dir&#8221;.

A nova estrutura de nossa aplicação será esta:

<img class="aligncenter" src="https://raw.githubusercontent.com/andrebian/posts/master/tableless/composer-um-pouco-alem-do-basico/images/05-nova-estrutura-vendor-path.jpg" alt="Nova estrutura vendor" width="809" height="550" />

## Direcionando pacotes

Cada pacote que você define como uma dependência de sua aplicação possui uma série de configurações e podem conter dependências também que são listadas em seus composer.json. Ou seja, cada pacote possui (comumente) dentro dele um json informando do que eles dependem, se são plugins de algum framework ou CMS entre outras configurações.

Um bom exemplo de plugins que são instalados em seus diretórios corretos são os plugins do wordpress, desde que você informe que estará utilizando os instaladores do composer _&#8220;composer/installers&#8221;: &#8220;*&#8221;_. Caso você não esteja utilizando os instaladores do composer pode simplesmente direcionar cada pacote para onde bem entender.

<pre class="lang-json">....
"require": {
    "php": "&gt;=5.2.8",
    "doctrine/orm": "*",
    "josegonzalez/cakephp-upload": "*"
},
"extra" : {
    "installer-paths" : {
        "plugins/Upload" : ["josegonzalez/cakephp-upload"]
    }
},
....</pre>

Mesmo que você esteja utilizando os instaladores ainda sim pode personalizar pacote por pacote onde quer que eles sejam instalados dentro de sua aplicação.

No novo exemplo do composer estou informando que o plugin de upload do CakePHP será instalado na pasta _plugins/Upload_ ao invés de _app/Plugin/Upload_ como seria instalado pelo CakePHPInstaller do composer.

<img class="aligncenter" src="https://raw.githubusercontent.com/andrebian/posts/master/tableless/composer-um-pouco-alem-do-basico/images/06-pacote-em-diretorio-personalizado.jpg" alt="pacote em diretorio personalizado" width="795" height="456" />

Como você pode ver, é possível personalizar a instalação cada pacote com simples configuração através de nosso arquivo _composer.json_.

## Require ou require-dev?

O composer trabalha basicamente com dois tipos de dependências, os _require _que são os estritamente necessários para o funcionamento da aplicação e os _require-dev_ que são dependências utilizadas em ambiente de desenvolvimento, são elas ferramentas como PHPUnit, ferramentas de log, entre outras. No exemplo abaixo informamos que para nossa aplicação utilizaremos o ORM Doctrine e para o ambiente de desenvolvimento somente utilizaremos o PHPUnit.

<pre class="lang-json">"require": {
    "php": "&gt;=5.2.8",
    "doctrine/orm": "*",
    "josegonzalez/cakephp-upload": "*"
},
"require-dev" : {
    "phpunit/phpunit" : "4.0.*"
},</pre>

Com a configuração distinta podemos instalar no ambiente de produção somente as dependências necessárias para o funcionamento correto da aplicação deixando de lado as dependências de desenvolvimento.

Como já realizamos a primeira instalação através do composer agora apenas utilizamos o comando **php /opt/composer/composer.phar update** (se for a instalação global do composer) ou **php composer.phar update** (se o composer.phar foi baixado na raiz de sua aplicação). Com este comando todos os pacotes serão instalados.

<img class="aligncenter" src="https://raw.githubusercontent.com/andrebian/posts/master/tableless/composer-um-pouco-alem-do-basico/images/07-atualizando-dev.jpg" alt="Atualização dev" width="834" height="615" />

Após a atualização (que baixará muitos pacotes) a nova estrutura de nosso projeto é a seguinte.

<img class="aligncenter" src="https://raw.githubusercontent.com/andrebian/posts/master/tableless/composer-um-pouco-alem-do-basico/images/08-estrutura-com-dev.jpg" alt="Nova estrutura com Dev" width="960" height="672" />

Pensemos agora que estamos no ambiente de produção ou homologação onde não se faz necessário o PHPUnit. Não é necessária a remoção do mesmo no arquivo \*composer.json\* e sim rodarmos o comando **php composer.phar update &#8211;no-dev** e o resultado será como na imagem abaixo.

<img class="aligncenter" src="https://raw.githubusercontent.com/andrebian/posts/master/tableless/composer-um-pouco-alem-do-basico/images/09-update-sem-dev.jpg" alt="Update sem Dev" width="955" height="499" />

Note apenas que na imagem acima eu rodei o update em meu ambiente de desenvolvimento apenas excluindo os pacotes de modo _dev_ para ilustrar o funcionamento. Na imagem também é possível perceber que o PHPUnit e suas dependências que já estavam instalados foram removidos por não serem mais necessários em modo produção. Na imagem abaixo está a nova estrutura de nossa aplicação.

<img class="aligncenter" src="https://raw.githubusercontent.com/andrebian/posts/master/tableless/composer-um-pouco-alem-do-basico/images/06-pacote-em-diretorio-personalizado.jpg" alt="Pacote personalizado" width="795" height="456" />

## 

## Definição de Autoload

Para quem não conhece existe a <a title="FIG" href="http://www.php-fig.org/" target="_blank">FIG</a> (Framework Interop Group) que visa sugerir padrões de desenvolvimento através de suas PSRs. Atualmente são 4 recomendações sendo a primeira delas (<a title="Conheça a PSR-0" href="http://www.php-fig.org/psr/psr-0/" target="_blank">PSR-0</a>) a que trata de como o carregamento de sua aplicação deve ocorrer. Basicamente é a informação de onde será definido o namespace de sua aplicação.

<pre class="lang-json">"autoload" : {
    "psr-0": {
         "Tableless\\": "src/"
    }
}</pre>

Note que foi definido o namespace _Tableless_ indicando que o mesmo está dentro da pasta _src_. O nome da pasta pode ser outro qualquer e não somente _src_.

Com isso a nova estrutura de nossa aplicação é esta

<img class="aligncenter" src="https://raw.githubusercontent.com/andrebian/posts/master/tableless/composer-um-pouco-alem-do-basico/images/21-namespace.jpg" alt="Nova estrutura com namespace" width="958" height="596" />

Para utilizar todo o projeto entitulado como Tableless neste exemplo basta informá-lo onde o mesmo se faça necessário:

<pre class="lang-php">use Tableless;</pre>

&nbsp;

## Criando um pacote do composer

Pra finalizar criaremos um pacote do composer. Primeiramente você precisa ter uma conta no <a title="Ir ao Github" href="https://github.com/" target="_blank">github</a> ou <a title="Ir ao bitbucket" href="https://bitbucket.org/" target="_blank">bitbucket</a> (trabalharemos apenas com versionamento em git). Também será necessária uma conta no <a title="Ir ao Packegist" href="https://packagist.org/" target="_blank">Packagist</a>.

Tendo os requisitos atendidos agora deve ser criado um repositório no github, se você não sabe criar ou não utilizou o github ainda leia <a title="Criando repositório no Github" href="https://help.github.com/articles/create-a-repo" target="_blank">este tutorial</a>.

Feito isto é hora de clonar o repositório em uma pasta de sua preferência, utilize o comando **git clone git@github.com:username/repo-name.git** no meu caso é: git clone git@github.com:andrebian/exemplo-composer-tableless.git. Na imagem abaixo é possível ver o git realizando o clone e a estrutura inicial do projeto que contém além dos arquivos do git somente o arquivo README.md que foi criado juntamente com a criação do repositório no github.

<img class="aligncenter" src="https://raw.githubusercontent.com/andrebian/posts/master/tableless/composer-um-pouco-alem-do-basico/images/10-clonando-novo-projeto.jpg" alt="Clonando novo projeto" width="874" height="451" />

Agora temos de criar nosso arquivo _composer.json_ para que sejam adicionadas as informações de nosso novo pacote. Sua estrutura é a seguinte.

<pre class="lang-json">{
    "name": "andrebian/exemplo-composer-tableless",
    "description": "Este pacote foi criado apenas para complementar o post no Tableless",
    "authors": [ 
        {
            "name": "Andre Cardoso",
            "email": "andrecardosodev@gmail.com"
        }
    ],
    "require": {
         "php": "&gt;=5.3.17",
         "kevinlebrun/slug.php": "1.*"
    }
 }</pre>

A chave &#8220;name&#8221; deve possuir o vendor (seu username) e o slug do nome  do projeto.

Note que adicionei uma dependência ao meu projeto, com isso mesmo se o pacote slug.php não estiver setado no composer que engloba toda a aplicação será instalado porque eu informei que meu pacote precisa dele para funcionar corretamente.

Feito isto basta que as alterações realizadas sejam enviadas ao github e podemos prosseguir com a criação do pacote no packagist. Não vou explicar o funcionamento do git (commit, pull, push e outros) pois o foco deste post é o composer. Se você ainda não conhece o git sujiro a leitura de [Iniciando no git][1] que foi escrito pelo Diego Eis e está divido em duas partes que lhe mostram conceitos e utilização do mesmo. A imagem abaixo mostra o repositório no github já com a nova estrutura contendo o _composer.json_.

<img class="aligncenter" src="https://raw.githubusercontent.com/andrebian/posts/master/tableless/composer-um-pouco-alem-do-basico/images/11-projeto-no-github.jpg" alt="Configurações" width="1088" height="641" />

Agora que já temos nosso repositório no github basta criarmos nosso pacote no packagist. Acessando https://packagist.org/ e estando logado clique em &#8220;Submit package&#8221;.

<img class="aligncenter" src="https://raw.githubusercontent.com/andrebian/posts/master/tableless/composer-um-pouco-alem-do-basico/images/12-submit-package.jpg" alt="Enviar pacote" width="1068" height="457" />

Informe a URL em que o mesmo se encontra, neste caso https://github.com/andrebian/exemplo-composer-tableless e clique em Check

<img class="aligncenter" src="https://raw.githubusercontent.com/andrebian/posts/master/tableless/composer-um-pouco-alem-do-basico/images/13-package-url.jpg" alt="Check" width="954" height="551" />

Após a verificação e confirmação de que está tudo ok basta clicar em Submit

<img class="aligncenter" src="https://raw.githubusercontent.com/andrebian/posts/master/tableless/composer-um-pouco-alem-do-basico/images/14-confirm-submit.jpg" alt="Confirm" width="927" height="557" />

Na imagem seguinte você pode ver que o pacote foi criado com sucesso e já está disponível para ser adicionado como dependência em qualquer projeto que você desejar.

<img class="aligncenter" src="https://raw.githubusercontent.com/andrebian/posts/master/tableless/composer-um-pouco-alem-do-basico/images/15-package-created.jpg" alt="Created" width="1150" height="556" />

Note apenas que há uma chamada de atenção ali informando que o pacote não é atualizável automaticamente, vamos corrigir isto agora.

Acessando sua conta no github navegue pelos seus repositórios até encontrar o desejado e entre em suas configurações.

<img class="aligncenter" src="https://raw.githubusercontent.com/andrebian/posts/master/tableless/composer-um-pouco-alem-do-basico/images/16-settings.jpg" alt="Settings" width="1138" height="664" />

À esquerda há um menu com algumas opções, clique em **Webhooks & Services** e em seguida em configurar serviços.

<img class="aligncenter" src="https://raw.githubusercontent.com/andrebian/posts/master/tableless/composer-um-pouco-alem-do-basico/images/17-webhooks.jpg" alt="Service" width="1115" height="572" />

Role a tela até localizar o serviço **Packagist** e clique no mesmo. Uma nova tela será aberta solicitando os dados de sua conta. Forneça &#8220;user&#8221; e &#8220;token&#8221;, o &#8220;domain&#8221; é opcional, em seguida marque a opção &#8220;Active&#8221; e clique em Update Settings.

<img class="aligncenter" src="https://raw.githubusercontent.com/andrebian/posts/master/tableless/composer-um-pouco-alem-do-basico/images/18-packagist-token.jpg" alt="Token" width="781" height="599" />

Para obter o token, vá até sua conta no Packagist e clique em &#8220;Show API Token&#8221;.

<img class="aligncenter" src="https://raw.githubusercontent.com/andrebian/posts/master/tableless/composer-um-pouco-alem-do-basico/images/19-show-api-token.jpg" alt="Show API Token" width="922" height="591" />

Após confirmado o user e token nas configurações de webhooks do github, acesse novamente Webhooks & Services, vá novamente até Packagist e perceba que agora existe um botão de teste para confirmar que o serviço foi habilitado com sucesso, clique sobre o mesmo e certifique-se de que uma mensagem de sucesso foi retornarda.

<img class="aligncenter" src="https://raw.githubusercontent.com/andrebian/posts/master/tableless/composer-um-pouco-alem-do-basico/images/20-confirm-service.jpg" alt="Confirm service" width="1129" height="662" />

Quase lá, agora falta somente acessarmos nosso pacote no composer para certificar que a mensagem de que o mesmo não é atualizado automaticamente não aparece mais.

<img class="aligncenter" src="https://raw.githubusercontent.com/andrebian/posts/master/tableless/composer-um-pouco-alem-do-basico/images/20-success.jpg" alt="Success" width="920" height="547" />

Prontinho! Tudo funcionando perfeitamente. Agora sempre que você der um push no github o pacote do composer é atualizado automaticamente.

## Concluindo

Como você pode ver o composer é muito versátil, pode (e deve preferencialmente) ser utilizado em todo e qualquer projeto em PHP. Obviamente que existem configurações mais avançadas no entanto elas não vem ao caso neste momento por serem muito específicas de cada projeto/pacote. A ideia deste post era fornecer um pouco mais de informações sobre a utilização do composer que foi iniciada no post anterior [Composer para iniciantes][2] para maiores informações a documentação oficial sempre será a melhor fonte.

 [1]: http://tableless.com.br/iniciando-no-git-parte-1/ "Iniciando no git parte 1"
 [2]: http://tableless.com.br/composer-para-iniciantes/ "Composer para iniciantes"