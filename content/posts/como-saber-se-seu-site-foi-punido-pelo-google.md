---
title: Como saber se seu site foi punido pelo Google
author: Carina Andrade
type: post
date: 2014-03-14
excerpt: 'As páginas de um site não aparecem nas buscas ou perderam posições no ranking do buscador: Saiba como identificar se o site sofreu uma punição do Google.'
url: /como-saber-se-seu-site-foi-punido-pelo-google/
dsq_thread_id: 2324919310
categories:
  - SEO
tags:
  - buscadores
  - google
  - search

---
Muitas pessoas percebem uma queda nas visitas do seu site com origem no Google ou até mesmo notam que já não aparecem mais tão bem posicionados para uma determinada busca. É aí que vem aquela dúvida, será que o site foi punido pelo Google? Como saber?

Existem dois tipos de punição: a que rebaixa as páginas na busca (Exemplo: uma página que aparecia na 1ª posição dos resultados orgânicos vai para a 30ª posição.) e a que remove completamente um site ou uma determinada página dos resultados.

A primeira coisa a ser feita é conferir se a página está indexada no Google. Para isso, é possível utilizar o próprio buscador. Existe uma série de operadores de busca (buscar em títulos de páginas e em URLs são exemplos) que ajudam a filtrar os resultados. O que vamos usar para descobrir se um site está indexado ou não é o **site:**. Buscando no Google por **site:seusite.com.br**, todos os resultados para esse domínio serão exibidos.

<span style="line-height: 1.5em">Se o site não tem nenhuma página (ou tem poucas) indexada no Google, é preciso partir para uma investigação. Existem duas hipóteses prováveis: 1) Seu site está sendo bloqueado ou apresenta algum erro e o Google não consegue acessá-lo; 2) Seu site foi punido pelo Google (essa é a opção que não queremos!).</span>

## Como um site pode estar impedindo o rastreio do Google

<span style="line-height: 1.5em">Você não é obrigado a compartilhar seu conteúdo com os usuários do Google. E é pra isso que existem algumas opções para não permitir que os robôs de busca (tanto do Google, como do Bing, Yahoo!, etc) acessem as páginas de um site.</span>

O recurso que gerencia isso é o **robots** do site, que pode ser um arquivo de texto (.txt) no servidor, como também uma meta tag no HTML das suas páginas (ou as duas coisas). Por isso é importante revisar todas essas possibilidades antes de se desesperar achando que levou uma punição. Muitas vezes o Google simplesmente não consegue acessar as páginas e por isso não as indexa no mecanismo.

Considere isso como uma segurança, afinal de contas você pode não querer exatamente todas as suas páginas nos resultados de busca, e esse recurso é uma ótima forma de controlar isso. As URLs que necessitam login para serem acessadas, por exemplo, geralmente não são boas páginas para os visitantes que vêm do Google. O que quero dizer é que o arquivo robots não foi feito somente para atrapalhar a indexação de sites, isso acontece quando algo é mal configurado. A intensão do robots é justamente dar a opção de aparecer ou não nos resultados de busca.

### Robots.txt

O **robots.txt** é um arquivo de texto com instruções simples que são lidas pelos robôs de busca antes de qualquer visita ao seu site. Outras opções também podem ser úteis no robots.txt, como a localização do sitemap do site, para facilitar o rastreio dos robôs. Veja como exemplo o robots.txt do Tableless: <http://tableless.com.br/robots.txt>

Se você não conhece a estrutura do robots.txt, mas quer saber se o arquivo está bloqueando alguma coisa no seu site, você pode testá-lo de forma fácil na [Google Webmaster Tools][1], que falaremos mais adiante,

### Meta tag Robots

A meta tag Robots também tem a mesma função de bloqueio de robôs do arquivo txt, ela é usada entre as tags <head> do HTML, dessa forma:

<pre>&lt;meta name="<strong>robots</strong>" content="<strong>noindex</strong>, follow" /&gt;</pre>

Dessa forma, a tag indica aos robôs de busca que essa página não deve ser indexada (noindex).

Caso você encontre essa tag indicando noindex, esse é o motivo pela página não estar nos buscadores. Lembrando que essa tag é referente apenas à página onde está contida. Para bloquear todas as páginas de um site, essa tag deve aparecer em todas as páginas.

Visto isso e certificando-se de que não há bloqueio aos robôs de busca, existem algumas formas de entender se o site foi ou não punido. Uma ferramenta grátis e com muitos recursos que ajuda nessa investigação é a [Google Webmaster Tools][1], ou ferramentas do Google para Webmasters. Os recursos são muitos, daria assunto para mais um artigo, mas consultando alguns deles já é possível ter uma ideia do que está acontecendo com seu site.

## Como usar o Google Webmaster Tools para investigar uma possível punição?

Além de consultar o volume de impressões que o site está tendo no Google, é possível monitorar os links que apontam para o site, testar os snippets e utilizar muitos outros recursos nas ferramentas para Webmasters. Existe uma opção bem específica criada recentemente que promete alertar quando um site foi punido manualmente (isso acontece quando o Google identifica compra de links, por exemplo, que é uma ação não recomendada por eles). A imagem a seguir mostra a localização do recurso na ferramenta:

[<img class="size-full wp-image-41265 aligncenter" alt="Google Webmaster Tools - Ações Manuais" src="http://tableless.com.br/uploads/2014/02/google-webmaster-tools-acoes-manuais.png" width="634" height="526" srcset="uploads/2014/02/google-webmaster-tools-acoes-manuais.png 634w, uploads/2014/02/google-webmaster-tools-acoes-manuais-202x168.png 202w, uploads/2014/02/google-webmaster-tools-acoes-manuais-373x310.png 373w, uploads/2014/02/google-webmaster-tools-acoes-manuais-400x331.png 400w" sizes="(max-width: 634px) 100vw, 634px" />][2]

Outra maneira de entender o que está acontecendo com seu site é através do menu Rastreamento > Erros de Rastreamento. Esse relatório da ferramenta mostra erros de DNS, servidor e bloqueio por robots (que falamos anteriormente). Verificando a existência desses erros já podemos ter bons insights de possíveis causas para nossa queda nas buscas.

Se você utilizar o recurso de sitemaps, enviando os sitemaps do seu site através da ferramenta, vai poder acompanhar quantas páginas, de todas contidas no arquivo, estão indexadas. Isso fornece uma informação muito importante, pois as URLs que estão no sitemaps, mas não estão indexadas, provavelmente estão bloqueadas ou gerando algum erro. No exemplo abaixo, a ferramenta mostra que apenas 7% das páginas do sitemap estão indexadas. A própria ferramenta alerta quais URLs estão com problema e por quê.

[<img class="size-full wp-image-41266 aligncenter" alt="Google Webmaster Tools - Sitemaps" src="http://tableless.com.br/uploads/2014/02/google-webmaster-tools-sitemaps.png" width="636" height="479" srcset="uploads/2014/02/google-webmaster-tools-sitemaps.png 636w, uploads/2014/02/google-webmaster-tools-sitemaps-223x168.png 223w, uploads/2014/02/google-webmaster-tools-sitemaps-411x310.png 411w, uploads/2014/02/google-webmaster-tools-sitemaps-400x301.png 400w" sizes="(max-width: 636px) 100vw, 636px" />][3]

## Se não existem erros nem bloqueios

Se você verificou tudo isso e não encontrou erros e nem bloqueios por robots, é bem possível que seu site esteja mesmo sob uma penalização do Google. Nesse caso será necessário fazer uma revisão completa no seu site, interna e externamente. É importante seguir as [Diretrizes para Webmasters][4] do Google no desenvolvimento do site e verificar se não existem links de má qualidade ou que podem ser considerados spam.

Ultimamente o Google vem sendo bem rígido quanto ao trabalho de Link Building (conquistar links para ganhar popularidade/autoridade). Verifique os sites que estão linkando para o seu, os textos dos links, quantidade e certifique-se que o Google não o puniu por algum deles. Criar diversos blogs e sites só para linkar para o seu também é passível de punição.

Depois de toda a investigação e correções feitas, você pode tentar acelerar a reindexação do seu site através da solicitação de reconsideração ao Google: <https://support.google.com/webmasters/answer/35843?hl=pt-BR>

Agora é só manter a qualidade do seu conteúdo na Web e continuar monitorando seu site.

 [1]: https://www.google.com/webmasters/tools/home?hl=pt-BR
 [2]: http://tableless.com.br/uploads/2014/02/google-webmaster-tools-acoes-manuais.png
 [3]: http://tableless.com.br/uploads/2014/02/google-webmaster-tools-sitemaps.png
 [4]: https://support.google.com/webmasters/answer/35769?hl=pt-BR