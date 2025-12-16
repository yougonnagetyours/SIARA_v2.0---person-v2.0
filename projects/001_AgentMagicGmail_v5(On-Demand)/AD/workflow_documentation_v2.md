# 📧 Dokumentacja Workflow: Agent Magic Gmail v5 (On-Demand + Slack Trigger)

> **Wersja:** v5.0
> **Typ:** On-Demand (Na Żądanie)
> **Zasada działania:** Marta (Użytkownik) oznacza maile etykietą -> AI przygotowuje drafty. 100% kontroli nad tym, CO jest przetwarzane.

## 🔄 Schemat Procesu (Logic Flow)

```mermaid
graph TD
    User[👤 Marta (User)] -->|1. Oznacza maile etykietą 'Draft Asystent'| Gmail
    
    A1[⏰ Schedule Trigger (co 15 min)] --> B[📩 Pobierz maile z etykietą 'Draft Asystent']
    A2[💬 Slack Trigger (komenda 'draftuj')] -->|Sprawdź czy 'draftuj'| B
    
    B --> C[🗑️ Usuń Etykietę 'Draft Asystent' (Start)]
    C --> D[✍️ AI Pisarz (Marta - gpt-4o)]
    D --> E[📝 Utwórz Draft w Gmail]
    E --> F[🏷️ Dodaj Etykietę 'Draft Gotowy']
    F --> G[🔔 Powiadomienie Slack z Linkiem]
```

## 🛠 Opis Węzłów (Nodes)

### 0. Rola Użytkownika (Marta)
- **Akcja:** Przegląda pocztę i jeśli widzi maila wymagającego "typowej" odpowiedzi, nakłada etykietę `Draft Asystent`.
- **Cel:** Filtracja. AI nie dotyka maili prywatnych, newsletterów ani spraw krytycznych, których nie oznaczymy.

### 1. Wyzwalacze (Triggers)
- **Schedule Trigger:** Uruchamia się automatycznie co 15 minut i sprawdza, czy Marta coś zleciła.
- **Slack Trigger:** Nasłuchuje na kanale. Jeśli użytkownik napisze "draftuj", natychmiast sprawdza pocztę (wymuszenie procesu).

### 2. Get Many Messages (Gmail)
- **Działanie:** Pobiera listę maili oznaczonych etykietą `Draft Asystent` (ID: `Label_8388846993740763261`).
- **Limit:** Max 10 maili na jeden przebieg.

### 3. Usuń Etykietę (Start)
- **Działanie:** Usuwa etykietę "Draft Asystent" z procesowanego wątku.
- **Cel:** Sygnalizacja, że zlecenie zostało przyjęte do realizacji (mail znika z widoku "Do zrobienia").

### 4. AI Pisarz (Marta)
- **Model:** `gpt-4o`.
- **System Prompt:** "Asertywna Właścicielka".
- **Logika:** Analizuje treść maila, rozpoznaje intencję (np. Scope Creep) i generuje gotowy kod HTML odpowiedzi.

### 5. Create Draft (Gmail)
- **Działanie:** Tworzy fizyczny draft w folderze "Wersje robocze".
- **Odbiorca:** Nadawca oryginalnego maila.

### 6. Oznacz jako Gotowe (Gmail)
- **Działanie:** Nakłada na wątek nową etykietę `Draft Gotowy` (ID: `Label_8698956675052924918`).
- **Efekt Wizualny:** W skrzynce odbiorczej pojawia się zielona etykieta, sygnalizująca Marcie: "Sprawdź mnie i wyślij".

### 7. Powiadomienie Slack
- **Treść:** "🔔 Nowy Draft! Od: [Klient] | Temat: [Temat]".
- **Deeplink:** Link kierujący bezpośrednio do edycji tego draftu w Gmailu (`https://mail.google.com/mail/u/0/#drafts/[ID]`).

## 🛡 Bezpieczeństwo i UX

1. **Selekcja (Human-First):** AI nie ma dostępu do całej skrzynki, tylko do tego, co wskaże człowiek etykietą `Draft Asystent`.
2. **Dual Trigger:** Automat działa w tle (co 15 min), ale można go "popędzić" ze Slacka w pilnej sprawie.
3. **Statusy Wizualne:** Mail przechodzi drogę: `Draft Asystent` (User) -> `Przetwarzanie` (n8n usuwa etykietę) -> `Draft Gotowy` (n8n dodaje nową).
4. **Link do Akcji:** Powiadomienie na Slacku skraca ścieżkę do jednego kliknięcia.
