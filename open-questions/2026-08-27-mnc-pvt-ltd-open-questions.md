# Current-State Assessment — MNC Pvt Ltd

**Assessment date:** 2026-08-27  
**Source files:** `domains/current-state/PARENT-CS-0001.md` through `PARENT-CS-0007.md`, `domains/evidence/PARENT-EVD-0001.md`, and `meeting_summary/meeting-2026-08-27`  
**System/engagement:** MNC Pvt Ltd data platform

## 1. Stated Pains

- ETL workflows are stored only in a GUI-based tool and are not managed under version control. — *Source: PARENT-CS-0003*
- Business logic is duplicated across Finance, Sales, Campaign, and Customer Ops data marts, causing inconsistent metric definitions. — *Source: PARENT-CS-0004; meeting summary*
- The nightly batch chain takes approximately five to six hours, has degraded from approximately three hours two years ago, and has no automated retry. — *Source: PARENT-CS-0005; PARENT-EVD-0001; meeting summary*
- Only two people understand the full pipeline, and three complex transformations are undocumented. — *Source: PARENT-CS-0002; meeting summary*
- The platform has no formal data catalog or data quality tooling beyond basic row-count reconciliation. — *Source: PARENT-CS-0006; PARENT-EVD-0001; meeting summary*
- The platform creates recurring cost pressure through annual ETL licensing and on-premises warehouse hardware maintenance. — *Source: PARENT-CS-0007; meeting summary*
- New reporting needs outside the four existing marts take approximately six to eight weeks to deliver, with no self-service option for business users. — *Source: meeting summary*
- ETL and warehouse capacity are fixed and co-located; additional capacity requires hardware procurement with an observed lead time of approximately eight to twelve weeks. — *Source: PARENT-EVD-0001; meeting summary*

## 2. Implied Pains

- [INFERRED] Business reporting may be delayed when a nightly job fails. — *Reasoning: one failure blocks all downstream processing and recovery is manual.* **Domain:** delivery
- [INFERRED] Reproducing or migrating undocumented transformations may produce incorrect results. — *Reasoning: complex transformations lack documentation and test coverage.* **Domain:** delivery
- [INFERRED] The lack of shared metric definitions may reduce confidence in management reporting. — *Reasoning: independently maintained definitions already caused a Finance-versus-Sales discrepancy.* **Domain:** governance
- [INFERRED] The lack of a clean data dictionary increases the time needed to assess source data for new reporting or migration. — *Reasoning: the source has approximately 1,000 organically grown tables and no clean data dictionary.* **Domain:** evidence
- [INFERRED] The current platform may be unable to respond quickly to demand for new reporting capacity. — *Reasoning: delivery takes six to eight weeks and infrastructure scaling requires procurement.* **Domain:** delivery

## 3. Current-State Facts

- **Domain:** current-state — One transactional database with approximately 1,000 tables and approximately 15 years of organic growth.
- **Domain:** current-state — ODBC extraction feeds scheduled batch jobs in a GUI-based ETL tool.
- **Domain:** current-state — A traditional on-premises relational data warehouse serves business reporting.
- **Domain:** current-state — Four data marts serve Finance, Sales, Campaign, and Customer Ops.
- **Domain:** current-state — Storage and compute share fixed-capacity on-premises infrastructure.
- **Domain:** current-state — The BI reporting tool connects directly to the warehouse and there is no semantic or metrics layer.
- **Domain:** current-state — A single central team maintains ingestion, transformation, and infrastructure.
- **Domain:** current-state — The current platform has no near-real-time ingestion capability.
- **Domain:** current-state — Finance uses the data for daily book closing, making the four marts business-critical.

## 4. Stakeholder Dynamics

- **Domain:** governance — Finance and Sales independently maintain or consume definitions for the same metrics; this resulted in a reported net-revenue discrepancy.
- **Domain:** governance — A single central team is responsible for ingestion, transformation, and infrastructure, with no separation between platform and pipeline concerns.
- **Domain:** delivery — Pipeline knowledge is concentrated in a very small number of people, and handover/documentation is incomplete.
- **Domain:** requirements — Business users depend on the existing four marts, while requests outside them have a six-to-eight-week delivery cycle and no self-service route.
- **Domain:** governance — Specific stakeholder names and decision rights are not provided. **Owner:** [NEEDS HUMAN INPUT: stakeholder names and decision rights]

## 5. Open Questions

1. **Business criticality and blast radius** — Which reports, business processes, and users are blocked when the nightly batch is late or unavailable? **Domain:** requirements **Likely answerable by:** [NEEDS HUMAN INPUT: business process owners]
2. **Finance close dependency** — What is the latest acceptable data-availability time for daily Finance book closing, and what is the business impact if that time is missed? **Domain:** requirements **Likely answerable by:** [NEEDS HUMAN INPUT: Finance process owner]
3. **Batch reliability** — How often have nightly jobs failed or exceeded the available processing window, and what has been the historical recovery time? **Domain:** delivery **Likely answerable by:** [NEEDS HUMAN INPUT: ETL operations owner]
4. **Failure dependencies** — Which jobs can run independently, and which dependencies cause one failure to block the complete chain? **Domain:** current-state **Likely answerable by:** [NEEDS HUMAN INPUT: pipeline subject-matter expert]
5. **Pipeline ownership** — Who are the two people with full-pipeline knowledge, and which three transformations are undocumented? **Domain:** governance **Likely answerable by:** [NEEDS HUMAN INPUT: current platform manager]
6. **Knowledge concentration discrepancy** — Does “only two people understand the full pipeline” describe the same risk as “three of twelve production pipelines are maintained by a single engineer,” or are these separate findings? **Domain:** evidence **Likely answerable by:** [NEEDS HUMAN INPUT: assessment participants]
7. **Metric governance** — Who owns the canonical definition of net revenue and other shared metrics, and how are changes approved and communicated across marts? **Domain:** governance **Likely answerable by:** [NEEDS HUMAN INPUT: Finance and Sales metric owners]
8. **Data quality** — Which data-quality dimensions beyond row counts are business-critical, and what thresholds should trigger an alert or stop downstream processing? **Domain:** requirements **Likely answerable by:** [NEEDS HUMAN INPUT: data quality owner and business data owners]
9. **Lineage and catalog** — Which datasets and lineage paths must be documented first to support Finance close and migration planning? **Domain:** evidence **Likely answerable by:** [NEEDS HUMAN INPUT: data consumers and migration lead]
10. **Capacity and performance** — What capacity limit or workload causes the current five-to-six-hour runtime, and what growth is expected over the next twelve to twenty-four months? **Domain:** current-state **Likely answerable by:** [NEEDS HUMAN INPUT: platform and infrastructure owner]
11. **Reporting demand** — Which reporting requests are delayed by the six-to-eight-week delivery cycle, and what business value or cost is associated with the delay? **Domain:** requirements **Likely answerable by:** [NEEDS HUMAN INPUT: business reporting stakeholders]
12. **Cost baseline** — What are the annual ETL licensing, hardware maintenance, procurement, and operational recovery costs? **Domain:** evidence **Likely answerable by:** [NEEDS HUMAN INPUT: finance/procurement and platform owners]
13. **Transition constraint** — What does “proven” mean for each mart before cutover, and which acceptance criteria must be met during parallel running? **Domain:** requirements **Likely answerable by:** [NEEDS HUMAN INPUT: Finance, Sales, Campaign, Customer Ops, and transition decision-makers]
14. **Target-state follow-up** — Who must attend the target-state options session, and what options or decision criteria should it cover? **Domain:** target-state **Likely answerable by:** [NEEDS HUMAN INPUT: meeting sponsor]

## Question List for Next Meeting

1. **What reports and business processes are blocked when the nightly batch misses its processing window, and what is the cost of that impact?** — *Ask: [NEEDS HUMAN INPUT: business process owners]* — *Why: sizes the business criticality and blast radius of the batch-chain risk.*
2. **What is the latest acceptable data-availability time for Finance book closing, and what happens when that deadline is missed?** — *Ask: [NEEDS HUMAN INPUT: Finance process owner]* — *Why: turns the stated Finance dependency into an explicit availability requirement.*
3. **How often do batch failures occur, how long does recovery take, and which dependencies prevent partial restart?** — *Ask: [NEEDS HUMAN INPUT: ETL operations owner and pipeline subject-matter expert]* — *Why: establishes reliability, recovery, and failure-isolation requirements.*
4. **Which three transformations are undocumented, who can validate their behavior, and what would be the impact of reproducing one incorrectly?** — *Ask: [NEEDS HUMAN INPUT: current platform manager and pipeline experts]* — *Why: sizes the key-person and migration risk.*
5. **Who owns the canonical definition of net revenue, and what governance process will approve shared metric definitions?** — *Ask: [NEEDS HUMAN INPUT: Finance and Sales metric owners]* — *Why: prevents recurrence of the reported cross-mart discrepancy.*
6. **Which data-quality checks are required before Finance and other business users can rely on a dataset?** — *Ask: [NEEDS HUMAN INPUT: data quality owner and business data owners]* — *Why: defines the quality controls missing from row-count reconciliation.*
7. **Which datasets and lineage paths must be cataloged first, and who will maintain that information?** — *Ask: [NEEDS HUMAN INPUT: data consumers and governance owner]* — *Why: reduces investigation time and migration uncertainty.*
8. **What workload, data-volume growth, or infrastructure limit explains the runtime increase from approximately three hours to five or six hours?** — *Ask: [NEEDS HUMAN INPUT: platform and infrastructure owner]* — *Why: identifies the cause and future blast radius of the scaling constraint.*
9. **Which delayed reporting requests have the highest business value, and what self-service capabilities would address them?** — *Ask: [NEEDS HUMAN INPUT: business reporting stakeholders]* — *Why: quantifies the delivery-agility pain rather than treating lead time as an isolated technical metric.*
10. **What are the annual licensing, hardware, procurement, and recovery costs of the current platform?** — *Ask: [NEEDS HUMAN INPUT: finance/procurement and platform owners]* — *Why: creates the cost baseline needed for target-state comparison.*
11. **What evidence and acceptance criteria must each mart meet before it can be cut over, and how long must parallel running continue?** — *Ask: [NEEDS HUMAN INPUT: mart owners and transition decision-makers]* — *Why: makes the no-big-bang constraint measurable and protects business-critical reporting.*
12. **Which stakeholders must attend the target-state options session, and what decision must that session produce?** — *Ask: [NEEDS HUMAN INPUT: meeting sponsor]* — *Why: turns the stated next step into an actionable decision process.*

## Source and resolution notes

- **[CONFLICT NEEDS HUMAN RESOLUTION]** The current-state material says only two people understand the full pipeline and three complex transformations are undocumented. The evidence entry says three of twelve production pipelines are maintained by a single engineer with no documented handover. Confirm whether these describe the same or separate risks.
- No named meeting participants or explicit owners for the open questions were provided. All such roles use `[NEEDS HUMAN INPUT: ...]` markers.
- The assessment is based on existing model files and the 2026-08-27 meeting summary; no current-state source files were modified.
