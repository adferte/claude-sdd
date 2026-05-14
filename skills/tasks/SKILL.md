---
name: tasks
description: Generates the next phase of tasks from PROJECT.md and PLAN.md. Use after PLAN.md is confirmed, or when the current phase is complete and the next phase needs to be generated.
disable-model-invocation: true
---

The project root is the current working directory. All project documents live in the `ai/` folder relative to the project root.

## Pre-conditions

Check that `ai/PROJECT.md` exists.
If not, say: "PROJECT.md not found. Run /claude-sdd:requirements first." Then stop.

Check that `ai/PLAN.md` exists.
If not, say: "PLAN.md not found. Run /claude-sdd:plan first." Then stop.

## Instructions

Read `ai/PROJECT.md` and `ai/PLAN.md` silently.
Read the templates at:
- ${CLAUDE_SKILL_DIR}/../../templates/TASKS.template.md
- ${CLAUDE_SKILL_DIR}/../../templates/TASK.template.md

## If ai/TASKS.md does not exist — first phase

Propose a phase list tailored to this specific project based on `ai/PROJECT.md` and `ai/PLAN.md`. Phases must reflect the actual work — do not use a generic preset list. Each phase needs a name and a one-line goal.

Say: "Based on PROJECT.md and PLAN.md, here are the proposed phases for this project: [list]. Does this look correct? Adjust as needed."

Wait for confirmation. Then ask: "Shall I generate the tasks for the first phase?"

Wait for confirmation. Generate tasks for the first phase only.

## If ai/TASKS.md exists — next phase

Read `ai/TASKS.md`. Check the current phase status.

If the current phase is not complete (any task still `pending`, `in progress`, or `blocked`), say:
"Phase [N] is not complete. Resolve all tasks before generating the next phase." Then stop.

If the current phase is complete, say:
"Phase [N] is complete. Before generating Phase [N+1], I need to check if anything has changed."

Ask: "Has anything in PROJECT.md or PLAN.md changed since Phase [N] was generated? Any new constraints, decisions, or scope changes?"

Wait for the answer. If changes are reported, update the relevant documents before continuing.

Re-read `ai/PROJECT.md` and `ai/PLAN.md`. If anything was invalidated by work done in the previous phase, flag it explicitly before proceeding.

Ask: "Shall I generate the tasks for Phase [N+1]?"

Wait for confirmation.

## Generating tasks

For each task in the phase:
- Assign a sequential ID continuing from the last used ID across all phases (T001, T002...)
- Create the task file at `ai/tasks/TXXX.md` using the TASK.template.md structure
- Add a row to the phase table in `ai/TASKS.md`

Tasks must be:
- Atomic — completable in one session without leaving code broken
- Verifiable — acceptance criteria are specific testable statements, not descriptions
- Ordered — dependencies between tasks within the phase must be explicit

After generating all tasks, show a summary and ask:
"Does this look correct? Shall I write these to ai/TASKS.md and ai/tasks/?"

Wait for explicit confirmation before writing any files.

After writing, say:
"Phase [N] tasks written. Run /claude-sdd:implement to start working."