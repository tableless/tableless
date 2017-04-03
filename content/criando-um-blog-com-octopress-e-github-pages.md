---
title: Criando um blog com Octopress e Github Pages
author: Diogo Beato
type: post
date: 2013-12-19
excerpt: Crie um blog em Octopress, framework baseado em Jekyll.
url: /criando-um-blog-com-octopress-e-github-pages/
categories:
  - Código
  - Técnicas e Práticas
tags:
  - jekyll
  - octopress
  - ruby

---
Já faz pouco mais de uma semana que venho estudando o Octopress para o desenvolvimento do meu <a title="divecch.com" href="http://divecch.com" target="_blank">blog</a>. Hoje vou mostrar como iniciar seu blog utilizando essa ferramenta e falar um pouco sobre como está sendo a experiência de criar um blog totalmente estático, sem a necessidade de um server-side.

O <a title="Octopress Official Page" href="http://octopress.org/" target="_blank">Octopress</a> é um framework criado por <a title="Brandon Mathis Website" href="http://brandonmathis.com/" target="_blank">Brandon Mathis</a> com o <a title="Jekyll Framework" href="http://jekyllrb.com/" target="_blank">Jekyll</a>, que é uma ferramenta Ruby para gerar sites estáticos a partir de templates HTML, CSS, Javascript, arquivos de configurações e markdowns. Também possui algumas tarefas automatizadas com o rake, para criar, novos posts, gerar o conteúdo estático, fazer deploy, etc. Eu nunca havia trabalhado com esse tipo de ferramenta e achei bem interessante essa ideia, porém o Octopress é totalmente voltado pra blogs e nesse pouco tempo de uso já senti algumas limitações, estou começando a cogitar a ideia de criar uma ferramenta dessas pra abranger outros segmentos além de blogs, mas isso é uma história para outro post. Bom, chega de blá, blá, blá e vamos pra prática!

### Como instalar

Antes de começar, certifiquem-se que vocês possuem instalado o **<a title="Ruby" href="https://www.ruby-lang.org/pt/" target="_blank">ruby</a> – versão > 1.9.3** e <a title="Git" href="http://git-scm.com/" target="_blank"><strong>git</strong></a>.

Agora basta fazer clone do repositório do Octopress e adicionar o nome do blog no final do comando. No nosso exemplo vamos utilizar “blog-zueiro”:

<pre><code class="sh">git clone git://github.com/imathis/octopress.git blog-zueiro
cd blog-zueiro</code></pre>

Dentro da pasta “blog-zueiro”, execute os seguintes comandos:

<pre><code class="sh">gem install bundler
rbenv rehash   # caso esteja utilizando o rbenv
bundle install # baixa todas as dependências do projeto
rake install   # instala o tema default do octopress
</code></pre>

Pronto, temos toda a estrutura do nosso “blog-zueiro” pronta.

### Rodando no localhost

Para visualizar nosso blog localmente, basta executar:

<pre><code class="sh">rake generate   # gera todos os arquivos estáticos do nosso blog.
rake preview    # inicia um servidor local na porta 4000
</code></pre>

aeee, agora podemos visualizar nosso “blog-zueiro” acessando <http://localhost:4000>.

### Configurações básicas:

Uma das grandes vantagens que notei no Octopress, é a parte de customizar seu blog através do arquivo de configurações, que fica em “**/_config.yml**”.

<pre><code class="yaml">
url:            # url do seu blog: joseh.github.io
title:          # Titulo do blog: Zueiro na Net
subtitle:       # Subtítulo do blog (Slogan)
author:         # Nome do autor do blog.
simple_search:  # Engine da barra de pesquisa no site, default é o google.
description:    # Descrição do blog
date_format:    # Formato de data, no nosso caso “%d/%m/%Y”
subscribe_rss:  # Url para os feeds do seu blog, por padrão é o arquivo /atom.xml
subscribe_email:# Url para inscrever-se por e-mail (serviço obrigatório)
email:          # E-mail para o feed RSS.
root:           # rootpath das nossas urls (default: /)
permalink:      # formato da url para os posts do nosso blog
source:         # diretório dos source do projeto
destination:    # diretório dos arquivos finais
plugins:        # diretório dos plugins que você for utilizar no projeto
code_dir:       # diretório para os code snippets 
category_dir:   # diretório das paginas de categoria do blog
pygments:       # opção para ativar o syntax highlighting do python pygments
paginate:       # numero de posts por pagina na pagina de blog index
pagination_dir: # diretório base para a paginação
recent_posts:   # quantidade de posts recentes a serem exibidos no sidebar do blog
default_asides: # assides que vão ser apresentados no sidebar do blog
blog_index_asides: # assides serão exibidos na página de blog index
post_asides:    # assides que serão exibidos na página de algum post
page_asides:    # assides que serão exibidos em uma página comum
</code></pre>

**dica:** os assides são componentes que ficam exibindo na lateral do blog, como o “Recent Posts” que ficam no diretório **source/_includes/assides**, lá você pode modificar , como por exemplo trocar os títulos pra português, ou alterar a estrutura do html e inserir novos códigos ruby para customizar seu asside.
  
Caso você queira criar novos assides, basta criar um novo arquivo em **source/_includes/custom/assides/** e adicionar ele no default_assides do arquivo **_config.yml**.

### Primeiro post

Legal, temos nosso blog configurado e rodando localmente mas ainda não tem nenhum conteúdo. O Octopress fornece uma rake task para automatizar a criação de postagens. Então vamos lá, vamos criar nossa primeira postagem com o título “começando a zueira na net”:

<pre><code class="sh">rake new_post[“começando a zueira na net”]</code></pre>

Com isso, foi gerado um arquivo .makdown dentro da pasta “blog-zueiro/source/_posts” com o seguinte aspecto:

<pre><code class="sh">layout: post
title: "começando a zueira na net"
date: 2013-11-29 11:14:44 -0200
comments: true
categories:
</code></pre>

**layout:** é referente ao layout que ele vai usar pra página. Esses layouts ficam dentro da pasta “blog-zueiro/source/_layouts”, caso você queira, pode criar seu próprio layout dentro dessa tela e alterar o markdown para utilizar ele.

**titulo:** é o titulo do post

**data:** é a data de criação

**comments:** é se o seu post vai ter comentários ou não (true | false)

**categories:** são as categorias relacionadas ao seu post, por exemplo:

<pre><code class="sh">categories: [zueiro na net, blog, octopress, ruby]</code></pre>

**author:** é o autor do post

Agora basta escrever nosso post:

<pre><code class="sh">---
layout: post
title: "começando a zueira na net"
date: 2013-11-29 11:14:44 -0200
comments: true
categories:[zueiro na net, blog, octopress, ruby]
author: Zeh Zueiro
---
Cheguei na net e to afim de zueira, meu primeiro post é sobre...
</code></pre>

**dica:** existem vários editores de arquivos markdown que facilita na hora de inserir links, imagens, etc. Teve dois que eu utilizei e gostei bastante que é o <https://stackedit.io> e o [http://mouapp.com][1]

### Deploy para o GithubPages

Ótimo, já temos a estrutura do nosso blog pronta, já criamos nosso primeiro post, agora quero mostrar pro meus amigos, afinal, de que adianta eu ter um blog que só eu vejo???

Pra colocar nosso blog no ar, vamos utilizar o Github Pages que é suportado nativamente pelo Octopress e a hospedagem é free.

Primeiro acesse sua conta no github.com e crie um repositório com o seguinte padrão: **username.github.io**.

Então se seu username for **joseh**, o repositório deverá se chamar: **joseh.github.io**.

Volte novamente pro terminal e execute:

<pre><code class="sh">rake setup_github_pages</code></pre>

Nesse momento ele vai pedir pra você inserir o repositório do github, o que a gente criou agora pouco: <http://github.com/joseh/joseh.github.io.git>

e em seguida:

<pre><code class="sh">
rake generate # para gerar o conteúdo estático do blog
rake deploy   # para subir fazer subir seu blog pro repositório que configuramos.
</code></pre>

agora você pode visualizar seu blog no endereço **joseh.github.io**, lembrando que algumas vezes podem levar até 10 minutos pro github disponibilizar seu site online.

**possíveis problemas:** caso sua pagina não esteja online depois de 10 min, verifique se o seu repositório esta no padrão correto: username.github.io, inclusive respeitando maiúsculas e minúsculas.
  
No meu caso, meu usuário é diRex, então meu repositório teve que ficar diRex.github.io. Se estiver errado, renomeie seu repositório pelo github e execute novamente o rake setup\_github\_pages pra configurar o repositório com o novo nome.

**dica:** o Octopress já vem com dois branches configurados, um master, onde vai ficar os arquivos de produção do blog e um source, onde ficam, obviamente, o source do seu projeto. Então, quando for atualizar o source do seu projeto no github…:

<pre><code class="sh">git add .
git commit -m “mensagem”
git push origin source
</code></pre>

e pra baixar as atualizações do source em outra máquina:

<pre><code class="sh">git pull origin source</code></pre>

### Socializando nosso blog

Nesse mesmo arquivo **_config.yml** temos algumas configurações que permitem adicionar algumas interações com as redes sociais:

**Github**

<pre><code class="yaml">github_user:                    # usuário do github
github_repo_count: 0            # quantidade de repositórios que vão ser exibidos
github_show_profile_link: true  # exibir link para o perfil
github_skip_forks: true         # não exibir forks
</code></pre>

**Twitter**

<pre><code class="yaml">twitter_user:                 # usuário do twitter
twitter_tweet_button: true    # exibir botão de tweet
</code></pre>

**Google Plus**

<pre><code class="yaml">google_plus_one: false        # exibir botão +1
google_plus_one_size: medium  # tamanho do botão
googleplus_user:              # usuário do gplus
googleplus_hidden: false      # esconder botão +1 dos assets
</code></pre>

**Pinboard**

<pre><code class="yaml">pinboard_user:       # usuário do pinboard
pinboard_count: 3    # quantidade de bookmarks exibidos
</code></pre>

**Delicious**

<pre><code class="yaml">delicious_user:      # usuário do delicious
delicious_count: 3   # quantidade de bookmarks exibidos
</code></pre>

**Disqus Comments**

<pre><code class="yaml">disqus_short_name:                # short name do seu disqus app
disqus_show_comment_count: false  # exibir quantidade de comentários
</code></pre>

Disqus é uma plataforma de comentários, caso você não preencher o short name do disqus, seu blog não vai ter comentários, a menos que utilize os comentários do facebook, como vou ensinar a seguir.

**Facebook**

<pre><code class="yaml">facebook_like: false     # exibir botões de curtir e compartilhar
</code></pre>

Agora é só escolher quais opções você quer adicionar no seu blog para ter maior interação com seus visitantes XD!

### Comentários com o Facebook

Uma coisa que não vem por padrão no Octopress e que eu queria colocar no meu blog, são os comentários com o Facebook. Acho que facilita mais do que usar o Disqus, pois grande maioria do pessoal já tem conta no Facebook.

Como acho que outras pessoas também irão sentir essa necessidade, vou mostrar como fazer pra colocar essa funcionalidade no seu blog.

Primeiro crie uma app para o facebook: <https://developers.facebook.com/apps>

Agora vamos até o doc de comentários do facebook: <https://developers.facebook.com/docs/plugins/comments/> e preencha os campos de acordo com a imagem a seguir.
  
![image][2]

Clique em **Get Code** e ele vai gerar pra você dois trechos de códigos, um javascript e um html. O javascript você deve substituir pelo código que tem dentro do arquivo **source/\_includes/facebook\_like.html**.
  
O código html você coloca onde for exibir os comentários, no meu caso coloquei em **source/_includes/post/sharing.html** para exibir em baixo dos botões de curtir e compartilhar.

### Customizar layout

O Octopress utiliza o pré-processador de css SaSS nos seus templates, esse está sendo meu primeiro contato com pré processadores e realmente traz muitas facilidades, quem quiser ficar por dentro de como o SaSS funciona, acesse: <http://sass-lang.com/.> Toda customização do layout pode ser feita através dos arquivos .scss que ficam na pasta /sass.

### Criando novas páginas

Caso você queira adicionar uma página mais paginas no seu blog, como uma página de contato:

<pre>rake new_page[“contato”]&lt;/code></pre>

e o arquivo da sua nova página será criado em **source/contato/index.markdown**

### Trafego de acesso com google analytics

Ter uma analise do trafego de acesso do seu site é crucial para tomar decisões na hora de melhorar o seu conteúdo online. Para quem ainda não usou o google analytics, essa é uma boa hora pra ver como funciona, eu mesmo ainda não tinha utilizado e estou me divertindo vendo os relatórios de acesso, locais de onde o blog recebe visitas e tudo mais.

Pra adicionar o analytics aos seu blog, basta criar uma conta em www.google.com/analytics/‎ e obter um ID de acompanhamento. Depois disso, só adicionar esse ID no arquivo _config.yml:

    google_analytics_tracking_id: XX-99999999-9
    

### Custom domain

Para finalizar, caso você queira usar um custom domain, como por exemplo: exemplo.com,
  
tudo que precisa fazer é criar um arquivo chamado CNAME dentro da pasta **source/**

Agora vá até o seu provedor de dominio, e configure o subdominio `www.exemplo.com`
  
para apontar pro seu endereço do github: **username.github.io**.

Caso você também queira usar o naked name `exemplo.com`, modifique o seu registro de dns do tipo A para apontar pro ip `204.232.175.78`.

E isso é tudo pessoal, kkkk! Espero que tenham gostado do post, curtam, comentem, compartilhem. Críticas quanto ao texto também são bem vindas. Se conhecerem outras ferramentas que possuem o mesmo propósito de gerar conteúdo estático, comentem também!

Gostaria também de agradecer o grande Diego Eis pelo espaço e pela iniciativa do Tableless. Parabéns!

vlw !!!

 [1]: http://mouapp.com/
 [2]: https://lh5.googleusercontent.com/7oygYA9JHZZUrF9NHv0OgZSFLSKSJ-MujapA0gUnm1M=w733-h453-no