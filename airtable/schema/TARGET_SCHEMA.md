# Target Airtable Schema — B2B BUSINESS

## Tables

### КОМПАНИЯ

Required operational fields:
- Компания — primary display.
- ИНН — normalized canonical identity.
- Телефон — usable general business phone.
- Потребность — concrete service/work need.
- Почему — evidence-based target fit.
- Зачем — business situation creating the opportunity.
- ЛПР / должность — known or explicitly inferred role.
- Сфера — linked hierarchy node.
- Скрипт — linked scenario when applicable.
- Рейтинг — 1–5; operational range 3–5.
- Приоритет — Высокий / Средний / Низкий.
- Статус — ОЧЕРЕДЬ / КЛИЕНТ / ПЕРЕЗВОНИТЬ / АРХИВ.
- Дата внесения — created time.
- Контроль качества — derived 1/0; must be 1 to enter any operator projection.
- Приоритет балл — derived sort value.
- Первое обращение / Последнее обращение — derived rollups from history.
- Следующий контакт — callback date/time.
- Последний комментарий — current operator summary.
- Источники — provenance links.
- Основание потребности — evidence for the stated need.
- История контактов — linked event history.
- Заказы — linked orders.
Optional detail:
- Доп. телефоны;
- Адрес;
- Сайт.

### Контроль качества

The derived operational gate must require:
- INN;
- phone;
- need;
- Почему;
- Зачем;
- LPR / должность;
- Основание потребности;
- rating >= 3;
- status;
- sphere.

It is an Airtable display gate, not a replacement for external identity/need verification.

### ИСТОРИЯ КОНТАКТОВ

- Компания — linked to КОМПАНИЯ.
- Дата/время.
- Тип.
- Результат.
- Комментарий.
- Следующий контакт.
- Создано.

### ЗАКАЗЫ

- Заказ — primary.
- КОМПАНИЯ — linked to КОМПАНИЯ.
- Услуга.
- Дата.
- Статус.
- Повторный.
- Следующий заказ.
- Сумма — optional.
- Комментарий.
- Создано.

### ИСТОЧНИКИ

- Источник;
- Группа;
- Подгруппа;
- Приоритет;
- Назначение;
- Что подтверждает;
- Ссылка;
- Доступ;
- Примечание.

The registry is hierarchical by group → subgroup → source.

### СФЕРЫ

- Сфера;
- Родительская сфера — self-link;
- Приоритет;
- Типовые потребности;
- Типовые сигналы;
- Основной скрипт;
- Примечание.

### СКРИПТЫ

- Сценарий;
- Сфера;
- Когда применять;
- Цель;
- Открытие;
- Квалифицирующие вопросы;
- Предложение;
- Типовые возражения;
- Ответы;
- Следующий шаг;
- Повторный контакт;
- Ограничения.

## Projection rules

- КОМПАНИЯ = quality gate true;
- ОЧЕРЕДЬ = quality gate true + status ОЧЕРЕДЬ or ПЕРЕЗВОНИТЬ;
- КЛИЕНТ = quality gate true + status КЛИЕНТ;
- АРХИВ = quality gate true + status АРХИВ;
- ЗАКАЗ = all orders.

No projection creates a company copy.
