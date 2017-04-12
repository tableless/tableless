---
title: Parse – Objetos na nuvem
author: Gabriel Ramos
type: post
date: 2015-07-07
excerpt: Parse, um banco de dados, na nuvem, orientado a objetos.
url: /parse-objetos-na-nuvem-2/
categories:
  - Artigos
  - Back-end
  - JavaScript
tags:
  - banco de dados
  - JavaScript
  - parse

---
Alguns dias atrás eu estava estudando um projeto que deveria apresentar, relacionado a WebApps. Decidi a plataforma da minha apresentação, mas acrescentar algo mais.

Eu tinha lido algumas coisas sobre um banco de dados que traria uma nova perspectiva aos desenvolvedores, facilitando seu acesso e fazendo suas conexões até por JavaScript (coisa que me intrigou bastante até começar a utilizá-lo), possibilitando leitura, gravação e consulta de dados. Foi aí que comecei a estudar sobre o Parse.

## Uma breve introdução ao Parse

Construirei um exemplo pequeno, utilizando JavaScript, gravando dados em uma Classe do Parse e retornando as IDs dos objetos que foram gravados. Mas antes, uma pequena explicação sobre os nomes que esta plataforma usa, para que a gente possa estar falando da mesma coisa, sem usar identificações diferentes:

  * Classe: dentro do Parse, é a mesma coisa que tabela. Ou seja, uma tabela de dados, dentro de suas aplicações e até mesmo no painel de sua conta será sempre tratada como &#8220;Class&#8221;;
  * Objetos: dentro e fora de seu projeto, cada linha da sua tabela será tratada como um objeto, possuindo várias informações divididas em colunas. Uma dessas informações é a ID que iremos utilizar, gerada automaticamente pelo Parse;
  * Campos são colunas.

Antes de tudo, vamos à nossa aplicação: você precisa criar uma conta no <a href="https://parse.com/" target="_blank">Parse</a>, para que possa entender exatamente o que estou falando, e seguir o passo a passo pelos seus dados de usuário (ao final, deixarei um exemplo contendo tudo que utilizei aqui).

Ao clicar para criar a sua conta, você preencherá seus dados e será informado sobre o nome do seu primeiro Aplicativo. Dê o nome que quiser; você poderá criar outros mais pra frente sem problemas. Após criar sua conta, aparecerá uma janela para você dar início às suas aplicações com o Parse. Como trataremos de um exemplo via JavaScript, clique em &#8220;Data&#8221;, depois clique em &#8220;Web&#8221; e depois em &#8220;New Project&#8221;.

Você será levado a uma página contendo uma explicação sobre o SDK do Parse, e também sua ID e Key de usuário, para que você possa fazer suas conexões com seus aplicativos do Parse. Um exemplo será disponibilizado para você baixar em um botão como **&#8220;Download the blank Javascript/HTML5 Project&#8221;**, onde você poderá baixar e dar uma olhada em um exemplo &#8220;em branco&#8221; de uma página acessando seu banco de dados. Baixem essa página, ela será necessária mais pra frente.

Sua ID e Key aparecerão na página em um trecho JavaScript, dessa forma (exemplo):

<pre class="lang-html">&lt;script&gt;
  Parse.initialize("valor-da-sua-id", "valor-da-sua-key");
&lt;/script&gt;
</pre>

Guarde este código, utilizaremos mais pra frente.

## No HTML

Construí uma página HTML básica, só para fazer o envio e o recebimento dos objetos à Classe do Parse, desta forma:

<pre class="lang-html">&lt;p&gt;
  Digite seu nome: &lt;input type="text" id="enviaNome"&gt;
  &lt;br&gt; 
  &lt;button onclick="armazena()"&gt;Armazenar nome no Parse&lt;/button&gt;  
  &lt;button onclick="retorna()"&gt;Retornar ID dos objetos do Parse&lt;/button&gt; 
&lt;/p&gt;
&lt;p id="tempNames"&gt;    
&lt;/p&gt;
</pre>

Deixei um parágrafo para um campo de texto, dois botões que chamam duas funções que já veremos mais pra frente (uma para gravar objetos na base de dados e outra para retornar), e um parágrafo vazio, com uma ID para receber os objetos que gravaremos.

## Mão na nuvem

Feito isso, começaremos a utilizar as infomações que o Parse nos dá. Eu separei meus scripts dessa forma, para facilitar a minha visualização (nada impede que você os coloque da forma que quiser, onde quiser, contanto que atinja o objetivo, utilize o padrão ao qual você está acostumado). Lembram daquela linha com o &#8220;Parse.initialize&#8221;? Então, eu a coloquei da seguinte forma, dentro da <head> do meu HTML:

<pre class="lang-html">&lt;script&gt;
  Parse.initialize("minha-id", "minha-key");
&lt;/script&gt;
</pre>

Como é um trecho de código que &#8220;inicializa&#8221; minha aplicação com o Parse, decidi por colocá-lo dentro do HTML mesmo. Precisaremos do script do Parse que é disponibilizado naquela página &#8220;em branco&#8221;. Você pode baixá-lo ou puxar pelo trecho que eles disponibilizam mesmo:

<pre class="lang-html">&lt;script src="http://www.parsecdn.com/js/parse-1.4.2.min.js"&gt;&lt;/script&gt;
</pre>

Beleza! Já temos a aplicação com o ID e com o scripts funcionando corretamente, agora vamos às funções.

Vamos lá, naquela página em branco vocês terão um exemplo de gravação de objetos dentro do Parse. Eu separei um script com duas funções para realizarmos isso:

<pre class="lang-html">&lt;script&gt;
  function armazena(){
    var nome = document.getElementById("enviaNome").value;
    var conectaParse = Parse.Object.extend("NomeClasse")
    obj = new conectaParse();
    obj.set("nome", nome);
    obj.save(null, {
      success: function(valor) {
        alert("Objeto criado com ID: " + obj.id);
      },
      error: function(valor, error) {
        alert("Falha ao criar objeto" + error.message);
      }
    });
  }

  function retorna(){
    document.getElementById("tempNames").innerHTML ="";
    var query = new Parse.Query("NomeClasse");
    query.greaterThan(
      "createdAt","2014-06-23T18:20:17.149Z" 
    );
    query.find({
      success: function(results) {
        for (var i = 0; i &lt; results.length; i++) {
          document.getElementById("tempNames").innerHTML += (i+1)+"º Objeto da Classe: "+ results[i].id +"";
        }
      },
      error: function(error) {
        alert('não foi');
      }
    });
  }
&lt;/script&gt;
</pre>

Notem que são as duas funções que são ativadas pelos botões que criamos; a função armazena e a função retorna, e elas fazem o seguinte:

Na função armazena uma variável **nome** é criada, pegando o valor do campo **enviaNome** e uma classe **conectaParse** é criada para realizar a conexão com a classe de nome **NomeParse** (vale lembrar também que o Parse não aceita Classes com vírgulas, pontos, acentos ou caracteres especiais). Um objeto **obj** foi criado seguindo as especificações da classe **conectaParse**, para realizar o armazenamento dos objetos num campo **nome**.

Se o dado for armazenado como sucesso, um alert aparecerá na tela com uma mensagem mostrando a ID do objeto dentro do banco de dados; caso contrário, uma mensagem de erro aparecerá. Vale lembrar que o tratamento das gravações dentro do Parse é um tanto quanto diferente. Se no seu código você indica uma Classe (lembrando que Classe = Tabela) ou um campo que não existe, a aplicação criará automaticamente essa Classe ou esse campo ao ser executada.

Na função retorna eu tratei primeiro aquele parágrafo que criamos, para que toda vez que o botão for clicado todo o conteúdo do parágrafo seja apagado antes de pegarmos os objetos do Parse. Uma variável com nome de **query** foi criada e igualada à query do Parse, recebendo o parâmetro **NomeClasse**, que é o nome da Classe na qual iremos fazer a consulta.

Feito isso, o trecho seguinte utiliza o método **greaterThan** para passar dois parâmetros dentro da pesquisa (ou query) que será executada. Um desses parâmetros é o **createdAt** e o outro é seu de data, ou seja, dentro dessa pesquisa, todos os objetos que estiverem na Classe do Parse que tenham sido criados na data que foi especificada, ou depois, devem ser retornados (notem que eu passei o ano de 2014, ou seja, como estamos criando essa pesquisa hoje, todos os objetos serão retornados).

É possível criar diversas pesquisas, com diversos métodos e diversos parâmetros. Esse mesmo que utilizei eu peguei dos próprios campos que são gerados na Classe do Parse, com a data de um dos objetos, aí só troquei o ano para que a função retornasse todos os meus objetos. Feito isso, o método **find** é chamado, podendo resultar em sucesso ou erro.
  
Caso retorne erro, um alert aparecerá com uma mensagem de &#8220;não foi&#8221;, e caso a pesquisa resulte em sucesso um laço de repetição será executado, inserindo no HTML do nosso parágrafo **tempNames** as IDs de cada objeto que veio como resultado do Parse.

Aliás, é muito interessante o tratamento das pesquisas dentro do Parse. Tentei criar arrays fora do método **find**, somente para armazenar os IDs dos objetos, mas não foi possível, todo o tratamento com os objetos que serão retornados com **results** da pesquisa devem ser trabalhados dentro da própria pesquisa.

Terminamos! Com isso temos uma página HTML que, por JavaScript, salva objetos em um banco de dados na nuvem e retorna todos os seus IDs.

Você pode encontrar no site do Parse toda a documentação com os códigos que eles possuem para todas as plataformas que eles atendem. Inclusive, dentro daquela página &#8220;em branco&#8221; que é disponibilizada para download quando criamos nosso projeto, você terá um link para as informações que estarão de acordo com a linguagem que você estiver utilizando.

## No Parse

Feito isso, você pode gerenciar seus aplicativos, suas classes e seus objetos dentro do seu painel no site do Parse. Acessando a aba &#8220;Core&#8221;, dentro do campo &#8220;Data&#8221; estarão as suas classes, e dentro das suas classes estarão os objetos com as suas informações.

Deixei um <a href="http://glr-tester.ueuo.com/parse/" target="_blank">exemplo pronto disponível</a>, rodando exatamente tudo isso que expliquei e até com alguns comentários dentro das funções JavaScript para dar uma lembrada do que cada uma faz.