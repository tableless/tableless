---
title: Redesign e SEO
author: Douglas Faria
type: post
date: 2013-09-24
excerpt: ' Evite problemas com sua campanha na hora de implementar a cara nova do seu site'
url: /redesign-seo/
dsq_thread_id: 1786520632
categories:
  - SEO
tags:
  - google
  - projetos
  - SEO

---
É muito bom quando damos uma cara nova a algum projeto. Trazemos novas ideias, conceitos diferentes e novidades. Muitas vezes isso é uma injeção de ânimo. Até porque, a ideia é que a mudança nos faça crescer.

Pois é! Falando do seu site, isso pode trazer problemas quando decidimos mudar e não prestamos atenção nos detalhes.

O que acontece é que, as vezes, deixamos erros bobos atrapalhar (e muito) a nossa campanha. Links quebrados, redirecionamentos errados ou sem fazer, cabeçalho mal estruturado, entre outras coisas.

É altamente recomendável que você tenha o acompanhamento de um analista de SEO para fazer isso. Qualquer bobeira pode lhe custar caro.

Pensando nisso, separei aqui algumas dicas para você mandar bem no design e seguir progredindo com sua campanha!

## 1. Arquitetura

Tenha muito cuidado ao fazer alguma alteração na arquitetura do seu site. Isso pode ser muito prejudicial se você não faz o mapeamento de forma correta. O Google trabalha com índices e mapeia toda a sua arquitetura. Quando você muda, é necessário tratar essa mudança com redirecionamentos e cuidar para perder a autoridade já conquistada desses links.

## 2. Linkagem Interna

A linkagem interna assume um papel muito importante no SEO. Ela ajuda os motores de busca a entender a arquitetura do seu projeto. Além disso, influencia na reputação de páginas, aumentando o PageRank (PR).

Basta você, de forma estratégica e contextualizada, colocar links de páginas mais reputadas, com maior PR em páginas em muita autoridade. Isso fortalecerá páginas novas e que possuem uma importância menor na sua campanha.

Se você fizer o redesign do seu site, de forma que prejudique sua linkagem interna, sua campanha perderá força.

## 3. URLS E Redirecionamentos

Aí está um grande vilão de implementação de projetos. Já vi e já tive problemas com isso. Se você não se preocupar em atualizar links e trabalhar sua URL, isso irá te dar uma grande dor de cabeça. Ao fazermos a mudança de arquitetura por exemplo, temos que informar ao motor que uma determinada página agora tem outro endereço.  Veja, se você tinha a seguinte estrutura:

http://www.seudominio.com.br/**o-que-fazemos**/marketing-digital

Por algum motivo e aproveitando a mudança de design no site, você decidiu mudar para:

http://www.seudominio.com.br/**servicos**/marketing-digital

Ao decidir fazer essa mudança, você deve se preocupar com erros 404, pois o Google irá buscar aquela página e não a encontrará. Você pode resolver isso com um redirect 301 via htaccess ou em PHP, por exemplo:

## Via htaccsess:

redirect 301 /**o-que-fazemos**/marketing-digital http://www.seudominio.com.br/**servicos**/marketing-digital

## Via PHP:

<pre class="lang-php">&lt;?php

Header( “HTTP/1.1 301 Moved Permanently” );

Header( “Location: http://www.seudominio.com.br” );

?&gt;
</pre>

Não vou entrar em detalhes, isso ficará para outro artigo, mas já orienta. A ideia é você fazer uma lista de links que não existem mais ou irão mudar e trata-los. Assim, você conserva a autoridade dessa página e evita que os motores de busca te penalizem com erros de Page Not Found. Leia mais sobre [Códigos de cabeçalho HTTP aqui.][1]

## 4. Google Analytics

Outro erro comum é esquecer de colocar os códigos de acompanhamento do analytics. Atente-se para não se esquecer, pois caso isso aconteça você perderá as informações de acesso do seu site nesse período.

## 5. Links patrocinados

Pensando nas URLs, não se esqueça de atualizar os links dos seus anúncios, seja Adwords ou Facebook Ads. Atualize os seus anúncios para evitar links quebrados e uma má impressão em relação à sua marca. E não se esqueça, se os links estiverem errados, você perde o click e o cliente!

## 6. Títulos Descriptions e Metatags

Cheque os títulos do seu site e não deixe nenhum passar em branco. Fique atento aos limites considerados para um título otimizado: no máximo 70 caracteres, se possível começando com a palavra-chave.

As metatags (algumas delas) também são de extrema importância. Destaque aqui para algumas:

**Viewport** – se você usa design responsivo com media queries, vale a pena lembrar.

## Description

– Não é fator relevante (oficialmente) de posicionamento, mas ajuda muito na conversão. Ela pode, mas não deve possuir mais do que 155 caracteres, pois o Google corta o restante. Não se esqueça, elas precisam ser chamativas, interessantes, informativas, curiosas e com um toque de call-for-action. Alguns exemplos de 

## Call-to-action: 

  * Clique e Confira;
  * Conheça as vantagens;
  * Cadastre-se;
  * Veja o preço;
  * Somente hoje;
  * Use a sua criatividade 😉

## 7. Erros 404

Já destacamos aqui os problemas com a URL, mas é sempre bom falar do erro 404. Checar se você possui links quebrados, retornando erro 404 é obrigação, mas você pode configurá-la a seu favor.  É importante separar erros vindos de links quebrados de links que realmente não existem mais e foram tratados e para estes você pode usufruir do acesso do usuário. Sugira links para páginas estratégicas, divulgue conteúdos oportunos e ganhe a permanência do usuário.

## 8. Atualização do Sitemap.xml

Esse aqui é o cara. Não deixe a manutenção do seu sitemap de lado. Ele é um auxiliar de luxo do Google e realmente faz a diferença. Mantenha todos os ativos linkaveis sempre atualizados, seja organizado e monitore possíveis erros.

Para verificar a forma correta de se escrever sitemaps, você pode consultar o [sitemaps.org][2]

Não deixe de fazer o sitemap de vídeos, imagens e links. Organização nunca é de mais!

## 9. E-mail marketing

Se você trabalha com newsletter, não se esqueça de mexer nos templates e adequá-los ao novo design do site, além de atualizar o rodapé e os seus links.

Como estamos falando de marketing digital, uma dica boa é sempre se manter atualizado quanto ao seu público alvo. Conhecer os seus usuários é essencial para definir melhor as estratégias de criação de layout, influência das cores, criação de botões e iscas digitais (para quem usa!).

Bom pessoal, é isso aí! Existem vários pontos que podem ser citados aqui e eu fiz uma seleção pensando no SEO. A ideia é passar para vocês alguns pontos que eu acredito serem importantes e que muitos de nós as vezes deixam passar desapercebidos e, por essa desatenção, perdemos um valioso trabalho construído, sem contar o tempo!

Valew pessoal e até o próximo artigo!

 [1]: http://pt.wikipedia.org/wiki/Anexo:Lista_de_c%C3%B3digos_de_status_HTTP
 [2]: http://www.sitemaps.org/