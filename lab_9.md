# Zadanie lab_9

## 1.1 
```
1. SELECT nazwisko FROM __firma_zti.pracownik ORDER BY nazwisko ASC;
2. SELECT imie, nazwisko, pensja FROM __firma_zti.pracownik WHERE data_urodzenia >= "1980-01-01";
3. SELECT * FROM __firma_zti.pracownik WHERE pensja BETWEEN 3500 AND 5000;
4. SELECT * FROM __firma_zti.stan_magazynowy WHERE ilosc > 10;
5. SELECT * FROM __firma_zti.towar WHERE nazwa_towaru LIKE "A%" OR nazwa_towaru LIKE "B%" OR nazwa_towaru LIKE "C%";
6. SELECT * FROM __firma_zti.klient WHERE czy_firma = "0";
7. SELECT * FROM __firma_zti.zamowienie ORDER BY data_zamowienia DESC LIMIT 10;
8. SELECT * FROM __firma_zti.pracownik ORDER BY pensja ASC LIMIT 5;
9. SELECT * FROM __firma_zti.towar WHERE nazwa_towaru NOT LIKE "%a%" ORDER BY cena_zakupu DESC LIMIT 10;
10. SELECT * FROM __firma_zti.towar t JOIN __firma_zti.stan_magazynowy sm ON t.id_towaru = sm.towar WHERE sm.jm = "3" ORDER BY nazwa_towaru ASC, cena_zakupu DESC;
11. CREATE TABLE towary_powyzej_100 SELECT * FROM __firma_zti.towar WHERE cena_zakupu >= 100;
12. CREATE TABLE pracownik_50_plus LIKE __firma_zti.pracownik;
INSERT INTO pracownik_50_plus SELECT * FROM __firma_zti.pracownik WHERE data_urodzenia >= "1976-01-01";
```
## 1.2
```
1. SELECT imie, nazwisko, dzial FROM __firma_zti.pracownik GROUP BY id_pracownika;
2. SELECT t.nazwa_towaru, t.kategoria, sm.ilosc FROM __firma_zti.towar t JOIN __firma_zti.stan_magazynowy sm ON t.id_towaru = sm.towar ORDER BY sm.ilosc DESC;
3. SELECT * FROM __firma_zti.zamowienie WHERE status_zamowienia = "6";
4. SELECT * FROM __firma_zti.klient k JOIN __firma_zti.adres_klienta ak ON k.id_klienta = ak.klient WHERE miejscowosc = "Olsztyn";
5. SELECT jm.nazwa FROM jednostka_miary jm LEFT JOIN stan_magazynowy sm ON jm.id_jednostki = sm.jm WHERE sm.jm IS NULL;
6. SELECT z.numer_zamowienia,t.nazwa_towaru,pz.ilosc,pz.cena FROM zamowienie z JOIN pozycja_zamowienia pz ON z.id_zamowienia = pz.zamowienie JOIN towar t ON pz.towar = t.id_towaru WHERE YEAR(z.data_zamowienia) = 2018;
7. SELECT t.nazwa_towaru,t.cena_zakupu,k.nazwa_kategori AS kategoria,sm.ilosc,jm.nazwa AS jednostka_miary FROM towar t LEFT JOIN kategoria k ON t.kategoria = k.id_kategori LEFT JOIN stan_magazynowy sm ON t.id_towaru = sm.towar LEFT JOIN jednostka_miary jm ON sm.jm = jm.id_jednostki;
8. SELECT z.numer_zamowienia,pz.id_pozycji,t.nazwa_towaru,pz.ilosc,pz.cena FROM zamowienie z JOIN pozycja_zamowienia pz ON z.id_zamowienia = pz.zamowienie JOIN towar t ON pz.towar = t.id_towaru WHERE z.id_zamowienia IN (SELECT id_zamowienia FROM zamowienie ORDER BY data_zamowienia ASC LIMIT 5)
ORDER BY z.data_zamowienia ASC, pz.id_pozycji;
9. SELECT z.numer_zamowienia,z.data_zamowienia,sz.nazwa_statusu_zamowienia AS status FROM zamowienie z JOIN status_zamowienia sz ON z.status_zamowienia = sz.id_statusu_zamowienia WHERE sz.nazwa_statusu_zamowienia != 'zrealizowane';
10. SELECT * FROM adres_klienta WHERE kod NOT REGEXP '^[0-9]{2}-[0-9]{3}$';
```
