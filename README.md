# Parent Knowledge Model — [Client / Org Name]

This repository is the **Parent Knowledge Model (PKM)** for the Data & Analytics
delivery engagement at **[Client / Org Name]** (placeholder used throughout this
scaffold: `MNC Pvt Ltd`).

It is the single source of truth for enterprise-wide context — business,
architecture, requirements, governance, and delivery — that engineering-discipline
knowledge models (Platform Engineering, Data Engineering, Analytics Engineering,
DevOps, AI/ML) link back to.

This scaffold is intentionally **industry-agnostic and reusable**. Swap the
example content for your actual engagement; keep the structure, ID scheme, and
frontmatter schema as-is so every future engagement is consistent and machine
readable by AI agents.

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
entities.index.yaml Registry of every entity in this repo (and links to child repos)
CHANGELOG.md        Human-readable log of what changed, release by release
```

Each domain folder contains:
- `_template.md` — a blank, generic template. Copy this to start a new entry.
- One or more populated example files showing the template in use for the
  `MNC Pvt Ltd` on-prem → cloud modernization scenario.

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
3. Delete or rewrite the example entities — keep the `_template.md` files.
4. Start with `engagement/` and `current-state/` — you can't write meaningful
   requirements or target-state until those are captured.
5. Stand up the first engineering-discipline repo (e.g. Platform Engineering)
   once `current-state` and the first `target-state` decisions exist for it to
   link against.
