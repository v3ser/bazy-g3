# Zadania lab6



## Zadanie 1

1.
```
Select avg(waga) from kreatura where rodzaj ="wiking";
```
2.
```
SELECT distinct rodzaj, 
       AVG(waga) AS srednia_waga, 
       COUNT(*) AS liczba_kreatur
FROM kreatura
GROUP BY rodzaj;
```
3.
```
SELECT rodzaj, 
       AVG(TIMESTAMPDIFF(YEAR, dataUr, CURDATE())) AS sredni_wiek
FROM kreatura
GROUP BY rodzaj;
```

## Zadanie 2
1.
```
SELECT rodzaj, 
       sum(waga * ilosc ) AS suma_wag
FROM zasob
GROUP BY rodzaj;
```
2.
```
SELECT nazwa, avg(waga) AS srednia_waga FROM zasob where ilosc >=4
GROUP BY nazwa
having sum(waga)>10;
```
3.
```
select rodzaj, count(distinct nazwa) from zasob group by rodzaj having min(ilosc) > 1;

```
## Zadanie 3
1.
```
select k.idKreatury, nazwa, e.idKreatury, idZasobu, ilosc 
from kreatura k, ekwipunek e  where e.idKreatury=k.idKreatury;
```
2.
```
SELECT k.nazwa AS nazwa_kreatury, GROUP_CONCAT(z.nazwa) AS zasoby
FROM kreatura k
JOIN ekwipunek e ON k.idKreatury= e.idKreatury
JOIN zasob z ON e.idZasobu = z.idZasobu
GROUP BY k.nazwa;
```
3.
```
select k.idKreatury, k.nazwa, e.idKreatury from kreatura k
left join ekwipunek e on k.idKreatury=e.idKreatury where e.idKreatury is null;
```

## Zadanie 4
1.
```
Select k.nazwa, z.nazwa FROM kreatura k NATURAL JOIN zasob z 
WHERE k.rodzaj = "wiking" AND k.dataUr BETWEEN '1670-01-01' AND '1679-12-31';
```
2.
```
SELECT k.nazwa, k.dataUr FROM kreatura k JOIN ekwipunek e
ON k.idKreatury = e.idKreatury JOIN zasob z ON e.idZasobu = z.idZasobu
WHERE z.rodzaj = "jedzenie" ORDER by k.dataUr DESC limit 5;
```
3.
```
select k1.idKreatury, k2.idKreatury, k1.nazwa, k2.nazwa from kreatura k1
inner join kreatura k2 on k1.idKreatury=k2.idKreatury - 5;
```
## Zadanie 5

1.
```
SELECT k.rodzaj, AVG(z.waga) FROM kreatura k JOIN ekwipunek e ON k.idKreatury = e.idKreatury
JOIN zasob z ON e.idZasobu = z.idZasobu WHERE k.rodzaj NOT IN ('małpa', 'wąż') 
AND(
	SELECT SUM(ekwipunek.ilosc)
    FROM ekwipunek
    WHERE e.idKreatury = idKreatury
) < 30 group by k.rodzaj;
```
2.
```
```













