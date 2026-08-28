---
id: PARENT-ADR-0002
domain: adr
type: decision
status: draft
owner: "Person D"
relates_to: [PARENT-ADR-0001, PARENT-TS-0001, PARENT-DEL-0001, PARENT-REQ-0003, PARENT-REQ-0004, PARENT-REQ-0005, PARENT-REQ-0006]
source: "Platform Decision: Azure + Microsoft Fabric 2026-09-10"
created: "2026-09-10"
tags: [azure, microsoft-fabric, platform-decision, analytics]
---

## Context
MNC Pvt Ltd previously selected Azure as its cloud direction and needed to
choose between Microsoft Fabric and Azure Databricks as the analytics compute
engine. The options were evaluated against team skill fit, time to first value,
cost predictability, existing tool investment reuse, governance and semantic
layer fit, and operational overhead.

The decision is driven by the reporting-and-analytics-first requirements,
Power BI adoption, the GUI-driven ETL background of the warehouse team, the
Supply Chain target use case, and the need to avoid duplicated metric logic.

## Decision
Proceed with Azure and Microsoft Fabric as the cloud and analytics compute
direction.

This decision is scoped to current reporting-and-analytics-first requirements.
It may be revisited if MNC's ambitions grow materially toward heavy machine
learning or data science workloads.

The decision remains draft until this ADR is circulated and signed off by
Person A.

## Alternatives Considered
- Azure Databricks — not chosen for the current scope because it has a steeper
  learning curve for the existing team, requires additional semantic/BI
  integration, offers less predictable consumption-based pricing, and creates
  greater operational overhead at the starting scale.
- Azure and Microsoft Fabric — chosen because it better fits the existing
  Power BI and GUI-oriented environment, supports a shorter path to the
  Supply Chain use case, provides capacity-based pricing, and reduces
  operational overhead.

## Consequences
- Fabric capacity must be provisioned and sized, initially using a smaller
  capacity SKU subject to confirmation.
- Fabric workspace access must integrate with existing Microsoft Entra ID
  groups.
- The semantic layer must be redesigned so canonical metrics are defined once,
  before the Supply Chain use case goes live.
- The Supply Chain use case must run in parallel with the existing mart until
  the new implementation is proven.
- A Fabric-specific landing-zone plan and team enablement plan are required
  during Milestone 1.
- ADLS Gen2 remains the storage foundation.
- Heavy ML or data-science growth may require reassessing this decision.