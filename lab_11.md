# Zadania lab_11
## Zadanie 1
```
CREATE TABLE student(
id_studenta INT UNSIGNED PRIMARY KEY AUTO_INCREMENT,
imie VARCHAR(100) NOT NULL,
nazwisko VARCHAR(100) NOT NULL,
rok_studiow INT UNSIGNED,
data_urodzenia DATE
);
```
## Zadanie 2
```
CREATE TABLE kierunek(
id_kierunku INT UNSIGNED PRIMARY KEY AUTO_INCREMENT,
nazwa_kierunku VARCHAR(200) NOT NULL
);
```
## Zadanie 3
```
CREATE TABLE student_na_kierunku(
	student INT UNSIGNED,
	kierunek INT UNSIGNED,
PRIMARY KEY(student, kierunek),
FOREIGN KEY (student) REFERENCES student(id_studenta),
FOREIGN KEY (kierunek) REFERENCES kierunek(id_kierunku)
);
```
## Zadanie 4
```
CREATE TABLE przedmiot(
id_przedmiotu INT PRIMARY KEY AUTO_INCREMENT,
nazwa_przedmiotu VARCHAR(200) NOT NULL,
opis LONGTEXT
);

```
## Zadanie 5
```
CREATE TABLE kierunek_has_przedmioty(
kierunek INT UNSIGNED,
przedmiot INT,
obowiazkowy BOOLEAN DEFAULT true,
PRIMARY KEY(kierunek, przedmiot),
FOREIGN KEY (kierunek) REFERENCES kierunek(id_kierunku),
FOREIGN KEY (przedmiot) REFERENCES przedmiot(id_przedmiotu)
);
```
## Zadanie 6
```
INSERT INTO student VALUES(1, "Jan", "Kowalski", 2, "2000-01-03");
INSERT INTO student VALUES(2, "Zbigniew", "Nowak", 3, "1999-03-04");
INSERT INTO student VALUES(3, "Karol", "Rybicki", 2, "2000-07-20");
INSERT INTO student VALUES(4, "Mateusz", "Grala", 1, "2001-09-23");

INSERT INTO kierunek VALUES(1, "Informatyka");
INSERT INTO kierunek VALUES(2, "Mechatronika");

INSERT INTO przedmiot VALUES(1, "matematyka", "obowiązkowy");
INSERT INTO przedmiot VALUES(2, "j. angielski", "obowiązkowy");
INSERT INTO przedmiot VALUES(3, "filozofia", "obowiązkowy");
INSERT INTO przedmiot VALUES(4, "chemia", "nieobowiązkowy");
```
## Zadanie 7
```
ALTER TABLE przedmiot MODIFY opis VARCHAR(100) DEFAULT "Brak opisu";
```
## Zadanie 8
```
ALTER TABLE student ADD indeks INT NOT NULL;
ALTER TABLE student_na_kierunku DROP FOREIGN KEY student_na_kierunku_ibfk_1;
ALTER TABLE student MODIFY id_studenta INT UNSIGNED;
ALTER TABLE student  DROP PRIMARY KEY;
ALTER TABLE student  ADD PRIMARY KEY(indeks);
```
## Zadanie 9
```
ALTER TABLE kierunek_has_przedmioty ADD semestr TEXT NOT NULL;
UPDATE kierunek_has_przedmioty SET semestr = "2024Z";
ALTER TABLE kierunek_has_przedmioty ADD rok_studiow INT UNSIGNED NOT NULL;
UPDATE kierunek_has_przedmioty SET rok_studiow = "2";
```
## Zadanie 10
```
```
