**Guia de DAO (Java)**

- Definição do padrão DAO
O padrão DAO é definido no livro "Core J2EE Patterns" como: "o padrão utilizado para abstrair e encapsular todos os acessos ao data source.
O DAO gerencia a conexão com o data source para obter e armazenar informações."
Ele surgiu com a necessidade de separar a lógica de negócios da lógica de persistência de dados.
Este padrão permite mudar a forma de persistência sem que isso influencie em nada na lógica de negócio, além de tornar classes mais legíveis.
O DAO funciona como se fosse um garçom, você pede o prato (dados) e ele resolve buscar na cozinha (banco), sem que você precise saber se o
fogão é a gás ou elétrico.

- Ciclo de vida da conexão JDBC


- Práticas de segurança (SQL injection, prepared statements)


- Checklist de qualidade (fechamento de recursos, exceções)


- Fontes utilizadas:
