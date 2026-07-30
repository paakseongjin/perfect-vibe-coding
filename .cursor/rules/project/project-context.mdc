---
description: "Project identity card / 프로젝트 신분증. Fill before coding. Default example stack is a starting template—replace per project. alwaysApply."
alwaysApply: true
---

# Project Context (Fixed Spec Template)
# 프로젝트 맥락 (고정 스펙 템플릿)

> **When to use / 사용 시점:** Every new repo copied from PVC. Fill this file once (~30 min) so every Cursor chat inherits the same stack, bans, budgets, and naming. Empty fields cause the agent to guess.  
> **주의:** 아래 값은 **기본 예시(Default Example)** 이다. 다른 스택이면 반드시 교체한다. PVC 자체는 특정 프레임워크를 강제하지 않는다.

---

## English

### 1. Product purpose

- Product / service goal: _(fill)_
- Primary users & environments: _(fill)_
- Success criteria: _(fill)_
- Non-goals: _(fill)_

### 2. Tech Stack — Default Example (replace if different)

```text
- Runtime: Node 22 / Bun 1.x
- Language / Type system: TypeScript (strict: yes)
- Framework: Next.js 15 (App Router) / React 19
- Styling: Tailwind CSS v4
- Data store / ORM: PostgreSQL + Prisma ORM
- Auth approach: _(e.g. Auth.js / custom session / IdP — fill)_
- Hosting / Deploy: Vercel / Railway
- CI: _(e.g. GitHub Actions — fill)_
- Observability: _(e.g. Sentry + Web Vitals — fill)_
- Major external integrations: _(fill)_
```

### 3. Forbidden

```text
- React class components (use function components)
- Inline styles except dynamic values
- TypeScript `any` or unguarded `unknown`
- Mixing Server/Client Components without an explicit reason
- Calling Prisma (or DB) directly inside UI presentational components
- Ad-hoc `fetch` from UI when a service/data layer exists — go through that layer
- Leaving `console.log` in production paths
- Client `useEffect` data-fetching when Server Components / TanStack Query (or project standard) should be used
- Using production DB for local experiments
```

### 4. Performance Budget

```text
- LCP: < 2.5s (p75) — Core Web Vitals “Good”
- INP: ≤ 200ms (p75)
- CLS: ≤ 0.1 (p75)
- TTFB: ≤ 800ms (target; diagnose via CrUX/PSI when missed)
- Initial JS bundle: < 200KB gzipped (entry / critical path)
```

### 5. Code Language & Naming

```text
- Comments / internal docs: Korean (한국어)
- Identifiers (variables, functions, types, files): English, camelCase / PascalCase as idiomatic
- Commit messages: English, Conventional Commits (feat/fix/chore/docs/…)
- Branch strategy: GitHub Flow (unless overridden below)
```

### 6. Domain rules

- Domain glossary: _(fill)_
- Hard business / legal / security constraints: _(fill)_
- Changes that always require human approval: _(fill)_

### 7. Architecture notes

- Entry points: _(fill)_
- Module boundaries / dependency direction: _(fill)_
- Data flow summary: _(fill)_
- API envelope / error format: prefer `{ data, meta }` success + RFC 9457 Problem Details errors (unless legacy fixed)
- Known tech debt: see §11

### 8. Environments & secrets

- Environments: development / staging / production _(adjust names)_
- Secret store: _(platform secrets / Vault / …)_
- `.env.example` path: _(fill)_

### 9. Reference docs

- `CODEMAP.md`:
- `ARCHITECTURE.md`:
- `DESIGN.md` / `TYPEGUIDE.md`:
- OpenAPI / schema:
- Other:

### 10. AI working patterns (fixed)

```text
- Components: Server Component by default; add 'use client' only when required
- Styling order: Tailwind utilities → cn()/clsx composition → CSS Module only as exception
- Data fetching preference: Server Actions / server fetch → TanStack Query → SWR (pick project standard and stick to it)
- New folders: only when ≥3 files share a domain; otherwise keep flat
- Do not invent a parallel stack when this file already specifies one
```

### 11. Known tech debt & temporary workarounds

```text
- [YYYY-MM-DD] description → location → do not “fix sideways” without updating this list
```

### 12. Version pins & compatibility

```text
- next: 15.x (App Router only; pages router forbidden unless listed here)
- react: 19.x (React Compiler: Y/N — fill)
- tailwindcss: 4.x (limit legacy v3-only patterns)
- prisma: _(major.x — fill)_
- Always read changelogs before major upgrades; no drive-by major bumps
```

---

## 한국어

### 1. 프로젝트 목적

- 제품/서비스 목적: _(기입)_
- 주요 사용자·사용 환경: _(기입)_
- 핵심 성공 기준: _(기입)_
- Non-goals: _(기입)_

### 2. Tech Stack — 기본 예시 (다르면 교체)

```text
- Runtime: Node 22 / Bun 1.x
- Language / Type system: TypeScript (strict: yes)
- Framework: Next.js 15 (App Router) / React 19
- Styling: Tailwind CSS v4
- Data store / ORM: PostgreSQL + Prisma ORM
- Auth approach: _(기입)_
- Hosting / Deploy: Vercel / Railway
- CI: _(기입)_
- Observability: _(기입)_
- Major external integrations: _(기입)_
```

### 3. Forbidden (금지)

```text
- React class components 금지 (함수 컴포넌트만)
- inline styles 금지 (동적 값 예외)
- TypeScript any / 가드 없는 unknown 금지
- Server/Client Component 근거 없는 혼용 금지
- UI 프레젠테이션 컴포넌트 안에서 Prisma(DB) 직접 호출 금지
- 서비스/데이터 계층이 있는데 UI에서 임의 fetch 금지
- production 경로에 console.log 잔류 금지
- Server Component / 프로젝트 표준 쿼리 라이브러리로 해야 할 일을 useEffect 데이터 패칭으로 대체 금지
- 운영 DB를 로컬 실험에 사용 금지
```

### 4. Performance Budget

```text
- LCP: < 2.5s (p75)
- INP: ≤ 200ms (p75)
- CLS: ≤ 0.1 (p75)
- TTFB: ≤ 800ms (목표)
- Initial JS (gzip): < 200KB
```

### 5. Code Language & Naming

```text
- 주석/내부 문서: 한국어
- 식별자: 영어 camelCase / PascalCase
- 커밋 메시지: 영어 Conventional Commits (feat/fix/chore/docs/…)
- 브랜치: GitHub Flow (아래에서 다르게 명시하지 않는 한)
```

### 6. 도메인·업무 규칙

- 핵심 용어: _(기입)_
- 법적·보안·업무 하드 제약: _(기입)_
- 무조건 승인 필요 변경: _(기입)_

### 7. 아키텍처 메모

- 진입점 / 모듈 경계 / 데이터 흐름: _(기입)_
- API: 성공 `{ data, meta }`, 오류 RFC 9457 (레거시 예외 시 명시)
- 기술 부채: §11

### 8. 환경·시크릿

- 환경명, 시크릿 위치, `.env.example` 경로: _(기입)_

### 9. 참고 문서

- CODEMAP / ARCHITECTURE / DESIGN / OpenAPI: _(기입)_

### 10. AI 작업 패턴 고정

```text
- 컴포넌트: Server Component 기본, 필요 시에만 'use client'
- 스타일: Tailwind → cn() 조합 → CSS Module은 예외
- 데이터: Server Action/서버 fetch → TanStack Query → SWR (프로젝트 표준 하나로)
- 폴더: 동일 도메인 파일 3개 이상일 때만 생성
- 이 파일에 스택이 있으면 병렬 스택을 새로 만들지 말 것
```

### 11. 알려진 기술 부채 & 임시 우회

```text
- [YYYY-MM-DD] 설명 → 위치 → 목록 갱신 없이 편법 확장 금지
```

### 12. 버전 고정 & 호환성

```text
- next 15.x App Router / react 19.x / tailwind 4.x / prisma (기입)
- 메이저 업은 changelog 확인 + 승인 후에만
```
