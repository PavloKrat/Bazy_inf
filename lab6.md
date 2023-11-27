# lab6

## Zad1

### 1)

```sql
Create table kreatura As(Select * from wikingowie.kreatura);
Create table zasob As(Select * from wikingowie.zasob);
Create table ekwipunek As(Select * from wikingowie.ekwipunek);
```

### 2)

```sql
Select * from zasob;
```
### 3)

```sql
Select * from zasob where rodzaj='jedzenie';
```
### 4)

```sql
Select idZasobu, ilosc from ekwipunek where idKreatury in(1,3,5);
```

## Zad2

### 1)

```sql
Select * from kreatura where udzwig > 50 and rodzaj <>  'wiedzma';
```

### 2)

```sql
Select nazwa from zasob where waga >2 and waga <5;
```

### 3)

```sql
Select nazwa from kreatura where nazwa like '%or%' and udzwig >30 and udzwig<81;
```
jak bedzie udzwig<70 nic sie nie wyswietli
## Zad3

### 1)

```sql
Select nazwa FROM zasob where MONTH(dataPozyskania) in(7,8);
```

### 2)

```sql
Select nazwa FROM zasob where rodzaj IS NOT NULL ORDER BY nazwa ASC;
```

### 3)

```sql
Select nazwa from kreatura ORDER BY dataUR ASC LIMIT 5;
```

## Zad4

### 1)

```sql
Select distinct rodzaj from zasob where rodzaj IS NOT NULL;
```

### 2)

```sql
Select CONCAT(nazwa,'-',rodzaj) AS gatunek from kreatura where rodzaj LIKE 'wi%';
```

### 3)

```sql
Select nazwa,ilosc*waga AS waga_calkowita from zasob where YEAR(dataPozyskania) >2000 and YEAR(dataPozyskania)<2007;
```

## Zad5

### 1)

```sql
Select SUM(waga*0.70) AS masa_wlasciwa,SUM(waga*0.30) AS odpadki from zasob where rodzaj='jedzenie';
```

### 2)

```sql
Select nazwa from zasob where rodzaj IS NULL;
```

### 3)

```sql
Select distinct rodzaj from zasob where nazwa LIKE 'Ba%' or nazwa like '%os' ORDER BY rodzaj ASC;
```
