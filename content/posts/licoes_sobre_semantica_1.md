---
title: 'Lições sobre semântica #1'
authors: Diego Eis
type: post
date: 2004-11-08
url: /licoes_sobre_semantica_1/
tweetbackscheck:
  - 1355700965
shorturls:
  - 'a:3:{s:9:"permalink";s:48:"https://tableless.com.br/licoes_sobre_semantica_1";s:7:"tinyurl";s:26:"https://tinyurl.com/3nty9gs";s:4:"isgd";s:19:"https://is.gd/Z7jQm9";}'
twittercomments:
  - 'a:0:{}'
dsq_thread_id: 503031988
categories:
  - Geral
tags:
  - Técnicas e Práticas

---
Eu vi a idéia em um [site][1], e gostei muito, por isso vou aplicar aqui no [Tableless][2].
  
A idéia consiste no seguinte: Colocarei aqui regularmente umas perguntas sobre semântica. Darei duas ou três opções e você dará sua opinião postando nos comentários. Acho que isso ajudará a desenvolver uma idéia geral sobre semântica e como construir uma estrutura correta.

**Para fazer o título de uma lista, qual o mais semântico?**
  
<h_n_>Lorem ipsum</h_n_>
  
<ul>
  
<li>Dollor</li>
  
<li>Sit ames</li>
  
<li>Ipsum</li>
  
</ul>

<dl>
  
<dt>Lorem ipsum</dt>
  
<dd>Dollor</dd>
  
<dd>Sit ames</dd>
  
<dd>Ipsum</dd>
  
</dl>

**Concluindo**
  
Vamos acabar com as dúvidas?
  
Na minha opinião, o jeito mais semântico e certo de se fazer é a primeira opção. Pois veja:
  
Na segunda opção usamos listas de definição. As Listas de definição servem para que você coloque uma definição, uma explicação, uma descrição sobre um ítem específico.
  
Então, na segunda opção, vem o ítem &#8220;Lorem ipsum&#8221; e logo abaixo as definições sobre este ítem. Já na primeira opção, vem o título &#8220;Lorem Ipsum&#8221; e logo abaixo a lista.

Para entendermos melhor, vamos ver o resultado dos dois códigos em uma página, sem nenhuma formatação de css. Veja este [resultado aqui][3].
  
Percebemos que a primeira opção é a mais coerente em relação a segunda. O título da primeira opção parece ser um título referente a lista. Já na segunda opção, o que deveria ser o título da lista, não se comporta como tal.
  
Leitores de tela, browsers de texto, robôs de busca e etc, só interpretam como título tags H_n_ (h1, h2, h3, h4, h5, h6).

Espero que eu tenha esclarecido a dúvida e que vocês tenham gostado da idéia, até a próxima.

 [1]: https://www.simplebits.com/
 [2]: https://tableless.com.br/
 [3]: https://tableless.com.br/estudo/quiz/quiz1.asp