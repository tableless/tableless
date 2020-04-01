---
title: 'Quando usar TypeScript'
authors: Gabriel Marinho
type: post
date: 2020-04-01
publishDate: 2020-04-01
image: https://i.imgur.com/6dzal8K.jpg
excerpt: 'Aperfeiçoado e amadurecendo: quando usar TypeScript?'
categories:
  - JavaScript
  - Front-end
  - Tecnologia e Tendências
tags:
  - TypeScript
  - Tendências
---

Se você vem acompanhando as últimas tendências do mercado de desenvolvimento web, muito provavelmente você ouviu falar sobre o TypeScript, um superset do JavaScript. Em outras palavras, ele seria a implementação de uma melhoria específica, como foi o C++ para o C, J++ e Kotlin para o Java.

Propósito inicial do projeto
----------
Basicamente, a ideia de criar um superset do JavaScript veio pela falta de informações nos erros onde a passagem de parâmetros em determinadas funções era feita. Isso trazia alguns problemas com back-ends tipados (ASP.NET, por exemplo).

Algumas notícias apontam que o problema surgiu no time de desenvolvimento do Bing Maps e Office 365 da Microsoft. Então o projeto saiu do papel, criou-se um time e é o que é hoje.

> Adoro trabalhar com pessoas inteligentes e ser desafiado. Eu também gosto de trabalhar em coisas relevantes. Essa é a minha injeção de adrenalina. — Anders Hejlsberg, desenvolvedor core do TypeScript

Com TypeScript você pode criar funções tipadas e bem modeladas. Exemplo:
```javascript
// Passa dois parâmetros (a e b) como números, e retorna um número
function soma(a: number, b: number): number { 
	return a + b;
}
```
Agora vamos errar propositalmente. Caso você tente fazer algo do tipo:
```javascript
// ERRADO: Passa dois parâmetros (a e b) como números, e retorna uma string
function soma(a: number, b: number): string {
  return a + b;
}
```
Seu código não rodará porque você declarou o retorno da sua função como ***string***, logo, nenhum outro tipo será aceito. Com isso, você garante a exatidão da tipagem nos dados que estão trafegando no seu software.

Desse modo, você deve ter percebido que para aplicações onde o erro NÃO PODE acontecer em hipótese alguma, o TypeScript é uma ótima opção. Isso é, aplicações grandes e complexas como:
- sistema de saúde
- sistema bancário
- sistema de pagamento
- entre outros

Por padrão, o Angular (framework web da Google para criação de SPAs) utiliza o TypeScript no desenvolvimento das aplicações, fazendo com que a comunidade impulsionasse mais ainda a linguagem.

Quando NÃO usar TypeScript
----------
Em alguns casos, é inevitável, não tem como aplicar determinada tecnologia. Se você, seu time ou sua empresa preza por alguns dos tópicos abaixo, não faz tanto sentido você desenvolver com TypeScript:
- agilidade no desenvolvimento
- documentação de frameworks e módulos do JavaScript para TypeScript
- dinamicidade

### Mais sobre o assunto:

* [Diga olá ao TypeScript e adeus ao JavaScript](https://tableless.com.br/diga-ola-ao-typescript-e-adeus-ao-javascript/) 
* [Gerenciado módulos no TypeScript](https://tableless.com.br/gerenciando-modulos-no-typescript/)
