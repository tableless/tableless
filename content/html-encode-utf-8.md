---
title: 'HTML: Encode UTF-8'
author: Alan Cezar
type: post
date: 2015-05-01
excerpt: Entendendo um pouco mais sobre encode e como funciona o UTF-8.
url: /html-encode-utf-8/
categories:
  - HTML
  - HTML5
  - Técnicas e Práticas
tags:
  - encode
  - html
  - utf-8

---
Há uns 7 anos atrás o Diego Eis publicou [aqui][1] um artigo sobre o assunto. Vou fazer uma nova abordagem.

Sabe quando sua página troca acentuações por caracteres bem loucos? Este é um problema simples de explicar e vou tentar mostrar as regras que se aplicam quando o browser faz o download de um HTML, como escolher um encode e como usá-lo.

Existem três formas de declararmos o encode do arquivo:

### 1 &#8211; Via cabeçalho HTTP

<pre>Content-Type: text/html; charset=utf-8</pre>

Esse aí é o cara que manda. Se declararmos o encode no parâmetro _charset_ do _Content-Type_, as outras duas opções serão ignoradas. Hoje em dia a customização no servidor é praticamente zero por parte do desenvolvedor, pois a maioria dos servers e banco de dados já vem com essa configuração.

### 2 &#8211; Via Meta Tag

<pre>&lt;!-- HTML 4 --&gt;
&lt;meta http-equiv="Content-Type" content="text/html; charset=utf-8"&gt;
&lt;!-- HTML5 --&gt;
&lt;meta charset="utf-8"/&gt;</pre>

Acredito que a maioria dos desenvolvedores utilizam essa técnica. Muitas vezes já vem nos snnipets que encontramos em nosso editores e ou até mesmo naqueles templates gerados via scaffolding (ex.: yoeman).

É uma boa prática colocar ele logo após a abertura da tag html. Pois se o encode não estiver disponível no cabeçalho da requisição, o browser irá procurar por essa informação nos primeiros 1024 bytes do arquivo. Se ele não encontrar, será utilizado o UTF-8.

Segundo a w3techs.com que é especialista em um monte de pesquisas sobre a web, o formato UTF-8 é utilizado em cerca de 80% das páginas web. Mas vamos falar um pouco mais do UTF-8 depois.

### 3 &#8211; Via XML

<pre>&lt;?xml version="1.0" encoding="utf-8"?&gt;</pre>

Esse cara só serve para páginas XHTML e deve ser colocado antes do DOCTYPE.

### Por que tanto UTF-8?

Em 2014 foi constatado que cerca de 83,6% das páginas web estavam utilizando esse encode. Sua popularização se deu pelo fato dele reconhecer bastante caracteres (tipo uns 65.536).

Tem uma galera por aí usando o ISO-8859-1 por que ele é mais performático chegando á cada caractere pesar metade do seu correspondente no UTF-8. Mas aí você fica com algumas opções de caracteres á menos (você se limita á usar 256 caracteres diferentes. Pouco né?).

Esse segundo encode apareceu nesse mesmo relatório em segundo lugar com 8.3% das páginas. Ele não é uma péssima opção, uma vez que ele cobre todos os caracteres do nosso idioma. Mas se você for trabalhar em uma aplicação com chances de rolar internacionalização, aconselho á usar o UTF-8 pra ter uma transição natural sem maiores problemas.

### Bala de Prata?

> Tudo isso é muito chato ou demais pra minha cabeça. Quero algo mais simples.

Então tá. Vamos ver&#8230;

Você pode ignorar qualquer encode e utilizar entidades HTML.

Escrever _Sab&atilde;o_ garante que o usuário vai ler _Sabão_ e evita que algum navegador por aí mostre na tela _SabÃ£o_ ou _Sab�o_.

> Legal! Quero ver dar errado agora depois dessa!

Mas calma jovem, tudo tem um preço. Dá uma olhada na lista de pontos negativos:

  1. Além de escrever mais caracteres você terá que aprender todas essas entidades (ou a maioria).
  2. Uma &#8220;alteraçãozinha de 2 minutos&#8221; pra um desenvolvedor que não está muito familiarizado se torna algo com uma certa complexidade desnecessária.
  3. Sua semântica diminui, uma vez que o conteúdo do seu código deixa de ter uma alta facilidade de entendimento.
  4. Isso vai exigir mais caracteres, o que aumenta <del>nem que seja só um pouquinho</del> o tráfego na rede.
  5. Não é uma técnica muito popular devido aos pontos negativos anteriores á esse.
  6. Você corre risco de sofrer bullying no trampo depois de seus colegas lerem teu código.

Eu até sei um ou outro de cabeça, tipo o _&ccedil;_ e o _&_, mas prefiro mil vezes digitar _ç_ e o _&_. Mais fácil né não?

Referências:

  * <a href="http://wiki.locaweb.com/pt-br/C%C3%B3digos_HTML_para_caracteres_acentuados" target="_blank">Locaweb &#8211; Códigos HTML para caracteres acentuados</a>
  * <a href="http://wiki.locaweb.com/pt-br/Como_resolver_problemas_de_acentua%C3%A7%C3%B5es_em_seu_site" target="_blank">Locaweb &#8211; Como resolver problemas de acentuação no seu site</a>
  * <a href="http://w3techs.com/technologies/overview/character_encoding/all" target="_blank">w3techs.com &#8211; Levantamento sobre o uso do UTF-8 na web</a>

 [1]: http://tableless.com.br/charsets-e-encodes-tabelas-de-caracteres/