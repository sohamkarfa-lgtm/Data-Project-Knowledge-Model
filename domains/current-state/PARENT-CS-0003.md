---
id: PARENT-CS-0003
domain: current-state
type: technical-debt
status: validated
owner: enterprise-architecture
relationships:
  - type: derived_from
    target: PARENT-CS-0001
  - type: depends_on
    target: PARENT-TS-0001
source: "Current State Discovery Workshop 2026-08-27"
created: "2026-08-27"
tags: [etl, version-control, technical-debt]
---

## Summary
ETL workflows are stored only in the GUI-based ETL tool and are not managed
under version control.

## Details
Workflow changes are coordinated informally over chat. The repository has no
versioned source representation of the ETL logic.

## Impact
Changes cannot be reviewed, compared, or reliably rolled back, increasing the
risk of undocumented production behavior during modernization.