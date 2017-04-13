---
title: 'Desempenho e eventos jQuery: event delegation'
author: leobetosouza
type: post
date: 2015-06-10
excerpt: Como a utilização de event delegation com o jQuery pode ser otimizada.
url: /desempenho-e-eventos-jquery-event-delegation/
categories:
  - JavaScript
  - JQuery

---
Todo mundo que leva a experiência de uso da sua página um pouco a sério já se pegou pensando &#8220;uso um plugin pronto ou faço eu mesmo?&#8221; e caso cogite usar algo já pronto, acaba em dúvida sobre quais das várias opções usar.

Esses dias eu resolvi estudar o código de algumas opções disponíveis. Fiquei com medo.

Existem algumas falhas que nós desenvolvedores cometemos no desenvolvimento usando jQuery que são críticas e comuns. Hoje eu quero falar sobre uma delas em especial:

# Excesso de _event listeners_ pela página

Acho que todo mundo já escreveu um código similar a este:

<pre class="lang-javascript">$( '.foo' ).click( callback );</pre>

Você sabe o que esse código faz? Ele coloca em todos os elementos com a classe _foo_ da sua página um _event listener_ que dispara um _callback handler_ sempre que o usuário clicar nele. No caso esse _listener_ dispara a função _callback_. Legal e útil, né?

Agora imagine que você tenha 100 elementos com a classe _foo_. Serão 100 _event listeners_ para o navegador tomar conta. Imagine que você coloque outros _listeners_ para outros eventos e seletores. Dá pra perceber que essa conta não escala muito bem, né?

A melhor maneira de resolver isso é com _event delegation_.

# Event Delegation

Vamos supor que nossa class _foo_ seja aplicada à `<tr>` de um tipo de tabela específica. Algo assim:

<pre class="lang-javascript">&lt;table class="tar"&gt;
    &lt;tr class="foo"&gt;...&lt;/tr&gt;
    &lt;tr class="foo"&gt;...&lt;/tr&gt;
    ...
&lt;/table&gt;</pre>

Se a gente colocar um _listener_ diretamente na class da tabela (._tar_) mandando ele ouvir os eventos internos que ocorrerem nos elementos (._foo_), vamos reduzir o número de _listeners_ espalhados pela página.

Como se faz isso, Léo?

Assim:

<pre class="lang-javascript">$( '.tar' ).on( 'click', '.foo', callback );</pre>

Essa linha de código basicamente diz: sempre que houver um evento de clique nos elementos com classe _tar_ selecionados, verifique se esse evento foi disparado por um elemento interno com a classe _foo_. Se sim, execute a função _callback_.

Isso pode ser feito pois os eventos do DOM normalmente são transmitidos (ou propagam) (ou propagam) à todos os seus elementos pais na árvore [DOM][1]. Esse é o caso do evento de clique.

Logo, o exemplo acima teria quase o mesmo efeito caso fosse escrito desse jeito:

<pre class="lang-javascript">$( document ).on( 'click', '.foo', callback );</pre>

Você pode adicionar um _event listener_ para responder a cliques no documento inteiro e só executar o _callback_ caso o clique tenha ocorrido em elementos especificados, nesse caso ‘_.foo_’.

Lembra que a gente está falando de melhora de desempenho? Se você forçar o navegador a ouvir todos os cliques na sua página e só executar em casos específicos, você estará disperdiçando recursos. Não faça isso, a não ser que seja extremamente necessário. Busque sempre  fixar seus eventos em elementos _wrappers_, como aquele <table> do exemplo.

## **Elementos adicionados dinâmicamente**

Usar _event delegation_ ainda garante um bônus: ter _event handlers_ disparados por elementos que foram adicionados dinamicamente à página.

Digamos que o _listener_ seja criado durante o [document ready][2], como tradicionalmente é feito:

<pre class="lang-javascript">$( document ).ready(function () {
    $( '.foo' ).on( 'click', callback );
});</pre>

O _handler_ será anexado somente aos elementos com a classe _foo_ existentes no momento em que o documento for carregado.

Se posteriormente você criar novos elementos com a classe _foo_ (como respostas à ações do usuário, AJAX, etc.), eles não vão ter o _event listener_ e não ocorrerá o efeito desejado quando o usuário clica-los.

Se nós delegarmos isso para um elemento pai das <tr class=&#8221;foo&#8221;>, como no caso o <table class=&#8221;tar&#8221;>, não teremos esse problema.

# As _DevTools_ são suas amigas

É possível inspecionar o documento através do _DevTools_ do seu navegador e identificar quais _event listeners_ estão anexados em cada elemento. Essa pode ser uma boa estratégia inicial para auditar a sua página e verificar quais eventos podem ser anexados em elementos mais específicos, além de eliminar possíveis excessos no _document_.

<div id="attachment_49318" style="width: 1450px" class="wp-caption alignnone">
  <a href="http://tableless.com.br/uploads/2015/06/devtools-chrome-evtdelegation.jpg"><img class="size-full wp-image-49318" src="http://tableless.com.br/uploads/2015/06/devtools-chrome-evtdelegation.jpg" alt="Screenshot de uma janela do Google Chrome mostrando a aba de eventos do inspector" width="1440" height="223" /></a>
  
  <p class="wp-caption-text">
    Aba de eventos do Chrome DevTools
  </p>
</div>

[<img class="alignnone size-full wp-image-49319" src="http://tableless.com.br/uploads/2015/06/devtools-firefox-evtdelegation.jpg" alt="Screenshot de uma janela do Mozilla Firefoz Developer Edition mostrando os de eventos no inspector" width="1440" height="296" />][3]

# Conclusão

Cada _event listener_ que criamos é incluído na memória utilizada pelo navegador, o excesso deles pode causar um uso excessivo de memória e deixar a sua página bem pesada. Assim como não é recomendável observar os eventos em muitos elementos, não é para fixar tudo em um único elemento pai, como o próprio _document_, pois você corre o risco de ter muitos _listeners_ sendo disparados ao mesmo tempo atoa, o que pode deixar as interações de sua página bem lentas.

Nem muito específico, nem muito genérico. O importante é observar que a utilização de _event delegation_ com o jQuery pode ser otimizada e que se deve tomar cuidado para não trocar uma má prática por outra.

No próximo artigo vou falar sobre como evitar colisão e duplicação de eventos.

 [1]: https://developer.mozilla.org/pt-BR/docs/Glossario/DOM
 [2]: http://api.jquery.com/ready/
 [3]: http://tableless.com.br/uploads/2015/06/devtools-firefox-evtdelegation.jpg