---
id: PARENT-REQ-0006
domain: requirements
type: business-requirement
status: draft
owner: "[NEEDS HUMAN INPUT: accountable owner]"
relationships:
  - type: derived_from
    target: PARENT-CS-0004
  - type: satisfies
    target: PARENT-TS-0001
source: "Target State Architecture Discussion 2026-08-28"
created: "2026-08-28"
tags: [semantic-layer, metrics, reporting]
---

## Statement
The platform shall provide one shared semantic layer in which business logic
and metrics are defined once rather than duplicated across data marts.

## Rationale
Finance and Sales currently define revenue differently, which has caused
reporting discrepancies and prolonged investigation.

## Acceptance Criteria
- Shared business metrics are defined in one governed semantic layer.
- Finance and Sales use the same definition for agreed common metrics.
- The initial Supply Chain use case demonstrates reuse of shared business logic
  where applicable.