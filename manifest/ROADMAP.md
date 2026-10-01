# Roadmap

## Phase 0 — Foundation
Scope, naming, repository contract, Airtable target.

## Phase 1 — Core
Canonical company identity, work statuses, duplicate rule by INN, order relation, contact history relation.

## Phase 2 — Data Model
Compact canonical tables: КОМПАНИЯ, ИСТОРИЯ КОНТАКТОВ, ЗАКАЗЫ, ИСТОЧНИКИ, СФЕРЫ, СКРИПТЫ. Define field visibility and relationship rules.

## Phase 3 — Security & Data Safety
Permissions, technical-field isolation, duplicate-by-INN checks, orphan checks, recovery/export contract.

## Phase 4 — Lead Acquisition
Lead Acquisition Contract, source hierarchy, need-signal search matrix, phone waterfall, identity/status verification, LPR-role rule, evidence precedence, deterministic scoring and hard READY LEAD gate.

## Phase 5 — Operator Layer
Five mobile-first projections:
КОМПАНИЯ → ОЧЕРЕДЬ → КЛИЕНТ → ЗАКАЗ → АРХИВ.
Shared record detail, status changes, linked history and linked orders.

## Phase 6 — Source & Reference Layer
Populate source registry, sphere hierarchy and script library; connect scripts to spheres where a primary scenario exists.

## Phase 7 — Integrated Validation
Representative data-set test, lead-acquisition gate tests, duplicate tests, projection integrity, status transitions, history, orders, mobile behavior and clean-state verification.

## Phase 8 — External Acceptance
Run the Moscow-wide 1000-result test across the sphere hierarchy. Pass condition: >=500 unique READY LEADS and zero mandatory-field failures in the ready set.

## Phase 9 — Release
Documentation, acceptance record, versioning and release audit.

The design branch is not considered release-complete until the integrated and external gates pass.
