## 🎯 AKTUALNY ETAP

**2. Tydzień 2: Pivot na MVP "Skrzynka Pocztowa" (Real Value)**

Cel: Zmiana logiki z "Agent na żądanie" (Slack) na "Automat w tle" (Gmail Trigger). Agent ma sam wyłapywać maile i przygotowywać drafty.

Status:
- ✓ **INFRASTRUKTURA:** VPS (Mikr.us) + Docker + n8n + Postgres (Pamięć).
- ✓ **SIECI:** Naprawiono komunikację międzykontenerową (Docker Network).
- ✓ **INTEGRACJA:** Google OAuth skonfigurowany (Scope: `gmail.modify`).
- ✓ **MVP (v5):** Workflow w pełni funkcjonalny. Agent tworzy drafty jako **odpowiedzi w wątku** (Reply in Thread).
- 🔄 **DOSTRAJANIE:** Trwa tuning promptu Marty (styl komunikacji).

## 🚧 BLOKERY

- (Brak)

## 🕒 HISTORIA

### 0. PRZYGOTOWANIE (2025-11-26)
- ✓ Zdefiniowanie Persony (Michał - Inżynier Procesów).
- ✓ Określenie grupy docelowej (Agencje Marketingowe).
- ✓ Restrukturyzacja projektu.

### 1. TECH STACK (2025-12-04)
- ✓ Decyzja o porzuceniu localhosta (problemy z tunelem).
- ✓ Wdrożenie na VPS (Mikr.us) dla stabilności demo.
- ✓ Konfiguracja Google OAuth i Postgres (2025-12-08).
- ✓ Pierwszy udany Smoke Test MVP (2025-12-09).


### 0. PRZYGOTOWANIE (2025-11-26)
- ✓ Zdefiniowanie Persony (Michał - Inżynier Procesów).
- ✓ Określenie grupy docelowej (Agencje Marketingowe).
- ✓ Restrukturyzacja projektu.

### 1. TECH STACK (2025-12-04)
- ✓ Decyzja o porzuceniu localhosta (problemy z tunelem).
- ✓ Wdrożenie na VPS (Mikr.us) dla stabilności demo.
- ✓ Konfiguracja Google OAuth i Postgres (2025-12-08).
