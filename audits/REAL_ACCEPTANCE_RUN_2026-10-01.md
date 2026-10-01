# Real Acceptance Run — 2026-10-01

## Objective

Run the B2B BUSINESS lead-acquisition system as a real operator would use it:
- Moscow;
- across the configured sphere hierarchy;
- only verifiable companies;
- only records that explain why to call, what to ask/offering, and what evidence supports the contact;
- no fabricated fields.

## Result

**CURRENT ACCEPTANCE: FAIL**

Control target: 1000 potential Moscow results.
READY LEADS admitted to Airtable in this run: **9**.
Acceptance threshold: **>=500 unique READY LEADS**.
Shortfall: **491**.
Effective ready ratio for this run: **0.9% of the requested 1000-result target**.

## Airtable state after run

All 9 accepted records are in КОМПАНИЯ with status ОЧЕРЕДЬ.

For all 9:
- quality gate = 1;
- INN present;
- phone present;
- need present;
- Почему present;
- Зачем present;
- ЛПР/должность present;
- need evidence present;
- sphere linked;
- script linked;
- at least 3 source links;
- no duplicate INN inside the current dataset.

The operator interface was republished after the real dataset was inserted.

## Records admitted

1. ООО СОЛЮС — direct current signal involving loaders/takelazhniks.
2. ООО БЕЛЫЙ СВЕТ 2000 — current loader/warehouse staffing signal.
3. ООО ФРАМБИНИ — current loader staffing signal.
4. ООО ПО РОСТТЕКСТИЛЬ — current production/loader signal.
5. ООО ДОСТУПНЫЕ ТЕХНОЛОГИИ — current production/warehouse staffing signal.
6. ООО ГАРДА — current production loader vacancy signal in Moscow.
7. ООО ТД АГАТМЕД — current loader-picker vacancy signal.
8. УНИКОМ — current exhibition stand construction/installation signal.
9. ООО ИНСАЙТ ЭКСПО — current exhibition / temporary-construction / installation signal.

## Rejected during this run

Companies were deliberately rejected when at least one hard requirement was not established from available evidence, including:
- no usable phone;
- no confirmed INN;
- unresolved legal identity;
- liquidation/closed status;
- ambiguous company identity;
- only generic sector fit without a strong current need signal.

## Critical interpretation

This FAIL is a data-acquisition result, not an Airtable schema result.

The Airtable quality gate is doing the intended thing: it prevents incomplete records from appearing in the operator queue.

The current run therefore demonstrates that the system refuses to turn weak or incomplete discoveries into READY LEADS.

## Release decision

The Airtable operator surface is published.

The project release gate remains **ACCEPTANCE_FAILED_CURRENT_RUN** until a real Moscow control request can produce >=500 unique READY LEADS satisfying the same hard contract.

No missing record should be manufactured merely to reach the threshold.