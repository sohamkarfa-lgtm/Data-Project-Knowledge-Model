---
id: PARENT-CS-0006
domain: current-state
type: technical-debt
status: validated
owner: enterprise-architecture
relationships:
  - type: derived_from
    target: PARENT-CS-0001
  - type: evidenced_by
    target: PARENT-EVD-0001
source: "Current State Discovery Workshop 2026-08-27"
created: "2026-08-27"
tags: [data-quality, catalog, lineage]
---

## Summary
The current platform has no data quality tooling or data catalog.

## Details
Data quality monitoring is limited to basic row-count reconciliation. Data
lineage and knowledge about data meaning are maintained through tribal
knowledge.

## Impact
Data issues and the origin of reported values are difficult to detect,
understand, and investigate.