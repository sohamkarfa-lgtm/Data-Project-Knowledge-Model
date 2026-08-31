---
id: PARENT-DEL-0001
domain: delivery
type: milestone
status: validated
owner: platform-engineer-lead
relationships:
  - type: depends_on
    target: PARENT-TS-0001
  - type: satisfies
    target: PARENT-REQ-0001
  - type: satisfies
    target: PARENT-REQ-0002
  - type: satisfies
    target: PARENT-REQ-0005
  - type: satisfies
    target: PARENT-REQ-0007
  - type: decided_by
    target: PARENT-ADR-0002
source: "Delivery Planning Session 2026-08-22"
created: "2026-08-22"
tags: [mvp, milestone-1]
---

## Summary
Milestone 1: stand up a cloud-based data platform landing zone and deliver one
business use case end-to-end, validating the target architecture direction.

## Details
**Scope:**
- Cloud platform/product decision recorded as an ADR
- Use Microsoft Fabric as the selected analytics compute platform, subject to
  ADR sign-off
- Landing zone: environments, networking, identity, base storage layout
- One real business reporting use case, preferably Supply Chain inventory
  visibility, running on the new platform within the current quarter
- Capped dev/test environment and visible cost monitoring from week one
- Fabric-specific landing-zone plan
- Structured enablement plan for Dataflows Gen2, pipeline orchestration, and
  semantic models

**Exit criteria:**
- The chosen use case is live on the new platform and validated by its
  business owner
- Platform Engineering knowledge model repo has current-state and initial
  target-state/decision entries populated
- No further hardware-procurement-driven scaling constraint for that use case
- Finance can view cost tracking from the beginning of the milestone
- The Supply Chain use case is operational in parallel with the existing mart
- Fabric capacity is provisioned at an agreed Milestone 1 size
- The team enablement plan is underway
- Canonical metric definitions are established before Supply Chain go-live

**Explicitly out of scope for Milestone 1:**
- Migrating all existing pipelines off on-prem
- Full data governance/catalog rollout
- Decommissioning any on-prem infrastructure
