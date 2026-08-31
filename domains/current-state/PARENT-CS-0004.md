---
id: PARENT-CS-0004
domain: current-state
type: pain-point
status: validated
owner: enterprise-architecture
relationships:
  - type: derived_from
    target: PARENT-CS-0001
  - type: evidenced_by
    target: PARENT-EVD-0001
source: "Current State Discovery Workshop 2026-08-27"
created: "2026-08-27"
tags: [metrics, duplicated-logic, reporting]
---

## Summary
Business logic is duplicated across four stakeholder-specific data marts.

## Details
Finance, Sales, Campaign, and Customer Ops marts define metrics independently.
The independently defined "net revenue" metric caused a Finance-versus-Sales
reporting discrepancy last quarter that took two weeks to trace.

## Impact
Reports can disagree on the same business metric, and investigating the cause
requires significant manual effort.