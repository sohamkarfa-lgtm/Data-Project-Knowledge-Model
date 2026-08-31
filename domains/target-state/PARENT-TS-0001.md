---
id: PARENT-TS-0001
domain: target-state
type: target-architecture
status: validated
owner: enterprise-architecture
relationships:
  - type: satisfies
    target: PARENT-REQ-0001
  - type: satisfies
    target: PARENT-REQ-0002
  - type: satisfies
    target: PARENT-REQ-0004
  - type: satisfies
    target: PARENT-REQ-0005
  - type: satisfies
    target: PARENT-REQ-0006
  - type: satisfies
    target: PARENT-REQ-0007
  - type: derived_from
    target: PARENT-CS-0001
  - type: decided_by
    target: PARENT-ADR-0002
source: "Target Architecture Working Session 2026-08-20"
created: "2026-08-20"
tags: [azure, adls-gen2, adf, cloud, lakehouse]
---

## Summary
Target architecture is an Azure-based cloud lakehouse platform using
Microsoft Fabric as the analytics compute engine, with independently scalable
storage and compute and Azure Data Lake Storage Gen2 as the common storage
foundation.

## Details
- **Ingestion**: batch and streaming ingestion patterns, replacing
  file-drop-and-poll with managed ingestion services.
- **Cloud direction**: Azure, supported by MNC's Microsoft estate, Enterprise
  Agreement, Microsoft Entra ID, Office 365, and Power BI usage.
- **Platform selection**: Microsoft Fabric was selected over Azure Databricks
  for the current reporting-and-analytics-first scope.
- **Selection rationale**: Fabric better fits the team's existing skills,
  Power BI usage, capacity-based cost predictability, semantic-layer needs,
  existing Microsoft investments, and operational constraints.
- **Initial ingestion**: Fabric Data Factory for batch and hourly Supply Chain
  ingestion. Event Hubs remains a later option if true streaming becomes
  necessary.
- **Storage/Processing**: object storage + medallion architecture
  (bronze/silver/gold), decoupling storage cost/scale from compute cost/scale.
- **Transformation**: version-controlled transformation code (not stored
  procedures), tested and CI/CD-deployed.
- **Serving**: shared semantic/metrics layer so business logic is defined
  once, not duplicated per report.
- **Operations**: platform vs. pipeline ownership split (see
  PARENT-GOV-0001), reducing single-team/single-person dependency.

Microsoft Fabric was selected as the analytics compute engine. The decision is
recorded in PARENT-ADR-0002. The decision may be revisited if MNC's ambitions grow
materially toward heavy machine learning or data science workloads.

## Depends On / Enables
- Depends on PARENT-REQ-0001 (independent scaling) and PARENT-REQ-0002
  (faster onboarding) being the binding constraints.
- Enables a Supply Chain inventory-visibility use case delivered in parallel
  with the existing mart.
- Depends on PARENT-ADR-0002 being signed off before the platform decision is
  treated as final.
- Depends on PARENT-REQ-0003 (incremental coexistence), PARENT-REQ-0004
  (Entra ID access), PARENT-REQ-0005 (cost visibility), PARENT-REQ-0006
  (shared semantic layer), and PARENT-REQ-0007 (ingestion frequencies).
- Enables the first `delivery` milestone: standing up the platform and
  delivering one business use case end-to-end.
