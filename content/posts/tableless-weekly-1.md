---
title: 'Tableless Weekly #1'
author: Lenilson Nascimento
type: post
date: 2014-08-12
excerpt: Seleção semanal do tableless que reúne links úteis, novidades no mercado front end e alguns sites bem legais.
url: /tableless-weekly-1/
dsq_thread_id: 2918018656
categories:
  - Digest
  - Geral
  - Weekly
tags:
  - Digest
  - tablelessweekly

---
Estamos começando com o primeiro artigo da série Tableless Weekly. Série semanal que trará um pouco das novidades do mercado front-end, links úteis e alguns sites legais que encontrarmos por ai.

### HTML5

O Elemento Dialog já está disponivel para o chrome a partir da versão 37.

Como o HTML5 sempre tem trazido consigo uma grande mudança nas tags, principalmente por questões semânticas, a tag Dialog já foi implementada a partir da versão 37 do Chrome e na versão 6 do Safari. Em breve estará disponível nos outros browsers.

A funcionalidade da tag é bem básica: Representar semânticamente as caixas de diálogo que geralmente implementamos em sistemas e sites.

Mas por que criar uma nova tag se podíamos fazer isso com uma div? A questão é semântica e não visual. Assim fica explícito para os robôs de busca e outros scripts, interpretarem o conteúdo de seu site e saber exatamente para que serve cada elemento, principalmente se tratando das caixas de diálogo que fazemos normalmente com divs, para destacá-las, para que eles entendam que aquilo não é somente uma div cheia de textos, mas sim uma caixa de alerta, de diálogo, que interfere na navegação do usuário.

Que tal mostrar na prática? Então vamos lá&#8230;

<img class="alignnone size-full wp-image-43803" src="http://tableless.com.br/uploads/2014/08/dialog.png" alt="dialog" width="1844" height="900" srcset="uploads/2014/08/dialog.png 1844w, uploads/2014/08/dialog-265x129.png 265w, uploads/2014/08/dialog-400x195.png 400w" sizes="(max-width: 1844px) 100vw, 1844px" />
  
Provavelmente você já deve ter visto muitas dessas por aí ou até feito alguma.

Como eu disse acima, nada que não se possa fazer com uma div, mas observe agora o código e veja a estrutura semântica.

<pre>&lt;dialog&gt;
   &lt;p&gt;Esta é uma caixa de diálogo&lt;/p&gt;
   &lt;button id="#close"&gt;Fechar&lt;/button&gt;
&lt;/dialog&gt;
&lt;button id="#show"&gt;Mostrar Caixa de diálogo&lt;/button&gt;
&lt;script&gt;
 var dialog = document.querySelector('dialog');
 document.querySelector('#show').onclick = function() {
 dialog.show();
 };
 document.querySelector('#close').onclick = function() {
 dialog.close();
 };
&lt;/script&gt;</pre>

Perceba que o código se tornou bem mais semântico e mais amigável concorda? Deixe sua opinião nos comentários&#8230;

## Links úteis

Estes são links interessantes pra você visitar nessa semana.

Se você tem alguma sugestão, estaremos disponibilizando no próximo artigo um link para envio.

### Ferramentas

Algumas das ferramentas úteis para front-end.

<a href="http://jsfiddle.net/" target="_blank">JSFiddle</a> &#8211; Talvez não seja uma novidade para ninguem, mas com o JSFiddle fica simples testar seu código HTML, CSS e JS, ou códigos prontos que você ahca por aí e não sabe se funciona 😉
  
<a href="http://fortawesome.github.io/Font-Awesome/" target="_blank">FontAwesome</a> &#8211; Também não deve ser novidade, mas com o FontAwesome, temos vários ícones disponíveis em formato de fonte.
  
<a title="BrowserDiet" href="http://browserdiet.com/pt/" target="_blank">BrowserDiet</a> &#8211; Um site com definitivamente tudo(ou quase tudo) que você precisa saber sobre como perder peso no carregamento de sites.
  
<a title="BrowserFit" href="http://browserfit.github.io/" target="_blank">BrowserFit</a> &#8211; Site que reúne vários conceitos para criar sites responsivos. Aborda conceitos como: mobile first, content first, media queries, entre outros.

## Alguns sites legais

[Ominisense][1]<span style="text-decoration: underline"><br /> </span>Site da Ominisense. Simplesmente estou namorando esse site. Os efeitos são muito legais e se você assistir o vídeo no final, verá o quanto é incrível o trabalho que fizeram. O video completamente feito em HTML5, fala sobre os sentidos humanos e sobre escolhas, achei bem interessante e resolvi colocar aqui.

<a title="Cantina Volpolicella Negrar" href="http://www.cantinanegrar.it/" target="_blank">Cantina Valpolicella Negrar</a>
  
Site de uma cantina de vinhos italiana. O Design é bem moderno, e o vídeo que fizeram ficou muito legal.

<a title="Volkswagen SportCars" href="http://volkswagen-sportscars.fr/" target="_blank">Volkswagen SportCars</a>
  
Site da Volkswagen para divulgar seus carros esportivos. A interface e navegação pelo site são muito intuitivos e agradáveis.

## Conclusão

Bom galera, este foi nosso primeiro Tableless Weekly, esperamos que tenham gostado. Deixem seus comentários abaixo e compartilhem com seus amigos front-enders.

Então até a próxima terça com mais conteúdo fresco pra vocês se deliciarem.

 [1]: http://omnisense.net/