# Lab7

## Zad1

### 1)
```sql
SELECT AVG(waga) as srednia_waga FROM kreatura WHERE rodzaj="wiking";
```

### 2)
```sql
SELECT rodzaj, AVG(waga) as srednia_waga, COUNT(waga) as liczba FROM kreatura GROUP BY rodzaj;
```

### 3)
```sql
SELECT rodzaj, AVG(2022-YEAR(dataUr)) as lat FROM kreatura GROUP BY rodzaj;
```

## Zad2

### 1)
```sql
SELECT rodzaj, SUM(waga) as suma_wag FROM zasob GROUP BY rodzaj;
```

### 2)
```sql
SELECT nazwa, AVG(waga) as suma_wag FROM zasob WHERE ilosc>=4 GROUP BY nazwa HAVING SUM(waga) > 10;
```

### 3)
```sql
SELECT rodzaj, COUNT(*) as liczba_nazw FROM (SELECT nazwa, rodzaj, COUNT(*) as liczba_nazw FROM zasob WHERE ilosc > 1 GROUP BY rodzaj, nazwa) as tab GROUP BY rodzaj HAVING liczba_nazw > 1;
```

## Zad3

### 1)
```sql
SELECT kreatura.nazwa, SUM(ekwipunek.ilosc) as ilosc FROM ekwipunek, kreatura WHERE kreatura.idKreatury=ekwipunek.idkreatury GROUP BY ekwipunek.idKreatury;
```

### 2)
```sql
SELECT k.nazwa, GROUP_CONCAT(z.nazwa) FROM kreatura as k, zasob as z, ekwipunek as e WHERE k.idKreatury=e.idKreatury AND z.idZasobu=e.idZasobu GROUP BY k.nazwa;
```

### 3)
```sql
SELECT idKreatury FROM kreatura WHERE idKreatury NOT IN (SELECT idKreatury FROM ekwipunek WHERE idKreatury IS NOT NULL GROUP BY idKreatury);
```

##Zad4

### 1)
```sql
SELECT kreatura.nazwa, zasob.nazwa FROM kreatura JOIN ekwipunek ON kreatura.idKreatury=ekwipunek.idKreatury JOIN zasob ON ekwipunek.idZasobu=zasob.idZasobu WHERE kreatura.rodzaj="wiking" AND YEAR(kreatura.dataUr) BETWEEN 1670 AND 1679;
```

### 2)
```sql
SELECT kreatura.nazwa FROM ekwipunek JOIN zasob ON ekwipunek.idZasobu=zasob.idZasobu JOIN kreatura ON kreatura.idKreatury=ekwipunek.idKreatury WHERE zasob.rodzaj="jedzenie" ORDER BY kreatura.dataUr DESC LIMIT 5;
```

### 3)
```sql
SELECT kreatura1.nazwa, kreatura2.nazwa FROM kreatura kreatura1 JOIN kreatura kreatura2 ON kreatura1.idKreatury=kreatura2.idKreatury-5;
```

## Zad5

### 1)
```sql
SELECT kreatura.rodzaj, avg(zasob.waga) as waga FROM kreatura JOIN ekwipunek ON kreatura.idKreatury=ekwipunek.idKreatury JOIN zasob ON zasob.idZasobu=ekwipunek.idZasobu WHERE kreatura.rodzaj NOT IN ("malpa","waz") AND ekwipunek.ilosc<30 GROUP  BY kreatura.rodzaj;
```

### 2)
```sql
SELECT test.rodzaj, GROUP_CONCAT(test.najstarsza_najmlodsza SEPARATOR " ") as najstarsza_najmlodsza, GROUP_CONCAT(test.nazwa SEPARATOR " ") as najstarsza_najmlodsza_nazwa FROM (SELECT kreatura.nazwa, najstarszeTAB.rodzaj, najstarsza as najstarsza_najmlodsza FROM kreatura, (SELECT kreatura.idKreatury, kreatura.rodzaj, MIN(kreatura.dataUr) as najstarsza, MAX(kreatura.dataUr) as najmlodsza FROM kreatura GROUP BY kreatura.rodzaj) as najstarszeTAB WHERE kreatura.dataUr=najstarszeTAB.najstarsza UNION ALL  
SELECT kreatura.nazwa, najmlodszeTAB.rodzaj, najmlodsza FROM kreatura, (SELECT kreatura.idKreatury, kreatura.rodzaj, MIN(kreatura.dataUr) as najstarsza, MAX(kreatura.dataUr) as najmlodsza FROM kreatura GROUP BY kreatura.rodzaj) as najmlodszeTAB WHERE kreatura.dataUr=najmlodszeTAB.najmlodsza ORDER BY rodzaj, najstarsza_najmlodsza) as test GROUP BY test.rodzaj;
```

