## Criação do banco de dados
```sql
CREATE DATABASE exercicio_1 CHARACTER SET utf8mb4
```

## Tabela filmes
```sql
CREATE TABLE filmes(
    id INT NOT NULL PRIMARY KEY AUTO_INCREMENT,
    titulo_do_filme VARCHAR(45) NOT NULL,
    ano_de_lancamento YEAR(4) NOT NULL,
    generos_id INT NOT NULL
);
```

## Tabela generos
```sql 
CREATE TABLE generos (
    id INT NOT NULL PRIMARY KEY AUTO_INCREMENT,
    generos VARCHAR(45) NOT NULL
);
```

## Chave estrangeira (relacionamento entre as tabelas)
```sql
ALTER TABLE filmes
ADD CONSTRAINT fk_filmes_generos

FOREIGN KEY (generos_id) REFERENCES generos(id);
```