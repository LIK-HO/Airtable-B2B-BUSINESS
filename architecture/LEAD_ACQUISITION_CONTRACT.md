# Lead Acquisition Contract — B2B BUSINESS

## 1. Purpose

This contract defines how external research becomes a READY LEAD for Airtable.
A ready lead is not a candidate, not a raw company hit, and not a record awaiting manual verification.

The operator must receive a compact company record whose core facts and business meaning are already assembled.

## 2. Input

A search request is defined as:

- target geography: Moscow;
- sphere hierarchy node or all leaf nodes;
- one or more need scenarios;
- target result count, when supplied;
- service scope: грузчики / такелаж / разнорабочие / related linear personnel;
- optional exclusions.

For a broad request, the search expands across all relevant leaf spheres and configured need scenarios.

## 3. Search matrix

Search is performed by:

сфера × потребность × источник × сценарий запроса

The search is not a single generic web query.

Each sphere supplies typical needs and search signals. Each scenario is tested against multiple source classes.

## 4. Source roles

### A — identity / official verification
FNS / EGRUL and equivalent official registries.

Used for:
- legal name;
- INN;
- active status;
- legal identity;
- official sector attributes.

### B — organization / phone / commercial signals
Maps, business directories, job sites, procurement sources, commercial databases.

Used for:
- operating organization;
- general business phone;
- active operational signals;
- need signals.

### C — industry / professional signals
Industry catalogues, exhibitions, professional communities and specialized sources.

Used for:
- sector fit;
- project/activity signals;
- supplementary need evidence.

### D — weak supplementary signals

Used only as supporting context.
A weak signal alone cannot make a lead operationally ready.

## 5. Enrichment waterfall

For each discovered organization:

1. identify the exact organization;
2. normalize and confirm INN;
3. confirm active status where applicable;
4. find a usable general business phone;
5. confirm Moscow relevance;
6. confirm sphere;
7. establish a concrete need or a strong documented need signal;
8. establish the relevant decision-maker role;
9. collect evidence for identity, phone, need and role;
10. deduplicate by normalized INN;
11. calculate rating and priority;
12. admit only READY LEAD records to the operational dataset.

Phone enrichment is multi-source. Failure in one source does not end the search.

## 6. Hard READY LEAD gate

A record is READY only when all are true:

- Moscow / target geography fit;
- organization identified;
- INN confirmed;
- active organization status confirmed where applicable;
- usable general business phone found;
- target sphere assigned;
- concrete need or strong documented need signal;
- Почему is evidence-based;
- Зачем explains the business task creating the opportunity;
- Потребность states the concrete work;
- Основание потребности records the evidence;
- LPR role is known or explicitly marked as an inferred role;
- provenance is retained;
- rating is 3–5.

If one mandatory condition is missing, the record is not ready.

Incomplete results are not exported into КОМПАНИЯ / ОЧЕРЕДЬ.

## 7. Semantic separation

The fields have different meanings:

- Почему — why this company belongs to the target segment;
- Зачем — what business situation creates the opportunity;
- Потребность — what work/service is actually relevant;
- Основание потребности — what public evidence supports the need statement.

The system must not turn a generic company description into a false statement of current demand.

## 8. LPR rule

The system may record:

- a publicly identified person and role, when reliably sourced;
- a role only, when the relevant decision-maker role is inferable from the organization's structure.

A role inference must never be presented as a confirmed person's identity.

## 9. Identity and deduplication

Primary canonical key:

normalized INN

Rules:

- digits only;
- one INN = one canonical company record;
- an existing INN is updated, not duplicated;
- name similarity and phone similarity are secondary duplicate signals;
- no display-name matching is treated as a canonical key.

## 10. Evidence precedence

When sources conflict:

### Identity
Official registry > reputable commercial database > directory.

### Phone
Official company contact > reputable map/directory > commercial database.

### Need
Direct company statement/listing > vacancy/tender/request/activity signal > profile description > weak inference.

A lower-grade source cannot silently override a higher-grade source.

## 11. Rating

- 5 — direct fit + strong/current need signal + usable phone + strong LPR signal.
- 4 — strong fit + credible need signal + usable phone.
- 3 — valid target fit + credible need signal with lower certainty.
- 1–2 — excluded from operational pool.

Rating is a quality gate, not a promise of conversion.

## 12. Coverage and batching

There is no artificial cap of 10, 20 or 30 records.

For a target of 1000 search opportunities, the workflow proceeds through the configured sphere hierarchy, need scenarios and source classes until:

- the requested quantity of READY LEADS is reached; or
- the configured source/scenario space is exhausted.

The output is deduplicated after enrichment, not before.

## 13. Quality report

Every broad search run must be measurable internally:

- discovered organizations;
- identity confirmed;
- active status confirmed;
- phone found;
- need signal found;
- LPR role established;
- duplicates merged;
- exclusions by reason;
- READY LEADS.

The operator-facing Airtable dataset contains only ready operational records.

## 14. Security

Search data may contain public business information only.
Secrets, API keys, session tokens and credentials never enter Airtable records or the repository.

## 15. Acceptance benchmark

The project-level external acceptance test is:

1000 search opportunities across the Moscow sphere hierarchy → at least 500 unique READY LEADS.

The denominator is the 1000 search opportunities requested by the operator.
The numerator counts only unique records that pass the complete READY LEAD gate.

The test fails if:

- READY LEADS < 500; or
- any record presented as ready is missing a mandatory core field such as phone, concrete need, confirmed INN, sphere or evidence-based meaning; or
- the output loses ordering/logic so the operator cannot understand why the company is present and what to do next.

This benchmark is an acceptance criterion, not a guarantee about external source coverage.

## 16. Non-negotiable failure mode

Never fill a missing fact with an invented value merely to increase the ready count.
A smaller truthful set is preferable to a larger fabricated or semantically weak set.
