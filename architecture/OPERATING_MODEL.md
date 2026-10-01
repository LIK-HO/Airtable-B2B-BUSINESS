# B2B BUSINESS — Operator Model

## 1. Product shape

The operator surface is exactly five areas:

КОМПАНИЯ · ОЧЕРЕДЬ · КЛИЕНТ · ЗАКАЗ · АРХИВ

Everything else is supporting/reference data.

## 2. Canonical company

One organization = one КОМПАНИЯ record.
Identity key = normalized INN.

## 3. What enters the operational dataset

A company must already have:
- Moscow/target geography fit;
- confirmed INN;
- active status where applicable;
- usable general business phone;
- sphere;
- concrete need or strong documented need signal;
- evidence-backed Почему;
- meaningful Зачем;
- evidence-backed Основание потребности;
- known or explicitly inferred LPR role;
- rating 3–5.

No manual verification state is shown to the operator.

## 4. Lead acquisition logic

Search is conducted by sphere × need × source × scenario.
Phone discovery uses multiple sources.
Identity is resolved before admission.
Duplicates are merged by normalized INN.
Weak signals do not become confirmed needs.

## 5. Queue

ОЧЕРЕДЬ shows:
- Status = ОЧЕРЕДЬ or ПЕРЕЗВОНИТЬ;
- sorted by priority score, rating and date for new records;
- callbacks remain in the same work surface.

## 6. Company detail

First useful chain:

Кто → Почему → Зачем → Как связаться → Потребность → Сфера → Рейтинг → Скрипт → следующий шаг.

Extended detail contains history, orders, sources and optional address/site/secondary phones.

## 7. Orders

Every order has one company link.
Repeat order = another order record for the same company.

## 8. Quality gate

Airtable operator pages expose only records for which Контроль качества = 1.
This prevents incomplete records from leaking into the work surface.

## 9. External acceptance

The operator may run a 1000-opportunity Moscow search across all sphere hierarchy.
The project acceptance threshold is >=500 unique ready records with no missing mandatory core fields or broken semantic chain.

This measures the quality of the integrated acquisition process, not merely the number of raw search hits.
