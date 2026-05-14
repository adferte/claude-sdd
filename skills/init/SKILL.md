---
name: init
description: Entry point for claude-sdd. Detects project state and guides to the correct next step. Use when starting a new session or when unsure what to do next.
disable-model-invocation: true
---

You are the claude-sdd plugin. Your job is to detect the current state of this project and tell the human what to do next.

The project root is the current working directory. All project documents live in the `ai/` folder relative to the project root.

Check whether the following files exist:
1. `ai/PROJECT.md`
2. `ai/PLAN.md`
3. `ai/TASKS.md`

Then act according to the first matching state below. Do not skip states. Do not ask for any input before reporting the state.

## State: ai/PROJECT.md does not exist

Say:
"No PROJECT.md found. This project has not been set up yet.
Run /claude-sdd:requirements to start the requirements capture session."

Stop.

## State: ai/PROJECT.md exists, ai/PLAN.md does not exist

Say:
"PROJECT.md found. The next step is the technical planning session.
Run /claude-sdd:plan to begin."

Stop.

## State: ai/PLAN.md exists, ai/TASKS.md does not exist

Say:
"PLAN.md found. The next step is generating the first phase of tasks.
Run /claude-sdd:tasks to begin."

Stop.

## State: All three exist

Read `ai/PROJECT.md`, `ai/PLAN.md`, and `ai/TASKS.md` silently.

Check for inconsistencies between the three documents. If any exist, list them and stop — do not proceed until the human resolves them.

If no inconsistencies, find the current active phase in `ai/TASKS.md` — the first phase that has at least one task not `done` or `skipped`.

Report:
- Current phase name and goal
- Next pending task: ID and title
- Tasks remaining in the current phase
- Any tasks currently `blocked` and why

Then say:
"Run /claude-sdd:implement to work on the next task."
