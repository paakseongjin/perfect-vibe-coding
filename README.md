# Perfect Vibe Coding (PVC)

**말로 웹·앱을 만드는 사람을 위한 Cursor 작업 운영 체제**

> **빠른 바이브 코딩**은 유지하고, **실무에서 버틸 수 있는 안전·일관성·문서**를 기본값으로 만듭니다.

코딩을 몰라도 Cursor Agent에게 원하는 화면·기능을 말해 제품을 만들 수 있습니다.  
PVC는 AI가 매번 다른 기준으로 흔들리지 않게 **얇은 상시 규칙 + 상황별 스킬·규정**을 제공합니다.

---

## 처음 10분만 이렇게 하세요

1. `.cursor/rules/` 와 `.cursor/skills/` 를 내 프로젝트에 복사한다 (또는 이 저장소를 템플릿으로 쓴다).  
2. (권장) [`docs/pvc/개발방향-설문.md`](./docs/pvc/개발방향-설문.md) 를 **따로 받아** Quick 4문항만이라도 채운다 — **필수는 아님**, 기획이 선명해질수록 Agent가 정확해진다.  
3. `.cursor/rules/project/project-context.mdc` 에 제품·스택·금지·검사 명령을 짧게 채운다.  
4. Cursor에서 폴더를 연다.  
5. Agent에게: `CODEMAP.md 초안만 제안해 줘. 구현은 승인 후에.`  
6. 작은 문구 수정 한 번으로 동작을 시험한다.

막히면: `PVC README 처음 10분 단계부터 한글로 도와줘`

---

## 누구를 위한가

| 대상 | 맞는 경우 |
|------|-----------|
| 비개발자·비전문가 | 아이디어는 있는데 코드를 직접 쓰기 어려울 때 |
| 1인 창업자·기획자 | Cursor로 MVP·랜딩·내부 도구를 만들 때 |
| 소규모 팀 | AI마다 결과 기준이 달라 흔들릴 때 |
| 개발자 | 보안·품질·문서 기준을 저장소에 고정하고 싶을 때 |

학위는 필요 없습니다. Cursor·GitHub·“무엇을 만들고 싶은지”를 말할 수 있으면 충분합니다.

---

## PVC가 막아 주는 문제

| 문제 | 결과 | PVC |
|------|------|-----|
| 기준이 매번 바뀜 | 구조·스타일 난잡 | 고정 규칙 + 사실 카드 |
| 위험한 수정 | 데이터·로그인 사고 | 승인 없는 위험 작업 금지 |
| 문서 없음 | 나중에 이해 불가 | CODEMAP 습관 |
| 디자인 분열 | 페이지마다 다른 UI | 디자인 시스템 우선 |
| 스킬 남용 | 충돌·비용 | **원칙만** 변환, 통째 설치 금지 |
| 토큰 낭비 | 매 채팅 과금 | 상시 규칙 2개만 |

---

## 핵심 원칙

1. **상시 규칙은 얇게** — Always는 안전 헌법 + 프로젝트 사실만.  
2. **상황 규칙은 정확하게** — 연 파일·작업 종류에 맞는 규칙만.  
3. **실행은 영어, 해설은 한글** — Agent용 rules/skills는 EN, 사람용 가이드는 KO.  
4. **유명해도 통째 설치 금지** — 필요한 원칙만 프로젝트에 맞게 변환.  
5. **한 주제는 한곳에** — Rules / Skills / Docs / Templates / References 역할 분리.  
6. **보안·데이터 최우선**  
7. **기획 설문은 권장** — [`개발방향-설문.md`](./docs/pvc/개발방향-설문.md) 로 초안을 선명히 (필수 아님).

---

## 설치 (조금 더 자세히)

### 준비물

Cursor, Git/GitHub. (선택) Node 등 — 스택은 `project-context`에 적습니다.

### 1) PVC 붙이기

- **A.** 이 저장소를 fork/복사 후 제품 이름으로 사용  
- **B.** 기존 앱에 `.cursor/rules/`, `.cursor/skills/` 복사 (+ 필요 시 `docs/`)

### 2) 기획 설문 (권장 · 별도 파일)

파일: [`docs/pvc/개발방향-설문.md`](./docs/pvc/개발방향-설문.md)

- 다운로드·복사해서 답변해도 됩니다.  
- **Quick** (실험) / **Standard** (MVP) / **High Risk** (인증·결제·DB 등) 등급이 있습니다.  
- 없어도 PVC는 동작합니다. 다만 답변이 있을수록 Agent 지시가 정확합니다.

```text
설문 답변을 project-context와 CODEMAP 초안에만 반영해 줘.
구현은 승인 후.
```

### 3) 프로젝트 사실 카드

`.cursor/rules/project/project-context.mdc` — Agent가 매 채팅에 보는 **짧은** 카드.

| 넣을 것 | 예 |
|---------|----|
| 제품 한 줄 | 동네 카페 예약 웹앱 |
| 사용자 | 사장님 + 손님, 모바일 |
| 스택 | 쓰는 기술만 |
| 금지 | 운영 DB 직접 쓰기 금지 |
| 검사 명령 | lint / test / build |

### 4) CODEMAP 초안 → 작은 시험 → 본 기능

큰 기능은 `skill-router`로 필요한 규칙만 고르게 하세요.

---

## 더 알아보기 — Rules / Skills / 문서가 켜지는 방식

자세한 지도: [`RULES_MAP.md`](./RULES_MAP.md)

| 스위치 | 의미 | 예 |
|--------|------|-----|
| Always (2개) | 매 채팅 | `core/00`, `project-context` |
| Globs | 관련 파일을 만질 때 | UI → design, API → security |
| Agent / Skill | 작업 성격에 맞게 | skill-router, 외부 스킬 import |
| Manual | 위험·드문 일 | migration, incident |

**역할 분리 (한 주제 한곳)**

| 종류 | 책임 | 넣지 말 것 |
|------|------|------------|
| Rules | 짧은 행동 명령 | 장문 절차·양식 |
| Skills | 작업 단계 절차 | 헌법 재서술 |
| Docs (ko) | 이유·사례 | Agent 자동 로드 전제 |
| Templates | 채울 양식 | 정책 원문 |
| References | 출처·후보 | 통째 설치 지시 |
| 개발방향-설문 | 기획 초안 (권장) | Always 규칙 대체 |

언어: 실행 rules/skills = **영어** / 설문·README·`pvc-guide/ko` = **한글** (자동 로드 안 함).

---

## 더 알아보기 — Agent에게 말하는 법

**좋은 예:** 범위가 보이는 요청 (“히어로에 제품명+CTA 하나”, “이 버튼 색만 토큰에 맞게”).  
**피할 예:** “전체 리팩터”, “유명 스킬 전부 설치”, “운영 DB로 테스트”.

**승인 필요:** 데이터 삭제·스키마 변경, 로그인/결제/개인정보, 대량 의존성, 폴더 전면 이동.

---

## 더 알아보기 — 외부 고급 참고 자료

**유명하다고 통째로 설치하지 않습니다.** 필요·적용 가능한 원칙만 변환합니다.

| 자료 | 링크 | 역할 |
|------|------|------|
| Meng To Skills | https://github.com/MengTo/Skills | UI·랜딩 절차형 스킬 구조 |
| VoltAgent DESIGN.md | https://github.com/VoltAgent/awesome-design-md | DESIGN.md 문서 구조 |
| Emil Kowalski Skills | https://github.com/emilkowalski/skills | 모션·인터랙션·UI 품질 |
| make-interfaces-feel-better | https://github.com/jakubkrehel/make-interfaces-feel-better | 미세 UI 폴리싱 |
| Agency Agents | https://github.com/msitarzewski/agency-agents | 역할 기반 검토 관점 |
| KRDS UI/UX | https://github.com/KRDS-uiux/krds-uiux | 접근성·폼·공공성 (출처 표기) |
| UI Skills | https://www.ui-skills.com/ | UI 스킬 탐색 |

가져오기: `external-skill-import` + `core/03`.  
상세: [`GITHUB_STAR_CATALOG.md`](./docs/references/GITHUB_STAR_CATALOG.md), [`03 한글 해설`](./docs/pvc-guide/ko/core/03-skill-and-reference-governance.md)

---

## 자주 묻는 질문

**Q. 설문을 꼭 써야 하나요?**  
A. **아니요, 권장입니다.** 별도 파일로 받아 기획 초안용으로 쓰세요. 없어도 `project-context`로 시작할 수 있습니다.

**Q. 영어 규칙을 다 읽어야 하나요?**  
A. 아니요. README·설문·`docs/pvc-guide/ko/`가 사람용입니다.

**Q. Next가 아니면요?**  
A. `project-context`만 바꾸면 됩니다.

**Q. 스킬을 많이 깔면 좋아지나요?**  
A. 보통 아닙니다. 원칙만 가져오세요.

**Q. 한글 해설과 영어 규칙이 다르면?**  
A. **영어 실행 규칙이 우선**입니다.

---

## 문서 링크

| 문서 | 내용 |
|------|------|
| [`docs/pvc/개발방향-설문.md`](./docs/pvc/개발방향-설문.md) | 기획 초안 설문 (**권장**, 별도 사용 가능) |
| [`RULES_MAP.md`](./RULES_MAP.md) | 규칙·스킬 지도·책임 경계 |
| [`docs/pvc/CHECKLISTS.md`](./docs/pvc/CHECKLISTS.md) | 적용 후 회고·체크 |
| [`docs/pvc/DECISIONS.md`](./docs/pvc/DECISIONS.md) | 운영 결정 기록 |
| [`docs/pvc-guide/ko/`](./docs/pvc-guide/ko/README.md) | 한글 상세 해설 |
| [`docs/references/`](./docs/references/GITHUB_STAR_CATALOG.md) | 외부 출처 카탈로그 |
| [`docs/templates/`](./docs/templates/FEATURE_BRIEF.md) | Brief / Blueprint |

---

## 마치며

PVC는 규칙 더미가 아니라 **상황에 맞는 최소 레일**입니다.  
시작은 **10분 블록**이면 충분하고, 기획을 깊게 하고 싶을 때만 설문을 쓰면 됩니다.
