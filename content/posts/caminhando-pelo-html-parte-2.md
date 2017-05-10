---
title: Caminhando pelo HTML – parte 2
author: Elcio Ferreira
type: post
date: 2006-01-11
url: /caminhando-pelo-html-parte-2/
tweetbackscheck:
  - 1356439352
shorturls:
  - 'a:3:{s:9:"permalink";s:52:"http://tableless.com.br/caminhando-pelo-html-parte-2";s:7:"tinyurl";s:26:"http://tinyurl.com/3los28n";s:4:"isgd";s:19:"http://is.gd/oCa8bL";}'
twittercomments:
  - 'a:0:{}'
dsq_thread_id: 503034375
categories:
  - Artigos
  - Browsers
  - Geral
  - Tecnologia e Tendências
tags:
  - acessibilidade
  - Técnicas e Práticas

---
Este é o segundo artigo da série de cinco, &#8220;Caminhando pelo HTML&#8221;, que foi publicada originalmente na Revista Webdesign. Divirta-se.

<!--more-->

Em nosso estudo desse mês vamos entender uma informação básica por trás da criação de um arquivo HTML: como indicar com que versão do HTML você está trabalhando.

**HTML e suas versões**

Um fato ignorado por muita gente é que a linguagem HTML possui versões. A versão 3.2 da linguagem HTML, por exemplo, é de 1996 não possuía tags como frame, iframe ou object. A versão 4.0, de dezembro de 1997, incluiu esse recurso. Essa versão sofreu algumas revisões dois anos depois, se tornando a 4.01. Esta é a versão mais antiga com a qual você poderia trabalhar hoje. Assim, começamos a estudar da 4.01 para frente.

Cada versão do HTML pode ter vários “sabores”. A HTML 4.01, por exemplo, possui os modos Strict, Transitional e Frameset. Para entender estes modos, é preciso entender que a versão 4.01 do HTML matou algumas tags antigas, como a tag font. Além disso, mudou pequenas regras na sintaxe da linguagem, ou seja, na forma como se escrevem as tags e atributos. Isso poderia ser um sério problema para quem mantinha documentos antigos e precisava migrar para a linguagem. Mudar regras de sintaxe é fácil, mas, por exemplo, eliminar as tags font do documento, substituindo-as por CSS, pode ser um trabalho muito difícil se você tiver milhares de documentos num site que já está no ar.

Para isso existe o modo Transitional. Ele faz valer as novas regras de sintaxe, mas é bastante flexível a respeito de que tags podem ser usadas e da semântica do documento. O modo Frameset é o que você vai usar no arquivo de frames, se tiver que trabalhar com frames. Você só precisa colocar em modo Frameset seu documento principal, que contém os outros frames. Neles, pode carregar documentos em qualquer modo.

Já o modo Strict é para quem está querendo migra para valer para a nova versão da linguagem, obrigando você a usar CSS para formatar seu documento e ao mesmo tempo a usar as novas regras da linguagem.

**XML e XHTML**

A próxima versão da linguagem HTML, depois da 4.01, é a XHTML 1.0. Trata-se de uma importante mudança de conceitos em relação à linguagem HTML, tornando-a compatível com XML. A linguagem XML é hoje um idioma praticamente universal de troca de dados. Usamos XML para fazer nossas páginas ASP ou PHP se comunicarem com aplicações Flash, para fazer nossos servidores Java falarem com servidores .NET e para fazer nossos leitores de RSS permanecerem atualizados. Para que possa ser lida por tantos sistemas diferentes, a linguagem XML tem algumas regras rígidas a respeito do que você pode ou não escrever.

Apesar disso, para quem já trabalha com HTML 4.01, a mudança não é dramática, uma vez que as duas linguagens derivam do mesmo padrão, o SGML. A sintaxe é muito parecida e as regras extras são poucas e simples.

A primeira é que você precisa fechar todas as tags e todos os seus atributos precisam estar entre aspas, simples ou duplas. A segunda é que nomes de classes e atributos precisam estar em minúsculas. Assim, no HTML 4.01 você podia escrever:

`<P CLASS=um>Primeiro Parágrafo<br />
<p class=dois>Segundo Parágrafo<br />
Mas, em XHTML, precisa escrever:<br />
<p class="um">Primeiro Parágrafo</p><br />
<p class="dois">Segundo Parágrafo</p>`

Em relação à sintaxe, à forma de escrever, estas são as principais mudanças que você vai sentir. Há outras pequenas regras, também simples, como o fato de você não poder “cruzar” tags, assim:

`<b>texto <i>texto</b> texto</i>`

E o fato de você precisar fechar até mesmo as tags img, br ou hr. Para isso, ao invés de fazer:

`<br></br>`

Você pode usar a sintaxe simplificadora:

`<br />`

Duas dicas: se você usa Dreamweaver 8 e não tinha entendido porque ele insiste em colocar uma barra no final do br, eis a resposta, ele usa por padrão a versão XHTML 1.0 em seus documentos. Já se você usa a versão MX e gostaria de experimentar o trabalho com XHTML, há ajuda para você aqui: http://tinyurl.com/zay3u

A XHTML 1.0 também tem os modos Strict, Transitional e Frameset. Os conceitos são os mesmos, a versão Transitional existe para promover uma migração facilitada para quem vem do HTML 4.01, a Frameset é para quem precisa trabalhar com frames e a Strict é para quem quer seguir todas as novas regras. No caso de XHTML 1.0, as novas regras representam uma boa “faxina” no HTML, tornando mais simples e cheio de significado, e naturalmente obrigando você a trabalhar arduamente com CSS.

**O DOCTYPE**

Como indicar com que tipo de documento você está trabalhando? Fazemos isso incluindo um pequeno trecho de código na primeira linha de nosso HTML, o DOCTYPE. Seguem os DOCTYPES para os três sabores do HTML 4.01:

Strict:
  
`<!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.01//EN" "http://www.w3.org/TR/html4/strict.dtd">`

Transitional:
  
`<!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.01 Transitional//EN" "http://www.w3.org/TR/html4/loose.dtd">`

Frameset:
  
`<!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.01 Frameset//EN" "http://www.w3.org/TR/html4/frameset.dtd">`

E os DOCTYPES para o XHTML 1.0:

Strict:
  
`<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Strict//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-strict.dtd">`

Transitional:
  
`<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">`

Frameset:
  
`<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Frameset//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-frameset.dtd">`

Até os antigos Internet Explorer 5.5 e Netscape 4.8, não fazia a menor diferença para o navegador que DOCTYPE você colocava, ou mesmo se não colocava nenhum em seus documentos. A partir do Internet Explorer 6.0, em todos os navegadores atuais, o DOCTYPE instrui o navegador a respeito de como renderizar o documento. Por isso é importante que você escolha e use um DOCTYPE em seu documento.

`Validação`

Uma das vantagens de colocar um DOCTYPE em seu documento é o fato de poder contar com validadores automáticos, como o do W3C (http://validator.w3.org). Eles são uma grande ajuda ao escrever um documento, indicando seus erros, o que é muito mais produtivo do que procurá-los você mesmo em um documento longo.

`E qual DOCTYPE usar?`

Depende. O ideal é que você use o XHMTL 1.0 Strict, preparando seus documentos e a si próprio para o futuro. Mas nem todo mundo pode viver hoje esta realidade. Talvez você tenha um gerenciador de conteúdo antigo, que gera código ruim. Talvez tenha outras pessoas publicando HTML na equipe, talvez centenas delas, e não pode definir as regras que todo mundo vai seguir.
  
Minha sugestão é que você tente trabalhar com XHMTL, mesmo que seja o Transitional. Assim vai poder desfrutar de coisas como os microformatos e outros usos do seu código que dependem de ele ser XML válido. Mas só faça isso se tiver condições de oferecer realmente XML válido, caso contrário, que pena, é melhor trabalhar com o HTML 4.01.

`E o futuro?`

O W3C já publicou uma revisão da XHTML 1.0, a XHTML 1.1, feita para ser modular. Isso significa que você poderá inserir em seu HTML trechos de outras linguagens, como MathML, SVG ou RSS. Já publicou também um “rascunho funcional” da nova versão da XHMTL, a 2.0. Tenho visto algumas pessoas usando o DOCTYPE XHTML 1.1 e muita gente fazendo perguntas sobre o 2.0.
  
Acredite em mim: estas versões não são para você ainda. O principal problema com elas é que foram feitas para um futuro próximo em que tudo na web será baseado em XML. Assim, ao trabalhar com esses “novos sabores” do HTML, você precisa servi-los como XML. Isso significa configurar seu servidor para servir um mime-type diferente ou incluir um header HTTP em suas páginas. Significa também lidar com problemas com o Internet Explorer se recusando a exibir seus documentos. (Mais sobre isso em http://tinyurl.com/zbyxw e http://tinyurl.com/bhwfr)

`E agora?`

Ao colocar um DOCTYPE em seus documentos e tentar validá-los, você pode se deparar com uma série de pequenos problemas. Suas páginas podem começar a aparecer com pequenas diferenças e a validação pode ser um tanto complicada, por exemplo. É assim só das primeiras vezes, e você supera isso muito rápido. Depois que você conseguir entender direitinho essa meia dúzia de regras e validar seus primeiros documentos, tudo vai ficar muito mais fácil.
  
Em nosso próximo artigo vamos falar sobre páginas de código e os problemas com caracteres acentuados. Até lá.