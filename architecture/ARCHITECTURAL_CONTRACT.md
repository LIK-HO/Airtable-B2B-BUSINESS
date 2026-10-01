# Architectural Contract — B2B BUSINESS

## 1. Canonical entities

КОМПАНИЯ is the single canonical organization table.
ИСТОРИЯ КОНТАКТОВ stores contact events.
ЗАКАЗЫ stores orders.
ИСТОЧНИКИ, СФЕРЫ and СКРИПТЫ are reference libraries.

## 2. Identity

One normalized INN identifies one organization in КОМПАНИЯ.
No interface projection may create a second company record.

## 3. Projections

КОМПАНИЯ = all operational company records.
ОЧЕРЕДЬ = Status IN {ОЧЕРЕДЬ, ПЕРЕЗВОНИТЬ}.
КЛИЕНТ = Status = КЛИЕНТ.
АРХИВ = Status = АРХИВ.

These are views/interface projections, not data tables.

## 4. Status contract

Only four operator statuses exist:

- ОЧЕРЕДЬ — green;
- КЛИЕНТ — blue;
- ПЕРЕЗВОНИТЬ — yellow;
- АРХИВ — red.

ПЕРЕЗВОНИТЬ remains in the ОЧЕРЕДЬ page until a final outcome.

## 5. Operational entry criteria

Only an operationally usable company enters КОМПАНИЯ:

- confirmed INN;
- usable general phone;
- relevant sphere;
- useful need or strong documented need signal;
- reason for relevance;
- expected decision-maker role;
- source evidence;
- rating 3–5.

Unusable and unverified records are not stored as user-facing lead states.

## 6. Data relationships

КОМПАНИЯ 1:N ИСТОРИЯ КОНТАКТОВ.
КОМПАНИЯ 1:N ЗАКАЗЫ.
КОМПАНИЯ N:N ИСТОЧНИКИ.
СФЕРЫ 1:N КОМПАНИЯ.
СФЕРЫ 1:N СКРИПТЫ.

Order history and contact history never duplicate company identity.

## 7. Operator boundary

Operator sees only the five work areas.
Technical/reference tables stay outside first-level navigation.
Address, website, source metadata and technical identifiers remain inside record detail unless directly useful.

## 8. Automation policy

No mandatory automation is part of the target architecture.
Status changes are implemented through direct record-update actions in the interface.
Any future automation requires a new design decision, measurable justification, and full regression.

## 9. AI policy

AI is not a required runtime component.
It may assist the external research workflow, but it does not create authoritative business state by itself.

## 10. Mobile design

Primary navigation and company work must be usable on the official Airtable mobile client.
List rows stay compact; record detail carries extended context.
Current Airtable mobile interfaces support list/record-detail workflows, linked records and update-field buttons. citeturn251792search0turn251792search1turn251792search5

## 11. Change control

Any change to identity, status, projection filters, relationships or required operator fields requires representative-data regression before Airtable publication.