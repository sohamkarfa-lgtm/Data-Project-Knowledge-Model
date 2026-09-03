# Agent Instructions

These instructions apply to the whole repository.

## Purpose

This repo is the Parent Knowledge Model for a Data & Analytics engagement. Treat
it as a structured, versioned source of truth for business context, evidence,
requirements, architecture, governance, target state, delivery, and ADRs.

Optimize for traceability over speed. Every new or changed model fact should be
linked to a source, an owner, and related entities where those are known.

## Read First

Before creating or changing model content, read:

- `README.md`
- `schemas/entity-schema.yaml`
- `entities.index.yaml`
- The relevant domain or `adr/_template.md`
- Any existing entity files that may overlap with the requested change

Use `rg`/`rg --files` to find IDs, titles, sources, and related entities.

## Knowledge Model Rules

- Use stable IDs in the format `PARENT-<DOMAIN-CODE>-####`.
- Domain codes are `ENG`, `EVD`, `REQ`, `CS`, `GOV`, `TS`, and `DEL`.
- ADRs use `PARENT-ADR-####` and live in `adr/`.
- Never reuse or renumber IDs.
- New entities start as `status: draft` unless the user has explicitly approved
  validation based on supplied evidence.
- Supersede old content with `status: superseded` and `superseded_by`; do not
  delete or silently replace historical entities.
- Keep each entity atomic. If content spans multiple domains, split it into
  multiple linked entities.
- Use typed `relationships` only when a specific target ID and relationship type
  are justified.

## Evidence And Uncertainty

- Do not invent owners, dates, statuses, scores, decisions, domain placement, or
  relationship links.
- If required information is missing, write `[NEEDS HUMAN INPUT: ...]`.
- If new source material conflicts with existing model content, preserve both
  positions and mark `[CONFLICT NEEDS HUMAN RESOLUTION]`.
- Evidence entities should describe observations, not recommendations.
- Decisions belong in `adr/`; requirements, risks, and target-state statements
  should link to those decisions when relevant.

## Approval Gate

For changes based on meeting notes, transcripts, discovery outputs, sign-off
material, or other source evidence:

1. Propose the new entities, updates, relationships, and index changes first.
2. Include the exact IDs and files that would be created or changed.
3. Wait for explicit human approval in the conversation.
4. Apply only the approved changes.

If the user asks for a narrow mechanical change, such as fixing a typo or adding
this instruction file, apply it directly.

## Registry Hygiene

Update `entities.index.yaml` whenever an entity is added, its status changes, or
it is superseded. The registry entry must include:

- `id`
- `title`
- `domain`
- `status`
- `path`

Paths in the registry are relative to the repository root. Keep child repository
links under `child_repos`.

## Folder Conventions

- `domains/*/_template.md` and `adr/_template.md` define the expected structure.
- `open-questions/` contains working assessment outputs and is not an entity
  domain unless content is later converted into entities.
- `meeting_transcript/`, `meeting_summary/`, and `sign-off-docs/` are source
  material. Use them for attribution.
- `_pending-review/` is for staged content awaiting human review or approval.
- `prompt-library/` contains reusable workflows. Preserve approval gates in
  prompts that propose model changes.

## Validation Checklist

Before finishing any model-content change:

- Confirm every new or changed ID is unique.
- Confirm every registry path points to an existing file.
- Confirm frontmatter follows the relevant template.
- Confirm relationship targets exist in this repo or in a declared child repo.
- Confirm unresolved facts use `[NEEDS HUMAN INPUT: ...]`.
- Summarize changed files and IDs in the final response.
