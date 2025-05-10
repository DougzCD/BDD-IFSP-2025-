# BDD-IFSP-2025-

DROP DATABASE venda;

CREATE DATABASE Venda;

USE Venda;

CREATE TABLE produto (
    idProduto INTEGER NOT NULL PRIMARY KEY,
    valor FLOAT NOT NULL);

CREATE TABLE venda (
    idVenda INTEGER NOT NULL PRIMARY KEY AUTO_INCREMENT,
    valorTotal FLOAT NOT NULL,
    datahora DATE);
    
CREATE TABLE itemVenda (
    idVenda INTEGER,
    idProduto INTEGER,
    idItemVenda INTEGER NOT NULL PRIMARY KEY AUTO_INCREMENT,
    CONSTRAINT fk_Venda FOREIGN KEY (idVenda) REFERENCES venda(idVenda),
    CONSTRAINT fk_Produto FOREIGN KEY (idProduto) REFERENCES produto(idProduto),
    CONSTRAINT uniq_VendaProduto UNIQUE(idVenda, idProduto));
    
INSERT INTO produto (idProduto, valor)
	VALUES
    ('1', '100'),
    ('2', '200'),
    ('3', '300'),
    ('4', '400'),
    ('5', '500');

INSERT INTO venda (valorTotal, datahora)
	VALUES
	('200', '2025-05-06'),
    ('200', '2025-05-07'),
    ('200', '2025-05-08'),
    ('200', '2025-05-09'),
    ('200', '2025-05-10');
