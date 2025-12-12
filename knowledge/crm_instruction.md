# Instrukcja Obsługi CRM (Notion) - Smoke Test

## Cel
Śledzenie postępów walidacji biznesowej w sposób uporządkowany, bez zbędnej biurokracji.

## Struktura Bazy (Notion)
Baza danych: **"CRM - Smoke Test"**

### Kolumny (Właściwości):
1.  **Name (Aa):** Imię i Nazwisko Lead'a.
2.  **Status (Select):**
    *   `Zaproszony` (Wysłano zaproszenie, czekamy).
    *   `Przyjął` (Jesteśmy w kontakcie, cisza).
    *   `Zareagował` (Lajk/Komentarz pod postem).
    *   `DM Wysłany` (Zaczepiłem go).
    *   `Demo Umówione` (Chce zobaczyć produkt - SUKCES CZĘŚCIOWY).
    *   `Klient` (Kupił/Chce wdrożyć - SUKCES PEŁNY).
    *   `Odrzucony` (Nie jest zainteresowany/Olał).
3.  **Źródło (Select):**
    *   `Cold Outreach` (Sam go znalazłem i zaprosiłem).
    *   `Post Wideo` (Sam przyszedł z contentu).
    *   `Inne` (Polecenie, itp.).
4.  **Data Kontaktu (Date):** Kiedy była ostatnia akcja.
5.  **Link LI (URL):** Link do profilu LinkedIn (opcjonalnie, dla wygody).

## Zasady Uzupełniania
1.  **Widok Tabeli:** Służy tylko do szybkiego podglądu statusu. Ma być czysto.
2.  **Szczegóły Rozmowy:** Wszystkie notatki, treść wiadomości, uwagi wpisujemy **W ŚRODKU** strony danego kontaktu (kliknij `Open` przy nazwisku).
3.  **Kiedy dodajemy rekord?**
    *   Od razu po wysłaniu zaproszenia (Status: `Zaproszony`, Źródło: `Cold Outreach`).
    *   Od razu, gdy ktoś skomentuje post w sposób merytoryczny (Status: `Zareagował`, Źródło: `Post Wideo`).

## KPI do monitorowania (Tygodniowe)
*   Liczba wysłanych zaproszeń.
*   Liczba nowych kontaktów (Przyjął).
*   Liczba rozpoczętych rozmów (DM Wysłany).
*   **Liczba umówionych DEMO (Cel: 5).**
