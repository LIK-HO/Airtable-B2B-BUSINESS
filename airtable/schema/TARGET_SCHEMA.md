# Target Airtable Schema — B2B BUSINESS

## Tables

### КОМПАНИЯ

| Field | Type | Visible in main list | Purpose |
|---|---|---:|---|
| Компания | Single line text | yes | primary display |
| ИНН | Single line text | yes | canonical identity |
| Телефон | Phone | yes | main contact |
| Потребность | Single line text | yes | concrete service need |
| Почему | Long text | detail | reason for relevance |
| Зачем | Long text | detail | business task |
| ЛПР / должность | Single line text | yes | decision-maker role; can be marked as inferred |
| Сфера | Link → СФЕРЫ | yes | primary category |
| Скрипт | Link → СКРИПТЫ | detail | primary scenario |
| Рейтинг | Rating 1–5 | yes | lead quality |
| Приоритет | Single select | yes | action order |
| Статус | Single select | detail | four work states |
| Дата внесения | Created time | yes | added date |
| Первое обращение | Rollup | detail | derived from history |
| Последнее обращение | Rollup | detail | derived from history |
| Следующий контакт | Date/time | detail | callback date |
| Последний комментарий | Long text | detail/queue | current operator summary |
| Доп. телефоны | Long text | detail | secondary numbers |
| Адрес | Single line text | detail only | optional supporting data |
| Сайт | URL | detail only | optional supporting data |
| Источники | Link → ИСТОЧНИКИ | detail | provenance |
| Основание потребности | Long text | detail | evidence for the stated need |
| История контактов | Link → ИСТОРИЯ КОНТАКТОВ | detail | contact history |
| Заказы | Link → ЗАКАЗЫ | detail | orders |

**Internal derived fields:**
- Первое обращение — rollup/min date from history;
- Последнее обращение — rollup/max date from history.

These are not manual source fields.

### ИСТОРИЯ КОНТАКТОВ

| Field | Type | Required |
|---|---|---:|
| Компания | Link → КОМПАНИЯ | yes |
| Дата/время | Date/time | yes |
| Тип | Single select | yes |
| Результат | Single select | yes |
| Комментарий | Long text | yes |
| Следующий контакт | Date/time | no |
| Создано | Created time | yes |

### ЗАКАЗЫ

| Field | Type | Required |
|---|---|---:|
| Заказ | Single line text | yes |
| Компания | Link → КОМПАНИЯ | yes |
| Услуга | Single line text | yes |
| Дата | Date | yes |
| Статус | Single select | yes |
| Повторный | Checkbox | yes |
| Следующий заказ | Date | no |
| Сумма | Currency | no |
| Комментарий | Long text | no |
| Создано | Created time | yes |

### ИСТОЧНИКИ

| Field | Type |
|---|---|
| Источник | Single line text |
| Группа | Single select |
| Подгруппа | Single line text |
| Приоритет | Single select |
| Назначение | Long text |
| Что подтверждает | Long text |
| Ссылка | URL |
| Доступ | Single select |
| Примечание | Long text |

### СФЕРЫ

| Field | Type |
|---|---|
| Сфера | Single line text |
| Родительская сфера | Link → СФЕРЫ |
| Приоритет | Single select |
| Типовые потребности | Long text |
| Типовые сигналы | Long text |
| Основной скрипт | Link → СКРИПТЫ |
| Примечание | Long text |

### СКРИПТЫ

| Field | Type |
|---|---|
| Сценарий | Single line text |
| Сфера | Link → СФЕРЫ |
| Когда применять | Long text |
| Цель | Long text |
| Открытие | Long text |
| Квалифицирующие вопросы | Long text |
| Предложение | Long text |
| Типовые возражения | Long text |
| Ответы | Long text |
| Следующий шаг | Long text |
| Повторный контакт | Long text |
| Ограничения | Long text |

## Status vocabulary

Exactly four operator statuses:

- ОЧЕРЕДЬ — green;
- КЛИЕНТ — blue;
- ПЕРЕЗВОНИТЬ — yellow;
- АРХИВ — red.

## Top-level interface

Interface name: **B2B**

Pages:

1. КОМПАНИЯ
2. ОЧЕРЕДЬ
3. КЛИЕНТ
4. ЗАКАЗ
5. АРХИВ

No numbered prefixes in table or page names.

No user-facing technical tables.

## Projection rules

### КОМПАНИЯ
No status filter.

### ОЧЕРЕДЬ
Status is ОЧЕРЕДЬ or ПЕРЕЗВОНИТЬ.

### КЛИЕНТ
Status is КЛИЕНТ.

### АРХИВ
Status is АРХИВ.

### ЗАКАЗ
All orders.

## Projection identity

All four company-oriented pages reference the same КОМПАНИЯ records.

No table-level duplication is permitted.

## Mobile field order

The first row context is:

**Компания → Потребность → Телефон → Приоритет/Рейтинг**

Record detail begins:

**Компания/ИНН/Телефон → Почему/Зачем → ЛПР/Сфера/Потребность → Status → Contact state → History → Orders → Sources → optional details.**
