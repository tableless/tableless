---
title: Instalando SASS na máquina – video
author: Diego Eis
type: post
date: 2014-08-18
excerpt: Quer usar SASS em seus projetos? Instale SASS na sua máquina e saia usando.
url: /instalando-sass-na-maquina-video/
dsq_thread_id: 2920943771
categories:
  - Código
  - CSS
  - Pré-processadores
  - SASS
tags:
  - CSS
  - pre-processador
  - SASS

---
Se você quiser usar um pré-processador em seus projetos, aqui vão instruções simples para você começar agora. Darei mais atenção para quem usa Mac porque é o sistema que eu uso. Mas no Windows as instruções são quase as mesmas, principalmente se você for usar algum sistema que gerencia os assets. Também estou abordando aqui apenas o SASS, nada de LESS, Style ou qualquer outro pré-processador. Depois desse disclaimer, vamos ao que interessa.

## Iniciando

Um pré-processador precisa ser pré-processado (!) antes do código resultante seja renderizado pelo browser. Isso quer dizer que o browser nunca (nunca diga nunca) vai ler direto seu código SASS e renderizar seu código. Por isso, você precisa de um parser, que vai ler seu SASS, salvar em um arquivo CSS para seu browser renderizar o CSS.

O SASS é uma GEM do Ruby, logo, invariavelmente você vai precisar do Ruby. Por isso, existem duas maneiras de você usar um Pré-processador sem se preocupar em preparar seu ambiente e rodar SASS com tranquilidade. A primeira forma é usando alguma aplicação que vai ler e parsar seus arquivos SASS, sem a necessidade do Ruby no ambiente. Claro, você vai precisar esperar alguns segundos para dar um refresh na página. Isso acontece por que o aplicativo está parseando seu código.

A outra maneira é a melhor, você não tem esse delay de segundos, mas é mais complicada para quem não está acostumado com Terminal. Mesmo assim, é tão fácil, tão fácil, que eu sugiro que você tente primeiro fazer funcionar o SASS pelo terminal, se conseguir, tente usar a aplicação.

## Scout

Existem várias aplicações que compilam SASS e outras linguagens como CoffeeScript, TypeScript, LESS, Stylus e etc. A maioria deles é pago, mas muito bons. Se você preferir pagar, sugiro que use o mais famoso que é o [CodeKit][1]. Mas se você não quer pagar nada, sugiro o Scout. 

O [Scout][2] (tem para Windows e Mac) é um compilador para exclusivo SASS/Compass e ele tem um único objetivo, ler seus arquivos SASS, parsear, compilar e por fim salvar em uma pasta no formato CSS.

Fiz um vídeo mudo (sou tímido) que mostra como adicionar um projeto no Scout. Basicamente você escolhe a pasta do projeto e indica quais as pastas onde ele vai encontrar os arquivos SASS e onde ele vai salvar os arquivos .CSS. Normalmente eu escolho sempre a mesma pasta, mas você pode escolher uma outra pasta que vai salvar os arquivos CSS finais. Veja abaixo o vídeo:



Se você quiser testar outra aplicação em vez do Scout, experimente o [Koala][3]. Ele também é free e compila outros pré-processadores como o LESS e CoffeeScript.

## Usando o terminal

Para usar no terminal, você precisa ter na máquina Ruby e a gem do Sass instalada. Feito isso, você vigia a pasta com os arquivos SASS com o comando abaixo:

<pre class="lang-shell">sass --watch [diretório dos arquivos SASS]
</pre>

Simples assim.
  
Se você quiser avançar e já leu sobre Compass e sua facilidade de usar CSS3, você usá-lo para vigiar sua pasta. Para iniciar o projeto:

<pre class="lang-shell">compass create [nome do projeto]
</pre>

Se você já tiver a pasta do projeto, basta fazer o mesmo comando. Ele vai criar dentro da pasta uma pasta chamada **sass**, com os arquivos SASS, uma pasta **stylesheet**, que é onde vai ficar o código CSS resultante do SASS. Ele vai criar também um arquivo **config.rb**, que é onde fica as configurações do seu projeto. 

Quando tiver feito esse comando acima, e claro, ter linkado o CSS no seu arquivo HTML, você pode começar digitar o comando **compass watch**, que vai vigiar a pasta stylesheets procurando por arquivos SASS e transformando-os em CSS.

Abaixo, veja outro vídeo mudo, onde eu crio o projeto e modifico o **config.rb** do Compass para que a estrutura de pastas fique do jeito que eu gosto, geralmente para mudar a estrutura de pastas, inserindo as pastas de stylesheets, imagens e javascripts para dentro da pasta **assets**.



Eu vou tentar melhorar ainda mais esse passo a passo com o tempo. Não encontrei nenhum lugar onde ensinasse exatamente como fazer para rodar SASS na máquina sem estar em um projeto Ruby. Isso era uma dificuldade para devs novatos que querem experimentar as maravilhosas peripécias do SASS.

 [1]: http://incident57.com/codekit/
 [2]: http://mhs.github.io/scout-app/
 [3]: http://koala-app.com