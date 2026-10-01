# Legacy Technical Archive — B2B BUSINESS

## Purpose

The legacy Airtable technical contour was inspected before cleanup.
No business rows were present in the old company/intake/order/task surfaces.
Technical records were archived by meaning before the legacy tables were removed.

## Archived counts

| Legacy table | Records | Disposition |
|---|---:|---|
| 90 Аудит | 6 | Evidence retained in repository |
| 91 Безопасность | 8 | Security findings retained in repository |
| 92 Конфигурация | 4 | Configuration semantics retained in repository |
| 93 Миграции | 4 | Migration evidence retained in repository |
| 09 Источники разведки | 6 | Superseded by 90-record ИСТОЧНИКИ registry |

## Important archived findings

- Historical relationship-smoke and migration checks reported PASS.
- A historical duplicate-identity automation test found that Airtable could physically contain duplicate INNs; therefore canonical deduplication remains an acquisition-contract responsibility rather than an Airtable uniqueness constraint.
- Historical automation activation was not relied upon for the new design.
- No credentials or API keys are archived here.
- Source rows are superseded by the current normalized source registry.

## Current authority

The repository architecture, Lead Acquisition Contract, target schema and current six-table Airtable contour are authoritative.
Legacy records are historical evidence only and must not drive operator behavior.
