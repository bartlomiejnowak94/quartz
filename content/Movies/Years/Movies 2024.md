---
cssclasses:
  - cards-cols-8
  - cards-cover
  - cards-2-3
  - cards
---

Obejrzałeś 86 filmów (7 w kinie)

## Rozkład ocen filmów obejrzanych
```
2     ##--------  8
2.5   #---------  6
3     #####----- 19
3.5   ########## 34
4     ##-------- 10
4.5   ##--------  8
5     ----------  1
```

## Ile filmów co miesiąc
```
styczeń      ####------  7
luty         ----------  1
marzec       ######---- 10
kwiecień     ########## 15
maj          ###-------  5
czerwiec     ##--------  3
lipiec       ##--------  4
sierpień     ######---- 10
wrzesień     ####------  7
październik  ###-------  5
listopad     ####------  7
grudzień     ########-- 13
```

## Lista filmów

[[The Chronicles of Narnia The Lion, the Witch and the Wardrobe (2005)]]

```dataview
Table WITHOUT ID cover, file.link, day.text, rating + "⭐"
FROM "4_Listy/41_Movies/Database" and #y2024
FLATTEN file.lists as day
WHERE contains(string(day.text), "2024")
SORT day.text DESC
```

## Ile filmów z danego roku obejrzałem
```
1967   #-------------------  1  
1974   #-------------------  1  
1987   #-------------------  1  
1993   #-------------------  1  
1994   #####---------------  4  
1995   #-------------------  1  
1996   #-------------------  1  
1997   #-------------------  1  
2001   ##------------------  2  
2002   #-------------------  1  
2003   ##------------------  2  
2004   #-------------------  1  
2005   #-------------------  1  
2006   ####----------------  3  
2007   #-------------------  1  
2008   ####----------------  3  
2010   #-------------------  1  
2011   ##------------------  2  
2013   #-------------------  1  
2014   ####----------------  3  
2016   #####---------------  4  
2017   ########------------  6  
2019   ######--------------  5  
2020   #-------------------  1  
2021   ######--------------  5  
2022   ########------------  6  
2023   ################---- 12  
2024   #################### 15
```

## Najczęściej oglądane z krajów:
```
USA           ########## 72
UK            ##-------- 15
Poland        #--------- 10
France        ----------  5
New Zealand   ----------  3
Australia     ----------  2
Canada        ----------  2
Germany       ----------  2
Italy         ----------  2
Japan         ----------  2
```


## Najczęściej oglądane gatunki
```
comedy            ########## 44  
drama             ######---- 30  
adventure         ######---- 28  
fantasy           #####----- 26  
family            #####----- 25  
romance           ####------ 18  
action            ###------- 16  
animation         ###------- 16  
science fiction   ##-------- 12  
thriller          #---------  6
```

## Najczęściej oglądany reżyser
```dataview
Table length(rows.directors) AS ile, rows.file.link
FROM "4_Listy/41_Movies/Database" and #y2024
FLATTEN directors
GROUP BY directors
SORT length(rows.directors) DESC
LIMIT 5
```

## Najczęściej oglądani aktorzy
```dataview
Table length(rows.cast) AS ile, rows.file.link
FROM "4_Listy/41_Movies/Database" and #y2024
FLATTEN cast
GROUP BY cast
SORT length(rows.cast) DESC
LIMIT 5
```
