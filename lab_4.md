# Lab 4
## Poziom 2
###### Poziom 6

Lista zadań do wykonania:
* todo 1
* todo 2
  * todo 2.1

 1. Rozdiał 1
 2. Rozdiał 2
    2.1 Rodział 2.1

**Listing 1** -> pogrubinie
_Listing 2_ -> kursywa

**_Listing 3_**

Poniżej to blok kodu.
```sql
CREATE TABLE postac (id_postaci INT AUTO_INCREMENT PRIMARY KEY, nazwa VARCHAR(40) NOT NULL, rodzaj ENUM('wiking','ptak','kobieta'), data_ur DATE, wiek INT UNSIGNED);
INSERT INTO postac VALUES (default,'Bjorn','wiking','1657-10-28',300);
INSERT INTO postac VALUES (default,'Drozd','ptak','1843-05-12',200);
INSERT INTO postac VALUES (default,'Tesciowa','kobieta','1949',83);
UPDATE postac SET wiek=88 WHERE id_postaci=3;
CREATE TABLE walizka (id_walizki INT AUTO_INCREMENT PRIMARY KEY, pojemnosc INT UNSIGNED, kolor ENUM('rozowy','czerwony','teczowy','zolty'), id_wlasciciela INT, FOREIGN KEY (id_wlasciciela) REFERENCES postac(id_postaci) ON DELETE CASDADE);
ALTER TABLE walizka ALTER KOLOR SET default 'rozowy';
INSERT INTO walizka VALUES (default, 50, 'zolty', 1);
INSERT INTO walizka VALUES (default, 500, 'rozowy', 3);
CREATE TABLE izba (adres_budynku VARCHAR(40), nazwa_izby VARCHAR(40), PRIMARY KEY(adres_budynku, nazwa_izby), metraz INT UNSIGNED, wlasciciel INT, FOREIGN KEY (wlasciciel) REFERENCES postac (id_postaci) ON DELETE SET NULL);
ALTER TABLE izba ADD kolor enum('rozowy') AFTER metraz;
INSERT INTO izba VALUES ('144', 'spiżarnia', 25, 'rozowy', 1);
CREATE TABLE przetwory (id_przetworu INT PRIMARY KEY, rok_produkcji INT default '1654', id_wykonawcy INT, zawartosc VARCHAR(255), dodatek VARCHAR(255) default 'papryczka chilli', id_konsumenta INT, FOREIGN KEY (id_wykonawcy) REFERENCES postac(id_postaci), FOREIGN KEY (id_konsumenta) REFERENCES postac(id_postaci));
INSERT INTO przetwory VALUES (1, 1700, 1, 'bigos', default, 3);



```
Kod umieszczany liniowo. Polecenie `SELECT` oznacza wybranie danych z bazy.
