---
id: PARENT-DEL-0002
domain: delivery
type: risk
status: validated
owner: platform-engineer-lead
relationships:
  - type: derived_from
    target: PARENT-CS-0002
  - type: depends_on
    target: PARENT-DEL-0001
source: "Delivery Planning Session 2026-08-22"
created: "2026-08-22"
tags: [risk, key-person]
---

## Summary
Key-person dependency (PARENT-CS-0002) could block migration of the three
affected pipelines if not mitigated before those pipelines are in scope for
migration.

## Details
**Likelihood:** Medium — the individual remains available today but has no
documented backup.
**Impact:** High for the specific pipelines affected; no impact to Milestone 1
scope since those pipelines are not in the Milestone 1 use case.
**Mitigation:** Document existing logic for the three pipelines before they
are scheduled for migration in a later milestone. Not a Milestone 1 blocker,
but should be scheduled early in Milestone 2 planning.
