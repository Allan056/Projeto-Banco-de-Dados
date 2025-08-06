
Create Database Teste;

USE Teste

CREATE TABLE USUARIO (
	CPF_USUARIO VARCHAR(20) NOT NULL PRIMARY KEY,
	NOME VARCHAR(50) NOT NULL,
	SOBRENOME VARCHAR(50) NOT NULL,
	TELEFONE VARCHAR(16) NOT NULL,
	EMAIL VARCHAR(20) NOT NULL,
	CEP VARCHAR(10) NOT NULL,
	RUA VARCHAR(50) NOT NULL,
	NUEMRO VARCHAR(10) NOT NULL,
	CIDADE VARCHAR(20) NOT NULL,
	ESTADO VARCHAR(20) NOT NULL
	);


CREATE TABLE PERFIL_CRIANCA (
	ID_PERFIL_CRIANCA INT PRIMARY KEY,
	NOME VARCHAR(20) NOT NULL,
	IDEDADE VARCHAR(20) NOT NULL,
	RESTICOES VARCHAR(20) NOT NULL,
	OBESERVAOES VARCHAR(20) NOT NULL,
	CPF_USUARIO VARCHAR(20) NOT NULL
	);

CREATE TABLE PEDIDOVENDA(
	ID_PEDIDO INT PRIMARY KEY NOT NULL,
	DATA DATE NOT NULL,
	QTD_PRODUTOS INT NOT NULL,
	STATUS_VENDA VARCHAR(100) NOT NULL,
	CPF_USUARIO VARCHAR(20) NOT NULL,
	CPF_ENTREGADOR VARCHAR(20) NOT NULL

	);


CREATE TABLE ENTREGADOR(
	CPF_ENTREGADOR VARCHAR(20) PRIMARY KEY,
	NOME VARCHAR(20),
	SOBRENOME VARCHAR(50),
	SALARIO DECIMAL(10,2),
	ID_PEDIDO INT NOT NULL
	);


ALTER TABLE PERFIL_CRIANCA
ADD CONSTRAINT FK_PERFIL_CRIANCA_USUARIO FOREIGN KEY (CPF_USUARIO)
REFERENCES USUARIO(CPF_USUARIO);


ALTER TABLE PEDIDOVENDA
ADD CONSTRAINT FK_PEDIDOVENDA_USUARIO FOREIGN KEY (CPF_USUARIO)
REFERENCES USUARIO(CPF_USUARIO);


ALTER TABLE PEDIDOVENDA
ADD CONSTRAINT FK_PEDIDOVENDA_ENTREGADOR FOREIGN KEY (CPF_ENTREGADOR)
REFERENCES ENTREGADOR(CPF_ENTREGADOR);


ALTER TABLE ENTREGADOR
ADD CONSTRAINT FK_ENTREGADOR_PEDIDOVENDA FOREIGN KEY (ID_PEDIDO)
REFERENCES PEDIDOVENDA(ID_PEDIDO);
.

CREATE TABLE PEDIDOPRODUTO_INCLUI (
    ID_PRODUTO INT PRIMARY KEY,          
	ID_PEDIDO INT,                       
    QUANTIDADE INT,                      
    FK_PRODUTO_ID_PROUTO INT,            
    FK_PEDIDOVENDA_ID_PEDIDO INT         
);

--DROP TABLE PEDIDOPRODUTO_INCLUI;
-- Exclui a tabela "PEDIDOPRODUTO_INCLUI" do banco de dados.

CREATE TABLE PRODUTO (
    ID_PRODUTO INT PRIMARY KEY,         
	COD_TIPO_PROD INT,                   
    DESCRICAO VARCHAR (100),             
    NOME VARCHAR (100),                  
    FK_TIPO_PRODUTO_COD_TIPO_PROD INT    
);

-- TABELA PROMOCAO
CREATE TABLE PROMOCAO (
    COD_PROMOCAO INTEGER PRIMARY KEY,   
    NOME_CAMPANHA VARCHAR(100),         
    PORCENT_DESCONTO DECIMAL(5,2),      
    ID_PRODUTO INTEGER,                 
    OBSERVACAO VARCHAR(255),            
    FOREIGN KEY (ID_PRODUTO) REFERENCES PRODUTO(ID_PRODUTO)     
); 

CREATE TABLE TIPO_PRODUTO (
    COD_TIPO_PROD INTEGER PRIMARY KEY,   
    NOME_TIPO_PROD VARCHAR(100)         
);



CREATE TABLE FORNECEDOR (
	CNPJ INT PRIMARY KEY,
	TELEFONE VARCHAR(20) NOT NULL,
	NOME_FANTASIA VARCHAR(100) NOT NULL,
	RAZAO_SOCIAL VARCHAR(100) NOT NULL,
	ENDERECO VARCHAR (100) NOT NULL,
	TELEFONE_2 VARCHAR (20),
	EMAIL VARCHAR(100) NOT NULL,
	CIDADE VARCHAR(100) NOT NULL,
	ESTADO VARCHAR(50) NOT NULL,
	BAIRRO VARCHAR(100) NOT NULL,
	CEP VARCHAR(10) NOT NULL,
	RUA VARCHAR(100) NOT NULL,
	NUMERO VARCHAR(10)
)

CREATE TABLE PEDIDO_COMPRA (
	NUM_PEDIDO_FORNECEDOR INT PRIMARY KEY,
	DATA_PEDIDO DATE,
	CNPJ INT,
	STATUS VARCHAR(50)
)


ALTER TABLE PEDIDO_COMPRA
ALTER COLUMN CNPJ INT NOT NULL


ALTER TABLE PEDIDO_COMPRA
ADD CONSTRAINT FK_FORNECEDOR_CNPJ FOREIGN KEY (CNPJ) REFERENCES FORNECEDOR(CNPJ);

CREATE TABLE PRODUTO_PEDIDOCOMPRA (
	ID_PRODUTO_PEDIDO INT PRIMARY KEY,
	DATA_COMPRA_FORNECEDOR DATE,
	QUANTIDADE INT,
	NUM_PEDIDO_FORNECEDOR INT
)



ALTER TABLE PRODUTO_PEDIDOCOMPRA
ADD CONSTRAINT FK_NUM_PEDIDO_FORNECEDOR FOREIGN KEY (NUM_PEDIDO_FORNECEDOR) REFERENCES PEDIDO_COMPRA(NUM_PEDIDO_FORNECEDOR);



use Teste
INSERT INTO USUARIO(CPF_USUARIO,NOME,SOBRENOME,TELEFONE,EMAIL,CEP,RUA,NUEMRO,CIDADE,ESTADO)
VALUES (48968321833, 'ALLAN', 'CAMILO', '40028922', 'ALLANCAMILO32@GMAIL.COM','05223100','TIBURNO','222','S�O PAULO','SP')

INSERT INTO USUARIO (CPF_USUARIO, NOME, SOBRENOME, TELEFONE, EMAIL, CEP, RUA, NUEMRO, CIDADE, ESTADO) VALUES
('00000000000', 'Juliana', 'Souza', '(11) 95122-8328', 'juliana37@yahoo.com.br', '83978-954', 'Av. Brasil', '367', 'Fortaleza', 'CE'),
('00000000001', 'Mariana', 'Lima', '(11) 98215-6106', 'mariana6@yahoo.com.br', '47568-329', 'Rua dos Andradas', '417', 'Fortaleza', 'CE'),
('00000000002', 'Carlos', 'Almeida', '(11) 94956-3900', 'carlos17@hotmail.com', '83194-598', 'Av. Brasil', '258', 'Curitiba', 'PR'),
('00000000003', 'Camila', 'Santos', '(11) 95791-1999', 'camila66@gmail.com', '35146-673', 'Av. Brasil', '116', 'Recife', 'PE'),
('00000000004', 'Pedro', 'Silva', '(11) 97951-6234', 'pedro2@yahoo.com.br', '63236-972', 'Av. Brasil', '447', 'Belo Horizonte', 'MG'),
('00000000005', 'Fernanda', 'Souza', '(11) 95758-8736', 'fernanda14@hotmail.com', '22363-268', 'Av. Paulista', '270', 'Bras�lia', 'DF'),
('00000000006', 'Juliana', 'Lima', '(11) 97978-2057', 'juliana48@hotmail.com', '83153-905', 'Av. Brasil', '352', 'Bras�lia', 'DF'),
('00000000007', 'Carlos', 'Ferreira', '(11) 92863-5812', 'carlos77@yahoo.com.br', '20276-709', 'Av. Paulista', '276', 'Rio de Janeiro', 'RJ'),
('00000000008', 'Camila', 'Oliveira', '(11) 98199-3549', 'camila46@gmail.com', '96744-343', 'Rua XV de Novembro', '431', 'Belo Horizonte', 'MG'),
('00000000009', 'Rafael', 'Martins', '(11) 92248-9509', 'rafael43@hotmail.com', '87865-398', 'Rua XV de Novembro', '59', 'Fortaleza', 'CE');


INSERT INTO PERFIL_CRIANCA (ID_PERFIL_CRIANCA, NOME, IDEDADE, RESTICOES, OBESERVAOES, CPF_USUARIO) VALUES
(1, 'Mateus', '6 anos', 'Nenhuma', 'Prefere frutas', '00000000000'),
(2, 'Mateus', '4 anos', 'Nenhuma', 'Recusa legumes', '00000000001'),
(3, 'Carlos', '9 anos', 'Alergia a ovos', 'Prefere frutas', '00000000002'),
(4, 'Lucas', '10 anos', 'Sem gl�ten', 'Prefere frutas', '00000000003'),
(5, 'Rafael', '9 anos', 'Vegetariano', 'Prefere frutas', '00000000004'),
(6, 'Carlos', '10 anos', 'Sem gl�ten', 'Aceita bem sopas', '00000000005'),
(7, 'Mateus', '4 anos', 'Alergia a ovos', 'Aceita bem sopas', '00000000006'),
(8, 'Juliana', '2 anos', 'Sem lactose', 'Aceita bem sopas', '00000000007'),
(9, 'Juliana', '7 anos', 'Vegetariano', 'Prefere frutas', '00000000008'),
(10, 'Carlos', '6 anos', 'Nenhuma', 'Al�rgico a amendoim', '00000000009');



INSERT INTO ENTREGADOR (CPF_ENTREGADOR, NOME, SOBRENOME, SALARIO, ID_PEDIDO) VALUES
('11111111110', 'Pedro', 'Costa', 2539.76, 1),
('11111111111', 'Fernanda', 'Costa', 2343.65, 2),
('11111111112', 'Lucas', 'Santos', 1955.91, 3),
('11111111113', 'Ana', 'Ferreira', 2846.78, 4),
('11111111114', 'Carlos', 'Santos', 2782.36, 5),
('11111111115', 'Lucas', 'Costa', 1779.45, 6),
('11111111116', 'Lucas', 'Oliveira', 2070.08, 7),
('11111111117', 'Mateus', 'Pereira', 2754.94, 8),
('11111111118', 'Pedro', 'Ferreira', 2816.95, 9),
('11111111119', 'Fernanda', 'Ferreira', 1870.68, 10);


INSERT INTO PEDIDOVENDA (ID_PEDIDO, DATA, QTD_PRODUTOS, STATUS_VENDA, CPF_USUARIO, CPF_ENTREGADOR) VALUES
(1, '2023-03-15', 2, 'Entregue', '00000000000', '11111111110'),
(2, '2023-05-22', 3, 'Pago', '00000000001', '11111111111'),
(3, '2024-01-09', 1, 'Pendente', '00000000002', '11111111112'),
(4, '2023-11-18', 5, 'Entregue', '00000000003', '11111111113'),
(5, '2024-07-30', 2, 'Cancelado', '00000000004', '11111111114'),
(6, '2023-06-04', 4, 'Pago', '00000000005', '11111111115'),
(7, '2024-04-12', 3, 'Entregue', '00000000006', '11111111116'),
(8, '2023-08-28', 1, 'Pendente', '00000000007', '11111111117'),
(9, '2024-03-20', 2, 'Pago', '00000000008', '11111111118'),
(10, '2024-05-05', 3, 'Entregue', '00000000009', '11111111119');


INSERT INTO TIPO_PRODUTO (COD_TIPO_PROD, NOME_TIPO_PROD) VALUES
(1, 'Papinha Org�nica'),
(2, 'Suco Natural'),
(3, 'Lanche Saud�vel'),
(4, 'Pur� de Legumes'),
(5, 'Comida Congelada'),
(6, 'Vitamina'),
(7, 'Cereal Infantil'),
(8, 'Sopinha'),
(9, 'Fruta Picada'),
(10, 'Iogurte Natural');


INSERT INTO PRODUTO (ID_PRODUTO, COD_TIPO_PROD, DESCRICAO, NOME, FK_TIPO_PRODUTO_COD_TIPO_PROD) VALUES
(1, 1, 'Papinha de cenoura org�nica', 'Papinha Cenoura', 1),
(2, 2, 'Suco de ma�� sem conservantes', 'Suco Ma��', 2),
(3, 3, 'Lanche com frutas secas e castanhas', 'Lanche Nutritivo', 3),
(4, 4, 'Pur� de batata doce com ab�bora', 'Pur� Nutri', 4),
(5, 5, 'Comida congelada caseira', 'Congelado Caseiro', 5),
(6, 6, 'Vitamina de banana e aveia', 'Vitamina Banana', 6),
(7, 7, 'Cereal de milho integral', 'Cereal Nutri', 7),
(8, 8, 'Sopa de legumes leve', 'Sopa Leve', 8),
(9, 9, 'Ma�� e banana picadas', 'Fruta Mix', 9),
(10, 10, 'Iogurte com probi�ticos', 'Iogurte Kids', 10);


INSERT INTO PROMOCAO (COD_PROMOCAO, NOME_CAMPANHA, PORCENT_DESCONTO, ID_PRODUTO, OBSERVACAO) VALUES
(1, 'Promo��o Ver�o', 10.00, 1, 'V�lido at� o fim do m�s'),
(2, 'Desconto Nutri', 15.00, 2, 'Apenas novos clientes'),
(3, 'Semana Saud�vel', 5.00, 3, 'Promo��o semanal'),
(4, 'Comida Fresca', 20.00, 4, 'Limitado a 3 por pedido'),
(5, 'Oferta Especial', 12.00, 5, 'At� acabar o estoque'),
(6, 'Super Sabor', 8.00, 6, 'Dispon�vel somente online'),
(7, 'Promo��o Cereal', 7.00, 7, 'V�lido nesta semana'),
(8, 'Sa�de em Conta', 13.00, 8, 'Clientes antigos'),
(9, 'Frutas do Dia', 6.00, 9, 'Inclui sobremesa'),
(10, 'Promo Yogurt', 10.00, 10, 'Combina com frutas');


INSERT INTO PEDIDOPRODUTO_INCLUI (ID_PRODUTO, ID_PEDIDO, QUANTIDADE, FK_PRODUTO_ID_PROUTO, FK_PEDIDOVENDA_ID_PEDIDO) VALUES
(1, 1, 2, 1, 1),
(2, 2, 1, 2, 2),
(3, 3, 4, 3, 3),
(4, 4, 1, 4, 4),
(5, 5, 3, 5, 5),
(6, 6, 2, 6, 6),
(7, 7, 2, 7, 7),
(8, 8, 1, 8, 8),
(9, 9, 3, 9, 9),
(10, 10, 1, 10, 10);


INSERT INTO FORNECEDOR (CNPJ, TELEFONE, NOME_FANTASIA, RAZAO_SOCIAL, ENDERECO, TELEFONE_2, EMAIL, CIDADE, ESTADO, BAIRRO, CEP, RUA, NUMERO) VALUES
(1000000001, '(11) 91234-5678', 'ForBaby Alimentos', 'ForBaby Ltda', 'Av. Brasil, 100', '(11) 99876-5432', 'contato@forbaby.com', 'S�o Paulo', 'SP', 'Centro', '01001-000', 'Av. Brasil', '100'),
(1000000002, '(21) 93456-7890', 'NutriVida', 'NutriVida Alimentos SA', 'Rua Sa�de, 200', '(21) 98765-4321', 'nutrivida@alimentos.com', 'Rio de Janeiro', 'RJ', 'Copacabana', '22041-001', 'Rua Sa�de', '200'),
(1000000003, '(31) 92345-6789', 'VidaNatural', 'VidaNatural ME', 'Av. Natureza, 300', '(31) 97654-3210', 'contato@vidanatural.com', 'Belo Horizonte', 'MG', 'Savassi', '30130-000', 'Av. Natureza', '300'),
(1000000004, '(41) 93234-5678', 'BabyFit', 'BabyFit Comercial', 'Rua Bem-Estar, 123', NULL, 'babyfit@fit.com', 'Curitiba', 'PR', '�gua Verde', '80240-000', 'Rua Bem-Estar', '123'),
(1000000005, '(51) 91876-5432', 'AlimentaBem', 'AlimentaBem Distribuidora', 'Av. Infantil, 987', NULL, 'contato@alimentabem.com', 'Porto Alegre', 'RS', 'Moinhos', '90430-000', 'Av. Infantil', '987'),
(1000000006, '(61) 92123-4567', 'Beb�Nutre', 'Beb�Nutre Ltda', 'Rua da Crian�a, 654', NULL, 'bebes@nutre.com', 'Bras�lia', 'DF', 'Asa Sul', '70380-000', 'Rua da Crian�a', '654'),
(1000000007, '(71) 90098-7654', 'OrganiKids', 'OrganiKids S/A', 'Av. Saud�vel, 852', '(71) 95544-3322', 'organikids@org.com', 'Salvador', 'BA', 'Pituba', '41830-000', 'Av. Saud�vel', '852'),
(1000000008, '(81) 94455-6677', 'Mam�eSabe', 'Mam�eSabe Ltda', 'Rua Saborosa, 741', NULL, 'mamae@sabe.com', 'Recife', 'PE', 'Boa Viagem', '51020-000', 'Rua Saborosa', '741'),
(1000000009, '(85) 97766-5544', 'Saud�velJ�', 'Saud�velJ� Fornecimentos', 'Av. Sa�de Total, 369', NULL, 'saude@ja.com', 'Fortaleza', 'CE', 'Meireles', '60170-000', 'Av. Sa�de Total', '369'),
(1000000010, '(92) 98877-6655', 'BemViver', 'BemViver Alimenta��o', 'Rua Vida Longa, 159', NULL, 'bemviver@nutricao.com', 'Manaus', 'AM', 'Adrian�polis', '69057-000', 'Rua Vida Longa', '159');


INSERT INTO PEDIDO_COMPRA (NUM_PEDIDO_FORNECEDOR, DATA_PEDIDO, CNPJ, STATUS) VALUES
(1, '2024-01-15', 1000000001, 'Recebido'),
(2, '2024-01-20', 1000000002, 'Processando'),
(3, '2024-02-01', 1000000003, 'Enviado'),
(4, '2024-02-10', 1000000004, 'Recebido'),
(5, '2024-03-05', 1000000005, 'Pendente'),
(6, '2024-03-20', 1000000006, 'Enviado'),
(7, '2024-04-11', 1000000007, 'Recebido'),
(8, '2024-05-03', 1000000008, 'Pendente'),
(9, '2024-06-18', 1000000009, 'Enviado'),
(10, '2024-07-10', 1000000010, 'Recebido');



INSERT INTO PRODUTO_PEDIDOCOMPRA (ID_PRODUTO_PEDIDO, DATA_COMPRA_FORNECEDOR, QUANTIDADE, NUM_PEDIDO_FORNECEDOR) VALUES
(1, '2024-01-16', 100, 1),
(2, '2024-01-21', 80, 2),
(3, '2024-02-02', 150, 3),
(4, '2024-02-11', 90, 4),
(5, '2024-03-06', 200, 5),
(6, '2024-03-21', 75, 6),
(7, '2024-04-12', 60, 7),
(8, '2024-05-04', 120, 8),
(9, '2024-06-19', 50, 9),
(10, '2024-07-11', 130, 10);


SELECT * FROM TIPO_PRODUTO;
SELECT * FROM PRODUTO;
SELECT * FROM USUARIO;
SELECT * FROM ENTREGADOR;
SELECT * FROM PEDIDOVENDA;
SELECT * FROM PERFIL_CRIANCA;
SELECT * FROM PEDIDOPRODUTO_INCLUI;
SELECT * FROM PROMOCAO;
SELECT * FROM FORNECEDOR;
SELECT * FROM PEDIDO_COMPRA;
SELECT * FROM PRODUTO_PEDIDOCOMPRA;

