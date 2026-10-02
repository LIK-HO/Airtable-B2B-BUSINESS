# Release Gate

Status: ACCEPTANCE_FAILED_CURRENT_RUN

## Completed PASS evidence

- [x] manifest aligned;
- [x] roadmap and architecture contract aligned;
- [x] target schema current;
- [x] six-table Airtable contour implemented;
- [x] 90 source records populated;
- [x] 39 sphere records populated;
- [x] 24 scripts populated;
- [x] sphere parent links verified;
- [x] primary script links verified;
- [x] hard quality gate tested;
- [x] projection semantics tested;
- [x] history and order relationships tested;
- [x] test data removed;
- [x] legacy operator/technical tables removed after zero-business-row preflight;
- [x] legacy technical evidence archived;
- [x] operator interface published;
- [x] real lead run executed;
- [x] 9 real READY LEADS passed field completeness, source-link, sphere/script and duplicate-INN checks.

## Failed acceptance gate

- [ ] >=1000 distinct Moscow candidate organizations discovered where source coverage permits;
- [ ] >=500 unique READY LEADS;
- [ ] complete acquisition funnel reported;
- [ ] zero mandatory-field failures across the full ready set.

Actual current run:
- requested: 1000;
- READY LEADS: 9;
- shortfall: 491;
- result: FAIL.

## Release rule

The product is not accepted as a complete 500/1000 lead-acquisition release while this gate is failed.

Airtable may remain published for inspection, but it is not certified as the completed production lead source until the new external acceptance gate passes.
