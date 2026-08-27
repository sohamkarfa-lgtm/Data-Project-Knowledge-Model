---
id: PARENT-CS-0005
domain: current-state
type: operational-process
status: validated
owner: enterprise-architecture
relates_to: [PARENT-CS-0001, PARENT-DEL-0001]
source: "Current State Discovery Workshop 2026-08-27"
created: "2026-08-27"
tags: [batch, reliability, etl]
---

## Summary
The nightly batch chain is a fragile sequential process with a runtime of
approximately five to six hours.

## Details
The chain has degraded from approximately three hours two years ago. A single
job failure blocks all downstream processing. There is no automated retry;
failures generate email alerts only.

## Impact
Reporting data may be delayed for the business, and operational recovery
requires manual intervention.