# Architectural Contract

## Entity
Every business record has a stable semantic identity, lifecycle state where applicable, validation policy and traceable origin.

## Relationship
Links are explicit. Orphan links are integrity failures. Duplicate relations are not silently tolerated.

## State
Authoritative states are enumerated. Invalid transitions must be rejected or surfaced as validation failures.

## Lead readiness
A lead is operator-ready only after all mandatory identity, geography, category, phone, source and freshness gates pass. READY is a derived operational state, not a manual approval flag.

## Lead identity
ИНН is the primary organization identity. Normalized phone, domain and normalized name + geography are secondary duplicate controls.

## Automation
Automations must be deterministic, bounded and idempotent where re-execution is possible. Cross-table writes require failure/recovery and audit evidence.

## Source adapters
External discovery and enrichment sources enter through a normalized source contract. Source-specific formats or failures must not redefine the canonical lead model.

## Operator boundary
Technical queues, verification states, source diagnostics and quarantine records are outside the primary operator surface. Operator actions are limited to business processing of READY leads.

## AI
AI output is advisory unless an explicit contract makes it authoritative. No security, legal, financial or destructive action may rely solely on unverified AI output.

## Migration
Each schema/data migration records preflight, transformation, postflight reconciliation, recovery path and test evidence.

## Change control
Any change to lead discovery, validation, deduplication or ready-state logic requires end-to-end regression against representative lead data before Airtable publication.