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
SELECT z.id_zamowienia AS numer_zamowienia, SUM(pz.ilosc * pz.cena) AS wartosc_zamowienia FROM zamowienie z INNER JOIN pozycja_zamowienia pz ON z.id_zamowienia = pz.zamowienie WHERE z.data_zamowienia BETWEEN '2017-01-01' AND '2017-03-31' GROUP BY z.id_zamowienia;
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
SELECT EXTRACT(YEAR FROM data_zamowienia) AS rok, SUM(pz.ilosc * pz.cena) AS przychod FROM zamowienie z INNER JOIN pozycja_zamowienia pz ON z.id_zamowienia = pz.zamowienie GROUP BY rok ORDER BY przychod DESC;
```
## Zadanie 14
```
SELECT SUM(pz.ilosc * pz.cena) AS suma_anulowanych_zamowien FROM pozycja_zamowienia pz INNER JOIN zamowienie z ON pz.zamowienie = z.id_zamowienia WHERE z.status_zamowienia = 'anulowane';
```
## Zadanie 15
```
SELECT ak.miejscowosc, COUNT(z.id_zamowienia) AS liczba_zamowien, SUM(pz.ilosc * pz.cena) AS wartosc_zamowien FROM adres_klienta ak INNER JOIN klient k ON ak.klient = k.id_klienta INNER JOIN zamowienie z ON k.id_klienta = z.klient INNER JOIN pozycja_zamowienia pz ON z.id_zamowienia = pz.zamowienie GROUP BY ak.miejscowosc;
```
## Zadanie 16
```
SELECT SUM(pz.ilosc * pz.cena) AS dochod FROM pozycja_zamowienia pz INNER JOIN zamowienie z ON pz.zamowienie = z.id_zamowienia INNER JOIN status_zamowienia sz ON sz.id_statusu_zamowienia = z.status_zamowienia WHERE sz.nazwa_statusu_zamowienia = 'zrealizowane';
```
## Zadanie 17
```
SELECT EXTRACT(YEAR FROM z.data_zamowienia) AS rok, SUM(pz.ilosc * pz.cena) - SUM(pz.ilosc * t.cena_zakupu) AS dochod FROM pozycja_zamowienia pz INNER JOIN zamowienie z ON pz.zamowienie = z.id_zamowienia INNER JOIN towar t ON pz.towar = t.id_towaru GROUP BY EXTRACT(YEAR FROM z.data_zamowienia) ORDER BY rok;
```
## Zadanie 18
```
SELECT k.nazwa_kategori, SUM(sm.ilosc) AS ilosc_w_magazynie FROM stan_magazynowy sm INNER JOIN towar t ON sm.towar = t.id_towaru INNER JOIN kategoria k ON t.kategoria = k.id_kategori GROUP BY k.nazwa_kategori;
```
## Zadanie 19
```
```
## Zadanie 20
```
SELECT imie, nazwisko, (DATEDIFF(CURDATE(), data_zatrudnienia) DIV 30) * pensja AS calkowity_koszt FROM pracownik;
```
