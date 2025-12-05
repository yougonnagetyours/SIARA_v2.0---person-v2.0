## 🎯 AKTUALNY ETAP

**1. Tydzień 1: Budowa Demo (VPS + n8n + Slack)**

Cel: Uruchomienie Agenta w środowisku n8n na VPS (stabilność) ze sterowaniem przez Slacka.

Status:
- ✓ **INFRASTRUKTURA:** VPS (Mikr.us) postawiony + Docker + n8n (`https://kacper140-20140.wykr.es`).
- ✓ **MIGRACJA:** Logika przeniesiona na VPS.
- ✓ **INTEGRACJA:** Slack Bot działa i odpowiada ("Rura drożna").
- ✓ **MVP:** Scenariusz "Scope Creep" działa na prostym modelu LLM.
- 🔄 **AGENT PRO:** Trwa budowa zaawansowanego agenta z dostępem do Gmaila (wymaga OAuth i Postgres).

## 🚧 BLOKERY

- **Google OAuth:** Brak Client ID / Client Secret do obsługi Gmail Tools.
- **Postgres:** Brak skonfigurowanej bazy danych dla pamięci Agenta.

## 🕒 HISTORIA

### 0. PRZYGOTOWANIE (2025-11-26)
- ✓ Zdefiniowanie Persony (Michał - Inżynier Procesów).
- ✓ Określenie grupy docelowej (Agencje Marketingowe).
- ✓ Restrukturyzacja projektu.

### 1. TECH STACK (2025-12-04)
- ✓ Decyzja o porzuceniu localhosta (problemy z tunelem).
- ✓ Wdrożenie na VPS (Mikr.us) dla stabilności demo.