---
dg-publish: true
tags:
  - be-ready-classrooms
---
## New York
```dataview
TABLE WITHOUT ID
    dateformat(rows[0].date, "MMMM yyyy") AS "Mês",
    map(rows, (r) => link(r.file.path, dateformat(r.date, "d, cccc"))) AS "Data da Aula",
    rows.conteúdo AS "Conteúdo"
FROM #be-ready-classes
WHERE title = "New York Classroom"
SORT date DESC
GROUP BY dateformat(date, "yyyy-MM")
SORT key DESC
```
```dataview
TABLE WITHOUT ID
    link(file.path,dateformat(date, "cccc, MMMM d")) AS "Data",
    Alunos AS "Alunos Presentes"
FROM #be-ready-classes 
WHERE title="New York Classroom"
SORT date DESC
```

```dataview
TABLE WITHOUT ID
link(Aluno) AS "Alunos"
FROM #be-ready-classes 
WHERE title="New York Classroom"
FLATTEN Alunos as Aluno
GROUP BY Aluno
SORT Aluno ASC
```