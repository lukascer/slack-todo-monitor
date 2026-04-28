# Slack Todo Monitor

Automatický AI asistent pro sledování závazků na Slacku, postavený na [Claude Code Routines](https://code.claude.com/docs/en/routines).

## Co to dělá

- 🔍 Každé ráno prohledá Slack konverzace kde jsem zmíněn nebo kde jsem odpovídal
- 🧠 AI analyzuje, jestli jsem nezapomněl odpovědět nebo jsem něco slíbil
- 📋 Pošle strukturovaný todo report do dedikovaného Slack kanálu
- 🔔 Ve 13:00 a 16:30 pošle připomínky otevřených úkolů
- ✅ Úkoly lze označit jako hotové odpovědí v kanálu

## Jak to funguje

```
9:00  → Claude Code Routine se spustí v cloudu
      → Prohledá Slack (zmínky, odpovědi za posledních 10h)
      → Analyzuje konverzace (nezodpovězeno? slib? úkol?)
      → Pošle report do #ai-assistant-lukas-cernohous
      → Naplánuje připomínky na 13:00 a 16:30

13:00 → Scheduled message – připomínka otevřených úkolů
16:30 → Scheduled message – poslední připomínka před koncem dne
```

## Nastavení

### Požadavky

- Claude Pro/Max/Team plán
- Claude Code Desktop nebo přístup na claude.ai/code/routines
- Slack konektor připojený v Claude.ai

### Vytvoření rutiny

1. Otevři Claude Desktop → Routines → New Remote Task
2. Vyber tento repozitář
3. Nastav schedule: Daily, 9:00
4. Connectors: Slack ✅
5. Prompt: `Řiď se instrukcemi v CLAUDE.md. Proveď ranní Slack check.`

## Potvrzení úkolů

V kanálu #ai-assistant-lukas-cernohous odpověz:

```
✅ 3        → označí úkol #3 jako hotový
hotovo 1, 4 → označí úkoly #1 a #4 jako hotové
```

## Licence

MIT
