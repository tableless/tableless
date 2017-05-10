---
title: Desenvolvimento de temas para Tumblr
author: Dani Guerrato
type: post
date: 2014-07-21
excerpt: Entenda como blogs e redes sociais podem andar de mãos dadas, veja como criar uma diagramação diferente para cada tipo de conteúdo e desenvolva temas para Tumblr utilizando variáveis dinâmicas e HTML.
url: /desenvolvimento-de-temas-para-tumblr/
dsq_thread_id: 2828991617
categories:
  - CMS
  - Técnicas e Práticas
tags:
  - blog
  - temas para tumblr
  - tumblr

---
Quando pensamos em sistemas de administração de conteúdo logo lembramos do WordPress, do Joomla ou do Drupal. E de fato estes CMS são super completos para lidar com sites, portais e, com algumas adaptações, até mesmo lojas virtuais. Mas se o que você precisa é um blog o Tumblr pode ser uma alternativa bem interessante. Primeiro por que a interface de adição de conteúdo é super simples e dividida por tipos de conteúdo: textos, imagens, vídeos, links, citações, áudio e diálogos. Cada um destes elementos possui uma diagramação diferente, o que pode ser um caminho bem interessante a ser explorado através do design.

<img src="http://tableless.com.br/uploads/2014/07/tumblr-interface.jpg" alt="tumblr-interface" width="750" height="400" class="alignnone size-full wp-image-43394" srcset="uploads/2014/07/tumblr-interface.jpg 750w, uploads/2014/07/tumblr-interface-260x139.jpg 260w, uploads/2014/07/tumblr-interface-400x213.jpg 400w" sizes="(max-width: 750px) 100vw, 750px" />

Além disto o Tumblr também funciona como uma rede social. Todos os blogs fazem parte de uma rede de conteúdo com diversas interações como seguir, gostar (o equivalente ao curtir do Facebook) e reblogar (compartilhar). A Dashboard funciona como um grande feed RSS de todos os blogs que o usuário segue. Assim é quase impossível perder uma postagem nova.

### Sobre

Desde sua criação em fevereiro de 1997 o Tumblr conta com 193 milhões de usuários e mais de 83 bilhões (sim, bilhões) de postagens. Além da interface web é possível atualizar a plataforma através de aplicativos nativos para iOS, Android e Windows Phone. Super prático! A língua padrão é inglês, mas é só entrar em configurações para escolher o nosso português brazuca se você preferir. Alias, nas configurações existem algumas outras opções interessantes como programar posts para serem publicados automaticamente, bloquear usuários trolls ou sinalizar o blog como impróprio para menores de 18 anos se for o caso.

Só lembrando que este artigo é apenas sobre desenvolvimento para Tumblr, então se você não sabe HTML estude um pouquinho e volte mais tarde.

### O Básico

O primeiro passo para iniciar no desenvolvimento para Tumblr é criar uma conta na plataforma. Então visite o site e registre seu usuário. Em seguida você deve escolher um nome, avatar, descrição e cabeçalho do seu blog. Não esquente a cabeça já que tudo isto pode ser trocado depois. É possível ter mais de um blog por usuário. Escolha o blog que você quiser editar na barra lateral, clique em &#8220;Personalizar&#8221;. A partir desta tela já é possível alterar alguns elementos gráficos como tipografia, formato do avatar, cores do tema e inserir sua ID do Disqus, Google Analalytics e, a opção mais importante de todas para este artigo; &#8220;Editar HTML&#8221;.

<img src="http://tableless.com.br/uploads/2014/07/tumblr-editorhtml.jpg" alt="tumblr-editorhtml" width="750" height="400" class="alignnone size-full wp-image-43393" srcset="uploads/2014/07/tumblr-editorhtml.jpg 750w, uploads/2014/07/tumblr-editorhtml-260x139.jpg 260w, uploads/2014/07/tumblr-editorhtml-400x213.jpg 400w" sizes="(max-width: 750px) 100vw, 750px" />

## Variáveis (Variables)

A partir do editor de HTML você pode conferir o código do tema. Reparou que existem diversas palavras escritas entre chaves? São as variáveis! Estas variáveis servem para determinar o conteúdo dinâmico do tema. Sempre que você quiser que o título do Blog seja exibido, por exemplo, é só utilizar a variável {title} em qualquer lugar do seu layout. Mais fácil que falar mal do Internet Explorer.

<pre class="lang-html">&lt;head&gt;
    &lt;title&gt;{Title}&lt;/title&gt;
&lt;/head&gt;
</pre>

Lembre-se apenas que esta informação precisa estar cadastrada no Tumblr. Se o seu blog não tiver um título, nada acontecerá. Existem variáveis para praticamente todos os elementos utilizados em um Blog. E isto ajuda a salvar bastante tempo de desenvolvimento. O conteúdo das variáveis é afetado pelos elementos do seu HTML e CSS. Ou seja, se você utilizar a variável {title} dentro de um H1, por exemplo, os estilos do seu layout vão ser aplicados.

## Blocos (Blocks)

Se as variáveis nos fornecem uma informação dinâmica específica os blocos servem para conjuntos inteiros de conteúdo (como uma postagem) ou para renderizar blocos de HTML (como o bloco de paginação).Blocos também são exibidos entre chaves e devem ser abertos e fechados com uma barra diagonal (como acontece com tags HTML). Para abrir um bloco utilizamos a expressão block:nomedobloco. O bloco description, por exemplo, é utilizado para exibir a descrição de um item.

<pre class="lang-html">{block:Description}
    &lt;p id="description"&gt;{Description}&lt;/p&gt;
{/block:Description}
</pre>

Através das variáveis e blocos é possível configurar itens como aparência global, navegação, tipos de posts (texto, foto, foto panorâmica, álbum de fotos, citação, link, diálogo, audio, video, resposta), data, notas, tags, fonte de conteúdo, submissões, blog em grupo, localização, busca, seguidores, likes e reblogs, integração com o Twitter e temas para iPhone. Ufa! É muita coisa para um artigo só. Consulte a [documentação do Tumblr][1] para uma lista completa de variáveis.

## Hands-on!

Como todo mundo adora uma demo eu criei um layout para um blog fictício para a gente brincar um pouquinho e aprender a desenvolver um tema na prática. É algo bem simples, só para conhecermos as funções finais. Então vamos supor que você tem uma cliente chamada Dani Guerrato (que nome criativo!) e ela enviou o seguinte layout.

<img src="http://tableless.com.br/uploads/2014/07/tumblr-layout.jpg" alt="tumblr-layout" width="750" height="1728" class="alignnone size-full wp-image-43395" srcset="uploads/2014/07/tumblr-layout.jpg 750w, uploads/2014/07/tumblr-layout-60x139.jpg 60w, uploads/2014/07/tumblr-layout-400x921.jpg 400w" sizes="(max-width: 750px) 100vw, 750px" />

É possível dividir a estrutura deste layout em algumas partes. Um cabeçalho contendo título do blog, descrição, nome do usuário, descrição do usuário e avatar. E cinco tipos de post: texto, citação, imagem, link e diálogo. Existem outros formatos, mas a estrutura é muito parecida com a que vamos desenvolver por aqui.

Antes de começar se atente para dois detalhes:
  
1. Como vamos ter que utilizar o editor do próprio Tumblr para ver o conteúdo dinâmico é mais fácil deixar o CSS declarado no próprio HTML por enquanto.
  
2. As imagens do tema e arquivos estáticos externos devem estar hospedados em um servidor. Você pode subir no seu próprio ou utilizar o [uploader do próprio Tumblr][2] (como um limite de 15 MB por dia).

Certo. Agora é só desenvolver o HTML normalmente (se preferir, baixe os arquivos de HTML &#8220;limpos&#8221; no final do post). O próximo passo é entrar no Tumblr e substituir o HTML do tema padrão pelo nosso.

### Metatags e Ícones

Lembra da variável {title}? Vamos inseri-la dentro do head do nosso template. E, para complementar, vamos utilizar também as variáveis de meta description e favicon.

<pre class="lang-html">&lt;head&gt;
    &lt;title&gt;{Title}&lt;/title&gt;
    &lt;meta name="description" content="{MetaDescription}"&gt;
    &lt;link rel="shortcut icon" href="{Favicon}"&gt;
&lt;/head&gt;
</pre>

Tranquilo, certo? Os nomes das variáveis são bem auto-descritivos.

### Header

Agora nós vamos começar o layout propriamente dito. No header do site insira novamente a variável title, desta vez dentro da tag h1.

<pre class="lang-html">&lt;header class="header"&gt;
    &lt;h1&gt;{Title}&lt;/h1&gt;
&lt;/header&gt;
</pre>

Um padrão de navegação comum na internet é que o título de uma página aponte para a Home. Para isto vamos utilizar a variável {BlogURL} em conjunto com o title.

<pre class="lang-html">&lt;header class="header"&gt;
    &lt;h1&gt;&lt;a href="{BlogURL}"&gt;{Title}&lt;/a&gt;&lt;/h1&gt;
&lt;/header&gt;
</pre>

Abaixo do h1 temos um elemento h2. Lembra que existia um bloco específico para descrições? Vamos utiliza-lo aqui.

<pre class="lang-html">{block:Description}
    &lt;h2&gt;&lt;{Description}&lt;/h2&gt;
{/block:Description}
</pre>

Ainda no cabeçalho do blog temos um espaço destinado ao usuário. Para mostrar o avatar no seu tema você deve usar a variável PortraitURL.

<pre class="lang-html">&lt;figure class="avatar"&gt;
    &lt;img src="{PortraitURL-128}"/&gt;
&lt;/figure&gt;
</pre>

O valor &#8220;128&#8221; serve para definir o tamanho do avatar que é sempre redimensionado automaticamente de acordo com a imagem do usuário. No nosso caso utilizamos 128&#215;128 pixels. Se você preferir um avatar menor estas são as opções: 16, 24, 30, 40, 48, 64 e 96.

O próximo passo é determinarmos o nome de usuário através da variável {name}

<pre class="lang-html">&lt;h3&gt;{Name}&lt;/h3&gt;
</pre>

#### Campos de texto personalizados

O último elemento do cabeçalho é um pouco mais complicadinho. Trata-se de uma descrição do usuário. Como este não é um elemento padrão em temas para Tumblr (por sabe-se lá qual razão) vamos criar um campo personalizado de edição do tema para que o nosso usuário possa cadastrar esta informação. Primeiro vamos &#8220;avisar&#8221; o Tumblr que usaremos um campo de texto com o nome Tagline. Para isto acrescente esta metatag ao seu head.

<pre class="lang-html">&lt;meta name="text:Tagline" content=""/&gt;
</pre>

Este nome é completamente arbitrário, ou seja, você pode criar o campo com o nome que desejar. Em seguida vamos criar um bloco para exibir nossa tagline dentro do header. A lógica é a seguinte se o usuário cadastrar um texto no campo (ou seja IfTagline) a descrição irá aparecer. Do contrário nada acontece.

<pre class="lang-html">{block:IfTagline}
     &lt;p&gt;{text:Tagline}&lt;/p&gt;
{/block:IfTagline}
</pre>

Fácil, né? Estas configurações avançadas permitem ao usuário customizar o layout do tema utilizando a interface gráfica do Tumblr. 

<img src="http://tableless.com.br/uploads/2014/07/tumblr-campopersonalizado.jpg" alt="tumblr-campopersonalizado" width="750" height="400" class="alignnone size-full wp-image-43392" srcset="uploads/2014/07/tumblr-campopersonalizado.jpg 750w, uploads/2014/07/tumblr-campopersonalizado-260x139.jpg 260w, uploads/2014/07/tumblr-campopersonalizado-400x213.jpg 400w" sizes="(max-width: 750px) 100vw, 750px" />

E não funciona apenas para campos de texto não. Podemos utilizar booleanos como este para todo tipo de conteúdo personalizado como opções de cores, tipografia, widgets e até mesmo variações de CSS. E isto é essencial para quem deseja desenvolver temas para venda ou que tem como público-alvo usuários sem familiaridade com HTML. Você pode criar, por exemplo, um modo de visualização das postagens em lista e outro em grid e o usuário poderá selecionar qual deseja utilizar em seu blog.

A esta altura o seu cabeçalho deverá estar assim:

<pre class="lang-html">&lt;header class="header"&gt;

    &lt;div class="wrap"&gt;
        &lt;h1&gt;&lt;a href="{BlogURL}"&gt;{Title}&lt;/a&gt;&lt;/h1&gt;
        {block:Description}
            &lt;h2&gt;{Description}&lt;/h2&gt;
        {/block:Description}
    &lt;/div&gt;

    &lt;div class="usuario"&gt;
        &lt;div class="wrap"&gt;
            &lt;figure class="avatar"&gt;
                &lt;img src="{PortraitURL-128}"&gt;
          &lt;/figure&gt;  
          &lt;h3&gt;{name}&lt;/h3&gt;
          {block:IfTagline}
              &lt;p&gt;{text:Tagline}&lt;/p&gt;
          {/block:IfTagline}
        &lt;/div&gt;
    &lt;/div&gt;

&lt;/header&gt;
</pre>

## Posts

Com o header pronto é hora de definir a área do layout destinada aos posts. Nós fazemos isto através do bloco &#8211; é isto mesmo você já adivinhou &#8211; posts! Portanto abra o bloco dentro da section principal e feche logo após o último post.

<pre class="lang-html">{block:Posts}
    ...
{/block:Posts}
</pre>

### Post &#8211; Texto

O bloco posts é o &#8220;pai&#8221; de todos as postagens. Agora devemos definir uma estrutura diferente para cada tipo de post que queremos utilizar. Vamos começar com o mais simples: texto. Cole o seguinte bloco antes e depois do article com a classe &#8220;texto&#8221;.

<pre class="lang-html">{block:Text}
    &lt;article class="post texto"&gt;
       …
    &lt;/article&gt;
{/block:Text}
</pre>

Todo texto precisa de um título, certo? Podemos definir isto utilizando o bloco Title. Para melhorar a usabilidade vamos fazer de cada título um link permanente através da variável permalink.

<pre class="lang-html">{block:title}
    &lt;h2&gt;&lt;a href="{Permalink}"&gt;{Title}&lt;/a&gt;&lt;/h2&gt;
{/block:title}
</pre>

Para puxar o conteúdo do post utilize a variável {Body}. O loop completo do nosso post de texto ficará assim:

<pre class="lang-html">{block:Posts}
    {block:Text}
        &lt;article class="post texto"&gt;
            {block:title}
                &lt;h2&gt;&lt;a href="{Permalink}"&gt;{Title}&lt;/a&gt;&lt;/h2&gt;
            {/block:title}
            {body}
        &lt;/article&gt;
    {/block:Text}
{/block:Posts}
</pre>

### Post &#8211; Citação

Este tipo de post é composto pela variável da citação {Quote} e o bloco da fonte referenciada {Source}. O loop ficará assim:

<pre class="lang-html">{block:Quote}
    &lt;article class="post citacao"&gt;
        &lt;blockquote&gt;
             &lt;p&gt;{Quote}&lt;/p&gt;
             &lt;p&gt;— {block:source}{Source}{/block:source};/p&gt;
        &lt;/blockquote&gt;
    &lt;/article&gt;
{/block:Quote}
</pre>

### Post &#8211; Links

Links também são um tipo de post. A estrutura vai ficar assim: a variável {URL} define o endereço do link, {Name} o nome a ser exibido e {Target} se ele será aberto na mesma janela ou em outra (de acordo com as configurações do usuário).

<pre class="lang-html">{block:Link}
    &lt;a href="{URL}" target=""&gt;{Name}&lt;/a&gt;
{/block:Link}
</pre>

Links também podem ter descrições.

<pre class="lang-html">{block:Link}
    &lt;a href="{URL}" target=""&gt;{Name}&lt;/a&gt;
    {block:description}{Description}{/block:description}
{/block:Link}
</pre>

### Post &#8211; Fotos

A estrutura inicial é bem parecida com a que já conhecemos.

<pre class="lang-html">{block:Photo}
    ...
{/block:Photo}
</pre>

Podemos inserir imagens através da variável {PhotoURL}. É necessário novamente seguir alguns tamanhos padrões. Como quero utilizar imagens de alta resolução vou ficar com a variável {PhotoURL-1280}. Este valor numérico é referente a largura pois a altura é sempre proporcional ao tamanho original da foto. O alt da imagem é definido pela variável {PhotoAlt}.

<pre class="lang-html">&lt;figure class="imagem"&gt;&lt;img src="{PhotoURL-1280}" alt="{PhotoAlt}"&gt;&lt;/figure&gt;
</pre>

Não se esqueça de colocar uma legenda para a sua foto.

<pre class="lang-html">{block:Caption}{Caption}{/block:Caption}
</pre>

O loop completo para a foto:

<pre class="lang-html">{block:Photo}
    &lt;article class="post foto"&gt;
        &lt;figure class="imagem"&gt;&lt;img src="{PhotoURL-1280}" alt="{PhotoAlt}"&gt;&lt;/figure&gt;
        {block:Caption}{Caption}{/block:Caption}
    &lt;/article&gt;
{/block:Photo}
</pre>

### Post &#8211; Chat

A esta altura você já deve ter pegado o jeito. O bloco de chat com seu respectivo título ficará assim:

<pre class="lang-html">{block:Chat}
    &lt;article class="post chat"&gt;
        {block:Title}
            &lt;h2&gt;&lt;a href="{Permalink}"&gt;{Title}&lt;/a&gt;&lt;/h2&gt;
        {/block:Title}
    &lt;/article&gt;
{/block:Chat}
</pre>

Agora precisaremos determinar cada linha de fala. Faremos isto através de uma lista dentro do bloco {Lines}

<pre class="lang-html">{block:Chat}
    &lt;article class="post chat"&gt;
        &lt;ul&gt;
            {block:Lines}
                &lt;li&gt;{Line}&lt;/li&gt;
            {/block:Lines}
        &lt;/ul&gt;
    &lt;/article&gt;
{/block:Chat}
</pre>

Dentro desta lista vamos determinar o nome de cada personagem através do bloco {Label}. Vamos acrescentar também a classe {Alt} user_{UserNumber} para o caso de o nosso char ser entre dois usuários. O código ficará assim:

<pre class="lang-html">&lt;article class="post chat"&gt;
    {block:Title}
        &lt;h2&gt;&lt;a href="{Permalink}"&gt;{Title}&lt;/a&gt;&lt;/h2&gt;
    {/block:Title}
    &lt;ul&gt;
        {block:Lines}
            &lt;li class="{Alt} user_{UserNumber}"&gt;
                {block:Label}
                    &lt;span class="voz"&gt;{Label}&lt;/span&gt;
                {/block:Label}{Line}
            &lt;/li&gt;
        {/block:Lines}
    &lt;/ul&gt;    
&lt;/article&gt;
</pre>

### Post &#8211; Outros

Existem mais tipos de post: foto panorâmica, álbum de fotos, respostas, audio e video. Mas a esta altura do campeonato você já entendeu a estrutura, certo? Então visite a documentação do Tumblr e considera sua lição de casa tentar desenvolver por conta própria estes dois últimos. Além dos posts você pode criar uma infinidade de páginas especiais como sobre ou um formulário de contato.

### Rodapé

Mas o nosso loop do post ainda não está pronto. Falta fazer o rodapé! No footer-post temos uma lista para exibir informações diversas. Vamos a elas:

#### Tags

O primeiro item da nossa lista são as tags. Para isto vamos utilizar o bloco HasTags. Se o post tiver tags, elas serão exibidas. Do contrário nada acontece. Dentro do HasTags temos o bloco da Tag propriamente dita.

<pre class="lang-html">{block:HasTags}
    {block:Tags}
    ...
    {/block:Tags}
{/block:HasTags}
</pre>

Para que possamos trocar o estilo e adicionar a url da tag (o símbolo # está ali só para fazer charminho mesmo) vamos acrescentar uma linha com a seguinte estrutura. 

<pre class="lang-html">&lt;ul&gt;
    &lt;li&gt;&lt;a href="{TagURL}"&gt;#{Tag}&lt;/a&gt;&lt;/li&gt;
&lt;/ul&gt;
</pre>

O código completo das tags final ficará assim:

<pre class="lang-html">&lt;footer class="footer-post"&gt;
    &lt;ul&gt;
        {block:HasTags}
            {block:Tags}
                &lt;li&gt;&lt;a href="{TagURL}"&gt;#{Tag}&lt;/a&gt;&lt;/li&gt;
            {/block:Tags}
        {/block:HasTags}
    &lt;/ul&gt;
&lt;/footer&gt;
</pre>

#### Data

O próximo item da nossa lista é marcação de data. Vamos utilizar um bloco de Data {block:Date}, junto como um link permanente {Permalink} e o conteúdo da data propriamente dito {TimeAgo}

<pre class="lang-html">&lt;ul&gt;
    &lt;li&gt;
        {block:Date}
            &lt;a href="{Permalink}"&gt;{TimeAgo}&lt;/a&gt;
        {block:Date}
    &lt;/li&gt;
&lt;/ul&gt;
</pre>

Agora nossos posts mostram a quanto tempo atrás foram escritos. Este é o formato de data padrão, mas é possível alterar através de variáveis. {DayOfMonth}{Month}{Year} mostraria uma data com a estrutura dia-mês- ano (7 de julho de 2004, por exemplo).

#### Gostar

Gostar (like) é o ícone de coraçãozinho no final do post. Tem o mesmo efeito do curtir do Facebook, ou seja, sevre para as pessoas demonstrarem o quanto elas gostaram do seu conteúdo. Para inserir o botão basta utilizar a variável {LikeButton}

<pre class="lang-html">&lt;li class="gostar"&gt;{LikeButton}&lt;/li&gt;
</pre>

#### Reblogar

O reblogar (reblog) funciona como o RT do Twitter. Serve para as pessoas repostarem o conteúdo acrescentando comentários próprios. É um bom aliado na hora de viralizar o conteúdo. A variável correspondente é {ReblogButton}

<pre class="lang-html">&lt;li class="reblogar"&gt;{ReblogButton}&lt;/li&gt;
</pre>

#### Notas

As notas são uma lista dos usuários que gostaram e reblogaram sua postagem. Vamos exibir no rodapé do post o número de notas da seguinte maneira:

<pre class="lang-html">&lt;li&gt;
   &lt;span&gt;
        {block:NoteCount}
            {NoteCountWithLabel}
        {/block:NoteCount} 
   &lt;/span&gt;
&lt;/li&gt;
</pre>

Para garantir que todas as notas serão exibidas, usaremos o bloco e a variável {PostNotes}. Podemos ainda inserir um avatar de cada usuário utilizando a variável {PostNotes-64}. 

<pre class="lang-html">{block:PostNotes}
    {PostNotes-64}{PostNotes}
{/block:PostNotes}
</pre>

No final o rodapé do nosso post ficou assim:

<pre class="lang-html">&lt;footer class="footer-post"&gt;
    &lt;ul&gt;
        {block:HasTags}
            {block:Tags}
                &lt;li&gt;&lt;a href="{TagURL}"&gt;#{Tag}&lt;/a&gt;&lt;/li&gt;
            {/block:Tags}
        {/block:HasTags}
       &lt;li&gt;
           &lt;span class="data"&gt;
               {block:Date}
                   &lt;a href="{Permalink}"&gt;{TimeAgo}&lt;/a&gt;
               {block:Date}       
          &lt;/span&gt;
      &lt;/li&gt;
      &lt;li&gt;
         &lt;span&gt;
              {block:NoteCount}
                  {NoteCountWithLabel}
              {/block:NoteCount} 
        &lt;/span&gt;
        &lt;/li&gt;
        &lt;li class="gostar"&gt;{LikeButton}&lt;/li&gt;
        &lt;li class="reblogar"&gt;{ReblogButton}&lt;/li&gt;
    &lt;/ul&gt;
&lt;/footer&gt;
</pre>

### Paginação

Agora que os posts estão prontos precisamos navegar de uma página a outra. Após o bloco de Posts insira a paginação da seguinte maneira.

<pre class="lang-html">{block:Pagination}
    {block:PreviousPage}
        &lt;a href="{PreviousPage}"&gt;P&#225;gina Anterior&lt;/a&gt;
    {/block:PreviousPage}
    {block:NextPage}
        &lt;a href="{NextPage}"&gt;Pr&#243;xima P&#225;gina&lt;/a&gt;
    {/block:NextPage}
{/block:Pagination}
</pre>

## Fim?

O nosso tema, embora esteja funcional, pode receber muitas melhorias. Podemos acrescentar um sistema de buscas, criar diversos campos personalizados, páginas extras, navegação, etc. Mas espero que este post tenha dado uma base sólida para que você possa conhecer a plataforma e mergulhar no mundo de desenvolvimento para Tumblr. Você pode [baixar os arquivos aqui][3] ou conferir esta [demo ao vivo no Tumblr][4]. Até a próxima!

 [1]: https://www.tumblr.com/docs/en/custom_themes?language=pt_BR "Tumblr Docs"
 [2]: https://www.tumblr.com/themes/upload_static_file "Tumblr - Upload Static Files"
 [3]: https://github.com/daniguerrato/Tumblr-demo "Tumblr-demo"
 [4]: http://daniguerrato.tumblr.com/ "Demo do artigo Desenvolvimento de temas para Tumblr"