# Comandos SQL

### Criando o Banco de Dados

```sql
CREATE DATABASE tecinternet_escola_joaopedro CHARACTER SET utf8mb4;
```

### Criando as tabelas

```sql
CREATE TABLE cursos(
    id INT NOT NULL PRIMARY KEY AUTO_INCREMENT,
    titulo VARCHAR(45) NOT NULL,
    carga_horaria INT NOT NULL,
    professores_id INT NULL
);
```

```sql
CREATE TABLE alunos(
    id INT NOT NULL PRIMARY KEY AUTO_INCREMENT,
    nome VARCHAR(45) NOT NULL,
    data_de_nacimento DATE NOT NULL,
    primeira_nota DECIMAL(4,2) NOT NULL,
    segunda_nota DECIMAL(4,2) NOT NULL,
    cursos_id INT NOT NULL
);
```

```sql
CREATE TABLE professores(
    id INT NOT NULL PRIMARY KEY AUTO_INCREMENT,
    nome VARCHAR(45) NOT NULL,
    area_de_atuacao ENUM('design', 'desenvolvimento', 'infra') NOT NULL,
    cursos_id INT NOT NULL
);
```

### Criando os relacionamentos entre as tabelas

```sql
ALTER TABLE alunos
    ADD CONSTRAINT fk_alunos_cursos
    FOREIGN KEY (cursos_id) REFERENCES cursos(id);
```

```sql
ALTER TABLE professores
    ADD CONSTRAINT fk_professores_cursos
    FOREIGN KEY (cursos_id) REFERENCES cursos(id);
```

```sql
ALTER TABLE cursos
    ADD CONSTRAINT fk_cursos_professores
    FOREIGN KEY (professores_id) REFERENCES professores(id);
```