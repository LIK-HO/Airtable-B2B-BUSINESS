# Design / Integration Gate — B2B BUSINESS

## Current status

**DESIGN CORRECTED AND AIRTABLE IMPLEMENTATION BUILT; FINAL RELEASE AUDIT IN PROGRESS**

## Passed design checks

- [x] Five operator areas are defined.
- [x] КОМПАНИЯ is the canonical company dataset.
- [x] Projections never duplicate companies.
- [x] INN is the canonical duplicate key.
- [x] Operational records require usable phone and confirmed identity.
- [x] Need semantics are separated into Почему / Зачем / Потребность / Основание потребности.
- [x] Multi-source phone enrichment is mandatory before rejection.
- [x] Source precedence is explicit.
- [x] LPR role inference is explicitly separated from known person identity.
- [x] Sphere × need × source × scenario search matrix is defined.
- [x] No arbitrary lead batch cap exists.
- [x] Airtable operator pages use a hard quality gate.
- [x] Source registry contains 90 records.
- [x] Sphere hierarchy contains 39 records.
- [x] Script library contains 24 scenarios.
- [x] External 1000-opportunity / 500-ready acceptance benchmark is fixed.

## Airtable implementation status

Built target tables:
- КОМПАНИЯ;
- ИСТОРИЯ КОНТАКТОВ;
- ЗАКАЗЫ;
- ИСТОЧНИКИ;
- СФЕРЫ;
- СКРИПТЫ.

Built B2B interface:
- КОМПАНИЯ;
- ОЧЕРЕДЬ;
- КЛИЕНТ;
- ЗАКАЗ;
- АРХИВ.

## Still required before release

1. verify and complete sphere-parent links and primary-script links;
2. insert controlled test records;
3. run all integrated tests;
4. delete test data and verify clean state;
5. remove legacy interface/tables after count preflight;
6. reconcile final Airtable schema against GitHub TARGET_SCHEMA;
7. update implementation/release evidence;
8. merge design branch to main only after final checks.

## External acceptance

The user will run the 1000-opportunity Moscow test.
Release remains compatible with that test only if the ready set contains >=500 unique companies and no mandatory-field failures.
