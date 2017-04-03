---
title: JPA Hibernate – Como funciona a anotação @version?
author: Mateus Malaquias
type: post
date: 2016-06-19
url: /hibernate-como-funciona-anotacao-version/
categories:
  - Back-end
  - Código
  - Java
tags:
  - back-end
  - hibernate
  - java
  - JPA
  - version

---
Recentemente um colega de trabalho me perguntou qual era função da anotação **@version** presente nas entidades aqui do projeto. Achei interessante essa pergunta e resolvi fazer da resposta o meu primeiro post no blog.

Para responder essa de pergunta temos que lembrar que todo banco de dados possui um controle de concorrência entre transações (se necessário solicitem nos comentários que faço um post explicando a fundo sobre isso). Para esse post só precisamos conhecer o método de controle _Optimistic concurrency control_ (controle de concorrência otimista).

**_Optimistic concurrency control_ (OCC)**

_Optimistic concurrency control _ou controle de concorrência otimista é um método aplicado nas transações de bancos de dados relacionais. Nesse método se acredita que a probabilidade de que duas transações utilizarem o mesmo objeto é minima, logo nada é verificado enquanto a transação está sendo executada e isso faz com que o custo dela diminua.

Normalmente essa técnica funciona bem em Frameworks ORM porque eles conseguem escalonar as transações para que ocorra pouca ou nenhuma interferência. Mas no caso de ocorrer uma interferência o que acontece? Simples, alguma transação escolhida pelo Hibernate vai ser abortada e terá que ser recomeçada pelo cliente.

**A anotação @version**

Agora que sabemos superficialmente o que é um controle de concorrência e o método **OCC **fica mais fácil compreender a importância do **@version** em nossas entidades. Tenha em mente que ao adicionar um atributo com essa anotação não precisamos nos preocupar em alterar seu valor porque o Hibernate fica encarregado dessa função.

Para usarmos o método de concorrência otimista só precisamos declarar um atributo com o nome **version** em nossa entidade. Normalmente ele é do tipo numérico e também pode ser do tipo data, mas não recomendo essa pratica e vou explicar o motivo no final deste post, abaixo temos um exemplo da classe Consulta.

<pre class="lang-java">@Entity
@Table(name = "CONSULTAS", schema = "tableless")
public class Consultas{
@Id
@GeneratedValue(strategy = GenerationType.AUTO)
@Column(name = "ID_CONSULTA")
private Integer numero;

@Temporal(TemporalType.TIMESTAMP)
@Column(name = "DATA_CONSULTA")
private Date dataConsulta;

@ManyToOne(fetch = FetchType.LAZY)
@JoinColumn(name = "PACIENTE_CODIGO")
private Pacientes paciente;

@Version
private Integer version;

//getter e setter
}
</pre>

Com esse mapeamento o Hibernate vai usar automaticamente o número da versão para verificar se o objeto utilizado na transição foi atualizado desde a ultima vez em que ele foi requisitado. Pelo código SQL a baixo podemos ver a presença do atributo version tanto no trecho do SET como na cláusula WHERE isso acontece porque o Hibernate vai buscar o objeto no banco de dados usando também o número da versão e vai incrementar esse número ao mesmo tempo.

<pre class="lang-sql">UPDATE CONSULTAS 
SET DATA_CONSULTA = ?, PACIENTE_CODIGO = ?, version = ?
WHERE ID_CONSULTA = ? 
AND version = ?</pre>

**@version com Data**

Usar um tipo data no atributo version é uma prática que não recomendo porque no banco de dados a coluna será do tipo **TIMESTAMP **e isso pode acabar permitindo que duas ou mais transações possam ser executadas com o mesmo objeto ao mesmo tempo dependendo da precisão do fuso horário configurada no banco de dados, c<span style="line-height: 1.5">aso essa situação acabe acontecendo vamos acabar tendo uma violação de normalização. Algumas pessoas preferem utilizar o tipo data para conseguirem visualizar &#8220;quando&#8221; aquele objeto foi alterado pela ultima vez, caso essa seja sua necessidade recomendo que crie um novo atributo em sua classe ao invés de utilizar a anotação <strong>@version</strong> como data.</p> 

<p>
  Por fim espero que esse post te ajude a trabalhar com controle de concorrência no Hibernate. Dúvidas, sugestões, correções, elogios nos comentários ou no meu twitter. Xablau!
</p>