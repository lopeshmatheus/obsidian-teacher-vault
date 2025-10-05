---
dg-publish: true
---
```dataview
TABLE WITHOUT ID
    data AS "Data da Aula",
    link(file.path, conteúdo) AS "Conteúdo Ministrado",
    material AS "Material",
    nivel AS "Nivel"
    
FROM #be-ready-classes 
WHERE contains(Alunos, "Rafael")
SORT data DESC
```
