# banco_de_dados_senac.

<img width="395" height="421" alt="Captura de tela 2025-11-13 193121" src="https://github.com/user-attachments/assets/c8a2f7e1-1abc-4ed3-b397-816907861895" />


CREATE TABLE Clientes 
( 
 cliente_id INT PRIMARY KEY,  
 nome INT NOT NULL,  
 email INT NOT NULL,  
 telefone VARCHAR NOT NULL,  
 idClientes INT,  
); 

CREATE TABLE Produtos 
( 
 produto_id INT PRIMARY KEY,  
 nome VARCHAR NOT NULL,  
 preco FLOAT,  
 categoria VARCHAR NOT NULL,  
 idClientes INT,  
); 

CREATE TABLE Pedidos 
( 
 pedido_id INT PRIMARY KEY,  
 cliente_id INT PRIMARY KEY,  
 data_pedido DATE NOT NULL,  
 valor_total FLOAT NOT NULL,  
 idClientes INT,  
 idProdutos INT,  
); 

CREATE TABLE Itens_Pedido 
( 
 item_id INT PRIMARY KEY,  
 pedido_id INT,  
 produto_id INT,  
 quantidade INT NOT NULL,  
 subtotal FLOAT NOT NULL,  
 idProdutos INT,  
 idPedidos INT,  
); 

ALTER TABLE Clientes ADD FOREIGN KEY(idClientes) REFERENCES Clientes (idClientes)
ALTER TABLE Produtos ADD FOREIGN KEY(idClientes) REFERENCES Clientes (idClientes)
ALTER TABLE Pedidos ADD FOREIGN KEY(idClientes) REFERENCES Clientes (idClientes)
ALTER TABLE Pedidos ADD FOREIGN KEY(idProdutos) REFERENCES Produtos (idProdutos)
ALTER TABLE Itens_Pedido ADD FOREIGN KEY(pedido_id) REFERENCES Itens_Pedido (pedido_id)
ALTER TABLE Itens_Pedido ADD FOREIGN KEY(produto_id) REFERENCES Itens_Pedido (produto_id)
ALTER TABLE Itens_Pedido ADD FOREIGN KEY(idProdutos) REFERENCES Produtos (idProdutos)
ALTER TABLE Itens_Pedido ADD FOREIGN KEY(idPedidos) REFERENCES Pedidos (idPedidos)

1. O que é DDL?
DDL (Data Definition Language) é o conjunto de comandos usados para definir a estrutura do banco de dados, como criar, alterar ou excluir tabelas e colunas.
Esses comandos não manipulam dados diretamente, apenas a estrutura que os armazena.

Principais comandos DDL:
ComandoFunçãoExemploCREATECria bancos de dados ou tabelasCREATE TABLE Produtos (...);ALTERAltera a estrutura de uma tabela existenteALTER TABLE Produtos ADD estoque INT;DROPRemove completamente um banco de dados ou tabelaDROP TABLE Clientes;

Exemplo DDL do nosso projeto

CREATE DATABASE CafeDoCodigo;
USE CafeDoCodigo;

Criando a Tabela de Clientes
CREATE TABLE Clientes (
   
    cliente_id INT PRIMARY KEY AUTO_INCREMENT,
    nome VARCHAR(100) NOT NULL,
    email VARCHAR(100),
    telefone VARCHAR(20)
);

CREATE TABLE Produtos (
    produto_id INT PRIMARY KEY AUTO_INCREMENT,
    nome VARCHAR(100) NOT NULL,
    preco DECIMAL(10,2) NOT NULL,
    categoria VARCHAR(50)
);

2. O que é DML?
DML (Data Manipulation Language) é o conjunto de comandos usados para inserir, atualizar, consultar e excluir dados dentro das tabelas criadas.
Enquanto o DDL cria as tabelas, o DML trabalha com os registros (linhas) dentro delas.

Principais comandos DML:
ComandoFunçãoExemploINSERTInsere novos dados em uma tabelaINSERT INTO Clientes (nome, email) VALUES ('Maria', 'maria@email.com');UPDATEAtualiza dados existentesUPDATE Produtos SET preco = 9.00 WHERE nome = 'Cappuccino';DELETEExclui dadosDELETE FROM Clientes WHERE cliente_id = 3;SELECTConsulta dadosSELECT * FROM Produtos;

Exemplo DML do nosso projeto

INSERT INTO Clientes (nome, email, telefone)
VALUES 
('Maria Silva', 'maria@email.com', '1199999999'),
('João Souza', 'joao@email.com', '1188888888');

UPDATE Produtos
SET preco = 7.50
WHERE nome = 'Café Expresso';

SELECT nome, preco FROM Produtos WHERE categoria = 'Bebida';

DELETE FROM Clientes WHERE cliente_id = 2;

Esses comandos manipulam os dados dentro das tabelas, permitindo visualizar, atualizar ou remover informações conforme a necessidade do negócio.

3. Organização do Repositório
Para manter o projeto organizado, é importante seguir uma estrutura de pastas clara.
Estrutura sugerida:
Projeto-BancoDeDados
README.md            → Este arquivo explicativo (conteúdo educacional)
sql_scripts          → Pasta com o script SQL
cafedocodigo.sql   → Script completo do banco de dados
imagens (opcional)   → Prints ou diagramas do banco

4. Conclusão

Criar a estrutura do banco de dados (DDL)
Manipular os dados armazenados (DML)
Organizar seus arquivos em um repositório profissional e bem estruturado
Assim, você está pronto para construir bancos de dados mais complexos e manter seus projetos documentados e compreensíveis para qualquer colaborador.
Se quiser, posso montar um modelo de README formatado em Markdown (pronto para subir ao GitHub) com o conteúdo acima — quer que eu gere essa versão?
