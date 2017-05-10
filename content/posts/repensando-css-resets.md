---
title: Repensando CSS Resets
author: Dani Guerrato
type: post
date: 2013-02-04
excerpt: Como melhorar seu CSS Reset.
url: /repensando-css-resets/
dsq_thread_id: 1064394526
categories:
  - CSS
  - HTML
  - O Básico
  - Técnicas e Práticas
tags:
  - 2013
  - CSS
  - css reset
  - CSS3

---
Cada desenvolvedor possui um fluxo de trabalho diferente, mas uma prática mais do que comum é utilização de algum tipo de reset ou normatização para o CSS. Você provavelmente já sabe para que serve este tipo de arquivo. Como cada browser tem suas configurações padrões iniciais, esta boa prática garante a consistência do código e minimiza as diferenças visuais de um layout em diferentes navegadores. O objetivo é sempre criar um resultado mais homogêneo. Basicamente existem duas abordagens: resetar todos os elementos do browser ou criar um novo padrão básico. Mas, você já parou para repensar o seu CSS reset ou simplesmente utiliza um modelo pronto?

Confesso que sou uma reset junkie. Ao longo da minha carreira como desenvolvedora eu cheguei a testar e utilizar diversos resets diferentes como o &#8211; já velhinho porem ainda muito utilizado &#8211; [Eric Meyer&#8217;s Reset][1]. Por final acabei ficando com um boilerplate customizado para HTML e CSS, baseado no [HTML5 Boilerplate][2]. Este boilerplate utiliza o [normalize.css][3], um reset muito completo e bem aceito. E, para poupar tempo, eu confiava cegamente no meu querido reset e continuava minha vida feliz e contente sem ao menos perceber quantas redundâncias haviam no meu código&#8230; 

## Sobre resets, cestas básicas e cavalos

O erro é confiar em juizo de valor. O normalize, por exemplo, é utilizado pelo Twitter Bootsrap, iA, Soundcloud e até pela Nasa. Deve ser bom, certo? Sim e não. A triste verdade, meus amigos, é que só você mesmo pode dizer o que é bom para o seu projeto. Um reset é projetado pensando em necessidades gerais. É como uma cesta básica. Vai ter o arroz e feijão, mas não vai ter sua bolacha recheada de morango favorita. E se você tiver alergia a alguns dos alimentos não tem como reclamar. Você ganhou a cesta. Cavalo dado não se olha os dentes. Se quer algo bem feito faça você mesmo. Um bom reset é o SEU reset.

## Você precisa de tudo isso?

Sério. Isto é importante. Vou até perguntar de novo: Você precisa de tudo isso? Não quero deixar você paranóico, mas cada linha de código potencialmente aumenta o tamanho do seu CSS e o usuário vai ter que baixar tudinho em sabe-se lá que velocidade de banda&#8230; Não estou falando que você deve jogar tudo fora. Mas é necessário fazer uma análise do público-alvo do seu projeto (e obviamente que tipo de combo dispositivo + browser ele utiliza). Alguns resets, contém, por exemplo, elementos de correções de bugs de browsers antigos como o IE6/7. Meio inútil se você não pretende dar suporte a estes navegadores, certo? Já parou para pensar como é desnecessário estilos específicos para impressão no caso de uma aplicação mobile? Tem que ver isto aí.

## Algumas coisas fazem falta&#8230;

Acrescentar elementos desnecessários pode ser um problema, mas o contrário também é verdadeiro. Muitas vezes um reset acaba retirando funcionalidades importantes, como por exemplo:

<pre class="lang-css">em,strong{
    font-style:normal;
    font-weight:normal;
}
</pre>

E isto da um pepino sério quando você esquece de corrigir. Um cliente veio me perguntar por que ele não conseguia deixar textos em negrito ou itálico através do WordPress&#8230; A culpa era do reset. No final eu sempre acabava acrescentando:

<pre class="lang-css">em{
    font-style:italic;
}
strong{
    font-weight:bold;
}</pre>

Completamente redundante. Outro elemento comum em resets que me faz ranger os dentes.

<pre class="lang-css">ol, ul {
	list-style: none;
}
</pre>

Não faz sentido. Para que tirar os bullet points de TODAS as listas? No final o código fica muito mais longo pois é preciso acrescentar de volta as tais bolinhas. Seria muito mais prático retirar apenas quando necessário&#8230; Outras coisas que costumam dar problemas são margens, espaçamentos e formulários.

## Uma questão de estilo pessoal 

O normalize já traz alguns estilos padrões para texto, como por exemplo.

<pre class="lang-css">h1 {
    font-size: 2em;
    margin: 0.67em 0;
}

h2 {
    font-size: 1.5em;
    margin: 0.83em 0;
}

h3 {
    font-size: 1.17em;
    margin: 1em 0;
}

h4 {
    font-size: 1em;
    margin: 1.33em 0;
}

h5 {
    font-size: 0.83em;
    margin: 1.67em 0;
}

h6 {
    font-size: 0.67em;
    margin: 2.33em 0;
}</pre>

O que é completamente desnecessário no meu caso. 100% dos meus designs contam com o tamanhos de texto customizados para títulos. 

Tudo isto é muito subjetivo. O reset utópico deve atender as suas necessidades e preferências pessoais como desenvolvedor. Por exemplo, alguns resets trabalham com font-size padrão em 100%. Ótimo para quem vai trabalhar com pixels ou porcentagem. Péssimo para quem gosta de utilizar EM. A não ser que você seja um pequeno gênio da matemática, o melhor é definir o font-size para 62.5% e trabalhar com casas decimais na hora de fazer a conversão de medidas. 

## Conclusão

E você? Utiliza algum reset? Qual? Contruiu o seu do 0? Já parou para revisar todas as classes e verificar se existe alguma redundância no seu código? 

Vale a pena &#8220;perder&#8221; de 5 a 10 minutos do seu dia para conferir se o seu reset esta de acordo com o seu projeto, mesmo no caso de um código autoral. Os ganhos em velocidade, praticidade e organização são impressionantes. Os usuários agradecem.

 [1]: http://meyerweb.com/eric/thoughts/2007/05/01/reset-reloaded/ "Eric Meyer's Reset"
 [2]: http://html5boilerplate.com/ "HTML Boilerplate"
 [3]: http://necolas.github.com/normalize.css/