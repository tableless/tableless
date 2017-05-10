---
title: O desenvolvedor e a ganância por economizar código
author: Diego Eis
type: post
date: 2007-02-23
url: /o-desenvolvedor-e-a-ganancia-por-economizar-codigo/
tweetbackscheck:
  - 1356329634
shorturls:
  - 'a:3:{s:9:"permalink";s:74:"http://tableless.com.br/o-desenvolvedor-e-a-ganancia-por-economizar-codigo";s:7:"tinyurl";s:26:"http://tinyurl.com/442xteo";s:4:"isgd";s:19:"http://is.gd/HntLr7";}'
twittercomments:
  - 'a:0:{}'
dsq_thread_id: 503036737
categories:
  - Artigos
  - Tecnologia e Tendências
tags:
  - Técnicas e Práticas

---
Está certo que o desenvolvedor é um bicho estranho, cheio de manias intratáveis e teimoso, mas muito teimoso. Mesmo assim há alguns pontos que podemos tratar antes que vire algo irrecuperável. Um destes pontos é a ganância por economizar código, seja ele qual for. Vamos pegar aqui exemplos de XHTML e CSS. Lembra do tempo que você trabalhava com códigos mais ou menos assim:`<br />
...<br />
<table width="100%" border="0" cellpadding="0" cellspacing="0" style="background:url(http://www.siteruim.com/mot/image/topnav_bckgrd.gif) repeat-x;"><br />
<tr><td><table width="100%" border="0" cellspacing="0" cellpadding="0"><br />
<tr><td width="91" valign="top"><table width="91" border="0" cellpadding="0" cellspacing="0" class="spacertable"><br />
<tr><td colspan="3"><img src="/mot/image/spacer.gif" alt="" width="1" height="10" /></td><br />
</tr><tr><br />
<td width="10"><img src="http://www.siteruim.com/mot/image/spacer.gif" alt="" width="10" height="1" /></td> ...`

Lembra?
  
Muitos faziam código deste modo e para economizar, não fechavam tags como TD ou TR. Os mais maníacos colocavam o código em uma linha. Bom, naquele tempo passado até que podíamos relevar porque o código era de fato terrível. Mas o que leva um sujeito optar a ter estes mesmos hábitos quando o desenvolvimento usa Padrões Web?

Sempre que estou dando alguma aula sobre XHTML e CSS, tento ressaltar que agora temos mais liberdade. Podemos (e devemos) fechar todas as tags sem medo de deixar o código mais pesado. Além do mais, você economizou alguns Kb só fazendo o site sem tabelas.

Código XHTML tem que ser identado, organizado, com todas tags fechadas e seus atributos bem colocados e com seus valores entre aspas. Nada de colocar tudo em uma linha e sair satisfeito com o resultado. Abuse da organização ela vai te aliviar das dores de cabeça e te livrar de problemas graves.

Mesma coisa acontece com o CSS. Alguns desenvolvedores resolvem por as propriedades em uma linha apenas. Isso prejudica a legibilidade do código, atrasa a manutenção e deixa o código sujeito a erros. Quebre linhas depois de cada propriedade. Mantenha o caminho completo nos seletores, [como sugerido no post anterior][1].
  
Já vi [muitos dos meus alunos][2] com medo de deixar o código CSS com muitas linhas. Relaxe. No começo ele vai ficar com muitas linhas, vai mesmo. Meu primeiro CSS decente teve por volta de mil e poucas linhas! Não, não tinha organização nenhuma. Havia muito código redundante, vários hacks e milhares de conflitos e pra ajudar o site era enorme. Mesmo assim era muito melhor/menor que um site feito em tabelas.

 [1]: http://tableless.com.br/estruturando-o-codigo-css
 [2]: http://visie.com.br/cursos/