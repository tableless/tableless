---
title: JPA de A à Z – Por que conhecer?
author: Mateus Malaquias
type: post
date: 2016-08-30
url: /jpa-de-z-por-que-conhecer/
titulo_personalizado:
  - 'Por que usar <strong>JPA?</strong>'
categories:
  - Back-end
  - Código
  - Destaques
  - Java
tags:
  - hibernate
  - java
  - JPA

---
Não dá pra negar que o Java é uma linguagem bastante verbosa e quando falávamos em juntar o Java com um banco de dados ai sim dava pra ver o tamanho do problema.
  
Se não tivéssemos cuidado era muito fácil perder o controle da complexidade de nossas entidades e consultas.

Antes de entendermos sobre a  JPA, é necessário entender que costumávamos utilizar em nossos projetos o JDBC (Java Database Connectivity) que é uma API presente no Java desde a versão 1.1 da plataforma. Mesmo sendo uma API bem antiga ela ainda continua sendo atualizada e modificada pela comunidade e pela Oracle.

Resumidamente o JDBC é o antecessor da JPA porque ela era a principal forma de executar nossas querys SQL de select, update, delete, insert e até mesmo executar funções presentes no banco de dados. U<span style="line-height: 1.5">m detalhe interessante sobre o JDBC são seus Drivers de conexão, sendo cada banco de dados é responsável por desenvolver e atualizar o seu Driver. Isso facilitava muito a vida do desenvolvedor porque esses Drivers visam encapsular boa parte do código necessário para se conseguir uma conexão, então era uma preocupação a menos que tínhamos que ter.</span>

Mas nem tudo eram flores quando usávamos o JDBC, porque além de ter que escrever códigos SQL direto no Java, tínhamos também que instanciar uma conexão, buscar a conexão com o banco de dados. Dai era preciso preparar um outro objeto para poder manipular a consulta informando os valores dos parâmetros e só então executávamos a consulta.

Acabávamos tendo um trabalho tedioso só para executar uma consulta, todavia o ciclo não acabava nisso, depois era preciso fazer um casting do retorno da consulta para com objeto que queríamos manipular e como se não fosse suficiente também era necessário lembrar de fechar as conexões com o banco de dados.
  
É preciso entender que estamos falando de muito tempo atrás, um tempo em que as facilidades da JPA ainda não existiam e que muita especificação que existe hoje nasceu das dificuldades do passado.

<pre class="lang-java">public class ProdutoDAO {

    Connection dbConnection;

    public ProdutoDAO(Connection con) {
        this.dbConnection = con;
    }

    public void salva(Produto produto) throws SQLException {
        String sql = "INSERT INTO PRODUTO (NOME, DESCRICAO) VALUES (?,?)";

        try (PreparedStatement prStmt = dbConnection.prepareStatement(sql,
                Statement.RETURN_GENERATED_KEYS)) {

            prStmt.setString(1, produto.getNome());
            prStmt.setString(2, produto.getDescricao());
            prStmt.execute();

            try (ResultSet rs = prStmt.getGeneratedKeys()) {
                if (rs.next()) {
                    int id = rs.getInt(1);
                    produto.setId(id);
                }
            }

        }
    }

    public List lista() throws SQLException {
        List produtos = new ArrayList();

        String sql = "SELECT * FROM PRODUTO";

        try (PreparedStatement prStmt = dbConnection.prepareStatement(sql)) {
            prStmt.execute();

            converterQueryEmProdutos(produtos, prStmt);
        }

        return produtos;
    }

    public List busca(Produto produto) throws SQLException {

        String sql = "SELECT * FROM PRODUTO WHERE DESCRICAO like ?";
        List produtos = new ArrayList();

        try (PreparedStatement prdStmt = dbConnection.prepareStatement(sql)) {
            prdStmt.setString(1, produto.getDescricao);
            prdStmt.execute();

            converterQueryEmProdutos(produtos, prdStmt);
        }

        return produtos;
    }

    private void converterQueryEmProdutos(List produtos, PreparedStatement prdStmt) throws SQLException {

        try (ResultSet rs = prdStmt.getResultSet()) {
            while (rs.next()) {
                int id = rs.getInt(1);
                String nomeProduto = rs.getString("nome");
                String descricaoProduto = rs.getString("descricao");
                Produto produto = new Produto(nomeProduto, descricaoProduto);
                produto.setId(id);
                produtos.add(produto);
            }
        }
    }
}
</pre>

Olhando pra esse código podemos passar um baita sufoco se por acaso algum dia o analista de requisitos resolva mexer nos atributos da entidadeProduto. Nessa DAO de exemplo só foi criada poucas consultas, mas vamos usar nossa criatividade e imaginar que na verdade existem 10 e o analista resolveu mudar o nome da coluna &#8220;DESCRICAO&#8221; para &#8220;TIPO_PRODUTO&#8221;, uma pequena mudança de nomenclatura já é suficiente para que perdêssemos tempo refatorando boa parte de nosso código.

Foi para evitar todo esse trabalho que surgiu o conceito ORM (Object Relational Mapping) que traduzindo livremente de acordo com a minha vontade quer dizer: “Estou salvando a sua alma transformando os dados de um banco de dados que estão no paradigma relacional para o paradigma orientado a objetos que você tanto precisa”.

Junto com a ORM também surgiu o Hibernate que é o framework JPA mais famoso e utilizado no momento. Só por curiosidade saiba que a JPA surgiu por causa dele, viram que a ideia era tão boa que resolveram transformar a implementação do Hibernate em uma especificação e até hoje muita coisa que é implementada no framework posteriormente vira especificação na JPA.

**Mas o que é JPA?**

JPA significa Java Persistence API e como já falei ela é uma especificação que nasceu de uma JSR (Java Specification Requests) que basicamente são pedidos para mudanças na linguagem, entenda a JPA como um contrato, normas, regras ou interface e que todos os Frameworks Java que trabalham com persistência de dados devem implementa-la. Além do Hibernate também temos outros Framworks como por exemplo o OpenJPA, o Batoo e o EclipseLink.

Então basicamente a JPA é uma especificação que regulamenta ferramentas muito poderosas que utilizamos no nosso dia a dia para automatizar e economizar tempo de desenvolvimento. Essa especificação nos ajuda em todos os processos quando precisamos trabalhar com um banco de dados, sendo assim podemos usa-la para executar consultas, inserts, updates e deletes.

Lembra daquele código verboso? Como sera que ele ficaria se fosse escrito utilizando a JPA?

<pre class="lang-java">public Produto obterPorId(Produto produto) {
        return manager.find(Produto.class, produto.getId());
    }

    @SuppressWarnings("unchecked")
    public List obterTodos() {
        return manager.createQuery("SELCT p FROM Produto p").getResultList();
    }
</pre>

Repare que no método **obterPorId** não foi necessário criar uma única query SQL para executar a consulta por ID, também não foi preciso fazer nenhum casting a JPA se encarregou de fazer tudo isso pra gente. Agora olhando o método **obterTodos **temos uma String que se parece muito com uma query SQL só que não é, a essa String damos o nome de JPQL (Java Persistence Query Language) e vamos conhecer mais sobre ela em outro momento.

Por fim espero que você nos acompanhe nos próximos posts porque vamos aprender mais sobre essa ferramenta poderosa em conjunto com boas práticas. A ideia é de que os posts não sejam muito longos e também não sejam só tutorias de JPA, aqui iremos explorar os conceitos, apresentar exemplos e colocar minha experiência em ação com as boas práticas.