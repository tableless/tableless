---
title: As cores da minha web
author: Reinaldo Ferraz
type: post
date: 2012-04-02
excerpt: Tenho um grande amigo que sonhava ser piloto de avião. Porém, seu sonho de pilotar acabou quando, aos trinta anos de idade, ele descobriu que tinha um grau de daltonismo que o impediu de continuar o treinamento.
url: /as-cores-da-minha-web/
tweetbackscheck:
  - 1356388667
shorturls:
  - 'a:3:{s:9:"permalink";s:31:"http://tableless.com.br/?p=5876";s:7:"tinyurl";s:26:"http://tinyurl.com/d76nrge";s:4:"isgd";s:19:"http://is.gd/2m3SYQ";}'
twittercomments:
  - 'a:0:{}'
dsq_thread_id: 634177252
categories:
  - Acessibilidade
  - Geral
tags:
  - acessibilidade
  - design
  - padroes web

---
Talvez as cores que eu veja não sejam as mesmas que você enxerga, mas isso não faz com que a sua percepção da web seja diferente. Nesse ambiente tão democrático, nada mais justo do que discutir as diversas formas de perceber as cores da web.

Tenho um grande amigo que sonhava ser piloto de avião. Por trabalhar em uma empresa aérea, a proximidade com as grandes máquinas voadoras o encantava. Porém, seu sonho de pilotar acabou quando, aos trinta anos de idade, ele descobriu que tinha um grau de daltonismo que o impediu de continuar o treinamento.

O mais curioso dessa história foi que ele viveu seus trinta anos anteriores sem saber que enxergava cores de forma diferente das demais pessoas. Seu tipo de daltonismo foi classificado como deuteranopia, que dificultava reconhecer certos tons de verde. A partir dessa descoberta, comecei a estudar como cada pessoa vê as cores da sua web.

Por esse motivo, os cuidados com cores são importantíssimos no desenvolvimento de páginas web. O WCAG 2.0 (Web Content Accessibility Guidelines) é bem direto com relação a isso: [A cor não deve ser utilizada como o único meio visual de transmitir informações][1]. Isso significa que você não deve utilizar indicações como &#8220;clique no botão verde para continuar&#8221; ou, &#8220;campos marcados em vermelho são obrigatórios&#8221;.

Mas isso não significa que o uso de cores deve ser banido da web. Pelo contrário. O uso de cores e contrastes é um dos maiores atrativos visuais de uma página. O que faz uma página ser bela aos olhos de um usuário é a combinação entre tons e cores. Mas o cuidado com o contraste deve ser considerado, já que pessoas com certos graus de daltonísmo e baixa visão podem ter dificuldade de enxergar alguns contrastes. Por isso mesmo, o [E-Mag, modelo de acessibilidade do Governo Eletrônico][2] diz que o mínimo de contraste entre o plano de fundo e o primeiro plano deve ser de 3 para 1. Se você tem dúvidas, na última página do E-Mag existe uma tabela de cores que faz o contraste adequado com preto e branco (já em hexadecimal). No [WCAG 2.0, esse valor é de 4,5 para 1][3].

E quando o daltonismo é tão severo ao ponto de fazer com que a pessoa não enxergue cor nenhuma (somente tons de cinza)? Esse é um tipo de daltonismo raro, mas aconteceu com o artista Neil Harbisson, que esteve na quinta edição da Campus Party Brasil contando como conseguiu resolver seu problema de distinguir cores: implantando uma câmera em seu crânio que identifica as cores e transforma essa informação em áudio. [Uma ótima palestra que vale a pena ser assistida][4].

E por falar em bani-las da web, o que podemos dizer da implementação de cores quando o acesso a página é feito por um software leitor de tela? A primeira recomendação dada pelo WCAG é [separar a estrutura do documento da apresentação][5], ou seja: Formatação visual somente dentro do CSS. Isso quer dizer que o software leitor de tela, que navega pelo código da página HTML, ignora as cores aplicadas no documento? Não!

O software JAWS, popular software leitor de tela, possui uma [configuração que permite que o usuário saiba quais as cores ou fontes utilizadas na página][6], ou mesmo [simples combinações de tecla podem permitir que o usuário cego saiba que fonte está sendo usada no site e qual a cor dela][7].

Isso significa que a minha web tem cor, inclusive para uma pessoa cega que acessa minha página.

Além de todas as diretrizes citadas nesse documento o uso do bom senso é fundamental para termos uma web bela, cheia de cores e que permitam que todos possam navegar por ela. Inclusive aquele meu amigo do início desse texto, que um dia me pediu ajuda para instalar sua televisão nova e não enxergava um tal botão verde no controle remoto que fazia a busca por canais. Felizmente, o termo &#8220;pesquisar canais&#8221; estava escrito no controle.

Talvez eu não enxergue as cores da mesma forma que você, mas mesmo com essas diferenças a minha web é tão bela quanto a sua deve ser.

 [1]: http://www.w3.org/WAI/WCAG20/quickref/#qr-visual-audio-contrast-without-color
 [2]: http://www.governoeletronico.gov.br/acoes-e-projetos/e-MAG
 [3]: http://www.w3.org/TR/UNDERSTANDING-WCAG20/visual-audio-contrast-contrast.html
 [4]: http://www.youtube.com/watch?v=CvPOh0p9cf0
 [5]: http://www.w3.org/WAI/GL/WCAG20/WD-WCAG20-TECHS/C22
 [6]: http://www.stacybleeks.com/jaws_speech_manager_tutorial.html
 [7]: http://webaim.org/resources/shortcuts/jaws