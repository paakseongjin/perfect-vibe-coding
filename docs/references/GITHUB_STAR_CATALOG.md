# GitHub High-Star Reference Catalog
# 고스타 GitHub 참고 카탈로그

> Stars checked via GitHub API on **2026-07-30**. Counts drift over time.  
> **Do not vendor-copy** entire repos. Use `core/03-skill-and-reference-governance` + this catalog: local project first → pick one principle → convert → cite.  
> 전체 복사 금지. 로컬 우선 → 원칙만 선별 변환 → 출처 기록.

PVC already encodes OWASP/NIST/RFC/Web Vitals. This file lists **additional community-proven** repos by category.

---

## How to use / 사용법

| Decision | Action |
|----------|--------|
| Need a style/lint baseline | airbnb/javascript + typescript-eslint + prettier (principles, not blind paste) |
| Need Node/API ops habits | goldbergyoni/nodebestpractices |
| Need clean naming/functions | clean-code-javascript / clean-code-typescript |
| Need security builders’ notes | OWASP/CheatSheetSeries (canonical; already in PVC security rules) |
| Need UI kit inspiration | shadcn/ui, Tailwind — match `project-context` design system first |
| Need agent skill procedures | MengTo/Skills, emilkowalski/skills — via `03` gate only |

**Status labels:** `Adopt principles` · `Optional proposal` · `Explore only` · `Already in PVC`

---

## Architecture & Clean Code

| Repo | Stars | License | PVC fit | Note |
|------|------:|---------|---------|------|
| [donnemartin/system-design-primer](https://github.com/donnemartin/system-design-primer) | ~360k | various | Explore only | Large-system design study; not a drop-in web template |
| [ryanmcdermott/clean-code-javascript](https://github.com/ryanmcdermott/clean-code-javascript) | ~95k | MIT | Adopt principles | Naming, functions, SOLID-ish JS habits → `architecture/`, `patterns/` |
| [labs42io/clean-code-typescript](https://github.com/labs42io/clean-code-typescript) | ~9.8k | MIT | Adopt principles | TS adaptation of Clean Code → TypeScript projects |
| [feature-sliced/documentation](https://github.com/feature-sliced/documentation) | ~2.3k | MIT | Optional proposal | FSD layering; only if `project-context` adopts FSD |
| [goldbergyoni/nodebestpractices](https://github.com/goldbergyoni/nodebestpractices) | ~105k | CC-BY-SA-4.0 | Adopt principles | Node structure, errors, Express/Nest habits → `runtime/`, `architecture/` |

## Language, Lint, Format

| Repo | Stars | License | PVC fit | Note |
|------|------:|---------|---------|------|
| [airbnb/javascript](https://github.com/airbnb/javascript) | ~148k | MIT | Adopt principles | Style guide; prefer ESLint shareable config over manual copy |
| [eslint/eslint](https://github.com/eslint/eslint) | ~27k | MIT | Adopt principles | Static analysis standard |
| [typescript-eslint/typescript-eslint](https://github.com/typescript-eslint/typescript-eslint) | ~16k | MIT | Adopt principles | TS-aware lint rules |
| [prettier/prettier](https://github.com/prettier/prettier) | ~52k | MIT | Adopt principles | Deterministic formatting; disable conflicting ESLint style rules |
| [microsoft/TypeScript](https://github.com/microsoft/TypeScript) | ~110k | Apache-2.0 | Already foundational | Language source of truth |
| [facebook/react](https://github.com/facebook/react) | ~247k | MIT | Stack-dependent | Follow official docs when React is in `project-context` |

## Web Frameworks & Data (stack-dependent)

| Repo | Stars | License | PVC fit | Note |
|------|------:|---------|---------|------|
| [vercel/next.js](https://github.com/vercel/next.js) | ~141k | MIT | Stack-dependent | Default example in `project-context`; not mandatory for all PVC projects |
| [remix-run/remix](https://github.com/remix-run/remix) | ~33k | MIT | Explore only | Alternative web framework |
| [withastro/astro](https://github.com/withastro/astro) | ~61k | MIT | Explore only | Content-heavy sites |
| [TanStack/query](https://github.com/TanStack/query) | ~50k | MIT | Optional proposal | Client server-state; align with §10 AI patterns |
| [trpc/trpc](https://github.com/trpc/trpc) | ~40k | MIT | Optional proposal | End-to-end typesafe APIs when chosen in context |
| [colinhacks/zod](https://github.com/colinhacks/zod) | ~43k | MIT | Optional proposal | Schema validation at boundaries (`security/input-validation`) |
| [prisma/prisma](https://github.com/prisma/prisma) | ~47k | Apache-2.0 | Stack-dependent | Default example ORM |
| [axios/axios](https://github.com/axios/axios) | ~109k | MIT | Optional proposal | HTTP client; prefer fetch if project standard says so |

## UI & Design Systems

| Repo | Stars | License | PVC fit | Note |
|------|------:|---------|---------|------|
| [tailwindlabs/tailwindcss](https://github.com/tailwindlabs/tailwindcss) | ~96k | MIT | Stack-dependent | Default example styling |
| [shadcn-ui/ui](https://github.com/shadcn-ui/ui) | ~120k | MIT | Optional proposal | Copy components into repo; still obey `design/` tokens |
| [VoltAgent/awesome-design-md](https://github.com/VoltAgent/awesome-design-md) | ~105k | MIT | Already in `03` | DESIGN.md structure reference only — do not clone brand identity |
| [KRDS-uiux/krds-uiux](https://github.com/KRDS-uiux/krds-uiux) | ~0.3k | check LICENSE | Already in `03` | KR public UX/a11y patterns; cite when used |
| [MengTo/Skills](https://github.com/MengTo/Skills) | ~3.9k | MIT | Already in `03` | Procedural agent skills — selective |
| [emilkowalski/skills](https://github.com/emilkowalski/skills) | ~23k | MIT | Already in `03` | Motion/UI polish skills — selective |

## Security & Supply Chain

| Repo | Stars | License | PVC fit | Note |
|------|------:|---------|---------|------|
| [OWASP/CheatSheetSeries](https://github.com/OWASP/CheatSheetSeries) | ~33k | CC-BY-SA-4.0 | Already in PVC | Canonical builder security notes |
| [gitleaks/gitleaks](https://github.com/gitleaks/gitleaks) | ~28k | MIT | Adopt principles | Secret scanning in CI (`secret-management`) |
| [aquasecurity/trivy](https://github.com/aquasecurity/trivy) | ~37k | Apache-2.0 | Optional proposal | Vuln/misconfig/SBOM scanning |

## Performance & Ops

| Repo | Stars | License | PVC fit | Note |
|------|------:|---------|---------|------|
| [GoogleChrome/web-vitals](https://github.com/GoogleChrome/web-vitals) | ~8.6k | Apache-2.0 | Already in PVC | Library matching web.dev thresholds |
| [conventional-changelog/conventional-changelog](https://github.com/conventional-changelog/conventional-changelog) | ~8.5k | ISC | Adopt principles | Changelog from Conventional Commits |
| [github/gitignore](https://github.com/github/gitignore) | ~175k | CC0-1.0 | Adopt principles | Ignore templates; never commit secrets/build output |

## Meta lists (browse, don’t import wholesale)

| Repo | Stars | Note |
|------|------:|------|
| [sindresorhus/awesome](https://github.com/sindresorhus/awesome) | ~491k | Index of awesome lists — discovery only |
| [public-apis/public-apis](https://github.com/public-apis/public-apis) | ~453k | Public API directory — not architecture gospel |
| [trekhleb/javascript-algorithms](https://github.com/trekhleb/javascript-algorithms) | ~196k | Learning algorithms — not app structure |

## Agentic engineering & vibe workflow (2026-07-30)

| Repo | Stars | License | PVC fit | Note |
|------|------:|---------|---------|------|
| [shanraisshan/claude-code-best-practice](https://github.com/shanraisshan/claude-code-best-practice) | ~64k | MIT | Adopt principles | Agentic catalog: plan-first, R→P→E→R→S, context hygiene, skills/hooks patterns → `core/04` |
| [coleam00/context-engineering-intro](https://github.com/coleam00/context-engineering-intro) | ~14k | MIT | Adopt principles | Feature Brief + Implementation Blueprint (PRP-style), examples/, validation loops → `docs/templates/` |
| [BloopAI/vibe-kanban](https://github.com/BloopAI/vibe-kanban) | ~28k | Apache-2.0 | Optional proposal | Kanban + isolated agent workspaces; **product sunsetting**—use pattern only, do not require install |
| [datawhalechina/easy-vibe](https://github.com/datawhalechina/easy-vibe) | ~19k | check LICENSE | Explore only | Beginner→ship vibe coding course; reinforce Brief/Blueprint, not skip PVC gates |
| [refly-ai/refly](https://github.com/refly-ai/refly) | ~7.5k | custom OSS | Optional proposal | Skills as versioned infrastructure / registry mindset → `03` + `04`; no forced Refly hosting |

Primary PVC rule: **`core/04-agentic-context-workflow.mdc`** (agent-requested). Import via **`external-skill-import`** + **`skill-router`**.

---

## Situational skill sources (triggers) — 2026-07-30

| Repo | Trigger (when to consider) | PVC fit | Do not |
|------|----------------------------|---------|--------|
| [mattpocock/skills](https://github.com/mattpocock/skills) | Need grill/spec/tdd/router patterns | Adopt principles | Install whole plugin set by default |
| [obra/superpowers](https://github.com/obra/superpowers) | Plan→execute gates, subagent review | Adopt principles | Require Superpowers plugin |
| [affaan-m/ECC](https://github.com/affaan-m/ECC) | Context-window hygiene ideas | Optional proposal | Vendor 200+ skills bundle |
| [Leonxlnx/taste-skill](https://github.com/Leonxlnx/taste-skill) | UI taste / visual polish asks | Optional proposal | Override `design/` tokens |
| [mvanhorn/last30days-skill](https://github.com/mvanhorn/last30days-skill) | Fresh multi-source research | Optional proposal | Use for ordinary coding tasks |
| [DietrichGebert/ponytail](https://github.com/DietrichGebert/ponytail) | Extreme minimalism / YAGNI reminders | Optional proposal | Duplicate if core already covers |
| [JuliusBrussee/caveman](https://github.com/JuliusBrussee/caveman) | — | Reject default | Conflicts with clear user reporting |

Import path: `.cursor/skills/external-skill-import` → thin **English** `SKILL.md` only.

---

## Mapping to PVC folders / PVC 폴더 매핑

| PVC area | Prefer these stars |
|----------|--------------------|
| `security/` | OWASP/CheatSheetSeries, gitleaks, trivy |
| `architecture/` | clean-code-*, nodebestpractices, system-design-primer (concepts) |
| `runtime/` | nodebestpractices, TypeScript, eslint, prettier |
| `patterns/` | TanStack Query, zod (when chosen), clean-code async sections |
| `design/` | Tailwind, shadcn/ui (optional), awesome-design-md (structure), KRDS |
| `core/03` + skills | MengTo/Skills, emilkowalski/skills, VoltAgent DESIGN.md, mattpocock/skills |
| `core/04` | claude-code-best-practice, context-engineering-intro, refly, vibe-kanban (pattern), easy-vibe, superpowers (principles) |

---

## Conflict policy / 충돌 정책

1. **PVC `security/` + OWASP/NIST/RFC win** over blog posts and starter templates.  
2. **`project-context.mdc` wins** over any starred repo’s default stack.  
3. **`design/` tokens win** over shadcn/Tailwind demos’ visual language.  
4. Star count ≠ fitness. Prefer license clarity + maintenance + stack match.  
5. New MDC/Skill from these sources must pass duplicate check in `03` / `external-skill-import`.  
6. Executable rules/skills are **English only**; Korean text lives in `docs/pvc-guide/ko/` and is not always-on.
