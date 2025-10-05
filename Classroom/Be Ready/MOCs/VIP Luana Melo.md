---
dg-publish: true
tags:
  - be-ready-classrooms
---
```dataview
TABLE WITHOUT ID
    key AS "Mês",
    map(rows, (r) => link(r.file.path, dateformat(r.data, "cccc, d"))) AS "Data da Aula",
    rows.conteúdo AS "Conteúdo"
FROM #be-ready-classes 
WHERE nome = "VIP Luana Melo"
SORT date DESC
GROUP BY dateformat(data, "MMMM yyyy") as key
SORT key DESC
```
