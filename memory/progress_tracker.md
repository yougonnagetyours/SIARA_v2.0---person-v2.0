## 🎯 AKTUALNY ETAP

**2. Tydzień 2: Pivot na MVP "Skrzynka Pocztowa" (Real Value)**

Cel: Zmiana logiki z "Agent na żądanie" (Slack) na "Automat w tle" (Gmail Trigger). Agent ma sam wyłapywać maile i przygotowywać drafty.

Status:
- ✓ **INFRASTRUKTURA:** VPS (Mikr.us) + Docker + n8n + Postgres (Pamięć).
- ✓ **INTEGRACJA:** Google OAuth skonfigurowany (Scope: `gmail.modify`).
- ✓ **SMOKE TEST 1 (Slack Tekst):** SUKCES. Agent czyta maile na komendę.
- ❌ **SMOKE TEST 2 (Slack Audio):** BŁĄD. Problemy z formatem plików audio.
- 🔄 **LOGIKA:** Przebudowa workflow pod "New Email Trigger".

## 🚧 BLOKERY

- **Brak Workflow MVP:** Trzeba stworzyć/przerobić workflow, aby reagował na nowe maile, a nie na komendę ze Slacka.

## 🕒 HISTORIA

### 0. PRZYGOTOWANIE (2025-11-26)
- ✓ Zdefiniowanie Persony (Michał - Inżynier Procesów).
- ✓ Określenie grupy docelowej (Agencje Marketingowe).
- ✓ Restrukturyzacja projektu.

### 1. TECH STACK (2025-12-04)
- ✓ Decyzja o porzuceniu localhosta (problemy z tunelem).
- ✓ Wdrożenie na VPS (Mikr.us) dla stabilności demo.
- ✓ Konfiguracja Google OAuth i Postgres (2025-12-08).
