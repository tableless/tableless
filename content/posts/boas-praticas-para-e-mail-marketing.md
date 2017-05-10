---
title: Boas práticas para E-mail Marketing
author: Deivid Marques
type: post
date: 2012-08-08
excerpt: Algumas dicas práticas para codificação de email marketings.
url: /boas-praticas-para-e-mail-marketing/
tweetbackscheck:
  - 1356407059
shorturls:
  - 'a:3:{s:9:"permalink";s:31:"http://tableless.com.br/?p=6602";s:7:"tinyurl";s:26:"http://tinyurl.com/cgxe3w4";s:4:"isgd";s:19:"http://is.gd/vhqQh2";}'
twittercomments:
  - 'a:0:{}'
dsq_thread_id: 797262658
categories:
  - Código
  - CSS
  - HTML
tags:
  - email marketing
  - html

---
Você que é do tempo do html feito somente em tabelas, acompanhou das mudanças dos padrões web ou senão conheceu essa época, mas mesmo assim sofreu muito com o IE6, acredite, montar E-mail Marketing é um pouco pior que isso tudo junto. Mas calma, deixarei algumas dicas e boas práticas, evitando assim muito do seu sofrimento.

Em resumo: E-mail Marketing é uma estratégia muito eficiente e útil para manter os visitantes ligados ao site e aumentar a taxa de conversão, mas isso tudo não tem resultado se sua newsletter chega quebrada ou mesmo se for direto para a caixa de SPAM.

Na montagem desse html não adianta seguir as melhores práticas de padrões web. Os clientes de e-mail não aceitam muitos dos atributos do CSS e nem conhecem as novas tags do HTML5.

### HTML:

E-mail Marketing é pura tabela. Tabelas são chatas, mas nesse caso, são a única saída por enquanto.

Utilize sempre o atributo _valig=&#8221;top&#8221;_.

<pre class="lang-html">&lt;tr&gt;
    &lt;td valign="top" width="350"&gt;&lt;/td&gt;
    &lt;td valign="top"&gt;&lt;/td&gt;
&lt;/tr&gt;
</pre>

Sobre os tipos de Doctype suas diferenças de renderização, vocês podem conferir 3 testes realizados pelo site [Campaign Monitor][1].

### CSS

Evite usar CSS externo. Alguns clientes de e-mail não aceitam. Tanto no HEAD, quanto no BODY.
  
Utilize CSS inline (direto no elemento), porém não abuse de propriedades como position, float e etc&#8230;

<pre class="lang-html">&lt;td style="font-size:18px; color:#666666"; font-family: Arial, Verdana, Tahoma;"&gt;Texto &lt;/td&gt;
</pre>

Alguns atributos de fontes funcionam em todos os clientes de e-mail, assim como: cores, line-height, font-size, entre outros.

**Não use** <del>style=&#8221;color: #fff&#8221;;</del>

**Use** <del>style=&#8221;color: #ffffff&#8221;;</del>

Use sem medo o atributo border:

<pre class="lang-html">&lt;span style="border: 5px solid #000000"&gt;texto&lt;/span&gt;
</pre>

Veja a tabela de atributos CSS suportados por diversos clientes de e-mail.
  
<a title="http://www.campaignmonitor.com/css/" href="http://www.campaignmonitor.com/css/" target="_blank">http://www.campaignmonitor.com/css/</a>

### Imagens

  1. Todas as imagens devem ter display:block, assim evita que o Gmail e o Hotmail acrescentem um espaçamento entre elas.
  2. Utilize url absoluta da imagem em seu html, além da sua altura e largura. `<img src="http://www.exemplo.com.br/imagem.jpg" alt="A imagem" width="500" height="50" />`
  3. Não use imagens com extensão PNG que possuem áreas transparentes, pois não são aceitas em versões do outlook anteriores a 2007, pois seu render engine é o mesmo que o do IE6, que não suporta PNG transparente. As áreas que deveriam ser transparentes são exibidas em cinza.
  4. O atributo ALT oferece um texto alternativo quando alguma imagem não carrega ou não pode ser visualizada. Esse atributo é muito usado para melhorar a acessibilidade de uma página na web e principalmente de um email marketing, já que muitos clientes de email bloqueiam as imagens enviadas por remetentes desconhecidos do destinatário. Nesta situação, a função do atributo é facilitar a “pré-leitura” para o usuário. O atributo alt pode ser formatado para a leitura ficar mais organizada.
  5. Não que seja proibido, mas evite user gifs animados.

### Javascript e Flash

Parece meio óbvio, mas nunca utilize Javascript ou Flash. Estes são bloqueados pelos anti-virus dos principais provedores.

Confira mais dicas e boas práticas para o desenvolvimento do seu e-mail marketing:

  1. O ideal é que o layout não ultrapasse 600px de largura, assim evita rolagem horizontal.
  2. Use a ferramenta slice do Photoshop e faça recortes em blocos horizontais.
  3. Evite mesclar colunas e linhas pelos atributos rowspan e colspan, ja que eles não são suportados pelo Microsoft Outlook 2007. Isso irá prejudicar a renderização correta da mensagem. (nesse caso use tabela dentro de tabela).
  4. Para otimizar a entrega das mensagens, desenvolva o código HTML para que tenha até 30 kb. (evita pontuar no ranking de spam)
  5. Não esqueça de preencher a tag <title> do documento HTML. Muitas ferramentas antispam verificam o conteúdo desta tag e, caso ela esteja vazia ou preenchida com expressões suspeitas, sua mensagem pode ser pontuada como spam.
  6. Se usar imagens de fundo para o corpo da mensagem, através de css inline background-image, saiba que elas não serão visualizadas por destinatários que utilizam Outlook e Hotmail, a solução é usar tambem background-color :#corSolida (cor próxima da imagem) pra não fugir muito do layout, usando assim o conceito &#8220;[Progressive Enhancement][2]&#8220;.
  7. Para remover um sublinhado basta usar css inline: _style=&#8221;text-decoration: none;&#8221;_ direto no link.
  8. Existem diversas palavras que devem ser evitadas no corpo do e-mail, caso ao contrário ele irá direto para a caixa de spam.
  
    Conheça algumas delas: <a href="http://emailmarketing.virtualtarget.com.br/dicas/quais-as-palavras-que-devem-ser-evitadas-no-email-marketing" target="_blank">http://emailmarketing.virtualtarget.com.br/dicas/quais-as-palavras-que-devem-ser-evitadas-no-email-marketing</a>.
  9. Teste seu template em diversos clientes de email.
  
    Ao criar um site, qualquer desenvolvedor deve testá-lo em vários navegadores. Para email marketing isso não é diferente, os destinatários usam uma ampla variedade de clientes de email e, você deve desenvolver um template que seja perfeitamente visualizado na maioria deles.
  
    &#8211; Ferramenta gratuita para enviar e-mails.
  
    <a href="http://putsmail.com" target="_blank">http://putsmail.com</a>
  
    &#8211; Ferramenta paga, porém muito útil, ele testa seu html em todos os clientes de e-mail e retorna um print.
  
    <a href="http://litmus.com/" target="_blank">http://litmus.com/</a>
 10. Mesmo que seu html esteja lindo e perfeito, ele pode cair no SPAM.
  
    Conheça a tabela de regras antispam.
  
    <a href="http://emailmarketing.virtualtarget.com.br/uploads/2008/04/tabela_de_pontos1.pdf" target="_blank">http://emailmarketing.virtualtarget.com.br/uploads/2008/04/tabela_de_pontos1.pdf</a>

Veja os clientes de e-mail mais utilizados:
  
 <a title="Saiba mais" href="http://www.ecommercebrasil.com.br/artigos/os-clientes-de-e-mail-mais-utilizados-pelos-usuarios/" target="_blank"><img src="http://anyzamaro.com.br/uploads/2011/10/emailmarketing1.jpg" alt="Clientes de e-mail mais utilizados" /></a>

Para aprofundar-se melhor sobre o assunto, segue links de referências:

  * <http://www.campaignmonitor.com/blog/>
  * <http://blog.templateria.com/html/>
  * <http://www.campaignmonitor.com/css/>
  * <http://emailmarketing.virtualtarget.com.br/>

 [1]: http://www.campaignmonitor.com/blog/post/3317/correct-doctype-to-use-in-html-email/
 [2]: http://tableless.com.br/bem-vindo-a-xangrila-parte-1/