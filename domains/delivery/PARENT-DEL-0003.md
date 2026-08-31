---
id: PARENT-DEL-0003
domain: delivery
type: risk
status: draft
owner: "[NEEDS HUMAN INPUT: accountable owner]"
relationships:
  - type: depends_on
    target: PARENT-DEL-0001
  - type: satisfies
    target: PARENT-REQ-0005
source: "Target State Architecture Discussion 2026-08-28"
created: "2026-08-28"
tags: [cloud-cost, forecasting, finance]
---

## Summary
Consumption-based cloud pricing may be difficult for Finance to forecast during
the transition from fixed hardware budgeting.

## Details
**Likelihood:** [NEEDS HUMAN INPUT: likelihood]

**Impact:** Finance may delay or constrain platform scaling because expected
costs are unclear.

**Mitigation:** Begin with a capped dev/test environment and visible cost
monitoring during Milestone 1, then use observed cost data before scaling across
all four business domains.