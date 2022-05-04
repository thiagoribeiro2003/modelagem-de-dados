# Comandos SQL para CRUD - Referência

## Resumo
- C -> Create (inserir dados)
- R -> Read (ler dados)
- U -> Update (atualizar dados)
- D -> Delete (excluir dados)

 
## INSERT

### Fabricantes
```sql
INSERT INTO fabricantes (nome) VALUES('Asus'); /* texto tem que ser em aspas simples*/
INSERT INTO fabricantes (nome) VALUES('Dell');
INSERT INTO fabricantes (nome) VALUES('Apple'), ('LG'), ('Samsung'), ('Brastemp');
```

### Produtos
```sql
INSERT INTO produtos(nome, descricao, preco, quantidade, fabricante_id) VALUES (
     'Ultrabook',
     'Ultrabook Asus com processador intel Core i12, memória RAM de 16GB e Windows 11',
     6500.99,
     7,
     1
);

INSERT INTO produtos(nome, descricao, preco, quantidade, fabricante_id) VALUES (
    'Tablet android',
    'Tablet com a versão 12 do sistema operacional da Google, possui tela de 10 polegadas e armazenamento de 64GB.',
    4999,
    3,
    5 #Samsung
);

INSERT INTO produtos(nome, descricao, preco, quantidade, fabricante_id) VALUES 
(
    'Geladeira',
    'Refrigerador Frost-free com acesso à Internet das coisas e Bla bla bla',
    1500,
    10,
    6 #Brastemp 
),

(
    'Iphone 13 Pro Max',
    'Alta durabilidade, processador Bionic 14, 128GB de armazenamento, 6GB de RAM e caro pra caramba',
    6999.99,
    3,
    3 #Apple
    
),

(
    'iPad Mini',
    'Tablet da Apple com tela retina display 4k, memória interna de 64GB, acesso ao iCloud.',
    5000,
    8,
    3 #apple
);
```

<!--1)Insira mais 2 fabricantes: Positivo e Microsoft

2) Insira mais 2 produtos:

    - Xbox; console de última geração com acesso aos melhores jogos e bla bla; 2500; 6; Microsoft

    - Ultrabook; Equipamento com processador AMD Ryzen55; 12GB; placa de vídeo RTX; 4500.68; 12; Positivo -->

```sql 
 INSERT INTO fabricantes (nome) VALUE ('Microsoft');
 INSERT INTO fabricantes (nome) VALUE ('Positivo');
 ```
```sql
 INSERT INTO produtos (nome, descricao, preco, quantidade, fabricante_id) VALUES 
 (
     'Xbox',
     'Console de última geração com acesso aos melhores jogos e bla bla.',
     2500,
     6,
     7 #Microsoft
 ),

 (
    'Ultrabook',
    'Equipamento com processador AMD Ryzen55, 12GB, placa de vídeo RTX.',
    4500.68,
    12,
    8
 );
 ```

 ```sql
INSERT INTO fabricantes (nome)
VALUES ('Positivo'), ('Microsoft');
 ```

 ## SELECT

 ### Ler dados da tabela produtos
 ```sql
 SELECT * FROM produtos; -- * = tudo
 SELECT nome, preco FROM produtos; -- FROM produtos; = pegar da tabela produtos
 SELECT nome FROM  produtos WHERE preco < 5000;
 SELECT nome, descricao FROM produtos WHERE fabricante_id = 3; #Apple
 ```


 ### Operadores Lógicos: E OU NÃO 
```sql
SELECT * FROM produtos 
WHERE preco >= 5000 AND preco < 8000;

SELECT nome, preco FROM produtos
-- dos fabricantes apple e microsoft
WHERE fabricante_id = 3 OR  fabricante_id = 7;

--Monte uma consulta que traga nome, preco e quantidade de todos os produtos exceto os do fabricante apple
```
```sql
SELECT nome, preco, quantidade FROM produtos
WHERE NOT fabricante_id = 3; -- Versão 1 - usando NOT

SELECT nome, preco, quantidade FROM produtos
WHERE fabricante_id != 3; -- Versão 2 - Usando operador != (operador de diferença)

SELECT nome, preco FROM produtos
WHERE fabricante_id IN (3,8); -- Usando função IN(Lista) (Obs: IN não é um operador lógico).
```


### Filtros
```sql
SELECT nome, preco FROM produtos ORDER BY nome; -- ordem crescente (para letras em ordem alfabética)
SELECT nome,preco FROM produtos ORDER BY nome DESC; -- ordem decrecente 

SELECT nome, descricao FROM produtos 
WHERE descricao LIKE '%processador%'; -- LIKE (COMO)
 -- % OPERADOR CORINGA, PROCURE PELA PALAVRA PROCESSADOR NO MEIO DO TEXTO (SIGNIFICA QUALQUER TEXTO, NESSE CASO QUALQUER COISA ANTES OU DEPOIS DA PALAVRA NAO IMPORTA OQ É, APENAS A PALAVRA Q ESTA ENTRE OS %...%)
```

### Operações e Funções de agregação
```sql
-- SUM (SOMA)
SELECT SUM(preco) FROM produtos; 

SELECT SUM(preco) AS TOTAL FROM produtos; -- AS É UM ALIAS (APELIDO) 
-- ( 'TOTAL' Nesse caso esse total é um nome que você da)

SELECT SUM(quantidade) AS "Quantidade em Estoque" FROM produtos;

SELECT SUM(quantidade) AS "Quantidade em estoque" FROM produtos WHERE fabricante_id = 3; -- Apple


-- AVG (MÉDIA)
SELECT AVG(preco) AS "Média dos Preços" FROM produtos; -
-- ROUND (Arredondamento) 
SELECT ROUND(AVG(preco),2) AS "Média dos Preços" FROM produtos; -- a virgula igual no exemplo ...,2 serve para vc definir o número de casa decimais que vai aparecer


-- COUNT (CONTAGEM)
SELECT COUNT(id) AS "Quantidade de Produtos" FROM produtos;


-- DISTINCT é um comando para evitar a duplicidade na contagem de campos que não são chave-primária
SELECT COUNT(DISTINCT fabricante_id) AS "Quantidade de fabricantes" FROM produtos; -- DISTINCT VAI VER Q O FABRICANTE SE REPETE E VAI CONTAR SOMENTE UMA VEZ

SELECT nome, preco, quantidade, (preco * quantidade) AS total FROM produtos;
```

### Agrupamentos
```sql
-- GROUP BY permite segmentar resultados da consulta. Neste caso, somamos todos os preços e segmentos/agrupando por cada fabricante.
SELECT fabricante_id, SUM(preco) AS Total FROM produtos
GROUP BY fabricante_id;
```


## UPDATE (sempre com WHERE)

### Atualizar dados de uma tabela
```sql
-- set(inserir)
UPDATE fabricantes SET nome = 'Microsoft Brasil' WHERE id = 7;
UPDATE fabricantes SET nome = 'Positivo' WHERE id = 8;

--Mudar o preço do ultrabook da Positivo para 5200
UPDATE produtos SET preco = 5200
WHERE id = 7;

--Mudar a quantidade dos produtos da Asus e da Apple para 15.
UPDATE produtos SET quantidade = 15
WHERE fabricante_id = 1 OR fabricante_id = 3;
```

### Excluir dados de uma tabela
```sql
DELETE FROM fabricantes WHERE id = 4; -- LG


```
