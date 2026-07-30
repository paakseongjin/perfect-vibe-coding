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

## Workflow

1. Classify the request into one primary bucket:

| Bucket | Load next |
|--------|-----------|
| Tiny UI copy/style | Always rules only |
| UI / components / a11y | `design/*` globs + optional UI skills from catalog |
| API / data / prisma | `architecture/data-integrity`, `security/input-validation` |
| Auth / sessions | `security/auth` + safe-work if risky |
| Forms | `patterns/form-handling` + validation rules |
| Tests | `architecture/testing-quality` |
| CI / deploy | `devops/*` |
| New dependency | `runtime/dependency-policy` + `external-skill-import` if also adding a skill |
| Multi-file feature | `01-safe-work-protocol` + `04-agentic-context-workflow` |
| External skill/research | `03` + `external-skill-import` + catalog |
| Migration / incident / audit | `manual/*` |

2. Announce briefly which rules/skills you will apply (2–5 bullets). Do not load Korean guides unless the user asks for Korean explanation.
3. Proceed with minimal context: always-on core + project-context + selected items only.

## Guardrails

- Never install entire marketplaces (ECC, Superpowers plugins, etc.) without explicit approval.
- Prefer principles from catalog over vendoring repos.
- Conflict order: security/data > core + project-context > glob rules > skills > external refs.

## Acceptance checks

- Correct bucket chosen; no alwaysApply spam; Korean docs not auto-loaded.
