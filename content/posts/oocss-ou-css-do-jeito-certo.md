---
title: OOCSS ou CSS do jeito certo
author: Diego Eis
type: post
date: 2011-12-19
excerpt: O CSS é algo muito simples de ser escrito mas com apenas um deslize todo o código pode transformar o projeto em um inferno. Saiba como podemos evitar isso.
url: /oocss-ou-css-do-jeito-certo/
tweetbackscheck:
  - 1356408379
shorturls:
  - 'a:3:{s:9:"permalink";s:31:"http://tableless.com.br/?p=4713";s:7:"tinyurl";s:26:"http://tinyurl.com/cg8d3k8";s:4:"isgd";s:19:"http://is.gd/CkmTVo";}'
twittercomments:
  - 'a:0:{}'
dsq_thread_id: 509393793
categories:
  - Código
  - CSS
  - HTML
  - Técnicas e Práticas
tags:
  - 2011
  - CSS
  - CSS3
  - desenvolvimento web
  - tecnicascss

---
## O conceito

Escrever CSS é fácil. Isto não deveria ser um problema, mas é. Por ser fácil os desenvolvedores acabam se esquecendo de princípios básicos, técnicas e metodologias que nos ajudam a manter o controle durante a produção. Entenda que algumas dessas metodologias não precisam ser aplicadas em sites pequenos. Por exemplo, aqui no Tableless eu não [modularizo o CSS em vários arquivos][1] por um ou dois motivos: **1)** Somente eu tenho acesso ao código. **2)** O site não é grande. Ele tem meia dúzia de páginas e funcionalidades.
  
Mas quando falamos de sites grandes (em visitação e quantidade de páginas) existem algumas restrições: velocidade de carregamento, compatibilidade entre browsers, manutenção, flexibilidade para mudanças etc. Tudo isso deve ser pensado e planejado antes de colocarmos a mão na massa. É no planejamento que iremos estruturar como serão feitas as manutenções posteriores, como iremos mudar elementos principais sem interferir no layout como um todo.

O CSS Orientado a Objeto (em inglês OOCSS &#8211; Object Oriented CSS &#8211; Sendo sincero, esse nome é muito ruim) tem como conceito técnicas que já falamos durante muito tempo, mas que como o <a href="http://tableless.com.br/introducao-ao-responsive-web-design/" title="Artigo sobre responsive web design" target="_blank">Responsive Web Design</a>, está ganhando força somente agora.

## Princípios

O OOCSS está baseado em dois pontos cruciais que são a separação da **estrutura e do visual** e a **independência do container em relação ao conteúdo**.

### Separação da estrutura e do visual

A maioria dos elementos estilizados em uma página web tem diferentes características visuais que são repetidas em diferentes contextos e situações. Algumas características são fáceis de identificar como cores, títulos, gradientes, bordas etc. Essas são características visuais. Contudo, existem também as características de estrutura, que é onde nós &#8220;montamos&#8221; os elementos, definindo tamanhos, distâncias, medidas etc. Essas características também são repetidas em diversos elementos no decorrer do site. 

A ideia é que nós separemos as características visuais das características estruturais, tornando-os modulares de forma que possamos reutilizá-los em diferentes elementos tendo resultados iguais.

Imagine 3 elementos diferentes, como um **botão**, uma **caixa de chamada** e um **destaque** que normalmente fica na lateral do site. Eles tem características estruturais diferentes, como width, height, paddings, margins etc. Mas as características visuais são iguais, como por exemplo o border-radius, background e o box-shadow. O CSS normal ficaria assim:

<pre class="lang-css">.botao {
   width:100px;
   height:50px;
   text-align:center;
   font:bold 13px verdana, arial, tahoma, sans-serif;
   border-radius:10px;
   background: url(gradients.png) repeat-X center;
   box-shadow: 0 0 10px rgba(0,0,0,0.5);
}

.chamada {
   width:250px;
   float:left;
   font:bold 23px verdana, arial, tahoma, sans-serif;
   border-radius:10px;
   background: url(gradients.png) repeat-X center;
   box-shadow: 0 0 10px rgba(0,0,0,0.5);
}

.destaque {
   width:300px;
   height:250px;
   border-radius:10px;
   background: url(gradients.png) repeat-X center;
   box-shadow: 0 0 10px rgba(0,0,0,0.5);
}
</pre>

Para reutilizar de forma inteligente as características iguais destes elementos e prevendo que talvez seria criado outros elementos com as mesmas características &#8211; já que o designer mantém sempre (quase sempre, né?) um padrão visual estético &#8211; é interessante que criemos uma classe que componha estas características e apliquemos essa classe nos elementos necessários. Assim:

<pre class="lang-css">.botao {
   width:100px;
   height:50px;
   text-align:center;
   font:bold 13px verdana, arial, tahoma, sans-serif;
}

.chamada {
   width:250px;
   float:left;
   font:bold 23px verdana, arial, tahoma, sans-serif;
}

.destaque {
   width:300px;
   height:250px;
}

.boxEffects {
   border-radius:10px;
   background: url(gradients.png) repeat-X center;
   box-shadow: 0 0 10px rgba(0,0,0,0.5);
}
</pre>

Em cada elemento que necessitasse destas características visuais, basta inserir a classe .boxEffects ao elemento.

Entenda que o abuso dessa técnica pode trazer complicações. Você não vai criar uma classe para cada característica visuais e sair aplicando essas classes em tudo quanto é elemento. Você estaria voltando a 1999 onde tínhamos aquele velho problema de misturar as [camadas de formatação e informação][2].

### Independência dos containers e do conteúdo

Imagine que você crie algum estilo para a formatação de algum elemento como por exemplo um parágrafo e atrela este estilo para os parágrafos localizados no article principal:

<pre class="lang-css">article p {
   font:bold 13px verdana, arial, tahoma, sans-serif;
   line-height:18px;
   letter-spacing:1px;
}
</pre>

Mas então surge a necessidade de ter um parágrafo com as mesmas características no rodapé, por exemplo, mas com o tamanho da fonte maior! Você pode fazer assim:

<pre class="lang-css">article p, footer p {
   font: 13px verdana, arial, tahoma, sans-serif;
   line-height:18px;
   letter-spacing:1px;
}

footer p {font-size:20px;}
</pre>

O que é ainda é ruim, mas é muito melhor do que fazer assim:

<pre class="lang-css">article p, footer p {
   font: 13px verdana, arial, tahoma, sans-serif;
   line-height:18px;
   letter-spacing:1px;
}

footer p {
   font: 20px verdana, arial, tahoma, sans-serif;
   line-height:18px;
   letter-spacing:1px;
}
</pre>

Onde duplicamos desnecessariamente vários estilos.

Com o OOCSS nós devemos transformas estes estilos em módulos para serem reutilizados e não atrelando os estilos a um elemento específico. 

Isso acontece também quando já fizemos uma classe onde carrega os estilos comuns. Se voltarmos ao exemplo anterior, alguém pode fazer assim:

<pre class="lang-css">footer .boxEffects {...}</pre>

Estamos aqui atrelando a classe que antes era para ser algo genérico ao elemento footer. Cuidado ao fazer isso. Tenha um bom motivo antes de ir adiante.

## Outras boas práticas

Existem algumas boas práticas que fazem parte do OOCSS e que melhoram muito o planejamento e a prática do desenvolvimento web:

### Modularização de código CSS

Não estou falando aqui sobre a modularização de **arquivos** CSS, mas sim do Código. Essa modularização é feita sob medida para cada um dos projetos. O objetivo é que o código CSS seja reutilizado em várias partes da produção evitando que você crie mais código. É aconselhável que se defina padrões de código para os principais elementos do layout. A equipe pode fazer isso ou delegar esse importante trabalho para um desenvolvedor, que será responsável em criar os métodos e os padrões estruturais dos elementos.

### Minimizar usos de seletores muito específicos

Encontre o meio termo. Não faça seletores muito específicos ou seletores muito genéricos. O CSS trabalha com especificidade: quanto mais específico, mais certeiro você é ao capturar um elemento, mas seu CSS fica mais engessado e consequentemente você usa mais código. Quanto mais genérico, mais elementos do mesmo tipo você formata, mas o risco de conflito de estilos aumenta. O ideal é encontrar o meio termo, onde você é tão específico e nem tão genérico.

Dependendo da forma que você utiliza os seletores os browsers podem ser ou não mais rápidos ao renderizar seu site. <a href="http://tableless.com.br/melhorando-performance-css/" title="Performance do seu CSS" target="_blank">Já falamos disso aqui</a>.

### Formate elementos com classes modulares

A ideia é que ao criar uma nova página, você não tenha que criar novo código CSS. Se a página tiver a estrutura diferente mas os elementos tem características visuais iguais, aí está uma boa oportunidade para modularizar o código visual dos objetos. 

Um exemplo para demonstrar essa prática é ao fazer botões para diferentes ações. Normalmente utilizamos os mesmos botões com cores diferentes para definirmos visualmente ações diferentes que o usuário pode tomar. O botão de SALVAR tem o mesmo formato de CANCELAR, mas a cor dos dois é diferente, sendo que o primeiro é verde o segundo vermelho. O código seria assim:

<pre class="lang-css">.botao {
   display:inline-block;
   padding:10px 20px;
   font:13px verdana, arial, tahoma;
   color:white;
   text-decoration: none;
}
</pre>

Este código cria toda a estrutura do botão. Agora falta definir as cores de fundo. Eu farei isso criando duas classes: **btVerde** e **btVermelho**. Essas classes serão utilizadas em pareceria com a classe **botao**

<pre class="lang-css">.btVermelho {background: red;}
.btVerde {background: green;}
</pre>

Agora, o HTML ficaria assim:

<pre class="lang-html">&lt;a href="#" class="botao btVermelho"&gt;Cancelar&lt;/a&gt;
&lt;a href="#" class="botao btVerde"&gt;Salvar&lt;/a&gt;
</pre>

Porque criei os nomes das classes btVermelho e btVerde em vez de btCancelar e btSalvar? Porque pode ser que exista algum botão que também seja verde, mas não tenha a ação de salvar. Assim deixo meu leque aberto para novas atribuições.

### Concluindo

Seguir esses pequenos detalhes evitam uma série de problemas comuns no desenvolvimento client-side. A reutilização de código CSS se torna real, a velocidade do carregamento melhora e os problemas de manutenção são solucionados. A flexibilidade que teremos ao modificar o CSS será muito grande e não aumentaremos nosso código a cada modificação feita. A ideia é que seu código CSS fique sob controle. A utilização de <a href="http://tableless.com.br/biblioteca-css-ou-framework/" target="_blank">frameworks e bibliotecas podem ajudar em muitos momentos</a>.

 [1]: http://tableless.com.br/modulando-o-css/
 [2]: http://tableless.com.br/camadas-de-desenvolvimento-client-side/