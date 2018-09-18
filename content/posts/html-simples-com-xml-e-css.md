---
title: HTML simples com XML e CSS
authors: Elcio Ferreira
type: post
date: 2007-12-06
url: /html-simples-com-xml-e-css/
tweetbackscheck:
  - 1356434007
shorturls:
  - 'a:3:{s:9:"permalink";s:50:"https://tableless.com.br/html-simples-com-xml-e-css";s:7:"tinyurl";s:26:"https://tinyurl.com/3td8d38";s:4:"isgd";s:19:"https://is.gd/78FXqj";}'
twittercomments:
  - 'a:0:{}'
dsq_thread_id: 503037747
categories:
  - Artigos
  - Técnicas e Práticas
tags:
  - CSS
  - elementos html
  - frames
  - html
  - popup
  - Semântica
  - tags
  - xhtml
  - xml

---
Qualquer um que codifique HTML, ou mesmo use um editor WYSIWYG, já esbarrou no problema. Se você trabalha com internet, já deve ter tido também esse problema. O código se tornou complexo, com várias tabelas, uma dentro da outra. Vários frames, com uma porção de scripts para manter o
  
conteúdo atualizado entre eles. Uma parte da aplicação rodando em um pop-up, com um script
  
que atualiza o conteúdo principal.

Então, cumprindo a lei de Murphy, um dos seguintes fatos indesejáveis acontece:

  1. Um cliente liga reclamando que o site está dando um tal de &#8220;erro de script&#8221; quando clica num link, você
  
    tenta, mas não consegue reproduzir o erro em nenhum navegador.
  2. Alguém da diretoria resolve que os títulos devem ser azuis, não vermelhos. E você se
  
    põe a localizar <font face=&#8221;verdana&#8221; size=&#8221;5&#8243; color=&#8221;red&#8221;> para poder mudar a cor.
  3. Alguma tabela não fechada corretamente estádando problemas no Netscape, mas o código tem cincotabelas aninhadas e você perde um dia tentando acharo defeito.
  4. Você percebe uma certa demora para carregar algumaspáginas, vai conferir o código e descobrealgumas coisas assim: <font face=&#8221;Verdana&#8221;><b></b><i></i><fontsize=&#8221;1&#8243;><b></b></font><fontface=&#8221;Arial&#8221;>Texto</font></font>

Que fazer? É claro que com muito cuidado e talentoesse tipo de problema pode ser evitado, mas isso envolve umaquantidade de trabalho insana. Já vi muitos projetosonde se gastou mais tempo preso nas entranhas de umcódigo complexo do que em qualquer outra fase doprojeto.

Tem um pessoal na web que propõe umasolução bastante interessante para isso.É a turma do WaSP (www.webstandards.org.) Assoluções não são apenas uma listade novas tecnologias, mas também uma filosofia dedesenvolvimento baseada na simplicidade.

Baseado nessa filosofia da simplicidade, que tem me rendidoresultados surpreendentes, gostaria de fazer algumassugestões interessantes:

### XHTML

Quem já trabalha com XML certamente percebeu o poderda flexibilidade e da simplicidade. Éimpossível escrever um XML com erros de sintaxe,porque os interpretadores reclamam imediatamente. Émuito simples escrever documentos XML, sendo fácilextrair dados de qualquer banco de dados etransformá-los em XML (a maioria dos SGBDs incorporaou tem planos de incorporar o suporte nativo a XML.)Através da poderosa linguagem XSL e da farta oferta deparsers gratuitos, XML pode ser transformado em praticamentequalquer formato de arquivo.

XHTML nada mais é do que uma forma de escrever umdocumento HTML de modo que ele também seja umdocumento XML válido. Ou seja, seu documento HTMLganha a coerência e flexibilidade de um documento XML,podendo ser facilmente lido por ferramentasautomáticas e convertido em outros formatos dearquivos. Com XHTML torna-se muito fácil oferecer osdados do seu site através de WAP ou de um RSS(<https://rssficado.pilger.inf.br>)por exemplo. Torna-se fácil também transformaro resultado de uma consulta a banco de dados ou um documentoXML numa página web.

A boa notícia é que é muito fácilescrever XHTML. Qualquer um que escreva HTML pode aprender afazê-lo sem muita dificuldade. Existem inclusive umasérie de ferramentas interessantes para tornar esseprocesso mais produtivo, como o excelente HTML Tidy(<https://tidy.sourceforge.net>)que tem uma eficiência impressionante para umaferramenta automática.

### CSS e a Abordagem Semântica

Como você cria um título num documento HTML?

O meio comum hoje em dia para fazê-lo é:<font face=&#8221;Arial&#8221; size=&#8221;4&#8243; color=&#8221;blue&#8221;>Texto doTítulo</font>.

Quando eu estudei HTML, em 1996, aprendi que existia uma tagespecífica para criação detítulos. É a tag h1. Assim, a maneira de secriar um título em HTML seria: <h1>Texto doTítulo</h1>.

Extremamente mais simples, não é verdade? Etorna o código também mais significativo. Assimum interpretador pode saber, por exemplo, onde estãoos títulos no meio do texto. Ou seja, esta abordagemdá significado semântico ao código.Aquele tag passa a significar alguma coisa, mesmo quenão seja vista num browser que renderize a fonte maiore azul que você tinha planejado.

Aliás, por falar no texto azul, se você usar asegunda abordagem seu título será exibido comos estilos padrão do navegador, e seu azul vai para obeleléu. Como você não quer perder abonita formatação que havia planejado, aquientra uma segunda linguagem, o CSS. Com CSS você podecolocar toda essa informação sobreformatação num arquivo externo. Assimvocê fica com um arquivo HTML apenas cominformação (que fica muito mais simples,organizado e rápido de se escrever) e mantémtoda a formatação num arquivo externo. Se umdia seu chefe resolver que todos os títulos do sitetem que ser vermelhos ao invés de azuis (acredite,isso é muito comum) você sóprecisará alterar uma palavra em um únicoarquivo e todos os títulos do site estarãoautomaticamente ajustados.

### No Tables

Tabelas são um recurso muito útil do HTML. Semtabelas como exibiríamos informaçõescomo uma lista de produtos, um extrato bancário ou umcalendário? O problema é que tabelas tem sidousadas para muito mais do que isso. É preciso colocaro menu ao lado do texto? Cria-se uma tabela. É precisoque o texto tenha uma largura delimitada? Cria-se uma tabela.Imagem junto ao texto? Menu no cabeçalho? Duas colunasde texto? Tabela neles!

E como fica, nessa situação, a semânticado documento? Como você deve imaginar, nãohá aqui aquela prática separaçãoentre informação e formatação.Além disso, temos um outro sério problema: embrowsers antigos, ou mesmo em browsers modernos maldesenvolvidos, como o Internet Explorer, as tabelas sósão exibidas depois que a última tag</table> chega ao navegador.

É por isso que, quando você estáconectado via dial-up, em alguns sites a tela fica em brancodurante longos segundos (às vezes minutos) atéque é exibido de uma vez só.

Abrir mão de tabelas para montar layouts vai tornarseu código muito menor, mais simples e organizado. Vaitambém centralizar a formatação,colocando tudo que se refere a layout em um únicoarquivo. Imagine a facilidade de manutenção.Melhora também a experiência do usuário,pois a informação é exibida instantaneamente, assim que chega ao browser.

Dá-se a esta abordagem o nome de tableless. Apesar donome, não é a ausência total de tabelas,mas o seu uso apenas onde é semanticamentejustificável. De lambuja, um documento tableless bempensado vai funcionar em qualquer navegador, em qualquer sistema operacional, mesmo em PDAs.

### No Frames, No Pop-ups, No DHTML

Pense muito antes de aplicar uma solução
  
baseada em frames, DHTML, scripts absurdos, pop-ups, plugins,
  
ActiveX, Applets ou qualquer outra tecnologia que quebre
  
essas duas premissas da internet:

&#8211; A web é um ambiente multiplataforma.

&#8211; Cada documento na web tem um endereço associado a
  
ele.

Não vou me alongar nesse tópico, mas gostaria que você tomasse um tempo para ler:

  * <https://www.wired.com/news/culture/0,1284,55675,00.html>
  * <https://www.digital-web.com/features/feature_2001-6.shtml>
  * <https://www.digital-web.com/features/feature_2002-09.shtml>
  * <https://www.useit.com/alertbox/990530.html>
  * <https://www.useit.com/alertbox/9612.html>

### Vamos com calma

O interessante dessa abordagem baseada na simplicidadeé que você não precisa fazer tudo de umavez. Se está inseguro para começar, pode apenaseliminar as tags <font> e criar um arquivo CSSúnico. Ou pode começar usando os recursos deXML do seu banco de dados para gerar XHTML, ou criando umRSS. O importante é começar a simplificar antes que você fique maluco!