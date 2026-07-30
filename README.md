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

공공·병원·업무 시스템처럼 **신뢰·가독성·접근성**이 중요한 서비스에 특히 유리합니다.

### 4. 외부 Skill을 “유행”이 아니라 “필요”로 고른다

`03-skill-and-reference-governance`가 다음을 강제합니다.

- 로컬 코드·규정·DESIGN.md를 먼저 조사
- 중복이면 새 파일 만들지 않음
- 출처·라이선스·적용 범위 기록
- 승인 없는 대량 도입 금지

Meng To, VoltAgent DESIGN.md, Emil Kowalski, KRDS 등  
허용된 참고 출처의 **역할 범위**까지 정해 두어, AI가 멋있는 자료를 통째로 복사하지 않게 합니다.

### 5. 프로젝트마다 다시 만들지 않아도 된다

한 번 익힌 PVC를 다른 저장소에 복사하면,  
Agent는 바로 같은 거버넌스 아래에서 일합니다.  
프로젝트별로 채울 것은 주로 `project-context.mdc` 하나입니다.

### 6. 토큰·비용을 아끼는 방향으로 움직인다

필요 파일만 읽고, 최소 수정하고, 결론·검증·남은 확인만 보고하도록 되어 있습니다.  
바이브 코딩의 속도는 유지하면서 **불필요한 재생성 비용**을 줄입니다.

---

## 한눈에 보는 구조

```text
perfect-vibe-coding/
├── README.md                 # 이 가이드
├── RULES_MAP.md              # 폴더·파일 맵
└── .cursor/
    └── rules/
        ├── core/             # 전역 헌장·절차·효율·Skill 거버넌스
        ├── architecture/     # 구조·데이터·검증
        ├── design/           # 디자인 시스템·타이포·접근성
        ├── docs/             # CODEMAP·문서 표준
        └── project/          # 프로젝트별 맥락 템플릿
```

### 규칙 우선순위 (충돌 시)

`00-development-governance`에 정의된 순서입니다.

1. 보안 · 개인정보 · 데이터 무결성  
2. 안전 작업 프로토콜 · 변경관리  
3. 프로젝트별 기술·도메인 규칙  
4. 디자인 시스템 · UI/UX  
5. 기능별 구현 가이드 · 개별 지시  
6. 일반 관행 · 외부 참고자료  

---

## 파일별 역할

### `core/` — 모든 작업에 항상 적용

| 파일 | 역할 |
|------|------|
| `00-development-governance.mdc` | 전역 헌장. 품질·관심사 분리·완료 코드 보존, 외부자료 원칙, 금지 사항, 최종 완료 질문 10개 |
| `01-safe-work-protocol.mdc` | 작업 전 필수 절차, 사전/완료 보고 양식, 변경 최소화, 작업 중단·질문 조건 |
| `02-token-efficiency.mdc` | 최소 자원·간결 응답. 불필요한 전체 재출력·범위 밖 리팩터링 억제 |
| `03-skill-and-reference-governance.mdc` | 외부 Skill·레퍼런스 선별, 중복 방지, MDC/Skill/DESIGN.md 생성 규격, 출처·라이선스 |

### `architecture/` — 코드와 데이터

| 파일 | 역할 |
|------|------|
| `code-structure.mdc` | 모듈·폴더·관심사 분리, 웹 표준, 성능 기준 |
| `data-integrity.mdc` | DB·API·연동 보호, 비밀값 비노출, 삭제/정리 제한 |
| `testing-quality.mdc` | 무결성 목표, 작업 후 필수 검증 체크리스트 |

### `design/` — UI의 일관성

| 파일 | 역할 |
|------|------|
| `design-system.mdc` | 토큰·컴포넌트 우선, 디자인 문서 운영 |
| `typography-korean.mdc` | 한글 조판, TYPEGUIDE·토큰 정합 |
| `accessibility.mdc` | WCAG 2.2, 키보드·포커스, 색상만으로 상태 전달 금지 |

### `docs/` — 문서가 코드와 같이 움직이게

| 파일 | 역할 |
|------|------|
| `codemap-maintenance.mdc` | `CODEMAP.md` 의무 항목, 변경 시 최신화 |
| `documentation-standard.mdc` | 단일 진실 공급원(README, CODEMAP, DESIGN 등), 변경 이력 형식 |

### `project/` — 프로젝트마다 채우는 유일한 템플릿

| 파일 | 역할 |
|------|------|
| `project-context.mdc` | 목적, 스택, 도메인, 진입점, 참고 문서 — **복사 후 반드시 수정** |

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

새 웹 프로젝트를 PVC로 시작할 때:

- [ ] `.cursor/rules/` 전체 복사  
- [ ] `project-context.mdc` 작성  
- [ ] `README.md` / `CODEMAP.md` 초안  
- [ ] (UI면) `DESIGN.md` / 토큰 방향 초안  
- [ ] Cursor에서 rules 로드 확인  
- [ ] 작은 작업으로 사전·완료 보고 동작 확인  
- [ ] 외부 Skill은 `03` 규정 통과 후에만 도입  

---

## 맵 문서

폴더 트리만 빠르게 보려면 [`RULES_MAP.md`](./RULES_MAP.md)를 참고하세요.

규칙 본문을 수정할 때는 가능하면 **한 파일 = 한 책임**을 유지하고,  
중복이 생기면 `03-skill-and-reference-governance`의 중복 검사 절차로 통합·보완을 먼저 검토하세요.
