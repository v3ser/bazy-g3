# Zadania lab_07

## Zadanie 1
1.
```
INSERT INTO infs_rawam.kreatura select * from wikingowie.kreatura;
CREATE TABLE uczestnicy AS SELECT * FROM wikingowie.uczestnicy;
CREATE TABLE etapy_wyprawy AS SELECT * FROM wikingowie.etapy_wyprawy;
CREATE TABLE sektor AS SELECT * FROM wikingowie.sektor;
CREATE TABLE wyprawa AS SELECT * FROM wikingowie.wyprawa;
```
2.
```
select  k.nazwa from kreatura k
left join wyprawa w on k.idKreatury=w.kierownik where w.kierownik is null;
```
3.
```
SELECT w.nazwa, SUM(e.ilosc) FROM wyprawa w
JOIN kreatura k ON w.kierownik = k.idKreatury
JOIN ekwipunek e ON k.idKreatury = e.idKreatury
GROUP BY w.nazwa;
```

## Zadanie 2
1.
```
select w.nazwa, count(k.nazwa),group_concat(k.nazwa separator '|') as liczba_uczestnikow 
from wyprawa w 
inner join uczestnicy u on w.id_wyprawy=u.id_wyprawy
inner join kreatura k on k.idKreatury=u.id_uczestnika
group by w.id_wyprawy;
```
2.
```
SELECT
    w.data_rozpoczecia,
    w.kierownik,
    e.kolejnosc,
    s.nazwa AS nazwa_sektora
FROM
    wyprawa w
INNER JOIN etapy_wyprawy e ON w.id_wyprawy = e.idWyprawy
INNER JOIN sektor s ON e.sektor = s.id_sektora
ORDER BY
    w.data_rozpoczecia,
    e.kolejnosc;

```
## Zadanie 3
1.
```
select s.nazwa, ifnull(count(ew.sektor), 'brak'), s.id_sektora
from etapy_wyprawy ew
right join sektor s on ew.sektor=s.id_sektora
group by s.id_sektora;
```
2.
```
select s.nazwa, if(count(ew.sektor) = 0, 'nie był odwiedzany', count(ew.sektor)) as ile_odwiedzin,s.id_sektora
from etapy_wyprawy ew
right join sektor s on ew.sektor=s.id_sektora
group by s.id_sektora;
```
## Zadanie 4
1.
```
SELECT w.nazwa AS nazwa_wyprawy, 
       SUM(LENGTH(e.dziennik)) AS liczba_znakow
FROM wyprawa w
JOIN etapy_wyprawy e ON w.id_wyprawy = e.idWyprawy
GROUP BY w.nazwa
HAVING SUM(LENGTH(e.dziennik)) < 400;
```
2.
```
SELECT 
    w.nazwa AS nazwa_wyprawy,
    AVG(z.waga * e.ilosc) / 
    (SELECT COUNT(*) FROM uczestnicy u WHERE u.id_wyprawy = w.id_wyprawy) AS srednia_waga_na_uczestnika
FROM wyprawa w
JOIN uczestnicy u ON u.id_wyprawy = w.id_wyprawy
JOIN ekwipunek e ON w.id_wyprawy = e.idZasobu
JOIN zasob z ON e.idZasobu = z.idZasobu
GROUP BY w.nazwa;
```
## Zadanie 5
1. 
```
SELECT
    k.nazwa AS nazwa_kreatury,
    DATEDIFF(w.data_rozpoczecia, k.dataUr) AS wiek_w_dniach
FROM
    kreatura k
INNER JOIN wyprawa w ON k.idKreatury = w.id_wyprawy
INNER JOIN etapy_wyprawy e ON w.id_wyprawy = e.idWyprawy
WHERE
    e.sektor = 7  
GROUP BY
    k.nazwa, k.dataUr, w.data_rozpoczecia;
```





