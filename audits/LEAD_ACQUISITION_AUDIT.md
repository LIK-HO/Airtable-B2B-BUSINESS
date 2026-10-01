# Lead Acquisition Audit — B2B BUSINESS

## Scope

Audit of the lead discovery, enrichment, qualification, deduplication and Airtable admission logic against mature CRM/data-quality patterns.

## Findings

### F-01 — Single-source discovery was insufficient
Risk: company-name search produces many records without an actionable reason to call.

Correction: search is now defined as sphere × need × source × scenario.

### F-02 — Phone acquisition needed a waterfall
Risk: a directory without a phone could become a useless operational lead.

Correction: phone enrichment is multi-source and absence of a usable phone is a hard rejection from the operational dataset.

### F-03 — Identity verification needed to precede operational admission
Risk: name similarity can create duplicates or wrong organizations.

Correction: normalized INN + active-status verification precede READY LEAD admission.

### F-04 — Need semantics were under-specified
Risk: sector fit was being mistaken for actual demand.

Correction: Почему → Зачем → Потребность → Основание потребности are now separate semantic roles.

### F-05 — LPR data could be fabricated by inference
Risk: inferred decision-maker identity could be presented as fact.

Correction: a confirmed person and an inferred role are explicitly separated.

### F-06 — Coverage could terminate too early
Risk: arbitrary small batches produce too few unique companies.

Correction: no fixed batch cap; all relevant hierarchy leaves and search scenarios are traversed until the requested target or source exhaustion.

### F-07 — Duplicate handling needed a canonical rule
Risk: the same company could appear from several sources.

Correction: normalized INN is the canonical identity key; existing records are enriched rather than copied.

### F-08 — Operator interface could expose incomplete records
Risk: technical intake states leak into the work surface.

Correction: Airtable work pages use a hard Контроль качества = 1 scope.

## Mature-system alignment

The resulting model follows established mature-CRM principles:

- one source of truth for the company;
- explicit duplicate detection before operational qualification;
- multi-source enrichment;
- evidence-backed qualification;
- lifecycle/status separated from identity;
- auditability of the underlying history.

## Residual risks

1. Public web coverage is finite and changes over time.
2. A general company phone does not prove that the phone reaches the decision-maker.
3. A strong activity signal does not guarantee current purchase intent.
4. External source outages may reduce coverage for a particular run.

These are handled by evidence precedence, source diversification and explicit acceptance metrics.

## Audit result

DESIGN CORRECTED.

The lead acquisition contract is now a first-class architectural boundary rather than an informal search habit.

## Release condition

A release is not accepted until the integrated Airtable test passes and the 1000-opportunity / 500-ready-lead external acceptance benchmark remains compatible with the hard field gate.
