# Lead Acquisition Tests — B2B BUSINESS

## A. Hard rejection tests

Each test must be rejected from the operational dataset:

1. no confirmed INN;
2. no usable general phone;
3. inactive / unresolved organization status;
4. no target sphere;
5. no concrete need or strong documented need signal;
6. missing Почему;
7. missing Зачем;
8. missing Основание потребности;
9. missing LPR role;
10. rating below 3.

## B. Positive ready-lead tests

A synthetic company passes only when all mandatory fields are present and logically consistent.

Expected sequence:

identity → phone → sphere → need evidence → role → rating → status

## C. Deduplication

Create the same company from three source scenarios.

Expected:

- one canonical company;
- one normalized INN;
- evidence merged;
- no duplicate operational record.

## D. Phone waterfall

Run a company with no phone in source A but a usable phone in source B.

Expected:

- enrichment continues;
- final record contains the usable phone;
- company becomes eligible if all other gates pass.

Run a company with no usable phone anywhere.

Expected:

- not READY;
- not visible in the operator work pages.

## E. Need semantics

Test:

- sector only;
- weak inference;
- strong activity signal;
- direct need statement.

Expected:

- sector-only and weak inference do not pass as a ready need;
- strong signal may pass;
- direct current need passes.

## F. Projection integrity

For one canonical company:

- status ОЧЕРЕДЬ → КОМПАНИЯ + ОЧЕРЕДЬ;
- status ПЕРЕЗВОНИТЬ → КОМПАНИЯ + ОЧЕРЕДЬ;
- status КЛИЕНТ → КОМПАНИЯ + КЛИЕНТ;
- status АРХИВ → КОМПАНИЯ + АРХИВ.

No projection creates another company record.

## G. History / orders

- contact history remains attached to the canonical company;
- first/last contact are derived;
- two orders can point to one company;
- repeat order never duplicates the company.

## H. Coverage benchmark

For the operator's 1000-result Moscow search:

- measure total unique READY LEADS;
- pass threshold: >= 500;
- inspect every ready record for phone, need, INN, sphere, reason and evidence;
- fail on any systematic unordered or semantically disconnected output.

## I. Regression rule

After every acquisition, schema or interface change, rerun:

identity → phone → need → dedup → quality gate → projections → history → orders → clean-state verification.
