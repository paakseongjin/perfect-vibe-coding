---
description: "Agentic / context engineering workflow. Map Research→Plan→Execute→Review→Ship, feature briefs, examples, validation loops. Principles from high-star vibe/agent repos—Cursor-adapted. KR+EN."
alwaysApply: true
---

# Agentic Context Workflow / 에이전틱 컨텍스트 워크플로

> **Purpose:** Move from unstructured “vibe chatting” to **context engineering + gated agentic delivery**.  
> **Sources (principles only, not vendor lock-in):**  
> - [shanraisshan/claude-code-best-practice](https://github.com/shanraisshan/claude-code-best-practice) (~64k★, MIT)  
> - [coleam00/context-engineering-intro](https://github.com/coleam00/context-engineering-intro) (~14k★, MIT)  
> - [refly-ai/refly](https://github.com/refly-ai/refly) (~7.5k★, Apache-2.0-based custom)  
> - [BloopAI/vibe-kanban](https://github.com/BloopAI/vibe-kanban) (~28k★, Apache-2.0; product sunsetting—pattern only)  
> - [datawhalechina/easy-vibe](https://github.com/datawhalechina/easy-vibe) (~19k★, course)  
> **Conflict rule:** `security/` + `01-safe-work-protocol` + `project-context` always win. Do not install Claude-only harnesses, Refly cloud, or Vibe Kanban unless the user explicitly asks.

---

## English

### 1. Default loop (all non-trivial work)

```text
Research → Plan → Execute → Review → Ship
```

1. **Research** — CODEMAP, rules, similar code, docs, tests; inventory gaps (see `03`).
2. **Plan** — Pre-report (`01`); phase-wise plan with validation per phase. Prefer plan/approval before large edits.
3. **Execute** — Minimal diffs; follow `project-context` stack/Forbidden.
4. **Review** — Self-check + tests/lint; optional second-pass review (separate agent/session) for risky changes.
5. **Ship** — Completion report, CODEMAP/docs update, clear rollback.

Never jump straight to code for ambiguous or multi-file features.

### 2. Context engineering > clever prompts

Most agent failures are **context failures**, not model failures.

Provide a **system of context**, not a sticky-note prompt:

| Context asset | PVC / Cursor location |
|---------------|------------------------|
| Global rules | `.cursor/rules/` (+ `en/` canonical) |
| Project identity | `project/project-context.mdc` |
| Structure map | `CODEMAP.md` |
| Feature brief | `docs/templates/FEATURE_BRIEF.md` (copy per feature) |
| Implementation blueprint (PRP-style) | `docs/templates/IMPLEMENTATION_BLUEPRINT.md` |
| Examples to mimic | `examples/` (recommended in app repos) |

- Keep always-on rules **focused**; put domain detail in globs/skills, not one endless file.
- Prefer **examples of good patterns** over long prose (“show, don’t only tell”).
- Feature requests should state: goal, examples to follow, docs links, gotchas AI usually misses.

### 3. Feature brief → blueprint → execute

Adapted from Context Engineering Intro (INITIAL.md → PRP → execute), Cursor-friendly:

1. User/agent fills a **Feature Brief** (what / constraints / examples / docs / risks).
2. Agent produces an **Implementation Blueprint** (steps, files, validation commands, acceptance, confidence).
3. User approves if risk is non-trivial (`01`).
4. Execute with **validation gates** (lint, unit, build, manual checks)—iterate until gates pass; do not declare done early.
5. Record outcomes in completion report + CODEMAP.

Blueprints are for **AI execution**, not only human PRD theater.

### 4. Skills & agents as infrastructure

From Refly + Claude best-practice (transformed):

- Skills are **durable, versioned capabilities**—not one-off chat prompts.
- Prefer **atomic skills** with: trigger description, when *not* to use, inputs, workflow, guardrails, acceptance, sources (`03` formats).
- Progressive disclosure: `SKILL.md` + optional `references/`, `scripts/`, `examples/`—don’t dump everything into alwaysApply rules.
- Description field = **when to fire**, not a marketing summary.
- Focus on what overrides default model behavior; avoid railroaded micro-steps that fight judgment.
- Do **not** bulk-install skill marketplaces; select via `03` + `GITHUB_STAR_CATALOG`.
- Subagents/Task tools: use to **isolate research context**; return conclusions, not raw tool spam, into the main thread (`02`).

### 5. Session & context hygiene

From Claude Code best-practice tips (tool-agnostic):

- New major task → prefer **new chat/session**; related doc-for-just-built-feature may reuse context.
- If the agent went down a bad path: **rewind/restate** with lessons learned rather than stacking corrections forever.
- Keep sessions from rotting: summarize state, compact intent, or restart when quality drops.
- Offload large exploration to subagents/tasks so the main context stays decision-focused.
- Put harness facts (test/build commands) where the agent can run them first try—`project-context` + CODEMAP.

(See also token/session notes in `02-token-efficiency` and English `en/core.mdc` §3.)

### 6. Planning / review boards (optional tooling pattern)

From Vibe Kanban (pattern only; product is sunsetting):

- Track work as **issues**: plan → in progress → review → done.
- Give each parallel agent task an **isolated branch/worktree** when possible (`devops/git-workflow`).
- Optimize human time on **plan quality and diff review**, not babysitting every keystroke.
- Inline review comments → feed back as explicit correction briefs; don’t silently merge broken agent output.

Do not require Vibe Kanban UI. GitHub Issues / Projects / local TODO is enough.

### 7. Learning → shipping (Easy-Vibe stance)

- “If you can describe it, you can start”—but PVC still requires **constraints, validation, and docs**.
- Beginners: follow Feature Brief + Blueprint templates before free-form chat coding.
- Describe product outcomes in user language, then map to `project-context` stack—don’t invent a new stack mid-vibe.

### 8. Explicit non-goals

- Not a requirement to use Claude Code, Refly hosting, or Vibe Kanban.
- Not permission to bypass PVC security, approvals, or CODEMAP.
- Not an excuse to paste entire upstream repos into `.cursor/`.

---

## 한국어

### 1. 기본 루프

```text
조사(Research) → 계획(Plan) → 실행(Execute) → 검토(Review) → 인도(Ship)
```

모호하거나 다중 파일 작업에서 계획·승인 없이 바로 코딩하지 않는다. 단계별 검증(테스트/린트/빌드)을 둔다.

### 2. 컨텍스트 엔지니어링

에이전트 실패의 상당수는 모델이 아니라 **컨텍스트 부족/오염**이다.  
규칙·`project-context`·CODEMAP·기능 브리프·예시 코드·검증 명령을 **시스템으로** 제공한다.  
말만 길게 하기보다 `examples/` 패턴을 보여 준다.

### 3. 기능 브리프 → 구현 블루프린트 → 실행

1. Feature Brief 작성 (`docs/templates/FEATURE_BRIEF.md`)  
2. Implementation Blueprint 작성 (`docs/templates/IMPLEMENTATION_BLUEPRINT.md`)  
3. 위험하면 승인 (`01`)  
4. 검증 게이트 통과까지 반복  
5. 완료 보고 + CODEMAP 갱신  

### 4. Skill은 인프라

일회성 프롬프트가 아니라 버전·수용 기준·가드레일이 있는 자산으로 관리한다 (`03`).  
대량 마켓 설치 금지. 서브에이전트는 조사 격리·결론만 본선에 반환.

### 5. 세션 위생

새 큰 작업은 새 세션 선호. 잘못된 분기는 교정 누적보다 재진술. 탐색은 서브태스크로 분리 (`02`).

### 6. 칸반/격리 (선택)

이슈로 계획·리뷰를 관리하고, 병렬 작업은 브랜치/워크트리로 격리. 도구는 강제하지 않음.

### 7. Easy-Vibe 관점

말로 시작하되, PVC의 제약·검증·문서는 생략하지 않는다.

## Sources

- https://github.com/shanraisshan/claude-code-best-practice — MIT — 2026-07-30 — loop, plan-first, context hygiene, skills progressive disclosure  
- https://github.com/coleam00/context-engineering-intro — MIT — 2026-07-30 — INITIAL/PRP-style briefs, examples, validation loops  
- https://github.com/refly-ai/refly — custom OSS license — 2026-07-30 — skills as versioned infrastructure  
- https://github.com/BloopAI/vibe-kanban — Apache-2.0 — 2026-07-30 — plan/review board + isolated agent workspaces (pattern; product sunsetting)  
- https://github.com/datawhalechina/easy-vibe — course — 2026-07-30 — structured learning path from vibe to product  
- Apply mode: principles transformed for Cursor/PVC; no wholesale copy of tool configs.
