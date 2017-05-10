---
title: EPTV.com.br é tableless
author: Elcio Ferreira
type: post
date: 2005-07-20
url: /eptv_tableless/
tweetbackscheck:
  - 1356419199
shorturls:
  - 'a:3:{s:9:"permalink";s:38:"http://tableless.com.br/eptv_tableless";s:7:"tinyurl";s:26:"http://tinyurl.com/428ulln";s:4:"isgd";s:19:"http://is.gd/K6ybb1";}'
twittercomments:
  - 'a:0:{}'
dsq_thread_id: 503033077
categories:
  - Geral
tags:
  - cotidiano

---
[EPTV][1], tableless. Acabaram de colocar no ar. Modéstia a parte, excelente exemplo para quem está começando. Com mais conteúdo, conseguimos reduzir o HTML em 65% na página inicial, com uma redução média de mais de 50% nas outras páginas. Contando imagens, CSS e javascript, a redução total média foi de mais de 30%.

Demos o curso para eles e acompanhamos o projeto até mais ou menos um mês atrás. Estou orgulhoso de ver o site no ar agora. Fizeram um excelente trabalho. Funcionou muito bem aqui no Firefox, Opera e Konqueror.

O HTML não valida. Antes que alguém reclame, vá tentar validar código num ambiente como o deles, do Terra ou do HSBC, com integração com conteúdo de diversas fontes, de diversas equipes diferentes. Aliás é isso que torna o projeto interessante. É muito fácil trabalhar com padrões quando você controla o conteúdo, como deve ser o trabalho da maioria dos leitores aqui. Quando você tem uma coleção de sites num mesmo portal, com conteúdo vindo de diversas fontes diferentes, qualquer coisa que você resolva fazer é bem mais complicada.

Converteram todos os sites do portal que são conteúdo do CMS da EPTV. Apenas os sites de parceiros ficaram como estavam. É um volume enorme de trabalho, que a equipe da EPTV fez muito rapidamente. Não interromperam em nenhum momento os serviços, não tiraram o CMS do ar e não pararam de publicar notícias. Conteúdos como a previsão do tempo, a publicidade e aquela barra de compras são fornecidos por parceiros. A publicidade, por exemplo, não está aparecendo aqui no Firefox, culpa do javascript do fornecedor da publicidade. E eles conseguiram ajustar todo o conteúdo do site e o conteúdo de parceiros, além do conteúdo multimídia da própria EPTV, de maneira exemplar.

Ah, vocês devem ter notado o ícone de RSS lá. Excelente, não?

Mas a parte mais interessante está por trás desse trabalho. Eles tem um CMS desenvolvido in-house, que é usado pelas equipes de jornalistas da EPTV e por quem mais tenha que publicar conteúdo ali dentro. Modificamos todo o sistema de integração do CMS com o site, criando um motor de templates baseado em XSLT. O site se tornou muito mais leve e fácil de administrar, e eles resolveram um dos problemas com o antigo sistema, o de encontrar mão-de-obra capacitada para administrar os templates na antiga linguagem. Como XSLT é uma linguagem padrão, é fácil encontrar alguém no mercado capaz de trabalhar com ela. A forma como construímos o publicador, com XSLT em cima de um XML que é único para todo o portal, em seguida CSS em cima do resultado, é separação entre layout e conteúdo também para o publicador. Deu à equipe uma flexibilidade única. O RSS, por exemplo, foi criado em uns dez minutos. É o tempo que leva também para se criar um novo template, um novo formato de página.

Parabéns à equipe da EPTV! Foi realmente um privilégio trabalhar com vocês.

**PS:** Não esquecemos do assunto anterior, da seção de convertidos. É que estamos, eu e o Diego, trabalhando muito, muito mesmo. Aquela carta chegou em péssima hora. Estou ansioso para responder aos comentários de vocês, só estou completamente sem tempo.

**PS2:** Não quero contar apenas as histórias de sucesso de clientes da Atípico aqui. Se você trabalhou em algum projeto que considera exemplar por algum motivo e gostaria de ver sua história publicada aqui, por favor, mande pra gente. Vamos aprender juntos.

 [1]: http://eptv.globo.com/