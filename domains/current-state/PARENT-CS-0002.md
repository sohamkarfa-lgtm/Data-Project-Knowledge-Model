---
id: PARENT-CS-0002
domain: current-state
type: pain-point
status: validated
owner: enterprise-architecture
relationships:
  - type: derived_from
    target: PARENT-CS-0001
  - type: evidenced_by
    target: PARENT-EVD-0001
source: "Current Platform Assessment Workshop 2026-08-08"
created: "2026-08-08"
tags: [tech-debt, key-person-risk]
---

## Summary
Only two people understand the full pipeline, and complex
transformations are undocumented.

## Details
Transformation logic for the complex transformations is undocumented
and depends on the knowledge of only two people who understand the full
pipeline. No test coverage exists to validate correctness if logic needs to be
reproduced elsewhere.

## Impact
- Blocks safe migration of these pipelines until logic is documented.
- Represents an operational risk independent of the modernization program.
- Should be flagged as a `delivery` risk with a mitigation task to document
  logic before migration begins.
