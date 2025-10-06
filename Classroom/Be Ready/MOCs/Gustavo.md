---
dg-publish: true
---
```dataview
TABLE WITHOUT ID
    date AS "Data da Aula",
    link(file.path, conteúdo) AS "Conteúdo Ministrado",
    title AS "Turma"
FROM #be-ready-classes 
WHERE contains(Alunos, "Gustavo")
SORT data DESC
```