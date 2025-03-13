CREATE DATABASE BDLOJA2;

USE BDLOJA2;

CREATE TABLE PRODUTO (
ID INT PRIMARY KEY AUTO_INCREMENT NOT NULL,
nome VARCHAR(50) NOT NULL,
preco DOUBLE NOT NULL,
estoque INT NOT NULL);

CREATE TABLE CLIENTE (
ID INT PRIMARY KEY AUTO_INCREMENT NOT NULL,
nome VARCHAR(50) NOT NULL,
email VARCHAR(50) NOT NULL UNIQUE,
telefone VARCHAR(20) NOT NULL);

CREATE TABLE VENDA (
ID INT PRIMARY KEY AUTO_INCREMENT NOT NULL,
cliente_id INT NOT NULL,
produto_id INT NOT NULL,
quantidade INT NOT NULL,
data_venda DATE NOT NULL,
FOREIGN KEY(cliente_id) REFERENCES CLIENTE(ID),
FOREIGN KEY (produto_id) REFERENCES PRODUTO(ID));

INSERT INTO PRODUTO (nome, preco, estoque) VALUES
('Notebook', 3500.00, 20),
('Smartphone', 1500.00, 50),
('Teclado Mecânico', 250.00, 100),
('Monitor 4K', 2800.00, 30),
('Mouse Gamer', 120.00, 150),
('Cadeira Gamer', 850.00, 25),
('HD Externo 1TB', 400.00, 40),
('Impressora', 600.00, 10),
('Fone de Ouvido', 200.00, 80),
('Pendrive 64GB', 50.00, 120);

INSERT INTO CLIENTE (nome, email, telefone) VALUES
('Ana Silva', 'ana.silva@email.com', '11987654321'),
('Carlos Souza', 'carlos.souza@email.com', '11976543210'),
('Mariana Lima', 'mariana.lima@email.com', '11965432109'),
('João Pedro', 'joao.pedro@email.com', '11954321098'),
('Fernanda Costa', 'fernanda.costa@email.com', '11943210987'),
('Lucas Almeida', 'lucas.almeida@email.com', '11932109876'),
('Rafael Santos', 'rafael.santos@email.com', '11921098765'),
('Juliana Torres', 'juliana.torres@email.com', '11910987654'),
('Bruno Ferreira', 'bruno.ferreira@email.com', '11909876543'),
('Paula Mendes', 'paula.mendes@email.com', '11908765432');

INSERT INTO VENDA (cliente_id, produto_id, quantidade, data_venda) VALUES
(2, 3, 1, '2025-03-12'),
(5, 8, 2, '2025-03-11'),
(1, 6, 4, '2025-03-10'),
(4, 7, 3, '2025-03-09'),
(3, 10, 5, '2025-03-08'),
(7, 2, 1, '2025-03-07'),
(6, 9, 2, '2025-03-06'),
(8, 5, 3, '2025-03-05'),
(9, 4, 4, '2025-03-04'),
(10, 1, 1, '2025-03-03');

SELECT * from PRODUTO 
ORDER BY nome;

SELECT CLIENTE.nome, PRODUTO.nome from CLIENTE
INNER JOIN PRODUTO 
ON CLIENTE.ID = PRODUTO.ID;

SELECT SUM(VENDA.quantidade), SUM(VENDA.quantidade * PRODUTO.preco)
FROM VENDA
INNER JOIN PRODUTO
ON VENDA.produto_id = PRODUTO.ID;

SELECT data_venda FROM VENDA
ORDER BY data_venda DESC;

UPDATE PRODUTO
SET preco = preco + (preco * 0.10)
WHERE ID = 5;

SELECT preco FROM PRODUTO
WHERE ID =5;

UPDATE CLIENTE
SET email = 'nandinhacosta@email.com'
WHERE ID = 5;

SELECT email FROM CLIENTE
WHERE ID =5;

UPDATE PRODUTO
SET estoque = 145
WHERE ID = 5;

SELECT estoque FROM PRODUTO
WHERE ID =5;

UPDATE VENDA
SET data_venda = '2025-02-22'
WHERE ID = 4;

SELECT data_venda FROM VENDA
WHERE ID =4;

DELETE FROM VENDA
WHERE cliente_id = 1;

DELETE FROM CLIENTE
WHERE ID = 1;
