---
title: Por que Python?
author: Elcio Ferreira
type: post
date: 2015-09-29
url: /por-que-python/
categories:
  - Back-end
tags:
  - back-end
  - backend
  - Código
  - desenvolvimento
  - desenvolvimento web
  - linux
  - mercado
  - open source
  - programação
  - programadores
  - python

---
Eu sou apaixonado por [Python][1]. Muito. Daquele tipo que fala de Python sempre que pode. E uma pergunta que sempre me fazem é: por quê? Vou tentar fazer uma lista dos motivos mais relevantes:

## 1. É muito bom escrever código Python

Geralmente, quando alguém cria uma linguagem de programação, tem em vista um objetivo. Por exemplo, Lisp foi escrita para programação funcional. Java foi escrita para que o mesmo código pudesse rodar em qualquer lugar. PHP foi criada para construir páginas web. E Python foi criada para ser produtiva e fácil de escrever.

Um programador experiente aprende a sintaxe do Python em algumas poucas horas. O jeito de escrever faz sentido.

Veja, por exemplo, essa função para calcular um número de [Fibonacci][2]:

<pre>def fib(n):
    if n&lt;3:
        return n
    return fib(n-1) + fib(n-2)</pre>

Note como a sintaxe é simples. Mesmo nas decisões de design que são &#8220;pouco ortodoxas&#8221;, como os blocos baseados na indentação, a decisão foi tomada pensando em produtividade. O modelo de blocos do Python faz com que você precise digitar menos. Além disso, é impossível escrever código não indentado em Python.

Veja nesse outro exemplo, a função de Fibonacci em uma versão [memoized][3]:

<pre>memo = {0:0, 1:1}

def fib(n):
    if not n in memo:
        memo[n] = fib(n-1) + fib(n-2)
    return memo[n]</pre>

Reparou como é simples? Ao trabalhar com Python, a linguagem nunca está entre você e seu problema. Você pode gastar seu tempo com a lógica de programação, que é o que realmente importa, e não com especificidades da linguagem que você está usando.

## 2. Organizar um projeto Python é muito fácil

Vamos colocar nossa função de Fibonacci e salvar num arquivo, fib.py, incluindo um pouquinho de documentação. Chamamos cada arquivo Python de módulo:

<pre>'''Fibonacci function, memoized for better performance.'''
memo = {0:0, 1:1}

def fib(n):
    '''Returns the nth Fibonacci number.'''
    if not n in memo:
        memo[n] = fib(n-1) + fib(n-2)
    return memo[n]</pre>

Agora vamos importar esse arquivo no console do Python, e veja o que dá para fazer:

<div style="width: 490px" class="wp-caption alignnone">
  <img class="" src="http://elcio.com.br/uploads/2015/09/fib.gif" alt="" width="480" height="267" />
  
  <p class="wp-caption-text">
    Executando fib.py e ajuda.
  </p>
</div>

É como PHPDoc ou Javadoc, mas completamente nativo, e com uma sintaxe muito simples. E tudo o que você precisa para ler a documentação é o próprio Python.

## 3. O ecossistema Python é fantástico

Começando pela própria linguagem, que vem com uma excelente [biblioteca padrão][4]. Essa biblioteca é bastante extensa e possui excelentes módulos, bem documentados e fáceis de usar. Por exemplo, digamos que você queira baixar o código fonte desse artigo e gerar um arquivo GZip com ele, veja como é fácil:

<pre>import urllib
import gzip
html=urllib.urlopen('http://tableless.com.br/por-que-python/').read()
gzfile=gzip.open('por-que-python.html.gz','w')
gzfile.write(html)</pre>

Usamos os módulos urllib e gzip. Entre os recursos fornecidos pelos módulos que já vem com o Python, posso citar o controle de threads e processamento paralelo, a criação de webservices, bibliotecas para sockets, http, ftp, e-mail, a leitura e escrita de XML, JSON, CSV, o acesso a recursos do sistema operacional, matemática e estatística, criptografia, manipulação de arquivos de áudio, testes automatizados, etc.

Como é fácil escrever código bom e bem documentado, a comunidade Python tem feito um excelente em fornecer módulos para praticamente tudo o que você precisar fazer. Você pode encontrar, no [Python Package Index][5], milhares de módulos prontos para coisas como ler e escrever arquivos Excel, trabalhar com imagens, acessar bancos de dados os mais diversos, trabalhar com automação residencial, enviar SMS, integrar seu software ao Gmail, falar com serviços de VoIP, conectar-se a redes sociais, criar um servidor de e-mails, desenvolver jogos 3D, e uma infinidade de outros recursos.

### E tem mais&#8230;

Se você não programa em Python, espero tê-lo deixado pelo menos um pouquinho curioso. No próximo artigo, vamos falar um pouco mais da linguagem, mostrando algumas características da sintaxe e dos tipos de dados que a tornam tão interessante. Até lá, fique à vontade nos comentários. Sugestões, dúvidas, críticas e opiniões são muito bem vindas e vão me ajudar a preparar os próximos artigos.

&nbsp;

 [1]: https://www.python.org/
 [2]: https://pt.wikipedia.org/wiki/Sequ%C3%AAncia_de_Fibonacci
 [3]: https://en.wikipedia.org/wiki/Memoization
 [4]: https://docs.python.org/3/library/
 [5]: https://pypi.python.org/pypi