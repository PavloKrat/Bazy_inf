#Lab5

##Zad1

###a)

```sql
DELETE FROM postac WHERE (rodzaj='wiking' AND wiek>348) AND nazwa NOT LIKE 'Bjorn';
```

###b)

```sql
ALTER TABLE walizka DROP CONSTRAINT walizka_ibfk_1;
ALTER TABLE przetwory DROP CONSTRAINT przetwory_ibfk_1;
ALTER TABLE przetwory DROP CONSTRAINT przetwory_ibfk_2;
ALTER TABLE postac MODIFY id_postaci int;
ALTER TABLE postac DROP PRIMARY KEY;
```

##Zad2

###a)

```sql
ALTER TABLE postac ADD COLUMN pesel VARCHAR(11) first;
UPDATE postac SET pesel='73042676159' WHERE nazwa='Bjorn';
UPDATE postac SET pesel='98032175728' WHERE nazwa='Drozd';
UPDATE postac SET pesel='02271128717' WHERE nazwa='Tesciowa';
UPDATE postac SET pesel='73080259383' WHERE nazwa='Agart';
UPDATE postac SET pesel='96012974918' WHERE nazwa='Okhord';
UPDATE postac SET pesel='50120451455' WHERE nazwa='Anko';
```

###b)

```sql
ALTER TABLE postac CHANGE COLUMN rodzaj rodzaj ENUM('wiking', 'ptak', 'kobieta', 'serena') NULL DEFAULT NULL ;
```

###c)

```sql
INSERT INTO postac(id_postaci,pesel,nazwa,rodzaj,wiek) VALUES(9,'49013028735','Gertruda Nieszczera','syrena',150);
```

##Zad3

###a)

```sql
UPDATE postac SET statek='Titanic' WHERE nazwa LIKE '%a%';
```

###b)

```sql
UPDATE statek SET data_wodowania='2001-09-01' WHERE nazwa_statku='Titanic';
UPDATE statek SET max_ladownosc=max_ladownosc*0.70 WHERE data_wodowania>='2000-01-01';
```

###c)

```sql
ALTER TABLE postac ADD CHECK(wiek<=1000);
```

##Zad4

###a)

```sql
INSERT INTO postac(id_postaci,pesel,nazwa,wiek) VALUES(10,'85062023451','Loko',500);
```

###b)

```sql
CREATE TABLE marynarz AS(SELECT*FROM postac WHERE statek IS NOT NULL);
```

###c)

```sql
ALTER TABLE marynarz ADD PRIMARY KEY (pesel);
ALTER TABLE marynarz ADD FOREIGN KEY (statek) REFERENCES statek(nazwa_statku);
```

##Zad5

###a)

```sql
UPDATE marynarz SET statek=null WHERE statek IS NOT NULL;
```

###b)

```sql
DELETE FROM marynarz WHERE rodzaj='wiking' AND id_postaci=8;
```

###c)

```sql
DELETE FROM statek;
```

###d)

```sql
ALTER TABLE marynarz DROP CONSTRAINT marynarz_ibfk_1;
DROP TABLE statek;
```

###e)

```sql
CREATE TABLE zwierz(id INT PRIMARY KEY AUTO_INCREMENT, nazta VARCHAR(30), wiek INT);
```

###f)

```sql
UPDATE postac SET funkcja='zwierzak' WHERE nazwa='Drozd' OR nazwa='LOKO';
INSERT INTO zwierz SELECT id_postaci,nazwa,wiek FROM postac WHERE funkcja='zwierzak';
```
