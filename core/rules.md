# Core Rules — B2B BUSINESS

- R-001: A company cannot enter the operational dataset without a confirmed INN and a usable general business phone.
- R-002: One normalized INN identifies one canonical КОМПАНИЯ record.
- R-003: КЛИЕНТ, ОЧЕРЕДЬ and АРХИВ are projections of КОМПАНИЯ, never copied records.
- R-004: ПЕРЕЗВОНИТЬ remains in the ОЧЕРЕДЬ projection until resolved.
- R-005: Status transitions are limited to ОЧЕРЕДЬ, КЛИЕНТ, ПЕРЕЗВОНИТЬ and АРХИВ.
- R-006: Technical/reference data stays outside the top-level operator navigation.
- R-007: Company identity is not duplicated in contact history or orders.
- R-008: First/last contact dates are derived from contact history; the full history remains the canonical event log.
- R-009: A repeat order is another ЗАКАЗ linked to the same company, never another company record.
- R-010: Address and website are optional supporting data and are hidden from compact work lists.
- R-011: Budget estimation is not part of the canonical lead model.
- R-012: Rating 1–2 is not valid for the operational company pool; operational companies are rated 3–5.
- R-013: The assistant/search workflow must check INN against the existing КОМПАНИЯ dataset before creating a new company record.
- R-014: No mandatory Airtable automation or AI component may be introduced without a demonstrated operational need.
- R-015: Airtable field names and display names are never treated as immutable business identifiers.
- R-016: Secrets never enter Airtable records, interface text or repository files.
