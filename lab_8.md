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
SELECT w.nazwa, COUNT(u.id_wyprawy) AS liczba_uczestnikow, GROUP_CONCAT(k.nazwa) AS nazwy_uczestnikow
FROM wyprawa w
JOIN uczestnicy u ON w.id = u.id_wyprawy
JOIN kreatura k ON u.id_kreatury = k.id
GROUP BY w.id, w.nazwa;

```

### 2
```sql
SELECT w.nazwa AS nazwa_wyprawy, e.numer AS numer_etapu, s.nazwa AS nazwa_sektora, k.nazwa AS nazwa_kierownika
FROM wyprawa w
JOIN etapy_wyprawy e ON w.id = e.id_wyprawy
JOIN sektor s ON e.id_sektora = s.id
JOIN kreatura k ON e.id_uczestnika = k.id
WHERE e.id_uczestnika = w.id_kierownika
ORDER BY w.data_poczatku, e.numer;

```

## Zad3

### 1
```sql

```

### 2
```sql
Select k.nazwa, if(count(u.id_wyprawy)=0, 'nie brał','brał') as czy_wyprawa from kreatura k left join uczestnicy u on u.id_uczestnika=k.idKreatury group by k.nazwa;
```

## Zad4

### 1
```sql
select idWyprawy, sum(length(dziennik)) from etapy_wyprawy group by idWyprawy having sum(length(dziennik))<400;
```

### 2
```sql

```

## Zad5

### 1
```sql

```

