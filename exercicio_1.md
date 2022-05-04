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
## Inserindo gêneros
```sql
INSERT INTO generos(generos) VALUES('Ação');
INSERT INTO generos(generos) VALUES('Suspense');
INSERT INTO generos(generos) VALUES('Terror'), ('Romance'), ('Comédia'), ('Drama'), ('Documentário');
```

## Inserindo filmes
```sql
INSERT INTO filmes(titulo_do_filme, ano_de_lancamento, generos_id) VALUES(
    'The Batman',
    2022,
    2
    );

INSERT INTO filmes(titulo_do_filme, ano_de_lancamento, generos_id) VALUES(
    'A Culpa É das Estrelas',
    2014,
    6
);

INSERT INTO filmes(titulo_do_filme, ano_de_lancamento, generos_id) VALUES(
    'Gente Grande 2',
    2013,
    5
);

INSERT INTO filmes(titulo_do_filme, ano_de_lancamento, generos_id) VALUES(
    'Homem-Aranha: Sem Volta para Casa',
    2021,
    1 
);

INSERT INTO filmes(titulo_do_filme, ano_de_lancamento, generos_id) VALUES(
    'Corra',
    2017,
    3
);

INSERT INTO filmes(titulo_do_filme, ano_de_lancamento, generos_id) VALUES(
    'Os Vingadores',
    2012,
    4
);

INSERT INTO filmes(titulo_do_filme, ano_de_lancamento, generos_id) VALUES(
    'Piratas do Caribe: A Maldição do Pérola Negra',
    2003,
    1
);
```

### Alterando dado
```sql
UPDATE filmes SET generos_id = 1 WHERE id = 6
```


### Inserindo campo de descrição
```sql
ALTER TABLE filmes ADD descricao NOT NULL;
```

### Inserindo no campo de descrição
```sql
UPDATE filmes SET descricao = 'Após dois anos espreitando as ruas como Batman, Bruce Wayne se encontra nas profundezas mais sombrias de Gotham City. Com poucos aliados confiáveis, o vigilante solitário se estabelece como a personificação da vingança para a população.' WHERE id = 1;

UPDATE filmes SET descricao = 'Hazel Grace Lancaster e Augustus Waters são dois adolescentes que se conhecem em um grupo de apoio para pacientes com câncer. Por causa da doença, Hazel sempre descartou a ideia de se envolver amorosamente, mas acaba cedendo ao se apaixonar por Augustus. Juntos, eles viajam para Amsterdã, onde embarcam em uma jornada inesquecível.' WHERE id = 2;
```

### Para exibir somenyr filmes de ação
```sql
SELECT titulo_do_filme, ano_de_lancamento FROM filmes WHERE generos_id = 1;
```




