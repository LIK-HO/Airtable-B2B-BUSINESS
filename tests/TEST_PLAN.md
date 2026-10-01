# Test Plan

## 1. Lead acquisition hard gates

Reject:
- missing confirmed INN;
- missing usable phone;
- unresolved/inactive organization;
- missing sphere;
- missing concrete need/strong need signal;
- missing Почему;
- missing Зачем;
- missing Основание потребности;
- missing LPR role;
- rating below 3.

## 2. Identity and deduplication

- Same normalized INN cannot create a second company.
- Multi-source discovery of one organization results in one canonical record.
- Existing INN is enriched rather than duplicated.

## 3. Phone waterfall

- Missing phone in source A triggers source B/C enrichment.
- No phone anywhere means not READY and not visible in operator pages.

## 4. Need semantics

- sector-only ≠ current need;
- weak inference ≠ confirmed need;
- strong activity signal may qualify;
- direct current need qualifies.

## 5. Projection integrity

For one canonical company:
- ОЧЕРЕДЬ => visible in КОМПАНИЯ and ОЧЕРЕДЬ;
- ПЕРЕЗВОНИТЬ => visible in КОМПАНИЯ and ОЧЕРЕДЬ;
- КЛИЕНТ => visible in КОМПАНИЯ and КЛИЕНТ;
- АРХИВ => visible in КОМПАНИЯ and АРХИВ.

No status transition creates a second company.

## 6. Contact history

- first contact and last contact are derived;
- current summary is visible on the company card;
- all historical events remain attached.

## 7. Orders

- multiple orders can point to one company;
- repeat order does not create a company duplicate;
- company card exposes linked orders.

## 8. Reference integrity

- every sphere leaf has a valid hierarchy parent where applicable;
- primary scripts link to their relevant sphere;
- source registry records remain accessible;
- no broken links after clean-up.

## 9. Mobile UX

Verify:
- opening each of the five pages;
- company drill-down;
- status edits;
- linked history/orders;
- compact first screen;
- order-to-company navigation.

## 10. Clean-state verification

After all tests:
- test company count = 0;
- test history count = 0;
- test order count = 0;
- reference counts remain intact;
- no test artifacts remain.

## 11. External acceptance benchmark

1000 Moscow search opportunities across the complete sphere hierarchy:
- unique READY LEADS >= 500;
- every ready record has phone, INN, sphere, concrete need, reason/evidence and logical operator context;
- no systematic chaotic output;
- any systematic violation fails acceptance.

## 12. Regression rule

After each schema, interface or acquisition change rerun:
identity → phone → need → dedup → quality gate → projections → history → orders → clean-state.
