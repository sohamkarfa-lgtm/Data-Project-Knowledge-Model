---
id: PARENT-EVD-0001
domain: evidence
type: assessment
status: validated
owner: enterprise-architecture
relates_to: [PARENT-ENG-0001]
source: "Current Platform Assessment Workshop 2026-08-08; Current State Discovery Workshop 2026-08-27"
created: "2026-08-08"
tags: [on-prem, assessment]
---

## Summary
Assessment of the existing on-premises data platform confirms it is
functionally serving the business today but has significant scaling and
agility limitations.

## Details
- Storage and compute are on the same fixed-capacity hardware; scaling either
  requires a hardware procurement cycle (8-12 weeks observed lead time).
- ETL jobs run on a nightly batch schedule; there is no near-real-time
  ingestion capability.
- Three of the twelve production ETL pipelines are maintained by a single
  engineer with no documented handover — a key-person risk.
- No formal data catalog; discovery of "where does this number come from"
  is largely tribal knowledge.
- The source estate contains one transactional database with approximately
  1,000 tables and approximately 15 years of organic growth, with no clean
  data dictionary.
- Four stakeholder-specific data marts serve Finance, Sales, Campaign, and
  Customer Ops.
- The nightly batch chain runs for approximately 5-6 hours, compared with
  approximately 3 hours two years ago.
- Data quality monitoring is limited to basic row-count reconciliation, and
  there is no data catalog.

## Implications
- Feeds directly into `current-state` domain entries.
- Key-person risk and lack of catalog should become explicit risks in
  `delivery` domain once scoping begins.
