---
title: Templates e jQuery – parte 1
author: Davi Ferreira
type: post
date: 2010-11-08
excerpt: Separar a programação do HTML é uma prática constante no desenvolvimento web. Durante muito tempo, no entanto, o JavaScript ficou de fora dessa. Chegou a hora de reverter este quadro.
url: /templates-e-jquery-parte-1/
aktt_notify_twitter:
  - yes
tweetbackscheck:
  - 1356440751
shorturls:
  - 'a:3:{s:9:"permalink";s:50:"http://tableless.com.br/templates-e-jquery-parte-1";s:7:"tinyurl";s:26:"http://tinyurl.com/3zhfa3b";s:4:"isgd";s:19:"http://is.gd/WkuhWP";}'
twittercomments:
  - 'a:17:{i:12589426408431616;s:6:"136321";i:14319027266527232;s:7:"retweet";i:14318747263176704;s:7:"retweet";i:12654536934035457;s:7:"retweet";i:12653002087211009;s:7:"retweet";i:17524290672926720;s:7:"retweet";i:60675013988204544;s:6:"137642";i:129613816362319873;s:7:"retweet";i:129543420053172224;s:7:"retweet";i:129543327329689600;s:7:"retweet";i:129541797994184704;s:7:"retweet";i:129541699046350848;s:7:"retweet";i:186442457112780800;s:7:"retweet";i:268663122141786112;s:7:"retweet";i:268553287744225281;s:7:"retweet";i:273469806190149632;s:7:"retweet";i:273465631557443585;s:7:"retweet";}'
tweetcount:
  - 25
dsq_thread_id: 503039705
categories:
  - Artigos
  - Código
  - JavaScript
  - JQuery
  - Técnicas e Práticas
tags:
  - 2010
  - JavaScript
  - JQuery

---
Na dieta diária do desenvolvedor front-end sempre esteve presente uma saladinha de HTML com JavaScript. Principalmente quando precisamos implementar um código com funcionalidades AJAX. Por exemplo, imagine que o bloco abaixo representa o retorno de um getJSON() da vida:

<pre class="lang-javascript">for( i in noticias )
{
    html = '&lt;li&gt;&lt;h3&gt;' + noticias[i]['titulo'] + '&lt;/h3&gt;';
    html += '&lt;span class="data"&gt;' + noticias[i]['data_publicacao'] + '&lt;/span&gt;';
    html += '&lt;span&gt;' + noticias[i]['chamada'] + '&lt;/span&gt;';
    html += '&lt;span&gt;&lt;a href="' + link + '"&gt;Veja mais&lt;/a&gt;&lt;/span&gt;&lt;/li&gt;';
}
$('#noticias').append( html );</pre>

O problema do código acima é que ele é pouco reutilizável e de baixa legibilidade, além de ser muito chato de digitar e prestar manutenção, com todas as concatenações e índices. Foi pensando nisso que o pessoal da Microsoft desenvolveu o plugin <a href="http://github.com/jquery/jquery-tmpl" rel="external" title="jQuery.tmpl() no GitHub">jQuery.tmpl()</a> (tmpl de template, é claro), aceito recentemente na <a href="http://api.jquery.com/jquery.tmpl/" rel="external" title="Página do plugin jQuery.tmpl() na documentação oficial do jQuery">API oficial do jQuery</a>.

Mas não confunda template com separar o JavaScript do HTML no sentido &#8220;físico&#8221; da coisa (colocando tudo que é JS em arquivos externos, outra boa prática para desenvolvedores). Neste texto você aprende a utilizar blocos de código HTML nas suas interações via jQuery, substituindo variáveis por conteúdos de saída/retorno.

## Definindo seu template

Quem já trabalhou ou já viu algum tipo de implementação de templates não vai ter muitas dificuldades para se adaptar à forma de templating do jQuery. O conceito básico é definir um modelo padrão para um bloco de código e trabalhar com substituição de variáveis. O template do bloco mostrado anteriormente seria o seguinte:

<pre class="lang-javascript">var tpl_noticia = '&lt;li&gt;&lt;h3&gt;${titulo}&lt;/h3&gt;&lt;span class="data"&gt;${data_publicacao}&lt;/span&gt;&lt;span&gt;${chamada}&lt;/span&gt;&lt;span&gt;&lt;a href="${link}"&gt;Veja mais&lt;/a&gt;&lt;/span&gt;&lt;/li&gt;';</pre>

Abaixo você confere uma chamada simples para nosso template. (Note que os dados de exemplo estão armazenados em um objeto JSON.)

<pre class="lang-javascript">var noticias = [
    {
        titulo : 'Notícia 1',
        data_publicacao : '28/10/2010 20h31',
        chamada : 'Chamada da notícia 1',
        link : '/noticia-1/',
    },
    {
        titulo : 'Notícia 2',
        data_publicacao : '28/10/2010 20h32',
        chamada : 'Chamada da notícia 2',
        link : '/noticia-2/',
    },
    {
        titulo : 'Notícia 3',
        data_publicacao : '28/10/2010 20h33',
        chamada : 'Chamada da notícia 3',
        link : '/noticia-3/',
    }
];

$(function(){
    // aplica o template tpl_noticias aos dados e adiciona a lista ao elemento ul
    $.tmpl( tpl_noticia, noticias ).appendTo( 'ul#noticias' );
});</pre>

Além do .appendTo(), você pode ainda utilizar os seguintes métodos para trabalhar co templates: .prependTo(), .insertAfter() e .insertBefore().

## Tipos de dados

### ${var}

Provavelmente a que você vai utilizar com mais frequência. Representa variáveis ou expressões JavaScript, é um atalho para {= expr/var}.

<pre class="lang-javascript">var tpl = '&lt;li&gt;${nome}&lt;/li&gt;';
                
// exemplo de express&atilde;o
var tpl = '&lt;p class=""&gt;${formataData( data_publicacao )}&lt;/p&gt;';

var formataData = function( sdata )
{
    var meses = { 
        1 : 'Janeiro', 2 : 'Fevereiro', 3 : 'Mar&ccedil;o', 4 : 'Abril', 
        5 : 'Maio', 6 : 'Junho', 7 : 'Julho', 8 : 'Agosto', 9 : 'Setembro', 
        10 : 'Outubro', 11 : 'Novembro', 12 : 'Dezembro' 
    };
    var mes = parseInt( sdata.substr( 3, 2 ), 10 );
    var dia = sdata.substr( 0, 2 );
    var ano = sdata.substr( 6, 4 );
    return dia + ' de ' + meses[mes] + ' de ' + ano;
};</pre>

### {{each}}{{/each}}

Define um loop entre elementos de um array ou objeto javascript, dentro do escopo do template. Assim como a tag para expressões, também aceita métodos para tratar o valor. Suas variáveis internas são $index e $value (chave e valor do array/objeto, respectivamente). 

<pre class="lang-javascript">var tpl_artigo = '&lt;p&gt;&lt;h3&gt;${titulo}&lt;/h3&gt;{{each autores}}${$value.toUpperCase()}&lt;br /&gt;{{/each}}&lt;/p&gt;';

var artigos = [
    { 
        titulo: 'Javascript &amp; Acessibilidade', 
        autores: ['Davi Ferreira', 'Let&iacute;cia Stallone'],
        abstract: '&lt;strong&gt;Acessibilidade e Javascript&lt;/strong&gt;',
        },
    { 
        titulo: 'Humor no Javascript', 
        autores: ['Let&iacute;cia Stallone'],
        abstract: '&lt;strong&gt;Javascript pode ser bem engra&ccedil;ado&lt;/strong&gt;',
    },
    { 
        titulo: 'Boas pr&aacute;ticas', 
        autores: '',
        abstract: '&lt;strong&gt;Boas pr&aacute;ticas de desenvolvimento web&lt;/strong&gt;',
    }
];</pre>

### {{if}}{{else}}{{/if}}

Implementa condicionais dentro do template. Executa (ou não) uma determinada condição, baseada no valor/retorno da variável/expressão. Esta tag interpreta como _false_ qualquer valor nulo, 0 ou _undefined_.

<pre class="lang-javascript">var tpl_artigo = '&lt;li&gt;&lt;h3&gt;${titulo}&lt;/h3&gt;{{if autores.length}}Autor(es): {{else}}sem autor cadastrado{{/if}}{{each autores}}${$value.toUpperCase()}&lt;br /&gt;{{/each}}&lt;/li&gt;';</pre></p> 

### {{html}}

Caso você tente dar a saída no template de um conteúdo com tags HTML o jquery.tmpl() vai transformar as marcações em texto puro. Para que a saída aconteça também em HTML é necessário utilizar a tag especial {{html}}. 

<pre class="lang-javascript">var tpl_artigo = '&lt;li&gt;&lt;h3&gt;${titulo}&lt;/h3&gt;{{if autores.length}}Autor(es): {{else}}sem autor cadastrado{{/if}}{{each autores}}${$value.toUpperCase()}&lt;br /&gt;{{/each}}{{html abstract}}&lt;/li&gt;';</pre>

Deu pra perceber a potencialidade deste plugin para aplicações mais elaboradas, com diversas interações via AJAX? Você pode ter um .js só para seus modelos e parar de concatenar tudo e todos diretamente no código. As tags são bastante flexíveis, permitindo tanto variáveis simples como expressões mais avançadas.

Na parte 2 deste artigo veremos como implementar os templates com caching e ainda as tags avançadas {{wrap}} e {{tmpl}}.