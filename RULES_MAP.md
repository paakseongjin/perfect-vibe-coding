# PVC Rules Map

Language: **executable rules = English**. Korean rationales: `docs/pvc-guide/ko/`.

## Responsibility boundaries (do not duplicate)

| Kind | Responsibility | Do not put here |
|------|----------------|-----------------|
| **Rules** (`.cursor/rules`) | Short must-do commands | Long procedures, fill-in forms |
| **Skills** (`.cursor/skills`) | Step-by-step for one task type | Restating core constitution |
| **Docs** (`docs/pvc-guide/ko`) | Why / examples for humans | Assuming auto-load into every chat |
| **Templates** (`docs/templates`) | Copy-and-fill forms | Policy source of truth |
| **References** (`docs/references`) | Provenance & candidates | “Install this repo wholesale” |
| **Survey** (`docs/pvc/개발방향-설문.md`) | Optional planning draft (downloadable) | Blocking PVC start; replacing `project-context` |

## Recommended planning survey (not mandatory)

| File | Role |
|------|------|
| `docs/pvc/개발방향-설문.md` | Korean development-direction questionnaire — **recommended** for clear briefs; Quick / Standard / High Risk modes |

## Always (`alwaysApply: true`)

| File | Role |
|------|------|
| `core/00-development-governance.mdc` | Safety + minimal change + done criteria |
| `project/project-context.mdc` | Project facts card |

## Agent requested (`alwaysApply: false`, no globs)

| File | Role |
|------|------|
| `core/01-safe-work-protocol.mdc` | Pre/completion reports for risky work |
| `core/02-token-efficiency.mdc` | Context hygiene |
| `core/03-skill-and-reference-governance.mdc` | External import + new-file gate |
| `core/04-agentic-context-workflow.mdc` | R→P→E→R→S |
| `docs/reference-catalog.mdc` | Catalog pointer |

## Globs

| Area | Files |
|------|--------|
| `architecture/` | code-structure, data-integrity, testing-quality |
| `security/` | auth, input-validation, secret-management |
| `design/` | design-system, accessibility, typography-korean |
| `devops/` | git-workflow, ci-cd, observability |
| `runtime/` | platform-targets, dependency-policy, build-output |
| `patterns/` | async-patterns, form-handling, caching-strategy |
| `docs/` | codemap-maintenance, documentation-standard |

## Manual

| File | Role |
|------|------|
| `manual/migration.mdc` | Schema/data migrations |
| `manual/incident-response.mdc` | Incidents |
| `manual/full-audit.mdc` | Full audits |

## Skills (English)

| Skill | Role |
|-------|------|
| `skill-router` | Task → rules/skills/catalog |
| `external-skill-import` | Safe import workflow |

## Removed in upgrade

- `.cursor/rules/en/` — merged into category EN rules (snapshot: `docs/pvc-guide/ko/_archived-en-canonical/`)
- Dual always-on KR+EN bodies — KR moved to `docs/pvc-guide/ko/`
