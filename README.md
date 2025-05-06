# DATABASE
...
Crie um banco de dados; - Crie suas tabelas e respectivos relacionamentos; - Insira no mínimo de 5 registros em cada tabela; - Atualize 2 registros de qualquer tabela; - Exclua 2 registros de qualquer tabela; - Faça 2 consultas utilizando order by e where.
...

CREATE DATABASE EleitoralDB;

USE EleitoralDB;

CREATE TABLE LOCALIDADE (
    id_localidade INTEGER PRIMARY KEY,
    nome_localidade VARCHAR(255),
    estado VARCHAR(255)
);

CREATE TABLE ZONA_ELEITORAL (
    id_zona INTEGER PRIMARY KEY,
    nome_zona VARCHAR(255),
    FK_LOCALIDADE_id_localidade INTEGER,
    FOREIGN KEY (FK_LOCALIDADE_id_localidade) REFERENCES LOCALIDADE(id_localidade)
);

CREATE TABLE SECAO_ELEITORAL (
    id_secao INTEGER PRIMARY KEY,
    nome_secao VARCHAR(255),
    FK_ZONA_id_zona INTEGER,
    FOREIGN KEY (FK_ZONA_id_zona) REFERENCES ZONA_ELEITORAL(id_zona)
);

INSERT INTO LOCALIDADE (id_localidade, nome_localidade, estado) VALUES (1, 'Localidade A', 'Estado A');
INSERT INTO LOCALIDADE (id_localidade, nome_localidade, estado) VALUES (2, 'Localidade B', 'Estado B');
INSERT INTO LOCALIDADE (id_localidade, nome_localidade, estado) VALUES (3, 'Localidade C', 'Estado C');
INSERT INTO LOCALIDADE (id_localidade, nome_localidade, estado) VALUES (4, 'Localidade D', 'Estado D');
INSERT INTO LOCALIDADE (id_localidade, nome_localidade, estado) VALUES (5, 'Localidade E', 'Estado E');

INSERT INTO ZONA_ELEITORAL (id_zona, nome_zona, FK_LOCALIDADE_id_localidade) VALUES (1, 'Zona 1', 1);
INSERT INTO ZONA_ELEITORAL (id_zona, nome_zona, FK_LOCALIDADE_id_localidade) VALUES (2, 'Zona 2', 2);
INSERT INTO ZONA_ELEITORAL (id_zona, nome_zona, FK_LOCALIDADE_id_localidade) VALUES (3, 'Zona 3', 3);
INSERT INTO ZONA_ELEITORAL (id_zona, nome_zona, FK_LOCALIDADE_id_localidade) VALUES (4, 'Zona 4', 4);
INSERT INTO ZONA_ELEITORAL (id_zona, nome_zona, FK_LOCALIDADE_id_localidade) VALUES (5, 'Zona 5', 5);

INSERT INTO SECAO_ELEITORAL (id_secao, nome_secao, FK_ZONA_id_zona) VALUES (1, 'Secao 1', 1);
INSERT INTO SECAO_ELEITORAL (id_secao, nome_secao, FK_ZONA_id_zona) VALUES (2, 'Secao 2', 2);
INSERT INTO SECAO_ELEITORAL (id_secao, nome_secao, FK_ZONA_id_zona) VALUES (3, 'Secao 3', 3);
INSERT INTO SECAO_ELEITORAL (id_secao, nome_secao, FK_ZONA_id_zona) VALUES (4, 'Secao 4', 4);
INSERT INTO SECAO_ELEITORAL (id_secao, nome_secao, FK_ZONA_id_zona) VALUES (5, 'Secao 5', 5);

UPDATE LOCALIDADE SET nome_localidade = 'Localidade X' WHERE id_localidade = 1;
UPDATE LOCALIDADE SET estado = 'Estado Y' WHERE id_localidade = 2;


DELETE FROM ZONA_ELEITORAL WHERE id_zona = 4;
DELETE FROM ZONA_ELEITORAL WHERE id_zona = 5;

SELECT * FROM LOCALIDADE WHERE estado = 'Estado A' ORDER BY nome_localidade;
SELECT * FROM SECAO_ELEITORAL WHERE FK_ZONA_id_zona = 3 ORDER BY nome_secao;
