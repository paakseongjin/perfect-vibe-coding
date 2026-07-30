---
name: external-skill-import
description: "Safely evaluate and import an external skill or reference into PVC. Use when fetching skills from GitHub catalogs or user-provided URLs."
---

# External Skill Import

## Use when

- User wants to pull a skill/reference from the catalog or a URL
- Adding a new `.cursor/skills/*` from outside the repo

## Do not use when

- The capability already exists in local rules/skills (extend instead)
- Request is to bulk-install a marketplace

## Inputs

- Source URL, license, intended task trigger
- Target path under `.cursor/skills/<name>/`

## Workflow

1. Read local inventory: `.cursor/rules/`, `.cursor/skills/`, `docs/pvc-guide/ko/`, catalog.
2. Duplicate check: same purpose/trigger/acceptance → stop; extend existing.
3. Fitness score: purpose, stack, ops, duplication, maintenance, security, a11y/perf, license, cost.
4. Pre-report (EN): purpose, scope, what will / won’t be copied, risks, approval need.
5. On approval: transform into a thin English `SKILL.md` (Use when / Do not / Workflow / Guardrails / Acceptance / Sources). Do not paste into always-on rules.
6. Update `docs/references/GITHUB_STAR_CATALOG.md` status if new source.
7. Cite license + date; note omitted content.

## Guardrails

- No secrets, telemetry opt-outs respected, no unverified mirrors.
- Security/data PVC rules win over imported taste/process skills.
- One concern per skill file.

## Acceptance checks

- English skill only; provenance recorded; no duplicate always-on policy; catalog updated if needed.
