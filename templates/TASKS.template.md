# TASKS.md — Template

> TEMPLATE: This file lives in the plugin at [plugin]/templates/TASKS.template.md.
> When filled in, it is written to [project]/ai/TASKS.md.
> Task detail files are written to [project]/ai/tasks/TXXX.md.
> All paths refer to [project]/ — not to the plugin.
>
> Task index derived from [project]/ai/PROJECT.md and [project]/ai/PLAN.md.
> Generated and updated incrementally — one phase at a time.
> Never modify this file silently — all changes must be confirmed by the human.
> If anything contradicts [project]/ai/PROJECT.md or [project]/ai/PLAN.md, stop and flag it.

---

## Status legend

| Status | Meaning |
|---|---|
| `pending` | Not started |
| `in progress` | Currently being worked on. Only one task in progress at a time. |
| `done` | Completed and verified by human |
| `blocked` | Cannot proceed — reason must be stated in task file |
| `skipped` | Deliberately deferred — reason must be stated in task file |

---

## Phases

Phases and their goals are defined during the tasks session based on [project]/ai/PROJECT.md and [project]/ai/PLAN.md. They are project-specific — not predefined.

Phases are sequential. A phase is complete when all its tasks are `done` or `skipped`.

Before generating the next phase, the agent must:
1. Confirm all tasks in the current phase are resolved.
2. Re-read [project]/ai/PROJECT.md and [project]/ai/PLAN.md for anything invalidated by work done so far.
3. Flag any inconsistencies or new unknowns to the human.
4. Wait for explicit confirmation before generating.

Task detail lives in [project]/ai/tasks/TXXX.md — not in this file. This file is the index only.

---

## Phase [N] — [Name]

> Goal: [what this phase achieves]
> Generated: [date]
> Status: pending

| ID | Title | Status | Depends on | ADR |
|---|---|---|---|---|
| T001 | | pending | — | — |

---

<!-- Next phase is generated here once the current phase is complete -->
<!-- Do not plan beyond the next phase until the current one is done -->