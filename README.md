**Guia de DAO (Java)**

- #**Definição do padrão DAO**#

 
 O padrão DAO é definido no livro "Core J2EE Patterns" como: "o padrão utilizado para abstrair e encapsular todos os acessos ao data source.
O DAO gerencia a conexão com o data source para obter e armazenar informações."
Ele surgiu com a necessidade de separar a lógica de negócios da lógica de persistência de dados.
Este padrão permite mudar a forma de persistência sem que isso influencie em nada na lógica de negócio, além de tornar classes mais legíveis.
O DAO funciona como se fosse um garçom, você pede o prato (dados) e ele resolve buscar na cozinha (banco), sem que você precise saber se o
fogão é a gás ou elétrico.

- **Ciclo de vida da conexão JDBC**

Primeiramente, que é JDBC?
JDBC é uma API fornecida pela Oracle que facilita a interação entre aplicações Java e bancos de dados. 
A API JDBC oferece uma série de classes e interfaces para conectar-se a um banco de dados, executar comandos SQL e processar os resultados. Com o JDBC, os desenvolvedores podem realizar operações de banco de dados diretamente de suas aplicações Java.

Seu ciclo de vida dividido em etapas é basicamente assim:
- A criação: a aplicação solicita uma conexão, o driver JDBC do banco é usado pra estabelecer a ponte, e aí o banco de dados faz a validação.
- O Uso: A conexão cria statements, comandos SQL são enviados, transações são iniciadas, commits e rollbacks são realizados, com o banco de dados fazendo todo o processamento
- Fechamento: A aplicação chama o método de fechá-la, mas não a exclui completamente, (em ambientes corporativos, entrando em uma "free pool" para ser reutilizada)
- Destruição: Se o pool de conexões for encerrado ou a aplicação finalizada, a conexão física com o banco de dados é fechada definitivamente




- **Práticas de segurança (SQL injection, prepared statements)**

  
Praticas de segurança são muito importantes de serem utilizadas, para se prevenir e proteger o sistema de qualquer intenção maliciosa como o sql injection.


Defesas principais:


Consultas parametrizadas:
binding de variáveis também chamadas consultas parametrizadas elas forçam o desenvolvedor a definir todo o código SQL primeiro e passar cada parâmetro para a consulta depois.
Se consultas de banco de dados usarem esse estilo de codificação, o banco de dados sempre distinguirá entre código e dados.

Uso de prepared statements:
  Em vez de montar a query juntando string você usa placeholders ? ou :nome e depois passa os valores.
  Onde ele compila a query sem os dados e depois recebe os valores separados.

exemplo de código:

$stmt = $pdo->prepare("SELECT * FROM usuarios WHERE email = ?");
$stmt->execute([$email]);

Validação de entrada:
 E um processo que verifica os dados que e enviado pelo usuário antes de usar.
 E feito definindo regras como tipo de dado, formato esperado

exemplo de código:

if (!$email) { 
    echo "Email inválido";
}
verifica se o email e correto


- **Checklist de qualidade (fechamento de recursos, exceções)**


É uma forma de garantir que o sistema esta seguro, e rodando sem problemas a longo prazo.
Ajuda a deixar o código mais organizado e seguro como exemplo:
Abrir conexões apenas quando e nessecesario
Capturar exceções especificas (SQLException)
Validar dados antes de enviar ao banco.



- **Fontes utilizadas:**
- https://dev.mysql.com/doc/
- https://www.postgresql.org/docs/
- https://www.devmedia.com.br/implementando-o-data-access-object-no-java-ee/33339
- https://www.devmedia.com.br/dao-pattern-persistencia-de-dados-utilizando-o-padrao-dao/30999
- https://www.dio.me/articles/jdbc-java-database-connectivity-uma-visao-geral-57b6b447ec8d
