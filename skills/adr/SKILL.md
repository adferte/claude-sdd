---
name: adr
description: Creates a new Architecture Decision Record in ai/adr/. Use when a significant technical decision arises during planning or implementation that has more than one reasonable option and would be costly to reverse.
disable-model-invocation: true
---

The project root is the current working directory. All project documents live in the `ai/` folder relative to the project root.

## Pre-conditions

Check that `ai/PROJECT.md` exists.
If not, say: "PROJECT.md not found. An ADR requires project context." Then stop.

## Instructions

Read the templates at:
- ${CLAUDE_SKILL_DIR}/../../templates/ADR.template.md
- ${CLAUDE_SKILL_DIR}/../../templates/ADR-README.template.md

Determine the next ADR number by counting existing ADR files in `ai/adr/`.
If the directory does not exist or is empty, this is ADR-001.

## ADR creation protocol

**Step 1 — Frame the decision**

State clearly:
- What decision needs to be made
- Why it cannot be deferred
- What constraints apply from `ai/PROJECT.md` or `ai/PLAN.md`

**Step 2 — Present options**

For each option:
- One sentence description
- Concrete pros
- Concrete cons

Maximum three options. If more exist, pick the three most relevant.
State your recommendation and why.

**Step 3 — Wait for decision**

Ask: "Which option do you choose?"

Wait for explicit confirmation. Do not proceed until the human decides.

**Step 4 — Write the ADR**

Write `ai/adr/ADR-NNN-short-title.md` using the ADR.template.md structure with status `accepted`.

If `ai/adr/README.md` does not exist, create it using ADR-README.template.md.
Add the new ADR to the index table in `ai/adr/README.md`.

**Step 5 — Reference the ADR**

State which document needs to reference this ADR: either `ai/PLAN.md` or the current task file `ai/tasks/TXXX.md`.

Say: "Add (→ ADR-NNN) to the relevant section before continuing."

## Superseding an existing ADR

If the decision changes an existing ADR:
- Update the old ADR status to `superseded by ADR-NNN`.
- Create the new ADR normally.
- Update `ai/adr/README.md`.
- Flag all places in `ai/PLAN.md` or task files that referenced the old ADR.