---
title: Adicionando SSL no NGINX com o Let’s Encrypt
author: Sergio Rodrigues
type: post
date: 2016-12-02
url: /adicionando-ssl-no-nginx-com-o-lets-encrypt/
titulo_personalizado:
  - "Adicionando SSL no NGINX com o <strong>Let's Encrypt</strong>"
categories:
  - Artigos
  - Back-end
  - Destaques
tags:
  - ssl

---
O **Let&#8217;s Encrypt** é uma forma fácil, automatizada e gratuita de se inserir **[SSL][1]** em uma aplicação _web_. A utilização do **SSL** é bem importante quando se há autenticação, tráfego de dados privados ou até mesmo para ser melhor colocado no _ranking_ do _Google_.

Neste artigo vou demonstrar como gerar e adicionar o **SSL** no **NGINX** com a ferramenta **Let&#8217;s Encrypt**. Irei utilizar o sistema operacional _Debian_ para executar os comandos, mas estes podem ser facilmente modificados para serem executados em qualquer _distro_.

#### Instalando o Let&#8217;s Encrypt: {#instalandooletsencrypt}

Clone o projeto no _github_ e redirecione para o caminho **/opt/letsencrypt**:

<pre class="lang-bash">$ sudo git clone https://github.com/letsencrypt/letsencrypt /opt/letsencrypt
</pre>

É necessário ter o _git_ instalado, caso não tenha:

<pre class="lang-bash">$ sudo apt-get install git
</pre>

#### Preparando o NGINX para ser validado: {#preparandoonginxparaservalidado}

O **Let&#8217;s Encrypt** valida se o domínio realmente é seu, então para isso é necessário adicionar uma regra no seu _site_ do **NGINX**. Adicione o **location** _^/.well-known_ no seu site **(/etc/nginx/sites-enabled/yoursite)**, como por exemplo:

<pre class="lang-css">server {  
    listen 80;
    server_name your-domain.com.br;

    location ~ ^/.well-known {
        root /var/www/yoursite;
    }

    location / {
        return 301 https://www.$server_name$request_uri;
    }
}
</pre>

Este **location** será requisitado pelo **Let&#8217;s Encrypt** para confirmar sua identidade. Lembrando que você deve substituir o **root** e o **server_name**.

Após adicionar o _well-known_, reinicie o seu **NGINX**:

<pre class="lang-bash">$ sudo systemctl restart nginx
</pre>

_É bom lembrar que o seu domínio deve estar apontando para sua aplicação para obter sucesso com o **SSL**._

#### Gerando o SSL com o Let&#8217;s Encrypt: {#gerandoosslcomoletsencrypt}

Substitua no comando abaixo, o caminho **/var/www/yoursite** pelo diretório raiz do seu site no **NGINX**, e também o **yourdomain.com.br** e **www.yourdomain.com.br** pelo seu domínio:

<pre class="lang-bash">$ sudo /opt/letsencrypt/letsencrypt-auto certonly -a webroot --webroot-path=/var/www/yoursite -d yourdomain.com.br -d www.yourdomain.com.br
</pre>

Neste processo irá ser solicitado seu _e-mail_, para caso necessite da recuperação de seu certificado.

#### Adicionando o certificado em sua aplicação: {#adicionandoocertificadoemsuaaplicao}

Após o certificado ser gerado com sucesso, altere novamente o seu arquivo de regras do seu site **(/etc/nginx/sites-enabled/yoursite)**, adicionando mais um **server**, desta vez o de **ssl**:

<pre class="lang-bash">server {  
    listen 443 ssl;
    server_name yourdomain.com.br www.yourdomain.com.br;

    location / {
        proxy_pass http://localhost:8080;
        proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
        proxy_set_header Host $http_host;
        proxy_set_header X-Forwarded-Proto $scheme;
        proxy_buffering off;
    }

    location ~ ^/.well-known {
        root /var/www/yoursite;
    }

    ssl_certificate /etc/letsencrypt/live/yourdomain.com.br/fullchain.pem;
    ssl_certificate_key /etc/letsencrypt/live/yourdomain.com.br/privkey.pem;
}
</pre>

_Lembrando que você deve alterar o **location /** com as configurações específicas da sua aplicação web._

Reinicie novamente o seu **NGINX**:

<pre class="lang-bash">$ sudo systemctl restart nginx
</pre>

Entre em seu domínio utilizando o **https** e veja se o processo ocorreu com sucesso.

#### Conferindo a qualidade do seu SSL: {#conferindoaqualidadedoseussl}

Altere _example.com_ pelo seu domínio:

<https://www.ssllabs.com/ssltest/analyze.html?d=example.com>

#### Melhorando a qualidade do seu certificado: {#melhorandoaqualidadedoseucertificado}

É importante validar as cifras utilizadas, limitar a versão do protocolo **SSL**, entre outras coisas. Para isso, recomendo a leitura do seguinte tópico na wiki da Mozilla, [Server Side TLS][2]. Existe também o [Mozilla SSL Configuration Generator][3], um gerador de configuração **SSL** para diversos servidores de aplicação.

#### Renovando seu certificado com crontab: {#renovandoseucertificadocomcrontab}

O certificado gerado é válido por 3 meses, para facilitar a renovação, você pode criar um _cronjob_ para fazer este trabalho:

<pre class="lang-bash">$ crontab -e
</pre>

Adicione no final do arquivo:

<pre class="lang-bash">0 0 1 */2 * /opt/letsencrypt/letsencrypt-auto renew --quiet --no-self-upgrade  
0 0 1 */2 * systemctl reload nginx  
</pre>

### Concluindo:

Neste artigo foi demonstrando a geração do **SSL** para o **NGINX**, mas este mesmos passos podem ser facilmente executados em qualquer servidor de aplicação, com algumas modificações. Lembrando que existem outros comandos específicos da ferramenta **Let&#8217;s Encrypt**, como **letsencrypt-apache** que faz todo o trabalho pra você no caso do _Apache_, mas tentei demonstrar a forma genérica, que pode servir para outros servidores.

### Referências e Links:

  * <https://letsencrypt.org>
  * <https://github.com/certbot/certbot>
  * <https://www.digitalocean.com/community/tutorials/how-to-secure-nginx-with-let-s-encrypt-on-ubuntu-16-04>
  * <https://www.nginx.com/blog/free-certificates-lets-encrypt-and-nginx>

* * *

O certificado [SSL][1] também pode ser contratado na [1&1][4] ou Certisign.

 [1]: https://www.1and1.com/certificado-ssl
 [2]: https://wiki.mozilla.org/Security/Server_Side_TLS
 [3]: https://mozilla.github.io/server-side-tls/ssl-config-generator
 [4]: https://www.1and1.com/