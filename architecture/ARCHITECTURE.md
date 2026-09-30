# Architecture

```
PLATFORM-NEUTRAL CORE
        |
     CONTRACTS
        |
 AIRTABLE ADAPTER
        |
 +------+--------+ 
 |      |        |
Base Interfaces Automations
 |      |        |
Tables-+---API/Scripts
```

## Layers
1. Core — invariants, state transitions and domain meaning.
2. Contracts — schema, events, permission expectations and test oracles.
3. Adapter — mapping core concepts to Airtable constructs.
4. Runtime — Base, tables, views, interfaces, automations, scripts and API.

Airtable implementation details never redefine domain meaning.
