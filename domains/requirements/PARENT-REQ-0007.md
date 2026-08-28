---
id: PARENT-REQ-0007
domain: requirements
type: functional-requirement
status: draft
owner: "[NEEDS HUMAN INPUT: accountable owner]"
relates_to: [PARENT-DEL-0001]
source: "Target State Architecture Discussion 2026-08-28"
created: "2026-08-28"
tags: [ingestion, batch, hourly, supply-chain]
---

## Statement
The initial ingestion capability shall support nightly reporting and
closer-to-hourly Supply Chain inventory updates.

## Rationale
Nightly ingestion is sufficient for most reporting, while Supply Chain has a
business need for more frequent inventory visibility because stockouts are
costly.

## Acceptance Criteria
- Nightly ingestion supports the main reporting workloads.
- Supply Chain inventory data can be refreshed at approximately hourly
  frequency.
- A separate streaming platform is not required for the initial hourly use
  case.