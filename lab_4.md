# Lab 4


## Zad1

```sql
CREATE TABLE postac (id_postaci INT AUTO_INCREMENT PRIMARY KEY, nazwa VARCHAR(40) NOT NULL, rodzaj ENUM('wiking','ptak','kobieta'), data_ur DATE, wiek INT UNSIGNED);
INSERT INTO postac VALUES (default,'Bjorn','wiking','1657-10-28',300);
INSERT INTO postac VALUES (default,'Drozd','ptak','1843-05-12',200);
INSERT INTO postac VALUES (default,'Tesciowa','kobieta','1949',83);
UPDATE postac SET wiek=88 WHERE id_postaci=3;
```

## Zad2

```sql
CREATE TABLE walizka (id_walizki INT AUTO_INCREMENT PRIMARY KEY, pojemnosc INT UNSIGNED, kolor ENUM('rozowy','czerwony','teczowy','zolty'), id_wlasciciela INT, FOREIGN KEY (id_wlasciciela) REFERENCES postac(id_postaci) ON DELETE CASDADE);
ALTER TABLE walizka ALTER KOLOR SET default 'rozowy';
INSERT INTO walizka VALUES (default, 50, 'zolty', 1);
INSERT INTO walizka VALUES (default, 500, 'rozowy', 3);
```

## Zad3

```sql
CREATE TABLE izba (adres_budynku VARCHAR(40), nazwa_izby VARCHAR(40), PRIMARY KEY(adres_budynku, nazwa_izby), metraz INT UNSIGNED, wlasciciel INT, FOREIGN KEY (wlasciciel) REFERENCES postac (id_postaci) ON DELETE SET NULL);
ALTER TABLE izba ADD kolor enum('rozowy') AFTER metraz;
INSERT INTO izba VALUES ('144', 'spiżarnia', 25, 'rozowy', 1);
```

## Zad4


```sql
CREATE TABLE przetwory (id_przetworu INT PRIMARY KEY, rok_produkcji INT default '1654', id_wykonawcy INT, zawartosc VARCHAR(255), dodatek VARCHAR(255) default 'papryczka chilli', id_konsumenta INT, FOREIGN KEY (id_wykonawcy) REFERENCES postac(id_postaci), FOREIGN KEY (id_konsumenta) REFERENCES postac(id_postaci));
INSERT INTO przetwory VALUES (1, 1700, 1, 'bigos', default, 3);
```

## Zad5

```sql
INSERT INTO postac values
(default, 'Agart', 'wiking', '1678-08-12', 340),
(default, 'Orakl', 'wiking', '1654-08-12', 380),
(default, 'Thor', 'wiking', '1667-08-12', 349),
(default, 'Okhord', 'wiking', '1767-08-12', 230),
(default, 'Anko', 'wiking', '1867-08-12', 140)
;
create table statek(nazwa_staku VARCHAR(40) PRIMARY KEY, 
rodzaj_statku ENUM('pasazerkie', 'wojenne', 'handlowe'),
data_wodowania DATE,
max_ladownosc INT UNSIGNED);
INSERT INTO statek values 
('Titanic', 'pasazerkie', '1837-10-06', 3000),
('Santa Maria', 'wojenne', '1628-03-23', 150)
;
select * from statek;
select * from postac;
select * from izba;
ALTER TABLE postac ADD COLUMN funkcja VARCHAR(40) DEFAULT NULL;
UPDATE postac set funkcja='kapitan' where nazwa='Bjorn';
ALTER TABLE postac ADD COLUMN statek VARCHAR(40) DEFAULT NULL;
ALTER TABLE postac ADD FOREIGN KEY (statek) REFERENCES statek(nazwa_staku) ON DELETE SET NULL;
ALTER TABLE postac DROP FOREIGN KEY postac_ibfk_1;
ALTER TABLE statek change nazwa_staku nazwa_statku VARCHAR(40);
ALTER TABLE postac ADD FOREIGN KEY (statek) REFERENCES statek(nazwa_statku) ON DELETE SET NULL;
UPDATE postac SET statek = 'Santa Maria' WHERE id_postaci= 8;
UPDATE postac SET statek = 'Titanic' WHERE id_postaci= 2;
DELETE FROM izba WHERE adres_budynku=144;
DROP TABLE izba;
```
