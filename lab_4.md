# Zadania lab 4 

## Zadanie 3
1. 
```
CREATE TABLE izba (
	adres_budynku VARCHAR(50),
	nazwa_izby VARCHAR(30),
	metraz SMALLINT UNSIGNED,
	wlasciciel INT,
  PRIMARY KEY (adres_budynku, nazwa_izby),
  FOREIGN KEY (wlasciciel) REFERENCES postac(id_postaci) ON DELETE SET NULL
);
```
2.
```
  ALTER TABLE izba ADD kolor VARCHAR(30) AFTER metraz DEFAULT 'czarny';
```
3.
```
INSERT INTO izba VALUES
('Sloneczna 54', 'spizarnia', 5, 'niebieski',  2);
```
## Zadanie 4

1. 
```
CREATE TABLE przetwory (
	id_przetworu INT PRIMARY KEY,
	rok_produkcji INT,
	id_wykonawcy INT,
	zawartosc VARCHAR(50),
    dodatek VARCHAR(50) default 'papryczka chilli',
    id_konsumenta INT,
    FOREIGN KEY (id_konsumenta) REFERENCES postac(id_postaci)
);
```
2.
```
INSERT INTO przetwory VALUES( 1, 2022, 3, 'bigos', default, default);
```

## Zadanie 5
1. 
```
INSERT INTO postac values 
(default, 'Wiking 1', 'wiking', '1900-01-02', 224),
(default, 'Wiking 2', 'wiking', '1901-01-02', 223),
(default, 'Wiking 3', 'wiking', '1902-01-02', 222),
(default, 'Wiking 4', 'wiking', '1903-01-02', 221),
(default, 'Wiking 5', 'wiking', '1904-01-02', 220);
```
2.
```
CREATE TABLE statek(
	nazwa_statku VARCHAR(20) PRIMARY KEY,
    rodzaj_statku ENUM('wiosłowe', 'żaglowe', 'mechaniczne'),
    data_wodowania DATE,
    max_ladownosc INT UNSIGNED);
```
3.
```
INSERT INTO statek VALUES('kajak', 'wiosłowe', '2024-11-30', 1);
```
4.
```
ALTER TABLE postac ADD funkcja VARCHAR(50);
```
5.
```
UPDATE `postac` SET `funkcja` = 'kapitan' WHERE (`nazwa` = 'Bjorn');
```
6.
```
ALTER TABLE postac ADD FOREIGN KEY(id_postaci) REFERENCES statek(nazwa_statku);
```
7.
```
```
8.
```
DELETE FROM izba WHERE (`nazwa_izby` = 'spizarnia');
```
9.
```
DROP TABLE izba;
```
