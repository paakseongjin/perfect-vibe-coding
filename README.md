# Perfect Vibe Coding (PVC)

Cursor Agent guidance for **safe, consistent, reusable** web/app building—tuned for vibe coding (including non-expert builders).

**Upgrade model (2026-07):** thin always-on English rules + path `globs` + agent-requested protocols + situational skills. Korean text is **human rationale only** under `docs/pvc-guide/ko/` (not auto-loaded).

---

## Why PVC

| Problem | Without PVC |
|---------|-------------|
| Criteria drift | Inconsistent structure/naming/style |
| Unsafe edits | Data loss, broken APIs |
| Missing ops docs | Nobody knows what code does |
| Design chaos | Per-page one-off styles |
| Skill spam | Duplicate rules, license risk, token burn |

PVC is an **operating system for vibe coding**: always keep a small safety core; load the rest only when the file or task needs it.

---

## Language policy (fixed)

| Asset | Language | Auto-load |
|-------|----------|-----------|
| `.cursor/rules/*.mdc` | **English** | always / globs / agent |
| `.cursor/skills/**` | **English** | on trigger |
| `docs/pvc-guide/ko/**` | **Korean** | **No** (human / ask) |
| `docs/references/**` | EN (+ notes) | No |

Conflict order: **security/data > core + project-context > glob rules > skills > external refs > Korean guides**.

---

## Token budget (operating limits)

| Tier | Target |
|------|--------|
| Always-on files | **2** (`core/00`, `project-context`) |
| Always-on total | **~120–180 lines** |
| Each glob rule | **~20–60 lines** |
| Agent / manual | Longer OK; checklist-first |
| Examples & long forms | In `docs/`, not always-on rules |

Do **not** set most rules to `alwaysApply: true`. Prefer `globs` or agent-requested descriptions.

---

## Rule application tiers

```text
Always (every chat)
  └─ core/00-development-governance.mdc
  └─ project/project-context.mdc

Globs (when matching files are in play)
  └─ architecture/ security/ design/ devops/ runtime/ patterns/ docs/*

Agent requested (model picks by description)
  └─ core/01, 02, 03, 04 · docs/reference-catalog

Manual (high risk / on demand)
  └─ manual/migration · incident-response · full-audit
```

| Task | What loads |
|------|------------|
| Button label tweak | Always only |
| New component | Always + design globs |
| API endpoint | Always + API/data + validation globs |
| New library | Dependency glob + approval |
| DB migration | `manual/migration` |
| “Which skill?” | `.cursor/skills/skill-router` |

---

## Layout

```text
perfect-vibe-coding/
├── README.md
├── RULES_MAP.md
├── docs/
│   ├── pvc/DECISIONS.md
│   ├── pvc-guide/ko/          # Korean rationales (human)
│   ├── templates/
│   └── references/
├── .cursor/rules/             # English executable rules
│   ├── core/ project/ architecture/ security/ …
│   └── manual/
└── .cursor/skills/            # English skills
    ├── skill-router/
    └── external-skill-import/
```

---

## Quick start

1. Copy `.cursor/rules/` and `.cursor/skills/` into your app repo (or clone PVC as a template).
2. Fill **`project/project-context.mdc`** with real product/stack/forbidden/checks (keep it short).
3. Add `CODEMAP.md` (and `DESIGN.md` if UI).
4. In Cursor, start with a small ask; for larger work say: use `skill-router`.
5. Import external skills only via `external-skill-import` + catalog—never wholesale marketplace installs.

---

## Skills & references

- **Router:** `.cursor/skills/skill-router/SKILL.md` — pick rules/skills by task type  
- **Import gate:** `.cursor/skills/external-skill-import/SKILL.md`  
- **Catalog:** [`docs/references/GITHUB_STAR_CATALOG.md`](./docs/references/GITHUB_STAR_CATALOG.md)  
- **Standards:** [`docs/references/SOURCES.md`](./docs/references/SOURCES.md)  
- **Korean guide:** [`docs/pvc-guide/ko/README.md`](./docs/pvc-guide/ko/README.md)

Allowed reference *roles* (principles only): Meng To, VoltAgent DESIGN.md structure, Emil Kowalski, make-interfaces-feel-better, agency-agents viewpoints, KRDS (cite), mattpocock/skills (router patterns), obra/superpowers (plan gates), ECC (context hygiene), etc. See catalog for triggers and reject reasons.

---

## Priority on conflict

1. Security · secrets · data integrity  
2. Safe-work · change control · devops  
3. project-context · runtime · architecture  
4. Design / UI  
5. patterns · task skills  
6. External refs (after governance gate)

---

## License / contributing

Treat this repo as a governance template: keep always-on thin, add globs/skills for detail, put Korean explanations only under `docs/pvc-guide/ko/`, and record decisions in `docs/pvc/DECISIONS.md`.
