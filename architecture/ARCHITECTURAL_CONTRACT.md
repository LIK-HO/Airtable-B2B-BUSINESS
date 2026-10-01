# Architectural Contract

## Canonical data

`КОМПАНИЯ` is the canonical organization table.

One organization must not exist twice in the canonical table. The primary identity key is INN. Other attributes are evidence/supporting data, not alternate company identities.

## Projections

The operator lists are filtered projections over the same canonical records:

- `КОМПАНИЯ`: all accepted companies;
- `ОЧЕРЕДЬ`: status = ОЧЕРЕДЬ;
- `КЛИЕНТ`: status = КЛИЕНТ;
- `АРХИВ`: status = АРХИВ.

No projection creates or copies a company record.

## Work status

The only operator status values are:

- ОЧЕРЕДЬ;
- КЛИЕНТ;
- ПЕРЕЗВОНИТЬ;
- АРХИВ.

Color semantics:
green = ОЧЕРЕДЬ;
blue = КЛИЕНТ;
yellow = ПЕРЕЗВОНИТЬ;
red = АРХИВ.

## Queue

ОЧЕРЕДЬ is sorted by priority, then rating, then freshness.

The queue contains only companies already suitable for contact. There is no user-facing candidate, verification, quarantine or waiting-for-phone state.

## Data quality

A company may enter КОМПАНИЯ only when identity is established, INN is confirmed, a working general phone is available, the sphere is assigned, and a useful need/relevance statement exists.

A website/address may be retained as supplementary data when known but is not required in list columns.

Budget estimation is not part of the canonical model.

## Contacts

`ИСТОРИЯ КОНТАКТОВ` is a child table linked to КОМПАНИЯ. It contains the contact date, outcome and note.

The company stores the concise current/latest comment shown in OЧЕРЕДЬ and the first/last contact dates needed for operation.

## Orders

`ЗАКАЗЫ` is a canonical child table linked to КОМПАНИЯ.

Repeat orders are ordinary order records with a repeat flag/relationship, not duplicated customer records.

## Source registry

`ИСТОЧНИКИ` is reference data. It does not become a queue or raw-lead table.

## Spheres and scripts

`СФЕРЫ` is the hierarchical search taxonomy.
`СКРИПТЫ` is the reusable contact-script library.
Neither table duplicates company data.

## Operator UX

The first-level interface contains only the five lists.

Opening a company from any list opens one shared record detail view with the complete available company context, linked history and orders.

Status actions update the canonical company record. The projections then change automatically because they are filtered views of the same record.

Airtable supports record-detail actions, linked-record drill-down and mobile list/record-detail interfaces; update-record buttons can change status without an automation. citeturn108379search0turn990997search2turn108379search1

## Automation policy

Automation is not part of the required architecture. It may be introduced only after a measured operational need is demonstrated and after the design is revised.

## Change control

Any change to canonical fields, status semantics, projection filters or relationship topology requires representative-data regression before Airtable publication.
