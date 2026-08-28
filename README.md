# Parent Knowledge Model — MNC Pvt Ltd

This repository is the **Parent Knowledge Model (PKM)** for the Data & Analytics
delivery engagement at **MNC Pvt Ltd**.

It is the single source of truth for enterprise-wide context — business,
architecture, requirements, governance, and delivery — that engineering-discipline
knowledge models (Platform Engineering, Data Engineering, Analytics Engineering,
DevOps, AI/ML) link back to.

The current model captures an on-premises data platform modernization scenario.
The structure, ID scheme, and frontmatter schema remain reusable for future
engagements; replace the example entities and client-specific content when
starting a new engagement.

## Why this exists

Data & Analytics delivery knowledge is normally scattered across docs, tickets,
meeting notes, and people's heads. This repo turns that into structured,
versioned, linkable entities so that:

- Every decision is traceable back to the evidence and requirement that drove it
- New team members and AI copilots can query "why" as easily as "what"
- Gap analysis, dependency analysis, and risk assessment can be automated over
  a consistent knowledge graph instead of re-discovered every time

## Repository structure

```
/domains
  /engagement       Business & stakeholder context
  /evidence         Discovery findings, workshops, assessments
  /requirements     Business, functional, non-functional, compliance, data
  /current-state    As-is architecture, platforms, pain points, tech debt
  /governance       Standards, controls, ownership, operating model
  /target-state     To-be architecture, strategy, roadmap
  /delivery         Workstreams, milestones, risks, assumptions, dependencies
/schemas            Entity & frontmatter schema definitions
/adr                Enterprise/solution-architecture-level decision records
/meeting_transcript Source meeting transcripts
/meeting_summary    Structured meeting summaries and source notes
/open-questions     Assessment outputs and questions for upcoming meetings
/prompt-library     Reusable prompts for summaries, updates, and discovery
/sign-off-docs       Approval and sign-off documents used as evidence
/_pending-review    Staged content awaiting human review or approval
entities.index.yaml Registry of every entity in this repo (and links to child repos)
CHANGELOG.md        Human-readable log of what changed, release by release
```

Each domain folder contains:
- `_template.md` — a blank, generic template. Copy this to start a new entry.
- One or more populated example files showing the template in use for the
  `MNC Pvt Ltd` on-prem → cloud modernization scenario.

The `open-questions/` folder contains working assessment outputs and is not an
entity domain. Its files may reference entity ids, but they are not added to
`entities.index.yaml` unless they are later converted into domain entities.

## Prompt workflows

The reusable prompts in `prompt-library/` support the current workflow:

- `meeting-transcript-to-summary.md` — extracts and organizes meeting content,
  tags each pointer to a core domain, and marks unknown owners or domains with
  `[NEEDS HUMAN INPUT: ...]`.
- `meeting-summary-to-domain-update.md` — classifies meeting content and
  proposes new or updated entities behind an explicit human approval gate.
- `decision-readiness-to-adr.md` — assesses a pending decision against model
  evidence and requirements, compares alternatives, and prepares an
  approval-gated ADR proposal.
- `model-to-delivery-plan.md` — converts model entities into traceable
  milestones, workstreams, dependencies, actions, risks, and acceptance
  criteria behind an explicit approval gate.
- `current-state-discovery/current-state-assessment-and-question-prep.md`
  — assesses current-state knowledge, identifies gaps, and creates an
  `open-questions/` outcome file for the next meeting.

Generated summaries, plans, decision records, and question lists must preserve
source attribution. Do not guess owners, dates, domains, statuses, scores, or
decisions; use a specific `[NEEDS HUMAN INPUT: ...]` marker instead.

All prompts that propose model changes are approval-gated. The normal flow is:

1. Read source material and existing entities.
2. Produce a reviewable proposal with traceable IDs and relationship links.
3. Wait for explicit human approval.
4. Apply only the approved changes and validate the registry, paths, links, and
   frontmatter.

Sign-off emails and other approval artifacts belong in `sign-off-docs/` and
should be represented by an evidence entity when they support a decision or
status change. Keep unresolved approval metadata explicit until it is verified.

## Entity ID convention

`PARENT-<DOMAIN-CODE>-####`

| Domain          | Code |
|-----------------|------|
| Engagement      | ENG  |
| Evidence        | EVD  |
| Requirements    | REQ  |
| Current State   | CS   |
| Governance      | GOV  |
| Target State    | TS   |
| Delivery        | DEL  |

Engineering-discipline repos use their own prefix, e.g. `PLAT-` (Platform
Engineering), `DE-` (Data Engineering), `AE-` (Analytics Engineering), `DEVOPS-`,
`AIML-`. IDs are never reused or renumbered, even if content is superseded —
supersede with `status: superseded` and a `superseded_by` reference instead.

## How child repos link back

Every engineering-discipline knowledge model repo (e.g.
`knowledge-model-platform-engineering`) keeps its own `entities.index.yaml` and
references parent entities via the `relates_to` field in its frontmatter, e.g.
`relates_to: [PARENT-REQ-0003]`.

At MVP stage, cross-repo linking is just consistent IDs plus each repo's index
file — no shared database needed yet. Once the number of entities grows, an
agent (or a simple script) can walk both index files and build the full graph.
A graph database (e.g. Neo4j) or vector index for RAG is a natural later step,
not a prerequisite to start.

## Entry lifecycle

Every entity has a `status`:

- `draft` — captured but not yet confirmed with a stakeholder/owner
- `validated` — confirmed and ready to be relied on for decisions
- `superseded` — no longer current; `superseded_by` points to the replacement

Only `validated` entities should be treated as ground truth by AI agents doing
gap or dependency analysis.

## Versioning

Tag releases per meaningful milestone, not per commit, e.g.:

```
git tag parent/v0.1.0 -m "Initial engagement context and current-state capture"
```

Keep `CHANGELOG.md` updated at each tag so a human (or an AI agent) can see
what changed between versions without diffing every file.

## Getting started with a new engagement

1. Duplicate this repo (or fork the scaffold) per client/engagement.
2. Replace `MNC Pvt Ltd` throughout with the real client name.
3. Delete or rewrite the example entities, meeting summaries, and open-question
  outputs; keep the `_template.md` files and reusable prompts.
4. Start with `engagement/` and `current-state/` — you can't write meaningful
   requirements or target-state until those are captured.
5. Use the assessment prompt to identify gaps and create the first
  `open-questions/` file before the next discovery session.
6. Stand up the first engineering-discipline repo (e.g. Platform Engineering)
   once `current-state` and the first `target-state` decisions exist for it to
   link against.
