---
dg-publish: true
---
```dataview
TABLE WITHOUT ID
    data AS "Data da Aula",
    link(file.path, conteúdo) AS "Conteúdo Ministrado",
    nome AS "Turma"
FROM #be-ready-classes 
WHERE contains(Alunos, "Jessica")
SORT data DESC
```