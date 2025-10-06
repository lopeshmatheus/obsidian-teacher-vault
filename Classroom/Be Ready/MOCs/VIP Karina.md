---
tags:
  - be-ready-classrooms
dg-publish: true
---
```dataview
TABLE WITHOUT ID
    dateformat(rows[0].date, "MMMM yyyy") AS "Mês",
    map(rows, (r) => link(r.file.path, dateformat(r.date, "cccc, d"))) AS "Data da Aula",
    rows.conteúdo AS "Conteúdo"
FROM #be-ready-classes
WHERE title = "VIP Karina"
SORT date DESC
GROUP BY dateformat(date, "yyyy-MM")
SORT key DESC
```