---
title: Criando comandos de atalhos no terminal
author: Willem Allan
type: post
date: 2013-04-14
excerpt: Criando comandos de atalhos direto no terminal.
url: /criando-comandos-de-atalhos-no-terminal/
dsq_thread_id: 1209281575
categories:
  - Editores
  - Técnicas e Práticas
tags:
  - django
  - linux
  - mac
  - python
  - terminal

---
Esta dica pode ser utilizada em qualquer distribuição Linux ou Mac OS X.

Se você está cansado de digitar comandos gigantescos no terminal, aqui vai uma dica: crie atalhos para os comandos no seu terminal para melhorar a produtividade. Uma dica simples mas é muito util.

Para rodar um projeto python/django, geralmente executamos este comando:

<pre class="lang-bash">python manage.py runserver
</pre>

Com o comando de atalho criado, execute-o desta maneira:

<pre class="lang-bash">run</pre>

## Criando os atalhos

Para começar a criar seus atalhos, abra o arquivo **.profile** ou **.bashrc** que ficam na raiz da pasta do usuário. Em seguida abra-os em seu editor de preferência.

<pre class="lang-bash">sublime ~/.bashrc</pre>

Agora adicione a função no final do arquivo:

<pre class="lang-bash">run() {
    echo "executando... python manage.py runserver
    python manage.py runserver
}
</pre>

Pronto! Agora basta atualizar o arquivo para que o terminal o reconheça e entenda os novos comandos. Faça isso assim:

<pre class="lang-bash">source ~/.bashrc</pre>

Após a execução do comando acima, a funcão criada já está disponível no terminal, digite o comando abaixo para testar:

<pre class="lang-bash">run</pre>

Podemos fazer funções mais elaboradas, imagine que você precisa rodar diversos projetos e cada um em uma porta diferente, então veja como fazer:

<pre class="lang-bash">run() {
    if [ "$1" != '' ]; then
        python manage.py runserver "0.0.0.0:$1"
    else
        python manage.py runserver "0.0.0.0:8000"
    fi
}
</pre>

Outra dica é utilizar argumentos em suas funções. No caso da função acima, $1 é um argumento que é passado após o comando que define em qual porta irá rodar o projeto. Se não for passado nenhum valor, ele irá rodar na porta padrão que foi definida como 8000.

<pre class="lang-bash">run</pre>

<pre class="lang-bash">run 8001</pre>

<pre class="lang-bash">run 8002</pre>

É possível passar diversos argumentos, veja um exemplo na função:

<pre class="lang-bash">teste(){
    echo $1 $2;
}
</pre>

Os argumentos veem em seguida ao comando sempre com espaços entre eles, como no exemplo abaixo:

<pre class="lang-bash">teste Willem Allan</pre>

Retorno do comando executado será:

<pre class="lang-bash">Willem Allan</pre>

Logo abaixo seguem algumas funções que eu utilizo no meu .bashrc 😉

<pre class="lang-bash"># git commit
cm() {
    git commit -m "echo $1" -a
}

# git add all & commit
cma() {
    git add .
    git commit -m "echo $1" -a
}

# python - run django
run() {
    if [ "$1" != '' ]; then
        python manage.py runserver "0.0.0.0:$1"
    else
        python manage.py runserver "0.0.0.0:8000"
    fi
}

# python - migrate
migrate() {
    echo "executando... python manage.py migrate"
    python manage.py migrate
}

# python - auto
auto() {
    echo "executando... python manage.py schemamigration $1 --auto"
    python manage.py schemamigration $1 --auto
}

# python - initial
initial() {
    echo "executando... python manage.py schemamigration $1 --initial"
    python manage.py schemamigration $1 --initial
}
</pre>