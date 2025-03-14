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

## Parte 1
```sql
SELECT nome, data_de_nacimento FROM alunos
WHERE data_de_nacimento < '2009-01-01';
```

## Parte 2
```sql
SELECT nome, ROUND((AVG(primeira_nota + segunda_nota) / 2), 2) AS "Média das notas" FROM alunos
GROUP BY nome;
```

## Parte 3
```sql
SELECT titulo, carga_horaria, (carga_horaria * 0.25) AS "Limite de Faltas" FROM cursos
ORDER BY titulo ASC;
```

## Parte 4
```sql
SELECT nome, area_de_atuacao FROM professores
WHERE cursos_id = 2 OR cursos_id = 1;
```

## Parte 5
```sql
SELECT area_de_atuacao,COUNT(*) AS quantidades_de_professores FROM professores
WHERE area_de_atuacao IN ('design','infra','desenvolvimento')
GROUP BY area_de_atuacao;
```

## Parte 6
```sql
SELECT alunos.nome, cursos.titulo,cursos.carga_horaria FROM alunos
JOIN cursos ON alunos.cursos_id = cursos.id;
```

## parte 7
```sql
SELECT professores.nome, cursos.titulo FROM professores
JOIN cursos ON professores.cursos_id = cursos.id
ORDER BY professores.nome;
```

## parte 8
```sql
SELECT alunos.nome AS alunos,
       cursos.titulo AS cursos,
       professores.nome AS professores
FROM alunos
JOIN cursos ON alunos.cursos_id = cursos.id
JOIN professores ON cursos.professores_id = professores.id;
```

## parte 9
```sql
SELECT cursos.titulo AS cursos,
       COUNT(alunos.id) AS quantidades_de_alunos
FROM cursos
LEFT JOIN alunos ON alunos.cursos_id = cursos.id
GROUP BY cursos.id
ORDER BY quantidades_de_alunos DESC;
```

## parte 10
```sql
SELECT alunos.nome AS alunos,
alunos.primeira_nota,
alunos.segunda_nota,
ROUND((alunos.primeira_nota + alunos.segunda_nota)/2,2) AS medias,
cursos.titulo AS cursos
FROM alunos
JOIN cursos ON alunos.cursos_id = cursos.id
WHERE cursos.titulo IN ('Front-End','Back-End')
ORDER BY alunos.nome;
```

## parte 11
```sql
UPDATE cursos
SET titulo = 'Adoble XD', carga_horaria = 15
WHERE titulo = 'Figma' AND carga_horaria = 10;
```

## parte 12
```sql
DELETE FROM alunos
WHERE cursos_id = (SELECT cursos_id FROM cursos WHERE nome = 'Redes de Computadores' LIMIT 1)
LIMIT 1;

DELETE FROM alunos
WHERE cursos_id = (SELECT cursos_id FROM cursos WHERE nome = 'UX/UI Design' LIMIT 1)
LIMIT 1;
```

## parte 13
```sql
SELECT alunos.nome AS alunos,
       cursos.titulo AS cursos
FROM alunos
JOIN cursos ON alunos.cursos_id = cursos.id
ORDER BY alunos.nome ASC;
```



