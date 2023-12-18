# Lab8

## Zad1

### 1
```sql
Insert into kreatura Select * from wikingowie.kreatura;
create table etapy_wyprawy as select * from wikingowie.etapy_wyprawy;
create table sektor as select * from wikingowie.sektor;
create table uczestnicy as select * from wikingowie.uczestnicy;
create table wyprawa as select * from wikingowie.wyprawa;
```

### 2
```sql
Select nazwa from kreatura where idKreatury not in (Select id_wyprawy from wyprawa);
```

### 3
```sql
Select w.nazwa, Sum(ekwipunek.ilosc) As suma_ekwipunku from wyprawa w join uczestnicy u
ON w.id_wyprawy = u.id_wyprawy join etapy_wyprawy e on u.id_wyprawy = e.id_uczestnika group by w.nazwa, w.id_wyprawy;
```

## Zad2

### 1
```sql

```

### 2
```sql

```

## Zad3

### 1
```sql

```

### 2
```sql

```

## Zad4

### 1
```sql

```

### 2
```sql

```

## Zad5

### 1
```sql

```

