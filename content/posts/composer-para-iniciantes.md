---
title: Composer para iniciantes
author: Andre Cardoso
type: post
date: 2014-03-18
url: /composer-para-iniciantes/
dsq_thread_id: 2457652649
categories:
  - PHP
  - Técnicas e Práticas
tags:
  - composer
  - gerenciamento de dependências
  - php

---
<a title="Ir para a homepage do Composer" href="https://getcomposer.org/" target="_blank">Composer</a> é uma ferramenta para gerenciamento de dependências para o PHP que vem ganhando espaço e se tornando cada vez mais indispensável. Com algumas poucas linhas de configurações você define todas as bibliotecas de terceiros ou mesmo suas que deseja/precisa utilizar em seu projeto, o composer encarrega-se de baixá-las e criar um autoloader deixando-as prontas para uso.

Para muitos o composer ainda é um mistério então o intuito deste post é mostrar ao usuário que ainda não conhece como baixar, configurar e utilizar o composer de forma básica.

&nbsp;

## Do que preciso?

Basicamente precisará do PHP em sua versão a partir da 5.3.2.

> Os exemplos criados neste post serão baseados em ambiente Linux, em sua maioria funcionará da mesma forma no Mac OS X mas para o Windows recomendo que leia a documentação oficial. O conceito é o mesmo nos três Sistemas Operacionais no entanto no Windows há algumas mínimas diferenças.
> 
> &nbsp;

## Como começo?

Primeiramente você precisa realizar o download do phar do composer. O <a title="Descubra o que é um arquivo Phar" href="https://php.net/manual/pt_BR/book.phar.php" target="_blank">phar</a> é um empacotamento de uma aplicação e é utilizado para fornecer bibliotecas e ferramentas nas quais o desenvolvedor não tem de se preocupar com sua estrutura. Em outras palavras, é pegar e usar.

Para que você obtenha o composer há duas maneiras distintas. Através da biblioteca <a title="Descubra o que é cURL" href="http://en.wikipedia.org/wiki/CURL" target="_blank">cURL</a> e através do próprio PHP. Basta selecionar uma das opções abaixo e executar em seu terminal.

Instalando via cURL:
  
curl -sS https://getcomposer.org/installer | php

Instalando via PHP:
  
php -r &#8220;readfile(&#8216;https://getcomposer.org/installer&#8217;);&#8221; | php

Existem outras maneiras de instalar, na verdade são configurações mais avançadas de instalação que não serão abordadas aqui por se tratar de ser um conteudo voltado à iniciantes.

&nbsp;

## Qual o próximo passo?

Antes de você sair querendo fazer as coisas acontecerem precisamos passar alguns conceitos básicos.

O composer facilita o gerenciamento de dependências em seus projetos, com isso houve a necessidade de uma padronização para a interoperabilidade entre os mais diversos frameworks PHP do mercado. Mas detalhe que o composer não limita-se à uso somente em frameworks, você pode tranquilamente utilizá-lo em seus projetos com PHP puro desde que siga as recomendações da <a title="Descubra o que é FIG" href="http://www.php-fig.org/" target="_blank">FIG</a> (Framework Interoperability Group).

&nbsp;

## O arquivo de configurações

Agora que você já tem uma noção do que é o composer está na hora de botar a mão na massa.

Primeiramente crie um arquivo chamado _composer.json_. Este arquivo possuirá as configurações de dependências de sua aplicação em formato <a title="Veja mais sobre a estrutura de um arquivo Json" href="http://json.org/json-pt.html" target="_blank">Json</a>.

Abaixo segue um esqueleto básico do _composer.json_ – o arquivo em que as dependências serão descritas, em seguida o mesmo será esclarescido.

<pre class="prettyprint lang-json">{
    "name": "Nome do projeto",
    "description": "Breve descrição do que a aplicação se propoe a fazer",
    "authors": [
        {
            "name": "Seu nome",
            "email": "seu-email@seu-dominio.com"
        }
    ],
    "require": {
        "php": "&gt;=5.2.8"
    }
}</pre>

O “name” é o nome de sua aplicação. Esta marcação é opcional mas recomendada.

O “description” é uma breve descrição do que sua aplicação se propõe a fazer. Também opcional.

Em “authors” aparecem os créditos de desenvolvedores que contribuiram com o projeto.

O “require” basicamente deixa claro quais são as dependências de sua aplicação. Neste caso se a versão do PHP for abaixo da 5.2.8 simplesmente uma mensagem de erro será lançada ao instalar as dependências lhe informando que não é possível prosseguir por nem todos os requisitos estarem satisfeitos.

Como você pode ver acima este é o esqueleto de uma aplicação muito básica, sem configurações avançadas e sem indicação de nenhuma biblioteca de terceiro.

&nbsp;

## Ok, mas e agora?

Agora que você já tem o esqueleto de seu composer configurado em sua aplicação falta incluir alguns pacotes. O composer utiliza como seu repositório o <a title="Pacotes do composer" href="https://packagist.org/" target="_blank">Packagist</a> onde qualquer desenvolvedor pode criar seus próprios pacotes e disponibilizá-los para a comunidade semelhante o <a title="Ir ao Github" href="https://github.com/" target="_blank">github</a>. O Packagist lhe fornece o total de instalações dos pacotes por dia, mês e o total. O mais legal é que estas estatísticas são fiéis, ou seja, se alguém remover um pacote do seu _composer.json_ o total de instalações é reduzido. Com esta informação restam contagens apenas aplicações que realmente estão utilizando determinado pacote.

&nbsp;

## Um pequeno exemplo.

Para fins didáticos mostrarei aqui a utilização de uma biblioteca para slug criada por <a title="Perfil de Kevin Le Brun no Github" href="https://github.com/kevinlebrun" target="_blank">Kevin Le Brun</a>, o <a title="Slug PHP no Github" href="https://github.com/kevinlebrun/slug.php" target="_blank">slug.php</a>. Na seção em que são definidos os requerimentos (require) no arquivo _composer.json _basta adicionar logo abaixo da linha que define que o necessita do PHP o nome do pacote desejado e a sua versão. Neste caso o pacote é &#8220;kevinlebrun/slug.php&#8221; e a versão é &#8220;1.*&#8221;. Com isso a nova estrutura do composer.json é:

<pre class="prettyprint lang-json">...
"require": {
        "php": "&gt;=5.2.8",
        "kevinlebrun/slug.php": "1.*"
}
...</pre>

&nbsp;

Muito bem, agora está tudo pronto para que você veja o composer em ação. Na pasta raíz de sua aplicação (que é a mesma que o _composer.json_ e o _composer.phar_ se encontram) rode o comando **php composer.phar install**. Este comando fará o composer ler as configurações setadas no arquivo json e instalar todas as bibliotecas/pacotes necessários para a sua aplicação e também estas mesmas bibliotecas que possuírem dependências terão as mesmas resolvidas. Pense no composer mais ou menos como o apt-get do Linux debian-like. Nele, ao instalar um pacote qualquer todas suas dependências são resolvidas automaticamente.

<img class="aligncenter size-large wp-image-41193" alt="Estruturdo composer e instalação" src="http://tableless.com.br/uploads/2014/02/estrutura-e-instalacao-660x292.png" width="660" height="292" srcset="uploads/2014/02/estrutura-e-instalacao-660x292.png 660w, uploads/2014/02/estrutura-e-instalacao-329x146.png 329w, uploads/2014/02/estrutura-e-instalacao-588x261.png 588w, uploads/2014/02/estrutura-e-instalacao-400x177.png 400w, uploads/2014/02/estrutura-e-instalacao.png 1275w" sizes="(max-width: 660px) 100vw, 660px" />

Perceba que na pasta em que encontra-se sua aplicação agora existem a pasta _vendor_, um arquivo _composer.phar_ (que já encontrava-se ali), um arquivo _composer.json_ (que já encontrava-se ali) e um arquivo _composer.lock_ – que é o arquivo gerado automaticamente após a instalação com sucesso.

<img class="aligncenter size-full wp-image-41194" alt="Estrutura de arquivos após a instalação via composer" src="http://tableless.com.br/uploads/2014/02/estrutura-arquivos.png" width="682" height="333" srcset="uploads/2014/02/estrutura-arquivos.png 682w, uploads/2014/02/estrutura-arquivos-329x160.png 329w, uploads/2014/02/estrutura-arquivos-588x287.png 588w, uploads/2014/02/estrutura-arquivos-634x310.png 634w, uploads/2014/02/estrutura-arquivos-400x195.png 400w" sizes="(max-width: 682px) 100vw, 682px" />

## O próximo passo (mais um)

Agora já temos tudo. O composer gerenciando as dependências, as dependências definidas em nosso arquivo composer.json, e uma pasta contendo todas as dependências necessárias juntamente com o autoloader do composer que encarrega-se de registar todos os namespaces dos arquivos baixados na pasta _vendor_. Com isso basta utilizarmos.

Crie um arquivo chamado index.php e inclua o autoloader do composer conforme o exemplo abaixo.

&nbsp;

<pre class="prettyprint lang-php">&lt;?php
header('Content-Type: text/html; charset=utf-8');

require 'vendor/autoload.php';</pre>

> Importante que esteja definido que o conteúdo será exibido utilizando a codificação UTF-8 pois problemas podem ocorrer no tratamento de caracteres especiais como acentuações.

Com isso em mãos, basta apenas utlizarmos nosso slug.php.

<pre class="prettyprint lang-php">$slugifier = new \Slug\Slugifier();

// Definindo tratamento de caracteres com acentuação
$slugifier-&gt;setTransliterate(true); 

$frase = 'Frase com acentuação para teste de criação de slug';

$slug = $slugifier-&gt;slugify($frase);

echo '&lt;b&gt;Frase natural: &lt;/b&gt;' . $frase . "&lt;br /&gt;&lt;br /&gt;";
echo '&lt;b&gt;Frase com aplicação de slug: &lt;/b&gt;' . $slug . "&lt;br /&gt;&lt;br /&gt;";</pre>

&nbsp;

Perfeito, agora basta exibir no seu browser ou mesmo via terminal.

<img class="aligncenter size-full wp-image-41196" alt="Slug rodando no terminal" src="http://tableless.com.br/uploads/2014/02/slug-terminal.png" width="816" height="424" srcset="uploads/2014/02/slug-terminal.png 816w, uploads/2014/02/slug-terminal-323x168.png 323w, uploads/2014/02/slug-terminal-588x305.png 588w, uploads/2014/02/slug-terminal-596x310.png 596w, uploads/2014/02/slug-terminal-400x207.png 400w" sizes="(max-width: 816px) 100vw, 816px" />

&nbsp;

Acessando nosso localhost através de um browser o resultado será este

<img class="aligncenter size-full wp-image-41195" alt="Slug rodando no navegador" src="http://tableless.com.br/uploads/2014/02/slug-browser.png" width="621" height="353" srcset="uploads/2014/02/slug-browser.png 621w, uploads/2014/02/slug-browser-295x168.png 295w, uploads/2014/02/slug-browser-545x310.png 545w, uploads/2014/02/slug-browser-400x227.png 400w" sizes="(max-width: 621px) 100vw, 621px" />

## Complementando

O comando **php composer.phar install** é utilizado somente uma vez em seu repositório. Para qualquer alteração do _composer.json_ que caracteriza-se como uma nova dependência ou remoção de uma existente deve ser utilizado o comando **php composer.phar update**.

O composer ainda possui um self-update em que baixa a sua última versão. Normalmente ao rodar qualquer comando você verá uma mensagem dizendo que a sua versão do composer precisa ser atualizada. Para isto basta o comando **php composer.phar self-update**.

&nbsp;

## Finalizando

O composer está se tornando a cada dia mais utilizado entre desenvolvedores e vale muito a pena se aprofundar no assunto.

O código-fonte deste exemplo está no github para eventuais consultas <a title="Código-fonte do projeto criado para este post" href="https://github.com/andrebian/posts/blob/master/tableless/tableless-composer-para-iniciantes/sources/sources.zip" target="_blank">neste link</a>.