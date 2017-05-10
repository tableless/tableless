---
title: Melhorando a exibição de tabelas com jQuery
author: Davi Ferreira
type: post
date: 2011-03-14
excerpt: Pode até ser meio irônico (já que estamos no Tableless!), mas neste artigo você aprende a dar um upgrade nas tabelas do seu site ou da sua aplicação web utilizando algumas técnicas jQuery.
url: /melhorando-exibicao-tabelas-jquery/
tweetbackscheck:
  - 1356390494
shorturls:
  - 'a:3:{s:9:"permalink";s:58:"http://tableless.com.br/melhorando-exibicao-tabelas-jquery";s:7:"tinyurl";s:26:"http://tinyurl.com/3v6c35h";s:4:"isgd";s:19:"http://is.gd/Ytlonr";}'
twittercomments:
  - 'a:18:{i:154615976267223040;s:7:"retweet";i:155083394810781698;s:7:"retweet";i:154616999388004352;s:7:"retweet";i:154616211605434368;s:7:"retweet";i:155435615784157184;s:7:"retweet";i:155413305966592001;s:7:"retweet";i:158879278535147521;s:7:"retweet";i:158005508240977920;s:7:"retweet";i:157983947568066560;s:7:"retweet";i:157976260235108354;s:7:"retweet";i:157969310793482242;s:7:"retweet";i:179074809936879618;s:7:"retweet";i:179074809878159360;s:7:"retweet";i:178877039108042752;s:7:"retweet";i:178844424304996353;s:7:"retweet";i:178842888539619328;s:7:"retweet";i:178831506565906432;s:7:"retweet";i:178824922548805632;s:7:"retweet";}'
tweetcount:
  - 57
dsq_thread_id: 503021281
categories:
  - JavaScript
  - JQuery
tags:
  - JavaScript
  - JQuery

---
Tabelas (aquelas com dados tabulares) são elementos importantes, principalmente em sistemas web. É muito comum a presença de tabelas na listagem dos registros em um aplicativo CRUD. Abaixo temos um exemplo de uma dessas tabelas:

<img src="http://tableless.com.br/uploads/2011/03/tabela.png" alt="Tabela HTML de exemplo" width="609" height="488" class="aligncenter size-full wp-image-3182" srcset="uploads/2011/03/tabela.png 609w, uploads/2011/03/tabela-300x240.png 300w" sizes="(max-width: 609px) 100vw, 609px" />

<a href="https://github.com/tableless/exemplos/tree/gh-pages/melhorando-exibicao-tabelas-jquery" target="_blank">Clique aqui para fazer o download do exemplo</a> ou <a href="http://tableless.github.com/exemplos/melhorando-exibicao-tabelas-jquery/" target="_blank">aqui para visualizar o exemplo no navegador</a>.

Utilizando algumas ferramentas jQuery vamos dar uma vida nova para tabelas e seus dados. Efeitos como uma cor diferente no mouseover, filtros, ordenação dos registros e paginação. Alguns desses efeitos utilizam apenas uma linha de código, enquanto outros serão proporcionados pelo plugin **tablesorter**.

### Cores e destaque

Uma maneira eficiente de melhorar a exibição dos dados é aplicar cores diferentes às linhas pares e ímpares da tabela. O jQuery oferece os seletores _odd_ e _even_ para esta função e a linha a seguir resolve nosso problema:

[cce lang=&#8221;jquery&#8221;]
  
$(&#8216;table > tbody > tr:odd&#8217;).addClass(&#8216;odd&#8217;);
  
[/cce]

Toda linha ímpar da nossa tabela receberá a classe odd, definida via CSS:

[cce lang=&#8221;css&#8221;]
  
table tbody tr.odd td{ background-color:#ffffcc; }
  
[/cce]

Caso você ainda não conheça muito bem a sintaxe HTML das tabelas, talvez esse seja o momento. É importante que suas tabelas possuam os elementos _thead_ e _tbody_ para nossos exemplos funcionarem.

Outro detalhe do código jQuery exibido acima é a utilização do sinal &#8220;>&#8221; no seletor. Isso significa que o método será executado apenas no primeiro _tbody_ filho da tabela e em suas _trs_ filhas diretas, evitando que, caso exista uma outra tabela dentro da sua tabela, ela também receba a classe em suas linhas, podendo gerar alguma confusão.

E que tal destacar as linhas da tabela toda vez que o usuário passar o mouse sobre elas? Nesse caso utilizaremos o método _hover_:

[cce lang=&#8221;jquery&#8221;]
  
$(&#8216;table > tbody > tr&#8217;).hover(function(){
    
$(this).toggleClass(&#8216;hover&#8217;);
  
});
  
[/cce]

[cce lang=&#8221;css&#8221;]
  
table tbody tr.hover td{ background-color:#a9d0f5; }
  
[/cce]

O _hover_ pode receber duas funções como parâmetros, a primeira para o mouseover e a segunda para o mouseout. No nosso caso passamos apenas uma função que será executada em ambos os casos, aplicando o método _toggleClass_ na linha da tabela, adicionando a classe hover. O que o _toggleClass_ faz é ativar/desativar automaticamente a classe especificada.

### Selecionando registros

Agora vamos falar dos checkboxes da nossa tabela. Toda vez que o usuário marcar o checkbox de uma linha, a mesma deve receber uma classe (selected) que aplicar uma outra cor diferente, indicando que ela foi selecionada. Os checkboxes da nossa tabela poderiam servir, por exemplo, para uma exclusão em massa, ou exportação de dados.

[cce lang=&#8221;jquery&#8221;]
  
$(&#8216;table > tbody > tr > td > :checkbox&#8217;).bind(&#8216;click change&#8217;, function(){
    
var tr = $(this).parent().parent();
    
if($(this).is(&#8216;:checked&#8217;)) $(tr).addClass(&#8216;selected&#8217;);
    
else $(tr).removeClass(&#8216;selected&#8217;);
  
});
  
[/cce]

[cce lang=&#8221;css&#8221;]
  
table tbody tr.selected td{ background-color:#a9f5a9!important; }
  
[/cce]

Note que associamos a função a dois eventos: click e change. O change vai ser importante quando implementarmos a função de marcar/desmarcar todos. Primeiro verificamos se o checkbox foi marcado ou desmarcado através do método/seletor **.is(&#8216;:checked&#8217;)** e, de acordo com a situação, adicionamos ou removemos a classe selected.

O checkbox localizado no cabeçalho da nossa tabela marca ou desmarca todos os registros.

[cce lang=&#8221;jquery&#8221;]
  
$(&#8216;#marcar-todos&#8217;).click(function(){
    
$(&#8216;table > tbody > tr > td > :checkbox&#8217;)
      
.attr(&#8216;checked&#8217;, $(this).is(&#8216;:checked&#8217;))
      
.trigger(&#8216;change&#8217;);
  
});
  
[/cce]

Acima você pode ver que o próprio seletor **.is(&#8216;:checked&#8217;)** funciona como o true/false do atributo checked, ou seja, se marcarmos o checkbox do cabeçalho marcamos também todos os checkboxes dos registros. Precisamos também &#8220;forçar&#8221; o evento change para marcar/desmarcar as linhas com a classe selected. Isso é necessário porque o jQuery só considera como change quando o evento é aplicado com o mouse. A simples troca do atributo checked via jQuery não é considerado como evento change (não sei muito bem porque :)).

### Pesquisando nos registros da tabela

Dependendo da sua tabela e dos dados exibidos é possível fazer uma busca rápida utilizando apenas javascript.

[cce lang=&#8221;html&#8221;]

[/cce]

Toda vez que o usuário digitar alguma coisa no campo pesquisar a tabela será filtrada automaticamente. Para isso utilizaremos o método/evento keydown. Também é importante desabilitar o submit do form, evitando que, ao pressionar enter no campo de pesquisa, o formulário seja enviado.

[cce lang=&#8221;jquery&#8221;]
  
$(&#8216;#pesquisar&#8217;).keydown(function(){
    
var encontrou = false;
    
var termo = $(this).val().toLowerCase();
    
$(&#8216;table > tbody > tr&#8217;).each(function(){
      
$(this).find(&#8216;td&#8217;).each(function(){
        
if($(this).text().toLowerCase().indexOf(termo) > -1) encontrou = true;
      
});
      
if(!encontrou) $(this).hide();
      
else $(this).show();
      
encontrou = false;
    
});
  
});

// desabilita envio do formulário
  
$(&#8216;form&#8217;).submit(function(e){ e.preventDefault(); });
  
[/cce]

No script acima estamos utilizando dois métodos/funções puros de javascript: **toLowerCase** e **indexOf**. O primeiro transforma os caracteres de uma string para minúsculo e o **indexOf** procura por uma ocorrência do termo pesquisado na string, retornando sua posição. O valor -1 significa que o termo não foi encontrado. Para cada linha da tabela, pesquisamos em suas células (td) pelo termo digitado no campo. Se o termo não for encontrado, a linha é escondida através do método **hide**.

### Bônus: tablesorter

Pra finalizar, vamos dar uma passada em um poderoso plugin jQuery para tabelas: tablesorter. Como o próprio nome sugere, sua principal função é ordenar os dados da tabela clicando em seus cabeçalhos. No entanto, ele também vem acompanhado de um plugin para paginação dos dados utilizando somente javascript.

[cce lang=&#8221;jquery&#8221;]
  
$(&#8220;table&#8221;)
    
.tablesorter({
      
dateFormat: &#8216;uk&#8217;,
      
headers: {
        
0: {
          
sorter: false
        
},
        
5: {
          
sorter: false
        
}
      
}
    
})
    
.tablesorterPager({container: $(&#8220;#pager&#8221;)})
    
.bind(&#8216;sortEnd&#8217;, function(){
      
$(&#8216;table > tbody > tr&#8217;).removeClass(&#8216;odd&#8217;);
      
$(&#8216;table > tbody > tr:odd&#8217;).addClass(&#8216;odd&#8217;);
    
});
  
[/cce]

[cce lang=&#8221;html&#8221;]

<div class="pager">
</div>

[/cce]

Não vou entrar muito em detalhes sobre as configurações do plugin, somente algumas observações. A propriedade _dateFormat_ informa o formato de data a ser utilizado, no nosso caso dd/mm/aaaa (formato padrão na Inglaterra, logo o &#8216;uk&#8217;). Os headers 0 (o checkbox de marcar todos) e 5 (as ações editar/excluir) não devem permitir ordenação, devem estar desabilitados.

Adicionamos também o método **tabelSorterPager**. O HTML necessário é o exibido acima, com a quantidade de registros por página, os botões de primeira, anterior, próxima, última e um input para exibição das páginas.

E, por último, toda vez que a ordenação for aplicada, precisamos re-aplicar as cores nas linhas ímpares (que agora passaram a ser outras). Para isso utilizamos o evento personalizado do tabelesorter, **sortEnd**.