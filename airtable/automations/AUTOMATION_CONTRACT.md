# Automation Contract

## AUDIT — новый клиент
Trigger: recordCreated on 01 Клиенты.
Action: create exactly one audit record in 90 Аудит.

Properties:
- deterministic;
- no external integrations;
- no AI dependency;
- no recursive write path;
- draft/off until reviewed.

## Next automation
Duplicate detection by ИНН must be implemented and tested before production release.
