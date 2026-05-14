# PROJECT.md — Template

> TEMPLATE: This file lives in the plugin at [plugin]/templates/PROJECT.template.md.
> When filled in, it is written to [project]/ai/PROJECT.md.
> All paths in the Docs Index refer to [project]/ — not to the plugin.
>
> This document is the single source of truth for this project.
> Never modify [project]/ai/PROJECT.md silently — all changes must be confirmed by the human.

---

## 1. Overview

**App name:**
**Tagline:** (one sentence)
**Platform:** (web / iOS / Android / all)
**Status:** (discovery / design / development / live)

**Problem:** (what pain, one or two sentences)
**Who has it:** (user profile, one sentence)
**Why now:** (why existing solutions fall short, one sentence)

---

## 2. Value Proposition

**Core value proposition:**
(What does the user get that they can't get elsewhere, or get better here than anywhere else)

**Key differentiators:**
-
-
-

**What we are NOT:**
(Explicit positioning against competitors or adjacent products)

---

## 3. Design Philosophy

**Tone and personality:**
(e.g. serious but approachable, no dark patterns, honest about limitations)

**Core design principles:**
-
-
-

**What we explicitly avoid:**
(e.g. manipulative mechanics, guilt notifications, aggressive upsells)

---

## 4. Users

**Primary user:**
(who they are, what they need, what they hate about current solutions)

**Secondary user (if any):**

**User journey — happy path:**
1.
2.
3.

---

## 5. Use Cases & User Stories

Format: *As a [user type], I want to [action] so that [outcome].*

### Must have (MVP)
-
-

### Should have (post-MVP)
-
-

### Nice to have (future)
-
-

---

## 6. Functional Map

Overview of all features grouped by module, with plan/tier assignment.

| Module | Feature | Plan | Notes |
|---|---|---|---|
| | | | |

---

## 7. Monetization

**Model:**
(e.g. freemium + monthly subscription + one-time purchases)

**User types:**
| User type | Description |
|---|---|
| | |

**Plans:**
| Plan | Price | Included |
|---|---|---|
| | | |

**One-time purchases (if any):**
| Item | Price | Description |
|---|---|---|
| | | |

**Monetization rules and edge cases:**
(e.g. what happens to user data if subscription is cancelled, export policy, etc.)

**Revenue projections (optional):**

---

## 8. Internationalization

**Languages at launch:**
-

**Languages planned post-launch:**
-

**i18n approach:**
(e.g. i18next with JSON locale files, community translations via open repo)

**Notes:**
(e.g. RTL support needed, date/number format considerations, legal text per region)

---

## 9. Security & Privacy

**Data stored on device:**

**Data stored in the cloud:**

**Authentication approach:**

**Sensitive data handling:**
(e.g. API keys, health data, financial data)

**Regulatory considerations:**
(e.g. GDPR, HIPAA, App Store content policies, PSD2)

**Disclaimers required:**
(e.g. "this app does not replace a doctor / lawyer / accountant")

---

## 10. Visual Identity

**App name:** (confirmed)
**Concept:** (the idea or metaphor behind the name and visual language)

**Icon:**
| Element | Value |
|---|---|
| | |

**Color palette:**

*Brand colors (fixed across themes)*
| Token | Hex | Usage |
|---|---|---|
| | | |

*Light theme*
| Token | Hex | Usage |
|---|---|---|
| | | |

*Dark theme*
| Token | Hex | Usage |
|---|---|---|
| | | |

**Typography:**
| Usage | Font | Weight |
|---|---|---|
| | | |

**Motion & animation concept:**
(describe any animation concept or metaphor that should be felt throughout the app, if applicable)

**Themes:**
(e.g. light/dark/system as baseline, premium themes as upsell)

---

## 11. Tech Stack

| Layer | Decision | Rationale |
|---|---|---|
| | | |

**Constraints:**
| Constraint | Detail |
|---|---|
| | |

**Decisions ruled out:**
| Option | Reason |
|---|---|
| | |

---

## 12. External Providers & Integrations

| Provider | Purpose | Tier / Cost | Risk |
|---|---|---|---|
| | | | |

---

## 13. MVP

### Included in MVP
-

### Excluded from MVP (planned for future)
-

### Out of scope permanently
-

### Launch criteria
(What must be true before this ships — specific and verifiable)
-

### Success metrics
| Metric | Target | Timeframe |
|---|---|---|
| | | |

---

## 14. Open Questions

Decisions not yet made. Each must be resolved — via ADR or direct confirmation — before implementing the section that depends on it.

| # | Question | Blocks | Status |
|---|---|---|---|
| 1 | | | Open |

---

## 15. Docs Index

> All paths below are relative to [project]/ — not to the plugin.

| Document | Path | Status |
|---|---|---|
| Plan | `ai/PLAN.md` | |
| Tasks index | `ai/TASKS.md` | |
| ADR index | `ai/adr/README.md` | |
| Changelog | `CHANGELOG.md` | |