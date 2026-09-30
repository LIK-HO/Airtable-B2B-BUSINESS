# Airtable-B2B-BUSINESS

Компактный инженерный эталон B2B-системы в среде Airtable.

## Архитектурная идея

`Core -> Contracts -> Airtable Adapter -> Airtable Runtime`

Airtable — runtime/data layer. Бизнес-смысл, инварианты, состояния, безопасность и тестовые оракулы не зависят от UI Airtable.

## Scope

Включено:
- platform-neutral core и контракты;
- B2B-сущности: клиенты, контакты, потребности, заказы, задачи;
- security, data-safety, audit, migration/recovery;
- Airtable schema, operator interface и deterministic automations;
- интеграционный/API boundary;
- unit, integration, regression, security и data-safety проверки.

Исключено:
- WEB/PWA;
- Yandex Cloud;
- Bitrix24;
- MAX;
- AL;
- инфраструктура, не обязательная для Airtable runtime.

## Deployed target

- Workspace: `B2B - BUSINESS`
- Base: `B2B - BUSINESS`
- GitHub: `LIK-HO/Airtable-B2B-BUSINESS`
- Baseline: `0.1.0`

## Definition of Done

Манифест -> дорожная карта -> архитектурный контракт -> модель данных -> реализация -> тесты этапа -> интеграционные/регрессионные проверки -> security/data-safety audit -> migration/recovery check -> финальная приёмка -> документация -> release audit.
