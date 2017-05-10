---
title: 'Web Storage  – HTML5'
author: Bruno Ruiz
type: post
date: 2014-01-28
excerpt: Cookies foram por muito tempo, e ainda são hoje, uma das formas mais utilizadas para armazenar dados no cliente. No entanto, com o advento do padrão HTML5, surgiram novas alternativas para armazenamento de dados no cliente. A principal delas é o WebStorage.
url: /web-storage-html5/
dsq_thread_id: 2168585309
categories:
  - HTML5
  - JavaScript
tags:
  - api
  - html5
  - JavaScript
  - webstorage

---
## Cookies &#8211; o passado

Para entendermos a vantagem obtida na utilização do WebStorage vamos compreender como uma aplicação trabalha(va) com cookies.

Os cookies são inseridos no cabeçalho HTTP, sendo assim, sua performance pode ser comprometida. E estando as informações no cabeçalho HTTP, podemos nos perguntar: o quão protegidas elas estão?

Outro desafio que se apresenta ao se trabalhar cookies é a capacidade de armazenamento: 4kB por cookies vezes no máximo 20 cookies é igual a capacidade de 80 kB. Essa restrição de capacidade por si só já é um problema, mas ela acarreta outro dificuldade, o gerenciamento destes cookies.

Pense que em uma aplicação que real seria muito útil armazenar mais do que 80 kB, para fazer isso com cookies seria necessário estabelecer um controle de validade dos cookies, essa seria uma maneira muito inteligente de utilizar cookies &#8211; afinal ele precisar estar armazenado somente enquanto for necessário, mas o trabalho para controlar as datas de validade dos cookies seria um trabalho que requisitaria calcular seus tempos de validade, mais código.

## WebStorage &#8211; o presente e suas vantagens.

As limitações dos cookies já foram citadas, mas o WebStorage é melhor no itens citados? SIM.
  
Vamos ver como o WebStorage é melhor.

Mas em primeiro lugar vamos falar de segurança.

Os pares de chave e valor gravados pela WebStorage não podem ser acessados por outros subdomínios. Isso garante que caso você use o WebStorage para gravar dados com sigilo. Isso faz com que ele não corra o risco de ser acessado por outro domínio.

Sobre a capacidade de armazenamento, temos o suficiente para trabalharmos bem. A API permite armazenamentos entre 2,5 MB até 10 MB. Esse espaço é suficiente para podermos trabalhar com folga, principalmente se compararmos com a capacidade permitida para se trabalhar com os cookies.

Com este espaço disponível talvez você não precise se preocupar com o controle de validade dos dados. Mas caso você queira controlar o período em que os dados estarão gravados no navegador do usuário, você pode fazer isto. Para tanto, temos que entender o desdobramento do conceito do WebStorage: localStorage e sessionStorage.

Este último manterá os dados salvos enquanto o navegador estiver aberto. Isso é muito útil, pois nem sempre queremos que os dados estejam sempre disponíveis. Enquanto o localStorage manterá o dado gravado até que ele seja removido diretamente, você poderá fechar o navegador, reiniciar o computador e os dados ainda estarão lá.

## Exemplo

Não há melhor maneira de aprender do que fazendo. Vamos construir uma calculadora em que seja possível salvarmos os valores calculados e visualizá-los ao lado, e sempre que o usuário desejar ver os resultados calculados ele poderá fazer isto, mesmo após ter fechada a sessão. Então vamos ao exemplo.

Primeiro vamos construir a estrutura do nosso documento html, nele usaremos a biblioteca jquery para facilitar a construção do nosso script. Também teremos uma tag input onde serão apresentados os dígitos clicados, em seguidas temos os botões com os numeros de 0 à 9, com as operações de SOMA, MULTIPLICAÇÃO, DIVISÃO e SUBTRAÇÃO, PARÊNTESES e os botões de SALVAR &#8211; que irá salvar o valor da tag input no localStorage &#8211; ,LISTAR que ira pegar todos os valores listados no localStorage e colocar em uma tabela e o botão APAGAR que deletará todos itens do localStorage, também temos a tabela onde serão colocados os valores encontrados no localStorage :

<pre class="lang-html">&lt;!--Início - Documento .html-- gt;
&lt;html&gt;    
  &lt;head&gt;
    &lt;script src="http://code.jquery.com/jquery-1.10.2.min.js"&gt;&lt;/script&gt;
  &lt;/head&gt;
  &lt;body&gt;

    &lt;input id="inputResult"&gt;&lt;/input&gt;
    &lt;br&gt;

    &lt;button class="btnNumber" value="1"&gt;1&lt;/button&gt;
    &lt;button class="btnNumber" value="2"&gt;2&lt;/button&gt;
    &lt;button class="btnNumber" value="3"&gt;3&lt;/button&gt;
    &lt;button class="btnNumber" value="4"&gt;4&lt;/button&gt;
    &lt;button class="btnNumber" value="5"&gt;5&lt;/button&gt;
    &lt;br&gt;

    &lt;button class="btnNumber" value="6"&gt;6&lt;/button&gt;
    &lt;button class="btnNumber" value="7"&gt;7&lt;/button&gt;
    &lt;button class="btnNumber" value="8"&gt;8&lt;/button&gt;
    &lt;button class="btnNumber" value="9"&gt;9&lt;/button&gt;
    &lt;button class="btnNumber" value="0"&gt;0&lt;/button&gt;
    &lt;br&gt;

    &lt;button class="btnOperacao" value="+"&gt;+&lt;/button&gt;
    &lt;button class="btnOperacao" value="-"&gt; - &lt;/button&gt;
    &lt;button class="btnOperacao" value="*"&gt; * &lt;/button&gt;
    &lt;button class="btnOperacao" value="/"&gt; / &lt;/button&gt;
    &lt;button class="btnOperacao" value="("&gt;(&lt;/button&gt;
    &lt;br&gt;

    &lt;button class="btnOperacao" value=")"&gt;)&lt;/button&gt;
    &lt;button class="btnResult" value="="&gt;=&lt;/button&gt;
    &lt;button id="btnLimpar" class="btnOperacao" value="LIMPAR"&gt;LIMPAR&lt;/button&gt;
    &lt;br&gt;
    &lt;button class="btnSalvar" value="SALVAR"&gt;SALVAR&lt;/button&gt;
    &lt;br&gt;
    &lt;button class="btnListar" value="LISTAR"&gt;LISTAR VALORES&lt;/button&gt;
    &lt;br&gt;
    &lt;button class="btnApagar" value="APAGAR"&gt;APAGAR VALORES&lt;/button&gt;
    &lt;br&gt;
    &lt;br&gt;
    &lt;br&gt;

    &lt;table id="tableResults" class="tabela" border="0"&gt;
            &lt;tr&gt;
                     &lt;td&gt;
      Chave
        &lt;/td&gt;
                    &lt;td&gt;
      Valor
                    &lt;/td&gt;
                 &lt;/tr&gt;

    &lt;/table&gt;
  &lt;/body&gt;

&lt;/html&gt;
&lt;!--Fim - Documento .html--&gt;</pre>

Criado o documento acima vamos construir nossa lógica.
  
O que queremos primeiramente é pegar o valor clicado nos números e colocá-los no input. Para isso vamos usar o evento clique que será atribuído aos botões dos números por meio da classe btnNumber, e dentro da função atribuída colocaremos o valor clicado mais o valor que ele terá.

<pre class="lang-javascript">$('.btnNumber').click(function(){  
   $('#inputResult').val($('#inputResult').val()+this.value)
});</pre>

Agora o que queremos é fazer o mesmo para pegarmos as operações clicadas. A lógica é a mesma, mas adicionaremos uma tratativa para acaso o botão de operação clicado seja o LIMPAR. Se clicar no botão LIMPAR o valor da tag input será esvaziado.

<pre class="lang-javascript">$('.btnOperacao').click(function(){  
  if(this.value != 'LIMPAR'){
    $('#inputResult').val($('#inputResult').val()+this.value)
  }
  else{
    $('#inputResult').val('')
  }
});</pre>

Bem, isso é uma calculadora, então temos que calcular. É neste momento onde gosto de expressar o amor ao javascript, basta passarmos a string com a conta montada na tag input para o método eval( ), para que ele execute o cálculo. O código abaixo mostra a atribuição da função e a execução do calculo e em seguida coloca o valor na tag input.

<pre class="lang-javascript">$('.btnResult').click(function(){  
    $('#inputResult').val(eval($('#inputResult').val()))
});</pre>

Finalmente vamos ao WebStorage, porque queremos gravar os valores e deixá-los disponíveis. Para gravarmos um valor no localStorage usamos o setItem(chave,valor), sempre gravaremos um par de chave e valor no WebStorage. Sabemos que queremos gravar o valor do resultado, mas a chave vamos deixar nas mãos do usuário. Quando ele clicar em salvar vamos dar ao usuário a opção dar um nome aquele resultado, e este nome será a chave a ser gravada com o valor.

<pre class="lang-javascript">$('.btnSalvar').click(function(){
    var lS = prompt("De um nome ao resultado para salvar.","");
    localStorage.setItem(lS,$('#inputResult').val());
})</pre>

Temos o botão LISTAR que pegará todos os valores salvos no localStorage e colocará na tabela abaixo da calculadora. Para pegarmos um valor usamos o getitem(chave), para sabermos quantos itens temos no localStorage usamos o localStorage.length e para pegar a chave usamos localStorage.key(index). Utilizando um while varremos localStorage e inserimos os valores na tabela.

<pre class="lang-javascript">$('.btnListar').click(function(){
  var tamanho = localStorage.length;
  var chave = '';
  var valor = '';

  if(document.getElementById("tableResults").rows.length &gt; 1)  {
    for(var t = document.getElementById("tableResults").rows.length; t &gt; 1; t--){
      document.getElementById("tableResults").deleteRow(1);
    }
  }

  var numOfCols =  document.getElementById("tableResults").rows[document.getElementById("tableResults").rows.length-1].cells.length;

  for(var c = 0; c &lt; tamanho;c++){
    chave = localStorage.key(c);
    valor = localStorage.getItem(chave);
    var newRow = document.getElementById("tableResults").insertRow(document.getElementById("tableResults").rows.length);

    for (var j = 0; j &lt; numOfCols; j++) {
      newCell = newRow.insertCell(j);

      if(j==0){
       newCell.innerHTML = chave.toUpperCase();
     }else if(j == 1){
       newCell.innerHTML = valor;
     }
   }
 }
})</pre>

A ultima lógica é a de limpar o localStorage com os dados salvos. Usamos o localStorage.clear() para limpar todos os itens. Veja como:

<pre class="lang-javascript">$('.btnApagar').click(function(){
   localStorage.clear()					
})</pre>

Estilo é importante, não é o nosso foco, mas é importante, então vamos implementar algum estilo.

<pre class="lang-css">button{
  width:27.5px;
}
.btnListar,.btnSalvar,.btnApagar{
  width:155px;
}
#btnLimpar{
  width:90px; 
}
#inputResult{
  text-align: center;
}
table.tabela tbody tr:nth-child(odd){
  background-color: #E9E9E9;
}</pre>

Este é o código que temos.Vamos ver como o navegador (Chrome) nos possibilita inspecionar o elemento.
  
Execute o documento no navegador e aperte F12. Aparecerá a tela do lado direito aperte a seta à esquerda do Local Storage para visualizar os dados salvos pelo documento em execução. No caso abaixo, ainda não temos nenhum valor salvo.

[<img class="alignnone size-medium wp-image-40582" alt="ws1" src="http://tableless.com.br/uploads/2014/01/ws1-588x171.png" width="588" height="171" srcset="uploads/2014/01/ws1-588x171.png 588w, uploads/2014/01/ws1-329x95.png 329w, uploads/2014/01/ws1-660x192.png 660w, uploads/2014/01/ws1.png 970w" sizes="(max-width: 588px) 100vw, 588px" />][1]

Faça qualquer conta.
  
[<img class="alignnone size-medium wp-image-40583" alt="ws2" src="http://tableless.com.br/uploads/2014/01/ws2-226x310.png" width="226" height="310" srcset="uploads/2014/01/ws2-226x310.png 226w, uploads/2014/01/ws2-122x168.png 122w, uploads/2014/01/ws2.png 262w" sizes="(max-width: 226px) 100vw, 226px" />][2]

Agora clique em igual (=) para obter o resultado.
  
[<img class="alignnone size-medium wp-image-40584" alt="ws3" src="http://tableless.com.br/uploads/2014/01/ws3-237x310.png" width="237" height="310" srcset="uploads/2014/01/ws3-237x310.png 237w, uploads/2014/01/ws3-128x168.png 128w, uploads/2014/01/ws3.png 264w" sizes="(max-width: 237px) 100vw, 237px" />][3]

Clicando em salvar, abriremos um prompt para ser digitado o nome do resultado que será utilizado para identificar o valor.
  
[<img class="alignnone size-medium wp-image-40585" alt="ws4" src="http://tableless.com.br/uploads/2014/01/ws4-588x156.png" width="588" height="156" srcset="uploads/2014/01/ws4-588x156.png 588w, uploads/2014/01/ws4-329x87.png 329w, uploads/2014/01/ws4-660x176.png 660w, uploads/2014/01/ws4.png 944w" sizes="(max-width: 588px) 100vw, 588px" />][4]

Depois de clicar em OK, abra o inspetor de elementos Developer Tools clique no botão de refresh no rodapé e você verá o valor salvo.
  
[<img class="alignnone size-medium wp-image-40586" alt="ws5" src="http://tableless.com.br/uploads/2014/01/ws5-588x162.png" width="588" height="162" srcset="uploads/2014/01/ws5-588x162.png 588w, uploads/2014/01/ws5-329x91.png 329w, uploads/2014/01/ws5-660x182.png 660w, uploads/2014/01/ws5.png 936w" sizes="(max-width: 588px) 100vw, 588px" />][5]

Execute mais um calculo e salve seu valor. Agora clique em LISTAR VALORES e assim serão exibidos todos os valores no localStorage.
  
[<img class="alignnone size-medium wp-image-40587" alt="ws6" src="http://tableless.com.br/uploads/2014/01/ws6-242x310.png" width="242" height="310" srcset="uploads/2014/01/ws6-242x310.png 242w, uploads/2014/01/ws6-131x168.png 131w, uploads/2014/01/ws6.png 264w" sizes="(max-width: 242px) 100vw, 242px" />][6]

Clicando em APAGAR VALORES os dados sumirão e não serão mais visualizados no Developers Tools e não serão listados na tabela.

Para finalizarmos temos que esclarecer que a maneira de se usar o sessionStorage é a mesma do localStorage. O que deve ficar claro é que ao usar o sessionStorage todos os dados salvos serão perdidos ao se fechar o navegador. O exemplo acima pode ser adaptado ao sessionStorage sem problemas. Veja o exemplo funcionando: <a title="EXEMPLO" href="http://jsfiddle.net/bruiz/d5prC/" target="_blank">EXEMPLO</a>

Bons estudos e bom trabalho!

 [1]: http://tableless.com.br/uploads/2014/01/ws1.png
 [2]: http://tableless.com.br/uploads/2014/01/ws2.png
 [3]: http://tableless.com.br/uploads/2014/01/ws3.png
 [4]: http://tableless.com.br/uploads/2014/01/ws4.png
 [5]: http://tableless.com.br/uploads/2014/01/ws5.png
 [6]: http://tableless.com.br/uploads/2014/01/ws6.png