# Prompt 03 — Current-State Assessment & Next-Meeting Question Prep

**Use when:** you have one or more populated `current-state` domain md files
(and/or the evidence entries behind them) and want to prepare for an
upcoming client meeting — specifically, to surface what's genuinely
understood vs. assumed, and turn the gaps into a sharp question list focused
on system criticality and risk, not just "more detail."

**Required context to attach:** the full content of the relevant
`domains/current-state/*.md` files (and any linked `evidence` entries worth
including — pass them if you have them, this prompt still works without
them).

---

## Prompt

```
You are preparing current-state assessment notes and a next-meeting
question list, based on existing current-state domain knowledge model files.

CONTEXT PROVIDED:
- CURRENT-STATE FILES: <<paste the full content of the relevant
  domains/current-state/*.md files>>
- LINKED EVIDENCE (optional): <<paste any related evidence entries, or
  transcripts/summaries these current-state files were derived from, if
  available>>

YOUR TASK:
Extract the content into exactly these categories. Do not add categories,
rename them, or merge them.

1. STATED PAINS — problems the client explicitly named as problems. For each,
   include a short verbatim quote (under 20 words) and the speaker/source it
   came from, if the source material makes that available. If no verbatim
   quote is available (e.g. you're working from a current-state md file
   rather than a transcript), use the closest available paraphrase and say so
   rather than fabricating a quote.

2. IMPLIED PAINS — problems that are evident from context but were not
   explicitly named as problems by anyone. Mark every item in this category
   clearly with `[INFERRED]` and give your reasoning in one sentence — what
   in the source material led you to infer this. Do not present an inferred
   pain as if it were stated.

3. CURRENT-STATE FACTS — neutral factual inventory: systems, tools,
   processes, data volumes, team structures, ownership. No evaluation, no
   pain framing — just what exists.

4. STAKEHOLDER DYNAMICS — who owns what, and any visible alignment or
   friction signals between people/teams (e.g. two teams defining the same
   metric differently, a single person being the point of contact for
   multiple critical items). Use neutral, observational wording only. Do not
   speculate about anyone's motives, competence, or intent — describe the
   situation, not the person.

5. OPEN QUESTIONS — what is still unknown that matters, and who is likely
   able to answer it, based on the stakeholder dynamics identified above.


CONSTRAINTS (non-negotiable):
- Every item must trace back to something actually present in the provided
  material. If you're inferring, say so via [INFERRED] — never blend
  inference into a stated fact or pain without marking it.
- Do not propose or draft any change to the current-state md files
  themselves. This is an assessment and question-prep exercise only — it
  does not create, edit, or move any file in /domains, /adr, or
  entities.index.yaml.
- Keep Category 5 strictly neutral — flag friction or misalignment as an
  observable pattern ("Team A and Team B independently maintain the same
  metric definition"), never as a judgment about why it happened.

FINAL DELIVERABLE — Question List for Next Meeting.
After completing the five categories above, produce a prioritized list of
questions to ask at the next client meeting. The list's purpose is to move
the team from "we know what exists" to "we understand how critical each
piece is and what breaks if it fails" — so weight the questions accordingly:

- Prioritize questions that probe **business criticality and blast radius**:
  what depends on this system, who is affected if it fails or is delayed,
  what the actual cost of an outage/delay has been historically.
- Prioritize questions that resolve items from OPEN QUESTIONS (category 7)
  and IMPLIED PAINS (category 2) over ones that just add more
  CURRENT-STATE FACTS detail — facts without criticality context don't move
  the assessment forward as much.
- Direct each question to the stakeholder(s) most likely to answer it, based
  on STAKEHOLDER DYNAMICS (category 5).
- Where a STATED PAIN lacks enough detail to size its actual business
  impact, write a follow-up question that would get you that sizing (e.g.
  frequency, cost, who is blocked, how it's currently worked around).
- Avoid generic discovery questions ("tell us more about your architecture")
  — every question should be answerable in one sitting and should move a
  specific open item forward.

OUTCOME FILE — OPEN QUESTIONS.
After completing the assessment and prioritized question list, create the
`open-questions/` folder at the repository root if it does not already exist.
Write the outcome to a Markdown file using this filename pattern:

`open-questions/<YYYY-MM-DD>-<system-or-engagement-slug>-open-questions.md`

Use the meeting or assessment date when it is available. If the date or
system/engagement name cannot be determined, use
`unknown-date-unknown-engagement-open-questions.md` and retain specific
`[NEEDS HUMAN INPUT: ...]` markers in the file content. Keep the slug
lowercase, replace spaces and punctuation with `-`, and remove repeated
hyphens.

The file must contain:
- The assessment title, date, source files, and system/engagement name.
- All items from `OPEN QUESTIONS`, including the likely answerable
  stakeholder, the relevant domain, and the source or evidence.
- The prioritized `Question List for Next Meeting`, with each question tied to
  the open question or pain it addresses and the criticality or blast-radius
  insight it should unlock.
- Any `[INFERRED]`, `[NEEDS HUMAN INPUT: ...]`, or
  `[CONFLICT NEEDS HUMAN RESOLUTION]` markers from the assessment.
- `No open questions identified.` if the assessment finds none; still create
  the file so the outcome is explicit.

Do not write, edit, move, or delete the source files in `domains/`, `adr/`, or
`entities.index.yaml`. If you cannot create the folder or file, include the
complete proposed file content in the response and state exactly where it
must be saved; do not claim that it was created.

OUTPUT FORMAT:

# Current-State Assessment — <system/engagement name>

## 1. Stated Pains
- "<verbatim or closest available quote>" — *<speaker/source>*

## 2. Implied Pains
- [INFERRED] <pain> — *Reasoning: <one sentence>*

## 3. Current-State Facts
- <fact>

## 4. Stakeholder Dynamics
- <observation, neutral wording>

## 5. Open Questions
- <question> — *Likely answerable by: <role/person>*

## Question List for Next Meeting
*(prioritized, each tied to a criticality or open-item goal)*

1. **<question>** — *Ask: <stakeholder>* — *Why: <ties to which pain/open
   question, and what criticality/blast-radius insight it unlocks>*
2. ...

**Outcome file:** `open-questions/<YYYY-MM-DD>-<system-or-engagement-slug>-open-questions.md`
```
