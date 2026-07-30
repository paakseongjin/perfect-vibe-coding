# PVC Decisions Log

## 2026-07-30 — README full Korean textbook guide

### Decision

- Expanded root `README.md` into a non-expert textbook / product manual / complete guide (TOC, install, survey, prompts, risk, glossary, roadmaps, FAQ).

### Why

- User requested a detailed, easy-to-read guide for non-developers beyond the short onboarding README.

---

## 2026-07-30 — Foundation polish (LICENSE, install tiers, risk, smoke)

### Decision

- Added MIT `LICENSE`.
- README: clarify PVC as copyable Cursor template; **min / recommended / full** install table; empty-project CODEMAP prompt; Quick survey emphasis.
- `core/00`: canonical Low / Medium / High / Critical risk table (README summarizes only).
- `CHECKLISTS.md`: seven smoke scenarios with expected Agent behavior.

### Why

- Close real onboarding gaps for non-expert vibe coding without growing the rule surface.

---

## 2026-07-30 — Survey recommended (not mandatory) + UX polish

### Decision

- `docs/pvc/개발방향-설문.md` remains a **standalone, downloadable planning tool** (권장). Not a hard gate to start PVC.
- Added Quick / Standard / High Risk guidance inside the survey; Quick = 4 questions.
- README reordered: **10-minute start first**; Rules/Skills/refs under “더 알아보기”.
- `RULES_MAP.md` fixed Rules / Skills / Docs / Templates / References / Survey responsibilities.
- `core/03` gained a 5-question **new file gate** (default: reject new always-on files).
- Added `docs/pvc/CHECKLISTS.md` for install smoke + post-use retrospective.
- Softened `core/00`, `project-context`, `skill-router`: recommend survey when vague; never block solely on empty survey.

### Why

- External review: mandatory full survey raises entry friction for prototypes; README cognitive load; duplication risk as PVC grows.
- User intent: keep the detailed survey for clearer briefs and agent accuracy, but as optional/recommended.

---

## 2026-07-30 — Mandatory Korean development-direction survey

### Superseded

Earlier “mandatory before PVC” wording is **superseded** by the decision above (recommended, not required).

### Original note

- Had added `개발방향-설문.md` and wired README/core as required pre-step for non-expert direction-setting.

---

## 2026-07-30 — Korean README textbook + curated UI sources

### Decision

- Main `README.md` is **Korean-only**, written as an install + vibe-coding textbook for non-experts.
- Curated UI/design sources (MengTo, VoltAgent, emilkowalski, make-interfaces-feel-better, agency-agents, KRDS, ui-skills.com) are first-class in `GITHUB_STAR_CATALOG`, `skill-router`, and thin `core/03`, with explicit **no wholesale install / principles-only** policy.
- Deep Korean role text remains in `docs/pvc-guide/ko/core/03-skill-and-reference-governance.md` §4.

### Why

- After the tier upgrade, the human-facing list disappeared from the short English README; users still need those premium references and a readable Korean guide.

---

## 2026-07-30 — Context-cost upgrade (tiers + EN-only executable + KR guide)

### Decision

- Always-on rules limited to **2 English files**: `core/00`, `project-context`.
- All executable `.mdc` and `SKILL.md` content is **English**.
- Korean long-form moved to **`docs/pvc-guide/ko/`** (not auto-loaded).
- Domain rules use **`globs`**; heavy protocols are **agent-requested**; high-risk flows under **`manual/`**.
- Folder names (`core/`, `security/`, …) **kept** (no flat `00`–`40` rename).
- Added skills: `skill-router`, `external-skill-import`.
- Removed duplicate `.cursor/rules/en/` after absorbing into category files.

### Why

- Previous layout had **35/35 `alwaysApply: true`**, dual KR+EN load, and ~550-line `03` always-on → high token cost and weak fit for vibe coding.
- Non-expert builders need thin defaults + situational skills, without policy collisions/duplication.

### Non-goals

- No wholesale install of ECC / Superpowers / skill marketplaces.
- No caveman-style default speech.
- CI/lint automation remains a *recommendation* for consumer apps, not shipped as PVC runtime.

### Rollback

- Restore pre-upgrade rules from git history; Korean archives remain under `docs/pvc-guide/ko/` even after rollback of EN thins.
