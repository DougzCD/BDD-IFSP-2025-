# BDD-IFSP-2025-

DROP DATABASE venda;

CREATE DATABASE Venda;

USE Venda;

DROP TABLE produto;
DROP TABLE venda;
DROP TABLE itemVenda;

CREATE TABLE produto (
    idProduto INTEGER NOT NULL PRIMARY KEY,
    valor FLOAT NOT NULL);

CREATE TABLE venda (
    idVenda INTEGER NOT NULL PRIMARY KEY,
    valorTotal FLOAT NOT NULL,
    datahora DATE);
    
CREATE TABLE itemVenda (
    idVenda INTEGER,
    idProduto INTEGER,
  	valorUnitario FLOAT,
  	quantidade INTEGER,
    idItemVenda INTEGER NOT NULL PRIMARY KEY,
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
    
--SELECT * FROM produto;

INSERT INTO venda (valorTotal, datahora)
	VALUES
	('200', '2025-05-06'),
    ('300', '2025-05-07'),
    ('400', '2025-05-08'),
    ('500', '2025-05-09'),
    ('600', '2025-05-10');
    
--SELECT * from venda;

INSERT into itemVenda(idvenda, idproduto, valorunitario, quantidade)
	VALUES
    ('1', '1', '100', '2'),
    ('2', '1', '100', '1'),
    ('2', '2', '200', '1'),
    ('3', '2', '200', '2'),
    ('4', '1', '100', '2'),
    ('4', '2', '200', '2'),
    ('5', '2', '200', '1'),
	('5', '4', '400', '1');
    
--SELECT * FROM itemVenda;

SELECT idVenda, SUM(valorUnitario * quantidade) FROM itemVenda GROUP BY idVenda;
