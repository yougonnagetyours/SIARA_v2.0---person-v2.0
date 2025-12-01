---
## 2025-12-01, 16:00 - Sesja #7 (Konfiguracja Make.com i Master Prompt)

**Co robiliśmy:**
- Zbudowano i skonfigurowano scenariusz w Make.com: Gmail (Watch) -> OpenAI (GPT-5.1) -> Gmail (Draft).
- Stworzono plik konfiguracyjny `product_mvp/make_scenarios_config/system_prompt_make_v1.md` jako "Single Source of Truth" dla promptu.
- Zintegrowano wszystkie scenariusze testowe (Scope Creep, Panika, Rabaty, Vibe Check) w jeden Master Prompt.
- Dopracowano styl: usunięto żargon ("dowożenie"), dodano formatowanie HTML, zmieniono listę opcji na naturalną (bez nawiasów "Opcja A").

**Ustalenia:**
- Agent działa w imieniu Marty (Właścicielki), styl "Asertywna Właścicielka".
- Make.com korzysta z modelu `gpt-5.1` (lub najnowszego dostępnego).
- Nie komplikujemy scenariusza bazami danych – prompt systemowy zawiera przykłady (Few-Shot).

**Następny krok:**
- Finalny test ("Run once") z nowym, naturalnym promptem.
- Nagranie wideo demo (Loom) z działającego procesu.
---
---
## 2025-11-28, 12:15 - Sesja #6 (Finalizacja Testów MVP i Plan Wdrożenia)

**Co robiliśmy:**
- Pomyślnie zweryfikowano Scenariusz 2 "Panika" po poprawkach (Agent nie zgaduje, jest merytoryczny).
- Pomyślnie przetestowano Scenariusz 3 "Vibe Check" (Agent asertywnie prosi o konkrety zamiast zgadywać "styl").
- Zaktualizowano Prompt Systemowy (`v1_agent_draftujacy_glowny.md`), wymuszając podpis "Marta" pod każdym draftem.
- Podjęto kluczowe decyzje technologiczne i biznesowe (Make.com, model wdrożenia).

**Ustalenia:**
- **Decyzja Tech:** MVP i Demo budujemy na **Make.com** (konto integratora).
- **Model Biznesowy:** "Integrator" - wdrażamy automatyzację na kontach klientów (bezpieczeństwo danych, brak kosztów API po naszej stronie).
- **Uproszczenie Promptu:** Należy zmodyfikować prompt systemowy, aby zwracał *tylko* treść maila (bez nagłówków "Temat:" / "Treść:"), co ułatwi konfigurację w Make.
- **Podpis Agenta:** Każdy draft kończy się podpisem "Marta".

**Następny krok:**
- Konfiguracja scenariusza w Make.com (Gmail -> OpenAI -> Gmail Draft).
- Nagranie wideo demo (Loom) pokazującego działanie na żywo.
---
---
## 2025-11-28, 11:20 - Sesja #5 (Budowa MVP Agenta)

**Co robiliśmy:**
- Zrestrukturyzowano projekt, wydzielając katalog `product_mvp/` dla zasobów produktowych (uniezależnienie od Wąskiego).
- Stworzono strukturę: `product_mvp/system_prompts`, `training_examples`, `test_cases`.
- Spisano "Biblię Stylu" dla Wąskiego w pliku `agents/waski/baza_wiedzy/StylKomunikacjiKlient.md`.
- Dopracowano Prompt Systemowy (`v1_agent_draftujacy_glowny.md`), dodając zasadę "Merytoryczna Precyzja" (zakaz zgadywania platform).
- Zaktualizowano przykłady treningowe (`styl_komunikacji.md`), usuwając anglicyzmy ("realny czas" -> "godziny pracy") i profesjonalizując scenariusz paniki.
- Przeprowadzono udane symulacje dla Scenariusza 1 (Scope Creep) i Scenariusza 2 (Panika).
- Wykonano commit zmian: "feat: Implement Agent Drafting MVP structure and initial prompts".

**Ustalenia:**
- Pliki w `product_mvp/` są jedynym źródłem wiedzy dla Agenta Draftującego (samodzielność produktu).
- Styl komunikacji Agenta: "Asertywna Dyplomacja" - konkret, bez korpo-slangu, edukacja klienta.
- Agent w symulacjach będzie podpisywał się imieniem "Marta".
- Agent nie może zgadywać faktów (np. "sprawdzam FB/Google") - musi używać bezpiecznych, ogólnych sformułowań ("audyt trackingu").

**Następny krok:**
- Ponowna weryfikacja Scenariusza 2 (dla 100% pewności).
- Opracowanie i przetestowanie Scenariusza 3 ("Vibe Check").
---
---
## 2025-11-27, 10:35 - Sesja #4 (Decyzja: Scenariusz Demo)

**Co robiliśmy:**
- Usunięto `memory/todo_list.md` zgodnie z filozofią Johna Galla (uproszczenie systemu, usunięcie martwej biurokracji).
- Wybrano konkretny scenariusz do budowy Demo MVP: **"Scope Creep"** (klient proszący o darmowe dodatki).

**Ustalenia:**
- Zostawiamy tylko dwa pliki pamięci: `session_notes.md` (dziennik) i `progress_tracker.md` (mapa).
- **Cel Demo:** Pokazać, jak Agent oszczędza pieniądze i nerwy, generując asertywną odpowiedź na próbę "scope creepu".
- **Strategia komunikacji:** "Wychowywanie klienta" – Agent odpisuje natychmiast na maile (nagroda), telefon milczy (brak nagrody), co przesuwa komunikację na kanał pisemny (asynchroniczny).

**Następny krok:**
- Budowa Promptu Systemowego realizującego scenariusz "Scope Creep" (asertywna dyplomacja).
---
---
## 2025-11-27, 10:15 - Sesja #3 (Konfiguracja i Plan)

**Co robiliśmy:**
- Zaktualizowano plik konfiguracyjny `GEMINI.md`:
    - Ujednolicono identyfikatory agentów na `#SIARA` i `#WASKI`.
    - Dodano wymóg stosowania prefixów `#siara:` / `#waski:` w odpowiedziach systemu.
- Zaktualizowano `memory/todo_list.md`: usunięto nieaktualne zadania, wprowadzono nowy plan "Agent Draftujący".
- Przygotowano "Zestaw Startowy Piekła Agencji" (3 scenariusze maili: Scope Creep, Panika, Vibe) do testowania Agenta.

**Ustalenia:**
- **Priorytet:** Najpierw budowa Demo (Tech) i weryfikacja działania Agenta, dopiero potem aktualizacja LinkedIn i outreach. Nie sprzedajemy "powietrza".
- Użytkownik zakończył sesję przed wyborem konkretnego scenariusza testowego.

**Następny krok:**
- Wybór scenariusza maila testowego.
- Stworzenie i przetestowanie Promptu Systemowego dla Agenta Draftującego.
---
---
## 2025-11-27, 10:00 - Sesja #2

**Co robiliśmy:**
- Naprawiono i skonfigurowano Agenta Wąski (Ghostwriter) do korzystania z właściwych danych klienta (knowledge/ideal_customer.md i knowledge/business_idea.md).
- Usunięto odniesienia do starego pliku MojaIdealnaPersona.md.
- Zapisano gotowy tekst profilu LinkedIn ("Systemy, które działają, gdy Ty odpoczywasz") w pliku agents/waski/drafts/linkedin_profile_draft.md.
- Przeprowadzono pivot biznesowy: zmieniono koncepcję produktu z "Dashboardy/Raporty" na "Inteligentny Asystent Komunikacji (Draft Mode) dla Agencji".
- Zdefiniowano Agent AI jako "Human in the Loop" (przygotowuje draft, klient zatwierdza).
- Zaktualizowano `knowledge/business_idea.md` o nową koncepcję usługi.
- Zaktualizowano `knowledge/smoke_test_plan.md` pod kątem Agenta Draftującego, włączając wideo Loom jako asset i nowe KPI.

**Ustalenia:**
- Wąski ocenił zgodność draftu profilu LinkedIn z personą Marty na 9/10.
- Nowy plan smoke testu obejmuje nagranie wideo Loom z demo Agenta w akcji i outreach do 20-30 właścicieli agencji.
- Kluczowe KPI to 5 osób chętnych do testu na swoich danych i 1 sprzedaż wdrożenia MVP.

**Następny krok:**
- Zatwierdzenie finalnej wersji profilu LinkedIn.
- Wgranie profilu na LinkedIn.
- Rozpoczęcie "Tygodnia 1" z planu (nagranie wideo/Loom z demo Agenta).
---
---
## 2025-11-26, 19:08 - Sesja #1 (Aktualizacja - Profil LinkedIn)
 
**Co robiliśmy:**
- Uzupełniono brakującą informację: Konkretna, poprawiona wersja profilu LinkedIn (nagłówek i sekcja "O mnie") została zapisana.
 
**Ustalenia:**
- Wersja robocza profilu LinkedIn znajduje się w pliku: `agents/waski/drafts/linkedin_profile_draft.md`.
 
**Następny krok:**
- Zatwierdzenie finalnej wersji profilu LinkedIn (z pliku `agents/waski/drafts/linkedin_profile_draft.md`).
- Wgranie profilu na LinkedIn.
- Rozpoczęcie "Tygodnia 1" z planu (przygotowanie wideo/Loom).
---
---
## 2025-11-26, 15:08 - Sesja #1
 
**Co robiliśmy:**
- Restrukturyzacja projektu: Wdrożenie systemu agentów (@Siara i @Waski) oraz Routera (GEMINI.md).
- Aktualizacja statusu Wąskiego (StatusAktualny.md) na tryb "Smoke Test".
- Commit zmian w repozytorium ("Refactor: New folder structure for agents @Siara and @Waski").
- Praca nad profilem LinkedIn: Mamy roboczą wersję nagłówka i bio, z usuniętym fałszywym social proof na rzecz uczciwego opisu kompetencji.
 
**Ustalenia:**
- Zostajemy przy wspólnych notatkach (memory/session_notes.md i memory/progress_tracker.md) zgodnie z filozofią Johna Galla (unikamy przedwczesnej optymalizacji).
- Decyzja o nieużywaniu osobnego pliku CHANGELOG.md; Git i session_notes.md pełnią tę rolę.
- Finalna wersja profilu LinkedIn do zatwierdzenia.
 
**Następny krok:**
- Zatwierdzenie finalnej wersji profilu LinkedIn.
- Wgranie profilu na LinkedIn.
- Rozpoczęcie "Tygodnia 1" z planu (przygotowanie wideo/Loom).
---
# Notatki z Sesji

Najnowsze wpisy na górze ↓

---