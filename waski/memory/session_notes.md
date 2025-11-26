# 📂 Historia sesji - Notatki i zmiany

## 📅 Sesja #3 - 2025-11-19

### 🎯 Cel sesji
Dopracowanie i sformatowanie posta LinkedIn z pliku `baza_wiedzy/posty+cytowanie_ze_zrodeł/95% wdrożeń AI w firmach kończy się porażką.md` zgodnie z wytycznymi użytkownika oraz przygotowanie koncepcji grafiki.

### ✅ Co zostało zrobione

1.  **Refinement treści posta:**
    *   Zmieniono frazę "To, czego się z tego uczę:" na "To tylko potwierdza moje doświadczenia z optymalizacji procesów:", aby lepiej odzwierciedlić osobiste doświadczenia użytkownika.
    *   Zmieniono "AI to nie jest kolejny zakup w budżecie IT." na "AI to nie jest kolejny zakup w budżecie firmy.", aby uogólnić kontekst budżetu.
    *   Poprawiono niespójność gramatyczną w pytaniu "Kupujecie narzędzia, czy zmieniają całą organizację?" na "Kupujecie narzędzia, czy zmieniacie całą organizację?".

2.  **Formatowanie posta dla LinkedIn:**
    *   Usunięto metainformacje takie jak `=== POST LINKEDIN ===`, `📊 POST - STATYSTYKI (z weryfikowalnymi źródłami)`.
    *   Usunięto wszystkie separatory `---` z głównej treści posta, zastępując je podwójnymi znakami nowej linii, aby poprawić czytelność i estetykę na LinkedIn.
    *   Usunięto całą sekcję samooceny (`=== SAMOOCENA ===` i jej zawartość), ponieważ jest to informacja wewnętrzna, a nie część publikowanego posta.
    *   Usunięto całą sekcję "Aneks" wraz z poprzedzającym ją separatorem `---`, ponieważ nie jest to część właściwego posta na LinkedIn.

3.  **Koncepcje grafiki:**
    *   Zaproponowano dwie koncepcje grafiki do posta, wraz z gotowymi promptami do zewnętrznych narzędzi AI do generowania obrazów:
        *   Koncepcja 1: Metafora z warsztatem (narzędzia vs. zespół)
        *   Koncepcja 2: Statystyka w centrum (duże "95%" z efektem pęknięcia)
    *   Zalecono Koncepcję 1 jako bardziej pasującą do stylu komunikacji użytkownika.

### 💡 Kluczowe learningi

1.  **Precyzja w `replace`:** Konieczność używania dokładnego kontekstu w `old_string` dla narzędzia `replace`, aby uniknąć niezamierzonych modyfikacji lub błędów spowodowanych wielokrotnym występowaniem tego samego ciągu znaków.
2.  **Holistyczne formatowanie:** Oprócz konkretnych poprawek językowych, ważne jest usunięcie wszystkich metainformacji i dostosowanie formatowania (np. usunięcie `---`) do specyfiki platformy docelowej (LinkedIn).
3.  **Proaktywne wsparcie:** Mimo braku narzędzi do generowania obrazów, można zaoferować wartościowe wsparcie poprzez tworzenie koncepcji i promptów dla zewnętrznych narzędzi.

### 📤 Rezultat
Post został w pełni dopracowany i sformatowany do publikacji na LinkedIn. Użytkownik otrzymał również propozycje grafik z promptami.

### ⚠️ Uwagi na przyszłość
*   Zawsze dokładnie weryfikować cały plik po każdej serii zmian, aby upewnić się, że żadne elementy formatowania nie zostały przeoczone.
*   Pamiętać o rozróżnieniu między treścią posta a metainformacjami/sekcjami pomocniczymi.

---

## 📅 Sesja #2 - 2025-01-18

### 🎯 Cel sesji
Przerobienie treści landing page dla 7-dniowego smoke testu, aby pasowała do stylu komunikacji i idealnej persony (Marek - właściciel agencji).

### ✅ Co zostało zrobione

1. **Analiza materiałów wejściowych**
   - Przeanalizowano brief landing page od "Siary" (asystenta biznesowego)
   - Sprawdzono dopasowanie do idealnej persony z `MojaIdealnaPersona.md`
   - Zidentyfikowano kluczowe pain points Marka (marża spada, chaos przy skalowaniu, zależność od ludzi)

2. **Przerobienie treści landing page**
   - **Hero:** Zmieniono z ogólnika "Automatyzacja w 7 dni" na konkretny problem: "Doszedłeś do ściany?"
   - **Sekcja Problem:** Użyto konkretnych pain points z persony (20% czasu na raporty, marża spada mimo wzrostu przychodów, urlop = chaos)
   - **Sekcja Rozwiązanie:** Dodano język persony ("Pokaże Ci w Excelu", ROI, EBITDA)
   - **Dla kogo:** Precyzyjny opis sytuacji Marka (10-25 osób, myśli systemami, chce skalować)
   - **Obiekcje (FAQ):** Dodano sekcję z typowymi obiekcjami i kontr-argumentami wprost z pliku persony
   - **Ton ogólny:** Z korporacyjnego na naturalny, konkretny, bez marketingowego bełkotu

3. **Iteracja nagłówka Hero**
   - Testowano kilka wersji z użytkownikiem:
     - ❌ "Przestań zatrudniać ludzi do gaszenia pożarów" - odrzucone (nienaturalne)
     - ✅ "Więcej klientów, ale marża spada? Doszedłeś do ściany." - zaakceptowane
   - Finalna wersja podnagłówka: "Pokażę Ci w 30 minut, które procesy zjadają Twoją marżę – i jak odzyskać kontrolę nad firmą."

4. **Zapisanie dwóch wersji**
   - **Oryginał:** `landing_page.md` (od Siary) - zostaje jako wersja robocza na smoke test
   - **Przerobiona:** `landing_page_przerobiony.md` - backup na wypadek, gdyby oryginał nie działał

### 💡 Kluczowe learningi

1. **Język persony = klucz** - Użycie konkretnych zwrotów z persony ("Pokaże Ci w Excelu", "EBITDA", "system operacyjny firmy") natychmiast zwiększa autentyczność

2. **Prostota > brzmiące mądrze** - Frazy typu "a zostawiają sobie mniej" czy "przestań zatrudniać ludzi do gaszenia pożarów" brzmią sztucznie. Lepiej: "marża spada", "procesy zjadają marżę"

3. **A/B testing w praktyce** - Użytkownik podchodzi pragmatycznie: testy oryginał vs przerobiona wersja w realnym smoke teście, a nie teoretyzowanie

### 📤 Rezultat

**2 wersje landing page** zapisane w `baza_wiedzy/SmokeTestAssets/`:
- `landing_page.md` - oryginał (wersja do smoke testu)
- `landing_page_przerobiony.md` - dopasowana do persony (backup na przyszłość)

### ⚠️ Uwagi na przyszłość

1. **Testowanie hipotez** - Użytkownik świadomie wybiera pragmatyczne podejście: najpierw test oryginału, potem ewentualna optymalizacja
2. **Unikaj "marketingowego języka"** - Frazy, które brzmią jak z szablonu landing page'a, są odrzucane
3. **Konkret > metafora** - W landing page'u liczy się bezpośredni problem i jego rozwiązanie, nie poetyckie opisy

---

## 📅 Sesja #1 - 2025-01-14

### 🎯 Cel sesji
Wygenerowanie pomysłów na posty LinkedIn na temat: "Wdrażanie automatyzacji i AI w firmach" z wykorzystaniem formatu "Czy wiedziałeś, że...?" (3 zaskakujące fakty + pytanie zachęcające do komentowania).

### ✅ Co zostało zrobione

1. **Analiza bazy wiedzy**
   - Sprawdzono aktualną fazę: **Łucznik** (początek journey)
   - Przeanalizowano idealną personę: **Marek** (właściciel agencji performance, 12 osób, chaos w procesach przy skalowaniu)
   - Zapoznano się ze stylem komunikacji z folderu `MojStyl/`

2. **Generowanie pomysłów na posty**
   - Zaproponowano **10 pomysłów na posty** dopasowanych do:
     - Fazy Łucznik (perspektywa uczącego się, nie eksperta)
     - Pain-pointów Marka (chaos, brak standaryzacji, koszty)
     - Naturalnego, konwersacyjnego stylu
   - Użytkownik wybrał pomysł #5: "Dlaczego zacząłem od mapowania procesów, zanim kupiłem jakiekolwiek AI"

3. **Weryfikacja i research case study**
   - **Problem #1:** Pierwszy przykład (Sitech) dotyczył SAP, nie AI - odrzucony przez użytkownika
   - **Problem #2:** Przykład zakładu farmaceutycznego był anonimowy (brak weryfikowalności)
   - **Rozwiązanie:** Znaleziono 3 weryfikowalne źródła:
     - **Exdrog** - firma straciła przetarg za 15,5 mln zł przez halucynacje AI
     - **Raport MIT** - 95% wdrożeń AI kończy się porażką
     - **Firma finansowa Warszawa** - skrócenie procesu z 48h do 15 min przez przeprojektowanie procesu wokół AI

4. **Utworzenie 3 gotowych postów** z weryfikowalnymi źródłami:
   - **POST A - EXDROG:** Weryfikowalny case polskiej firmy (mycompanypolska.pl, Krakowski ZDW, Jarosław Sroka)
   - **POST B - STATYSTYKI:** Raport MIT "The GenAI Divide: State of AI in Business 2025"
   - **POST C - SUKCES:** Firma finansowa z Warszawy (raport EY Polska 2024 + badanie McKinsey)

### 💡 Kluczowe learningi

1. **Weryfikowalność > storytelling** - Użytkownik w fazie Łucznik priorytetowo traktuje wiarygodność. Lepiej odrzucić ciekawy przykład niż zaryzykować utratę zaufania.

2. **Złamanie własnej zasady** - Pierwszy draft używał metafory "Trabant/Ferrari" z PostyUdostepnione.md, co naruszało regułę z CLAUDE.md:
   - 🔴 NIE WOLNO kopiować konkretnych zwrotów i metafor
   - 🦜 NAŚLADUJ TYLKO styl, strukturę, ton
   - **Poprawiono:** Zamieniono na nowe metafory (budowa domu, GPS wymyślający ulice, budowa mostu)

3. **Systematyczne podejście do research:**
   - WebSearch -> WebFetch -> weryfikacja źródeł
   - Odrzucanie anonimowych przykładów
   - Priorytet: polskie firmy > zagraniczne + konkretne dane > ogólniki

### 📤 Rezultat

**3 gotowe posty** zapisane w folderze `posty_do_review/`:
- Każdy ~1100-1150 znaków (zgodnie z limitami)
- Format "Czy wiedziałeś, że...?" + 3 fakty + metafora + CTA
- Weryfikowalne źródła
- Dopasowane do persony Marek + faza Łucznik

### ⚠️ Uwagi na przyszłość

1. **Proces weryfikacji** - Użytkownik rozpoczyna od weryfikacji postów przed publikacją (świetna praktyka!)
2. **Unikaj recyklingu metafor** - Zawsze twórz NOWE metafory w stylu przykładów, nie kopiuj treści
3. **AI vs ERP** - Zwracaj uwagę na różnicę między AI/automatyzacją a systemami ERP/SAP