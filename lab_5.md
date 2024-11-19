# Zadania lab_5


## Zadanie 1

1.
```
CREATE table kreatura  as select * from wikingowie.kreatura;
CREATE table zasob  as select * from wikingowie.zasob;
CREATE table ekwipunek  as select * from wikingowie.ekwipunek;

```

2.
```
Select * from zasob;

```
3.
```
Select * from zasob where rodzaj="jedzenie";

```
4.
```
Select idZasobu, ilosc from ekwipunek where idKreatury in (1, 3, 5);

```
## Zadanie 2
1.
```
```
2.
```
select * from zasob where waga > 2  and waga < 5;

```
3.
```
select * from kreatura where  nazwa LIKE "%or%" and udzwig between 30 and 70;
```
## Zadanie 3

1.
```
SELECT * FROM zasob WHERE MONTH(dataPozyskania) IN (7, 8);

```
2.
```
SELECT * FROM zasob WHERE rodzaj is not null  order by waga ASC;

```
3.

```
SELECT * FROM kreatura WHERE dataUR is not null order by dataUr asc limit 5; 
```


## Zadanie 4

1.

```
SELECT distinct rodzaj from zasob;
```

2.
```
SELECT concat("Kreatura z id " , idKreatury , "to " , nazwa) FROM kreatura WHERE rodzaj LIKE "wi%"

```

3.
```

```

## Zadanie 5
1.
```
```

2.
```
SELECT * FROM zasob where rodzaj is null;
```

3.
```
SELECT distinct rodzaj  FROM zasob where nazwa LIKE "Ba%" or nazwa LIKE "%os" ORDER BY rodzaj ASC;

```




