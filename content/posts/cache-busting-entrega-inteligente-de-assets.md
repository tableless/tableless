---
title: 'Cache busting: entrega inteligente de assets'
author: James Clébio
type: post
date: 2015-06-18
excerpt: Sabe quando você faz o deploy com aquele ajuste no JS ou CSS e o usuário não consegue visualizar essas alterações por conta do cache do browser? Então, cache busting pode lhe poupar desse contratempo.
url: /cache-busting-entrega-inteligente-de-assets/
categories:
  - Técnicas e Práticas
tags:
  - cache
  - grunt
  - performance

---
## Definição

Cache busting nada mais é do que uma técnica para contornar o problema do carregamento de versões antigas dos assets armazenados em cache no navegador do cliente.

## Problema

Na verdade, essa é uma questão de longa data. Muitos desenvolvedores utilizam-se do incremento de variáveis com códigos aleatórios no final das chamadas (querystrings) dos assets para contornar o problema, o que, de acordo com [Steve Souders][1], guru em performance de sites na web, não é uma boa prática.

<pre class="lang-html">&lt;link rel="stylesheet" href="assets/main.css?v=786523"&gt; &lt;!-- NÃO RECOMENDADO! --&gt;
</pre>

Segundo Souders, [o uso de querystrings não é bom][2] porque faz com que normalmente o browser recarregue o asset da origem. Para o ambiente de desenvolvimento isso seria o ideal. Para o usuário final isso não seria bom, pois o comportamento de seu navegador seria alterado em termos do número de conexões que são abertas, ignorando o uso do cache e comprometendo a performance de carregamento da página.

## Solução

Para resolver o problema sem a utilização de querystrings, o ideal é que todos os arquivos de assets que estão sendo requisitados na página sejam renomeados. Logicamente que as chamadas para esses assets renomeados também precisam ser atualizadas na página. Sabemos que fazer esse processo manualmente seria algo árduo, quase insano. Então como fazê-lo de forma elegante, automatizada?

A fórmula mágica para que isso aconteça de maneira prática é o [grunt-cache-bust][3], um plugin para o [Grunt][4].

### Show me the code

Vou supor que você já conhece o [Grunt][5] e que há uma _index.html_ na raiz de seu projeto, ok? Sendo assim, irei focar apenas na utilização do plugin.

A princípio você só precisa seguir 4 passos básicos para usar o grunt-cache-bust:

1. Instale o plugin usando o seguinte comando:

<pre class="lang-sh">npm install grunt-cache-bust --save-dev
</pre>

2. Em seu _Gruntfile.js_, adicione a seguinte propriedade ao objeto passado como parâmetro em _grunt.initConfig_:

<pre class="lang-js">cacheBust: {
  options: {
    encoding: 'utf8',
    length: 16
  },
  scripts: {
    files: [{
      src: ['index.html']
    }]
  }
}
</pre>

3. Ainda em seu _Gruntfile.js_, adicione a seguinte linha para ativar o plugin:

<pre class="lang-js">grunt.loadNpmTasks('grunt-cache-bust');
</pre>

4. Tudo certo, agora é só rodar a task e voilà!

<pre class="lang-sh">grunt cacheBust
</pre>

### Resultado

Lembra que na raíz de seu projeto há uma _index.html_? Então, basicamente a task vai varrer esse documento buscando por chamadas de assets (CSS, JS, imagens e favicons), copiar esses arquivos com um novo nome e atualizar o source de cada chamada encontrada com o novo nome do arquivo. Esse novo nome terá o formato {nome}.{hash}.{extensão}, onde {hash} seria um código aleatório.

_index.html_ antes:

<pre class="lang-html">&lt;script src="assets/main.js"&gt;&lt;/script&gt;</pre>

_index.html_ depois:

<pre class="lang-html">&lt;script src="assets/main.6419373d85d7afe3.js"&gt;&lt;/script&gt;
</pre>

Lindo, né?

Vale lembrar que o plugin irá ignorar automaticamente chamadas que apontam para CDNs.

A propriedade [options][6] do plugin oferece uma porção de possibilidades interessantes que flexibilizam a utilização do cache busting, como por exemplo manter ou não os arquivos originais dos assets requisitados, escolher o algoritmo e tamanho das hashes, ignorar chamadas de assets através de regex, etc. Enfim, considere dar uma boa olhada na [documentação oficial do plugin][7].

## Conclusão

Cache busting é algo realmente útil no ciclo de desenvolvimento web. Chega de _Cmd+Shift+R_ ou _Ctrl+F5_, né?

Se você tem alguma outra solução para essa questão, utilizando Gulp ou outra ferramenta, conta pra gente aqui nos comentários. A comunidade agradece! ;D

 [1]: http://stevesouders.com/
 [2]: http://www.stevesouders.com/blog/2008/08/23/revving-filenames-dont-use-querystring/
 [3]: https://github.com/hollandben/grunt-cache-bust
 [4]: http://tableless.com.br/grunt-voce-deveria-estar-usando/
 [5]: http://gruntjs.com/
 [6]: https://github.com/hollandben/grunt-cache-bust#options
 [7]: https://github.com/hollandben/grunt-cache-bust#getting-started