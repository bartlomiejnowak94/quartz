---
cssclasses:
  - cards
  - cards-cover
  - cards-2-3
  - cards-cols-8
---

Obejrzałeś `$= dv.pages('"4_Listy/41_Movies/Database" and #y2025').length` (`$= dv.pages('"4_Listy/41_Movies/Database" and #y2025').file.etags.where(p => p == "#kino/2025").length` w kinie)

## Rozkład ocen filmów obejrzanych
```dataviewjs
const pages = dv.pages('"4_Listy/41_Movies/Database" and #y2025')
.where(p => p.rating)
.groupBy(p => p.rating)
.map(p => `${p.key},${p.rows.length}`)
dv.span(["~~~tinychart", ...pages, "~~~"].join("\n"))
```

## Ile co miesiąc
```dataviewjs
const pages = dv.pages('"4_Listy/41_Movies/Database" and #y2025')
.file.lists.text
.map(p => p.toString().substring(2, 9))
.where(p => p.substring(0, 4) == 2025)
.map(p => p.substring(5,7)).groupBy(t => t)
.map(p => `${p.key},${p.rows.length}`);
dv.span(["~~~tinychart", ...pages, "~~~"].join("\n"))
```

## Ile w dany dzień tygodnia
```dataviewjs
const pages = dv.pages('"4_Listy/41_Movies/Database" and #y2025')
.file.lists.text
.map(p => p.toString().substring(2, 15))
.where(p => p.substring(0, 4) == 2025)
.map(p => p.substring(11,13)).groupBy(t => t)
.map(p => `${p.key},${p.rows.length}`);
dv.span(["~~~tinychart",...pages, "~~~"].join("\n"))
```

## Lista filmów
```dataview
Table WITHOUT ID cover, file.link, day.text, rating + "⭐"
FROM "4_Listy/41_Movies/Database" and #y2025
FLATTEN file.lists as day
WHERE contains(string(day.text), "2025")
SORT day.text DESC
```

## Ile filmów z danego roku obejrzałem
```dataviewjs
const pages = dv.pages('"4_Listy/41_Movies/Database" and #y2025')
.where(p => p.rating)
.groupBy(p => p.year)
.map(p => `${p.key},${p.rows.length}`)
dv.span(["~~~tinychart", ...pages, "~~~"].join("\n"))
```

## Najczęściej oglądane z krajów:
```dataviewjs
const pages = dv.pages('"4_Listy/41_Movies/Database" and #y2025')
.countries
.groupBy(t => t)
.sort(p => p.rows.length, "desc")
.map(p => `${p.key.path},${p.rows.length}`).limit(10)
dv.span(["~~~tinychart", ...pages, "~~~"].join("\n"))
```

## Najczęściej oglądane gatunki
```dataviewjs
const pages = dv.pages('"4_Listy/41_Movies/Database" and #y2025')
.genres
.groupBy(t => t)
.sort(p => p.rows.length, "desc")
.map(p => `${p.key.path},${p.rows.length}`).limit(10)
dv.span(["~~~tinychart", ...pages, "~~~"].join("\n"))
```

## Najczęściej oglądany reżyser
```dataview
Table length(rows.directors) AS ile, rows.file.link
FROM "4_Listy/41_Movies/Database" and #y2025
FLATTEN directors
GROUP BY directors
SORT length(rows.directors) DESC
LIMIT 5
```

## Najczęściej oglądani aktorzy
```dataview
Table length(rows.cast) AS ile, rows.file.link
FROM "4_Listy/41_Movies/Database" and #y2025
FLATTEN cast
GROUP BY cast
SORT length(rows.cast) DESC
LIMIT 5
```
