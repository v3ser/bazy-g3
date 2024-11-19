# ZADANIA LAB 4

## Zadanie 1
a) 
```
DELETE from postac where id_postaci = 5;
DELETE from postac where id_postaci = 4;
```
b)

```
ALTER TABLE walizka DROP FOREIGN KEY walizka_ibfk_1;
ALTER TABLE izba DROP FOREIGN KEY izba_ibfk_1;
ALTER TABLE przetwory DROP FOREIGN KEY przetwory_ibfk_1;
ALTER TABLE postac modify id_postaci INT;
ALTER TABLE postac DROP PRIMARY KEY;
```

## Zadanie 2 
a)
```
ALTER TABLE postac add pesel CHAR(11);
UPDATE postac set pesel="12345678919" where nazwa="Wiking 5";
ALTER TABLE postac ADD PRIMARY KEY(pesel);
```
b)
```
ALTER TABLE postac modify   `rodzaj` enum('wiking','ptak','kobieta','syrena');
```
c)
```
INSERT INTO postac VALUES ("12345678921" ,10, "Gertruda Nieszczera", "syrena", "2000-01-01", 24, NULL);
```
## Zadanie 3
a)
```
update postac set nazwa_statku="kajak" where nazwa like "%a%";
```
b)
```
update statek set max_ladownosc= max_ladownosc * 0.7;
```
c)
```
alter table postac add check (wiek<=1000);
```
## Zadanie 4
a)
```
ALTER TABLE postac modify   `rodzaj` enum('wiking','ptak','kobieta','syrena','wąż');

INSERT INTO postac VALUES ("12345678922" ,11, "Loko", "wąż", "2010-01-01", 14, NULL);
```

b)
```
create table marynarz like postac;
insert into marynarz select * from postac where statek is not null;
```
c)
```
```

## Zadanie 5

a) 
```
ALTER TABLE postac DROP FOREIGN KEY id_postaci;
```
b)
```
DELETE FROM postac WHERE nazwa = 'Wiking1'
```
c)
```
```
d)
```
DROP TABLE statek;
```
e)
```
CREATE TABLE zwierz(
	id INT PRIMARY KEY AUTO INCREMENT,
  nazwa VARCHAR(50),
  wiek INT);
```
