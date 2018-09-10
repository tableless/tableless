---
title: Testando aplicações com Cypress
authors: Tailo Mateus Gonsalves
type: post
image: https://i.imgur.com/3N55xi3.jpg
date: 2018-09-10
excerpt: As suas dores de cabeça acabaram
categories:
  - Front-end
  - Tecnologias e Tendências
tags:
  - testes
  - end-to-end
  - cypress
---

**Testes end-to-end são excelentes pois refletem as ações dos usuários**. Essa
categoria de testes se comportam como um humano real, validando várias partes da
aplicação ao mesmo tempo. O [Cypress](https://www.cypress.io/), é um novo *test
runner* com a premissa de testes rápidos, fáceis e confiáveis para qualquer
coisa que seja executada em um navegador. 

**OBS**: O ideal é sempre fazer um teste falhar, após fazer ele passar e por fim
a refatoração. Mas afim de estudos do *Cypress*, a maioria dos exemplos não
seguiram essa ordem.

### O que vem a seguir

* Instalação do *Cypress*
* Configuração do ambiente de testes
* Fazendo nosso primeiro teste
* Executando nosso primeiro teste
* Verificando um elemento da página
* Testando a responsividade de nossos elementos 
* Como podemos nos aprofundar

### Instalando Cypress

Podemos utilizar o *npm* para instalar, digite no seu terminal:

```
npm install --save-dev cypress
```

Se tudo ocorrer bem, agora podemos escrever nossos primeiros testes.

### Configuração dos testes

Vou utilizar como exemplo [meu site pessoal](https://tailomateus.github.io/).
Por padrão o *Cypress* espera que os testes de integração estejam dentro das
pastas *cypress/integration*, então teremos que criá-las. 

Caso não queira utilizar esse caminho padrão, você pode criar um [arquivo de
configuração](https://docs.cypress.io/guides/references/configuration.html)
*cypress.json* na raiz do seu projeto, com qualquer caminho que desejar.

### Testando o título da página

Nosso primeiro teste é muito simples, apenas testar se o título da página está
funcionando corretamente.

Dentro da pasta *cypress/integration* criei um arquivo chamado *sample-spec.js*

```
describe('Personal website home page', () => {
  it('contains "Tailo Mateus Gonsalves" in the title', () => {
  })
})
```

A *describe* possui dois argumentos, uma string com o assunto e uma *função de
callback* que executa qualquer código, dentro dessa função vamos poder
incluir vários *it* (vários testes). A função *it* também espera dois
parâmetros. O retorno da função deve verificar nossa afirmação do teste contra a
realidade.

Para testar a página inicial teremos que dizer onde ela está. Como todos os
nossos testes serão feitos nessa página, podemos adicionar em um lugar que
sempre é executado antes dos testes:

```
describe('Personal Website home page', () => {
  beforeEach(() => {
    cy.visit('https://tailomateus.github.io/')
  })
  
  it('contains "Tailo Mateus Gonsalves" in the title', () => {
    cy.title().should('contain', 'Tailo Mateus Gonsalves)
  })
})
```

No exemplo acima adicionamos a função
[cy.visit()](https://docs.cypress.io/api/commands/visit.html) no nosso
*beforeEach*, com isso garantimos que antes de executar um teste, o código vai
saber qual é a página que estamos testando. Estamos afirmando que o título da
página contém o nome “Tailo Mateus Gonsalves”, [você pode ver aqui outras
asserções suportadas.](https://docs.cypress.io/guides/references/assertions.html#Chai)

### Rodando nosso primeiro teste

Como o *Cypress* não está instalado globalmente, temos que adicionar o caminho
da pasta *bin*, dentro da nossa pasta *node_modules*. Use esse comando na raiz
do projeto:

```
(npm bin)/cypress open
```

Na minha máquina ficou assim o caminho: 

```
node_modules/cypress/bin/cypress open
```

Se tudo ocorrer bem, essa interface vai abrir:

![](https://cdn-images-1.medium.com/max/800/1*LolhBhXNFHk0ne-Q1qIDRg.png)
<span class="figcaption_hack">Interface Cypress</span>

O arquivo que criamos está disponível para que possamos executar nosso teste.
Temos uma interface, onde conseguimos visualizar como nossa página está se
comportando e os resultados obtidos.

![](https://cdn-images-1.medium.com/max/800/1*xb7WjOdjOUJe43hK3NhRYA.png)
<span class="figcaption_hack">Executando os testes</span>

### Verificando um elemento na página

Agora vamos verificar se um elemento realmente esta presente na página. Neste
teste vamos validar se a imagem do perfil esta visível.

Como estamos testando a mesma página, podemos fazer no mesmo *describe*, apenas
adicionando um novo *it*. 

```
it('has a visible profile picture', () => {
  cy.get('.img_profile').should('be.visible')
})
```

Este teste usa [cy.get()](https://docs.cypress.io/api/commands/get.html#Syntax)
para capturar o elemento. Se o elemento estiver sendo carregado de forma
assíncrona, essa função vai esperar por *defaultCommandTimeout* para aparecer (o
valor padrão é 4 segundos e pode ser configurado em
[cypress.json](https://docs.cypress.io/guides/references/configuration.html#Timeouts)).


Resultado dos nossos testes:

![](https://cdn-images-1.medium.com/max/800/1*yZFX1NmJavGysMbeYntbUQ.png)
<span class="figcaption_hack">Verificando elemento</span>

Mas, se por algum motivo cometermos algum erro no teste, veja como vai ser o
resultado:

![](https://cdn-images-1.medium.com/max/800/1*YvE1hed6KvHJ7TBH1j-JOg.png)
<span class="figcaption_hack">Erro na verificação do elemento</span>

### Testando a responsividade

Vamos fazer um teste um pouco diferente. Atualmente tenho que ter a certeza que
o site vai funcionar em dimensões diferentes. Dessa forma, todos os usuários
consigam usar corretamente.

Como ainda estamos testando a mesma página, apenas acrescentaremos outro
*describe* dentro do existente. Aqui testamos o tamanho de 320px de largura e
verificamos se a imagem de perfil ainda esta visível. Para alterar a largura
para este teste, podemos utilizar
[cy.viewport()](https://docs.cypress.io/api/commands/viewport.html#Syntax).

```
describe('with a 320x568 viewport', () => {
  beforeEach(() => {
    cy.viewport(320, 568);
  })

  it('has a visible mobile profile picture', () => {
    cy.get('.img_profile').should('be.visible')
  })
})
```

Por padrão o tamanho é 1000×660, mas podemos alterar no arquivo de configuração,
*cypress.json* mencionado anteriormente. Você pode testar qualquer dimensão,
veja como ficou nosso teste no mobile:

![](https://cdn-images-1.medium.com/max/800/1*TB71xoVOqBCoE26FHt3Vjg.png)
<span class="figcaption_hack">Testes em mobile</span>

### Quero me aprofundar

[Na própria
documentação](https://docs.cypress.io/api/introduction/api.html#Sections) você
vai encontrar vários exemplos. Porém se quiser algo visível, quando instalar o
*Cypress*, vai ter uma pasta chamada “examples” com mais de 100 testes para
serem executados.

![](https://cdn-images-1.medium.com/max/800/1*L2_GisT-XWYYqRDF8HLquA.png)
<span class="figcaption_hack">Outros tipos de testes</span>

Como você pode ver na imagem, existe vários tipos de funções. Uma coisa legal e
que não foi explorado neste artigo, é como o *Cypress* fica entre as respostas
*ajax* e o *front-end*. Podemos controlar os resultados que recebemos do
servidor.

**A medida que seu projeto vai ganhando novas funcionalidades, as chances de
erros acontecerem aumentam consideravelmente.** E sei bem que você não quer
isso. Então, basta testar e começar implementar em seus projetos.

**Os códigos dos exemplos estão no [GitHub](https://github.com/TailoMateus/testing_personal_site_cypress)**.

### **Créditos e Referências:**

[Documentação
Cypress](https://docs.cypress.io/api/introduction/api.html#Sections)<br> [An
Intro to Web Site Testing with
Cypress](https://css-tricks.com/an-intro-to-web-app-testing-with-cypress-io/)
