---
id: PARENT-ADR-0001
domain: adr
type: decision
status: validated
owner: enterprise-architecture
relationships:
  - type: derived_from
    target: PARENT-ENG-0001
  - type: evidenced_by
    target: PARENT-EVD-0001
  - type: satisfies
    target: PARENT-REQ-0001
source: "Architecture Decision Session 2026-08-21"
created: "2026-08-21"
tags: [strategy]
---

## Context
MNC Pvt Ltd's on-premises data platform (PARENT-CS-0001) cannot meet the
independent storage/compute scaling requirement (PARENT-REQ-0001) and the
faster use-case onboarding requirement (PARENT-REQ-0002) without a
fundamental platform change.

## Decision
Adopt a cloud-first modernization strategy: new business use cases will be
built on a cloud-based platform going forward, with the on-prem platform
continuing to serve existing reporting during an incremental, milestone-based
transition rather than a single cutover.

## Alternatives Considered
- **Upgrade on-prem hardware** — rejected: addresses capacity short-term but
  does not solve independent scaling or reduce procurement lead time.
- **Big-bang full migration** — rejected for MVP: higher risk, delays time to
  value, and does not allow validating the target architecture against a real
  use case before committing fully.

## Consequences
- Requires a specific cloud/platform product decision next (tracked as a
  follow-on ADR in the Platform Engineering knowledge model repo).
- Requires a dual-run/coexistence approach with the on-prem platform during
  transition, captured in PARENT-REQ-0003. The four business-critical marts,
  including Finance's book-closing dependency, must remain available until each
  modernized component is proven.
- Milestone 1 (PARENT-DEL-0001) becomes the first validation point for this
  strategy.
