---
title: Testes de Invasão e Análise de Vulnerabilidades
author: Marcus Aurelius
type: post
date: 2016-04-26
excerpt: O que são teste de invasão e análises de vulnerabilidades?
url: /testes-de-invasao-e-analise-de-vulnerabilidades/
titulo_personalizado:
  - 'Testes de Invasão e Análise de <strong>Vulnerabilidades</strong>'
categories:
  - Destaques
  - Tecnologia e Tendências

---
## O que é um Teste de Invasão

Teste de invasão ou _pentest_ são métodos que avaliam a segurança de um sistema de computador ou de uma rede, simulando ataques de uma fonte maliciosa. O processo envolve uma análise nas atividades do sistema, que envolvem a busca de alguma vulnerabilidade em potencial que possa ser resultado de uma má configuração do sistema, falhas em hardwares/softwares desconhecidas, deficiência no sistema operacional ou técnicas contramedidas. Todas as análises submetidas pelos testes escolhidos são apresentadas no sistema, junto com uma avaliação do seu impacto e muitas vezes com uma proposta de resolução ou de uma solução técnica.

### Testes de Invasão x Análise de Vulnerabilidades

Diferente de uma avaliação de vulnerabilidades, ao realizar um teste de invasão, os _pentesters_ não só identificam as vulnerabilidades que poderiam ser utilizadas pelos invasores, mas também exploram essas vulnerabilidades, sempre que possível, para avaliar os danos que os invasores poderiam causar após uma exploração bem-sucedida das falhas.

### Como se realiza um Pentest?

Um _pentest_ é realizado seguindo algumas etapas explicadas abaixo. Porém, antes de iniciar um _pentest_, é necessário que o cliente esteja a par de todo o processo para que não haja nenhuma falha de comunicação entre as partes. É necessário conhecer os objetivos do negócio do cliente no que diz respeito ao teste de invasão: se esse é o primeiro teste de invasão, o que o levou a procurar esse serviço? Quais as exposições que ele mais teme? Existe algum dispositivo frágil com o qual deveremos ter cuidado ao efetuar os testes?

#### 1. Preparação

Nessa fase é necessário decidir o escopo do teste de invasão: quais endereços de IP serão incluídos nos testes e quais não serão, quais tipos de ações o cliente permitirá que sejam realizados durante o teste, permissões para desativar potencialmente determinado serviço, limitar a avaliação a simplesmente uma análise de vulnerabilidades, etc. O cliente pode solicitar que os testes sejam realizados somente em determinados dias e durante horários específicos.

#### 2. Coleta de Informações

Nesta fase será analisada livremente as fontes de informações disponíveis, um processo conhecido como coleta de OSINT (_Open Source Intelligence_, ou inteligência de fonte aberta). Essa pesquisa é realizada através de motores de busca, como o Google, Bing e Yahoo, redes sociais e demais fontes de informações públicas como registro de domínio.

#### 3. Mapeamento de Rede

O DNS (_Domain Name System_, ou sistema de nomes de domínio) é um sistema de gerenciamento de nomes hierárquico e distribuído para computadores, serviços ou qualquer recurso conectado à Internet ou em uma rede privada. Através do DNS é possível descobrir a topologia da rede, endereços de IP e a quantidade de computadores na rede interna.

#### 4. Enumeração de Serviços

Utilizando ferramentas específicas, uma varredura de portas abertas é realizada nas máquinas descobertas e nos IP&#8217;s informados com o fim de descobrir quais sistemas estão presentes na Internet ou na rede interna, bem como quais softwares estão sendo executados.

#### 5. Análise de Vulnerabilidades

Tendo conhecimento das portas, softwares instalados e sistemas ativos, é iniciado o processo de análise de vulnerabilidades utilizando _scanners_ e banco de dados de vulnerabilidades no auxílio em detectar falhas nos ativos do cliente que possam a vir, através da execução de _exploits_ (códigos específicos para exploração de falhas), permitir o acesso à rede e computadores.

#### 6. Exploração de Falhas

Esta é a fase onde executamos os _exploits_ nas vulnerabilidades detectadas na fase anterior, como por exemplo: acessar remotamente uma máquina sem a necessidade de autenticação através de login e senha ou por meio de tentativas de autenticação com senhas padrão em determinados sistemas.

#### 7. Pós-Exploração de Falhas

Nesta fase são reunidas informações sobre o sistema invadido, busca por arquivos relevantes ao teste de invasão, a criação de _backdoors_ para posteriores acessos ao sistema, ampliar a exploração da rede ganhando assim acesso à demais máquinas/sistemas que não estavam visíveis na tentativa inicial de escaneamento da rede.

#### 8. Relatório

Ao final de todas as etapas de um _pentest_ é gerado um relatório contendo todo o descritivo do teste realizado de forma clara, transparente e objetiva. Neste relatório será apontado o que o cliente está fazendo corretamente, quais pontos ele deverá melhorar sua postura quanto à segurança da informação, como foi possível realizar a invasão, quais os resultados das descobertas durante a invasão, como corrigir esses problemas, etc.