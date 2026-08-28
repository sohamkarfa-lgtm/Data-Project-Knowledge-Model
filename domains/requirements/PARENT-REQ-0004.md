---
id: PARENT-REQ-0004
domain: requirements
type: non-functional-requirement
status: validated
owner: platform-engineer-lead
relates_to: [PARENT-GOV-0001]
source: "Target State Architecture Discussion 2026-08-28"
created: "2026-08-28"
tags: [identity, security, entra-id, access-control]
---

## Statement
The platform shall provide role-based access control integrated with existing
Microsoft Entra ID groups and shall not require a separate identity system.

## Rationale
MNC's corporate identity is already managed through Microsoft Entra ID, and the
organization wants to avoid duplicating identity administration.

## Acceptance Criteria
- Platform authentication integrates with Microsoft Entra ID.
- Authorization can be mapped to existing Entra ID groups.
- No separate identity system is required for platform access.