# Architectural Contract

## Entity
Every business record has a stable semantic identity, lifecycle state where applicable, validation policy and traceable origin.

## Relationship
Links are explicit. Orphan links are integrity failures. Duplicate relations are not silently tolerated.

## State
Authoritative states are enumerated. Invalid transitions must be rejected or surfaced as validation failures.

## Automation
Automations must be deterministic, bounded and idempotent where re-execution is possible. Cross-table writes require failure/recovery and audit evidence.

## AI
AI output is advisory unless an explicit contract makes it authoritative. No security, legal, financial or destructive action may rely solely on unverified AI output.

## Migration
Each schema/data migration records preflight, transformation, postflight reconciliation, recovery path and test evidence.
