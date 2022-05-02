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
 SELECT * FROM produtos;
 ```