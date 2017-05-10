---
title: Padrões de Código de CSS do WordPress
author: Wanderson Macêdo
type: post
date: 2014-07-18
excerpt: Os padrões de código WordPress são para tornar mais legível, significativo, consistente e bonito o seu código PHP, HTML, CSS e JAVASCRIPT. E nesse artigo veremos alguns pontos sobre o CSS WordPress.
url: /padroes-de-codigo-de-css-wordpress/
dsq_thread_id: 2853665341
categories:
  - CSS
  - Técnicas e Práticas
  - Wordpress
tags:
  - CSS
  - Wordpress

---
Todo mundo no comecinho da carreira já desenvolveu aquele código esquisito, que dias depois não conseguiu lembrar bem o que era, se perdia nos seletores, usava padrões de nomenclatura vistos na programação tipo o CamelCase, ou algo semelhante. Ter um padrão de escrita de código é essencial para que você e também outros na equipe entendam de maneira efetiva cada ponto do sistema. Para tanto, as famosas guide lines fazem com que gostos pessoais sejam ignorados e padrões de escrita se firmem. 

Manter um padrão de escrita de código em um projeto Open Source é muito importante, talvez até mais importante do que para uma equipe presencial, que trabalha todos os dias juntos numa mesma empresa. Em um produto Open Source você vai receber contribuições de pessoas do mundo inteiro, de forma dessincronizada, com gostos diferentes. É muito importante nesse momento manter uma uniformidade no produto todo.

Confesso que eu não costumava seguir um determinado padrões em meus projetos. Mas ao conhecer os padrões de código do WordPress, fui me &#8220;consertando&#8221;. Acredito que talvez você também já tenha passado por isso em algum momento da carreira, então, pensando nisso, vamos ver aqui o fundamental sobre o CSS WordPress. Vai servir para você conhecer mais sobre os padrões de código do time do WordPress. Talvez você até adote alguns dos padrões deles em seus projetos.

###  REGRA 1 &#8211; Quanto a estrutura:

Não é difícil encontrar por aí códigos CSS nessa estrutura:

<pre class="lang-css">#seletor1, #seletor2, #terceiroSeletor{
propriedad: valor;
propriedade: valor;
}</pre>

E segundo a documentação do WordPress, esse tipo de estrutura é considerado incorreto e abaixo vemos três pontos pra corrigir e se dar bem com os padrões.

  * Seletores e pares de propriedade-valor, devem ser postos cada um em uma linha.
  * Usar TAB para identar o código e não varios espaços.
  * Usar duas linhas em branco entre seções de código, e uma linha em branco a cada bloco de código dentro de uma seção.

Corrigindo o exemplo acima ficaria assim:

<pre class="lang-css">#seletor1,
#seletor2,
#terceiroSeletor{
propriedade: valor;
propriedade: valor;
}</pre>

### REGRA 2 &#8211; Quando aos seletores:

Vamos direto aos pontos da regra, e observar sempre o exemplo anterior para demonstrar a correção necessária.

  * Não usar padrão CamelCase e underlines na nomenclatura dos seletores CSS. nomear todos em minúsculo e caso mais de uma palavra componha o nome do seletor, separar essas palavras por hífen.
  * Utilizar nomes descritivos a função do seletor, fáceis de ler e saber de cara o que é.
  * Utilizar aspas duplas nos valores dos atributos de seletores.
  * Evitar super qualificação dos elementos, exemplo: div#comments.

Corrigindo o exemplo anterior…

<pre class="lang-css">#seletor-1,
#seletor-2,
#terceiro-seletor{
propriedade: valor;
propriedade: valor;
}</pre>

### REGRA 3 &#8211; Quanto as propriedades.

  * As propriedades devem ser seguidas de dois pontos e espaço.
  * Todas as propriedades e valores devem ser escritas em minusculo (exceções  para fontes e outras especificidades).
  * Usar cores em hexadecimal, e rgba quando precisar de opacidade. Evitar RGB. Usar modo recurso das propriedades (e valores) quando possíve: ex: margin: 0; em vez de: margin-bottom:0; margin-top: 0;

**OBS: Um ponto interessante, é que a documentação oferece até um ordenamento referente as propriedades. A lista a seguir mostra a indicação da documentação.**

  * Display (Regras como, width e height se encaixam aqui).
  * Posicionamento (Regras como top e position se encaixam aqui).
  * Box-model (Já deve saber, mas revisando, padding e border se encaixam aqui).
  * Cores e Tipografia (Nem precisa explicação).
  * Outros (Qualquer propriedade que não se encaixem nas categorias acima)

Há também uma outra indicação que é usada pelo pessoal da Automattic e desenvolvedores de temas do WordPress.com é ordenar as propriedades em ordem alfabética.

### REGRA 4 &#8211; Quanto as valores.

  * Espaço antes, ponto e vírgula depois. Sempre! 🙂
  * Não por espaços nos parênteses. (escrever colado nos parênteses).
  * Usar aspas duplas, ao invés de aspas simples.
  * Valores que sejam 0, não precisam de unidades como px, %, em.
  * Em comandos com múltiplos valores, separe estes com vírgula e espaço, ou insira os valores em diversas linhas.

Existem outros pontos que não falei aqui, mas você caso se interesse pode consulta-los na própria documentação do WordPress, [aqui][1].

Bom gente, é assim que chego ao fim desse novo artigo que escrevo pra vocês, espero que gostem e qualquer dúvida, comente!

###### Leia mais:

  * [http://make.wordpress.org/core/handbook/coding-standards/css/][2]
  * [http://make.wordpress.org/core/handbook/coding-standards/][3]

 [1]: http://make.wordpress.org/core/handbook/coding-standards/css/ "Coding Standards CSS"
 [2]: http://make.wordpress.org/core/handbook/coding-standards/css/ "Conding Standards CSS"
 [3]: http://make.wordpress.org/core/handbook/coding-standards/ "Conding Standards"