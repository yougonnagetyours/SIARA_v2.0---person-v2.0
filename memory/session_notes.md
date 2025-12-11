# Notatki z Sesji

Najnowsze wpisy na górę ↓

---
## 2025-12-11, 18:00 - Sesja #22 (Strategia Rozgrzewki LinkedIn)

**Co robiliśmy:**
- **Analiza Grupy Docelowej:** Michał celuje w właścicieli małych agencji (5-15 os.), którzy toną w operacyjce.
- **Strategia Zapraszania ("Cichy Inżynier"):**
    - Decyzja: Wysyłamy zaproszenia **BEZ notatki** (Blank Invites).
    - Powód: Nagłówek profilu ("Inżynier Procesów | Automatyzacja...") jest wystarczającym filtrem i "lepem". Notatki sprzedażowe palą mosty.
    - Timing: Zaproszenia idą DZIŚ (przed publikacją wideo), aby nowy content ("Inżynier vs Gmail") trafił do feedu świeżych kontaktów (Freshness Boost).
- **Profil LinkedIn:**
    - Opis "O mnie" (About) uznano za gotowy i spójny z nową narracją.
    - Zadanie dla Michała: Wkleić opis na profil -> Wysłać 20 zaproszeń.

**Ustalenia:**
- Zanim opublikujemy wideo, musimy mieć "oczy", które na nie spojrzą.
- Nie spamujemy. Budujemy sieć w oparciu o ciekawość ("Kim jest ten inżynier?").

**Następny krok (Jutro):**
- Nagranie i montaż wideo (według scenariusza Wąskiego).
- Publikacja posta.
- Obsługa ewentualnych komentarzy/reakcji.

---
## 2025-12-11, 17:30 - Sesja #21 (Smoke Test: SUKCES)

**Co robiliśmy:**
- **Finalizacja n8n (Magic Gmail v5):**
    - Rozwiązano problem "głuchego telefonu" w przepływie danych. Wdrożono metodę referencji (`$('Get many messages')...`) zamiast polegania na danych wejściowych z poprzedniego kroku.
    - Naprawiono tworzenie draftów: teraz poprawnie przypisują się do istniejących wątków (Thread ID) i mają status DRAFT.
    - Naprawiono powiadomienia Slack: zawierają poprawne linki bezpośrednie do draftu w Gmailu.
    - **Zabezpieczenie:** Wyeksportowano działający workflow do `n8n/AgentMagicGmail_v5_OnDemand.json` (Golden Master).
- **Strategia Smoke Testu (Pivot v2.0):**
    - Zaktualizowano `knowledge/smoke_test_plan.md`. Stary plan zarchiwizowano jako `_OLD`.
    - Nowa narracja: "Inżynier Procesów" (autentyczna dla Michała), a nie "Właściciel Agencji".
    - Argument sprzedażowy: "Zbudowałem to dla siebie, bo nienawidzę marnotrawstwa (Lean). Chcesz zobaczyć demo?"
- **Content:**
    - Wąski przygotował draft posta na LinkedIn oraz scenariusz wideo (60s).
    - Ustalono format wideo: **4:5 z dynamicznym zoomem** (optymalny na mobile LinkedIn i Instagram).
    - Zapisano drafty w `agents/waski/drafts/linkedin_post_magic_gmail_v1.md`.

**Ustalenia:**
- System działa stabilnie i jest gotowy do pokazania światu.
- Nie udajemy agencji. Gramy kartą "Inżyniera od optymalizacji".
- Instagram traktujemy jako "recykling" (wrzucamy to samo wideo co na LI).

**Następny krok (Jutro):**
- Finalna redakcja posta i scenariusza przez Michała (nadanie osobistego szlifu).
- Nagranie wideo (Screen recording + Voiceover).
- Publikacja (LinkedIn + Instagram).
---
## 2025-12-11, 10:00 - Sesja #20 (Pivot na Slack Command Center)

**Co robiliśmy:**
- **Zmiana Architektury (Pivot):** Zrezygnowano z automatycznego triggera (Polling) na rzecz modelu "Na Żądanie" sterowanego ze Slacka.
    - Powód: Problemy z testowaniem (opóźnienia, ignorowanie starych maili) i potrzeba "poczucia kontroli" dla Persony (Marta).
- **Slack Command Center:**
    - Wdrożono `Slack Trigger` reagujący na słowo kluczowe `draftuj` na kanale.
    - Zastosowano logikę "Odkurzacz": Komenda uruchamia `Gmail Get Many Messages`, który pobiera i przetwarza paczkę maili z etykiety `Draft Asystent`.
- **System Etykiet (UX):** Wprowadzono wizualny status procesu w Gmailu:
    - Fioletowa `Draft Asystent` = Do zrobienia.
    - Zielona `✅ Draft Gotowy` = Zrobione.
- **Decyzje Techniczne:** Odrzucono pomysł wdrożenia Agenta AI (LangChain) w MVP (zbyt wolny/drogi). Postawiono na deterministyczny workflow w n8n.

**Ustalenia:**
- Workflow w n8n jest gotowy i skonfigurowany pod demo (Slack -> Gmail -> Slack).
- System jest odporny na "stare maile" i działa natychmiast po komendzie.

**Następny krok:**
- Przeprowadzenie "Wielkiego Testu" (Integracja Slack-Gmail na żywo).
- Nagranie wideo demo (Loom) dla Marty.
---
## 2025-12-10, 10:45 - Sesja #19 (MVP v5: Wątkowanie Działa!)

**Co robiliśmy:**
- **Naprawa n8n (v5):**
    - Zmieniono operację w węźle Gmail z `Create Draft` na `Reply`.
    - Skonfigurowano opcję "Create Draft" wewnątrz `Reply`, aby nie wysyłać wiadomości od razu.
    - Naprawiono mapowanie zmiennych dla AI Pisarza (zamiana `textPlain` na `text` oraz precyzyjne wyciągnięcie nadawcy z obiektu `from`).
- **Test Bojowy:**
    - Scenariusz: "Start kampanii na LinkedIn" (Scope Creep).
    - Wynik: Agent poprawnie odebrał maila, zanalizował treść i utworzył **draft odpowiedzi w wątku** (Reply in Thread).
    - Treść draftu: Asertywna odmowa (zgodnie z promptem Marty).

**Ustalenia:**
- Mamy w pełni funkcjonalne MVP (v5). Agent czyta, myśli, odpisuje w wątku.
- Prompt Marty wymaga lekkiego tuningu (styl, ton), ale technologia działa.
- **Zasady Pamięci:** Wprowadzono rygor: Zero zapisu w `GEMINI.md`, wszystko w `session_notes.md`.

**Następny krok (Jutro):**
- **Tuning Promptu:** Dopracowanie stylu Marty na podstawie naszych test cases (Scope Creep, Panika, Vibe Check).
- **Nagranie Demo:** Skoro technologia działa, czas na wideo dla klientów.
---
## 2025-12-09, 12:45 - Sesja #18 (MVP Sukces: Magic Gmail Działa)

**Co robiliśmy:**
- **Walka z n8n:** Naprawiono błędy mapowania JSON-a (`[object Object]`) i parsowania odpowiedzi AI.
- **Wdrożenie v4:** Ręcznie skonfigurowano węzły w n8n, dodając "Parser JSON" i poprawne mapowanie zmiennych Gmaila (adres nadawcy ukryty w tablicy).
- **Smoke Test (Bojowy):** Wysłano maila "Scope Creep" z zewnętrznej skrzynki.
- **Wynik:** **SUKCES.** Agent odebrał maila, zanalizował go i utworzył poprawny Draft w folderze "Wersje robocze" Gmaila. Powiadomienie na Slacku również dotarło.

**Ustalenia:**
- Mamy działające MVP. Agent tworzy drafty, ale jako **nowe wiadomości**, a nie w wątku (Reply).
- Treść generowana przez Martę wymaga doszlifowania (stylistycznie).

**Następny krok (Jutro):**
- **Wątkowanie:** Sprawdzić, jak rozwiązano "Reply in Thread" w workflow PRO (`agent_AI_gmail.json`), który wcześniej analizowaliśmy. Celem jest sklejanie draftu z oryginalnym mailem.
- **Tuning Pisarza:** Poprawa promptu Marty, żeby odpowiedzi były bardziej naturalne/lepsze.
- **Nagranie Demo:** Dopiero po dopracowaniu wątków i stylu.
---
## 2025-12-09, 11:30 - Sesja #17 (Postgres Fix & Magic Workflow v4)

**Co robiliśmy:**
- **Naprawa Infrastruktury (Docker Network):**
    - Rozwiązano problem połączenia n8n <-> Postgres (`bad address`).
    - N8n i Postgres znajdowały się w odseparowanych sieciach dockerowych (`bridge` vs `agent_net`).
    - Zastosowano komendę `docker network connect agent_net n8n`, co skutecznie połączyło kontenery.
    - Połączenie z bazą danych w n8n świeci na zielono (Host: `postgres`).
- **Workflow "Magic Gmail" (Ewolucja v1 -> v4):**
    - Przeszliśmy przez bolesny proces debugowania workflow w n8n.
    - Problemy: Parsowanie JSON z OpenAI (zwracany jako string), błędy mapowania zmiennych (`[object Object]`), niezgodność wersji węzłów.
    - **Rozwiązanie (v4):** Stworzono finalny plik `n8n_workflow_magic_gmail_v4_final.json`.
    - Kluczowe zmiany w v4:
        - Dodano węzeł `Code` ("Parser JSON") do bezpiecznego zamieniania tekstu z AI na obiekt.
        - Zastosowano `JSON.stringify()` w promptach, aby uniknąć błędów mapowania.
        - Zaszyto prompty systemowe (Bramkarz, Marta) bezpośrednio w kodzie JSON.
- **Dokumentacja:** Stworzono plik `product_mvp/workflow_documentation_v2.md` opisujący logikę procesu.

**Ustalenia:**
- Workflow v4 jest wersją ostateczną do Smoke Testu.
- Postgres jest gotowy do działania (pamięć długoterminowa jest możliwa w przyszłości).

**Następny krok:**
- Przeprowadzenie Smoke Testu (Wysłanie maila "Scope Creep").
- Nagranie wideo demo (Loom) dla Marty.
---
## 2025-12-08, 15:00 - Sesja #16 (Wielki Sukces: Agent Żyje)

**Co robiliśmy:**
- **Google OAuth:** Finalnie skonfigurowano i naprawiono błąd braku aktywnego API w Google Console.
- **Postgres:** Postawiono kontener Postgresa na VPS i spięto go siecią Dockerową z n8n (pamięć Agenta działa).
- **Logika Workflow:** Naprawiono błąd w Agencie, który na sztywno oczekiwał transkrypcji. Zastosowano formułę warunkową obsługującą zarówno Tekst jak i Audio.
- **Smoke Test (Tekst):** **SUKCES.** Agent odebrał komendę na Slacku ("sprawdź maile"), połączył się z Gmailem, pobrał dane i odpisał.
- **Smoke Test (Audio):** Wykryto błąd formatu pliku przy notatkach głosowych ze Slacka (OpenAI odrzucił plik). Do poprawki.

**Ustalenia:**
- Infrastruktura jest kompletna (VPS + n8n + Postgres + OAuth).
- Agent działa w trybie "na żądanie" (Slack Trigger).

**Następny krok:**
- **Fix Audio:** Dodać obsługę formatów audio ze Slacka (sprawdzenie mimetype).
- **Pivot na MVP dla Marty:** Przebudowa workflow (lub stworzenie nowego), gdzie Triggerem jest "Nowy Email" (Gmail Trigger), a Agent automatycznie tworzy draft odpowiedzi.
---
---
## 2025-12-08, 14:40 - Sesja #16 (Google OAuth - Sukces)

**Co robiliśmy:**
- **Konfiguracja Google OAuth:** Przeszliśmy przez pełny proces w Google Cloud Console.
- **Rozwiązanie problemu "Error 414":** Błąd "URI Too Long" został naprawiony poprzez ręczne ograniczenie Scopes do samego `.../auth/gmail.modify` (zamiast pełnej listy n8n).
- **Weryfikacja:** Pomyślnie połączono konto Google (`michal.potoczny.92@gmail.com`) z instancją n8n na VPS.
- **Status:** **Google OAuth Configured ✅**. Droga do narzędzi Gmaila jest otwarta.

**Ustalenia:**
- Używamy **jednego wąskiego uprawnienia** (`gmail.modify`), co wystarcza do czytania i tworzenia draftów, a jest bezpieczniejsze i nie psuje autoryzacji.
- Należy pamiętać, że aplikacja jest w trybie "Testing" i wymaga odnawiania tokenu co 7 dni (chyba że przejdziemy na Production, ale na razie MVP).

**Następny krok:**
- Sprawdzenie/Uruchomienie bazy Postgres na VPS (niezbędne dla pamięci Agenta).
- Wdrożenie workflow `n8n_workflow_agent_openai_only.json` i podpięcie Credentials (OpenAI + Google + Postgres).
---
---
## 2025-12-05, 14:20 - Sesja #15 (Konfiguracja Google OAuth)

**Co robiliśmy:**
- **Konfiguracja Google Cloud:** Użytkownik przeszedł przez proces tworzenia projektu i konfiguracji OAuth.
- **Problem Wyboru (Internal vs External):** Przeanalizowano opcję zakupu Google Workspace (Internal) vs darmowy Gmail (External).
- **Decyzja Strategiczna:** Mimo chęci zakupu Workspace, wybrano **darmowy Gmail (External)** dla szybkości wdrożenia MVP demo. Przejście na Workspace zaplanowano po pierwszym kliencie.
- **Status:** Utknięto w połowie procesu konfiguracji "OAuth Consent Screen".

**Ustalenia:**
- **Tryb:** External.
- **Test Users:** Wymagane dodanie adresu email użytkownika (tego samego co admin).
- **Cel:** Uzyskanie `Client ID` i `Client Secret` do wklejenia w n8n.

**Następny krok:**
- Dokończenie konfiguracji OAuth (dodanie Test User, wygenerowanie Credentials).
- Wklejenie kluczy do n8n.
- Konfiguracja Postgresa na VPS.
---
---
## 2025-12-05, 13:30 - Sesja #14 (Działający Slack Bot & Plan na Agenta PRO)

**Co robiliśmy:**
- **Sukces MVP:** Uruchomiono działający workflow Slack -> n8n -> OpenAI -> Slack (`n8n_workflow_simple_v4.json`).
- **Implementacja Osobowości:** Wdrożono prompt "Marta - Asertywna Właścicielka" i poprawiono formatowanie na Markdown (kompatybilne ze Slackiem).
- **Test Bojowy:** Przeprowadzono symulację "Scope Creep" na żywo. Bot poprawnie zidentyfikował prośbę o darmową pracę i odpisał asertywną odmową z cennikiem.
- **Decyzja Strategiczna (Pivot):** Zrezygnowano z nagrywania prostego demo "kopiuj-wklej". Użytkownik zdecydował się na budowę **zaawansowanego Agenta** (Skrzynka Pocztowa z narzędziami Gmail), aby demo było wiarygodne i pokazywało realną wartość ("Wiara w produkt").
- **Przygotowanie Agenta PRO:** Stworzono plik `n8n_workflow_agent_openai_only.json`, który jest adaptacją zaawansowanego workflow z Akademii Automatyzacji (zmieniono model Anthropic na OpenAI, zachowano strukturę Tools/Memory).

**Ustalenia:**
- Nie idziemy na skróty. Demo ma pokazywać realną integrację Gmail <-> Slack.
- Wymagana konfiguracja Gmail OAuth w Google Cloud Console.
- Wymagane postawienie bazy Postgres (lub użycie wbudowanej) na VPS dla obsługi pamięci długoterminowej Agenta.

**Następny krok:**
- Konfiguracja Google OAuth (Client ID/Secret) dla n8n.
- Uruchomienie kontenera Postgres na VPS.
- Szczegółowa analiza i konfiguracja węzłów w `n8n_workflow_agent_openai_only.json`.
---
---
## 2025-12-05, 12:45 - Sesja #13 (Walka z n8n i Wdrożenie OpenAI)

**Co robiliśmy:**
- **Próba wdrożenia OpenAI:** Podjęto próbę dodania węzła `OpenAI Chat Model` do istniejącego workflow "Echo" w n8n.
- **Problem Techniczny:** Wystąpiły problemy z mapowaniem zmiennych (Slack Channel ID) po wstawieniu nowego węzła. Węzeł końcowy "zgubił" kontekst Triggera.
- **Blokada Wizualna:** Brak możliwości podejrzenia screenów błędów (ograniczenia `.gitignore` / bezpieczeństwa) utrudnił diagnozę "na ślepo".
- **Decyzja:** Przerwanie walki "na żywo". Plan naprawczy: Użytkownik dostarczy kod JSON workflow w kolejnej sesji, a System odeśle poprawiony kod do wklejenia.
- **Status:** Workflow n8n jest obecnie "rozgrzebany" (dodany moduł OpenAI, ale zerwane połączenia).

**Ustalenia:**
- #Waski: Gotowy z treścią posta i DM-a (czeka na wideo).
- #Siara: Przejmuje pełną kontrolę nad kodem workflow w następnym kroku.
- **Next Step:** Naprawa workflow metodą "Copy-Paste JSON" (najpewniejsza metoda bez screenów).

**Następny krok:**
- Pobraniem JSON workflow od użytkownika.
- Naprawa powiązań (Mapping) w kodzie.
- Wdrożenie poprawionego workflow.
- Nagranie demo.
---
---
## 2025-12-05, 12:00 - Sesja #12 (Strategia Contentowa & Demo Scope Creep)

**Co robiliśmy:**
- **Strategia LinkedIn:** Opracowano finalną treść posta "Powrót z Warsztatu". Przekaz: "Nudna stabilność (VPS) > Efektowne zabawki (Localhost)".
- **Korekta Kursu:** Zrezygnowano z tłumaczenia się z nieobecności ("Tłumaczą się winni"). Skupiono się na wartości biznesowej (ciągłość działania 24/7).
- **Plan Demo:** Zaplanowano nagranie wideo (Loom) pokazującego scenariusz "Scope Creep" na żywo w Slacku (bez pokazywania Gmaila).
- **Podział Ról:** #Waski dostał formalny zakaz dotykania n8n. Technikaliami zajmuje się #Siara (i Michał).
- **Przygotowanie n8n:** Dostarczono prompt systemowy ("Marta - Asertywna Dyplomacja") do wklejenia w węzeł OpenAI w n8n.

**Ustalenia:**
- **Strategia Outreachu:** Najpierw publikujemy post z wideo (Social Proof), a dopiero POTEM wysyłamy zaproszenia do grupy docelowej ("Marta"). Świeży content ma zwiększyć Acceptance Rate.
- **USP:** Wideo ma pokazać "Draft w 3 sekundy" + "Ludzką kontrolę" (Human-in-the-Loop).

**Następny krok:**
- Konfiguracja węzła OpenAI w n8n (według dostarczonego promptu).
- Nagranie wideo demo (Slack: "Scope Creep").
- Publikacja posta i start kampanii zaproszeń.
---
---
## 2025-12-04, 21:45 - Sesja #11 (Integracja Slack <-> n8n VPS)

**Co robiliśmy:**
- **Rozwiązano problem z brakiem komunikacji:** Zdiagnozowano, że Slack wysyłał dane, ale n8n (w trybie edycji) ich nie wyświetlał bez trybu manualnego "Execute", a w trybie Active (Production) działał "po cichu".
- **Skonfigurowano poprawnie Slack API:**
    - Dodano brakujące uprawnienia (`channels:read`, `message.channels`, `message.im`).
    - Wykonano "Reinstall to Workspace" po zmianie uprawnień.
    - Skonfigurowano **Request URL** w dwóch miejscach: "Event Subscriptions" i "Interactivity & Shortcuts".
- **Zrealizowano "Handshake" (Uścisk dłoni):**
    - Zweryfikowano Test URL (w trybie manualnym).
    - Zweryfikowano Production URL (w trybie Active).
    - Uzyskano status **Verified** w panelu Slacka.
- **Zrealizowano Workflow "Echo" (Full Loop):**
    - Stworzono workflow: Slack Trigger -> Slack Send Message.
    - Skonfigurowano dynamiczne ID kanału (`{{ $json.channel }}`), dzięki czemu bot odpisuje dokładnie tam, skąd przyszła wiadomość.
    - Przetestowano na żywo: Bot poprawnie odsyła treść wiadomości użytkownika ("Echo test 123" -> "Odebrałem: Echo test 123").

**Ustalenia:**
- Infrastruktura jest gotowa i przetestowana ("rura drożna").
- Bot słucha na kanałach publicznych (gdzie zostanie zaproszony) i w wiadomościach prywatnych (DM).
- N8N na VPS działa stabilnie, obsługuje Webhooki produkcyjne.

**Następny krok:**
- **Migracja Logiki:** Wpięcie OpenAI (Agent Draftujący - Marta) pomiędzy Trigger a Send Message.
- Implementacja Promptu Systemowego Marty w n8n.
- Testy scenariuszy (Scope Creep, Panika) przez Slacka.
---
---
## 2025-12-04, 12:30 - Sesja #10 (Wdrożenie VPS i Docker)

**Co robiliśmy:**
- Zdiagnozowano problemy z tunelem n8n na localhost (zrywanie połączeń, błędy "Challenge" od Slacka).
- Podjęto decyzję o migracji na stabilny VPS (Mikr.us).
- Zakupiono i uruchomiono serwer VPS (srv49.mikr.us).
- Skonfigurowano środowisko na VPS:
    - Połączenie SSH.
    - Aktualizacja systemu Linux.
    - Instalacja Dockera.
    - Instalacja n8n za pomocą skryptu `n8n_install`.
- Uzyskano publiczny, stabilny adres SSL dla Agenta: `https://kacper140-20140.wykr.es`.
- Założono konto właściciela na nowej instancji n8n.

**Ustalenia:**
- Od teraz pracujemy WYŁĄCZNIE na instancji VPS (`wykr.es`).
- Localhost zostaje porzucony (służy tylko do wyeksportowania dotychczasowej pracy).
- Adres Agenta dodany do zakładek.

**Następny krok:**
- Migracja workflowów (Agent Draftujący) z localhosta na VPS.
- Konfiguracja Slack Triggera na nowym adresie (Webhook URL).
- Finalne spięcie Slack <-> n8n <-> Slack (Full Loop).
---
---
## 2025-12-03, 12:00 - Sesja #9 (Instalacja n8n i Setup Slacka)

**Co robiliśmy:**
- Zmiana strategii technologicznej: Rezygnacja z Make.com (problemy z UX/pollingiem) na rzecz własnej instancji n8n (lokalnie + tunel).
- Zainstalowano n8n na Windows (przez npm) i uruchomiono z flagą `--tunnel` (dostęp z zewnątrz).
- Rozpoczęto konfigurację integracji Slack <-> n8n.
- Wyjaśniono architekturę: Slack App (Bot) do pisania, Tunel do odbierania komend.
- Ustalono, że budujemy rozwiązanie oparte na "Bot User" (`xoxb`), a nie "User OAuth" (symulacja użytkownika).

**INSTRUKCJA KONFIGURACJI BOTA (Do wykonania):**
1.  **Tworzenie:** [api.slack.com/apps](https://api.slack.com/apps) -> Create New App -> From scratch -> Nazwa "Agent Draftujący".
2.  **Uprawnienia (Scopes):** Menu "OAuth & Permissions" -> Sekcja "Bot Token Scopes" -> Dodaj: `chat:write`, `channels:history`, `groups:history`, `im:history`.
3.  **Instalacja:** Na górze strony "OAuth & Permissions" -> "Install to Workspace" -> Allow.
4.  **Token:** Skopiuj "Bot User OAuth Token" (zaczyna się od `xoxb-...`).
5.  **Integracja:** W n8n -> Credentials -> Add "Slack API" -> Wklej Token.

**Ustalenia:**
- N8N stoi lokalnie na `localhost:5678` i jest tunelowany do Internetu.
- Slack App "Agent Draftujący" jest w trakcie tworzenia.
- Celem jest sterowanie Agentem z poziomu Slacka (telefonu/komputera) w czasie rzeczywistym.

**Następny krok:**
- Dokończenie konfiguracji Slack App (pobranie tokenu `xoxb` wg instrukcji powyżej).
- Wpięcie tokenu do n8n (Credentials).
- Uruchomienie pierwszego workflow "Echo" (Slack -> n8n -> Slack).
---
---
## 2025-12-02, 11:00 - Sesja #8 (Weryfikacja Tech Stacku: Make vs n8n)

**Co robiliśmy:**
- Zweryfikowano technicznie scenariusz w Make.com (Gmail -> OpenAI -> Gmail Draft).
- Zidentyfikowano ograniczenie UX w Make: opóźnienie w przetwarzaniu (polling co 15 min) vs oczekiwanie użytkownika na "Instant".
- Przeanalizowano alternatywne podejście "Instant": Google Apps Script (odrzucone jako overengineering) vs Forward na Slacka.
- Przeanalizowano potencjał n8n w oparciu o dostarczony plik JSON ("5 Agentów AI").
- Zaproponowano nowy workflow oparty na n8n + Slack: Forward maila na kanał Slack -> n8n generuje draft -> Przyciski akcji na Slacku.

**Ustalenia:**
- Make.com działa poprawnie technicznie, ale UX "przeciągania maili" ma wady (opóźnienie).
- Rozwiązanie n8n + Slack oferuje lepszy "Time to Value" (Instant) i efekt WOW (sterowanie z poziomu czatu).
- Wymagana decyzja dotycząca wdrożenia n8n (potrzeba tunelowania dla lokalnej instancji vs VPS).

**Następny krok:**
- Decyzja: Czy nagrywamy Demo na Make (symulując szybkość) czy migrujemy na n8n (dla lepszego UX w demo).
---
---
## 2025-12-02, 10:00 - Sesja #8 (Fixing Hallucinations & Master Prompt)

**Co robiliśmy:**
- Zdiagnozowano problem z Agentem Draftującym: halucynacje (TikTok zamiast WWW) i używanie zakazanego słowa "dowieźć".
- Wykryto niespójność instrukcji w starych plikach promptów.
- Skupiono się na naprawie Master Promptu dla Make.com (`product_mvp/make_scenarios_config/system_prompt_make_v1.md`).
- Wprowadzono **absolutny zakaz** słowa "dowieźć" i dodano alternatywy ("działa", "pracuje").
- Dodano sekcję **CRITICAL: Wierność Kontekstowi**, aby wyeliminować wymyślanie kanałów (TikTok) i formatów przez model.

**Ustalenia:**
- Master Prompt (`system_prompt_make_v1.md`) jest jedynym źródłem prawdy dla Make.com.
- Model ma twardy zakaz zgadywania kanałów komunikacji, jeśli nie wynikają one wprost z treści maila klienta.
- Zaktualizowany prompt jest gotowy do wdrożenia w module OpenAI w Make.com.

**Następny krok:**
- Ponowny test scenariusza w Make.com z nowym promptem.
---
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