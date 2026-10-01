# Roadmap

## Phase 0 — Foundation
Scope, naming, repository contract, Airtable target.

## Phase 1 — Core
Entities, invariants, lifecycle states, duplicate identity rules.

## Phase 2 — Data Model
Tables, links, controlled vocabularies, technical-field policy.

## Phase 3 — Security & Data Safety
Access model, audit ledger, duplicate/orphan checks, recovery contract.

## Phase 4 — Lead Factory & Operator Layer
Automated lead discovery, enrichment, authoritative verification, phone verification, category qualification, deduplication, quarantine, ready-stock management and minimal operator surface.

## Phase 5 — Automation
Only deterministic, idempotent and bounded automations first.

## Phase 6 — Integration Contract
API/event boundaries, idempotency, source adapters, export/import and future migration.

## Phase 7 — Full Validation
Unit -> integration -> regression -> security -> data-safety -> recovery, including end-to-end lead pipeline tests.

## Phase 8 — Release
Documentation, versioning, acceptance record and release audit.

### Current baseline
Phase 0-2: deployed.
Phase 3: baseline controls deployed; duplicate detector and recovery drill remain in progress.
Phase 4: lead-factory contract is design-only on branch design/lead-factory; Airtable implementation is not authorized by this branch.