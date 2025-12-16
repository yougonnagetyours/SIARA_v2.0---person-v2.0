# 📧 Dokumentacja Workflow: Agent Magic Gmail v5 (On-Demand)

> **Wersja:** v5.0 (Workflow JSON)
> **Dokumentacja:** v3.1 (Zaktualizowana o Personalizację)
> **Status:** Released
> **Data:** 16.12.2025
> **Plik źródłowy:** `projects/001_Agent Magic Gmail v5 (On-Demand)/AD/project.json`

## 🧠 Logika Biznesowa
System działa w trybie **"Na Żądanie"**. Agent nie dotyka skrzynki, dopóki Użytkownik (Marta) nie nada wyraźnego sygnału.

1.  **Input:** Użytkownik nadaje etykietę **"Draft Asystent"**.
2.  **Process:** System pobiera maila, usuwa etykietę wejściową (sygnał "W toku"), generuje treść.
3.  **Output:** System tworzy draft, nadaje etykietę **"Draft Gotowy"** i powiadamia na Slacku.

## 💎 Kluczowy Wyróżnik: Hiper-Personalizacja
System nie generuje "generycznego AI". Posiada zaszyty **System Prompt** (osobowość "Marta"), który narzuca:
*   **Tone of Voice:** Asertywny, konkretny, profesjonalny (bez "Mam nadzieję, że mail zastanie Cię w zdrowiu").
*   **Styl:** Krótkie zdania, wypunktowania, brak lania wody.
*   **Słownik Zakazany:** (np. zakaz używania słowa "dowieźć" w kontekście projektu).
*   **Strategia:** W zależności od typu maila (Scope Creep / Awaria / Negocjacje) dobiera inną taktykę odpowiedzi.

## 🔄 Schemat Techniczny (Nodes)

```mermaid
graph TD
    %% Triggers
    TR1[⏰ Schedule Trigger (co 15 min)] --> GET
    TR2[💬 Slack Trigger] -->|Komenda: 'draftuj'| IF{Warunek IF}
    IF -->|Treść == 'draftuj'| GET
    
    %% Main Flow
    GET[📩 Get Messages<br/>(Label: Draft Asystent)] --> RM[🗑️ Usuń Etykietę<br/>'Draft Asystent']
    RM --> AI[🧠 AI Pisarz<br/>(Persona: Marta - Styl Własny)]
    AI --> DRAFT[📝 Create Draft<br/>(Gmail)]
    DRAFT --> ADD[🏷️ Dodaj Etykietę<br/>'Draft Gotowy']
    ADD --> SLACK[🔔 Powiadomienie Slack<br/>(z linkiem do Gmail)]
```

## ⚙️ Szczegółowa Konfiguracja Węzłów

### 1. Wyzwalacze (Triggers)
*   **Schedule Trigger:** Uruchamia się cyklicznie co 15 minut.
*   **Slack Trigger:**
    *   **Event:** `On Message`
    *   **Kanał:** `general` (ID: `C0A1HQ6UV5G`)
    *   **Działanie:** Uruchamia workflow natychmiast po wykryciu wiadomości.
*   **IF (Filtr Komendy):**
    *   Sprawdza, czy treść wiadomości ze Slacka to dokładnie słowo `draftuj`.

### 2. Wejście (Gmail Input)
*   **Get many messages:**
    *   **Filtr Etykiety:** `Label_8388846993740763261` (Mapowanie: **"Draft Asystent"**).
    *   **Limit:** Pobiera max 10 wiadomości w jednej paczce.

### 3. Przetwarzanie (Processing)
*   **Usuń Etykietę (Start):**
    *   Usuwa `Label_8388846993740763261`.
    *   **Cel:** Zapobiega pętlom (żeby nie pobrać tego samego maila ponownie) i czyści widok "Do zrobienia" u użytkownika.
*   **AI Pisarz (Marta):**
    *   **Model:** `gpt-4o`.
    *   **Prompt Systemowy:** "Asertywna Właścicielka".
    *   **Funkcja:** Naśladuje styl Marty tak wiernie, że klient nie rozpoznaje, że to automat.

### 4. Wyjście (Gmail Output)
*   **Create Draft:**
    *   Tworzy wiadomość w folderze `Drafts`.
    *   Adresat: Nadawca oryginalnego maila.
*   **Oznacz jako Gotowe:**
    *   Dodaje etykietę `Label_8698956675052924918` (Mapowanie: **"Draft Gotowy"**).
    *   **Cel:** Wizualna sygnalizacja dla użytkownika, że praca została wykonana.

### 5. Powiadomienie (Slack)
*   **Slack:**
    *   Wysyła wiadomość na kanał `general`.
    *   **Treść:** "🔔 Nowy Draft! Od: [Nadawca] | Temat: [Temat]".
    *   **Link:** Deeplink kierujący bezpośrednio do edycji draftu (`https://mail.google.com/mail/u/0/#drafts/[ID]`).

## 🛡 Bezpieczeństwo
*   AI nigdy nie wysyła maili automatycznie (tylko tworzy Drafty).
*   AI przetwarza tylko maile wskazane przez człowieka (etykieta).
*   Proces jest widoczny dzięki zmianie etykiet.
