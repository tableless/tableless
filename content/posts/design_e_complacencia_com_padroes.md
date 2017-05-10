---
title: Design e complacência com padrões
author: Elcio Ferreira
type: post
date: 2004-06-28
url: /design_e_complacencia_com_padroes/
tweetbackscheck:
  - 1356002346
shorturls:
  - 'a:3:{s:9:"permalink";s:57:"http://tableless.com.br/design_e_complacencia_com_padroes";s:7:"tinyurl";s:26:"http://tinyurl.com/3vz6jp7";s:4:"isgd";s:19:"http://is.gd/ptjLl0";}'
twittercomments:
  - 'a:0:{}'
dsq_thread_id: 503031707
categories:
  - Artigos
  - Técnicas e Práticas
  - Tecnologia e Tendências

---
[Excelente post do Jonas][1]:

> &#8230; A simplicidade de design, simplicidade extrema, que pode ser caracterizada por um estilo focado primordialmente no texto, conteúdo, e não nos ornamentos da página. Esse tipo de design é uma espécie de caminho natural para quem começa a entender a importância de padrões, e passa a utilizar técnicas modernas como o design tableless (layout definido via CSS) &#8230;

Embora isso tenha acontecido na prática, a questão não é tão preto-no-branco quanto pode parecer ao leitor incauto. Muitas pessoas confundem layout CSS com design minimalista. São coisas diferentes. Estão associadas por uma série de circunstâncias, entre elas dois fatos:

  1. As mentes pensantes na produção web, que se preocupam com padrões web, por coincidência também se preocupam com usabilidade, acessibilidade e arquitetura de informação. E, generalisando tanto quanto o Jonas, posso dizer que o minimalismo é um caminho natural para quem se preocupa com essas coisas.
  2. Como é natural com qualquer coisa que se aprenda, as pessoas que começam a aprender layout CSS querem produzir logo algo útil. O uso de padrões web é apaixonante ao ponto de as pessoas que ainda não dominam bem as técnicas do layout CSS simplificarem seus layouts afim de conseguir produzí-lo de maneira adequada com o que sabem.

A despeito desses dois fatos, não há relação técnica entre layouts simples e CSS. Como disse o próprio Jonas:

> Neste momento é importante ressaltar que CSS não necessariamente sugere o design simplista, muito pelo contrário.

Ou seja, as pessoas que realmente conhecem padrões web e tem construído layouts simples o tem feito porque enxergam nessa simplificação uma boa solução de layout, não porque sejam obrigadas a isso.
  
Mais:

> E consequentemente, designers que utilizam essas ferramentas se mantém distantes da realidade, mantendo a idéia de que editar código é muito difícil. A situação é de **dependência**.

Disse tudo. Mais:

> Uma coisa que poucas pessoas compreendem, principalmente com toda essa publicidade em torno de, abre aspas, tableless, fecha aspas, é que CSS Layout não implica, de forma alguma, [a complacência com padrões][2].

Há uma confusão de conceitos aqui. É difícil definir &#8220;complacência com padrões&#8221;. As recomendações de acessibilidade do W3C tem tanto valor e autoridade quanto as do XHTML, por exemplo (é curioso notar, o W3C raramente usa o termo &#8220;standard&#8221;.) Assim, o que seria exatamente &#8220;complacência com padrões&#8221;? Validar o documento assegura que ele é complacente com os padrões?
  
Mas é apenas uma questão de terminologia, o Jonas está certíssimo em separar conceitos que muitas pessoas erroneamente vinculam. Um site pode ter layout CSS e não ser um HTML válido, como este aqui. Pode também ter código válido e ser montado com tabelas. Pode ter código inválido, layout com tabelas e ser acessível a deficientes visuais, enquanto outro pode, por exemplo, ser tableless, com XHMTL Strict validado e ser inacessível.
  
Claro, quando você aborda o HTML semanticamente, como manda o W3C, fica mais fácil construir código validado e sites acessíveis. Mas são trabalhos diferentes, que se aplicarão também a recomendações diferentes do W3C. Acho que seria mais apropriado, ao invés de falar sobre complacência aos padrões como algo que um trabalho possui ou não, falar em níveis de complacência. Talvez a pergunta apropriada não seja &#8220;é complacente?&#8221; e sim &#8220;quão complacente?&#8221; Talvez ao invés de &#8220;é complacente com os padrôes?&#8221; devêssemos perguntar &#8220;é complacente com quais padrôes?&#8221;
  
Sobre &#8220;consumptibilidade&#8221;, gostaria de perguntar aos meus leitores: vocês validam seu HTML e CSS? Porquê? Eu costumo validar meus documentos (sim, eu sei, nem este site nem [meu Blog][3] são válidos, mas, a despeito desse desleixo, eu costumo sim validar meus documentos.) Mas confesso que tenho uma certa dificuldade em convencer algumas pessoas a validar. A pergunta que sempre me fazem é, uma vez que o documento não-válido é acessível hoje, e bem, em qualquer navegador, se vale a pena se dar ao trabalho de validar. Se você escreve seu blog pessoal ou prepara conteúdo para um cliente, onde você sabe que ninguém vai mexer, faz todo o sentido, e meu blog não valida, confesso, por puro desleixo. Mas se você, como alguns dos meus alunos, trabalha na criação e manutenção de sites conectados a complexos CMS, usados por mais de duas centenas de jornalistas e editores a coisa parece diferente. Sim, jornalistas, não webdesigners ou programadores, gente para quem difereça entre negrito e forte, ou itálico e enfatizado, parece o sexo dos anjos. Gente que precisa inserir imagens e formatar texto, e quem vai convencer uma centena de jornalistas a fornecer boas alternativas textuais para suas imagens? Ainda não tenho uma resposta.

 [1]: http://jonasgalvez.com/br/blog/2004-06/bozoless "Jonas Galvez: Design e complacência com padrões"
 [2]: http://validator.w3.org/check?uri=http://tableless.com.br/
 [3]: http://elcio.locaweb.com.br/blog/ "fechaTag"