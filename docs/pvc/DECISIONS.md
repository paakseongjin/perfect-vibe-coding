# PVC Decisions Log

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
