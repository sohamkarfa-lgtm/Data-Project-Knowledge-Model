---
id: PARENT-GOV-0001
domain: governance
type: operating-model
status: draft
owner: governance
relates_to: [PARENT-ENG-0002]
source: "Governance Alignment Session 2026-08-15"
created: "2026-08-15"
tags: [ownership]
---

## Summary
Draft operating model: platform infrastructure is centrally owned by Platform
Engineering; data products built on top are owned by the producing business
domain team ("data mesh"-influenced, not full decentralization at MVP stage).

## Details
- Platform Engineering owns: landing zone, networking, identity, shared
  storage/compute platform, platform-level security controls.
- Each Engineering discipline (Data/Analytics/DevOps/AI-ML) owns its own
  knowledge model repo and the artifacts within its remit.
- Business-unit-aligned data product ownership is a target-state ambition,
  not required for MVP — MVP keeps a single central data engineering team
  producing the first use case.

## Applies To
All engineering-discipline knowledge model repos; referenced by their
`relates_to` fields rather than duplicated.
