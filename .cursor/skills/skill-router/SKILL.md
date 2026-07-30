---
name: skill-router
description: "Route vibe-coding tasks to the right PVC rules, skills, and catalog references. Use at the start of non-trivial work or when the user asks what skill/rule to use."
---

# Skill Router

## Use when

- Starting a feature, UI polish, API/auth work, dependency change, research, or external skill import
- User asks “which skill/rule should we use?”
- Ambiguous request that might over-load context

## Do not use when

- Trivial single-line copy change already covered by always-on core + project-context
- Survey `docs/pvc/개발방향-설문.md` is missing on a new product — stop and complete the survey first (see core/00)

## Workflow

0. New product / first PVC setup: verify `docs/pvc/개발방향-설문.md` has required sections filled. If not, help complete it; do not implement yet.
1. Classify the request into one primary bucket:

| Bucket | Load next |
|--------|-----------|
| Tiny UI copy/style | Always rules only |
| UI / components / a11y | `design/*` globs; catalog UI sources below if needed |
| Landing / marketing page | MengTo skill **shape** principles via catalog + `external-skill-import` |
| DESIGN.md / design system doc | VoltAgent DESIGN.md **structure** only |
| Motion / interaction polish | emilkowalski principles (checklist, not wholesale) |
| Micro UI polish on existing screens | make-interfaces-feel-better principles |
| Multi-role review (UX/QA/brand) | agency-agents **viewpoints** only |
| Public/gov-like a11y & forms | KRDS patterns + mandatory cite |
| Discover more UI skills | ui-skills.com → then `03` gate before import |
| API / data / prisma | `architecture/data-integrity`, `security/input-validation` |
| Auth / sessions | `security/auth` + safe-work if risky |
| Forms | `patterns/form-handling` + validation rules |
| Tests | `architecture/testing-quality` |
| CI / deploy | `devops/*` |
| New dependency | `runtime/dependency-policy` + `external-skill-import` if also adding a skill |
| Multi-file feature | `01-safe-work-protocol` + `04-agentic-context-workflow` |
| External skill/research | `03` + `external-skill-import` + catalog |
| Migration / incident / audit | `manual/*` |

2. Announce briefly which rules/skills/catalog sources you will apply (2–5 bullets). Do not load Korean guides unless the user asks for Korean explanation.
3. Proceed with minimal context: always-on core + project-context + selected items only.

## Curated UI/design references (principles only)

Full table: `docs/references/GITHUB_STAR_CATALOG.md` → “Curated design/UI skill sources”.  
Korean deep guide: `docs/pvc-guide/ko/core/03-skill-and-reference-governance.md` §4.

**Never** install these repos wholesale. Convert only applicable principles into English skills/rules after `external-skill-import`.

## Guardrails

- Never install entire marketplaces (ECC, Superpowers plugins, MengTo full tree, agency persona packs, etc.) without explicit approval.
- Prefer principles from catalog over vendoring repos.
- Conflict order: security/data > core + project-context > glob rules > skills > external refs.

## Acceptance checks

- Correct bucket chosen; no alwaysApply spam; Korean docs not auto-loaded; external UI sources used as principles only.
