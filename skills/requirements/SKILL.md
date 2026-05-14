---
name: requirements
description: Conducts the requirements capture interview and writes ai/PROJECT.md. Use when starting a new project or when PROJECT.md does not exist.
disable-model-invocation: true
---

The project root is the current working directory. All project documents live in the `ai/` folder relative to the project root.

## Pre-conditions

Check that `ai/PROJECT.md` does not exist.
If it exists, say: "PROJECT.md already exists. Edit it directly or delete it to restart requirements capture." Then stop.

---

## Instructions

Read the template at ${CLAUDE_SKILL_DIR}/../../templates/PROJECT.template.md.
Use it as the blueprint for this session. Do not show the template to the user.

Say:
"Let's define your project. Describe your idea in 5–10 lines — plain language, no technical detail needed."

Wait for the response. Then work through every section of the template together, one section at a time.

Rules:
- Ask focused questions for each section. Wait for answers before moving on.
- Never move to the next section until the current one is confirmed.
- If a section does not apply, say so and skip it together.
- If additional sections emerge from the conversation, include them.
- Keep answers concise — no placeholders, no vague descriptions.
- Challenge answers that are unclear or contradictory. Do not accept them to avoid friction.

When all sections are complete, show a summary of the full document and ask:
"Does this look correct? Shall I write ai/PROJECT.md?"

Wait for explicit confirmation. Then write `ai/PROJECT.md` using the template structure with all sections populated.

After writing, say:
"PROJECT.md written. Run /claude-sdd:plan to start the technical planning session."