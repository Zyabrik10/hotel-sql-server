**Temat:** Hotel

**Autorzy:** Oleksandr Mazurok, Oleksandr Katsal, Helena Parinova, Karyna Nemliienko, Anton Krykhta, Dinmukhammed Abdullayev 

--- 

# 1.  Zakres i krótki opis systemu

- Rejestracja klientów na podstawie:
    1) numeru pokoju;
    2) kategorii cenowej pokoju;
- System jaki rozpoznaje czy pokój jest zajęty czy nie
- System rejestracji klijenótw.
- Jakie z nich są stałe, dla takich osób zniżki
- System zmiany numeru pokoju jeżeli klient chce wymienic pokój na inny
- System obliczenia ceny na bazie "luksusowości" pokoju. 
- W koszt końcowy wchodzi piętro, więlkość pokoju, czy jest czy nie ma AGD.
- Możliwość rezerwacji pokoju przez klienta.
- System jaki pryriotyzuje klientów po czasu, w razie nie odzwonienia czy upłynął termin  rezerwacji
- Przechowywanie danych klienta(paszport/id, pesel, numer telefonu), jego członków rodziny (jeżeli są)
- Zakres obowiązów dla pracowników w zależności od stanowiska.
- Możliwość dodawania dodatkowych usług za odpowiednią wpłatę.
- Materiału zużywalne (ręczniki, mydła, minibar, pościel, worki na śmieci, szczoteczki do zębów)
                          
# 2.	Wymagania i funkcje systemu

## 1) Lista wymagań funkcjonalnych

Wymagania funkcjonalne definiują, jakie operacje system ma wspierać. W kontekście projektu z bazą danych mogą to być takie operacje jak dodawanie, edytowanie, usuwanie danych, czy też ich wyszukiwanie. Oto przykładowa lista:

Dodawanie nowych rekordów do bazy danych: System musi umożliwiać użytkownikom dodawanie nowych danych do tabeli (np. nowych klientów, produktów).

Edycja danych: System powinien pozwalać na edytowanie istniejących danych, np. zmiana adresu klienta.

Usuwanie rekordów: Użytkownicy powinni mieć możliwość usuwania danych, które nie są już potrzebne.

Wyszukiwanie danych: Użytkownicy powinni mieć możliwość wyszukiwania danych na podstawie różnych kryteriów (np. według imienia, numeru telefonu, daty rejestracji).

Raportowanie: System musi generować raporty na podstawie zgromadzonych danych (np. lista wszystkich zamówień w danym okresie).

Zarządzanie uprawnieniami użytkowników: System powinien umożliwiać różnym użytkownikom wykonywanie różnych działań w zależności od przypisanych im ról (np. administrator, pracownik).

## 2) Historyjki użytkownika

Historyjki użytkownika pomagają określić, jak system ma działać z perspektywy końcowego użytkownika. Każda historyjka opisuje prostą funkcję, którą użytkownik chce mieć do dyspozycji. Przykładowe historyjki dla systemu bazodanowego mogą wyglądać tak:

Jako administrator systemu, chcę mieć możliwość dodawania nowych użytkowników, aby kontrolować dostęp do systemu.

Jako pracownik, chcę móc wyszukiwać klientów po numerze telefonu, aby szybko znaleźć ich dane kontaktowe.

Jako menedżer, chcę móc generować raporty sprzedaży, aby analizować wyniki biznesowe.

Jako użytkownik, chcę mieć możliwość edytowania mojego profilu, aby poprawić moje dane kontaktowe.

## 3) Przypadki użycia

Przypadki użycia opisują, jak użytkownicy będą wchodzić w interakcje z systemem. Zawierają szczegóły dotyczące tego, jakie kroki musi wykonać użytkownik, aby wykonać określoną operację. Przykłady przypadków użycia:

Przypadek użycia 1: Dodawanie nowego rekordu do bazy danych
Aktorzy: Użytkownik (np. pracownik)

Opis: Użytkownik chce dodać nowy rekord do bazy danych (np. nowego klienta).

Prekondycje: Użytkownik jest zalogowany i ma odpowiednie uprawnienia.

Kroki:

Użytkownik kliknie przycisk „Dodaj nowego klienta”.

System wyświetli formularz do wprowadzenia danych.

Użytkownik wpisuje dane (imię, nazwisko, numer telefonu, adres).

Użytkownik kliknie „Zapisz”.

System zapisuje dane w bazie danych i wyświetla komunikat o pomyślnym dodaniu.

Postkondycje: Nowy rekord został zapisany w bazie danych.

Przypadek użycia 2: Wyszukiwanie rekordu w bazie danych
Aktorzy: Użytkownik (np. pracownik)

Opis: Użytkownik chce wyszukać dane klienta w systemie.

Prekondycje: Użytkownik jest zalogowany i ma dostęp do funkcji wyszukiwania.

Kroki:

Użytkownik wybiera opcję wyszukiwania.
Użytkownik wpisuje kryterium wyszukiwania (np. numer telefonu, nazwisko).
Użytkownik kliknie „Szukaj”.
System wyświetli wyniki pasujące do kryteriów wyszukiwania.
Użytkonik wybiera wynik, aby wyświetlić szczegóły.
Postkondycje: System zwróci rekordy, które pasują do zapytania użytkownika.

## 4) Wymagania niefunkcjonalne

Oprócz wymagań funkcjonalnych, projekt może obejmować również wymagania niefunkcjonalne, które odnoszą się do jakości systemu. Mogą to być takie wymagania jak:
Wydajność: System powinien obsługiwać co najmniej 1000 zapytań na sekundę.
Bezpieczeństwo: Wszystkie dane użytkowników muszą być przechowywane w sposób zaszyfrowany.
Niezawodność: System powinien być dostępny 99% czasu, z maksymalnym czasem przestoju nieprzekraczającym 1 godziny miesięcznie.
Skalowalność: System musi być skalowalny i obsługiwać zwiększoną liczbę użytkowników bez utraty wydajności.
(np. lista wymagań, np. historyjki użytkownika, np. przypadki użycia itp.)

# 3.	Projekt bazy danych

## Schemat bazy danych

(diagram (rysunek) przedstawiający schemat bazy danych) 

## Opis poszczególnych tabel

(Dla każdej tabeli opis w formie tabelki)


Nazwa tabeli: (nazwa tabeli)
- Opis: (opis tabeli, komentarz)

| Nazwa atrybutu | Typ  | Opis/Uwagi |
|----------------|------|------------|
| Atrybut 1 …    |      |            |
| Atrybut 2 …    |      |            |


# 4.	Implementacja

## Kod poleceń DDL

(dla każdej tabeli należy wkleić kod DDL polecenia tworzącego tabelę)

```sql
create table tab1 (
   a int,
   b varchar(10)
)
```

## Widoki

(dla każdego widoku należy wkleić kod polecenia definiującego widok wraz z komentarzem)

## Procedury/funkcje

(dla każdej procedury/funkcji należy wkleić kod polecenia definiującego procedurę wraz z komentarzem)

## Triggery

(dla każdego triggera należy wkleić kod polecenia definiującego trigger wraz z komentarzem)


