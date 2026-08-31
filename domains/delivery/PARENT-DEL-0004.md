---
 id: PARENT-DEL-0004
 domain: delivery
 type: workstream
 status: validated
 owner: platform-engineer-lead
relationships:
  - type: decided_by
    target: PARENT-ADR-0002
  - type: satisfies
    target: PARENT-REQ-0001
  - type: satisfies
    target: PARENT-REQ-0004
  - type: depends_on
    target: PARENT-DEL-0001
 source: "Parent Knowledge Model delivery planning"
 created: "2026-08-28"
 tags: [fabric, landing-zone, capacity, identity]
---

## Summary
Fabric platform foundation workstream for Milestone 1, covering capacity,
landing-zone planning, and Entra ID access.

## Details
**Scope:**
- Draft the Fabric-specific landing-zone plan.
- Start and complete capacity procurement and sizing.
- Configure environments, storage, and Entra ID group-based access.

**Dependencies:**
- PARENT-ADR-0002 sign-off.
- Existing Entra ID groups and role mapping.

**Exit criteria:**
- Fabric capacity is provisioned at an agreed Milestone 1 size.
- The landing zone is available for the Supply Chain workstream.
- Workspace access is mapped to existing Entra ID groups.
