# Roadmap

## Phase 0 — Foundation
Scope, naming, repository contract, Airtable target.

## Phase 1 — Core
Canonical company identity, work statuses, duplicate rule by INN, order relation, contact history relation.

## Phase 2 — Data Model
Compact canonical tables: КОМПАНИЯ, ИСТОРИЯ КОНТАКТОВ, ЗАКАЗЫ, ИСТОЧНИКИ, СФЕРЫ, СКРИПТЫ. Define field visibility and relationship rules.

## Phase 3 — Security & Data Safety
Permissions, technical-field isolation, duplicate-by-INN checks, orphan checks, recovery/export contract.

## Phase 4 — Operator Layer
Five mobile-first projections:
КОМПАНИЯ → ОЧЕРЕДЬ → КЛИЕНТ → ЗАКАЗ → АРХИВ.
Shared record detail for all projections, status actions, linked history and linked orders.

## Phase 5 — Source Intelligence
Populate and structure the source registry (government, maps, jobs, tenders, commercial databases, industry sources) and the sphere/script libraries.

## Phase 6 — Validation
Representative data-set test, projection integrity, status transition tests, duplicate tests, mobile UX checks, data-safety/security review.

## Phase 7 — Release
Documentation, acceptance record, versioning and release audit.

### Current design branch
The five-list operating model, source registry, sphere matrix and script library are design artifacts only on branch `design/lead-factory`.

Airtable implementation must not begin until the design is accepted and the live base has been reconciled against it.
