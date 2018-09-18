---
title: Você conhece o Google Hacking?
authors: Julio Carneiro
type: post
date: 2017-08-20
excerpt: O Google Hacking nada mais é que uma prática para encontrar aquivos e/ou falhas a partir do GoogleEntão vamos entender e conhece-lo na prática!
categories:
  - SEO
  - Na Prática
tags:
  - SEO
  - Na Prática
image: https://cdn-images-1.medium.com/max/2000/1*emwyXFuZ7vlHsUFc0P1qkA.png
---

Hoje decidi trazer pra vocês algo que não é
novidade, porém é bem interessante para quem trabalha com web, vamos falar hoje
sobre **Google Hacking**!

Antes de tudo, lembre-se: você **não tem o direito de invadir a privacidade de ninguém**! O que
estou fazendo aqui é para **deixar desenvolvedores cientes de falhas que são
ridiculamente fáceis de serem exploradas e ridiculamente fáceis de serem
corrigidas também**!

## Bora falar de Google

O Google utiliza uma tecnologia chamada **spiders**, ou **webcrawlers** que são
robôs que fazem a varredura na web buscando e** indexando as páginas**. Quando
fazemos uma busca pela ferramenta ela procura por este termo nestas páginas
indexadas nos retornando **o que estamos procurando de fato**, cada resultado
retornado é composto por um **titulo**, uma **url** e uma **descrição**.

Um servidor mal configurado pode expor informações da empresa no Google. Não é
difícil conseguir acesso a arquivos de base de dados através do Google.

O **Google Hacking** nada mais é que uma prática para encontrar aquivos e/ou
falhas a partir do Google, usando ele como uma espécie de scanner, dando
comandos e possibilitando manipular buscas avançadas por strings chamadas de
"dorks" ou "operadores de pesquisa".

## Conhecendo as dorks:

Com a composição de **dorks** nós podemos retornar **domínios específicos**,
**títulos**, **palavras**, **arquivos**, e algumas outras coisas que vamos ver a
seguir:

"**site:**" — Busca em um site específico

```
site:exemplo.com.br
```

"**intitle:**" — Busca por título de páginas


```
intitle:"< Fazer login"
```

"**inurl:**" — Busca de termos presentes na url

```
inurl:/wp-admin
```

"**intext:**" — Busca por texto no conteúdo do site

```
intext:adminpass
```

"**filetype:**" — Busca por formato de arquivos (.jpg,.zip,.txt)

```
filetype:.txt
```


"**-termo**" — O "-" exclui o termo da pesquisa

"**2015…2017**" — Retorna resultados entre as datas estipuladas

Estes são só **alguns operadores**, com uma básica pesquisa sobre o assunto em
algum buscador **você consegue uma lista mais extensa**, a minha ideia é alertar
e **não me aprofundar no assunto**, é ensinar como funciona e **não te tornar um
especialista**.

## Construindo uma dork

Então com esses dados já conseguimos construir algumas dorks simples para
iniciar os estudos em nossos domínios e **achar possíveis falhas na indexação**
do nosso site.

Eu preciso de uma dork que me traga arquivos php da área de login do phpmyadmin
do meu site, como será que eu poderia fazer? Veja:


**Simples não**? Podemos adaptar conforme nossa necessidade, e caso acharmos
alguma brecha de segurança, caso o google esteja mostrando algo que ele não
devia estar, podemos **corrigir essa falha de um jeito muito simples**, veja:

Caso ainda não tenha, crie um arquivo "**robots.txt**" na pasta **raiz** do seu
site e vamos escrever uma regra para poder tirar a pasta "**/exemplo**" da
indexação geral:

```
    User-agent: * 
    Disallow: /exemplo/
```

Onde o **User-agent** são os mecanismos de busca, neste caso todos eles. <br>
**Disallow** vc está desativando a pasta "**/exemplo**".

- **NÃO** bloqueie no robots.txt até que as páginas **JÁ** indexadas sejam
removidas; <br> - Adicione a meta tag abaixo em todas as páginas que **desejar
remover**:

```html
<meta name="robots" content="noindex" />
```

Outro método simples de fazer isso é usando o **htpaswd** do **.htaccess**, nele
você pode limitar **por IP** (que pode ser manipulável e **não muito seguro**)
ou com **senhas** (**recomendável**).

### Wordpress

Fiz uma pequena pesquisa na web pois não uso Wordpress a algum tempo e o plugin
que eu usava **não existe mais**. **Segundo o HostGator** os 5 melhores plugins
de segurança para para usarmos no Wordpress são:

1.  [WP Security Scan](https://wordpress.org/plugins/wp-security-scan): escaneia seu
site em busca de vulnerabilidades. Caso encontre alguma, sugere ações
corretivas. Entre as ações, destaque para segurança das senhas, permissões de
arquivos, banco de dados e área administrativa, entre outras ações de proteção.
1.  [Login LockDown](https://wordpress.org/plugins/login-lockdown): analisa e
registra os endereços de IP que tentam fazer login no seu site, mas que por
alguma razão falham. Caso registre um determinado número de falhas no login, o
plugin bloqueia a caixa de login para o usuário por um tempo determinado.<br> O
plug-in é uma alternativa para ajudar a proteger seu site contra ataques
forçados.
1.  [Captcha on Login](https://wordpress.org/plugins/captcha-on-login): adiciona um
captcha na página de login, criando uma camada a mais de segurança no acesso à
área administrativa do site. O plugin bloqueia IPs determinados após um
determinado número de tentativas frustradas de login.<br> O sistema também
permite mudar o nome do usuário padrão do administrador, garantindo mais
segurança para seu site ou blog.
1.  [Wordfence Security](https://wordpress.org/plugins/wordfence/): mostra se algum
arquivo do blog foi alterado, além de enviar um e-mail quando algum plugin está
com atualização pendente, ou há alguma tentativa de acesso a seu blog por
pessoas não autorizadas.<br> O plug-in varre o conteúdo do WordPress, além dos
temas e demais plugins, em busca de alguma adulteração ou bug, ajudando a manter
o WordPress livre de ameaças.
1.  [AntiVirus](https://wordpress.org/plugins/antivirus/): o plugin procura por
injeções maliciosas e possíveis ataques ao seu site ou blog, assim como procura
por *worms* e *malwares*.

Estes pugins **prometem resolver a maioria dos problemas de segurança que
temos** com o Wordpress.

## Bancos de dados de Dorks

São sites em que podemos encontrar uma variedade de **Dorks** para explorar
vulnerabilidades dos nossos sites e ver como pessoas **maliciosas** agem na
**prática**.

### Exploit-db

O **Exploit-db** creio eu que seja o site referência entre os hackers **do mundo
todo**, além disso ele tem uma área dedicada somente ao **Google Hacking** com
milhares de **Dorks** para explorarmos:

[https://www.exploit-db.com/google-hacking-database](https://www.exploit-db.com/google-hacking-database/)

### InurlBR

Outro site muito legal (**e nacional**) com um banco de dados gigante de **Dorks
**é o **InurlBR**, lá tembém podemos encontrar ferramentas desenvolvidas por
eles em php para busca de **Dorks** automatizadas, vale a pena dar uma olhada:

Imaginamos que o cara que quer **fazer merda na internet** tem bastante tempo
pra gastar com isso, então temos que pensar a frente e tapar todos os buracos
para não cair na de **programadores pilantras e maliciosos**.

Espero que tenham curtido o artigo e **que eu possa ter ajudado** de alguma
forma, feedbacks positivos são sempre bem vindos! Abraços até o próximo post.

* [Google Hacking](https://medium.com/tag/google-hacking?source=post)
* [Hacking](https://medium.com/tag/hacking?source=post)
* [Segurança](https://medium.com/tag/seguranÃ§a?source=post)
* [Segurança Da Informação](https://medium.com/tag/seguranÃ§a-da-informaÃ§Ã£o?source=post)

---

Este artigo foi escrito e publicado primeiramente no [Canal do Tableless lá no Medium](https://medium.com/tableless)! 
