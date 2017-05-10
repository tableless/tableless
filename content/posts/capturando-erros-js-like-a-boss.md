---
title: Capturando erros JS LIKE-A-BOSS
author: Almir Filho
type: post
date: 2012-12-12
excerpt: Hoje iremos aprender para que serve o evento window.onerror e como tirar proveito desta ótima utilidade.
url: /capturando-erros-js-like-a-boss/
tweetbackscheck:
  - 1356440102
shorturls:
  - 'a:3:{s:9:"permalink";s:31:"http://tableless.com.br/?p=7493";s:7:"tinyurl";s:26:"http://tinyurl.com/d6a2c8a";s:4:"isgd";s:19:"http://is.gd/j0XFrE";}'
twittercomments:
  - 'a:0:{}'
dsq_thread_id: 970809508
categories:
  - Código
  - JavaScript
tags:
  - aprenda
  - desenvolvimento web
  - JavaScript

---
O evento **onerror** é disparado quando há erros no script. Estes erros geralmente pertencem a duas categorias:

#### Erros de sintaxe

Antes de serem executados, _scripts_ passam por uma análise sintática (operação mais conhecida como _parsing_) – afim de encontrar erros de sintaxe antes da execução do _script_. Qualquer um dos erros abaixo são erros de sintaxe:

<pre class="lang-javascript">&lt;!-- string não fechada --&gt;
&lt;script&gt;"oops, fiz merd*&lt;/script&gt;
&lt;!-- for errado --&gt;
&lt;script&gt;for(;)&lt;/script&gt;
&lt;!-- ??? (só pode ser coisa de estagiário) --&gt;
&lt;script&gt;chamaFuncao() = 'estagiario maluco'&lt;/script&gt;</pre>

#### Erros de _runtime_ (Exceções não tratadas)

Um _script_ pode até ser válido sintaticamente, ou seja, pode ter sido analisado com sucesso pelo _parser_ JS, mas mesmo assim ainda pode haver erros em tempo de execução (_runtime_). Por exemplo:

<pre class="lang-javascript">// chamar métodos não definidos
dartVader.comerTorta() // <a title="dartVader.comerTorta()" href="http://d.pr/VRVy" target="_blank">clique aqui</a> para mais informações.
// ler índices inexistentes
var lordSidious = jedi[ 'palpatine' ];
// ler propriedades inexistentes
var paciencia = hanSolo.paciencia;
// mensagens de erro manuais
throw 'Noooooooooooooooooooo!';</pre>

## Erros: temos que pegar

Apenas precisamos tratar o evento **onerror** de **window**, e para isso precisamos definir o seguinte _callback_:

<pre>// navegadores antigos
window.onerror = function( message, filename, lineno ){
    // trate o erro
}

// navegadores modernos
window.addEventListener( 'error', function( event ){
    // a mensagem de erro
    console.log( event.message );
    // a url de onde ocorreu o erro
    console.log( event.filename );
    // o número da linha onde ocorreu o erro
    console.log( event.lineno );
});

// jQuery
$(window).on( 'error', function( event ){
    // event tem os mesmos dados do exemplo anterior
});</pre>

A função que trata o evento **onerror**recebe 3 valores (como mostrado acima):

  * **Mensagem**: A mensagem de erro que o navegador joga (**message** ou **event.message** dos trechos código acima). Por exemplo: &#8220;_Uncaught ReferenceError: comerTorta is not defined_&#8220;.
  * **URL**: O endereço URL de onde ocorreu o erro (**filename** ou **event.filename** dos trechos código acima).
  * **Linha**: O número da linha do documento ou _script_ de onde ocorreu o erro (**lineno** ou **event.lineno** dos trechos de código acima). Pode ser no contexto de um documento HTML (se o _script_ for _inline_) ou de um arquivo **.js** (se o _script_ for externo). Neste caso, o valor de **filename**/**event.filename** será o caminho de um arquivo **.js**.

Por padrão, a função retorna **false**, o que significa que a mensagem de erro será jogada no _console_ de erros. Se quisermos suprimir as mensagens de erro no _console_ (não aconselhável), apenas precisamos retornar **true**:

<pre class="lang-javascript">window.addEventListener( 'error', function( event ){
    return true;
});</pre>

## Customize mensagens de erro

Já que agora temos o poder de fazer o que quiser com nossas mensagens de erro, também podemos ter aparência customizada para elas. Podemos alcançar isso facilmente como no _script_ abaixo:

<pre class="lang-javascript">window.addEventListener( 'error', function( event ){
    var boxError = document.createElement( 'div' );
    boxError.className  = 'box-error';

    boxError.innerHTML  = '&lt;h4&gt;Erro de JS:&lt;/h4&gt;';
    boxError.innerHTML += '&lt;p class="msg"&gt;'+ event.message +'&lt;/p&gt;';
    boxError.innerHTML += '&lt;p&gt;Em: '+ event.filename +'&lt;/p&gt;';
    boxError.innerHTML += '&lt;p&gt;Linha: '+ event.lineno +'&lt;/p&gt;';

    document.body.appendChild( boxError );
    return false;
});</pre>

O _script_ acima basicamente cria uma nova **<div>**, monta o conteúdo da mensagem e a mostra no final. Agora é só definir o CSS para a classe **.box-error** e _voilá,_ mensagens de erro customizadas.

## Tenha feedback da sua aplicação

A maior utilidade que encontrei para isso é a possibilidade de fazer **_logging_ de erros**. Numa aplicação, poderíamos por exemplo, fazer uma _requisição_ _ajax_ para nosso servidor salvar as informações do erro corrente e uma base de dados qualquer, e assim poderíamos gerar relatórios de erros da nossa aplicação com base nestes dados coletados, ou seja, graças a estas informações, estaríamos promovendo uma atitude focada na melhoria constante dos serviços.

#### Mantendo as coisas simples com o Google Analytics

[<img class="alignnone size-full wp-image-7566" alt="" src="http://tableless.com.br/uploads/2012/12/Final-result.jpg" width="600" height="143" srcset="uploads/2012/12/Final-result.jpg 600w, uploads/2012/12/Final-result-300x71.jpg 300w" sizes="(max-width: 600px) 100vw, 600px" />][1]

Pra quem já usa o **Google Analytics**, aqui vai uma idéia que iria simplificar bastante o ato de fazer _log_ de erros: em vez de fazer uma requisição _ajax_ para o servidor da nossa aplicação, poderíamos simplesmente disparar <a title="Eventos customizados do Google Analytics" href="https://developers.google.com/analytics/devguides/collection/gajs/eventTrackerGuide?hl=pt-PT" target="_blank">eventos customizados do Google Analytics</a> (com o método **_trackEvent()**), e assim teríamos essas informações prontas com os relatórios bonitinhos da ferramenta – o que nos economizaria o trabalho de desenvolver toda uma estrutura para isso: criar uma tabela de erros no nosso banco de dados, escrever o _backend_ que receberia as requisições _ajax,_ e finalmente, implementar relatórios de erros.

## Suporte

O evento **window.onerror** é suportado por todos os navegadores atuais: Chrome 13+, Firefox 6.0+, Opera 11.60+, Safari 5.1+ e Internet Explorer 5.5+ (quem diria!).

 [1]: http://tableless.com.br/uploads/2012/12/Final-result.jpg