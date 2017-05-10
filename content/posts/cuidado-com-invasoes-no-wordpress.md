---
title: Cuidado com invasões no WordPress
author: Paulo Rodrigues
type: post
date: 2012-04-20
excerpt: O WordPress não é perfeito e possui falhas, tome cuidado com possíveis invasões.
url: /cuidado-com-invasoes-no-wordpress/
tweetbackscheck:
  - 1356399447
shorturls:
  - 'a:3:{s:9:"permalink";s:31:"http://tableless.com.br/?p=5943";s:7:"tinyurl";s:26:"http://tinyurl.com/dyocp2d";s:4:"isgd";s:19:"http://is.gd/UkH7QV";}'
twittercomments:
  - 'a:0:{}'
dsq_thread_id: 657472274
categories:
  - Wordpress
tags:
  - 2012
  - cotidiano
  - Wordpress

---
Um dos principais gerenciadores de conteúdo, o WordPress, possui ainda possui algumas falhas. É necessário ficar atento e tomar cuidado para qualquer situação.

Há duas semanas, passei sérios problemas com o WordPress, com o blog [Papo de Buteco][1]. Nunca tinha passado por uma situação parecida com essa, e por isso que tomar cuidado antes de agir.

## Como verifiquei

Por otimizar o site, sempre estou verificando como as páginas do blog estão se comportando no Google. Busquei por **site:papodebuteco.net** para verificar todas as minhas páginas indexas no Google, e obtive o seguinte resultado:

[<img class="alignnone size-medium wp-image-5948" src="http://tableless.com.br/uploads/2012/04/serp-papo-de-buteco-300x280.png" alt="" width="300" height="280" srcset="uploads/2012/04/serp-papo-de-buteco-300x280.png 300w, uploads/2012/04/serp-papo-de-buteco.png 800w" sizes="(max-width: 300px) 100vw, 300px" />][2]

Ao primeiro olhar, já observei as tags de título das páginas estavam totalmente diferentes, no mínimo estranho, não é? Comecei a estudar a situação, e conclui que neste caso, aconteceu uma espécie de **[Cloaking][3]**, que reproduzia a página normal para o usuário e outra página para o Google.

De primeira, achei que eram os plug-ins instalados no site que estavam fazendo isso, mas até que o Google me enviou a seguinte mensagem para o **[Web Master Tools][4]**** **do site:

[<img class="alignnone size-medium wp-image-5951" src="http://tableless.com.br/uploads/2012/04/mensagem-google-300x211.png" alt="" width="300" height="211" srcset="uploads/2012/04/mensagem-google-300x211.png 300w, uploads/2012/04/mensagem-google.png 1000w" sizes="(max-width: 300px) 100vw, 300px" />][5]

Ao acessar o link indicado na mensagem, e realmente foi mostrada uma página com um conteúdo não relacionado ao blog.

## Solucionando o problema

O que precisa ser feito é: **Reinstalar o WordPress para atualizar seus arquivos.**

**No próprio painel do gerenciador**, é possível fazer essa reinstalação, então nada de apagar todos os arquivos do FTP, enviar novamente e reintegrar com o banco de dados.

Em seu painel de adiminstração, procure no menu de navegação por **Atualizações** e siga como na imagem abaixo:

[<img class="alignnone size-medium wp-image-5944" src="http://tableless.com.br/uploads/2012/04/menu-navegacao-128x300.png" alt="" width="128" height="300" srcset="uploads/2012/04/menu-navegacao-128x300.png 128w, uploads/2012/04/menu-navegacao.png 286w" sizes="(max-width: 128px) 100vw, 128px" />][6][<img class="alignright size-medium wp-image-5953" src="http://tableless.com.br/uploads/2012/04/reinstalando-wordpress-300x164.png" alt="" width="300" height="164" srcset="uploads/2012/04/reinstalando-wordpress-300x164.png 300w, uploads/2012/04/reinstalando-wordpress.png 800w" sizes="(max-width: 300px) 100vw, 300px" />][7]

Depois disso, acessei a página que o Google indicou na mensagem e não tive mais problemas, a página foi carregou com seu conteúdo real.

Para confirmar, você pode tirar a _“prova real”_ **buscando como o Googlebot**, que é uma ferramenta encontrada no Google Webmaster Tools.

[<img class="size-medium wp-image-5945 alignleft" src="http://tableless.com.br/uploads/2012/04/gwmt-1-300x156.png" alt="" width="300" height="156" srcset="uploads/2012/04/gwmt-1-300x156.png 300w, uploads/2012/04/gwmt-1-1024x535.png 1024w, uploads/2012/04/gwmt-1.png 1423w" sizes="(max-width: 300px) 100vw, 300px" />][8]

&nbsp;

&nbsp;

&nbsp;

&nbsp;

&nbsp;

Ao clicar em **“Processando”** e estiver lendo a página do jeito que deveria ler, com o seu código fonte real, pode ter certeza que o problema foi resolvido.

## Conclusão

Não se sabe ao certo ainda como essa invasão se manifestou no blog, mas é bom ficar atento a qualquer tipo de propagação estranha relacionada a seu site. O tipo de invasão apresentado no artigo não é único, podem existir outros casos espalhados. A vulnerabilidade pode também está relacionada com o servidor onde o seu site está hospedado.

As páginas que não entraram no cache do Google depois que o problema foi solucionado, ainda se encontram com o mesmo conteúdo da invasão, se vocês procurarem, ainda acharam algumas páginas assim.

Apesar de tudo isso, **não houve oscilação com o número de visitas do site**, ele se mantéu estável. E o **número de _backlinks_ apontados para as páginas do blog cresceu**, mas com um textos âncora sem relação ao conteúdo real do blog.

O **Cloaking** é considerada uma técnica de blackhat pelo Google, caso o problema não fosse solucionado a tempo, o blog poderia ser sofrer algum tipo de punição, veja mais em: <http://support.google.com/webmasters/bin/answer.py?hl=pt-BR&answer=66355>.

Se o seu site ainda não é integrado ao Google **[Web Master Tools][9]**, acesse agora e integre! É simples, fácil, e oferece informações importantes para o seu site. Para completar e evitar que algo semelhante aconteça, confira **[dicas para aumentar a segurança no WordPress][10]**.

Quero aproveitar o espaço para agradecer [Leandro Lopes][11] (dono do blog Papo de Buteco), que autorizou a postagem de exemplos relacionados ao blog dele. É importante relatar o que aconteceu, ainda mais com casos verídicos, pois pode acontecer com qualquer um.

 [1]: http://papodebuteco.net
 [2]: http://tableless.com.br/uploads/2012/04/serp-papo-de-buteco.png
 [3]: http://www.mestreseo.com.br/black-hat/cloaking-aplicacao-scripts-blackhat-e-questoes-eticas "Cloaking"
 [4]: https://www.google.com/webmasters/tools
 [5]: http://tableless.com.br/uploads/2012/04/mensagem-google.png
 [6]: http://tableless.com.br/uploads/2012/04/menu-navegacao.png
 [7]: http://tableless.com.br/uploads/2012/04/reinstalando-wordpress.png
 [8]: http://tableless.com.br/uploads/2012/04/gwmt-1.png
 [9]: https://www.google.com/webmasters/tools/
 [10]: http://webperfeita.com/10-dicas-para-aumentar-a-seguranca-do-wordpress/
 [11]: http://twitter.com/#!/papodebuteco