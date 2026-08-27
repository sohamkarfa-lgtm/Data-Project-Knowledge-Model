---
id: PARENT-CS-0001
domain: current-state
type: architecture
status: validated
owner: enterprise-architecture
relates_to: [PARENT-EVD-0001]
source: "Current Platform Assessment Workshop 2026-08-08"
created: "2026-08-08"
tags: [on-prem]
---

## Summary
An on-premises data platform consisting of one transactional database,
GUI-based ETL, a relational data warehouse, and four stakeholder-specific data
marts serving scheduled and ad-hoc business reporting.

## Details
- **Ingestion**: Data is extracted from source systems through ODBC connections 
  and processed by scheduled batch jobs.
- **Storage/Processing**: relational data warehouse hosted on on-prem servers;
  fixed storage and compute capacity, shared across all workloads.
- **Transformation**: stored-procedure-based ETL, orchestrated by a legacy
  scheduler and managed through a traditional GUI-based ETL tool.
- **Serving**: BI reporting tool connects directly to the warehouse; no
  semantic/metrics layer — four marts serve Finance, Sales, Campaign, and
  Customer Ops, with business logic duplicated across marts.
- **Source**: one transactional database with approximately 1,000 tables and
  approximately 15 years of organic growth; no clean data dictionary exists.
- **Operations**: single central team maintains ingestion, transformation, and
  infrastructure; no separation of platform vs. pipeline concerns.

## Impact
All current business reporting depends on this path. Finance uses the data
for daily book closing. Any modernization must migrate these flows
incrementally and dual-run them without disrupting existing reports until each
piece is proven.
