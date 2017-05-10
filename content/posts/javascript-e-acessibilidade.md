---
title: Javascript e acessibilidade
author: Davi Ferreira
type: post
date: 2010-11-04
excerpt: Dando continuidade a nossa série sobre acessibilidade, confira algumas dicas para desenvolver sites dinâmicos tendo um mínimo de cuidado com screen readers e navegadores com JavaScript desabilitado.
url: /javascript-e-acessibilidade/
aktt_notify_twitter:
  - yes
tweetbackscheck:
  - 1356440622
shorturls:
  - 'a:3:{s:9:"permalink";s:51:"http://tableless.com.br/javascript-e-acessibilidade";s:7:"tinyurl";s:26:"http://tinyurl.com/42jstn4";s:4:"isgd";s:19:"http://is.gd/Ry9ISe";}'
twittercomments:
  - 'a:1:{i:15372882397896704;s:6:"136424";}'
tweetcount:
  - 1
dsq_thread_id: 503039694
categories:
  - Acessibilidade
  - AJAX
  - Artigos
  - Código
  - JavaScript
  - JQuery
tags:
  - acessibilidade
  - JavaScript

---
É muito comum o desenvolvedor ficar empolgado ao descobrir recursos, plugins, animações e efeitos JavaScript e acabar exagerando no produto final. Também é muito comum, [como disse a Thaiana][1], que acessiblidade esteja ligado exclusivamente a sites governamentais. Aos poucos este cenário está mudando.

Além de tornar o seu site acessível à pessoas com necessidades especiais, as técnicas abaixo serão úteis também quando o navegador do usuário estiver com JavaScript desabilitado. E se mesmo assim você ainda não estiver convencido, pense que, quanto menos JavaScript, mais otimizado e estável será o seu site/sistema.

## O problema

Acessibilidade, basicamente, significa tornar o seu site/sistema compatível com dispositivos leitores de tela. O que este dispositivo faz é tentar converter todo o conteúdo presente em uma página para uma saída especial, seja ela voz (text-to-speech) ou braille. Por isso a importância da semântica no HTML e, por isso também, a importância do JavaScript não acabar atrapalhando o funcionamento do seu site.

Dependendo da forma como você utilizou JavaScript, parte do conteúdo pode passar batida no screen reader. Isso acontece muito com animações (conteúdos escondidos) e eventos que não são nativos do elemento, como tentar utilizar onClick em um parágrafo.

## <noscript>

A prioridade número 1 nas regras para acessibilidade é tornar todo o conteúdo disponível quando o navegador não estiver com JavaScript habilitado. Procure implementar alternativas HTML parecidas com o conteúdo estabelecido por seus scripts.

No entanto, é importante ressaltar que o noscript só vai funcionar quando o javascript estiver dasabilitado no navegador (ele não vai funcionar se o JavaScript estiver com erro, por exemplo). Alguns screen readers tentam interpretar JS, portanto, utilizar JavaScript NÃO significa tornar seu site pouco acessível. Depende da forma como você implementa seus scripts.

Muita gente é a favor da extinção da tag <noscript>. O que eles defendem é que basta você desenvolver seus scripts de forma não-obstrutiva. Seu script pode ser executado ou não &#8211; independente disso ele não afetará a funcionalidade básica da página.

## Preciso mesmo usar JavaScript?

Sempre que for utilizar algum efeito ou interação em JavaScript você deve se perguntar se ele é mesmo necessário. Ou ainda, não daria pra fazer a mesma coisa utilizando apenas HTML e CSS? 

Pense duas vezes antes de implementar qualquer tipo de script. Analise não só a questão da acessibilidade, mas também performance e manutenção.

## Não invente eventos e não fique preso ao mouse

Procure utilizar eventos JavaScript apenas em elementos que estão aptos a recebê-los. Por exemplo, não utilize onClick em um <li>. Geralmente, os eventos de interação devem estar associados a links e botões.

Lembre-se também que nem sempre vai ser utilizado o mouse, logo, eventos como onMouseOver e onMouseOut seriam inválidos. Ofereça alternativas globais, como onFocus, onBlur, onClick (que, no teclado, seria executado com a tecla Enter) &#8211; visando usuários que utilizam outros dispositivos.

Um problema grave são menus ativados no mouseover. Nesse caso o usuário não teria como acessar todas as páginas &#8211; ele não poderia navegar por toda a estrutura do site.

Essas regras estão também diretamente ligadas a conteúdos carregados via AJAX. Dependendo da forma como você ativa o evento, o screenreader vai ler ou não o conteúdo recém adicionado.

## WAI-ARIA

Procurando estabelecer um padrão para acessibilidade e conteúdos dinâmicos foi criada a especificação WAI-ARIA (Accessible Rich Internet Applications). O que ela faz é adicionar novas formas de identificar e habilitar funcionalidades dinâmicas através de propriedades nas tags HTML. Recentemente o jQuery UI adicionou suporte total ao framework ARIA tornando assim seus widgets e elementos de interface acessíveis a usuários com alguma necessidade especial.

O ARIA, por exemplo, pode definir regiões em um site e habilitar o movimento via tab entre essas regiões, ao invés de elemento por elemento. O WAI-ARIA também possibilita definir papéis (roles) para elementos como menu, menuitem, banner, application etc.

Este é um assunto muito rico e ainda pouco explorado. Para mais informações visite a <a href="http://www.w3.org/WAI/PF/aria/" rel="external">especificação do WAI-ARIA no site do W3C</a> e também <a href="http://www.paciellogroup.com/blog/?p=106" rel="external">este tutorial sobre os papéis disponíveis no ARIA</a>.

 [1]: /como-tornar-seu-website-acessivel