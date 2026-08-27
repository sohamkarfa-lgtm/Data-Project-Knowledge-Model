---
id: PARENT-TS-0001
domain: target-state
type: target-architecture
status: draft
owner: enterprise-architecture
relates_to: [PARENT-REQ-0001, PARENT-REQ-0002, PARENT-CS-0001]
source: "Target Architecture Working Session 2026-08-20"
created: "2026-08-20"
tags: [cloud, lakehouse]
---

## Summary
Target architecture is a cloud-based lakehouse platform with independently
scalable storage and compute, replacing the fixed-capacity on-prem warehouse.

## Details
- **Ingestion**: batch and streaming ingestion patterns, replacing
  file-drop-and-poll with managed ingestion services.
- **Storage/Processing**: object storage + medallion architecture
  (bronze/silver/gold), decoupling storage cost/scale from compute cost/scale.
- **Transformation**: version-controlled transformation code (not stored
  procedures), tested and CI/CD-deployed.
- **Serving**: shared semantic/metrics layer so business logic is defined
  once, not duplicated per report.
- **Operations**: platform vs. pipeline ownership split (see
  PARENT-GOV-0001), reducing single-team/single-person dependency.

Specific vendor/product choice (e.g. which cloud, which lakehouse engine) is
an architecture decision to be recorded separately — see `/adr`.

## Depends On / Enables
- Depends on PARENT-REQ-0001 (independent scaling) and PARENT-REQ-0002
  (faster onboarding) being the binding constraints.
- Enables the first `delivery` milestone: standing up the platform and
  delivering one business use case end-to-end.
