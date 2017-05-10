---
title: 'Seletores do CSS: Pseudo-classes'
author: Diego Eis
type: post
date: 2009-03-23
excerpt: Uma breve explicação sobre pseudo-classes, seus funcionamentos e tipos.
url: /pseudo-classes-css/
aktt_notify_twitter:
  - yes
aktt_tweeted:
  - 1
tweetbackscheck:
  - 1356400622
shorturls:
  - 'a:3:{s:9:"permalink";s:42:"http://tableless.com.br/pseudo-classes-css";s:7:"tinyurl";s:26:"http://tinyurl.com/3hyrllj";s:4:"isgd";s:19:"http://is.gd/635MdT";}'
twittercomments:
  - 'a:0:{}'
dsq_thread_id: 503038935
categories:
  - CSS
  - Técnicas e Práticas
tags:
  - Browsers
  - CSS
  - css-seletores
  - pseudo-classes
  - seletores
  - serie-seletores

---
Existem vários tipos de **pseudo-classes**. Podemos separá-las em dois grandes grupos: **Estruturais** e **Dinâmicas**. Existem outras pseudo-classes que não se encaixam nestes dois grupos principais, que controlam a interface do usuário, elementos de URLs e etc. <!--more-->Não irei me alongar em todos os grupos, entenda melhor sobre todos os grupos e pseudo-classes diretamente da fonte: 

[CSS3 Selectors][1] ou se quiser, temos uma [tabela de compatibilidade de CSS][2] para que você possa conferir o que funciona em cada browser.

### Pseudo-classes Dinâmicas

As pseudo-classes dinâmicas controlam os estados dos elementos. Abaixo, vão alguns deles:

  * **:hover** &#8211; quando passamos o mouse em cima do elemento.
  * **:active** &#8211; quando ativamos o elemento. Por exemplo, quando clicamos em um link e não soltamos o botão do mouse. Nesse momento, estamos ativando a ação do elemento. Esse estado é ativado também quando navegamos pelos links pelo teclado utilizando o TAB. Este estado não há em todos os elementos.
  * **:visited** &#8211; quando o link é visitado.
  * **:focus** &#8211; quando um elemento recebe foco. Muito utilizado em campos de texto. Quando clicamos em cima um campo de texto para escrever, o elemento está ganhando foco.

Teoricamente, todos os elementos tem estes estados. Partindo dessa premissa, podemos fazer, por exemplo, um menu com submenu sem utilizar Javascript. Basta fazer com que ao passar em cima de uma LI, a UL que ela contém, apareça, ou seja, ganhe display: block;. Complicado? Claro que não. Veja o HTML abaixo:

<pre lang="HTML" line="1"><ul>
  <li>
    <a href="#">Home</a>
  </li>
     
  
  <li>
    <a href="#">Produtos</a>
          <ul>
      <li>
        <a href="#">Carros</a>
      </li>
              
      
      <li>
        <a href="#">Motos</a>
      </li>
              
      
      <li>
        <a href="#">Charretes</a>
      </li>
              
      
      <li>
        <a href="#">Skates</a>
      </li>
            
    </ul>
       
  </li>
     
  
  <li>
    <a href="#">Sobre</a>
  </li>
     
  
  <li>
    <a href="#">Contato</a>
  </li>
  
</ul>
</pre>

Largue de ser preguiçoso, copie o código acima em um HTML com Doctype STRICT e veja o resultado no browser. Agora, defina o seguinte CSS:

<pre lang="CSS" line="1">ul li ul {
   display: none;
}

ul li:hover ul {
   display: block; 
}
</pre>

No seletor **UL LI UL**, você selecionou a UL que está dentro da LI, e definiu para que ela não aparecesse com a propriedade **display: none;**.
  
No seletor **UL LI:HOVER UL**, como no seletor acima, você selecionou a UL que está dentro da LI. Mas com uma diferença: você colocou logo após a LI a pseudo-classe :hover, o seja, você definiou a UL que está dentro da LI, mas só quando o mouse é passado em cima dessa LI. Complicado? Que nada. Veja aí no seu exemplo como ficou, ou [veja aqui][3].

Eu não preciso dizer que isso não funciona no IE6. Esse artigo faz parte daquela série: o que podemos fazer sem o IE6. 

Abriu um pouco a cabeça para várias possibilidades, não é? Pois é. Essa é a idéia.

### Pseudo-classes Estruturais

As pseudo-classes estruturais servem para selecionarmos um elemento da estrutura do código. Existem várias, por exemplo:

**:first-child** &#8211; seleciona o primeiro filho de um outro elemento.
  
**:last-child** &#8211; seleciona o último filho de um elemento.
  
**:root** &#8211; representa um elemento que é a raiz do documento. No HTML 4, é sempre a tag HTML.
  
**:nth-child()** &#8211; permite que selecionemos qualquer elemento no meio de um grupo de elementos. Por exemplo, você pode selecionar linhas de uma tabela. Assim, podemos fazer uma tabela zebrada, sem a ajuda de javascript. Há variações dessa pseudo-classe para podermos pegar os elementos de baixo para cima (:nth-last-child) e assim por diante. Testei aqui e isso não funcionou no meu FF3 (mac).
  
**:lang()** &#8211; seleciona elementos que tem o atributo lang com um valor específico. [Veja um exemplo][4].

Um exemplo básico.
  
Imagine que você tem o seguinte HTML:

<pre lang="HTML" line="1"><div id="destaques">
  &lt;div 
  		
  
  <h3>
    Título do Destaque
  </h3>
  		
  
  <p>
    Nullam cursus, dui vitae rhoncus imperdiet, nibh justo fermentum lectus, ac faucibus est ipsum id mauris. Phasellus auctor pede sed sem. Proin metus diam, ullamcorper ac, aliquet sit amet, semper in, ipsum. Nullam turpis dui, tristique quis, cursus non, tristique ac, mauris. Nunc mauris. Sed adipiscing. Aliquam ultricies egestas eros. Etiam nec ipsum id justo vestibulum condimentum. Aenean rhoncus, erat at luctus tincidunt, dolor dolor pharetra sem, ac iaculis lacus neque ut lectus. Quisque elementum bibendum diam. 
    		
  </p>
  	
</div>
	&lt;div 
		

<h3>
  Título do Destaque
</h3>
		

<p>
  Nullam cursus, dui vitae rhoncus imperdiet, nibh justo fermentum lectus, ac faucibus est ipsum id mauris. Phasellus auctor pede sed sem. Proin metus diam, ullamcorper ac, aliquet sit amet, semper in, ipsum. Nullam turpis dui, tristique quis, cursus non, tristique ac, mauris. Nunc mauris. Sed adipiscing. Aliquam ultricies egestas eros. Etiam nec ipsum id justo vestibulum condimentum. Aenean rhoncus, erat at luctus tincidunt, dolor dolor pharetra sem, ac iaculis lacus neque ut lectus. Quisque elementum bibendum diam. 
  		
</p>
	&lt;/div>

	&lt;div 
		

<h3>
  Título do Destaque
</h3>
		

<p>
  Nullam cursus, dui vitae rhoncus imperdiet, nibh justo fermentum lectus, ac faucibus est ipsum id mauris. Phasellus auctor pede sed sem. Proin metus diam, ullamcorper ac, aliquet sit amet, semper in, ipsum. Nullam turpis dui, tristique quis, cursus non, tristique ac, mauris. Nunc mauris. Sed adipiscing. Aliquam ultricies egestas eros. Etiam nec ipsum id justo vestibulum condimentum. Aenean rhoncus, erat at luctus tincidunt, dolor dolor pharetra sem, ac iaculis lacus neque ut lectus. Quisque elementum bibendum diam. 
  		
</p>
	&lt;/div>
&lt;/div>
</pre>

E agora, defina a formatação abaixo para este HTML:

<pre lang="CSS" line="1">div#destaques div{
	width: 300px;
	float: left;
	padding: 10px 30px;
	border-right: 1px solid black;
}
</pre>

Ao aplicar esse código, você vai perceber que o último destaque também tem uma borda do lado direito. Normalmente, queremos as bordas apenas entre os elementos do meio. Para fazer isso por meios não muito inteligentes, nós teríamos que marcar algum dos divs das laterais para tirar a borda, ou marcar o div do meio para definir uma borda para os seus dois lados.
  
Mas considere que você não pode modificar o HTML por algum motivo, e apenas é liberado modificações pelo CSS, como fazer?
  
A pseudo-classe :last-child pode ajudar. Você quer retirar a borda do último filho do div **#DESTAQUES**. Você iria inserir uma linha de CSS assim:

<pre lang="CSS" line="7">div#destaques div:last-child {border-right:none;}
</pre>

[Veja o resultado final][5].

Você selecionou o DIV que é o último filho do **div#destaques** e retirou a borda da direita que havíamos dado logo anteriormente. Sem modificar o HTML, colocando novas tags ou novas classes apenas para retirar uma borda.

Há outras pseudo-classes como a :disabled ou :enabled, que modificam elementos com os atributos DISABLED ou ENABLED, como por exemplo, campos de texto, checkbox, radios etc.

O CSS pode fazer muito por nós, basta os navegadores implementarem essas possibilidades. É por isso toda essa campanha contra o Internet Explorer 6. Esse artigo e [outros][6] [artigos][7] fazem parte dessa campanha. É uma forma de mostrar o quanto perdemos de produtividade em nosso dia a dia.

 [1]: http://www.w3.org/TR/css3-selectors/ "Seletores do CSS3"
 [2]: http://tableless.com.br/compatibilidadecss/ "Tabela para ver a compatibilidade de propriedades CSS entre os browsers"
 [3]: http://tableless.com.br/uploads/2009/03/submenu.html "Submenu sem javascript"
 [4]: http://tableless.com.br/uploads/2009/03/lang.html
 [5]: http://tableless.com.br/uploads/2009/03/lastchild.html "Selecionando o último filho"
 [6]: http://tableless.com.br/seletores-complexos-do-css
 [7]: http://tableless.com.br/seletores-agrupados-e-encadeados