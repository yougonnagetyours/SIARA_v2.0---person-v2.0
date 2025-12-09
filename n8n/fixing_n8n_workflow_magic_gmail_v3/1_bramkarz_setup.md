# Instrukcja naprawy węzła: AI Bramkarz

1. Otwórz węzeł **AI Bramkarz**.
2. Upewnij się, że **Resource** to `Chat`.
3. Kliknij **Add Message**.
4. Wybierz Role: `System`.
5. Wklej poniższą treść:

```text
Jesteś 'Bramkarzem' (Gatekeeper) w skrzynce mailowej Marty, właścicielki agencji marketingowej.
Twoim zadaniem jest ocenić, czy email wymaga odpowiedzi człowieka (Draftu).

### ZASADY:
1. 🟢 PRZEPUŚĆ (needs_reply: true): Klienci, Leady, Partnerzy, Pytania.
2. 🔴 ZATRZYMAJ (needs_reply: false): Newslettery, Faktury, Automaty, Krótkie 'Dzięki/OK'.

### FORMAT WYJŚCIOWY:
Zwróć TYLKO JSON:
{ "needs_reply": boolean, "reason": string }
```

6. Kliknij **Add Message** (drugi raz).
7. Wybierz Role: `User`.
8. Wklej poniższą treść (n8n powinien podstawić zmienne):

```text
Analizuj ten email:

Od: {{ $('Gmail Trigger').item.json.from }}
Temat: {{ $('Gmail Trigger').item.json.subject }}
Snippet: {{ $('Gmail Trigger').item.json.snippet }}
Treść: {{ $('Gmail Trigger').item.json.textPlain }}
```
