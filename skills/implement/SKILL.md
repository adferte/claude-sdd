---
name: implement
description: Executes the next pending task from TASKS.md. Works one task at a time with human verification at each step. Use when ready to start or continue implementation.
disable-model-invocation: true
---

The project root is the current working directory. All project documents live in the `ai/` folder relative to the project root.

## Pre-conditions

Check that `ai/TASKS.md` exists.
If not, say: "TASKS.md not found. Run /claude-sdd:tasks first." Then stop.

## Instructions

Read `ai/TASKS.md`. Find the current active phase — the first phase that is not complete.

Find the next task to work on:
- First, check for any task with status `in progress`. If one exists, resume it.
- Otherwise, take the first `pending` task in the current phase that has all its dependencies met.

If all tasks in the current phase are `done` or `skipped`, say:
"Phase [N] is complete. Run /claude-sdd:tasks to generate the next phase." Then stop.

If a task is `blocked`, report it and ask the human how to proceed. Do not skip it silently.

## Task execution protocol

Read `ai/tasks/TXXX.md` for the selected task.

**Step 1 — Propose**

State clearly:
- What you are about to do (one sentence)
- Which files you will create or modify
- Any assumption you are making

Ask: "Shall I proceed?"

Wait for explicit confirmation. Do not write any code before this confirmation.

**Step 2 — Implement**

Mark the task as `in progress` in `ai/TASKS.md`.

Implement the task. Follow `ai/PLAN.md` strictly.

If during implementation you encounter a decision not covered in `ai/PLAN.md` that has more than one reasonable option and would be costly to reverse — stop immediately. Do not write speculative code. Run /claude-sdd:adr and wait for the decision before continuing.

If anything contradicts `ai/PROJECT.md` or `ai/PLAN.md`, stop and flag it. Do not reconcile silently.

**Step 3 — Verify**

Go through each acceptance criterion in the task file one by one.
State explicitly whether each one passes or fails.
Do not mark the task done if any criterion fails.

**Step 4 — Report**

Summarize:
- What was done
- Files created or modified
- Any decisions made (reference ADR if created)

Fill in the Implementation notes section of `ai/tasks/TXXX.md`.

Ask: "Does this look correct? Shall I mark T[XXX] as done?"

Wait for explicit confirmation. Then update the task status to `done` in `ai/TASKS.md`.

**Step 5 — Next**

Report the next pending task in the current phase, or say that the phase is complete.