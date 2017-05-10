---
title: Testando seu código jQuery com Jasmine – Parte 1
author: Davi Ferreira
type: post
date: 2011-09-12
excerpt: 'Com a evolução do desenvolvimento em JavaScript, testes automatizados começam a ganhar cada vez mais força. Neste artigo você conhece um pouco mais sobre a biblioteca Jasmine, focada em BDD &mdash;  Behavior Driven Development.'
url: /testando-seu-codigo-jquery-com-jasmine-parte-1/
tweetbackscheck:
  - 1356408208
shorturls:
  - 'a:3:{s:9:"permalink";s:31:"http://tableless.com.br/?p=4187";s:7:"tinyurl";s:26:"http://tinyurl.com/3mlgjzg";s:4:"isgd";s:19:"http://is.gd/1Aob5g";}'
twittercomments:
  - 'a:0:{}'
dsq_thread_id: 503040397
categories:
  - JavaScript
  - JQuery
tags:
  - bdd
  - jasmine
  - JavaScript
  - JQuery
  - tdd

---
Durante muito tempo testar/debugar JavaScript era uma tarefa árdua (infelizmente, em alguns navegadores, ainda é). Quem aí se lembra do tempo em que não existia Firebug, por exemplo? E o tamanho dos scripts? Um simples menu drop-drown possuía umas 1.500 linhas de código. Não existia jQuery ou qualquer outro tipo de framework. Tempos difíceis.

Hoje a tarefa do desenvolvedor é muito mais fácil. Para debug temos o já citado Firebug e o Developer Tools do Chrome, entre outros. Nos testes, além do <a href="http://pivotal.github.com/jasmine/" target="_blank">Jasmine</a>, outro framework bem legal é o [QUnit][1]. O Jasmine, por focar em BDD, possui uma sintaxe mais fluida. Quem programa em Ruby/Rails vai notar a enorme semelhança com a ferramenta RSpec.

Nos exemplos vou utilizar uma versão modificada do Jasmine, jasmine-jquery. Ela possui alguns métodos próprios para o framework além de funções para carregar fixtures (templates).

### Baby steps

Começar a trabalhar com uma cultura de testar sempre antes de desenvolver é bem difícil, principalmente para quem já está acostumado a programar antes e testar depois (manualmente). Comece devagar, sem medo. No início as coisas serão um pouco confusas, mas depois de adotar essa prática, você vai se perguntar como era possível programar sem testes.

O que testar e que testes escrever? Isso também vem com o tempo. Comece testando uma ou outra funcionalidade principal de um aplicativo já existente. Entenda como funciona a sua ferramenta de testes. Depois de um tempo comece a acreditar e confiar na sua intuição.

Procure sempre utilizar um conjunto variado de possibilidades, desde as mais óbvias até as mais inusitadas. Pense nos diferentes contextos, em tudo que interage com seu aplicativo: navegadores, sistemas operacionais, usuários, dados de entrada, scripts de terceiros etc.

Testes não evitam que seu software, uma vez finalizado, tenha bugs; não são a solução para todos os seus problemas de _deploy_, mas facilitam bastante essas etapas.

### Red &rarr; Green &rarr; Refactor

O padrão básico a ser seguido é o seguinte:

  1. Escreva o teste &mdash; naturalmente, ele vai falhar;
  2. Escreva, sem se preocupar muito com qualidade, o código mais simples, que faça o teste passar;
  3. Reescreva seu código, implementando melhorias de performance, escalabilidade e removendo duplicidades.

### Configurando o jasmine-jquery

Baixe a última versão do <a href="https://github.com/velesin/jasmine-jquery" target="_blank">jasmine-jquery</a> e vamos começar com nossos primeiros testes. A estrutura de pastas do nosso aplicativo deve ficar da seguinte maneira:

[cce lang=&#8221;xml&#8221;]- /
    
&#8211; /tests
      
&#8211; /lib
      
&#8211; /spec
        
&#8211; /fixtures
        
&#8211; /suites
          
&#8211; saudacao-spec.js
      
&#8211; /vendor
      
&#8211; SpecRunner.html
    
&#8211; tableless.js
  
[/cce] 

Note que criamos um diretório &#8220;tests&#8221; onde ficarão todos os arquivos dos nossos testes, incluindo a biblioteca Jasmine. O arquivo SpecRunner.html é o responsável por executar e exibir os resultados dos testes, basta abri-lo no navegador. Dentro do diretório “tests/spec” ficarão nossos conjuntos de testes (suites) e nossos templates HTML (fixtures).

No início do SpecRunner ficam as chamadas para os testes:

[cce lang=&#8221;javascript&#8221;]<script type=&#8221;text/javascript&#8221; src=&#8221;spec/suites/saudacao-spec.js&#8221;></script>[/cce]

Você também pode incluir aqui qualquer javascript personalizado necessário para os testes. No nosso caso vamos incluir o arquivo tableless.js, que fica na raiz do nosso aplicativo.

[cce lang=&#8221;javascript&#8221;]<script type=&#8221;text/javascript&#8221; src=&#8221;../tableless.js&#8221;></script>[/cce]

### Nosso primeiro teste

Vamos supor o seguinte: uma página deve exibir uma mensagem de boas-vindas para o usuário que varia de acordo com o horário. De 5 da manhã ao meio-dia, exibe &#8220;Bom dia!&#8221;; de meio-dia até 6 da tarde, exibe &#8220;Boa tarde!&#8221;; de 6 à meia-noite, exibe &#8220;Boa noite!&#8221;; e, por fim, de meia-noite até 6 da manhã exibe &#8220;Dormir é para os fracos!&#8221;. A mensagem fica sempre dentro de um elemento div com id &#8220;mensagem&#8221;. Os horários vão desde a hora inicial (incluída) até a hora final. A função pode receber como parâmetro uma hora no formato hh:mm ou, caso não receba nada, exibe a mensagem de acordo com a hora do usuário.

Esse é um bom começo para seus testes, tente escrever, em um parágrafo, o que deve ser executado e o que é esperado. Trabalhe sempre com um pedaço de papel por perto, para rascunhos.

Vejamos como ficaria o desenho inicial dos nossos testes. Crie o arquivo /tests/spec/suites/saudacao-spec.js e digite o seguinte código:

[cce lang=&#8221;javascript&#8221;]describe(&#8216;Exibição da mensagem de boas-vindas&#8217;, function(){
    
beforeEach(function(){
      
setFixtures(&#8216;<div id=&#8221;mensagem&#8221; />&#8217;);
      
this.mensagem = $(&#8216;#mensagem&#8217;);
    
});

afterEach(function(){
      
this.horas = [];
    
});

it(&#8220;Deve exibir &#8216;Bom-dia!&#8217; entre 5:00 e 11:59&#8221;, function(){
    
});

it(&#8220;Deve exibir &#8216;Boa-tarde!&#8217; entre 12:00 e 17:59&#8221;, function(){
    
});

it(&#8220;Deve exibir &#8216;Boa-noite!&#8217; entre 18:00 e 23:59&#8221;, function(){
    
});

it(&#8220;Deve exibir &#8216;Dormir é para os fracos!&#8217; de 00:00 a 04:59&#8221;, function(){
    
});

it(&#8220;Deve exibir, por padrão, a mensagem de acordo com a hora do cliente&#8221;, function(){
    
});
  
});[/cce]

Na raiz do aplicativo, crie um arquivo chamado &#8220;tableless.js&#8221;. Nele nós escreveremos nossa função para exibir a mensagem de acordo com a hora. Sua estrutura inicial é a seguinte:

[cce lang=&#8221;javascript&#8221;]function saudacao(hora_atual){
    
var hora;
  
}[/cce] 

Os conceitos básicos dos nossos testes giram em torno de três funções: **describe**, **it** e **expect**. Outras funções úteis, mas que nem sempre estarão presentes, são as funções **beforeEach** e **afterEach**. Também trabalhamos com uma função do jasmine-jquery, a **setFixtures** &mdash; falarei mais sobre ela na parte 2, por enquanto você só precisa saber que ela define templates/elementos no DOM.

  * **describe** &mdash; representa um conjunto de testes/comportamentos. Podem existir situações dentro de situações, por exemplo:
  
    [cce lang=&#8221;javascript&#8221;]describe(&#8216;Login&#8217;, function(){
    
    describe(&#8216;Sucesso&#8217;, function(){
    
    });</p> 
    describe(&#8216;Falha&#8217;, function(){
    
    });
  
    });[/cce] </li> 
    
      * **it** &mdash; define um teste, uma ação. Por exemplo, &#8220;It should validate the username&#8221;, ou, &#8220;Deve validar o nome do usuário&#8221;, seria uma boa situação para nosso teste de login.
      * **expect** &mdash; espera que alguma variável ou retorno de função seja igual a alguma coisa, ou verdadeiro, ou falso etc. Nos testes acima utilizamos apenas um tipo de validação, o matcher &#8220;toEqual&#8221;. Todo o teste deve ser chamado com a função expect, utilizando um dos matchers disponíveis (mais sobre eles na parte 2). Os principais são: toEqual, toContains, toBeTruthy e toBeFalsy.
      * **beforeEach** &mdash; executada antes de cada teste dentro de um conjunto, muito útil para configurar elementos.
      * **afterEach** &mdash; executada depois de cada teste dentro de um conjunto, ideal para reiniciar variáveis.</ul> 
    
    ### Escrevendo os testes
    
    Agora chegou a hora de preencher os nossos testes. Os testes que verificam a mensagem entre uma hora e outra seguirão um mesmo padrão. Dado um conjunto de horas válidas, a função saudacao deve retornar a mensagem correta.
    
    [cce lang=&#8221;javascript&#8221;]it(&#8220;Deve exibir &#8216;Bom-dia!&#8217; entre 5:00 e 11:59&#8221;, function(){
    
    this.horas = [&#8217;05:00&#8242;, &#8217;09:33&#8242;, &#8217;10:22&#8242;, &#8217;11:59&#8242;];
    
    for(i in this.horas){
      
    saudacao(this.horas[i]);
      
    expect(this.mensagem.text()).toEqual(&#8216;Bom-dia!&#8217;);
    
    }
  
    });[/cce]
    
    O teste que valida o retorno da função saudacao sem passagem de parâmetro busca a hora do cliente e exibe a mensagem de acordo com ela.
    
    [cce lang=&#8221;javascript&#8221;]it(&#8220;Deve exibir, por padrão, a mensagem de acordo com a hora do cliente&#8221;, function(){
    
    var data = new Date;
    
    data.setTime(data.getTime());
    
    var hora = data.getHours();
    
    saudacao();
    
    var texto = this.mensagem.text();
    
    if(hora < 5)
      
    expect(texto).toEqual('Dormir é para os fracos!');
    
    if(hora < 12)
      
    expect(texto).toEqual('Bom-dia!');
    
    else if(hora < 18)
      
    expect(texto).toEqual('Boa-tarde!');
    
    else
      
    expect(texto).toEqual('Boa-noite!');
  
    });[/cce]
    
    Nesse momento, abrindo o SpecRunner no navegador, todos os nossos testes estarão falhando. Lembra da nossa regra? Red (falhou), Green (passou) e Refactor.
    
    ### A função saudacao()
    
    Abaixo segue a minha implementação da função saudacao(). Não me preocupei muito com repetições e performance. Meu objetivo principal era fazer o teste passar.
    
    [cce lang=&#8221;javascript&#8221;]function saudacao(hora_atual){
    
    var hora;
    
    if(typeof hora_atual == &#8216;undefined&#8217;){
      
    var data = new Date;
      
    data.setTime(data.getTime());
      
    hora = data.getHours();
    
    }else{
      
    hora = hora_atual.split(&#8216;:&#8217;);
      
    hora = parseInt(hora[0].replace(/^0/, &#8221;));
    
    }
    
    if(hora < 5)
      
    $('#mensagem').text('Dormir é para os fracos!');
    
    else if(hora < 12)
      
    $('#mensagem').text('Bom-dia!');
    
    else if(hora < 18)
      
    $('#mensagem').text('Boa-tarde!');
    
    else
      
    $('#mensagem').text('Boa-noite!');
  
    }[/cce]
    
    Atualizando nossa SpecRunner veremos agora que todos os testes estão passando. Você pode (e deve) desenvolver aos poucos. Valide um teste de cada vez. Desenvolva com calma.
    
    ### Melhorando nosso código
    
    Como de praxe, vou deixar um dever de casa para vocês: a etapa de refactoring. O que podemos melhorar na nossa função saudacao()? E se o usuário passar uma hora atualmente inválida para nossa função, como &#8220;meio-dia&#8221;, &#8220;nove horas&#8221; etc. E se quisermos mudar o id do elemento #mensagem? E se quisermos exibir a saudação em mais de um elemento? Podemos melhorar algum nome de variável? Podemos reduzir o tamanho da nossa função? Nossa função está cumprindo seu objetivo? Tem algum código/texto repetido? E nossos testes? Estão cobrindo tudo? Prevendo todos os cenários?
    
    O que não falta é opção para um bom refactoring.
    
    Na segunda parte veremos a função spy, além de mais sobre fixtures, matchers personalizados e outros recursos avançados.
    
    ### Referências
    
      * [Código fonte dos exemplos deste artigo][2]
      * [SpecRunner do exemplo rodando no github][3]
      * <a href="http://pivotal.github.com/jasmine/" target="_blank">Jasmine BDD</a>
      * <a href="https://github.com/velesin/jasmine-jquery" target="_blank">jasmine-jquery</a>
      * <a href="http://pt.wikipedia.org/wiki/Behavior_Driven_Development" target="_blank">BDD segundo a Wikipedia</a>

 [1]: http://docs.jquery.com/Qunit
 [2]: https://github.com/tableless/exemplos/tree/gh-pages/jasmine-parte-1
 [3]: http://tableless.github.com/exemplos/jasmine-parte-1/tests/SpecRunner.html