# Architectural Contract — B2B BUSINESS

## 1. Canonical entities

КОМПАНИЯ is the single canonical organization table.
ИСТОРИЯ КОНТАКТОВ stores contact events.
ЗАКАЗЫ stores orders.
ИСТОЧНИКИ, СФЕРЫ and СКРИПТЫ are reference libraries.

## 2. Identity

One normalized INN identifies one organization in КОМПАНИЯ.
No interface projection may create a second company record.

## 3. Lead acquisition boundary

External research is governed by LEAD_ACQUISITION_CONTRACT.md.

The pipeline is deterministic:

need signal → exact organization → INN/status → phone → sphere → need evidence → LPR role → dedup → rating → READY LEAD → Airtable.

Airtable does not decide that a weak raw hit is ready.

## 4. Projections

КОМПАНИЯ = quality gate true.
ОЧЕРЕДЬ = quality gate true + Status IN {ОЧЕРЕДЬ, ПЕРЕЗВОНИТЬ}.
КЛИЕНТ = quality gate true + Status = КЛИЕНТ.
АРХИВ = quality gate true + Status = АРХИВ.

## 5. Status contract

Only four operator statuses exist:
- ОЧЕРЕДЬ;
- КЛИЕНТ;
- ПЕРЕЗВОНИТЬ;
- АРХИВ.

ПЕРЕЗВОНИТЬ remains in the ОЧЕРЕДЬ projection until resolved.

## 6. Evidence semantics

Почему, Зачем, Потребность and Основание потребности are separate fields.
A generic company profile cannot be transformed into a claimed current need without evidence.

## 7. Data relationships

КОМПАНИЯ 1:N ИСТОРИЯ КОНТАКТОВ.
КОМПАНИЯ 1:N ЗАКАЗЫ.
КОМПАНИЯ N:N ИСТОЧНИКИ.
СФЕРЫ 1:N КОМПАНИЯ.
СФЕРЫ 1:N СКРИПТЫ.

## 8. Operator boundary

Operator sees only five work areas.
Technical/reference data remains outside first-level navigation.

## 9. Automation / AI policy

No mandatory background lead factory and no mandatory AI runtime.
External AI/web research may produce proposed data, but only data passing the acquisition contract becomes authoritative operational state.

## 10. Change control

Any change to identity, quality gate, status, projections or relationship semantics requires representative-data regression and clean-state verification.

## 11. Acceptance

A project release must support the external benchmark of 1000 search opportunities with >=500 unique READY LEADS and zero mandatory-field failures in the ready set.
