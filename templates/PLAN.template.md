# PLAN.md — Template

> TEMPLATE: This file lives in the plugin at [plugin]/templates/PLAN.template.md.
> When filled in, it is written to [project]/ai/PLAN.md.
> All paths in this document refer to [project]/ — not to the plugin.
>
> Technical implementation plan. Derived from [project]/ai/PROJECT.md after spec is confirmed.
> Never modify [project]/ai/PLAN.md silently — all changes must be confirmed by the human.
> When this file contradicts [project]/ai/PROJECT.md, flag it. Do not silently reconcile.
> Significant decisions made here must reference their ADR: (→ ADR-NNN)

---

## 1. Architecture

**Component overview:**
(Brief description of the main components and how they relate. A diagram in ASCII or mermaid is acceptable.)

**Folder structure:**
```
/
```

**Patterns and conventions:**
| Pattern | Where it applies | Notes |
|---|---|---|
| | | |

---

## 2. Data Model

**Entities:**
| Entity | Fields | Notes |
|---|---|---|
| | | |

**Relationships:**
(Describe non-obvious relationships between entities.)

**Schema:**
(SQL, JSON schema, or equivalent. Only include if the structure is not obvious from the entities table.)

---

## 3. Interfaces & Contracts

**Internal module interfaces:**
(How modules talk to each other. Only document non-obvious contracts.)

| Interface | Input | Output | Notes |
|---|---|---|---|
| | | | |

**External service contracts:**
(What the app sends to each external service and what it expects back. Focus on edge cases and error responses.)

| Service | Call | Expected response | Error handling |
|---|---|---|---|
| | | | |

---

## 4. Key Technical Flows

Document flows that are non-obvious or that the agent could implement incorrectly without context.

### [Flow name]
(Step by step. As concise as possible.)

1.
2.
3.

---

## 5. Configuration & Environments

**Environment variables:**
| Variable | Purpose | Required | Example |
|---|---|---|---|
| | | | |

**Environment differences:**
| Setting | Dev | Staging | Prod |
|---|---|---|---|
| | | | |

---

## 6. Testing Strategy

**What gets tested:**
| Layer | Test type | Tool | Notes |
|---|---|---|---|
| | | | |

**What does NOT get tested and why:**
-

**Conventions:**
(naming, file location, what a test must assert to be considered valid)

---

## 7. Security Implementation

**Validation:**
(Where input is validated, by whom, what rules apply.)

**Encryption:**
(What is encrypted, with what, where keys are stored.)

**Session & auth:**
(How sessions are created, stored, invalidated.)

**What never reaches the client:**
-

---

## 8. Error Handling & Logging

**Error handling by layer:**
| Layer | Strategy | User sees | Logged |
|---|---|---|---|
| | | | |

**Log levels and when to use them:**
| Level | When |
|---|---|
| error | |
| warn | |
| info | |
| debug | |

**What is never logged:**
(e.g. passwords, tokens, PII)
-

---

## 9. Known Technical Debt

Shortcuts taken consciously for the MVP. Each item must have a reason and a note on when it should be addressed.

| Item | Reason accepted | Address when |
|---|---|---|
| | | |

---

## 10. Open Technical Questions

Questions that block implementation of a specific section. Each must be resolved via ADR or direct decision before work on that section begins. Once resolved, reference the ADR: (→ ADR-NNN).

| # | Question | Blocks | Status | ADR |
|---|---|---|---|---|
| 1 | | | Open | — |

---

## 11. Docs Index

> All paths below are relative to [project]/ — not to the plugin.

| Document | Path | Status |
|---|---|---|
| Spec | `ai/PROJECT.md` | |
| Tasks index | `ai/TASKS.md` | |
| ADR index | `ai/adr/README.md` | |