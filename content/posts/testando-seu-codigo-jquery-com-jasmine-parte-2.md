---
title: Testando seu código jQuery com Jasmine – Parte 2
author: Davi Ferreira
type: post
date: 2011-10-04
excerpt: Nesta segunda parte você conhece um pouco mais sobre o framework de testes Jasmine. Aprenda a criar matchers personalizados e testar AJAX e métodos em objetos.
url: /testando-seu-codigo-jquery-com-jasmine-parte-2/
tweetbackscheck:
  - 1356393493
shorturls:
  - 'a:3:{s:9:"permalink";s:31:"http://tableless.com.br/?p=4189";s:7:"tinyurl";s:26:"http://tinyurl.com/6kyqegk";s:4:"isgd";s:19:"http://is.gd/3Ae4hM";}'
twittercomments:
  - 'a:0:{}'
dsq_thread_id: 503040401
categories:
  - JavaScript
  - JQuery
tags:
  - bdd
  - jasmine
  - tdd

---
Jasmine é um framework para testes focado em BDD (_Behavior Driven Development_). Na [primeira parte][1] deste artigo aprendemos seus métodos básicos e realizamos alguns testes simples. Agora chegou a hora de ir um pouco além e conhecer técnicas mais avançadas.

Vale lembrar que, em nossos exemplos, utilizamos uma versão modificada da biblioteca, adaptada para jQuery: [jasmine-jquery][2].

Utilizaremos os dados de um outro artigo, [Conteúdo sob demanda com jQuery][3]. O objetivo é testar as solicitações AJAX do carregamento da lista de tweets do Tableless.

### Fixtures

Antes dos testes propriamente ditos vamos conhecer uma forma prática de carregar nosso conteúdo HTM. Fixtures são arquivos carregados através do método **loadFixtures**. Esta funcionalidade, aliás, está disponível apenas no jasmine-jquery.

Vamos salvar o código HTML abaixo no arquivo **tweets.html**, dentro do diretório de fixtures.

[cce lang=&#8221;xml&#8221;]
  
<div id=&#8221;container&#8221;>
    
<h1>Tweets do Tableless</h1>
    
<ul id=&#8221;lista-tweets&#8221;></ul>
    
<p><a href=&#8221;#&#8221; id=&#8221;carrega-tweets&#8221; data-pagina=&#8221;1&#8243;>Mais!</a></p>
  
</div>
  
[/cce]

Por padrão, o jasmine-jquery procura as fixtures no diretório **spec/javascripts/fixtures**. Como na primeira parte do artigo indicamos uma estrutura diferente, utilizando o diretório **spec/fixtures**, precisamos atualizar a propriedade fixturesPath nas configurações do Jasmine.

[cce lang=&#8221;javascript&#8221;]
  
jasmine.getFixtures().fixturesPath = &#8216;spec/fixtures/&#8217;; 

describe(&#8216;Exibição dos últimos tweets do Tableless&#8217;, function(){
    
beforeEach(function(){
      
loadFixtures(&#8216;tweets.html&#8217;);
    
});

it(&#8216;Deve carregar na primeira página&#8217;, function(){
      
expect($(&#8216;#carrega-tweets&#8217;).data(&#8216;pagina&#8217;)).toEqual(1);
    
});
  
});
  
[/cce]

Outra forma de utilizarmos fixtures é carregando diretamente no código, sem a necessidade de um arquivo HTML. Esse caso é mais indicado para templates mais simples, com poucos elementos.

[cce lang=&#8221;javascript&#8221;]
  
setFixtures(&#8216;<ul id=&#8221;lista-tweets&#8221; />&#8217;);
  
[/cce]

### Testando código assíncrono

Testar código AJAX pode ser um pouco mais complicado. No nosso exemplo, como acessamos uma URL externa à nossa aplicação, o tempo de resposta vai depender de vários fatores, como velocidade da conexão, estabilidade do Twitter etc.

Os métodos **runs** e **waits** são úteis para tentar simular esse tempo de carregamento. O **runs** executa os testes e funções um escopo próprio e, além disso, são executados em sequência (quando um termina, o outro começa). Já o método **waits** funciona como uma espécie de pausa/sleep e recebe como parâmetro o tempo em milissegundos.

[cce lang=&#8221;javascript&#8221;]
  
it(&#8216;Deve carregar os últimos 20 tweets&#8217;, function(){
    
runs(function(){
      
Tableless.retorna_tweets(1);
    
});
    
waits(1500);
    
runs(function(){
      
expect($(&#8216;#lista-tweets li&#8217;).length).toEqual(20);
    
});
  
});
  
[/cce]

### Espionando métodos

Às vezes precisamos testar se um método de um objeto é chamado (e com que parâmetros) &mdash; e não testar apenas seu resultado. O Jasmine oferece a função **spyOn** para capturar e validar essas chamadas. O **spyOn** recebe dois parâmetros: o objeto e o nome do método.

[cce lang=&#8221;javascript&#8221;]
  
it(&#8216;Deve executar função para retornar tweets&#8217;, function(){
    
spyOn(Tableless, &#8216;retorna_tweets&#8217;);
    
Tableless.retorna_tweets(1);
    
expect(Tableless.retorna_tweets).toHaveBeenCalledWith(1);
  
});
  
[/cce]

Acima testamos se o método foi chamado com o parâmetro 1 (página). Poderíamos ter utilizado também **toHaveBeenCalled**, testando apenas a chamada. As funções de spy podem ainda ser combinadas com o not, por exemplo:

[cce lang=&#8221;javascript&#8221;]
  
expect(Tableless.retorna_tweets).not.toHaveBeenCalled();
  
[/cce]

### Matchers personalizados

Outra funcionalidade poderosa do Jasmine é a possibilidade de criação de matchers personalizados. Os matchers são asserts para seus tests. No exemplo abaixo, criamos o matcher **toBeATweet** para validar se um elemento possui a classe &#8220;tweet&#8221;.

[cce lang=&#8221;javascript&#8221;]
  
beforeEach(function(){
    
this.addMatchers({
      
toBeATweet: function(){
                    
return this.actual.hasClass(&#8216;tweet&#8217;);
                  
}
    
});
  
});
  
[/cce]

[cce lang=&#8221;javascript&#8221;]
  
expect($(&#8216;#lista-tweets li:first&#8217;)).toBeATweet();
  
[/cce]

O método addMatchers deve ser executado dentro do beforeEach, utilizando o Jasmine como contexto. Notem que ele recebe um objeto que pode conter um ou mais matchers personalizados. No código, **this.actual** representa a variável, elemento, ou objeto que estará sendo passado ao **expect**.

### Outros projetos utilizando Jasmine

Nesses dois artigos vocês conheceram o jasmine-jquery, mas existem diversos outros projetos baseados no framework Jasmine, incluindo adaptações para NodeJS, Rails e iPhone e snippets para Vim e TextMate. A lista completa você confere no [wiki do projeto no Github][4].

### Referências

  * [Código fonte dos exemplos deste artigo][5]
  * [SpecRunner dos exemplos rodando no browser][6]
  * [Testing jQuery plugins with Jasmine][7]
  * [HTML fixtures in Jasmine (using jasmine-jquery)][8]

 [1]: http://tableless.com.br/testando-seu-codigo-jquery-com-jasmine-parte-1/
 [2]: https://github.com/velesin/jasmine-jquery
 [3]: http://tableless.com.br/conteudo-sob-demanda-com-jquery/
 [4]: https://github.com/pivotal/jasmine/wiki/Related-projects
 [5]: https://github.com/tableless/exemplos/tree/gh-pages/jasmine-parte-2
 [6]: http://tableless.github.com/exemplos/jasmine-parte-2/tests/SpecRunner.html
 [7]: http://f.souza.cc/2011/05/testing-jquery-plugins-with-jasmine/
 [8]: http://testdrivenwebsites.com/2010/07/29/html-fixtures-in-jasmine-using-jasmine-jquery/