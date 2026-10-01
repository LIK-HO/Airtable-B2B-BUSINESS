# Design Gate — B2B BUSINESS

## Status

**DESIGN READY FOR USER ACCEPTANCE — Airtable implementation NOT STARTED**

## Passed design checks

- [x] Five top-level work lists are defined.
- [x] КОМПАНИЯ is the single canonical company dataset.
- [x] КЛИЕНТ, ОЧЕРЕДЬ and АРХИВ are projections, not copies.
- [x] ПЕРЕЗВОНИТЬ is explicitly retained in ОЧЕРЕДЬ until resolved.
- [x] ИНН is the primary duplicate key.
- [x] Company records require confirmed identity and a usable general phone for the operational pool.
- [x] Address and website are optional detail data.
- [x] Budget estimation is excluded.
- [x] Contact history and orders are modeled as child records.
- [x] Repeat orders do not duplicate companies.
- [x] Sources, spheres and scripts are reference tables.
- [x] No mandatory automation is in the target architecture.
- [x] No mandatory AI is in the target architecture.
- [x] Mobile-first field order is defined.
- [x] Status actions are defined.
- [x] Source registry contains 90 entries.
- [x] Sphere hierarchy is defined.
- [x] Script library is defined.
- [x] Representative-data regression requirements are defined.

## Required before Airtable publication

1. Reconcile the current empty live base against TARGET_SCHEMA.
2. Remove/rename old technical table and interface names only after schema preflight.
3. Build exactly the target tables and relationships.
4. Build the five interface pages.
5. Configure record-detail status buttons.
6. Load reference data.
7. Insert a controlled representative test dataset.
8. Run full projection, identity, status, history, orders and mobile tests.
9. Remove test data and verify clean state.
10. Record final acceptance and release evidence.

## Explicit non-goals

No automatic lead factory, no background enrichment, no AI qualification, no lead pools, no candidate quarantine visible to the operator.

## Acceptance question

The design is accepted only when the operator can open Airtable and work from:

**КОМПАНИЯ → ОЧЕРЕДЬ → КЛИЕНТ → ЗАКАЗ → АРХИВ**

without maintaining a parallel technical workflow.
