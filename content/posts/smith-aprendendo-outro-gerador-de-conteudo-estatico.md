---
title: 'Wintersmith: Outro gerador de conteúdo estático'
author: João Felix
type: post
date: 2014-01-15
excerpt: Conheça o Wintersmith, mais um gerador de conteúdo estático.
url: /wintersmith-aprendendo-outro-gerador-de-conteudo-estatico/
dsq_thread_id: 2125264349
categories:
  - Código
  - Técnicas e Práticas
tags:
  - front-end
  - wintersmith

---
## Primeiro, o que são os Geradores de Conteúdos Estáticos?

Diferente de plataformas como WordPress, Joomla e etc., os geradores de conteúdo estáticos servem para criar páginas de conteúdo sem a utilização de qualquer persistência ou dependência server-side, onde ao final, você possui um pacote de arquivos html e seus companheiros (css,javascript,imagens&#8230;).

O Tableless tem um artigo sobre [Jekyll][1], outro gerador de conteúdo estático. O Jekyll é usado pelo pessoal do Bootstrap.

## Segundo, o que é o [Wintersmith][2]?

O ponto de partida foi a escolha de qual gerador utilizar. Eu já possuía uma queda pelo [Jekyll][3] (devido à diversos blogs que eu acompanho o utilizarem) e uma [lista de 32 Geradores de Conteúdo Estáticos][4], porem, eu não queria utilizar Ruby (só não queria) e decidi procurar algo em Node.js (aproveitando a vibe), eis que surge o Wintersmith! O projeto é open-source e utiliza outros projetos open-source para criar um ambiente bem simples! Foi criado utilizando o [Markdown][5] (igual ao github) como conversor de texto para HTML, [Jade][6] para criação de templates e [Coffescript][7] para os plugins (muita coisa legal para aprender)!

Agora, chega de conversa e mão na massa (lembrando que ao final tem um link para você baixar todo o código do resultado).

## Instalando o Wintersmith

Neste artigo eu vou adotar como precedência que você já tenha o Node.js instalado e saiba do que se trata o [npm][8], mas nada impede de aprendermos mais sobre eles em um outro momento; Segue o comando de instalação:

    $ npm install wintersmith -g
    

## Criando o projeto

Estando com o pacote instalado, basta criar o seu projeto na pasta que desejar.

    $ wintersmith new
    

O template padrão do projeto é o de blog (existem também basic e webapp), o que atende bem à minha necessidade, mas você pode criar outros. Junto com a estrutura de arquivos, o Wintersmith já criará um conjunto de artigos bem explicativos que mostram o potencial da ferramenta, para visualizar como está o seu projeto, basta coloca-lo em peview:

    $ wintersmith preview
    

Ai pronto! Você já pode acessar http://localhost:8080 e ver o que está criado (Vale lembrar que enquanto estiver visualizando, qualquer alteração é refletida na pré-visualização sem a necessidade de executar o comando novamente).

## Personalizando o blog

Como a estrutura criada pelo projeto já é bem próxima à de um blog bem enxuto, precisei apenas fazer algumas mudanças de parametros, alterar os autores (dos artigos, claro!) e criar um template jade para os comentários (utilizando \[Disqus\]\[12\]).

Na raiz do projeto existe um arquivo chamado config.json e o padrão dele é:

    {
      "locals": {
        "url": "http://localhost:8080",
        "name": "The Wintersmith's blog",
        "owner": "Someone",
        "description": "Ramblings of an immor(t)al demigod"
      },
      "plugins": ["./plugins/paginator.coffee"],
      "require": {
        "moment": "moment",
        "_": "underscore",
        "typogr": "typogr"
      },
      "jade": {
        "pretty": true
      },
      "markdown": {
        "smartLists": true,
        "smartypants": true
      },
      "paginator": {
        "perPage": 3
      }
    }
    

E após as minhas alterações, eu o deixei assim:

    {
      "locals": {
        "url": "http://oqueaprendihoje.com.br",
        "name": "O Que Aprendi Hoje",
        "owner": "João Felix",
        "description": "A saga de um aprendiz encantado com o universo do Front-end",
        "keywords" : ["javascript","css","front-end","web","development"],
        "disqus": {
          "id" : "oqueaprendihoje"
        }
      },
      "plugins": ["./plugins/paginator.coffee"],
      "require": {
        "moment": "moment",
        "_": "underscore",
        "typogr": "typogr"
      },
      "jade": {
        "pretty": true
      },
      "markdown": {
        "smartLists": true,
        "smartypants": true
      },
      "paginator": {
        "perPage": 10
      }
    }
    

Basicamente alterei as propriedades do blog, como nome, proprietário, descrição e palavras-chaves, alem de alterar o número de paginas e inserir o objeto &#8220;disqus&#8221; para utilizarmos no controle de comentários; Vale ressaltar que o objeto &#8220;locals&#8221; fica acessivel aos templates também.

Outra alteração necessária foi a criação de um autor, para isso, removi os autores padrões e adicionei o meu na pasta &#8220;contents/authors&#8221;; O identificador de autor no artigo é o nome do arquivo e o conteúdo é um objeto JSON:

    
    {
      "name": "João Felix",
      "email": "jr8116[at]gmail[dot]com",
      "bio": "Aprendiz, desenvolvedor e empreendedor!"
    }
    

## Comentários nos artigos

Todo blog que se preze, precisa aceitar comentários. Para isso, utilizei a solução Disqus, que me permite apenas pela referência do utilizador e da página atual, disponibilizar para os usuários uma forma de comentar os artigos.

Para manter o padrão de organização do projeto, eu criei um template jade chamado &#8216;disqus.jade&#8221; e o coloquei na pasta &#8220;templates&#8221; (Também o dinamizei para utilizar o id do objeto disqus que determinamos); Este arquivo nada mais é do que a transposição do código fornecido pelo Disqus:

    <div id="disqus_thread"></div>
    <script type="text/javascript"> 
      var disqus_shortname = 'oqueaprendihoje'; (function() { var dsq = document.createElement('script'); dsq.type = 'text/javascript'; dsq.async = true; dsq.src = '//' + disqus_shortname + '.disqus.com/embed.js'; (document.getElementsByTagName('head')[0] || document.getElementsByTagName('body')[0]).appendChild(dsq); })(); 
    </script>
    <noscript>Please enable JavaScript to view the <a href="http://disqus.com/?ref_noscript">comments powered by Disqus.</a></noscript> 
    <a href="http://disqus.com" class="dsq-brlink">comments powered by <span class="logo-disqus">Disqus</span></a>

Para o padrão de escrita Jade:

    div(id="disqus_thread")
    script.
      var disqus_shortname = "#{disqus.id}";
      (function() {
        var dsq = document.createElement('script'); dsq.type = 'text/javascript'; dsq.async = true;
        dsq.src = '//' + disqus_shortname + '.disqus.com/embed.js';
        (document.getElementsByTagName('head')[0] || document.getElementsByTagName('body')[0]).appendChild(dsq);
      })();
    noscript
      Habilite o Javascript do seu browser para ver os
      a(href="http://disqus.com/?ref_noscript") comentários mantidos pelo Disqus.
    a.dsq-brlink(href="http://disqus.com")
      comments powered by
      span.logo-disqus
        Disqus
    

Com o template pronto, basta inclui-lo no template &#8220;article.jade&#8221; que também está no diretório &#8220;templates&#8221;:

    include disqus
    

Resultado final do template:

    extends layout
    
    block append vars
      - bodyclass = 'article-detail'
    
    block prepend title
      | #{ page.title + " - "}
    
    block header
      include author
      h1= page.title
      p.author
        | #{ "Escrito por " }
        mixin author(page.metadata.author)
    
    block content
      article.article
        section.content!= typogr(page.html).typogrify()
    
    block prepend footer
      include disqus
      div.nav
        a(href=contents.index.url) « Lista
    

Também fiz algumas alterações por menores, como: Exibir o Twitter e não o E-mail do autor, links para compartilhamento utilizando o Addthis, inserção do Google Analytics e tradução dos links de avançar, ver mais e etc. que estão disponíveis no código fonte do blog.

## Publicando

Pronto! Nossa estrutura de blog está criada! Agora falta apenas gerar os arquivos finais para a publicação, que estarão disponíveis na pasta &#8220;build&#8221;:

    $ wintersmith build
    

## Acabamos!

Neste momento, temos um blog pronto, porem, sem customização e apenas com o layout padrão do Wintersmith.  Espero que tenham gostado.

Todo o código está disponível no Github e no site: https://github.com/jr8116/oqueaprendihoje

 [1]: http://tableless.com.br/jekyll-servindo-sites-estaticos/
 [2]: http://wintersmith.io/ "Wintersmith"
 [3]: http://jekyllrb.com
 [4]: https://iwantmyname.com/blog/2011/02/list-static-website-generators.html
 [5]: http://daringfireball.net/projects/markdown/
 [6]: http://jade-lang.com
 [7]: http://coffeescript.org/
 [8]: https://npmjs.org/