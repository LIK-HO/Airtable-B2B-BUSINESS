# B2B BUSINESS — Operator Model

## 1. Product shape

The operator surface is exactly five areas:

**КОМПАНИЯ · ОЧЕРЕДЬ · КЛИЕНТ · ЗАКАЗ · АРХИВ**

Everything else is supporting/reference data.

The operator is not expected to maintain a lead-processing machine. Airtable is the clean operational workspace around already prepared company data and its business history.

## 2. Canonical company record

КОМПАНИЯ contains exactly one record per organization.

The identity key is the normalized ИНН.

The company record contains the compact facts required to decide whether to contact and how to contact:

**Компания · ИНН · Телефон · Потребность · ЛПР/должность · Сфера · Рейтинг · Дата внесения**

The record detail contains the extended context:

**Почему · Зачем · Скрипт · Приоритет · Статус · Первый/последний контакт · Следующий контакт · Последний комментарий · История · Источники · Заказы · адрес/сайт/доп. телефоны, если известны.**

## 3. What enters КОМПАНИЯ

Only companies that are already operationally usable:
- identity confirmed;
- INN confirmed;
- active organization status confirmed where relevant;
- at least one usable general phone;
- relevant sphere identified;
- concrete need or strong documented need signal;
- clear reason for relevance;
- expected decision-maker role;
- source evidence retained;
- rating 3–5.

There is no visible pool of unverified companies.

## 4. Почему / Зачем / Потребность

These fields have distinct meanings.

**Почему** — why this company belongs in the target segment.

**Зачем** — the business task that creates the opportunity.

**Потребность** — the concrete service/work need that can be discussed.

Example:

- Почему: регулярно работает на строительных объектах.
- Зачем: усилить объектную бригаду на пиковых работах.
- Потребность: разгрузка и подъём строительных материалов.

The wording must distinguish verified facts from reasonable inference.

## 5. Status model

Exactly four operator statuses:

**ОЧЕРЕДЬ** — not yet processed.

**КЛИЕНТ** — agreement reached / client relationship established.

**ПЕРЕЗВОНИТЬ** — conversation occurred or callback agreed; next action remains.

**АРХИВ** — not reached, declined, or otherwise closed for current work.

Color semantics:

green / blue / yellow / red respectively.

## 6. Projection logic

КОМПАНИЯ shows all company records.

ОЧЕРЕДЬ shows records with status ОЧЕРЕДЬ or ПЕРЕЗВОНИТЬ.

КЛИЕНТ shows status КЛИЕНТ.

АРХИВ shows status АРХИВ.

ЗАКАЗ is its own order table.

No projection creates a second company record.

## 7. Queue behavior

ОЧЕРЕДЬ is the main work surface.

Priority hierarchy:
1. High priority;
2. Medium priority;
3. Low priority.

Within priority:
- rating descending;
- newest records first for new leads;
- next-contact date ascending for callbacks.

The queue can be visually grouped into:

**НОВЫЕ** — ОЧЕРЕДЬ

**ПЕРЕЗВОНИТЬ** — ПЕРЕЗВОНИТЬ

This remains one page, not two tables.

## 8. Queue row

The compact row should surface:

**Компания · Потребность · Телефон · Приоритет · Рейтинг**

The opened record detail immediately exposes:

**Кто → Почему → Зачем → Как связаться → Потребность → Сфера → Рейтинг → Скрипт → следующий шаг.**

## 9. Status actions

Four buttons in company record detail:

- ОЧЕРЕДЬ;
- КЛИЕНТ;
- ПЕРЕЗВОНИТЬ;
- АРХИВ.

Each button updates the single canonical status field.

No duplicate record is created.

The projection changes because the filter changes.

## 10. Contacts

ИСТОРИЯ КОНТАКТОВ contains one event per real contact attempt or conversation.

The company card exposes:
- first contact;
- last contact;
- next contact;
- current/latest comment;
- full history.

The latest comment is a compact operational summary; the historical event records remain the detailed history.

## 11. Orders

ЗАКАЗЫ contains one record per order.

Repeat business is represented by multiple order records attached to the same company.

There is no separate repeat-client object.

## 12. Technical/reference contour

Only three reference libraries are required:

- ИСТОЧНИКИ;
- СФЕРЫ;
- СКРИПТЫ.

They support the operator but do not enter the five-list navigation.

## 13. Deliberately absent

No:
- separate КЛИЕНТ table;
- separate ОЧЕРЕДЬ table;
- separate АРХИВ table;
- lead pools;
- candidate/quarantine tables;
- mandatory automation;
- mandatory AI;
- mandatory website/address columns;
- mandatory budget estimate;
- unnecessary analytics.

## 14. Mobile rule

The first view is short and actionable.

Detailed context belongs behind the company click.

Airtable's current Interface model supports List/Record Detail, linked-record drill-down and record-detail update buttons on iOS and Android. citeturn251792search0turn251792search1turn251792search5