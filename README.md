# Perfect Vibe Coding (PVC)

Cursor Agent가 **안전하고, 일관되고, 재사용 가능하게** 웹·앱을 만들도록 돕는 전역 거버넌스 규칙 세트입니다.

새 프로젝트를 열 때마다 “어떻게 코딩할지”를 다시 설명하지 않아도 되게,  
품질·안전·문서·디자인·외부 Skill 도입 기준을 `.cursor/rules/`에 고정해 두는 것이 목적입니다.

---

## 왜 만들었는가

AI로 빠르게 화면과 기능을 만드는 **바이브 코딩**은 속도는 빠르지만, 아래 문제가 쉽게 생깁니다.

| 문제 | 실제 결과 |
|------|-----------|
| 요청마다 기준이 바뀜 | 같은 프로젝트인데 파일 구조·네이밍·스타일이 들쭉날쭉해짐 |
| 안전장치 없이 수정 | 데이터 삭제, API 계약 변경, 기존 기능 깨짐 |
| 문서·운영맵 누락 | 나중에 “어디가 뭐하는 코드인지” 알 수 없음 |
| 디자인 시스템 무시 | 페이지마다 다른 색·폰트·버튼, 유지보수 지옥 |
| 외부 Skill·레퍼런스 무분별 도입 | 중복 규칙, 라이선스 리스크, 프로젝트와 안 맞는 패턴 |
| 토큰·비용 낭비 | 불필요한 전체 재작성, 장황한 설명, 범위 밖 리팩터링 |

PVC는 이런 실패를 **규칙 파일로 미리 막아** 두고,  
Cursor가 작업할 때 항상 같은 우선순위·절차·완료 기준을 따르게 만듭니다.

한 줄로 말하면:

> **“빠른 바이브 코딩” + “실무에서 버틸 수 있는 품질·안전·문서화”를 동시에 가져가기 위한 운영 체제**

---

## 웹 개발을 이것으로 시작하면 왜 좋은가

### 1. 첫 커밋부터 “완성 기준”이 있다

“일단 돌아가게”만 하지 않고, 아래를 완료 조건으로 강제합니다.

- 최소 변경으로 목적 달성
- 데이터·연동·기존 기능 보존
- 검증(빌드·테스트·화면·접근성) 수행
- CODEMAP·관련 문서 갱신
- 롤백 방법을 설명할 수 있을 것

### 2. 작업 전·중·후 프로토콜이 있다

구현 전에 영향 범위·위험을 보고하고,  
위험하면 멈추고 질문하며,  
끝나면 완료 보고 형식으로 남깁니다.  
혼자 작업하거나 AI와 협업할 때 **의사결정 로그**가 자연스럽게 쌓입니다.

### 3. 디자인·접근성·한글 타이포가 기본값이다

웹 프로젝트에서 자주 빠지는 항목을 규칙으로 올립니다.

- 디자인 토큰·공통 컴포넌트 우선
- WCAG·키보드·포커스·색상만으로 상태 전달 금지
- 한글 조판·TYPEGUIDE와의 정합성

신뢰·가독성·접근성이 중요한 서비스(공공, 업무, 커머스, SaaS 등)에 특히 유리합니다.

### 4. 방어만이 아니라 “잘하는 방향”도 있다

PVC는 AI가 함부로 하지 못하게 막는 **방어 레이어**와,  
일관된 품질로 구현하게 이끄는 **공격(가이던스) 레이어**를 함께 둡니다.

| 레이어 | 역할 |
|--------|------|
| `security/` | 인증·검증·시크릿 — OWASP·NIST 기준 |
| `devops/` | Git·CI/CD·관찰성 — Conventional Commits·Web Vitals |
| `runtime/` | 타깃 플랫폼·의존성·번들 예산 |
| `patterns/` | async·폼·캐시 등 반복 구현 패턴 |

### 5. 외부 Skill을 “유행”이 아니라 “필요”로 고른다

`03-skill-and-reference-governance`가 다음을 강제합니다.

- 로컬 코드·규정·DESIGN.md를 먼저 조사
- 중복이면 새 파일 만들지 않음
- 출처·라이선스·적용 범위 기록
- 승인 없는 대량 도입 금지

Meng To, VoltAgent DESIGN.md, Emil Kowalski, KRDS 등  
허용된 참고 출처의 **역할 범위**까지 정해 두어, AI가 멋있는 자료를 통째로 복사하지 않게 합니다.

### 6. 프로젝트마다 다시 만들지 않아도 된다

한 번 익힌 PVC를 다른 저장소에 복사하면,  
Agent는 바로 같은 거버넌스 아래에서 일합니다.  
프로젝트별로 채울 것은 주로 `project-context.mdc` 하나입니다.  
스택은 강제하지 않습니다. **고정 스펙 필드만 채우면** 웹·API·앱 모두에 쓸 수 있습니다.

### 7. 토큰·비용을 아끼는 방향으로 움직인다

필요 파일만 읽고, 최소 수정하고, 결론·검증·남은 확인만 보고하도록 되어 있습니다.  
바이브 코딩의 속도는 유지하면서 **불필요한 재생성 비용**을 줄입니다.

---

## 한눈에 보는 구조

```text
perfect-vibe-coding/
├── README.md
├── RULES_MAP.md
├── docs/references/
│   ├── SOURCES.md                 # 공인 표준 출처
│   └── GITHUB_STAR_CATALOG.md     # 고스타 GitHub 카탈로그
└── .cursor/rules/
    ├── core/ architecture/ security/ devops/ runtime/ patterns/ design/ docs/
    ├── project/project-context.mdc   # KR+EN 고정 스펙
    └── en/*.mdc                      # 카테고리별 English canonical (AI용)
```

상세 트리: [`RULES_MAP.md`](./RULES_MAP.md)  
공인 출처: [`docs/references/SOURCES.md`](./docs/references/SOURCES.md)  
고스타 제안: [`docs/references/GITHUB_STAR_CATALOG.md`](./docs/references/GITHUB_STAR_CATALOG.md)

### 언어 이중화 (KR + EN)

| 레이어 | 역할 |
|--------|------|
| 기존 `core/`…`design/` 등 | **한국어 상세 규정** (절차·표·양식) |
| `en/*.mdc` | **영어 canonical** — 전문 개발 용어로 AI가 우선 파싱 |
| `project-context.mdc` | 같은 파일 안에 **English + 한국어** 고정 스펙 |

충돌 시: 보안·데이터 무결성 > `project-context` 기입값 > 한국어 상세와 영어 canonical의 공통 취지 > 고스타 카탈로그 제안.

### 규칙 우선순위 (충돌 시)

1. 보안 · 시크릿 · 데이터 무결성  
2. 안전 프로토콜 · 변경관리 · devops  
3. 프로젝트 맥락 · runtime · architecture  
4. 디자인 시스템 · UI/UX  
5. patterns · 개별 지시  
6. 일반 관행 · (03 절차를 거친) 외부 참고  

---

## 파일별 역할

### `core/`

| 파일 | 역할 |
|------|------|
| `00-development-governance` | 헌장, 우선순위, 금지·최종 기준 |
| `01-safe-work-protocol` | 사전/완료 보고, 중단 조건 (+ Feature Brief 권장) |
| `02-token-efficiency` | 최소 자원 + 컨텍스트 윈도우·세션 요약 |
| `03-skill-and-reference-governance` | 외부 Skill 선별·중복 방지·출처 (+ §4.8 agentic refs) |
| `04-agentic-context-workflow` | Research→Plan→Execute→Review→Ship, Brief/Blueprint, Skill 인프라, 칸반 패턴 |

### `architecture/`

| 파일 | 역할 |
|------|------|
| `code-structure` | 모듈 분리 + **API `{data,meta}` / RFC 9457 에러 / HTTP 상태** |
| `data-integrity` | DB·연동·삭제 제한 |
| `testing-quality` | **테스트 피라미드·커버리지·픽스처/목킹** + 완료 검증 |

### `security/` (신규)

| 파일 | 역할 |
|------|------|
| `auth` | JWT/세션/OAuth 선택, HttpOnly 쿠키, 세션 고정 방지 (OWASP·NIST) |
| `input-validation` | 서버 검증 필수, XSS·CSRF·인젝션·업로드 |
| `secret-management` | `.env`·번들 노출 금지, 스캔·회전 |

### `devops/` (신규)

| 파일 | 역할 |
|------|------|
| `git-workflow` | GitHub Flow, Conventional Commits, PR 조건 |
| `ci-cd` | env 분리, 품질 게이트, 롤백 |
| `observability` | 로그 레벨, 에러 추적, **LCP≤2.5s / INP≤200ms / CLS≤0.1** |

### `runtime/` (신규)

| 파일 | 역할 |
|------|------|
| `platform-targets` | 지원 런타임·브라우저 — 추측 코딩 방지 |
| `dependency-policy` | 패키지 도입·라이선스·audit |
| `build-output` | 번들 예산·트리쉐이킹·산출물 |

### `patterns/` (신규)

| 파일 | 역할 |
|------|------|
| `async-patterns` | loading/success/error, 레이스, AbortController |
| `form-handling` | 검증 계층, 접근성, 중복 제출 방지 |
| `caching-strategy` | HTTP/CDN/클라이언트 캐시·무효화 |

### `project/`

| 파일 | 역할 |
|------|------|
| `project-context` | **KR+EN 고정 스펙**: Tech Stack 기본 예시(Node22/Bun, Next15/React19, Tailwind v4, Postgres+Prisma, Vercel/Railway), Forbidden, LCP/INP/CLS/TTFB/번들 예산, 주석 한국어·식별자 영어·커밋 영어, AI 패턴, 기술부채, 버전 핀 |

### `en/` (English canonical)

| 파일 | 대응 한국어 |
|------|-------------|
| `en/core` | `core/00`–`03` |
| `en/architecture` | `architecture/*` |
| `en/security` | `security/*` |
| `en/devops` | `devops/*` |
| `en/runtime` | `runtime/*` |
| `en/patterns` | `patterns/*` |
| `en/design` | `design/*` |
| `en/docs` | `docs/*` + 카탈로그 포인터 |

### `design/` · `docs/`

| 파일 | 역할 |
|------|------|
| `design/*` | 토큰·한글 타이포·WCAG |
| `docs/codemap-maintenance` | CODEMAP |
| `docs/documentation-standard` | 문서 SSOT |
| `docs/reference-catalog` | 고스타 카탈로그 인덱스 |

---

## 다른 프로젝트에 적용하는 방법

### 1) 규칙 복사

PowerShell 예시:

```powershell
# 이 저장소를 클론했다고 가정
$src = "C:\Users\Yonsei\perfect-vibe-coding\.cursor\rules"
$dst = "경로\내프로젝트\.cursor\rules"
New-Item -ItemType Directory -Force -Path (Split-Path $dst) | Out-Null
Copy-Item -Recurse -Force $src $dst
```

또는 GitHub에서 private 클론 후 `.cursor/rules`만 복사합니다.

```bash
git clone https://github.com/paakseongjin/perfect-vibe-coding.git
```

### 2) 프로젝트 맥락 채우기

`.cursor/rules/project/project-context.mdc`를 열고 다음을 실제 값으로 교체합니다.

- 제품 목적 · 주요 사용자  
- 프론트/백엔드/DB/배포 스택  
- 반드시 지켜야 할 업무·보안 제약  
- CODEMAP / DESIGN / 주요 진입점 위치  

이 파일을 비워 두면 Agent가 **일반적인 가정**으로 움직일 수 있으니, 새 프로젝트의 첫 작업으로 두는 것을 권장합니다.

### 3) 운영 문서 뼈대 만들기 (권장)

PVC 규칙이 기대하는 최소 문서:

```text
프로젝트 루트/
├── README.md          # 개요·실행 방법
├── CODEMAP.md         # 폴더·연동·진입점 (규칙으로 유지 의무)
├── DESIGN.md          # 시각 언어·토큰·컴포넌트 (UI 프로젝트)
├── TYPEGUIDE.md       # 타이포 (한글 포함 시)
└── CHANGELOG.md       # 사용자/운영 관점 변경
```

처음에는 짧은 초안이라도 두고, 기능이 늘 때마다 Agent가 갱신하게 하면 됩니다.

### 4) Cursor에서 확인

1. 대상 프로젝트를 Cursor로 연다.  
2. Rules가 로드되는지 Settings / 프로젝트 rules에서 확인한다.  
3. 작은 요청(예: “CODEMAP 초안 작성”)으로 사전 보고·완료 보고가 나오는지 시험한다.

### 5) 필요에 따라 조정

- 모바일 앱만 한다면 웹 전용 문장은 `project-context`나 개별 mdc에서 구체화한다.  
- `alwaysApply: true`인 파일이 많으면 토큰을 더 쓰므로, 성숙한 프로젝트에서는 일부만 `globs` 기반으로 좁혀도 된다.  
- 팀 규칙과 충돌하면 **보안·데이터 무결성**을 최우선으로 남기고 나머지를 조정한다.

---

## 권장 워크플로 (웹 신규 프로젝트)

```text
1. 저장소 생성 + PVC rules 복사
2. project-context.mdc 작성
3. README / CODEMAP 초안
4. 스택·폴더 구조 확정 (최소 골격만)
5. DESIGN.md / 토큰 초안 (UI가 있으면)
6. 기능 단위로 구현
   → 사전 보고 → 최소 수정 → 검증 → 완료 보고 → CODEMAP 갱신
7. 외부 Skill이 필요하면
   → 03 규정으로 로컬 조사 → 중복 검사 → 사전 보고 → 승인 후 도입
```

Agent에게 첫 메시지로 이렇게 지시해도 됩니다.

```text
이 프로젝트는 perfect-vibe-coding(.cursor/rules)을 따른다.
먼저 project-context와 CODEMAP 초안을 제안하고,
구현은 승인 후 최소 범위로 진행한다.
```

---

## 외부 Skill·레퍼런스를 쓸 때

`03-skill-and-reference-governance.mdc` 요약:

1. **로컬 먼저** — rules, skills, DESIGN, CODEMAP, 코드  
2. **요청 분류** — 구조 / 기능 / UI / 폴리싱 / 모션 / 랜딩 / 감사 / 문서화  
3. **후보 평가** — 목적·호환·운영·중복·보안·라이선스·비용  
4. **판정** — 즉시 적용 / 제안 보관 / 제외  
5. **사전 보고 양식**으로 승인 요청  
6. 적용 후 **출처·라이선스·변환 범위** 기록  

규정에 역할이 정의된 참고 출처 예:

- [MengTo/Skills](https://github.com/MengTo/Skills) — 절차형 UI/랜딩 Skill 구조  
- [VoltAgent/awesome-design-md](https://github.com/VoltAgent/awesome-design-md) — DESIGN.md 문서 구조  
- [emilkowalski/skills](https://github.com/emilkowalski/skills) — 모션·인터랙션·UI 품질  
- [make-interfaces-feel-better](https://github.com/jakubkrehel/make-interfaces-feel-better) — 미세 UI 폴리싱  
- [agency-agents](https://github.com/msitarzewski/agency-agents) — 역할 기반 검토 관점  
- [KRDS UI/UX](https://github.com/KRDS-uiux/krds-uiux) — 국내 공공·접근성·정보 구조  
- [UI Skills](https://www.ui-skills.com/) — Skill 탐색 후보  

**유명하다고 통째로 설치하지 않습니다.** 부족한 원칙만 프로젝트에 맞게 변환합니다.

---

## Agent가 지키는 보고 형식

### 작업 사전 보고

```text
[작업 사전 보고]
- 작업 목적:
- 수정 또는 생성 대상:
- 영향받는 기능·화면·데이터:
- 유지할 기존 동작:
- 작업 단계:
- 예상 위험 요소:
- 검증 계획:
- 사용자 확인이 필요한 사항:
```

### 작업 완료 보고

```text
[작업 완료 보고]
- 완료한 작업:
- 변경된 파일 및 각 파일의 역할:
- 변경하지 않고 유지한 기능:
- 데이터·API·외부 연동 영향:
- 수행한 검증 / 결과:
- 위험 또는 제한사항:
- 롤백 방법:
- 문서·운영 맵 갱신:
- 후속 권장 / 사용자 확인 사항:
```

확인이 필요한 사안이 있으면 **구현을 시작하지 않는 것**이 정상입니다.

---

## 하지 말아야 할 것 (승인 없이)

거버넌스에 명시된 대표 금지 항목:

- DB·파일·사용자 데이터 삭제·초기화·대량 수정  
- 기존 기능 제거·동작 임의 변경  
- API·인증·권한 정책 임의 변경  
- 비밀값·환경변수 노출  
- 의존성 대량 업데이트·프레임워크 교체  
- 폴더 전면 개편  
- 테스트·문서·CODEMAP 없이 구조 변경 완료 선언  
- 디자인 시스템을 무시한 페이지별 임의 스타일  
- 출처 불명 코드·Skill 통째 복사  

---

## 이 저장소 자체는 무엇인가

| 항목 | 내용 |
|------|------|
| 이름 | `perfect-vibe-coding` (PVC) |
| 성격 | **규칙 템플릿 저장소** (앱 런타임 코드 없음) |
| 가시성 | Private |
| 사용법 | 다른 프로젝트의 `.cursor/rules/`로 복사·커스터마이즈 |
| 로컬 경로 예 | `C:\Users\Yonsei\perfect-vibe-coding` |
| 원격 | https://github.com/paakseongjin/perfect-vibe-coding |

앱을 “실행”하는 저장소가 아니라,  
**Cursor Agent의 행동 규약**을 버전 관리하는 저장소입니다.

---

## 빠른 체크리스트

새 프로젝트를 PVC로 시작할 때:

- [ ] `.cursor/rules/` 전체 복사 (+ `docs/references/`)
- [ ] `project-context.mdc` 고정 스펙을 **프로젝트 실제 값으로** 수정 (기본 예시는 Next 스택)
- [ ] `README.md` / `CODEMAP.md` 초안
- [ ] (UI면) `DESIGN.md` / 토큰 방향 초안
- [ ] auth·시크릿·CI 정책을 프로젝트 값으로 구체화
- [ ] 필요 시 `GITHUB_STAR_CATALOG.md`에서 후보만 골라 `03` 절차로 도입
- [ ] Cursor에서 rules 로드 확인 (KR + `en/`)
- [ ] 작은 작업으로 사전·완료 보고 동작 확인
- [ ] 외부 Skill은 `03` 규정 통과 후에만 도입

---

## 공인 출처

규칙은 블로그 유행이 아니라 아래급 원전을 **원칙만 변환**해 넣었습니다.

- 표준·임계값: [`docs/references/SOURCES.md`](./docs/references/SOURCES.md)  
  (OWASP, NIST SP 800-63B-4, RFC 9457/9110/9111, Web Vitals, Conventional Commits, …)
- 고스타 GitHub 제안·별점·라이선스·PVC 매핑: [`docs/references/GITHUB_STAR_CATALOG.md`](./docs/references/GITHUB_STAR_CATALOG.md)  
  (예: airbnb/javascript ~148k, nodebestpractices ~105k, clean-code-javascript ~95k, OWASP CheatSheet ~33k, shadcn/ui ~120k, VoltAgent awesome-design-md ~105k, …)  
  → 도입은 항상 `03` 거버넌스 + `project-context` 우선.

---

## 맵 문서

폴더 트리: [`RULES_MAP.md`](./RULES_MAP.md)  
출처·적용 범위: [`docs/references/SOURCES.md`](./docs/references/SOURCES.md)  
고스타 카탈로그: [`docs/references/GITHUB_STAR_CATALOG.md`](./docs/references/GITHUB_STAR_CATALOG.md)

규칙 본문을 수정할 때는 **한 파일 = 한 책임**을 유지하고,  
한국어 상세를 바꾸면 `en/` canonical도 같은 취지로 맞추며,  
중복이 생기면 `03-skill-and-reference-governance`로 통합을 먼저 검토하세요.
