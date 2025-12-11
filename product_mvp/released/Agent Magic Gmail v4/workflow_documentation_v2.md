# 📧 Dokumentacja Workflow: Agent Magic Gmail v2.1 (MVP - On-Demand)

> **Zmiana (v2.1):** Przejście z modelu "Full Auto" na model "On-Demand" (Na Żądanie).
> **Cel:** Użytkownik decyduje, na które maile AI ma przygotować odpowiedź, nadając im etykietę. 100% kontroli, 0% ryzyka spamu.

## 🔄 Schemat Procesu (Logic Flow)

```mermaid
graph TD
    A[👤 Marta (User)] -->|Nadaje etykietę 'Draft Asystent'| B[📩 Gmail Trigger]
    B -->|Pobierz maila z etykietą| C[🗑️ Remove Label]
    C -->|Etykieta usunięta - status 'W toku'| D[✍️ AI Pisarz (Marta)]
    D --> E[📝 Utwórz Draft w Gmail]
    E --> F[🔔 Powiadomienie Slack]
```

## 🛠 Opis Węzłów (Nodes)

### 1. Gmail Trigger (Nasłuch)
- **Metoda:** Polling (co 1 min).
- **Filtr:** Pobiera maile **TYLKO** z etykietą `Draft Asystent`.
- **Zasada:** Ignoruje wszystko inne (spam, newslettery, prywatne).

### 2. Remove Label (Czyszczenie)
- **Działanie:** Usuwa etykietę `Draft Asystent` z procesowanego maila.
- **Cel:** Zapobiega pętli (żeby n8n nie pobrał tego samego maila 2 razy) i sygnalizuje Marcie, że "zamówienie zostało przyjęte".

### 3. AI Pisarz (Marta)
- **Model:** `gpt-4o`.
- **Rola:** "Asertywna Właścicielka".
- **Zadanie:** Analizuje treść i pisze gotowy kod HTML odpowiedzi.
- **Inteligencja:** Sama rozpoznaje typ problemu (Scope Creep, Panika, Negocjacje) i dobiera strategię.

### 4. Create Draft (Gmail)
- **Działanie:** Tworzy wiadomość w folderze **Wersje robocze**.
- **Odbiorca:** Nadawca oryginalnego maila.
- **Treść:** Wygenerowana przez AI.

### 5. Slack Notification (Opcjonalne)
- **Treść:** "✅ Draft gotowy dla: [Klient]. Sprawdź Gmaila."

## 🛡 Bezpieczeństwo i UX

1. **Pełna Kontrola:** Automat nie dotknie maila, póki Marta nie nada etykiety.
2. **Czysty Inbox:** Etykieta znika po pobraniu maila przez robota, co daje wizualny feedback "Robimy to".
3. **Brak Halucynacji:** AI pracuje tylko na wyselekcjonowanym materiale biznesowym.