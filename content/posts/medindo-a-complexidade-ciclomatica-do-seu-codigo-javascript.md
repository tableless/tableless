---
title: Medindo a complexidade do seu código JavaScript
author: Davi Ferreira
type: post
date: 2013-06-18
excerpt: Você sabe o que é complexidade ciclomática? E você sabia que já é possível medir a complexidade do seu código JavaScript?
url: /medindo-a-complexidade-ciclomatica-do-seu-codigo-javascript/
dsq_thread_id: 1407418323
categories:
  - JavaScript
tags:
  - 2013
  - codigo
  - complexidade javascript
  - JavaScript

---
Já mostramos aqui no Tableless [ferramentas para testes][1] e [ferramentas para garantir o padrão do seu código JavaScript][2], mas, enquanto esses utilitários asseguram uma consistência maior, eles nem sempre acabam com complexidades desnecessárias.

Neste artigo vamos falar sobre complexidade ciclomática e mostrar uma ferramenta para análise de códigos JavaScript, a biblioteca Plato.

## Complexidade Ciclomática

> A primeira regra de funções é que elas devem ser pequenas. A segunda regra de funções é que elas devem ser ainda menores.  
> &mdash; Uncle Bob

> Funções devem fazer uma coisa apenas. Fazê-la bem. Fazer somente ela.  
> &mdash; Uncle Bob

Explicando de forma bem direta, complexidade ciclomática é uma métrica do número de caminhos possíveis no seu código. Por exemplo, vejamos o código abaixo:

<pre class="lang-javascript">function authenticate() {
  if (user.isValid() === true) { 
    user.login(); 
  } else { 
    showMessage('Invalid credentials', 'error'); 
  } 
}</pre>

A função **authenticate** possui valor **2** de complexidade ciclomática. Na prática, isso quer dizer que precisaríamos escrever dois testes unitários para cobrir todos os possíveis caminhos. Ou seja, quanto mais caminhos, maior a complexidade ciclomática e, quanto maior a complexidade ciclomática, mais difícil será de manter/testar seu código.

<a href="http://www.mccabe.com/pdf/MeasuringSoftwareComplexityUAV.pdf" target="_blank">Estudos</a> recomendam **10** como o valor máximo que você deve permitir de complexidade ciclomática no seu método ou sua função. Este é um bom valor, mas tenha em mente que **10** já é uma complexidade alta e não deve, de forma alguma, ser a média de complexidade do seu projeto.

## Bad Fix

Outra métrica tirada a partir da complexidade ciclomática é a probabilidade de uma correção injetar novos bugs no seu código. O pessoal da Aivosto, uma empresa especializada em ferramentas para desenvolvedores, chegou a <a href="http://www.aivosto.com/project/help/pm-complexity.html" target="_blank">seguinte tabela</a>:

<table>
  <tr>
    <th>
      Complexidade Ciclomática
    </th>
    
    <th>
      Probabilidade de &#8220;bad fix&#8221;
    </th>
  </tr>
  
  <tr>
    <td>
      1-10
    </td>
    
    <td>
      5%
    </td>
  </tr>
  
  <tr>
    <td>
      20-30
    </td>
    
    <td>
      20%
    </td>
  </tr>
  
  <tr>
    <td>
      >50
    </td>
    
    <td>
      40%
    </td>
  </tr>
  
  <tr>
    <td>
      próximo de 100
    </td>
    
    <td>
      60%
    </td>
  </tr>
</table>

Segundo a pesquisa da Aivosto, uma correção aplicada em um método com complexidade ciclomática 25 tem 20% de chances de introduzir um novo bug na sua aplicação. Tente lembrar quantas vezes isso já aconteceu com você? E tente lembrar também do tamanho do método ou função que você estava &#8220;corrigindo&#8221;. Por isso é muito importante tentar medir tudo a respeito do seu código.

## Plato

<p style="text-align: center">
  <img src="http://tableless.com.br/uploads/2013/06/complexityplato.jpg" alt="complexityplato" width="372" height="396" class="alignnone size-full wp-image-37790" style="border: 1px solid #ccc" srcset="uploads/2013/06/complexityplato.jpg 372w, uploads/2013/06/complexityplato-157x168.jpg 157w, uploads/2013/06/complexityplato-291x310.jpg 291w" sizes="(max-width: 372px) 100vw, 372px" />
</p>

Desenvolvida por Jarrod Overson, a ferramenta <a href="https://github.com/jsoverson/plato" target="_blank">Plato</a> aplica na prática todas as teorias de medição de complexidade ciclomática, exibindo na forma de gráficos dados como taxa de mantenabilidade, bugs estimados e erros de lint.

A instalação é feita através do npm, gerenciador de pacotes do nodejs:

<pre>npm install -g plato</pre>

A forma mais básica de uso é a seguinte:

<pre>plato -d report src</pre>

Onde **-d report** é a flag para indicar o diretório **report** como saída do seu relatório e **src** é o diretório dos arquivos JavaScript a serem analisados. 

Outras opções importantes são as flag **-r** para ler o diretório recursivamente e **-x <regex>** para excluir arquivos baseados em uma regex.

Os relatórios do Plato armazenam históricos e é bem interessante ver os números subindo e descendo durante o desenvolvimento do seu projeto. Uma prática legal é guardar e exibir o relatório em algum lugar disponível para todo o seu time.

## Exemplos de relatórios

Abaixo temos alguns exemplos de relatórios disponibilizados no repositório do projeto, gerados a partir de bibliotecas e utilitários populares:

  * <a href="http://jsoverson.github.com/plato/examples/jquery/" target="_blank">jquery</a>
  * <a href="http://jsoverson.github.com/plato/examples/grunt/" target="_blank">grunt</a>
  * <a href="http://jsoverson.github.com/plato/examples/marionette/" target="_blank">marionettejs</a>

## Bugs estimados

<p style="text-align: center">
  <img src="http://tableless.com.br/uploads/2013/06/bugs.jpg" alt="bugs" width="404" height="246" class="alignnone size-full wp-image-37786" style="border: 1px solid #ccc" srcset="uploads/2013/06/bugs.jpg 404w, uploads/2013/06/bugs-275x168.jpg 275w" sizes="(max-width: 404px) 100vw, 404px" />
</p>

Um gráfico que chama a atenção nos relatórios do Plato é o de bugs estimados. Afinal de contas, entregar um produto sem bugs é (ou deveria ser) o objetivo final de qualquer desenvolvedor.

Maurice Howard Halstead criou um <a href="http://www.amazon.com/Elements-Software-Science-Operating-programming/dp/0444002057" target="_blank">conjunto de fórmulas</a> para medir coisas como volume, esforço, dificuldade e bugs estimados em um código. As fórmulas são baseadas nos números únicos e totais de operadores e operandos.

Não vou entrar muito em detalhes sobre os valores e as fórmulas, mas é bem interessante ler sobre esse assunto (não precisa ser o livro, a Wikipedia mesmo fornece uma <a href="http://en.wikipedia.org/wiki/Halstead_complexity_measures" target="_blank">página</a> bem completa sobre as fórmulas).

## Integração com Grunt

Overson também desenvolveu um <a href="https://github.com/jsoverson/grunt-plato" target="_blank">módulo</a> que disponibiliza uma task Grunt para relatórios Plato.

A instalação segue o padrão de pacotes Grunt:

<pre>npm install grunt-plato --save-dev</pre>

Uma vez instalado o pacote, basta carregar a task no seu **Gruntfile.js** e rodar a task com o comando **grunt plato**:

<pre>grunt.initConfig({
  plato: {
    your_task: {
      files: {
        'report/output/directory': ['src/**/*.js', 'test/**/*.js'],
      }
    },
  },
});
grunt.loadNpmTasks('grunt-plato');</pre>

## Métricas, métricas e mais métricas

Medir o código do seu projeto ajuda você e seu time a entender e prevenir problemas. Com a ajuda de métricas você vai conseguir manter um código fácil de ler e entender. Além de métricas dos níveis de complexidade também é importante possuir um relatório visível de cobertura de testes e uma documentação simples e direta do seu projeto.

Apesar do nome pomposo e de muita teoria, não é pra ninguém ficar assustado. Pode parecer um conceito avançado, mas na verdade é uma coisa muito básica: o que você estará fazendo é medir se é fácil (ou difícil) manter o seu código.

E lembrem-se: nunca refatore um código sem que ele possua uma cobertura de testes satisfatória!

 [1]: http://tableless.com.br/testando-seu-codigo-jquery-com-jasmine-parte-1/
 [2]: http://tableless.com.br/qualidade-codigo-javascript/