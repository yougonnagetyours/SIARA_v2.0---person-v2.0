# 📧 Dokumentacja Workflow: Agent Magic Gmail v2 (MVP)

> **Cel:** Automatyczne przygotowywanie wersji roboczych (draftów) odpowiedzi na maile biznesowe, z zachowaniem pełnej kontroli użytkownika.
> **Technologia:** n8n + OpenAI (GPT-4o) + Gmail + Slack.

## 🔄 Schemat Procesu (Logic Flow)

```mermaid
graph TD
    A[📩 Gmail Trigger] -->|Nowy email| B[🧠 AI Bramkarz]
    B --> C{Czy ważny?}
    C -->|⛔ Nie (Spam/News)| D[Kosz / Ignoruj]
    C -->|✅ Tak (Klient)| E[✍️ AI Pisarz (Marta)]
    E --> F[📝 Utwórz Draft w Gmail]
    F --> G[🔔 Powiadomienie Slack]
```

## 🛠 Opis Węzłów (Nodes)

### 1. Gmail Trigger (Czuwanie)
- **Działanie:** Sprawdza skrzynkę co 1 minutę.
- **Filtry:** Pobiera tylko maile **nieprzeczytane** z Inboxa.
- **Hard Filter:** Wycina na wejściu oczywisty spam (`-from:noreply`, `-subject:faktura`, `-category:promotions`).

### 2. AI Bramkarz (Decyzja)
- **Model:** `gpt-4o-mini` (Szybki i tani).
- **Rola:** Filtr biznesowy.
- **Zadanie:** Analizuje treść i zwraca JSON: `{ "needs_reply": true/false, "reason": "..." }`.
- **Logika:**
    - Odrzuca: Newslettery, faktury, powiadomienia z systemów, krótkie "Dzięki".
    - Przepuszcza: Pytania od klientów, leady, problemy projektowe.

### 3. Switch (IF Node)
- **Działanie:** Rozdziela ruch na podstawie decyzji Bramkarza.
- **Ścieżka False:** Kończy pracę (nic nie robi).
- **Ścieżka True:** Przekazuje maila do Pisarza.

### 4. AI Pisarz (Generacja)
- **Model:** `gpt-4o` (Wysoka jakość, rozumienie niuansów).
- **Persona:** "Marta - Asertywna Właścicielka".
- **Styl:** Konkretny, partnerski, bez korpo-bełkotu (zakaz słowa "dowieźć").
- **Scenariusze:** Rozpoznaje sytuację (Scope Creep, Panika, Negocjacje) i dobiera strategię odpowiedzi.
- **Output:** Gotowy kod HTML wiadomości.

### 5. Create Draft (Gmail)
- **Działanie:** Tworzy w Gmailu wiadomość w folderze **Wersje robocze**.
- **Bezpieczeństwo:** Nic nie jest wysyłane do klienta. Użytkownik musi wejść i kliknąć "Wyślij".

### 6. Slack Notification (Raport)
- **Działanie:** Wysyła powiadomienie na wybrany kanał.
- **Treść:** "🔔 Nowy Draft! Od: [Klient]. Temat: [Temat]. Sprawdź Gmaila."

## 🛡 Bezpieczeństwo i Kontrola (Human-in-the-Loop)

1. **Brak Automatycznej Wysyłki:** Agent nigdy nie wysyła wiadomości samodzielnie.
2. **Filtr Wstępny:** AI Bramkarz chroni przed generowaniem draftów na spam.
3. **Edytowalność:** Draft w Gmailu jest w pełni edytowalny przez człowieka przed wysłaniem.
