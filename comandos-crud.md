### Comandos CRUD

### Inserindo Dados na Tabela Cursos

```sql
INSERT INTO cursos(titulo, carga_horaria, professores_id)
VALUES(
    'Front-End',
    40,
    null
),
(
    'Back-End',
    80,
    null
),
(
    'UX/UI Design',
    30,
    null
),
(
    'Figma',
    10,
    null
),
(
    'Redes de Computadores',
    100,
    null
);
```

```sql
INSERT INTO professores(nome, area_de_atuacao, cursos_id)
VALUES(
    'Jon Oliva',
    'infra',
    5
),
(
    'Lemmy Kilmister',
    'design',
    4
),
(
    'Neil Peart',
    'design',
    3
),
(
    'Ozzy Osbourne',
    'desenvolvimento',
    2
),
(
    'David Gilmour',
    'desenvolvimento',
    1
);
```

```sql
UPDATE cursos SET professores_id = 1  WHERE id = 5;
UPDATE cursos SET professores_id = 2  WHERE id = 4;
UPDATE cursos SET professores_id = 3  WHERE id = 3;
UPDATE cursos SET professores_id = 4  WHERE id = 2;
UPDATE cursos SET professores_id = 5  WHERE id = 1;
```

```sql
INSERT INTO alunos(nome, data_de_nacimento, primeira_nota, segunda_nota, cursos_id)
VALUES(
    'Joao Silva',
    '1998-05-15',
    7.50,
    8.00,
    1
),
(
    'Maria Oliveira',
    '1999-07-22',
    9.00,
    8.00,
    2
),
(
    'Carlos Santos',
    '1998-11-10',
    6.50,
    7.50,
    3
),
(
    'Ana Souza',
    '2001-02-05',
    9.50,
    9.00,
    4
),
(
    'Lucas Pereira',
    '2000-01-12',
    7.50,
    6.00,
    5
),
(
    'Beatriz Costa',
    '1997-05-28',
    8.00,
    7.00,
    5
),
(
    'Gabriel Almeida',
    '1999-09-19',
    7.00,
    8.50,
    4
),
(
    'Sofia Rodrigues',
    '2002-04-30',
    9.00,
    9.50,
    3
),
(
    'Pedro Lima',
    '1998-08-25',
    6.00,
    5.50,
    2
),
(
    'Laura Martins',
    '2000-12-14',
    8.00,
    8.50,
    1
);
```

### Usando Comandos CRUD Para Consultas

```sql
SELECT nome, data_de_nacimento FROM alunos
WHERE data_de_nacimento < '2009-01-01';
```

```sql
SELECT nome, ROUND((AVG(primeira_nota + segunda_nota) / 2), 2) AS "Média das notas" FROM alunos
GROUP BY nome;
```

```sql
SELECT titulo, carga_horaria, (carga_horaria * 0.25) AS "Limite de Faltas" FROM cursos
ORDER BY titulo ASC;
```

```sql
SELECT nome, area_de_atuacao FROM professores
WHERE cursos_id = 2 OR cursos_id = 1;
```



