#Zadania lab_07

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
```
2.
```
```
## Zadanie 3
1.
```
```
2.
```
```
## Zadanie 4
1.
```
```
2.
```
```
## Zadanie 5
1. 
```
```





