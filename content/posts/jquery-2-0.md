---
title: jQuery 2.0
author: Dani Guerrato
type: post
date: 2013-05-23
excerpt: Conheça as vantagens (e desvantagens) da nova versão da biblioteca de JavaScript mais utilizada no mundo.
url: /jquery-2-0/
categories:
  - Artigos
  - JQuery
tags:
  - JavaScript
  - JQuery

---
Há cerca de um mês o jQuery 2.0 foi oficialmente lançado. Neste meio tempo pudemos analisar a nova versão da biblioteca e conhecer de perto as novidades. Mas será que vale a pena fazer o upgrade? Ou já é hora de abandonar o barco? Conheça os novos recursos da biblioteca, diga adeus para alguns antigos e decida por si mesmo.

## Builds Customizáveis

O jQuery funciona como uma biblioteca real. Você pode escolher quais livros entram e quais vão embora da sua prateleira pessoal. Desde a compilação 1.8 já existia a opção de personalizar a biblioteca. Agora na versão 2.0 este recurso foi ampliado. É possível selecionar entre 12 módulos diferentes.

  * **ajax**: Todas as funcionalidades do AJAX: $.ajax(), $.get(), $.post(), $.ajaxSetup(), .load(), transports, e todos os atalhos de ajax, como.ajaxStart().
  * **ajax/xhr**: Apenas o evento de transporte do AJAX XMLHTTPRequest.
  * **ajax/script**: Método de transporte AJAX// <![CDATA[; usado para recuperar scripts.
  * **ajax/jsonp**: Método de transporte JSONP AJAX; depende do transporte ajax/script.
  * **css**: O método .css() mais .show(), .hide() e .toggle() não animados.
  * **deprecated**: Métodos documentados como obsoletos mas que não foram removidos. Atualmente apenas .andSelf().
  * **dimensions**: Os metodos .width() e .height() , incluindo as variações inner- e outer-.
  * **effects**: O método .animate() e seus atalhos como .slideUp() e .hide(&#8220;slow&#8221;).
  * **event-alias**: Eventos com gatilhos, como .click() ou .mouseover().
  * **offset**: Os métodos .offset(), .position(), .offsetParent(), .scrollLeft(), e .scrollTop()
  * **wrap**: Métodos .wrap(), .wrapAll(), .wrapInner(), e .unwrap().
  * **sizzle**: O motor de seletor Sizzle. Quando este módulo é excluido, ele é substituido por um motor de seletor rudimentar baseado no método querySelectorAll do browser, que não é suportado pelas extensões de seletores ou pela semântica aumentada do jQuery.

Eliminar os módulos inúteis para o seu projeto é uma boa prática que pode pode diminuir e muito o tamanho da biblioteca (a versão mais simples pode chegar a cerca de 10Kb quando minificada). Mas Infelizmente ainda não é uma solução prática já que para construir sua versão customizada do jQuery você precisa conhecer um pouco sobre Git, Node.js e Grunt. Você pode ler as [instruções completas][1] no repositório da equipe. Ou você pode usar o gerador automático [jQuery builder][2]. Ele ainda não é compatível com todos os módulos novos, mas já quebra um galho. Ah, e ele funciona também para personalizar as versões mais antigas do jQuery.

Parece óbvio, mas vale lembrar que os plugins que você pretende utilizar precisam estar trabalhando com os mesmos módulos que você escolheu ou simplesmente não vão funcionar.

## O jQuery 2.0 não é compatível com IE 6/7/8

É isto mesmo. Segundo a equipe de desenvolvimento o jQuery é &#8220;feito para a Web moderna&#8221; e ao abandonar o suporte aos browsers mais antigos eles podem agora se concentrar em deixar a biblioteca mais rápida, leve, etc. Esta atitude foi no mínimo controversa já que muitos profissionais optavam por desenvolver em jQuery em detrimento de soluções mais práticas como HTML5/CSS3 justamente pela retro-compatibilidade.

Se desenvolver algo acessível para as versões mais antigas do Internet Explorer é algo realmente importante pra você não se desespere. A versão 1.9 continuará sendo suportada pela equipe&#8230; Ou seja, a partir de agora existirão dois caminhos de desenvolvimento diferentes. Algo como duas timelines: uma para a versão 1x e outra para a 2x. Mas é provável que as próximas mudanças da família 1x sejam apenas correções de bugs. Para ser sincera não acredito que implantarão recursos novos. Espero estar errada.

## Mais Leve

O jQuery 2.0 é 12% mais leve do que a versão anterior (1.9.1). Mas isto, infelizmente, não foi graças a uma otimização mágica. Ser mais leve frequentemente implica em perda de funcionalidades e esta foi a decisão estratégica da equipe do jQuery. Estes 12% a mais eram justamente os patches de compatibilidade do IE que foram retirados. E podemos esperar mais cortes deste tipo no futuro. Provavelmente as próximas atualizações do jQuery não serão compatíveis com versões antigas do Android/Webkit 2.x.

## Onde eu consigo

[http://code.jquery.com/jquery-2.0.0.min.js][3] (minificada, para produção)
  
[http://code.jquery.com/jquery-2.0.0.js][4] (não minificada, para teste)

## Fallback

Como dito anteriormente o jQuery 2.0 não é compatível com IE 6/7/8. A solução proposta pela equipe é utilizar comentários condicionais como Fallback.

<pre class="lang-HTML">&lt;!--[if lt IE 9]&gt;
&lt;script src="jquery-1.9.1.js"&gt;&lt;/script&gt;
&lt;![endif]--&gt;
&lt;!--[if gte IE 9]&gt;&lt;!--&gt;
&lt;script src="jquery-2.0.js"&gt;&lt;/script&gt;
&lt;!--&lt;![endif]--&gt;
</pre>

## Vale a pena mudar?

A resposta para esta, como muitas outras perguntas sobre desenvolvimento web é depende. Eu também gostaria de viver em um mundo mágico onde ninguém utiliza IE8, mas infelizmente ele ainda é um browser relativamente popular. Os números flutuam de acordo com as pesquisas que você utiliza, mas considerando a [W3C Schools][5] o IE 8 representa cerca de 5.3% dos usuários. Se você esta pensando em implementar o jQuery 2.0 no seu site minha recomendação é ignorar estatísticas genéricas e analisar o seus próprios dados para conhecer seus visitantes e tomar uma decisão informada. No geral a nova versão tem mais prós do que contra e até que a participação de mercado do Internet Explorer 6. 7 e 8 realmente diminua ela pode ser inviável se este for seu público alvo. Manter duas versões em comentários condicionais, como sugerido pela própria equipe do jQuery, pode ir contra a proposta de facilitar o desenvolvimento e acabar mais atrapalhando que auxiliando, já que precisaríamos trabalhar com duas bibliotecas diferentes. Se compatibilidade com o IE não é um problema vá em frente e seja feliz!

## Pouco demais, tarde demais?

Quando o jQuery foi lançado ele representou uma mudança grande no modo como pensávamos a internet. Naqueles idos tempos de 2006 a web era um lugar bem diferente. O iPhone ainda não havia sido lançado e nem se sonhava em algo como design responsivo. Muitos sites naquela época ainda utilizavam o formato Flash para interações, mas isto já estava com os dias contados. A nova ordem agora era cortar o peso desnecessário e desenvolver sites mais semânticos e compatíveis com multiplos browsers. Mas alguns desenvolvedores se sentiram orfãos da capacidade de animações dinâmicas oferecidas pelo Flash. O jQuery chegou na hora certa para suprir esta necessidade ao mesmo tempo que oferecer uma solução crossbrowser. Muita gente se jogou de cabeça e centenas de plugins surgiram para todo tipo de situação. Slider, carrosel, shadowbox, pequenas animações&#8230; O mecanismo dos plugins era tão simples que até quem não era familiarizado com JavaScript conseguia implementar com facilidade. E isto foi utilizado com um certo exagero. O que era novo acabou tornando-se repetitivo e até desnecessário algumas vezes. Por uma ironia do destino, o jQuery aos poucos vai sofrendo o mesmo destino do Flash: ser pesado demais para a nova geração. Com o crescimento de dispositivos móveis a preocupação com a perda de peso no browser ficou ainda maior. E as tendências de design minimalista acabam jogando para escanteio todas aquelas firulas e animações desnecessárias. O que entusiasmava muitos no inicio acaba sendo ouvido com uma certa torcida de nariz da comunidade de desenvolvedores. 

O HTML5 e o CSS3 ganharam mais espaço (afinal você pode [criar diversos elementos da user interface][6] utilizando apenas estas tecnologias) e houve uma revitalização do JS baunilha. É, de repente, o jQuery não parece mais tão leve e legal assim quanto no inicio. É claro, ainda existe muita coisa bacana para ser feita com jQuery, mas infelizmente não existe a mesma empolgação de quando era algo novo. Agora é esperar para ver se as próximas versões irão revolucionar novamente a vida dos desenvolvedores.

## Saiba mais

[jQuery 2.0 Release][7]

 [1]: https://github.com/jquery/jquery/#readme "jQuery ReadMe"
 [2]: http://projects.jga.me/jquery-builder/ "jQuery Builder"
 [3]: http://code.jquery.com/jquery-2.0.0.min.js "jQuery 2.0 Min"
 [4]: http://code.jquery.com/jquery-2.0.0.js "jQuery 2.0"
 [5]: http://www.w3schools.com/browsers/browsers_explorer.asp "Browser Explorer - W3C Schools"
 [6]: http://tableless.com.br/elementos-de-interface-utilizando-apenas-css3 "Elementos de interface utilizando apenas css3"
 [7]: http://blog.jquery.com/2013/04/18/jquery-2-0-release "jQuery 2.0 Release"