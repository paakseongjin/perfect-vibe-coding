# PVC 한국어 해설 가이드

이 폴더는 **사람이 읽는 해설·배경·사례**용입니다.  
Cursor Agent가 매 채팅에 자동으로 로드하지 않습니다.

## 언어 정책

| 종류 | 언어 | 위치 |
|------|------|------|
| 실행 규칙 (`.mdc`) | English | `.cursor/rules/` |
| Skills (`SKILL.md`) | English | `.cursor/skills/` |
| 해설·양식·사례 | 한국어 | `docs/pvc-guide/ko/` (여기) |

Agent에게 “한국어로 설명해 줘”라고 할 때만 이 폴더를 열람하면 됩니다.

## 목차

- **`../개발방향-설문.md`** — PVC 적용 전 **필수** 개발 방향 설문 (한글)
- `core/` — 거버넌스, 안전 프로토콜, 토큰, Skill 거버넌스, 에이전틱 워크플로
- `architecture/` — 코드 구조, 데이터 무결성, 테스트
- `security/` — 인증, 입력 검증, 시크릿
- `devops/` — Git, CI/CD, 관찰성
- `runtime/` — 플랫폼, 의존성, 빌드
- `patterns/` — async, 폼, 캐시
- `design/` — 디자인 시스템, 접근성, 한글 타이포
- `docs/` — CODEMAP, 문서화, 레퍼런스 카탈로그
- `project/` — project-context 템플릿 해설 (구 이중언어 본문)
- `_archived-en-canonical/` — 업그레이드 전 EN canonical 스냅샷

## 실행 규칙과의 관계

실제 Agent 동작은 `.cursor/rules/`의 **English 실행 규칙**과 `.cursor/skills/`를 따릅니다.  
여기 문서와 실행 규칙이 다르면 **실행 규칙(EN)이 우선**입니다.
