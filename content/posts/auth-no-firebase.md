---
title: Como usar auth no Firebase
authors: Morais Junior
type: post
image: https://firebase.google.com/images/social.png
date: 2018-04-21
excerpt: Autenticação de usuário com o Firebase Auth
categories:
  - Artigos
  - Javascript
  - Tecnologia e Tendências
tags:
  - FireBase
  - Auth
  - HTML
---

Quem já trabalha com [Firebase](https://firebase.google.com/ "Firebase") provavelmente está vivendo um sonho, afinal, temos uma infraestrutura que lhe entrega de forma fácil todos os serviços necessários para rodar uma aplicação web em produção. Para quem ainda não o conhece, irei descrever em uma pequena série de artigos algumas de suas funcionalidades. 

O ponto de partida de quase toda aplicação é a autenticação. Dentro do Firebase, temos este recurso na aba Authentication. Lá é possível fazer todos os controles de forma simples e intuitiva por isso não entrarei em detalhes sobre a área administrativa e irei direto aos códigos.

Tendo como ponto de partida que você já conhece o Firebase e entende um pouco de JavaScript, tudo começa por declará-lo na tag <head> ou<footer>da aplicação:

```html
<script src="https://www.gstatic.com/firebasejs/4.6.1/firebase.js"></script>
```

Após essa declaração, basta iniciarmos a aplicação com as chaves geradas no Firebase. Isso é super simples e bem documentado por isso não entrarei em detalhes:

Pronto, agora você já tem o Firebase na sua aplicação ;)

> Para melhorar o entendimento deixei todos os códigos prontos em funcionamento aqui: https://jsfiddle.net/tm0jx4hp/28/

Começamos por saber qual o status do auth, se está logado ou não. Para isso, é só incluir o código abaixo no lugar desejado. O evento onAuthStateChanged é disparado sempre que houver uma alteração no status do auth, ele pode estar em qualquer parte do código:
```javascript
firebase.auth().onAuthStateChanged(function(user) {
  if (user) {
    //online
    console.log( user );
  } else {
    //offline
  }
});
```


Como já sabemos o status, agora precisamos fazer o login. Existem várias formas de se fazer isso: pelo Google, Facebook, número do telefone, etc. Neste exemplo utilizaremos e-mail e senha (que é o procedimento mais simples). No local da aplicação responsável pelo login, você irá utilizar o código abaixo (provavelmente no onclick do botão de algum formulário):
<pre class="lang-javascrip">
firebase.auth().signInWithEmailAndPassword('email@dominio.com.br', 'senha')
.catch(function(error) {
  console.error( error );
});
</pre>

Para logout é tão simples quanto:

```javascript
  firebase.auth().signOut()
  .then(function() {
    console.log('Logout');
  }, function(error) {
    console.error( error );
  });
```

Se precisar alterar a senha, temos o método **updatePassword**:

```javascript
firebase.auth().currentUser.updatePassword(pass1)
.then(function() {
	////Senha alterada!
})
.catch(function(error) {
	console.error(error);
});  
```

Para cadastrar um novo usuário:

```javascript
firebase.auth().createUserWithEmailAndPassword('email@email.com.br', "123mudar").catch(function(error) {
  console.error(error);
});
```

Para excluir o usuario logado:

```javascript
var user = firebase.auth().currentUser;

user.delete().then(function() {
  // User deleted.
}).catch(function(error) {
  // An error happened.
});
```

O Firebase foi desenvolvido para ser simples e entregar o máximo possível com o mínimo de código. Neste artigo podemos ver como com poucas linhas conseguimos implementar recursos que em outra estrutura seria bem mais complicado. No próximo artigo veremos outros métodos de auth.  

Mais detalhes na documentação oficial do Firebase:
https://firebase.google.com/docs/auth/web/start?authuser=0

Se tiver alguma dúvida, só deixar aqui nos comentários :)
