---
title: Informação e Formatação; As duas camadas de desenvolvimento web
author: Diego Eis
type: post
date: 2007-12-06
url: /informacao-e-formatacao-as-duas-camadas-de-desenvolvimento-web/
tweetbackscheck:
  - 1356185078
shorturls:
  - 'a:3:{s:9:"permalink";s:86:"http://tableless.com.br/informacao-e-formatacao-as-duas-camadas-de-desenvolvimento-web";s:7:"tinyurl";s:26:"http://tinyurl.com/4x3orpq";s:4:"isgd";s:19:"http://is.gd/ZghY6o";}'
twittercomments:
  - 'a:4:{i:27420609470271488;s:7:"retweet";i:27420591564783616;s:7:"retweet";i:27420234260414465;s:7:"retweet";i:27419999169679360;s:7:"retweet";}'
tweetcount:
  - 4
dsq_thread_id: 503037754
categories:
  - Artigos
  - Técnicas e Práticas
tags:
  - camadasdesenvolvimento
  - CSS
  - desenvolvimento web
  - formataçao
  - html
  - padroes web
  - tableless
  - xhtml

---
Se você já leu alguma coisa sobre Tableless, já deve ter percebido que nesse método nós separamos a informação da formatação.
  
Para fazer a formatação do site, ou seja, para literalmente aplicarmos o design do site, nós usamos o CSS (as famosas Folhas de Estilo), que eu julgo ser a principal ferramenta do desenvolvedor para criar sites tableless. Para a apresentação da informação, você pode usar HTML ou XHTML, o que você achar mais apropriado.

A separação entre informação e formatação traz muitas vantagens, mas vou citar apenas duas, divididos em dois artigos:

  1. Facilidade de Manutenção
  2. Maior produtividade

Então, vamos ao que interessa.

### Facilidade de Manutenção

Separando a informação da formatação, você já organiza grande parte do código, pois você os separa em arquivos distintos, um arquivo .css para a formatação e outro arquivo .html (.asp, .php. seja lá o que for) para a informação. Esta simples organização, lhe permite fazer com rapidez e objetividade qualquer tipo de manutenção, sendo ela grande ou pequena.

Imagine a seguinte situação:
  
Você está no final daquele grande projeto, aquele site em que você fica horas desenhando tabelas, puxando daqui e dali, acertando medidas, etc&#8230; e quando você olha para o lado para descansar um pouco as vistas, você chega a pensar que seguiu o coelho branco&#8230;
  
Então, sem mais nem menos seu chefe lhe chama para conversar sobre o projeto e fala que o cliente pediu para que todos os títulos do site mudassem de cor, você o olha desacreditado, e já contando silenciosamente quantos títulos tem no site, se dirige para sua mesa e decide por onde começar.

Se você não passou por esta situação, acredite, muitos desenvolvedores já passaram por isso.

Vamos supor que o desenvolvedor do exemplo acima, usasse para apresentar os títulos a tag <h1></h1>, ele simplesmente atribuiria pelo CSS um valor para que todas as tags <h1> tivessem a cor desejada, em poucos segundos, ele mudaria a cor de todos os títulos do site, e isso tudo, sem mexer no arquivo HTML, economizando o tempo que ele levaria abrindo vários arquivos para procurar as intermináveis tags <font color=&#8221;#666666&#8243;></font> somente para mudar uma simples cor. Problemas como este, não vão mais tomar o precioso tempo do desenvolvedor.

Agora, e se a manutenção não fosse simples assim? E se fosse mais um pouco complicada, como do tipo mudar todo o layout do site? E se você pudesse mudar todo o layout do site, mudando apenas um arquivo .css?
  
Em um site tableless, o código HTML fica livre de tags desnecessárias do tipo: <font> <center>, deixando você à vontade para modificar o visual do site usando apenas CSS, te dando total controle sobre localização de objetos, tamanhos, cores e famílias de fontes, medidas, alinhamentos de texto, etc&#8230;

Fazendo isso, você pode escrever vários arquivos CSS distintos, que modifiquem o visual do site completamente, e o melhor, sem tocar numa letra do arquivo HTML, ele continua sendo o mesmo.

Vários sites usam está técnica, deixando o usuário escolher o layout que mais lhe agrada, veja alguns exemplos:

  * <http://www.csszengarden.com/>
  * <http://www.meyerweb.com/>
  * <http://www.zeldman.com/>
  * <http://jeffhowden.com/styleswitcher/>
  * <http://www.accessanet.com/standard/styleswitcher.html>
  * <http://roselli.org/adrian/>
  * <http://www.alltheweb.com/help/alchemist/gallery.html>

Realmente é uma mão na roda, não acha?
  
Tudo organizado, formatação de um lado, informação do outro, sem complicação&#8230; Seu código fica enxuto, limpo, muito menor do que se você tivesse feito do jeito tradicional, lhe dando menos dor de cabeça, e mais tempo. Ainda por cima, você contribui para uma web mais semântica.

No próximo artigo trataremos sobre o ganho de produtividade observado com a aplicação da metodologia tableless.

Leitura Recomendada:
  
<http://www.pedromendes.com/words/molly-200211-truelanguage1.html>