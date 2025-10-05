---
dg-publish: true
tags:
  - be-ready-classrooms
---
## New York
```dataview
TABLE WITHOUT ID
    key AS "Mês",
    map(rows, (r) => link(r.file.path, dateformat(date(r.data), "d, cccc"))) AS "Data da Aula",
    rows.conteúdo AS "Conteúdo"
FROM #be-ready-classes 
WHERE nome = "New York Classroom"
SORT data DESC
GROUP BY dateformat(data, "MMMM yyyy") as key
SORT key DESC
```
```dataview
TABLE WITHOUT ID
    link(file.path,dateformat(data, "cccc, MMMM d")) AS "Data",
    Alunos AS "Alunos Presentes"
FROM #be-ready-classes 
WHERE nome="New York Classroom"
SORT data DESC
```

```dataview
TABLE WITHOUT ID
link(Aluno) AS "Alunos"
FROM #be-ready-classes 
WHERE nome="New York Classroom"
FLATTEN Alunos as Aluno
GROUP BY Aluno
SORT Aluno ASC
```