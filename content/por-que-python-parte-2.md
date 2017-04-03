---
title: Por que Python? (parte 2)
author: Elcio Ferreira
type: post
date: 2016-01-07
excerpt: Por que escrever código Python é tão bom? Por que os programadores Python são tão apaixonados? Parte da resposta é a própria sintaxe da linguagem.
url: /por-que-python-parte-2/
categories:
  - Back-end
  - Opinião
  - Técnicas e Práticas
  - Tecnologia e Tendências

---
Continuando meu [artigo anterior][1], vou tentar mostrar alguns motivos porque, em minha opinião, é tão bom escrever código Python. E dessa vez vamos falar da sintaxe da linguagem e seus tipos de dados. As características e recursos da sintaxe tornam Python uma linguagem tão poderosa e produtiva. Veja os exemplos:

## Packing e Unpacking

<pre># encoding: utf-8
# Atribuindo três valores de uma vez
a, b, c = 2, 3, 5
 
# Trocando o valor de duas variáveis:
a, b = b, a

# Uma função que retorna mais de um valor:
def vizinhos(n):
    return n-1, n+1

# Executando a função acima e guardando os valores em duas variáveis:
x, y = vizinhos(42)</pre>

## Sem sobrecarga de métodos

Você pode escrever uma função que pode receber parâmetros opcionais assim:

<pre>def addr(domain, path='/', querystring='', hash=''):
    return 'http://%s%s%s%s' % (domain,path,querystring,hash)</pre>

E pode chamar com um, dois, três ou quatro parâmetros:

<pre><strong>&gt;&gt;&gt;</strong> addr('tableless.com.br')
<em>'http://tableless.com.br/'</em>
<strong>&gt;&gt;&gt;</strong> addr('tableless.com.br','/code/css/')
<em>'http://tableless.com.br/code/css/'</em>
<strong>&gt;&gt;&gt;</strong> addr('tableless.com.br',querystring='?s=python')
<em>'http://tableless.com.br/?s=python'</em></pre>

Você pode até criar uma função que recebe qualquer quantidade de parâmetros:

<pre>def div(content,**attributes):
    html="&lt;div"
    for attribute in attributes.iteritems():
        html+=' %s="%s"' % attribute
    html+="&gt;"+content+"&lt;/div&gt;"
    return html</pre>

Veja funcionando:

<pre><strong>&gt;&gt;&gt;</strong> div("Hello")
<em>'&lt;div&gt;Hello&lt;/div&gt;'</em>
<strong>&gt;&gt;&gt;</strong> div("Hello",id="blue")
<em>'&lt;div id="blue"&gt;Hello&lt;/div&gt;'</em>
<strong>&gt;&gt;&gt;</strong> div("Hello",id="blue",contenteditable="true",title="Edite como quiser.")
<em>'&lt;div contenteditable="true" id="blue" title="Edite como quiser."&gt;Hello&lt;/div&gt;'</em></pre>

## Listas poderosas

Em programação, lidamos com arrays o tempo todo. Ter arrays flexíveis e poderosos em uma linguagem é algo que vai te ajudar o tempo todo. Veja esses exemplos:

<pre><strong>&gt;&gt;&gt;</strong> import random
<strong>&gt;&gt;&gt;</strong> l=[random.randint(0,100) for i in range(20)]
<strong>&gt;&gt;&gt;</strong> l
<em>[4, 89, 49, 87, 33, 7, 57, 41, 50, 53, 63, 71, 12, 57, 4, 32, 13, 9, 67, 9]</em>
<strong>&gt;&gt;&gt;</strong> l[0] <em><strong># Primeiro elemento</strong></em>
<em>4</em>
<strong>&gt;&gt;&gt;</strong> l[1] <em><strong># Segundo elemento</strong></em>
<em>89</em>
<strong>&gt;&gt;&gt;</strong> l[-1] <em><strong># Último elemento</strong></em>
<em>9</em>
<strong>&gt;&gt;&gt;</strong> l[-2] <em><strong># Penúltimo elemento</strong></em>
<em>67</em>
<strong>&gt;&gt;&gt;</strong> l[0:5] <em><strong># Primeiros cinco elementos</strong></em>
<em>[4, 89, 49, 87, 33]</em>
<strong>&gt;&gt;&gt;</strong> l[:5] <em><strong># Primeiros cinco elementos</strong></em>
<em>[4, 89, 49, 87, 33]</em>
<strong>&gt;&gt;&gt;</strong> l[-5:] <em><strong># Últimos cinco elementos</strong></em>
<em>[32, 13, 9, 67, 9]</em>
<strong>&gt;&gt;&gt;</strong> l[4::-1] <em><strong># Primeiros cinco elementos, de trás para frente</strong></em>
<em>[33, 87, 49, 89, 4]
</em><strong>&gt;&gt;&gt;</strong> l="abcdefghijklmnopqrstuvwxyz"
<strong>&gt;&gt;&gt;</strong> l[1] <em><strong># Segundo elemento</strong></em>
<em>'b'</em>
<strong>&gt;&gt;&gt;</strong> l[:5] <em><strong># Primeiros cinco elementos</strong></em>
<em>'abcde'</em>
<strong>&gt;&gt;&gt;</strong> l[-5:] <em><strong># Últimos cinco elementos</strong></em>
<em>'vwxyz'</em>
<strong>&gt;&gt;&gt;</strong> l[4::-1] <em><strong># Primeiros cinco elementos, de trás para frente</strong></em>
<em>'edcba'
</em></pre>

Veja, por exemplo, como saber quais os elementos comuns entre duas listas:

<pre><strong>&gt;&gt;&gt;</strong> l1=[1,2,3,4,5,6,7,8,9]
<strong>&gt;&gt;&gt;</strong> l2=[1,3,5,7,9]
<strong>&gt;&gt;&gt;</strong> set(l1) & set(l2)
<em>set([7, 1, 3, 5, 9])</em></pre>

E como remover de uma lista os elementos que existem em outra:

<pre><strong>&gt;&gt;</strong> set(l1)-set(l2)
<em>set([8, 2, 4, 6])
</em></pre>

Vamos criar uma função que recebe uma lista de strings e retorna uma lista HTML em ordem alfabética, com os duplicados removidos:

<pre>def ol(l):
    return "\n".join("&lt;li&gt;%s&lt;/li&gt;" % i for i in sorted(set(l)))</pre>

Veja funcionando:

<pre><strong>&gt;&gt;&gt;</strong> print ol(["charlie","foxtrot","bravo","delta","bravo","juliet","charlie","echo","alpha","bravo"])
<em>&lt;li&gt;alpha&lt;/li&gt;</em>
<em>&lt;li&gt;bravo&lt;/li&gt;</em>
<em>&lt;li&gt;charlie&lt;/li&gt;</em>
<em>&lt;li&gt;delta&lt;/li&gt;</em>
<em>&lt;li&gt;echo&lt;/li&gt;</em>
<em>&lt;li&gt;foxtrot&lt;/li&gt;</em>
<em>&lt;li&gt;juliet&lt;/li&gt;</em></pre>

## De novo, a biblioteca padrão

Por exemplo, estou apaixonado pelo módulo itertools:

<pre><strong>&gt;&gt;&gt;</strong> import itertools
<strong>&gt;&gt;&gt;</strong> for i in itertools.permutations('abc'):
<strong>...</strong>     print ''.join(i)
<strong>...</strong>
<em>abc</em>
<em>acb</em>
<em>bac</em>
<em>bca</em>
<em>cab</em>
<em>cba
</em><strong>&gt;&gt;&gt;</strong> for i in itertools.combinations('abc',2):
<strong>...</strong>     print ''.join(i)
<strong>...</strong><em>
ab
ac
bc
</em></pre>

No próximo artigo vamos falar mais sobre a biblioteca padrão.

 [1]: http://tableless.com.br/por-que-python/