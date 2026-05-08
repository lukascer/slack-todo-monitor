# Slack Todo Monitor

Automatický AI asistent pro sledování závazků na Slacku, postavený na [Claude Code Routines](https://code.claude.com/docs/en/routines).

## Co to dělá

- 🔍 Každé ráno prohledá Slack konverzace kde jsem zmíněn nebo kde jsem odpovídal a take dm - direct messages
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

V kanálu #ai-assistant-lukas-cernohous sleduj vlákno, ve kterém posíláš připomínky. Pokud uživatel odpoví zprávou obsahující „✅ číslo“ nebo slovo „hotovo“ následované čísly úkolů (oddělenými čárkami nebo mezerami), tyto úkoly označ jako dokončené a odeber je z příštích připomínek.

- Příklad: „✅ 3“ znamená, že úkol #3 je hotový.  
- „hotovo 1, 4“ znamená, že jsou hotové úkoly #1 a #4.

**Udržování seznamu úkolů**  
Pokud jsi v předchozích bězích vytvořil seznam otevřených úkolů, ujisti se, že při dalším běhu tento seznam znovu načteš, aby úkoly zůstaly v přehledu, dokud nejsou označené jako hotové. Po každém běhu seznam aktualizuj tak, aby v něm zůstaly jen nevyřešené úkoly.

**Formát Slack zpráv**  
Posílej do Slacku pouze čistý text a seznam úkolů. Není třeba přidávat odkazy typu „Open in Claude“ – pokud je Claude přidává automaticky, ignoruj je a do těla zprávy je nevkládej.

## Licence

MIT
