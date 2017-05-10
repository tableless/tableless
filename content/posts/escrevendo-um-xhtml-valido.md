---
title: Escrevendo um XHTML válido
author: Diego Eis
type: post
date: 2007-12-06
url: /escrevendo-um-xhtml-valido/
aktt_notify_twitter:
  - no
tweetbackscheck:
  - 1356453532
shorturls:
  - 'a:3:{s:9:"permalink";s:50:"http://tableless.com.br/escrevendo-um-xhtml-valido";s:7:"tinyurl";s:26:"http://tinyurl.com/3zwstgf";s:4:"isgd";s:19:"http://is.gd/IIlPd6";}'
twittercomments:
  - 'a:0:{}'
dsq_thread_id: 503037686
categories:
  - Artigos
  - HTML
  - Técnicas e Práticas
  - Tecnologia e Tendências
tags:
  - CSS
  - doctype
  - padroes web
  - Semântica
  - tableless
  - tutorial
  - w3c
  - xhtml
  - xml

---
Acho que todos já ouviram falar de Web Semântica, para quem não ouviu, em poucas palavras é: Um projeto para organizar e estruturar a informação da WEB.

Ter uma Web com as suas informações todas &#8220;organizadas&#8221; é extremamente importante, isso facilita uma busca pela Web por informações mais precisas.
  
Para que seu arquivo possa ser lido por máquinas além de humanos é muito importante que você escreva um XHTML válido, com isso você está fazendo com que as informações do seu site fique mais acessível para as buscas, contribuindo para o projeto e principalmente melhorando as visitas do seu site.

### DOC o que?!

O Doctype (Document Type Definition, vulgo DTD) é a primeira coisa que se deve escrever em um arquivo XHTML, ele vai na PRIMEIRA LINHA do seu documento, se você quiser ter um XML Válido, não devemos esquecê-lo, ele serve para informar ao browser que tipo de documento será visualizado, ok?

Existem 3 tipos:

  * **Strict**: Este tipo é usado quando você fez um código 100% XHTML, sem erros, deve ser escrito assim:
  
    <!DOCTYPE html
  
    PUBLIC &#8220;-//W3C//DTD XHTML 1.0 Strict//EN&#8221;
  
    &#8220;http://www.w3.org/TR/xhtml1/DTD/xhtml1-strict.dtd&#8221;>
  * **Transitional**: Este é o modo mais usado, você o usa quando está começando a migrar do nosso amigo HTML para o poderoso XHTML, sua sintaxe é:
  
    <!DOCTYPE html
  
    PUBLIC &#8220;-//W3C//DTD XHTML 1.0 Transitional//EN&#8221;
  
    &#8220;http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd&#8221;>
  * **Frameset**: É usado quando você está utilizando FRAMES em seu site, se escreve assim:
  
    <!DOCTYPE html
  
    PUBLIC &#8220;-//W3C//DTD XHTML 1.0 Frameset//EN&#8221;
  
    &#8220;http://www.w3.org/TR/xhtml1/DTD/xhtml1-frameset.dtd&#8221;>

Exemplo:
  
<!DOCTYPE html
  
PUBLIC &#8220;-//W3C//DTD XHTML 1.0 Strict//EN&#8221;
  
&#8220;http://www.w3.org/TR/xhtml1/DTD/xhtml1-strict.dtd&#8221;>
  
<html>
  
<head>
  
<title></title>
  
</head>
  
<body>
  
&#8230;
  
</body>
  
</html>

### Feche TODAS as tags

Quem já escreveu algum XML sabe que ele não funciona até que TODAS as tags estiverem bem fechadas, no HTML era diferente, muitas vezes deixávamos tags abertas, e ele funcionava que era uma beleza.

Para se fazer um XHTML válido, devemos fechar TODAS as tags:

  1. Não devemos esquecer de fechar as tags que estamos carecas de conhecer: <p></p>, <b></b>, etc&#8230;
  2. E não devemos esquecer de forma alguma de fechar as tags &#8220;solitárias&#8221;, assim, ao invés de <br> escrevemos <br></br>, ou na forma simplificada: <br />.

Descobriram que fechando tags desta forma <br/>, não se sabe porque estava causando um problema no Netscape, mas apenas colocando um espaço antes da / o problema é solucionado.

### Use letras minúsculas

Quem nunca viu um código fonte de um documento HTML escrito assim:
  
<A href=&#8221;http://tags.com.letras.minúsculas/&#8221; TARGET=&#8221;_BLANK&#8221;> </A>
  
Um documento XHTML deve ter TODAS as tags e seus respectivos atributos escritos com letra minúscula!

### Não esqueça das &#8220;ASPAS&#8221;

Esta regra é bem simples. Todos os atributos XHTML devem conter as benditas &#8220;ASPAS&#8221;.

### Atributo NAME

O antigo atributo NAME foi substituído pelo atributo ID. Se seus usuários, clientes, etc, utilizam ainda antigos browsers, você pode sem problema nenhum utilizar as duas formas juntas durante neste período em que estamos migrando:
  
<img src=&#8221;imagem.gif&#8221; id=&#8221;imagem&#8221; name=&#8221;imagem&#8221; />

### Atributos sem valor

Não devemos esquecer também os atributos que escrevemos sem valor, por exemplo:

ERRADO:
  
<option selected>
  
<frame noresize>
  
<input checked>
  
<input readonly>

CERTO:
  
<option selected=&#8221;selected&#8221;>
  
<frame noresize=&#8221;noresize&#8221;>
  
<input checked=&#8221;checked&#8221;>
  
<input readonly=&#8221;readonly&#8221;>

E assim por diante.

### Quer uma ajudinha?

Se você está migrando do HTML para o XHTML, o TIDY pode te dar uma forcinha.
  
O TIDY é uma ferramenta para validar e consertar códigos HTML, ele tem opções que você pode escolher qual a versão do HTML você quer validar, uma dessas opções é a XHTML. Se você já está escrevendo um XHTML e quer que seu código fique livre de todos os erros, o TIDY arruma para você.
  
Ele foi originalmente desenvolvido por Dave Raggett e hoje é mantido por um projeto de código aberto: SourceForge, por um grupo de voluntários.

### Últimas palavras

Fazendo todas essas pequenas porém importantes regras, quer dizer, regras não, LEIS, você terá um belo de um documento XHTML válido, e acima de tudo, estará contribuindo para uma WEB melhor.

Como eu passei apenas o miolo, navegando nestes links poderão ser achados mais informações a respeito:

  * <a href="http://www.w3schools.com/xhtml/xhtml_reference.asp" target="_blank">Referência de XHTML 1.0</a>
  * <a href="http://www.w3schools.com/w3c/" target="_blank">Tutorial da W3C</a>
  * <a href="http://www.w3schools.com/default.asp" target="_blank">W3Schools:</a>
  * <a href="http://www.comciencia.br/reportagens/internet/net08.htm" target="_blank">WebSemântica</a>

### Notas:

Para saber se seu documento XHTML é válido:
  
<a href="http://validator.w3.org" target="_blank">http://validator.w3.org</a>

Tidy:
  
<a title="Source Forge" href="http://tidy.sourceforge.net/" target="_blank">http://tidy.sourceforge.net/</a>
  
<a title="Dave Raggett's Original" href="http://www.w3.org/People/Raggett/tidy/" target="_blank">http://www.w3.org/People/Raggett/tidy/</a>