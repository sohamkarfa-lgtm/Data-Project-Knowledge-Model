---
id: PARENT-DEL-0001
domain: delivery
type: milestone
status: validated
owner: platform-engineering
relates_to: [PARENT-TS-0001, PARENT-REQ-0001, PARENT-REQ-0002]
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
- Landing zone: environments, networking, identity, base storage layout
- One real business reporting use case, source-to-report, running on the new
  platform

**Exit criteria:**
- The chosen use case is live on the new platform and validated by its
  business owner
- Platform Engineering knowledge model repo has current-state and initial
  target-state/decision entries populated
- No further hardware-procurement-driven scaling constraint for that use case

**Explicitly out of scope for Milestone 1:**
- Migrating all existing pipelines off on-prem
- Full data governance/catalog rollout
- Decommissioning any on-prem infrastructure
