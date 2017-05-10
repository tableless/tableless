---
title: Introdução de como executar testes unitários em diferentes tipos de navegadores
author: Igor Ribeiro Lima
type: post
date: 2013-12-04
excerpt: Entenda um pouco mais sobre testes unitários e como executá-los em diversas plataformas.
url: /introducao-de-como-executar-testes-unitarios-em-diferentes-tipos-de-navegadores/
dsq_thread_id: 2023558245
categories:
  - Browsers
  - JavaScript
tags:
  - bdd
  - JavaScript
  - SauceLabs
  - tdd
  - Testem
  - testes unitários

---
[SauceLabs][1] é uma plataforma de teste que possibilita realizar testes automáticos ou manuais em aplicações móveis e web (incluindo navegadores como Internet Explorer, Opera, Safari, Android, iPhone, Chrome etc). Essa plataforma permite executar os testes em diversas linguagem de programação, porém, em nosso exemplo, iremos utilizar o NodeJS (JavaScript).

O NodeJS e o Gerenciador de Pacotes do Node (traduzido do inglês Node Package Manager &#8211; NPM) podem ser baixados no [site oficial][2]. Esse gerenciador de pacotes permite a interação com um repositório online via linha de comando, facilitando a instalação de várias ferramentas.

Nesse exemplo, será utilizado uma ferramenta chamada [Test&#8217;em][3], que é gerenciada e instalada pelo NPM. Essa ferramenta permite rodar os testes unitários de JavaScript localmente em diferentes plataformas, tornando a execução mais fácil e divertida. Test&#8217;em suporta vários frameworks de teste, tais como: Jasmine, QUnit e Mocha. Para instalar, basta digitar no terminal:

<pre class="lang-ssh">npm install testem -g</pre>

No exemplo, será utilizado o framework Jasmine. Mesmo código do [tutorial oficial do SauceLabs][4]. As especificações do código estão descritas no arquivo PastaSpec.js e a implementação no arquivo Pasta.js. Ambos arquivos encontra-se abaixo:

**PastaSpec.js**

<pre class="lang-js">describe("Pasta", function() { 
  it("should make spaghetti bolognese", function() { 
    var pasta = new Pasta(); 
    pasta.add("tomatoes"); 
    pasta.add("garlic"); 
    pasta.add("olive"); 
    pasta.add("herbs"); 
    pasta.add("meat"); 
    expect(pasta.getType()).toEqual("bolognese"); 
    expect(pasta.isTasty()).toEqual(true); 
  }); 

  it("should make pasta with no sauce", function() { 
    var pasta = new Pasta(); 
    pasta.add("meat"); 
    expect(pasta.getType()).toEqual(undefined); 
    // pasta with no sauce? yeah that's not too tasty 
    expect(pasta.isTasty()).toEqual(false); 
  }); 
});</pre>

**Pasta.js**

<pre class="lang-js">function Pasta() { 
  // recipes for good pasta sauces 
  this.sauces = { 
    'bolognese': ["tomatoes", "garlic", "olive", "herbs", "meat"] 
  }; 
  this.sauceIngredients = []; 
} 

Pasta.prototype.add = function (ingredient) { 
  this.sauceIngredients.push(ingredient); 
}; 

Pasta.prototype.getType = function () { 
  for (var posssibleSauce in this.sauces) { 
    var ingredientsValid = true; 
    // checking if arrays are equal 
    if (!(this.sauceIngredients.sort() &gt; this.sauces[posssibleSauce].sort() || 
          this.sauceIngredients.sort() &lt; this.sauces[posssibleSauce].sort())) { 
      return posssibleSauce; 
    } 
  } 
  return undefined; 
}; 

Pasta.prototype.isTasty = function () { 
  if (this.getType() !== undefined) { return true; } 
  return false; 
};</pre>

Uma vez criado o arquivo de especificação &#8216;PastaSpec.js&#8217; e a implementação &#8216;Pasta.js&#8217;, é preciso criar um arquivo de configuração &#8216;_testem.json_&#8216;. Necessário apenas informar o framework utilizado e os arquivos JavaScript. Conforme escrito abaixo:

**testem.json**

<pre class="lang-js">{ 
  "framework": "jasmine", 
  "src_files": [ 
    "Pasta.js", 
    "PastaSpec.js" 
  ] 
}</pre>

O Test&#8217;em usa como padrão a porta 7357. O parâmetro &#8216;&#8211;port&#8217; serve para especificar uma outra. Nesse caso, vamos utilizar a 8080, digitando:

<pre class="lang-ssh">testem --port=8080</pre>

Após a execução do comando, o resultado dos testes pode ser visto pela url **http://localhost:8080/**. Caso a url seja aberta no Chrome, os testes serão executados no navegador Chrome. Caso aberta no Safari, será executado no Safari. Como ilustra a figura seguinte.

![testing Jasmine code on Test'em][5]

Para testar o código em diversos navegadores ou diversos sistemas operacionais, não é necessário ter máquinas virtuais nem mesmo outros dispositivos, como celulares ou tablet. O Sauce Labs prover o conector [Sauce Connect][6]. Com ele é possível criar uma conexão entre a nossa máquina e os servidores do SauceLabs, assim é possível rodar os testes dentro do firewall do Sauce Labs Cloud. Cloud que disponibiliza mais de [200 plataformas][7], que inclui dispositivos móveis, diversos SO e navegadores. Uma vez baixado o Sauce Connect, essa conexão é feita pelo comando:

<pre class="lang-ssh">java -jar Sauce-Connect.jar --tunnel-identifier "tabless" $SAUCE_USERNAME $SAUCE_ACCESS_KEY</pre>

Vale ressaltar que _$SAUCE_USERNAME_ e _$SAUCE\_ACCESS\_KEY_ são variáveis de ambientes. Método recomendado para evitar a divulgação de dados privados. Para obter dados de acesso, acesse a [página de cadastro][8]. Após a criação da conta, uma chave de acesso já é fornecida, conforme é ilustrado na figura abaixo.

![página inicial da conta SauceLabs][9]

Na página inicial, o botão **New Interactive Session** permite a criação de uma instância de navegador. Uma popup (ilustrada na imagem abaixo) será exibida ao clicar no botão, com várias opções de sistema operacional e de navegador.

![popup para a criação de uma nova instância de navegador do SauceLabs][10]

Ao instanciar o navegador, é possível visualizar o resultado dos testes no terminal (ilustração na imagem abaixo). Os testes sempre serão executados novamente caso haja alguma alteração tanto no código quanto nas especificações, possibilitando assim a prática de TDD ou BDD, utilizando qualquer tipo de navegador.

![instancia de um iPad do SauceLabs][11]

Esse exemplo contempla apenas a execução de testes de forma manual. Essas ferramentas que foram utilizadas também oferecem suporte para a automatização de testes, mas isso ficará para um próximo capítulo. Para quem se interessar, todo código está disponível em um [gist][12]. Muito obrigado.

 [1]: https://saucelabs.com/ "SauceLabs"
 [2]: http://nodejs.org/download/ "site oficial NodeJS"
 [3]: https://github.com/airportyh/testem "documentação do Test'em"
 [4]: https://saucelabs.com/docs/javascript-unit-testing-tutorial "tutorial oficial do SauceLabs"
 [5]: https://camo.githubusercontent.com/4c25f04b60b6f6aaff1b50a0069ca0f5487860be/687474703a2f2f7332312e706f7374696d672e6f72672f6e72393273783469762f6a61736d696e655f74657374735f6f6e5f74657374656d2e706e67
 [6]: http://saucelabs.com/downloads/Sauce-Connect-latest.zip "Sauce Connect"
 [7]: https://saucelabs.com/docs/platforms "plataformas SauceLabs"
 [8]: https://saucelabs.com/signup "página de cadastro do SauceLabs"
 [9]: https://camo.githubusercontent.com/b29a04372bbe9224392df879736467128316054e/687474703a2f2f7332312e706f7374696d672e6f72672f63673666346a786e722f73617563656c6162735f6163636f756e745f706167652e706e67
 [10]: https://camo.githubusercontent.com/7de3c788dc9a56a153bada645514034a442ae6d4/687474703a2f2f7332312e706f7374696d672e6f72672f736f693230616834372f6e65775f696e7465726163746976655f73657373696f6e5f706f7075702e706e67
 [11]: https://camo.githubusercontent.com/404afe58a076603719c0448fbc1a41ca92c85e0c/687474703a2f2f7332312e706f7374696d672e6f72672f74687a39366e6369762f697061645f73617563656c6162735f73657373696f6e2e706e67
 [12]: https://gist.github.com/igorlima/7649954 "gist do exemplo"