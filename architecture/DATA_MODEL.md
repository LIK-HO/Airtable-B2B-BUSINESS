# Data Model — B2B BUSINESS

## 1. Canonical Airtable tables

The production model is intentionally limited to six tables.

| Table | Role | Canonical? |
|---|---|---|
| КОМПАНИЯ | one record per organization | yes |
| ИСТОРИЯ КОНТАКТОВ | one record per contact event | yes |
| ЗАКАЗЫ | one record per order | yes |
| ИСТОЧНИКИ | source directory | reference |
| СФЕРЫ | business/search taxonomy | reference |
| СКРИПТЫ | contact script library | reference |

There are no separate tables for КЛИЕНТ, ОЧЕРЕДЬ or АРХИВ.

## 2. КОМПАНИЯ

### Identity

- **Компания** — primary display field.
- **ИНН** — canonical organization identifier; normalized digits only.
- **Дата внесения** — created time.

### Operator data

- **Телефон** — primary general business phone.
- **Потребность** — concrete service/work need supported by direct evidence or a strong documented signal.
- **Почему** — concise evidence for why the company is relevant.
- **Зачем** — the business task for which the service is needed.
- **ЛПР / должность** — known or inferred decision-maker role; inference is explicitly marked as an assumption in the detail record.
- **Сфера** — link to one primary sphere.
- **Скрипт** — link to one primary scenario.
- **Рейтинг** — 1–5 quality/relevance rating.
- **Приоритет** — Высокий / Средний / Низкий.
- **Статус** — ОЧЕРЕДЬ / КЛИЕНТ / ПЕРЕЗВОНИТЬ / АРХИВ.

### Contact state

- **Первый контакт** — derived from ИСТОРИЯ КОНТАКТОВ.
- **Последний контакт** — derived from ИСТОРИЯ КОНТАКТОВ.
- **Следующий контакт** — operational date for callbacks.
- **Последний комментарий** — concise current operator note.

### Supporting data

- **Доп. телефоны** — optional.
- **Адрес** — optional, hidden from primary lists.
- **Сайт** — optional, hidden from primary lists.
- **Источники** — links to relevant source records.
- **Заказы** — reciprocal link.
- **История контактов** — reciprocal link.

Supporting data never determines the existence of another company record.

## 3. ИНН integrity rule

The INN is the primary duplicate key.

The system must not create a second КОМПАНИЯ record with the same normalized INN.

Where a source returns conflicting company data for an existing INN, the existing company record is updated after verification instead of creating a new row.

No Airtable display name is a business key.

## 4. Status semantics

| Status | Meaning | Projection |
|---|---|---|
| ОЧЕРЕДЬ | not yet processed | ОЧЕРЕДЬ |
| КЛИЕНТ | agreement / client relationship established | КЛИЕНТ |
| ПЕРЕЗВОНИТЬ | contact made; follow-up required | ОЧЕРЕДЬ, callback group |
| АРХИВ | no contact, no agreement or closed opportunity | АРХИВ |

The status is one field in КОМПАНИЯ. Projections never duplicate the record.

## 5. ИСТОРИЯ КОНТАКТОВ

Fields:

- Компания — required link to КОМПАНИЯ.
- Дата/время — required.
- Тип — Звонок / Сообщение / Email / Другое.
- Результат — Договорились / Перезвонить / Отказ / Не дозвонился / Другое.
- Комментарий — what happened and relevant context.
- Следующий контакт — optional.
- Создано — created time.

The first and last contact dates on КОМПАНИЯ are calculated from this table.

The latest operator summary remains on КОМПАНИЯ because it is the compact current state shown in the queue; the full history remains canonical in ИСТОРИЯ КОНТАКТОВ.

## 6. ЗАКАЗЫ

Fields:

- Заказ — primary display.
- Компания — required link.
- Услуга.
- Дата.
- Статус — Новый / Подтверждён / В работе / Завершён / Отменён.
- Повторный — checkbox.
- Следующий заказ / контрольная дата.
- Сумма — optional, only when actually known.
- Комментарий.
- Создано.

A repeat order is another order record linked to the same company. There is no second company record and no repeat-customer table.

## 7. ИСТОЧНИКИ

Fields:

- Источник.
- Группа.
- Подгруппа.
- Приоритет.
- Назначение.
- Что подтверждает.
- Ссылка.
- Способ доступа.
- Примечание.

The registry is hierarchical by group → sub-group → priority → source name.

## 8. СФЕРЫ

Fields:

- Сфера.
- Родительская сфера.
- Приоритет.
- Типовые потребности.
- Типовые сигналы.
- Основной скрипт.
- Примечание.

A self-link to the parent sphere provides the hierarchy without additional hierarchy tables.

## 9. СКРИПТЫ

Fields:

- Сценарий.
- Сфера.
- Когда применять.
- Цель.
- Открытие.
- Квалифицирующие вопросы.
- Предложение.
- Типовые возражения.
- Ответы.
- Следующий шаг.
- Повторный контакт.
- Ограничения / чего не говорить.

## 10. Relationships

`КОМПАНИЯ 1 → N ИСТОРИЯ КОНТАКТОВ`

`КОМПАНИЯ 1 → N ЗАКАЗЫ`

`КОМПАНИЯ N → N ИСТОЧНИКИ`

`СФЕРА 1 → N КОМПАНИЯ`

`СФЕРА 1 → N СКРИПТЫ`

`СКРИПТ 1 → N КОМПАНИЯ`

No relationship is duplicated by a second company copy.

## 11. What is deliberately excluded

- separate КЛИЕНТ table;
- separate ОЧЕРЕДЬ table;
- separate АРХИВ table;
- candidate/quarantine tables;
- lead-pool tables;
- budget model;
- mandatory website/address fields;
- mandatory contact-person table;
- mandatory AI fields;
- mandatory automation/configuration tables.

Every excluded entity can be added only after a demonstrated operational requirement.
