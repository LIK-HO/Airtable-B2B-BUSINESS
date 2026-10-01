# Migration Map — live Airtable → B2B BUSINESS target

## Current live state

The live base `B2B - BUSINESS` was inspected directly. The current company and incoming tables contain 0 records, so structural reconciliation can be performed without a business-data migration.

## Target

Exactly six canonical/reference tables:

1. КОМПАНИЯ
2. ИСТОРИЯ КОНТАКТОВ
3. ЗАКАЗЫ
4. ИСТОЧНИКИ
5. СФЕРЫ
6. СКРИПТЫ

## Current → target mapping

| Current live table | Target action | Reason |
|---|---|---|
| 01 Клиенты | replace with КОМПАНИЯ | current schema mixes company, identity checks, intake and old links |
| 02 Контакты | replace with ИСТОРИЯ КОНТАКТОВ | current table stores persons, while target requires contact events |
| 03 Потребности | remove as standalone table | need becomes a canonical company field in compact model |
| 04 Заказы | reshape and rename to ЗАКАЗЫ | keep order history, remove unnecessary duplicate links |
| 05 Задачи | remove | not required by current business model |
| 06 Повторные заказы | remove | repeat orders are ordinary orders with Repeat flag |
| 00 Входящие | remove from runtime | raw intake is not an operator object and there are no current records |
| 09 Источники разведки | reshape and rename to ИСТОЧНИКИ | compact source directory |
| 90 Аудит | not part of target operator database | structural/release evidence stays in repository unless later need is demonstrated |
| 91 Безопасность | not part of target operator database | security is implemented through Airtable permissions + repository controls |
| 92 Конфигурация | remove | no mandatory runtime automation/configuration |
| 93 Миграции | remove | migration evidence belongs in repository |

## Interface reconciliation

Current interface pages that must not survive in the final operator surface:

- Входящие;
- Потребности;
- Контакты;
- Повторные заказы;
- Источники.

Final interface pages:

- КОМПАНИЯ;
- ОЧЕРЕДЬ;
- КЛИЕНТ;
- ЗАКАЗ;
- АРХИВ.

Interface name: **B2B**.

## Preflight

Before any destructive structural change:

1. confirm the live table counts are still zero;
2. export/save the current schema snapshot;
3. record current interface/page IDs;
4. record the target schema version in GitHub;
5. verify no business data has appeared since the previous inspection.

## Postflight

After implementation:

1. verify exactly six target tables;
2. verify field names/types and links against TARGET_SCHEMA;
3. verify exactly five operator pages;
4. verify no old numeric prefixes remain in user-facing names;
5. insert representative test data;
6. test every status projection and relationship;
7. remove test data;
8. verify clean final state.

## Recovery

If any structural write produces an unexpected result, stop further changes and restore from the captured schema/data snapshot before continuing.

Schema acceptance is not equivalent to migration success; postflight reconciliation is mandatory.