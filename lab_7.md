# Zadania lab_7
## Zadanie 1
1.
```
DELIMITER $$
CREATE TRIGGER sprawdzenie_wagi1
BEFORE INSERT ON kreatura
FOR EACH ROW
BEGIN
    IF NEW.waga <= 0 THEN
        SIGNAL SQLSTATE '45000'
            SET MESSAGE_TEXT = 'Waga musi być większa od zera!';
    END IF;
END$$
DELIMITER ;


DELIMITER $$
CREATE TRIGGER sprawdzenie_wagi2
BEFORE UPDATE ON kreatura
FOR EACH ROW
BEGIN
    IF NEW.waga <= 0 THEN
        SIGNAL SQLSTATE '45001'
            SET MESSAGE_TEXT = 'Waga musi być większa od zera!';
    END IF;
END$$
DELIMITER ;
```
## Zadanie 2
```
DELIMITER //
CREATE TRIGGER po_usunieciu 
AFTER DELETE ON wyprawa
FOR EACH ROW 
BEGIN
	DECLARE nazwa_kierownika varchar(255);
	SELECT nazwa INTO nazwa_kierownika
	FROM kreatura
    WHERE idKreatury = old.id_wyprawy;
    INSERT INTO archiwum_wypraw (id_wyprawy, nazwa, data_rozpoczecia, data_zakonczenia, kierownik)
    VALUES (old.id_wyprawy, old.nazwa, old.data_rozpoczecia, old.data_zakonczenia, nazwa_kierownika);
END //
DELIMITER ;
```
## Zadanie 3
1.
```
DELIMITER $$
CREATE PROCEDURE eliksir_sily(IN p_idKreatury INT)
BEGIN
    UPDATE kreatura
    SET udzwig = udzwig * 1.2
    WHERE idKreatury = p_idKreatury;
END$$
DELIMITER ;
```
2.
```
CREATE FUNCTION duze_litery(tekst VARCHAR(255))
RETURNS VARCHAR(255)
DETERMINISTIC
BEGIN
    RETURN UPPER(tekst);
END$$
DELIMITER ;
```
## Zadanie 4
1.
```
CREATE TABLE system_alarmowy (
	id_alarmu INT,
    wiadomosc VARCHAR(255));
```
2.
```
```
## Zadanie 5
1.
```
CREATE PROCEDURE oblicz_udzwig(
    OUT srednia_udzwigu DECIMAL(10, 2),
    OUT suma_udzwigu DECIMAL(10, 2),
    OUT max_udzwigu DECIMAL(10, 2)
)
BEGIN
    SELECT 
        AVG(udzwig), 
        SUM(udzwig), 
        MAX(udzwig)
    INTO 
        srednia_udzwigu, 
        suma_udzwigu, 
        max_udzwigu
    FROM kreatura;
END$$
```
2.
```
CREATE PROCEDURE sektory_wyprawy(
    IN p_idWyprawy INT
)
BEGIN
    SELECT s.id_sektora, s.nazwa
    FROM etapy_wyprawy e
    JOIN sektor s ON e.sektor = s.id_sektora
    WHERE e.idWyprawy = p_idWyprawy
    ORDER BY e.kolejnosc;
END$$
DELIMITER ;

CALL sektory_wyprawy(1);
```







