---
title: Documentando sua API com Apiary
authors: Breno Panzolini
type: post
date: 2019-02-03
excerpt: Como fazer a documentação da sua API de maneira simples com Apiary + Blueprint.
categories:
  - Tecnologia e Tendências
tags:
  - API
  - Documentação
image: https://pbs.twimg.com/profile_images/689198553751760896/Q84Qf_4w_400x400.png
---

Preciso confessar de que nunca gostei de fazer documentação das APIs que desenvolvia, sempre achei um trabalho "chato" e que não entregava valor nenhum.

Porém, conforme você vai ganhando experiência e trabalhando com times de desenvolvimentos maiores e mais descentralizados, fica nítido de que uma boa documentação é tão fundamental quanto uma boa API. Além disso, se sua API for para uso público ter uma boa documentação não é opção, mas sim uma obrigação.

Nesse post vamos ver como utilizar o **Apiary** e **Blueprint** para escrever a especificação das nossas APIs. Se você está buscando uma forma simples e efetiva de executar essa tarefa, garanto que essa é uma excelente escolha.

# O que é Apiary?

[Apiary](https://apiary.io/) é uma plataforma completa que possibilita o design, prototipação, documentação e testes da sua API.

Com a ferramenta é possível escrever um mock da sua API muito rápido e com isso fazer os testes, pedir opinião, compartilhar com os clientes e colegas que irão consumir seu serviço e com isso a codificação de fato será muito mais assertiva.

Para começar, é necessário [criar um usuário no site](https://login.apiary.io/register), que pode ser feito inclusive através da sua conta do GitHub.

# Escrevendo seu primeiro Endpoint

A primeira coisa que encontramos é o cabeçalho da nossa API.

```
FORMAT: 1A
HOST: http://polls.apiblueprint.org/

# Foo Bar

Exemplo de API utilizando Apiary + Blueprint
```

- A primeira linha indica que estamos utilizando o **[Blueprint](https://apiblueprint.org/)** no nosso Markdown.
- A segunda linha é para conseguirmos testar nossa API diretamente do editor.
- Por final temos o nome e uma descrição da nossa API.

Vamos começar escrevendo nosso primeiro recurso:

```
## Usuários [/usuarios]
```

Para definir uma coleção, utilizamos um `Heading 2 = ##` e ao final entre `[]` definimos o nome do recurso, no nosso exemplo `/usuarios`.

Agora que já temos um recurso definido, podemos começar a documentar as operações HTTP (GET, POST, PUT, DELETE) de maneira simples:

```
### Listar todos os usuários [GET]

+ Response 200 (application/json)

        [
            {
                "id": "abc-123",
                "login: "joao_silva",
                "name": "João da Silva",
                "age": 40,
            }
        ]
```

É importante notar que as operações utilizam a convenção de um `Heading 3 = ###`.

Como estamos definindo as operações abaixo do recurso `## Usuários [/usuarios]` que foi criado anteriormente, precisamos apenas informar o tipo da ação desejada, no exemplo acima um `[GET]`.

Outro ponto que é necessário ter atenção, é na identação do Markdown, pois se ela estiver errada a sua documentação não irá funcionar. Porém, fique tranquilo nesse ponto pois o **Apiary** faz a validação e caso tenha algum erro te informa a linha.

# Melhorando nossa documentação com o MSON

Antes de continuar e mostrar outros exemplos, vamos melhorar a nossa documentação com [MSON](https://github.com/apiaryio/mson).

O **MSON** vêm de *Markdown Syntax for Object Notation*, ele é totalmente compatível com JSON e nos ajuda a evitar a repetição e manter uma documentação bem organizada.

No final do nosso Markdown, vamos adicionar uma seção chamada `# Data Structures` e modificar nosso recurso anterior para utilizar a entidade criada.

```
### Listar todos os usuários [GET]

+ Response 200 (application/json)
    + Attributes
        - data (array[UsuarioInstance])

# Data Structures

## Usuario (object)

- login: "JoseSilva" (string, required)
- name: José da Silva (string, required)
- age: 40 (number)

## UsuarioInstance (Usuario)

- id: "abc123" (string, required)
```

Algumas modificações importantes:

- Definimos a estrutura `Usuario` e `UsuarioInstance` com suas respectivas propriedades.
- A estrutura `UsuarioInstance` herda todas as propriedades de `Usuario` e adicionar o atributo `id`. Essa separação será importante principalmente na hora que criarmos o método `POST`.
- Nosso endpoint foi alterado para conter uma nova lista chamada `attributes` que irá retornar uma propriedade `data` que contém um array de `UsuarioInstance`.

A vantagem de utilizar o **MSON** é que temos objetos reusáveis (isso ficará mais evidente quando formos definir mais endpoints), além de facilitar a manutenção e possíveis modificações futuras na nossa API.

Aconselho fortemente uma lida no [tutorial](https://github.com/apiaryio/mson/blob/master/Tutorial.md) e no [README](https://github.com/apiaryio/mson) do projeto. Existe uma grande quantidade de coisas que podemos declarar para facilitar nossa vida (herença, type definitions, enum, etc).

# Finalizando nosso recurso /usuarios

Vamos escrever mais alguns endpoints para o nosso `/usuario`.

```
### Recuperar um usuário [GET /{id}]

+ Parameters
    + id: "abc123" (string)

+ Response 200 (application/json)
    + Attributes (UsuarioInstance)
    
+ Response 404 (application/json)

        {
            "message": "Usuário não encontrado"
        }
    
### Criar um usuário [POST]

+ Request (application/json)
    + Attributes (Usuario)

+ Response 200 (application/json)
    + Attributes (UsuarioInstance)

### Deletar um usuário [DELETE /{id}]

+ Parameters
    + id (string)

+ Response 204
```

Pontos importantes:

- Incluímos a possibilidade de passar parâmetros nas nossas requisições. Como por exemplo o `GET /{id}]`.
- Criamos uma response de `404 - Not Found` caso determinado usuário não seja encontrado pelo id.
- Temos um endpoint para a criação de um novo usuário. Importante reparar o uso tanto da estrutura `Usuario` no momento do `request`, quanto da estrutura `UsuarioInstance` no momento do `response`.
- Podemos chamar o verbo `DELETE` para remover um usuário, e o response será vazio apenas retornando o status `204`.

# Exemplo completo

```
FORMAT: 1A
HOST: http://polls.apiblueprint.org/

# Foo Bar

Exemplo de API utilizando Apiary + Blueprint

## Usuários [/usuarios]

### Listar todos os usuários [GET]

+ Response 200 (application/json)
    + Attributes
        - data (array[UsuarioInstance])

### Recuperar um usuário [GET /{id}]

+ Parameters
    + id: "abc123" (string)

+ Response 200 (application/json)
    + Attributes (UsuarioInstance)
    
+ Response 404 (application/json)

        {
            "message": "Usuário não encontrado"
        }
    
### Criar um usuário [POST]

+ Request (application/json)
    + Attributes (Usuario)

+ Response 200 (application/json)
    + Attributes (UsuarioInstance)

### Deletar um usuário [DELETE /{id}]

+ Parameters
    + id (string)

+ Response 204

# Data Structures

## Usuario (object)

- login: "JoseSilva" (string, required)
- name: José da Silva (string, required)
- age: 40 (number)

## UsuarioInstance (Usuario)

- id: "abc123" (string, required)
```

# Conclusão

Esse post foi para mostrar uma ferramenta muito útil para a criação da documentação de nossas APIs. Vimos que é simples utilizar o **Blueprint** e que podemos utilizar o **MSON** para deixar as coisas um pouco mais robustas e fáceis de se alterar no futuro.

O **Apiary** nos fornece uma série de outras funcionalidades super úteis que não foram abordadas nesse post.

Aconselho para quem quer se aprofundar no tema que consulte os seguintes materiais de referência:

- [Blueprint](https://apiblueprint.org/)
- [Apiary](https://apiary.io/how-apiary-works)
- [MSON](https://github.com/apiaryio/mson)
