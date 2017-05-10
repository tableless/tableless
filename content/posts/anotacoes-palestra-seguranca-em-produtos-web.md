---
title: 'Anotações palestra: Segurança em Aplicações Web'
author: Diego Eis
type: post
date: 2014-05-21
excerpt: Anotações sobre a palestra de segurança que o Nando fez no 16 Encontro Locaweb.
url: /anotacoes-palestra-seguranca-em-produtos-web/
dsq_thread_id: 2702130948
categories:
  - Eventos e Workshops
  - Slides e Apresentações
tags:
  - anotacoes
  - palestras

---
Estas são as minhas anotações da palestra do Nando Vieira no evento 16 Encontro Locaweb de 2014.



  * seu site está seguro? Você se pergunta isso quando coloca seu produto no ar?
  * 75% dos ataques estão na camada da aplicação.
  * brechas de segurança acabam com sua credibilidade.
  * OWASP é uma fundação voltada para distribuir informações sobre segurança em aplicações web. http://owasp.org/
  * o raios teve algo em torno de 8 ou 9 relesses de segurança em 2013. Parece muito mas não é.
  * falha de segurança vai ter em qualquer tipo de linguagem, não importa qual.
  * outras brechas são feitas pelos próprios devs por conta de experiência, pressa, deadline apertado, falta de atenção etc etc.

## configurações

  * nunca armazene configurações no seu repositório
  * use variáveis de ambientes em vez de arquivos de configuração ou copie o arquivo de configuração na hora do deploy
  * para quem usa ruby use dotenv. para PHP use phpdotenv
  * nunca salve arquivos .env no repositório.

## Session Hijacking

  * o protocolo http é stateless
  * uso de cookies para fazer a identificação do usuário
  * um atacante pode roubar o cookie de um usuário
  * tente forçar o uso de ssl em tudo que exige autenticação.
  * expire a sessão em caso de inatividade. Nesse caso seja criterioso, porque você pode afetar o conforto do usuário fazendo-o logar novamente
  * marque os cookies com a opção http only na hora que você definir o cookie

## Session ficariam

  * um atacante se autêntica como outro usuário pra sempre. Isso porque não temos um mecanismo de expirar o login depois de um tempo determinado.
  * toda vez que o usuário se autentica, você não zera a sessão dele, iniciando uma nova sessão
  * no rails existe um método chamado reset_session, que vai zerar cookies e etc do usuário
  * use outro session storage que armazene sessões ativas
  * o github colocou um caixinha de sessions mostrando as informações de usuários ligados na sua conta

## passwords

  * nunca armazene senhas em texto puro no banco. Claro!
  * hashing é um pouco melhor mas não ajuda muito. Se você usa sha1, ele gera uma hash de 40 caracteres, que procurando no Google, você consegue descobre a senha
  * fazer salting é um pouco melhor
  * as senhas baseadas em hash foram feitas para serem rápidos
  * o brute force com sha1 é muito rápido e eficiente
  * use algoritmo blowfish para criptografar senhas, isso dificulta o brute force porque a decodificarão dessa hash é muito lenta

## redirecionamentos

  * processe a url antes de fazer redirecionamentos
  * o referrer pode conter informações confidenciais
  * faça o redirect a partir de uma página específica
  * crie uma página intermediária, como o youtube faz, avisando que o usuário está saindo do seu site

## SQL Injection

  * nesse caso um ataque injeta parâmetros via query.
  * nunca interpole variáveis em query strings.
  * use prepares statements.

## Cross-scripting (XSS)

  * não confie em dados enviados pelos usuários. O usuário pode ser qualquer um.
  * Valide as informações antes de aceitar qualquer dado de usuário.
  * se toda informação enviada pelo é insegura, significa que toda vez que você for mostrar essas informações, você precisa validar antes.
  * escape caracteres como > e &
  * tome cuidado no JavaScript também. Não atribua html ao definir o conteúdo fornecido pelo usuário.
  * no Rails use a biblioteca Sanitize (loofah)
  * se você precisa uma estrutura html, crie uma variável temporária.

## software Update

  * sempre atualize seus software. Atualize seu PHP, seu ruby, rails e qualquer outra linguagem
  * ferramenta metasploit
  * Você não precisa de um super usuário pra fazer deploy
  * use seu servidor usando ssh
  * libere apenas as portas necessárias para rodar seu projeto
  * segurança deve ser uma preocupação constante