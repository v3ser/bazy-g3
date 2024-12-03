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
select w.nazwa, count(k.nazwa),group_concat(k.nazwa separator '|') as liczba_uczestnikow 
from wyprawa w 
inner join uczestnicy u on w.id_wyprawy=u.id_wyprawy
inner join kreatura k on k.idKreatury=u.id_uczestnika
group by w.id_wyprawy;
```
2.
```
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
```
2.
```
```
## Zadanie 5
1. 
```
```





