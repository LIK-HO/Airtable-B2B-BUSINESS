# Security Model

## Domains
1. Access control.
2. Data integrity.
3. Secret handling.
4. Automation safety.
5. Export/migration safety.
6. Recovery readiness.

## Requirements
- least privilege;
- technical data separated from operator surfaces;
- no secrets in repository or Airtable configuration records;
- critical writes auditable;
- destructive actions restricted;
- safe failure over silent mutation.

## Repository rule
Never commit Airtable PATs, API keys, OAuth tokens, webhook secrets or private credentials.
