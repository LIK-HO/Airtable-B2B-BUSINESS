# Interface Specification — B2B BUSINESS

## 1. Top-level navigation

Exactly five work areas:

**КОМПАНИЯ · ОЧЕРЕДЬ · КЛИЕНТ · ЗАКАЗ · АРХИВ**

Technical/reference tables are not part of first-level navigation.

## 2. КОМПАНИЯ

### Filter
All canonical company records.

### Mobile row
**Компания · Потребность · Телефон · Рейтинг**

### Secondary context
**ЛПР · Сфера · Дата**

### Record detail
Sections in this order:

1. Компания / ИНН / Телефон
2. Потребность / Почему / Зачем
3. ЛПР / Сфера / Рейтинг / Приоритет
4. Status buttons
5. First / Last / Next contact
6. Last comment
7. Contact history
8. Orders
9. Sources
10. Optional address / website / additional phones

## 3. ОЧЕРЕДЬ

### Filter
Status = ОЧЕРЕДЬ OR ПЕРЕЗВОНИТЬ.

### Ordering

For new leads:
1. Priority descending;
2. Rating descending;
3. Date added descending.

For callbacks:
1. Next contact date ascending;
2. Priority descending;
3. Rating descending.

The interface may group the same page into two sections:

**НОВЫЕ** → ОЧЕРЕДЬ

**ПЕРЕЗВОНИТЬ** → ПЕРЕЗВОНИТЬ

No third queue is created.

### Mobile row
**Компания · Потребность · Телефон · Приоритет · Рейтинг · Status**

### Record detail
The first screen must expose:

**Кто → Почему → Зачем → Как связаться → Потребность → Сфера → Рейтинг → Скрипт → что делать дальше.**

The full detail then exposes contacts, dates, comment history and orders.

### Status actions

- ОЧЕРЕДЬ — sets Status = ОЧЕРЕДЬ.
- КЛИЕНТ — sets Status = КЛИЕНТ.
- ПЕРЕЗВОНИТЬ — sets Status = ПЕРЕЗВОНИТЬ.
- АРХИВ — sets Status = АРХИВ.

No second company record is created.

## 4. КЛИЕНТ

### Filter
Status = КЛИЕНТ.

### Mobile row
Same as КОМПАНИЯ.

### Record detail
Same canonical company detail layout.

The interface is a projection only. It does not contain a client copy.

## 5. ЗАКАЗ

### Mobile row
**Заказ · Компания · Услуга · Дата · Статус**

### Record detail
**Компания → услуга → дата → status → repeat → next order → amount when known → comment.**

The company link must open the same canonical company record.

## 6. АРХИВ

### Filter
Status = АРХИВ.

### Mobile row
Same as КОМПАНИЯ.

### Record detail
Same canonical company detail plus archived contact history and reason/current comment.

## 7. No technical clutter

The following never appear in top-level work lists:

- record IDs;
- source registry metadata;
- raw search queries;
- verification state;
- import state;
- API state;
- internal errors;
- audit metadata;
- technical timestamps not useful to the operator;
- address or website unless explicitly opened in detail.

## 8. Mobile design rule

The first screen of a list shows no more than four high-value pieces of context where Airtable's mobile layout requires compact rows. Additional fields belong in record detail.

Status buttons belong in record detail rather than creating four separate technical lists.

Airtable mobile Interfaces support list/record-detail workflows, linked records and record-detail update buttons on both iOS and Android. citeturn251792search0turn251792search1turn251792search5

## 9. Navigation rule

Every company link in КОМПАНИЯ, ОЧЕРЕДЬ, КЛИЕНТ and АРХИВ opens the same canonical company record.

Every order's company link opens that same company record.

History records are children of the company and are accessible from the company record.

This is the primary anti-duplication UX rule.
