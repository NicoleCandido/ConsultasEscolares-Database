<h1 align="center">Consultas Escolares</h1>

<p align="center">
  <img src="https://img.shields.io/badge/MySQL-8a2be2?style=for-the-badge&logo=mysql&logoColor=white" />
  <img src="https://img.shields.io/badge/SQL-ff69b4?style=for-the-badge&logo=databricks&logoColor=white" />
  <img src="https://img.shields.io/badge/Status-Concluído-8a2be2?style=for-the-badge" />
</p>

<p align="center">
  Banco de dados de alunos, turmas e notas, criado para praticar relacionamentos entre tabelas,<br>
  chaves estrangeiras, <code>JOIN</code> e subconsultas.
</p>

---

## Estrutura

```
ConsultasEscolares-Database/
├── consultas_escolares.sql   # Script completo do banco
└── README.md
```

## Modelo de dados

```
 Aluno ──┐                ┌── Turma
         │                │
         └──< AlunoTurma >┘      (N:N — um aluno pode estar em várias turmas)
                  │
                  └──< Nota      (cada nota pertence a um aluno matriculado na turma)
```

| Tabela       | Campos principais                                   |
| :----------- | :-------------------------------------------------- |
| `Aluno`      | `id` (PK), `nome`, `email`, `data_nascimento`        |
| `Turma`      | `id` (PK), `inicio`, `fim`, `observacoes`            |
| `AlunoTurma` | `aluno_id` + `turma_id` (PK composta, FKs)           |
| `Nota`       | `id` (PK), `aluno_id`, `turma_id` (FK), `nota`       |

## O que o script pratica

- Chaves primárias simples e **compostas**
- Chaves estrangeiras e relacionamento **N:N** com tabela associativa
- `JOIN` entre várias tabelas
- **Subconsulta correlacionada** no `WHERE` (notas acima da média da turma)
- **Subconsulta no `SELECT`** (maior nota de cada turma)
- Funções de agregação: `AVG` e `MAX`
