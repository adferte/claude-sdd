---
name: plan
description: Conducts the technical planning session and writes ai/PLAN.md. Use after PROJECT.md is confirmed and before tasks are generated.
disable-model-invocation: true
---

The project root is the current working directory. All project documents live in the `ai/` folder relative to the project root.

## Pre-conditions

Check that `ai/PROJECT.md` exists.
If it does not exist, say: "PROJECT.md not found. Run /claude-sdd:requirements first." Then stop.

Check that `ai/PLAN.md` does not exist.
If it exists, say: "PLAN.md already exists. Edit it directly or delete it to restart planning." Then stop.

---

## Instructions

Read `ai/PROJECT.md` silently.
Read the template at ${CLAUDE_SKILL_DIR}/../../templates/PLAN.template.md.
Use it as the blueprint for this session. Do not show the template to the user.

Say:
"PROJECT.md is confirmed. Let's define the technical plan. We'll go section by section."

Work through every section of the template together, one section at a time.

Rules:
- Ask focused questions for each section. Wait for answers before moving on.
- Never move to the next section until the current one is confirmed.
- If a section does not apply, say so and skip it together.
- When a technical decision has more than one reasonable option and would be costly to reverse, stop and run /claude-sdd:adr before continuing. Reference the ADR in the plan as (→ ADR-NNN).
- Challenge decisions that contradict `ai/PROJECT.md`. Do not reconcile silently.
- If something in PROJECT.md is unclear or insufficient to make a technical decision, flag it and ask the human to update `ai/PROJECT.md` before continuing.

When all sections are complete, show a summary and ask:
"Does this look correct? Shall I write ai/PLAN.md?"

Wait for explicit confirmation. Then write `ai/PLAN.md` using the template structure with all sections populated.

After writing, say:
"PLAN.md written. Run /claude-sdd:tasks to generate the first phase of tasks."