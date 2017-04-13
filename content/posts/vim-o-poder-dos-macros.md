---
title: 'Vim: o poder dos macros'
author: weslleyaraujo
type: post
date: 2015-04-28
excerpt: Execute a mesma ação múltiplas vezes dentro de vim.
url: /vim-o-poder-dos-macros/
categories:
  - Código
  - Editores

---
No nosso dia-a-dia em muitas situações diferentes temos que executar a mesma ação em um arquivo por diversas vezes, e com certeza o seu editor oferece à sua maneira uma forma muito eficiente de lidar com isso.

No vim isso não é diferente, uma feature muito poderosa e ainda pouco explorada são os _macros_. Legal, mas o que é isso?

Esses _macros_ são uma sequencia de comandos que vão ser gravados numa espécie de buffer do vim e você pode executa-los quantas vezes desejar.

## Em prática

Vamos supor que temos uma lista de itens como strings escrito dessa maneira:

<pre class="lang-html">'foo', 'bar', 'example', 'text'</pre>

e o nosso objetivo é que cada item dessa lista fique uma abaixo da outra, também queremos que a primeira letra de cada item seja convertida para maiúscula:

<pre class="lang-html">'Foo',
'Bar',
'Example',
'Text'
</pre>

Para iniciarmos a gravação de um macro deve ser pressionada tecla **q**, note que a palavra **recording** vai aparecer na parte inferior do editor:

<img class="alignnone size-full wp-image-48305" src="http://tableless.com.br/uploads/2015/04/macro-01.gif" alt="macro-01" width="475" height="145" />

A partir desse momento qualquer tecla pressionada vai ser gravada, e se mais uma vez pressionarmos **q** em _NORMAL MODE_ a gravação vai ser concluída.

O que devemos fazer agora é executar um conjunto de comandos para atingirmos o nosso objetivo, que nesse caso seria algo como:

<ul class="task-list">
  <li>
    <code>q</code> : inicia a gravação do macro
  </li>
  <li>
    <code>w</code> : move uma &#8220;palavra&#8221; no cursor
  </li>
  <li>
    <code>v</code> : entra no &#8220;<em>VISUAL MODE</em>&#8221; (automaticamente seleciona o caractere em que o cursor está em foco)
  </li>
  <li>
    <code>U</code>: transforma o que foi selecionado em maiúsculo
  </li>
  <li>
    <code>w</code>: move uma &#8220;palavra&#8221; no cursor
  </li>
  <li>
    <code>w</code>: move uma &#8220;palavra&#8221; no cursor
  </li>
  <li>
    <span style="font-family: monospace">i</span>: entra no &#8220;<em>INSERT MODE</em>&#8220;
  </li>
  <li>
    <code>&lt;backspace&gt;</code>: deleta o espaço entre a virgula e a próxima palavra
  </li>
  <li>
    <code>&lt;enter&gt;</code>: insere a quebra da linha
  </li>
  <li>
    <code>&lt;esc&gt;</code>: volta para o &#8220;<em>NORMAL MODE</em>&#8220;
  </li>
  <li>
    <code>q</code>: finaliza a gravação do macro
  </li>
</ul>

Executando isso temos:

<img class="alignnone size-full wp-image-48308" src="http://tableless.com.br/uploads/2015/04/macro-02.gif" alt="macro-02" width="475" height="145" />

Bacana! Ja temos os comandos gravados em memória, agora vamos usar o atalho **@q** para a execução em cada item:

<img class="alignnone size-full wp-image-48310" src="http://tableless.com.br/uploads/2015/04/macro-03.gif" alt="macro-03" width="475" height="145" />

e voilà, temos nossa lista como queriamos 🙂

### Conclusão

Com o tempo o uso do macro dentro do vim se torna algo automático, você começa a perceber padrões e cada vez mais começa a usar essa feature de maneira inteligente que vai poupar muito do seu tempo.

Nesse artigo foi utilizado um exemplo muito simples, mas imagine quantas possibilidades você pode alcançar com os _macros_ desde tarefas complexas como copy/paste em arquivos diferentes, alinhamentos e etc.

Se você achou interessante entenda mais sobre as diversas açoes dos _macros_ na documentação oficial do vim <a href="http://vim.wikia.com/wiki/Macros" rel="noreferrer">nesse link</a>.