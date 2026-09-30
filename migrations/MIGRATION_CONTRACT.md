# Migration Contract

Every migration records:
- source version;
- target version;
- structural changes;
- data transformation;
- preflight checks;
- postflight reconciliation;
- failure/recovery path;
- test evidence.

A schema write accepted by Airtable is not itself migration success.
