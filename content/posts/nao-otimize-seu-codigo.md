---
title: Não “otimize” seu código
author: Diego Eis
type: post
date: 2008-11-09
url: /nao-otimize-seu-codigo/
aktt_tweeted:
  - 1
aktt_notify_twitter:
  - no
tweetbackscheck:
  - 1356392850
shorturls:
  - 'a:3:{s:9:"permalink";s:46:"http://tableless.com.br/nao-otimize-seu-codigo";s:7:"tinyurl";s:26:"http://tinyurl.com/3atkpd9";s:4:"isgd";s:19:"http://is.gd/1quHZz";}'
twittercomments:
  - 'a:1:{i:19795282808016896;s:6:"136512";}'
tweetcount:
  - 1
dsq_thread_id: 503038603
categories:
  - Artigos
  - CSS
  - Técnicas e Práticas
tags:
  - codigo
  - CSS
  - desenvolvimento
  - html
  - padroes web
  - Semântica
  - tableless
  - xhtml

---
Quando fazíamos sites com tabelas, o grande problema era a quantidade de código que escrevíamos. Naquele tempo – 1996, 97, 98 – tínhamos outros pontos que precisavam de uma atenção maior. A conexão era lerda para todo mundo e isso dificultava um bocado as coisas. Por isso, fazer um site pesado era fora de cogitação. Ficávamos “mendigando” cada byte para que o site ficasse milésimos de segundo mais rápido.<!--more-->

O código era o grande problema. A quantidade de código interferia diretamente na performance do site. E isso fez com que os desenvolvedores encontrassem saídas não muito agradáveis.

Era comum fazer códigos como o de baixo:

<pre lang="html" line="1"><table>
  <tr>
    <th>
      Produto
    </th>
       
    
    <th>
      Preço
    </th>
     
  </tr>
   
  
  <tr>
    <td>
      Tênis
    </td>
       
    
    <td>
      R$230
    </td>
     
  </tr>
  
</table>
</pre>

Se transformarem em verdadeiros monstros:

<pre lang="1"><table>
  <tr>
    <th>
      Produto
    </th>
    
    <th>
      Preço
    </th>
  </tr>
  
  <tr>
    <td>
      Tênis
    </td>
    
    <td>
      R$230
    </td>
  </tr>
</table>
</pre>

Isso tudo para economizar alguns bytes, que dependendo do site, significavam teras e teras de banda por mês. Naquele tempo, fazer isso era totalmente justificável. Precisávamos de alguma forma diminuir esse código para que o site ficasse mais rápido para o usuário e as requisições não sobrecarregassem o servidor.

Hoje isso é totalmente dispensável.

Aprendemos a utilizar o CSS e sabemos escrever HTML semântico.
  
A utilização dos Padrões trazem uma série de vantagens, e uma grande parte dessas vantagens são por causa da diminuição do código. Com o desenvolvimento de camadas e principalmente por causa do uso do CSS, não precisamos mais “otimizar” o código.

Mas parece que os desenvolvedores gostam de coisas complicadas. Esse mal costume de otimização de código ainda existe, e hoje querem otimizar o CSS. Eu acho totalmente inútil. O CSS foi feito para controlar o visual do site inteiro. Ele tirou a responsabilidade de formatação que colocávamos no HTML. Seu trabalho é exclusivamente esse: controlar o visual e diagramação do site.
  
É normal ele ficar grande, enorme, bizarro! Sim, haverão alguns casos que o tamanho superará mais de 1000, 2000, 3000, 4000 linhas.
  
Dá para evitar? Claro que dá! Pense simples. [Module os arquivos][1]. Faça um planejamento. Mas NUNCA faça com que um CSS escrito assim:

<pre lang="css" line="1">div {
 padding: 10px;
 border: 1px solid #CCC;
 width: 485px;
 height: 37px;
 background: #EEE;
}
</pre>

Fique assim:

<pre lang="css" line="1">div{padding:10px;border:1px solid #CCC;width:485px;height:37px;background:#EEE}
</pre>

Tenha dó do seu próximo e tenha dó de você mesmo.

Se você escreve o código de acordo com os Padrões, já economizou código suficiente. Não prejudique a manutenção do site por conta dessa neura. Escreva código legível!

Há outro ponto que devemos levar em consideração: imagine que o site pese 40Kb. Estes 40Kb são compostos por 20Kb de CSS e 20Kb de HTML. O CSS tem uma característica interessante: ele é cacheado pelo browser quando visitante entra no site.
  
Na primeira visita do usuário ele baixará 40Kb de uma vez. Já na segunda visita ele baixará apenas 20Kb relativos ao HTML. Ele não precisará baixar os 20Kb de CSS porque o arquivo já está cacheado pelo browser.

Não “otimize” seu código CSS, nem seu código HTML. Faça apenas com Padrões Web e siga categoricamente a semântica. É a melhor otimização que você pode conseguir.

O Leonardo Caineli [escreveu um artigo sobre isso][2]. Claro, discordo da opinião dele.

**[update]**Depois do post o pessoal chamou a atenção para essa prática em empresas grandes. Notei que no post eu não falei nada sobre isso. Sim, concordo que essa prática, só nessa hipótese, é totalmente considerável.

Quando treinei a primeira equipe do Terra &#8211; da época do site laranjão, lembra-se? &#8211; a primeira coisa que eles fizeram foi converter a home, e eles ainda sim queriam colocar todo o CSS em apenas uma linha. 

Realmente 1Kb multiplicado por milhões é coisa para caramba e não há banda que agüente. Por isso, é totalmente aceitável que sites com um porte muito grande, &#8220;otimizem&#8221; seu código. **[/update]**

 [1]: http://tableless.com.br/modulando-o-css "Modulação de CSS"
 [2]: http://leonardocaineli.com.br/dicas-para-otimizar-seu-css/