---
title: Instalando e configurando NGINX via Homebrew
author: Diego Eis
type: post
date: 2017-01-12
url: /instalando-e-configurando-nginx-via-homebrew/
categories:
  - Código
  - Tooling

---
# Instalando NGINX no Mac com Homebrew

Faz um tempo que deixei de usar Apache como Web Server padrão, tanto no servidor do Tableless, quanto para projetos pessoais. Se você quiser instalar o NGINX no seu Mac, usando Homebrew, basta seguir os passos abaixo:

<pre class="lang-bash">brew install nginx
</pre>

<img src="uploads/2017/01/first-command.png" alt="first-command" width="1172" height="670" class="aligncenter size-full wp-image-56786" />

Feito isso, o NGINX já deve estar rodando. Para testar, rode o comando abaixo:

<pre class="lang-bash">sudo nginx
</pre>

Agora entre em **localhost:8080** pelo seu navegador. Deve aparecer uma tela mais ou menos igual a essa:

<img src="uploads/2017/01/nginx-works.png" alt="nginx-works" width="976" height="668" class="aligncenter size-full wp-image-56787" />

Feito isso, vamos agora configurar nosso NGINX. Primeiro, vamos querer mudar a porta onde o NGINX está respondendo que é **8080** para **80**. Para tanto, pare o servidor do NGINX:

<pre class="lang-bash">sudo nginx -s stop
</pre>

Para que não dê alguma treta obscura, pare o Apache também.

<pre class="lang-bash">sudo apachectl stop
</pre>

O arquivo de configuração do NGINX no Mac, via Homebrew fica nesse endereço **/usr/local/etc/nginx/nginx.conf**. Abra-o com seu editor de texto predileto.

Você vai perceber que há uma série de configurações default. Provavelmente, na linha 36 vai estar o bloco **server**, com a opção da porta. Mude para 80. Salve e reinicie o NGINX.

<pre class="lang-bash">sudo nginx
</pre>

Abra seu navegador no **localhost**. Deve estar funcionando.

## Mudando o path default

Aqui no meu Mac, eu gosto de usar os projetos na pasta **~/Sites**. Por default, o Brew diz que a pasta default é **/usr/local/Cellar/nginx/3.2.1/html**, onde **3.2.1** é a versão do seu NGINX. Para descobrir a versão do seu NGINX, basta digitar **nginx -v** no seu terminal. O meu retornou **nginx version: nginx/1.10.2**.

Abra novamente o **nginx.conf**. Provavelmente ali na linha 44, vai ter algo assim:

<pre class="lang-javascript">location / {
    root   html;
    index  index.html index.htm;
}
</pre>

Mude o **root html** para **root [endereço da pasta]**. Aqui no meu ficou assim:

<pre class="lang-javascript">location / {
    root   /Users/diegoeis/Sites;
    index  index.html index.htm;
}
</pre>

Tudo já deve estar funcionando agora.