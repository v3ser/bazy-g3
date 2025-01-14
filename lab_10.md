# Zadania lab_10

## Zadanie 1
```
SELECT imie, nazwisko, YEAR(data_urodzenia)FROM pracownik;
```
## Zadanie 2
```
SELECT imie, nazwisko, YEAR(CURRENT_DATE) - YEAR(data_urodzenia) AS wiek FROM pracownik;
```
## Zadanie 3
```
SELECT d.nazwa, COUNT(*) AS liczba_pracownikow FROM pracownik p INNER JOIN dzial d ON p.dzial = d.id_dzialu GROUP BY d.nazwa;
```
## Zadanie 4
```
SELECT k.nazwa_kategori, COUNT(*) AS liczba_produktow FROM towar t INNER JOIN kategoria k ON t.kategoria = k.id_kategori GROUP BY k.nazwa_kategori;
```
## Zadanie 5
```
SELECT k.nazwa_kategori, GROUP_CONCAT(t.nazwa_towaru SEPARATOR ', ') AS lista_produktow FROM kategoria k INNER JOIN towar t ON k.id_kategori = t.kategoria GROUP BY k.nazwa_kategori;
```
## Zadanie 6
```
SELECT ROUND(AVG(pensja), 2) AS srednia_pensja FROM pracownik;
```
## Zadanie 7
```
SELECT (AVG(pensja)) AS srednie_zarobki FROM pracownik
WHERE DATEDIFF(CURRENT_DATE, data_zatrudnienia) >= 1825;
```
## Zadanie 8
```
```
## Zadanie 9
```
```
## Zadanie 10
```
SELECT p.imie, p.nazwisko, SUM(pz.ilosc * pz.cena) AS suma_wartosci_zamowien FROM zamowienie z INNER JOIN pozycja_zamowienia pz ON z.id_zamowienia = pz.id_pozycji INNER JOIN pracownik p ON z.pracownik_id_pracownika = p.id_pracownika GROUP BY p.id_pracownika, p.imie, p.nazwisko ORDER BY suma_wartosci_zamowien DESC;
```
## Zadanie 11
```
SELECT d.nazwa, MIN(p.pensja), MAX(p.pensja), AVG(p.pensja) FROM pracownik p INNER JOIN dzial d ON d.id_dzialu = p.dzial GROUP BY d.nazwa;
```
## Zadanie 12
```
SELECT k.pelna_nazwa, SUM(pz.ilosc * pz.cena) AS wartosc_zamowienia FROM zamowienie z INNER JOIN pozycja_zamowienia pz ON z.id_zamowienia = pz.id_pozycji INNER JOIN klient k ON z.klient = k.id_klienta GROUP BY z.id_zamowienia, k.pelna_nazwa ORDER BY wartosc_zamowienia DESC LIMIT 10;
```
## Zadanie 13
```
```
## Zadanie 14
```
```
## Zadanie 15
```
```
## Zadanie 16
```
```
## Zadanie 17
```
```
## Zadanie 18
```
```
## Zadanie 19
```
```
## Zadanie 20
```
```
