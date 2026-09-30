# Airtable Adapter Contract

| Core concept | Airtable implementation |
|---|---|
| Entity | Table + stable semantic key |
| Relationship | multipleRecordLinks |
| Enum | singleSelect |
| Lifecycle state | singleSelect |
| Audit event | record in 90 Аудит |
| Configuration | record in 92 Конфигурация |
| Migration ledger | record in 93 Миграции |
| Security control | record in 91 Безопасность |
| Operator surface | Airtable Interface |
| Deterministic workflow | Airtable Automation |

Airtable field IDs are implementation details. Business contracts use logical field names and meanings.
