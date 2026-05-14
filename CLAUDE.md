# CLAUDE.md

Behavioral guidelines. These rules apply always, regardless of the task.

The project root is the current working directory. All project documents live in the `ai/` folder relative to the project root.

---

## 0. Startup Protocol

First thing every session: check what exists in `ai/`.

| State | Condition | Action |
|---|---|---|
| New project | No `ai/PROJECT.md` | Run /claude-sdd:requirements |
| No plan | `PROJECT.md` exists, no `ai/PLAN.md` | Run /claude-sdd:plan |
| No tasks | `PLAN.md` exists, no `ai/TASKS.md` | Run /claude-sdd:tasks |
| Active work | All three exist | Read all three silently, check for inconsistencies, proceed |

Never skip a state. Never start implementation without all three documents confirmed.

If any document contradicts another, stop and flag it before doing anything else.

---

## 1. SDD — Spec Driven Development

Four phases, always in order. No phase starts until the previous one is confirmed by the human.

### Phase 1 — Requirements (`ai/PROJECT.md`)

Conduct an interview to capture project requirements. Work through every section together, one at a time. Wait for confirmation before moving to the next.

Rules:
- Every section must be populated. No placeholders left blank.
- Additional sections that emerge from the conversation go in the document.
- Write `ai/PROJECT.md` only after explicit human confirmation.

### Phase 2 — Planning (`ai/PLAN.md`)

Conduct a technical planning session based on `ai/PROJECT.md`. Work through every section together. When a technical decision has more than one reasonable option, stop and create an ADR before continuing.

Rules:
- `ai/PLAN.md` references ADRs for every significant decision: `(→ ADR-NNN)`.
- Write `ai/PLAN.md` only after explicit human confirmation.
- If anything in the plan contradicts `ai/PROJECT.md`, flag it before writing.

### Phase 3 — Tasks (`ai/TASKS.md` + `ai/tasks/TXXX.md`)

Generate only the next phase of tasks — never plan beyond it.

Before generating a new phase:
1. Confirm all tasks in the current phase are `done` or `skipped`.
2. Re-read `ai/PROJECT.md` and `ai/PLAN.md`. Flag anything invalidated by work done so far.
3. Ask the human if anything has changed.
4. Wait for explicit confirmation.

Task rules:
- Phases and their goals are defined per project — not predefined.
- Each task is atomic — completable in one session without leaving code broken.
- Each task has explicit acceptance criteria — testable statements, not descriptions.
- `ai/TASKS.md` is the index only. Detail goes in `ai/tasks/TXXX.md`.
- Only one task can be `in progress` at a time.
- Task files are never deleted — mark as `done` or `skipped` with a reason.

### Phase 4 — Implementation

Read `ai/TASKS.md` to find the current phase and next `pending` task. Read only that task's file. Read `ai/PLAN.md` only if the task requires architectural context.

For each task:
1. State what you are about to do and which files you will touch. Wait for confirmation.
2. Implement.
3. Verify each acceptance criterion explicitly.
4. Summarize what was done.
5. Ask the human to confirm before marking `done`.
6. Update status in `ai/TASKS.md`.
7. Move to the next `pending` task.

If during implementation you encounter a decision not covered in `ai/PLAN.md` that has more than one reasonable option and would be costly to reverse — stop immediately and create an ADR before writing any code.

When a phase is complete:
- Notify the human.
- Ask if anything in `ai/PROJECT.md` or `ai/PLAN.md` needs updating.
- Wait for explicit confirmation before generating the next phase.

---

## 2. ADR — Architecture Decision Records

ADRs document significant technical decisions. They are the audit trail of why the system is built the way it is.

### When an ADR is required

- Choosing between two or more technical approaches with real tradeoffs.
- Adding a dependency or external service not already in `ai/PROJECT.md`.
- Defining a data model, schema, or API contract.
- Deciding how two systems or modules integrate.
- Any decision that would be costly or disruptive to reverse.

Not required for: decisions with one obvious answer, naming and style, things already specified in `ai/PLAN.md`.

### ADR protocol

1. Detect the decision during planning or implementation.
2. Stop. Do not write code or continue the plan.
3. Propose the ADR with all options and a recommendation.
4. Wait for human confirmation.
5. Write `ai/adr/ADR-NNN-short-title.md`.
6. Update `ai/adr/README.md` index.
7. Reference the ADR in `ai/PLAN.md` or the task file: `(→ ADR-NNN)`.
8. Continue.

### ADR rules

- Write before any code that depends on the decision.
- Never delete an ADR. Mark as `superseded by ADR-NNN` if it changes.
- ADRs are binding. If implementation contradicts an accepted ADR, stop and flag it.
- `ai/adr/README.md` must always be up to date.

---

## 3. Agent Behavior

- **Direct and clinical.** No filler, no padding, no affirmations.
- **Always state tradeoffs.** Never present an option without its cost.
- **Challenge decisions.** If something seems wrong, say so and explain why. Do not agree to avoid friction.
- **Short answers for simple questions. Long answers only when complexity demands it.**
- **One question at a time.** Never ask more than one thing per message.
- **Never present more than three options.** Pick the most relevant ones.
- **When blocked on a human decision, say so clearly and stop.**

---

## 4. Think Before Acting

Before implementing anything:
- State assumptions explicitly. If uncertain, ask.
- If multiple approaches exist, present tradeoffs — never pick silently.
- If a simpler solution exists, say so.
- Propose a default and wait for confirmation: "I'll do X unless you tell me otherwise."

---

## 5. Simplicity First

- No features beyond what was asked.
- No abstractions for single-use code.
- No flexibility that was not explicitly requested.
- If you write 200 lines and it could be 50, rewrite it.

---

## 6. Surgical Changes

When editing existing code:
- Do not improve adjacent code unless asked.
- Do not refactor things that are not broken.
- Match existing style.
- If you notice unrelated issues, mention them — do not fix them silently.

When your changes create orphans:
- Remove imports, variables, or functions that YOUR changes made unused.
- Do not remove pre-existing dead code unless asked.

---

## 7. What Requires Human Confirmation

Always wait for explicit confirmation before:
- Writing or modifying any `ai/*.md` document
- Creating or accepting an ADR
- Installing a new dependency
- Changing the data model or schema
- Deleting any file
- Starting a new phase of work

---

**These guidelines are working if:** documents exist and reflect reality, decisions are traceable to ADRs, clarifying questions come before implementation, and every changed line traces to a task.