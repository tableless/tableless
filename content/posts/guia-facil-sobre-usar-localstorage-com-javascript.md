+++
authors = "Alice Graça"
canonical = ""
categories = ["front-end", "Técnicas e Práticas", "javascript"]
date = "2019-06-06T03:00:00+00:00"
excerpt = "Entendendo um pouco sobre como utilizar localStorage com Javascript"
image = "https://i.imgur.com/UiDDUAF.jpg"
publishdate = "2019-06-10T03:00:00+00:00"
sponsor = "organizze"
tags = ["javascript", "localstorage"]
title = "Guia fácil para usar localStorage com Javascript"
type = "post"

+++
A API chamada Web Storage provê dois mecanismos básicos para se guardar informações no browser do usuário: sessionStorage e localStorage. O sessionStorage (que não vamos ver nesse artigo), funciona muito parecido com o localStorage, mas com uma diferença: ele mantém o dado gravado apenas até o término da sessão do usuário, ou seja, até o browser do usuário se fechar incluindo reloads da página ou restores. Já o localStorage mantém o dado gravado mesmo se o browser é fechado e reaberto. Isso facilita criar alguns comportamentos de interface durante o uso do usuário. E obviamente, nem preciso dizer, que não serve para gravar dados sensíveis.

A estrutura de storage de dados é bem simples, composta pelo par **chave** e **valor**. Um exemplo:

```javascript
{
  chave: 'valor';
}
```

Para trabalhar com esses dados, você pode fazer basicamente 4 ações, usando 4 métodos:

* **localStorage.setItem()** para criar um novo par de `chave: valor`;
* **localStorage.getItem()** para recuperar o valor do par `chave: valor`;
* **localStorage.removeItem()** para remover um par específico;
* **localStorage.clear()** apaga TODOS os pares gravados pro aquele domínio;

Tem um método chamado `key()`. Mas não vou falar dele aqui para simplificar as explicações.

## Vendo o localStorage no Inspect

Para você ver todos os dados gravados no localStorage do seu browser, basta abrir o inspect, clicar na aba Application, e depois, na sidebar, clicar em Local Storage (caminho usando o Chrome ou browsers que usam motor Chromium):

![](https://i.imgur.com/8hnl6ij.png)

O seu localStorage, quando gravado, ficará aí, dentro do endereço do site que você está trabalhando.

## Gravando um dado: localStorage.setItem()

Esse método te permite gravar os valores dentro do localStorage no browser do usuário.

<script async src="//jsfiddle.net/alicegraca/d8mpL7eq/1/embed/result,js/dark/"></script>

Abra agora o Inspector, vá ate onde os LocalStorages ficam guardados e clique em "http://fiddle.jshell.net". Você verá nosso `nome: 'Jack Sparrow'` guardado.

![](https://imgur.com/LuPwv7X.png)

**Observação**: Note que os valores sempre serão uma string. Logo, os dados que serão gravados ali precisam ser convertidos para strings antes de serem gravados. Para fazer isso, basta usar o método `JSON.stringify()` antes de passar o valor para o `setItem()`.

Agora que gravamos o valor no browser do usuário, agora vamos recuperá-lo usando o método `localStorage.getItem()`.

## Recuperando um dado: localStorage.getItem()

Funcionando de forma bem parecida que o `setItem()`, nós vamos usar o `getItem()` para recuperar o valor de uma chave gravada anteriormente. No nosso caso, vamos usar para para pegar a chave `nome` que gravamos no exemplo do `setItem()`.

![](https://imgur.com/9kdIv8A.gif)

<script async src="//jsfiddle.net/alicegraca/d8mpL7eq/11/embed/result,js/dark/"></script>

Clique no botão GRAVAR e depois no PEGAR. Veja que o no `console.log()`, colocamos o valor que foi gravado anteriormente.

## Removendo um dado: localStorage.removeItem()

Depois de não usarmos mais esses dados, é uma boa prática apagar o locaStorage, evitando assim acumulo desnecessário de dados.

O método `removeItem()` irá apagar a chave que você definir. Se a chave não existir, ele não fará nada.

![](https://i.imgur.com/PTL9pwi.gif)

<script async src="//jsfiddle.net/alicegraca/d8mpL7eq/15/embed/result,js/dark/"></script>

O `removeItem()` remove apenas a chave (ou o objeto) que você pediu. Já o `localStorage.clear()` para apagar TODAS as chaves do seu domínio. Não precisa passar nenhum parâmetro.

## Cuidados, segurança e limitações

Alguns cuidados e limitações ao usar o `localStorage`:

* Não use o localStorage para guardar dados sensíveis;
* Os dados que estão gravados não tem camada nenhuma de proteção de acesso, ou seja, todos os dados gravados ali podem ser acessados por qualquer código da sua página;
* Em qualquer browser, o localStorage é limitado a guardar apenas 5Mb de dados. Muito mais que os 4Kb dos cookies;
* O uso do localStorage é sincrona, ou seja, toda execução só é feita uma depois da outra;
* Você só pode usar strings no localStorage, e isso é um saco, porque limita a gravação de dados mais complexos e se você tentar fazer qualquer conversão se transforma numa gambiarra sem limites;
* Não pode ser usado por web workers. Isso significa que se você quiser fazer aplicações mais complexas, usando processamento em bakcground para melhorar performance, você não poderá usar localStorage porque não está disponível.

Logo, o ideal é você usar o localStorage para situações onde você quer gravar dados que podem ser públicos, não sensíveis, que não serão usados em apps mais complexos, que não sejam maiores do que 5MB e que sejam strings.

Para coisas simples de interface, que não faz muito sentido gravar algo no banco ou em algum lugar mais permanente, é legal usar o localStorage. Se você está criando um SPA ou qualquer site/sistema e quer um pouco de independencia do server, o uso do localStorage é adequado e quebra um galho.

## Mais segurança

Mais uma palavra sobre segurança: qualquer javascript rodando no seu domínio, nas suas páginas, podem acessar os dados que você gravou no localStorage. Bom, você pode pensar: "Mas eu que controle os JS que eu coloco na página" E sim, isso é verdade... Mas se você usa qualquer script, plugin, framework, library e seja lá o que for de terceiros, você corre riscos.

Aposto que você não analisa todos os scripts importados do NPM e lincados na sua página, certo? Aquele `ultimate-slide-v03.min.js` foi analisado minuciosamente por você e pelo time, certo? Bom... você me entendeu.
