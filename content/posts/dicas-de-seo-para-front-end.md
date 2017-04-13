---
title: Dicas de SEO para Front-end
author: Gabriel Azevedo
type: post
date: 2015-02-19
excerpt: 'Sabemos que SEO é uma forte arma que nos possibilita alcançar um bom posicionamento nos sites de busca e aqui vai algumas dicas para isso. '
url: /dicas-de-seo-para-front-end/
categories:
  - SEO
tags:
  - palavras chave
  - SEO

---
## 1 &#8211; Webmaster Tools

[Webmaster Tools][1] é uma ferramenta disponibilizada pelo Google e através dela você pode medir o desempenho de seu site, ter informações bem completas de erros e melhorias e muito mais para você que queira investir em otimização.

  * Mas, como começo a utilizar esta ferramenta?

Simples! Você só precisa dar permissão ao Webmaster Tools a seu site, enviando um arquivo HTML para o FTP (é o método mais recomendado), ou utilizando uma meta tag ou outros tipos de verificação.

Pronto, ja fez isto? Agora você já pode ver quais os erros o Google está apontando em seu site, ele vai te mostrar tudo que precisa arrumar ou melhorar, e agora só depende de você.

E no próprio Webmaster Tools você tem acesso ao Page Speed do Google, que é uma ferramenta show de bola, que vai te dar um relatório completo do seu site.

Vai lá e da uma olhadinha em tudo isso.

## 2 &#8211; A tag Title e Description

A tag **<title>** é uma das coisas que o Google mais da relevância na otimização do seu site, sempre planeje bem o que você vai colocar no titulo de sua página, para que seu cliente saiba o que ele vai encontrar entrando nela.

A tag **<description>** também é um dos passos mais importantes na otimização de seu site, e é ele que vai levar a seu cliente uma breve descrição do que ele vai encontrar entrando em sua página.

Ah vocês lembram da nossa ferramenta ali em cima, o Webmaster Tools? Ele também nos ajuda bastante com nossas tags Title e Description, entrando no Webmaster Tools indo em **Aspecto da pesquisa > Melhorias de HTML**, lá você encontrará alguns erros reportados, como:

Quais são as páginas que tem meta tag **<title>** e **<description>** duplicadas, longas demais, curtas demais ou até mesmo as páginas que não possuem title, é só você entrar la e ajustar.

## 3 &#8211; URL amigável

Uma regra muito importante no SEO é utilizar URLs amigáveis em sua página. Como:

**http://www.meusite.com.br/nome-do-produto** e não utilizar **http://www.meusite.com.br/prod001**

Pois o Google lê sua URL para saber do que se trata aquela página antes mesmo de ler o documento.

Então vamos ter atenção nisso ai também.

## 4 &#8211; Imagens

As imagens do seu site possuem nomes amigáveis ou não? Quando você vai acrescentar alguma imagem em seu site, você se preocupa com o nome dela?

O Google não sabe o que é aquela imagem que você acrescentou, ele só vai entender a partir do momento que você falar para ele, que imagem é esta.

Use nomes detalhados e informativos, como:

**nome-do-produto.jpg** e não **prod001.jpg**

Use o atributo **ALT** em suas imagens, para falar para o Google o que significa aquela imagem, para que ele entenda melhor sobre ela. Como:

<img src=“nome-do-produto.jpg” **alt=“O significado de sua imagem”**>

Pronto! Você acaba de ganhar alguns pontinhos a mais com nosso amigo Google.

## 5 &#8211; Tempo de carregamento

Os usuários querem acessar sites mais rápidos e o Google também gosta bastante de sites rápidos, então comece a se preocupar se seu website está ou não com um bom tempo de carregamento.

  * Como podemos diminuir o tempo de carregamento do site?

**Duas dicas são:**

  * Reduzir seus arquivos CSS e JS, retirando comentários e espaços.
  * Comprimir o tamanho de suas imagens

E podemos fazer isso utilizando um automatizador de tarefas, o meu favorito é o [Gulp][2]

Você também pode utilizar o Page Speed que você terá informações mais precisas sobre isso.

## 6 &#8211; Utilize CSS Sprites

[CSS Sprites][3] é uma técnica onde podemos combinar várias imagens em uma só, procurando diminuir o número de requisições para o servidor.

Um exemplo que eu gosto bastante de usar é:

  * Supondo que você tenha que ir a padaria comprar 10 pães, mas você tem que trazer 1 por 1. Seria muito cansativo e mais demorado concorda? Mas nós podemos trazer todos estes pães de uma vez só. A mesma coisa é com as requisições no servidor, é muito mais cansativo e demorado para o servidor trazer imagem por imagem, sendo que podemos trazer todas de uma vez só.

O próprio Google utiliza CSS Sprites.

[<img class="alignnone size-medium wp-image-47162" src="http://tableless.com.br/uploads/2015/02/css-sprites-265x107.png" alt="css-sprites" width="265" height="107" srcset="uploads/2015/02/css-sprites-265x107.png 265w, uploads/2015/02/css-sprites.png 356w" sizes="(max-width: 265px) 100vw, 265px" />][4]

## 7 &#8211; Websites responsivos

Não podemos criar nossos sites pensando somente em se ele vai funcionar somente em desktop ou somente em um tipo de tela, ter um site acessível em todas as plataformas é muito importante, pois acessos por dispositivos móveis vem crescendo bastante e isso não irá parar.

Então preocupe se o seu website é acessível a todas as telas, seja ela desktop ou mobile, isto é um dos fatores que conta bastante para o Google indexar seu site.

Essas são somente algumas dicas para que você venha ter mais vontade em aplicar mais técnicas de SEO em seus websites.

 [1]: http://www.google.com.br/webmasters/ "Webmaster"
 [2]: http://tableless.com.br/gulp-o-novo-automatizador/ "Automatizador de tarefas"
 [3]: http://tableless.com.br/css-sprites/ "CSS Sprites"
 [4]: http://tableless.com.br/uploads/2015/02/css-sprites.png