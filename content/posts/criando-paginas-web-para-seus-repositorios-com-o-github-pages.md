---
title: Criando páginas web para seus repositórios com o GitHub Pages
author: William Martins
type: post
date: 2013-07-29
excerpt: Entenda como funciona o Github Pages.
url: /criando-paginas-web-para-seus-repositorios-com-o-github-pages/
dsq_thread_id: 1544020576
categories:
  - O Básico
  - Técnicas e Práticas
tags:
  - github
  - github pages
  - iniciantes
  - iniciantes git
  - iniciantes github
  - páginas no github

---
O github é um dos principais meios de compartilhamento de projetos disponíveis na internet, lá, encontram-se desde projetos simples até projetos extremamente complexos, como o kernel do linux (<https://github.com/torvalds/linux>).

Visando expandir a forma de divulgação de projetos, o github possui um serviço chamado ‘github pages’, que serve principalmente para prover páginas na internet sobre os repositórios. Essas páginas podem servir para divulgar exemplos, demos, documentações e qualquer outro tipo de informação sobre o seu projeto. E o melhor, esse serviço é de graça, basta ter uma conta no github! 😀

[<img class="size-full wp-image-38035 aligncenter" alt="its-free" src="http://tableless.com.br/uploads/2013/07/its-free.png" width="520" height="300" srcset="uploads/2013/07/its-free.png 520w, uploads/2013/07/its-free-291x168.png 291w" sizes="(max-width: 520px) 100vw, 520px" />][1]

## Conhecimentos iniciais

Para conseguirmos criar páginas com o github não é necessário que se tenha um conhecimento avançado sobre a ferramenta, visto que veremos que ela disponibiliza um gerador automático de páginas que gera o conteúdo a partir de uma sintaxe bem simples (github flavored markdown). Porém, se você quiser fazer algumas coisas um pouco mais elaboradas com as suas páginas, é necessário conhecer alguns dos principais conceitos envolvidos com o github, como push, commit, fetch e pull.

Portanto, se quiser descobrir um pouco mais sobre o github, recomendo que seja feita a leitura dos seguintes artigos disponíveis aqui no tableless:

Iniciando no GIT &#8211; Parte 1: <a href="http://tableless.com.br/iniciando-no-git-parte-1/" target="_blank">http://tableless.com.br/iniciando-no-git-parte-1/</a>
  
Iniciando no GIT &#8211; Parte 2: <a href="http://tableless.com.br/iniciando-no-git-parte-2/" target="_blank">http://tableless.com.br/iniciando-no-git-parte-2/</a>

## Criando páginas automaticamente

Uma das opções que o github nos dá é a criação automática de páginas. Com ela, podemos criar rapidamente uma página com conteúdo e inclusive escolher um dos templates disponibilizados pelo github para estilizarmos nossa página.

Para criar uma página utilizando o github pages clique na opção ‘settings’ do seu repositório:

[<img class="size-full wp-image-38034 aligncenter" alt="github-settings-option" src="http://tableless.com.br/uploads/2013/07/github-settings-option.png" width="113" height="44" />][2]

O github irá abrir as opções de configurações do repositório, lá, poderá ser encontrado um botão chamado ‘Automatic page generator’, dentro da seção &#8216;GitHub Pages&#8217;:

[<img class="size-medium wp-image-38031 aligncenter" alt="github-pages-box" src="http://tableless.com.br/uploads/2013/07/github-pages-box-588x148.png" width="588" height="148" srcset="uploads/2013/07/github-pages-box-588x148.png 588w, uploads/2013/07/github-pages-box-329x83.png 329w, uploads/2013/07/github-pages-box-660x166.png 660w, uploads/2013/07/github-pages-box.png 681w" sizes="(max-width: 588px) 100vw, 588px" />][3]

Ao clicar nesse botão, você será redirecionado para um formulário contendo alguns campos e um editor de conteúdo, lá, você deverá informar o nome do projeto (que servirá como título na página criada), um subtítulo e o conteúdo que queremos que seja apresentado (em formato de markdown específico do github, referência disponível em <a href="http://github.github.com/github-flavored-markdown/" target="_blank">http://github.github.com/github-flavored-markdown/</a>):

[<img class="size-medium wp-image-38032 aligncenter" alt="github-pages-form" src="http://tableless.com.br/uploads/2013/07/github-pages-form-588x305.png" width="588" height="305" srcset="uploads/2013/07/github-pages-form-588x305.png 588w, uploads/2013/07/github-pages-form-322x168.png 322w, uploads/2013/07/github-pages-form-596x310.png 596w, uploads/2013/07/github-pages-form.png 944w" sizes="(max-width: 588px) 100vw, 588px" />][4]

Após informar esses dados, poderemos escolher o layout que queremos. Assim, ao clicarmos no botão ‘Continue to Layouts’ somos redirecionados para um local onde são exibidos alguns templates pré-prontos que github nos disponibiliza. Basta clicar em algum deles para termos uma live-preview de como a nossa página irá ficar:

[<img class="size-medium wp-image-38033 aligncenter" alt="github-pages-template" src="http://tableless.com.br/uploads/2013/07/github-pages-template-474x310.png" width="474" height="310" srcset="uploads/2013/07/github-pages-template-474x310.png 474w, uploads/2013/07/github-pages-template-256x168.png 256w, uploads/2013/07/github-pages-template.png 930w" sizes="(max-width: 474px) 100vw, 474px" />][5]

Se você quiser editar o que escreveu, basta clicar no botão ‘edit’, senão, se estiver satisfeito com o resultado, basta clicar no botão ‘publish’.

Pronto! Já possuímos uma página no github para o nosso repositório.

## E como faço para acessar essa página?

As páginas criadas pelo github possuem o seguinte formato de endereço:

http://<span style="color: #ff0000">nomedousuario</span>.github.io/<span style="color: #ff0000">nomedorepositorio</span>

No meu caso, o endereço ficou disponível da seguinte maneira:

<http://wmartins.github.io/criando-paginas-github-pages/>

Portanto, basta substituir os valores em vermelho para acessar a sua página!

## Erro 404!?

O github demora um pouco (cerca de uns 10 minutos) para criar a sua página e disponibilizá-la, portanto, se você tentar acessá-la e estiver dando um erro 404, não se assuste, em breve ela estará disponível!

Se você já esperou algum tempo e o erro 404 persiste, verifique se digitou corretamente o endereço e tente novamente.

## Branch ‘gh-pages’

Mas, qual é a mágica envolvida nisso? Como o github sabe onde está essa minha página recém criada? E se eu quiser adicionar coisas mais complexas, como por exemplo um demo do que estou desenvolvendo?

A resposta dessa pergunta pode ser respondida ao observarmos os branches do nosso projeto. Ao olharmos a listagem de branches, conseguimos ver que um branch chamado ‘gh-pages’ foi criado automaticamente.

O gh-pages é o responsável por conter os arquivos que darão vida à nossa página, assim, se o explorarmos, poderemos ver que existem arquivos como ‘index.html’, arquivos ‘.css’ entre outros. Enfim, é um branch que representa toda a página gerada.

[<img class="size-full wp-image-38030 aligncenter" alt="github-gh-pages-branch" src="http://tableless.com.br/uploads/2013/07/github-gh-pages-branch.png" width="512" height="232" srcset="uploads/2013/07/github-gh-pages-branch.png 512w, uploads/2013/07/github-gh-pages-branch-329x149.png 329w" sizes="(max-width: 512px) 100vw, 512px" />][6]

## Mas, e agora? Como edito a minha página?

Como essa página é gerada a partir de um branch (o branch gh-pages), é só editarmos os códigos desse branch que automaticamente editamos a página. Para isso, podemos realizar o seguinte procedimento:

1. Baixamos o branch ‘gh-pages’ no nosso repositório local.

2. Fazemos as modificações necessárias.

3. Fazemos o commit dos arquivos modificados.

4. Realizamos um push para o branch ‘gh-pages’.

5. Pronto!

## E como eu baixo o branch gh-pages?

Para baixar o branch gh-pages devemos realizar um fetch desse branch através do comando:

<pre class="lang-git">git fetch origin gh-pages</pre>

Após baixar esse branch, simplesmente trocamos o branch em que estamos para o branch gh-pages através do comando:

<pre class="lang-git">git checkout gh-pages</pre>

Agora é só editar o que desejarmos e realizarmos os pushs e commits para que a a nossa página seja atualizada.

## Já tenho um layout pronto que fiz manualmente, como posso usá-lo para gerar uma página no github?

Bom, isso é simples, o github mostra as páginas lendo os arquivos do branch gh-pages, dessa forma, basta ter esse branch criado com um arquivo ‘index.html’ dentro que o github irá exibir a página corretamente.

## Cuidado:

Um único ponto importante para quem quer criar uma página no github manualmente é tomar o cuidado de fazer com que o branch gh-pages seja um branch órfão, ou seja, não tenha nenhum branch ‘pai’ associado. Visto que se este possuir algum branch pai, pode ser que em alguma alteração em algum dos dois cause uma boa dor de cabeça ou no branch pai ou no branch gh-pages após a realização de commits e pushs.

## Como assim branch órfão? Como faço para criar um?

Criar um branch órfão é um processo bem simples, usualmente, para criarmos um branch usamos o seguinte comando:

<pre class="lang-git">git checkout -b new-branch</pre>

Porém, esse comando irá estabelecer uma relação entre o branch que estávamos com o branch recém criado, e isso é um problema quando estamos trabalhando no branch para geração de páginas, visto que não queremos associar o código do projeto com o código da página. Dessa forma, podemos usar a opção &#8216;orphan&#8217; para criar um branch desasociado de qualquer pai, nesse caso, já faremos a criação do branch gh-pages:

<pre class="lang-git">git checkout --orphan gh-pages</pre>

Após criarmos o branch gh-pages, basta adicionar os arquivos (lembre-se de adicionar um arquivo chamado index.html) e realizar o commit e o push dos mesmos.

## Considerações finais

Não sei se acontece o mesmo com vocês, mas quando eu vejo um repositório no github, a primeira coisa que eu procuro ver é se o mesmo possui algum demo ou então algum exemplo interessante de utilização.

No final das contas, por mais que o código seja muito bem elaborado e etc, a melhor forma de atrair as pessoas para o seu repositório é disponibilizando uma página para o mesmo.

Portanto, minha recomendação é que se você possui um projeto hospedado no github, tente criar uma página para ele. Quem sabe você não acaba atraíndo mais desenvolvedores para ajudar e torne o seu projeto mais legal ainda?

 [1]: http://tableless.com.br/uploads/2013/07/its-free.png
 [2]: http://tableless.com.br/uploads/2013/07/github-settings-option.png
 [3]: http://tableless.com.br/uploads/2013/07/github-pages-box.png
 [4]: http://tableless.com.br/uploads/2013/07/github-pages-form.png
 [5]: http://tableless.com.br/uploads/2013/07/github-pages-template.png
 [6]: http://tableless.com.br/uploads/2013/07/github-gh-pages-branch.png