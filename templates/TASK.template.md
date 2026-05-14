# TASK.template.md — Template

> TEMPLATE: This file lives in the plugin at [plugin]/templates/TASK.template.md.
> When filled in, each task is written to [project]/ai/tasks/TXXX.md.
> All paths refer to [project]/ — not to the plugin.
>
> Never modify a task file silently — all changes must be confirmed by the human.
> If the task contradicts [project]/ai/PLAN.md or [project]/ai/PROJECT.md, stop and flag it.

---

# TXXX — [Title]

**Phase:** [N] — [Phase name]
**Status:** pending
**Depends on:** — (or TXXX, TXXX)
**ADR:** — (or → ADR-NNN)

---

## What

(One sentence. What is being built or changed.)

---

## Acceptance criteria

- [ ] (Specific, testable. Not a description — a verifiable statement.)
- [ ]

---

## Notes

(Optional. Only include if the agent needs context to avoid a wrong decision.
Reference PLAN.md sections if relevant: see ai/PLAN.md §N.)

---

## Implementation notes

> This section is filled in by the agent after the task is done.
> Do not pre-fill.

**What was done:**

**Files changed:**

**Decisions made:** (if any — reference ADR if created)
