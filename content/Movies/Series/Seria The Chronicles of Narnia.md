---
cssclasses:
  - cards
  - cards-2-3
  - cards-cols-6
  - cards-cover
---

```dataview
TABLE WITHOUT ID
cover, nr_seri, rating + "⭐"
FROM "4_Listy/41_Movies/Database"
WHERE seria_movie = link(this.file.name)
SORT number(nr_seri)
```
