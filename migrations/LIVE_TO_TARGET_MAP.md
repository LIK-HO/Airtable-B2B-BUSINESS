# Migration Map — B2B BUSINESS

## Preflight finding

The live base was inspected before the target build. The key legacy company/intake tables were empty, and the target model was built as a new canonical contour.

## Final target tables

1. КОМПАНИЯ
2. ИСТОРИЯ КОНТАКТОВ
3. ЗАКАЗЫ
4. ИСТОЧНИКИ
5. СФЕРЫ
6. СКРИПТЫ

## Target IDs currently present

- КОМПАНИЯ — tblDWeqZhSNEXkUHP
- ИСТОРИЯ КОНТАКТОВ — tbl9q1CZEGFPs2rvE
- ЗАКАЗЫ — tblMCXiyxKlZ9A0FA
- ИСТОЧНИКИ — tblZU4qLjBM87HGUD
- СФЕРЫ — tbltCoRgqz9LpdfK2
- СКРИПТЫ — tblbfXZoedAe0aLxi

## Legacy contour

The legacy tables and old operator interface remain temporarily for controlled cleanup only.

Before deletion:
1. count every legacy table;
2. confirm zero business records;
3. retain schema evidence;
4. delete only after preflight passes;
5. verify exactly six target tables afterwards.

## Recovery rule

If any legacy table has non-zero business data at deletion preflight, stop and reconcile instead of deleting.
