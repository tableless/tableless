---
title: Precisamos confirmar a senha?
author: Marcus Himura
type: post
date: 2015-10-02
url: /precisamos-confirmar-senha/
categories:
  - Design
  - UX
tags:
  - arquitetura de informacao
  - design
  - design centrado no usuario
  - ux design

---
Você deve me entender: formulários são muito chatos. Tanto para desenhá-los quanto para produzir código front-end. Mas cada vez que desenho um formulário, eu tento simplificar ao máximo. A inclusão ou a exclusão de um campo pode afetar a taxa de conversão ou causar um desinteresse do usuário ao produto. Mas um dos campos que sempre me deixa com a pulga atrás da orelha é o de “cadastramento de senha”.

O padrão que é utilizado são dois campos: um para digitar e o outro para confirmar a senha. E são nesses dois campos, que há um aumento da taxa de desistência do seu produto.

### O problema

Muitos pensam que devem colocar o segundo campo de confirmação, para evitar o erro de digitação, já que os campos usam uma máscara nos caracteres. E é aí, que mora o problema.

Alguns usuários cometem erros de digitação e não sabe se errou no campo da senha ou no de confirmação. <a href="http://www.formisimo.com/blog/case-study-small-changes-lead-to-a-55-increase-in-conversions/" rel="nofollow">Este estudo</a> constatou que o campo de confirmação foi responsável por mais de um quarto de abandono dos usuários. Feito isso, resolveram fazer outro teste sem o campo de confirmação e perceberam que houve uma diminuição de erros e um aumento na taxa de conversão de conclusão.

### Não basta excluir

Excluir o campo de confirmação não irá resolver o problema por completo. O erro de digitação ainda persiste pelo uso da máscara nos caracteres, o que acaba gerando em problemas como: logar e pedir para redefinir a senha.

### Visão do Superman

Uma boa maneira de resolver esse problema é dar a opção ao usuário de enxergar o que foi digitado.<figure id="f140"> 

<div class="aspectRatioPlaceholder is-locked">
  <div class="aspect-ratio-fill">
  </div>
  
  <p>
    <img src="https://cdn-images-2.medium.com/max/900/1*4iuMApy2iH1g4JIK_D7Yww.png" alt="" /></div> </figure> 
    
    <p>
      Em seu Windows 8, a Microsoft adota o uso do ícone de um olho, para revelar a senha.
    </p><figure id="267c"> 
    
    <div class="aspectRatioPlaceholder is-locked">
      <div class="aspect-ratio-fill">
      </div>
      
      <p>
        <img src="https://cdn-images-2.medium.com/max/720/1*V07wwjNvW_1VoUcJR6ajsw.png" alt="" /></div> 
        
        <div class="aspectRatioPlaceholder is-locked">
        </div></figure> 
        
        <p>
          Uma outra maneira que está sendo adotado pelo o Android é a de revelar a senha usando um <em class="markup--em markup--p-em">check box</em>, acompanhado da frase “exibir senha”.
        </p>
        
        <p>
          <strong class="markup--strong markup--p-strong">E você, concorda com tudo isso? Acha que devemos adotar isso como um padrão para o cadastramento de senhas?</strong>
        </p>