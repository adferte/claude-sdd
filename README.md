# claude-sdd

Spec Driven Development plugin for Claude Code. Guides projects through requirements capture, technical planning, task generation, and implementation — one step at a time, with human supervision at every stage.

---

## What it does

- Captures project requirements and writes `ai/PROJECT.md`
- Conducts technical planning sessions and writes `ai/PLAN.md`
- Generates implementation tasks phase by phase into `ai/TASKS.md` and `ai/tasks/`
- Executes tasks one at a time with explicit verification before marking done
- Creates Architecture Decision Records in `ai/adr/` whenever a significant technical decision arises

---

## Installation

```bash
/plugin install https://github.com/adferte/claude-sdd
```

---

## Project setup

Add a minimal `CLAUDE.md` to your project root:

```markdown
# CLAUDE.md

## Required plugin

This project requires the claude-sdd plugin.

If not installed:
/plugin install https://github.com/adferte/claude-sdd

Once installed:
/claude-sdd:init
```

---

## Usage

Every session starts with:

```
/claude-sdd:init
```

This detects the current state of the project and tells you what to do next.

### Skills

| Skill | When to use |
|---|---|
| `/claude-sdd:init` | Start of every session. Detects state and guides next step. |
| `/claude-sdd:requirements` | No `ai/PROJECT.md` yet. Starts requirements interview. |
| `/claude-sdd:plan` | `PROJECT.md` confirmed. Starts technical planning session. |
| `/claude-sdd:tasks` | `PLAN.md` confirmed, or current phase complete. Generates next phase of tasks. |
| `/claude-sdd:implement` | Tasks exist. Executes next pending task with verification. |
| `/claude-sdd:adr` | Significant technical decision needs to be documented. |

---

## Project structure

After running the full flow, your project will have:

```
your-project/
  CLAUDE.md
  ai/
    PROJECT.md        ← requirements spec
    PLAN.md           ← technical plan
    TASKS.md          ← task index
    tasks/
      T001.md
      T002.md
      ...
    adr/
      README.md       ← ADR index
      ADR-001-*.md
      ...
```

---

## Development

To test the plugin locally:

```bash
claude --plugin-dir ./claude-sdd
```

To reload after changes:

```
/reload-plugins
```