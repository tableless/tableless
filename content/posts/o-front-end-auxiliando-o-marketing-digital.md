---
title: O Front-end auxiliando o Marketing Digital
author: Deivid Marques
type: post
date: 2012-09-30
excerpt: Nos dias atuais estamos ligados a semântica, seo, performance, boas práticas, entre outros assuntos, que tal ajudar também a equipe de Marketing Digital?
url: /o-front-end-auxiliando-o-marketing-digital/
tweetbackscheck:
  - 1356393177
shorturls:
  - 'a:3:{s:9:"permalink";s:31:"http://tableless.com.br/?p=6931";s:7:"tinyurl";s:26:"http://tinyurl.com/9f6pe3t";s:4:"isgd";s:19:"http://is.gd/Lspqc2";}'
twittercomments:
  - 'a:0:{}'
dsq_thread_id: 859140025
categories:
  - Artigos
tags:
  - 2012
  - facebook
  - front-end
  - marketing digital
  - social
  - socialmedia

---
Aos desenvolvedores front-ends, que trabalham em agências que possuem a área de Marketing Digital, saiba que vocês podem ser muito úteis para esses profissionais.
  
Nesse post resolvi escrever sobre criação de um app simples e deixá-lo como Aba Personalizada dentro de uma Página do Facebook, gerando insights (dados estatísticos) para a equipe de Marketing Digital, pois assim fica mais fácil para criar estratégias e mensurar os resultados gerados pela própria rede social.

Em outras palavras, vamos pegar o conteúdo hospedado por você em um servidor e “embedar” dentro de uma Página do Facebook, como se fosse um iframe, porém, seguindo as recomendações da maior rede social até o momento.

### Iniciando a estrutura:

1. Necessário ter um servidor com url segura, ou seja, que tenha url https://
  
2. Imagem 75&#215;75 pixels (icone de aplicativo)
  
3. Imagem 16&#215;16 pixels (favicon de aplicativo)
  
4. Imagem 111&#215;74 pixels (icone de aba na page)

### Dicas:

1. O Layout não deve ultrapassar o tamanho de 800 x 800 pixels, evitando barra de rolagem dentro da Page.
  
2. Criar uma pasta no servidor e o arquivo inicial como index
  
Exemplo: http://urldosite.com.br/app/index.html
  
3. Desenvolva o html, css e js normalmente e faça upload em uma pasta específica no servidor.
  
4. Após efetuar o upload de todos os arquivos, vamos precisar de 2 urls.

**Exemplo:**
  
A: http://urldosite.com.br/app/
  
B: https://urlsegura.com.br/app

_Obs: Para saber o endereço da url segura, é necessário ver com sua hospedagem._

#### Passo 1:

1. Entre no link <a title="Área de desenvolvimento de app do Facebook" href="https://developers.facebook.com/apps" target="_blank">https://developers.facebook.com/apps</a> ou buscar, no fim do sidebar direito, o link Mais >> Desenvolvedores, depois clicar no link do topo: Aplicativos
  
2. Clique no link “Criar um novo Aplicativo”
  
3. Para criar apps do Facebook é necessário que sua conta seja validada com um número de celular ou cartão de crédito, caso já tenha sido, basta continuar.
  
4. Digite o nome do seu app e clique em “Continuar”
  
5. App Criado.

![App Facebook para Pages][1]

#### Passo 2: 

1. Selecione a Categoria: Aplicativos para Páginas
  
2. Inserindo Imagens do seu app
  
A: Imagem que será exibida em ambiente de Aplicativos no Facebook
  
B: Imagem de ícone que será exibida minimizada na Aba da Pagina no Facebook.

![App Facebook para pages][2]

3. Clique em App on Facebook e preencha os campos com as url absoluta e a url segura, conforme a imagem abaixo:

![App Facebook para pages][3]

4. Clique em Page Tab (legenda da imagem abaixo)
  
A: Nome que vai aparecer na Aba da Página no Facebook
  
B: url do projeto
  
C: url segura do projeto
  
D: Link para inserir a imagem que aparecerá na Aba da Página no Facebook (lembrando que o tamanho é de: 111 x 74 pixels)
  
E/F: Definição de largura de conteúdo do Aplicativo dentro da Página no Facebook

![App Facebook para pages][4]

5. Clique em “Salvar Alterações”

**Criando a Aba na Página.**
  
1.Pronto! Seu app já foi criado. Agora vou ensinar a mágica de criar a Aba dentro da sua Página no Facebook, trazendo esse conteúdo, para isso, é necessário ser Administrador da Página no Facebook.
  
A: Ao Criar o app ele terá um ID único conforme a imagem abaixo:

![App Facebook para pages][5]

2: Copie e cole a url abaixo em seu navegador com o ID do seu app.
  
Exemplo: https://www.facebook.com/add.php?api_key=APP-ID&pages=1&

3. Em seguida, abrirá uma janela mostrando todas as página que você for administrador, basta selecionar a página escolhida e clicar em “Adicionar”, conforme a imagem abaixo

![App Facebook para Pages][6]

**IMPORTANTE:
  
** 
  
No seu html, é necessário inserir um código simples, para que os profissionais de Marketing Digital possam acessar esses dados estatísticos gerados pelo próprio Facebook.
  
Inserindo o código abaixo no seu html, basta colocar o ID do aplicativo, o mesmo que usamos na url para criar a Aba no Facebook.
  
Insira o html abaixo entre a tag **HEAD**

**<meta property=&#8221;fb:app_id&#8221; content=&#8221;APP-ID&#8221;>**

ou

**<meta property=&#8221;fb:admins&#8221; content=&#8221;USER_ID&#8221;/>**

User_ID = ID do seu Perfil, caso não saiba qual é o seu , veja o exemplo:

<a title="Dados do Perfil do Deivid Marques no Facebook" href="http://graph.facebook.com/deividmarquess" target="_blank">http://graph.facebook.com/deividmarquess</a>
  
ID= 100000470381955

Bem, espero ter ajudado a todos, qualquer dúvida basta deixar uma mensagem por aqui.
  
Na minha Page, existem alguns apps Promocinais que eu já criei: <a title="Página do Deivid Marques" href="https://www.facebook.com/deividmarques.com.br" target="_blank">https://www.facebook.com/deividmarques.com.br</a>

#### Em caso de dúvidas, confira as documentações do Facebook

1. Central de ajuda:
  
<a title="Central de Ajuda" href="http://www.facebook.com/help/?ref=pf" target="_blank">http://www.facebook.com/help/?ref=pf</a>
  
2. Documentação Developers (APP):
  
<a title="Documentaçao do Facebook " href="https://developers.facebook.com/docs/" target="_blank">https://developers.facebook.com/docs/</a>
  
3.Blog dos desenvolvedores:
  
<a title="Blog dos Desenvolvedores do Facebook" href="https://developers.facebook.com/blog" target="_blank">https://developers.facebook.com/blog</a>

 [1]: https://lh5.googleusercontent.com/4difRBMeCIeY17-CtclLKkUyguliSxePUsLDcgLfYPkeq07M-6W4IfibX_Y1-_xY7pYp1ezKwFVVpZjuOyLtuu7_mbBz1TJqC-OncFMpih2eKRtXYY0s
 [2]: https://lh6.googleusercontent.com/U7xO8qBBa7Jm6SDvfZtVGMqpvvpSoCopfM_bPEVMrjK0Kc0eTNYD8S8k3YapwG2OPxu-TKHOAhKikPUYLL5C_a4WHBnkXRaADDQoaXH_nl4LqVUJ9jMS
 [3]: https://lh4.googleusercontent.com/Uydm1ezb9Zrim0LAlwZ7mddxVD5oEkUGyL8YokrvVDmZkNJqvRt0YxFhr8q8JLdYh8GoTka-4Avqu0nIPXq6oeRz3yis_2eG_S3PfOshJLdF5i0VwTjy
 [4]: https://lh5.googleusercontent.com/-3aHe8lIzfyWxuwl1pFD19RX_Sd_bdQwNuzk2ow32CYbpgb_H8C4zhKj68k5cRB1KEdoQNxZ4qrCE4p0StQwxT1gHBiTWf-PqY_ME1U92nxygovuf7eM
 [5]: https://lh4.googleusercontent.com/oojacp-bM6uAroruxVTbqrXpeY8y2_vCXr_aYHylYNA_XmXO9cDSRlWESRn5rkyrHAqgenoj4GuzoofkuKglBkR1a7l4X1M3Jm4C3CSfO1ByWENrMzvo
 [6]: https://lh3.googleusercontent.com/s5Kg7J__SH27XBF06K3VlV9_aFy4ZWsOEh8-Wjn7eD9_-N6fZQkt2EcuEdh6KktrblGFcm9Y2keG5Qnf0jCcP8iFZg1QZGfPdSNf7pZOAgC9cuEPG8Ix