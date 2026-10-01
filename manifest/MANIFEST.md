# Manifest

## Purpose

Создать небольшой, инженерно строгий B2B runtime в Airtable, который выглядит максимально просто для оператора и хранит данные без лишних сущностей, дублей и служебного шума.

## Non-negotiable principles

1. Core first: бизнес-смысл и связи определены до Airtable.
2. Five-list operator surface: оператор работает только с КОМПАНИЯ, ОЧЕРЕДЬ, КЛИЕНТ, ЗАКАЗ, АРХИВ.
3. One company — one record: ИНН является главным идентификатором организации; рабочие списки — проекции, а не копии.
4. Only usable companies in КОМПАНИЯ: неподтверждённые компании и непригодные контакты не попадают в пользовательский контур.
5. No technical workflow for operator: никаких ручных подтверждений ИНН, очистки дублей, переводов кандидатов или обслуживания внутренних пулов.
6. Compact mobile UX: на первом экране только поля, необходимые для принятия решения и связи.
7. No unnecessary analytics: бюджет и финансовые показатели не вычисляются без прямой бизнес-необходимости.
8. Deterministic relationships: компания → контакты/история → заказы; проекции читают те же записи.
9. Lead acquisition contract: поиск выполняется по матрице сфера × потребность × источник × сценарий, затем проходит enrichment waterfall и hard READY LEAD gate.
10. No silent admission: отсутствие INN, телефона, потребности, evidence, sphere или LPR role блокирует готовую запись.
11. No AI dependency: AI не является обязательным компонентом системы.
12. No silent degradation: изменение не принимается без системного тестирования.
13. Migration-ready: техническая модель переносима без потери семантики.
14. Auditability: критические изменения и структурные миграции должны иметь проверяемое основание.
15. Resource economy: никаких механизмов, которые не дают измеримой операционной пользы.
16. No fabricated coverage: внешний benchmark 1000 → 500 является критерием приёмки качества, но не оправданием выдуманных данных.

## Acceptance benchmark

For the operator's Moscow-wide sphere request:
- input = 1000 search opportunities;
- required = at least 500 unique READY LEADS;
- every ready lead must contain the mandatory core facts and causal semantics;
- zero tolerance for presenting missing-phone / missing-need / unverified-identity records as ready.

The benchmark is an acceptance gate, not a promise that external sources can always supply that volume.
