---
title: Deixando seu site online com Surge.sh
author: Fabio Soares
type: post
date: 2016-08-29
excerpt: Com apenas seis caracteres na linha de comando você pode deixar seu site estático online.
url: /deixando-seu-site-online-com-surge-sh/
titulo_personalizado:
  - 'Coloque seu site estático no ar, com <strong>uma linha de comando</strong>'
categories:
  - Código
  - Destaques
  - Técnicas e Práticas

---
Já pensou em um mundo perfeito onde você pode digitar uma linha de comando e em poucos segundos o seu website está online? E mais um detalhe, **GRATUITAMENTE**.

Sim, é verdade, esse mundo existe com o <a href="https://surge.sh/" target="_blank">Surge.sh</a>.

<a href="https://surge.sh/" target="_blank">Surge.sh</a> é muito simples de usar, para você instalar você precisa do gerenciador de pacotes <a href="http://nodejs.org" target="_blank">npm</a>.

## Instalando

Para instalar digite o comando:

<pre class="lang-shell prettyprint linenums prettyprinted">$ npm install --global surge 
</pre>

Pronto! O <a href="https://surge.sh/" target="_blank">Surge.sh</a> já está pronto para usar.

## Utilizando

Para utilizar basta ir para pasta do seu projeto e digitar o seguinte comando:

<pre class="lang-shell prettyprint linenums prettyprinted">$ surge
</pre>

Se for o seu primeiro uso, você terá que criar uma conta de forma gratuita na plataforma. Depois de criar a conta ou logar, o <a href="https://surge.sh/" target="_blank">Surge.sh</a> mostrará algumas informações:
  
![][1]

Ele mostra o diretório do teu projeto, o tamanho e quantidade de arquivos e ele sugere um subdomínio aleatório, mas que você pode alterar, inclusive pode incluir um domínio próprio, que eu vou ensinar como fazer daqui a pouco.

Depois disso, PRONTO, o seu website estático está online.

## Definino o próprio domínio

Com <a href="https://surge.sh/" target="_blank">Surge.sh</a> você pode usar um domínio próprio, isso significa que você pode publicar o _seu-dominio.com.br_.

### Definindo o CNAME

Vá no seu servidor DNS e adicione o seu subdomínio surge.sh **CNAME**(_mega-dev.surge.sh_ por exemplo). Caso seu DNS não suporte **CNAME**, suporte apenas **A** você pode colocar o IP `45.55.110.124`.

Agora na linha de comando é só usar o comando

<pre class="lang-shell prettyprint linenums prettyprinted">$ surge diretorio/do/projeto seu-dominio.com.br
</pre>

### Salvando o domínio personalizado

Para que o <a href="https://surge.sh/" target="_blank">Surge.sh</a> &#8220;se lembre&#8221; do domínio personalizado, é preciso salvar o domínio em um aquivo chamado **CNAME**(sem extensão) na pasta raiz do seu projeto. Apenas o domínio na primeira linha sem qualquer tipo de marcação.

<pre class="lang-shell prettyprint linenums prettyprinted">echo seu-dominio.com.br &gt; CNAME
</pre>

## E se eu quiser retirar o site da rede?

Para desativar o site, ter todos os arquivos apagados e liberar o domínio também é preciso apenas um comando

<pre class="lang-shell prettyprint linenums prettyprinted">$ surge teardown seu-dominio.com.br
</pre>

## Conclusão

O <a href="https://surge.sh/" target="_blank">Surge.sh</a> possui diversas outras funcionalidades, como adicionar alguém ao seu projeto, usar URL amigáveis, usar Jekyll caso você queira conteúdo dinâmico. Você pode acessar o <a href="https://surge.sh/" target="_blank">site</a> e ler a <a href="https://surge.sh/help/getting-started-with-surge" target="_blank">documentação</a> para atender as suas necessidades. A plataforma possui um plano pago que te permite utilizar várias outras funções.

 [1]: https://surge.sh/images/help/getting-started-with-surge.gif