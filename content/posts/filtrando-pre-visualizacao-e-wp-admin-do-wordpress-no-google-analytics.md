---
title: Filtrando pré-visualização e wp-admin do Wordpress no Google Analytics
authors: Henrique Marques Fernandes
type: post
image: https://marquesfernandes.com/wp-content/uploads/2019/12/Check-Out-the-Advanced-Features-of-New-Google-Analytics-Home-Screen.png
date: 2019-12-09
excerpt: É muito fácil sujar a coleta de dados do Google Analytics no seu site em Wordpress ao acessar seu painel administrativo e ao escrever e pré-visualizar suas páginas e artigos.
categories:
  - Wordpress
tags:
  - wordpress
  - google analytics
---
Se você administra um blog ou um site em WordPress, provavelmente utiliza o Google Analytics para monitorar seu trafego. Em sites novos, que ainda estão começando a ganhar trafego, é muito fácil sujar a coleta de dados com acessos “falsos” ao acessar seu painel administrativo (o famoso /wp-admin) e ao escrever e pré-visualizar suas páginas e artigos (preview=true). Se você, como eu, gosta de pré-visualizar e ver como seus artigos vão se encaixar e se comportar com o seu tema, precisamos filtrar esses acessos para gerar dados reais e limpos para futuras análises.

## Filtrando as páginas de pré-visualização

Antes de criar qualquer filtro, devemos criar uma nova **Visualização** na propriedade. Isso gera um backup dos dados para criar e testar os filtros; Se algo der errado e sujarmos seus dados, temos ainda os dados originais e brutos da propriedade. Para criar uma nova visualização:

1. Entre no [Google Analytics](http://analytics.google.com/) e clique em **Administrador**.
2. Verifique se no drop-down superior esquerdo está selecionado a conta e a propriedade correta.
3. Na aba de **visita** clique em **Criar visita**. De um nome descritivo, como “_Teste de filtros_“.

![Criar nova Vista na Propriedade](https://marquesfernandes.com/wp-content/uploads/2019/12/image-15-1024x496.png)<figcaption>Criar nova Vista na Propriedade</figcaption>

Uma vez criado, retorne para a página de Administrador e verifique se a **Visita** recém criada está selecionada. Agora vamos criar dois filtros para remover as páginas de pré-visualização e wp-admin:

1. Clique em **Filtros** na aba de **Visita** e clique no botão **+Adicionar filtro**.
2. Coloque um nome significativo, como “_Excluir páginas de pré-visualização_“.

![Criar novo filtro](https://marquesfernandes.com/wp-content/uploads/2019/12/image-17-1024x496.png)<figcaption>Criar novo filtro</figcaption>

3. Em **Tipo de Filtro** selecione **Customizado**.
4. Selecione a opção **Excluir**.
5. Em **Campo de filtro** selecione **URI da solicitação**.
6. Em **Padrão de filtro** digite, _preview=true.  
(Esse texto está presente em todas as páginas de pré-visualização, incluindo nas [pré-visualizações públicas](https://marquesfernandes.com/2019/12/04/como-permitir-a-pre-visualizacao-publica-em-artigos-nao-publicados-no-wordpress), se habilitado)._  

![Excluir páginas de pré-visualização (preview)](https://marquesfernandes.com/wp-content/uploads/2019/12/image-18-1024x496.png)<figcaption>Excluir páginas de pré-visualização (preview)</figcaption>

7. Clique em  **Salvar**.

## Filtrando as páginas do painel administrativo (/wp-admin)

Para filtrar as páginas do painel administrativo, seguiremos quase todos os mesmos passos anteriores exceto a definição do filtro.

1. Crie um novo filtro clicando no botão **+Adicionar filtro** (Na mesma propriedade de vista).
2. Coloque um nome significativo como “Excluir páginas administrativas”.
3. Em **Tipo de Filtro** selecione **Padrão**.
4. Selecione a opção **Excluir** , **tráfego para subdiretórios** e **que contém**.
5. Em **Subdiretório** digite, _/wp-admin/_  
(Esse caminho está presente em todas as páginas do painel administrativo).

![Excluir páginas administrativas (/wp-admin/)](https://marquesfernandes.com/wp-content/uploads/2019/12/image-19-1024x496.png)<figcaption>Excluir páginas administrativas (/wp-admin/)</figcaption>

Pronto, agora os dados da sua nova **Vista** criada deverão estar limpos de acessos e visualizações de páginas falsas.

O post [Filtrando pré-visualização e wp-admin do WordPress no Google Analytics](https://marquesfernandes.com/2019/12/09/filtrando-pre-visualizacao-e-wp-admin-do-wordpress-no-google-analytics) apareceu primeiro em [Henrique Marques Fernandes](https://marquesfernandes.com).

---
## Sobre o autor
**[Henrique Marques Fernandes](https://marquesfernandes.com)**

Um nerd nada tradicional… Desenvolvedor web full-stack, escritor amador e inventor nas horas vagas. Apaixonado por tecnologia e entusiasmado por projetos de código aberto!
