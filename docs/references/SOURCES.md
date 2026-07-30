# PVC 외부 출처 및 적용 기록

이 문서는 perfect-vibe-coding 규칙이 **참고·변환**한 공신력 있는 자료의 목록이다.  
외부 자료를 통째로 복사하지 않았고, 원칙·임계값·절차만 프로젝트 거버넌스에 맞게 재작성했다.

확인일: **2026-07-30**

추가 카탈로그: 고스타 GitHub 선별 목록은 [`GITHUB_STAR_CATALOG.md`](./GITHUB_STAR_CATALOG.md) (API로 star 수 확인).  
실행 규칙: `.cursor/rules/**/*.mdc` (**English only**, always/globs/agent).  
한국어 해설: `docs/pvc-guide/ko/` (자동 로드 안 함).  
에이전틱/컨텍스트: `.cursor/rules/core/04-agentic-context-workflow.mdc` + `docs/templates/` + `.cursor/skills/`.

## 보안

| 자료 | URL | PVC 반영 위치 | 참고 범위 |
|------|-----|---------------|-----------|
| OWASP Session Management Cheat Sheet | https://cheatsheetseries.owasp.org/cheatsheets/Session_Management_Cheat_Sheet.html | `security/auth.mdc` | Cookie 속성, 세션 수명, 고정 공격 방지 |
| OWASP ASVS V7 | https://asvs.dev/v5.0.0/V7-Session-Management/ | `security/auth.mdc` | 세션 검증 요구사항 |
| OWASP Authentication Cheat Sheet | https://cheatsheetseries.owasp.org/cheatsheets/Authentication_Cheat_Sheet.html | `security/auth.mdc` | 인증 일반 원칙 |
| NIST SP 800-63B-4 | https://doi.org/10.6028/NIST.SP.800-63B-4 | `security/auth.mdc`, `secret-management.mdc` | 인증기·비밀 취급 원칙 |
| OWASP Input Validation / XSS / CSRF / File Upload Cheat Sheets | https://cheatsheetseries.owasp.org/ | `security/input-validation.mdc` | 검증·출력 인코딩·업로드 |
| OWASP Top 10 | https://owasp.org/www-project-top-ten/ | `security/input-validation.mdc` | 위협 우선순위 |
| OWASP Secrets Management / Logging Cheat Sheets | https://cheatsheetseries.owasp.org/ | `security/secret-management.mdc`, `devops/observability.mdc` | 비밀·로그 |

## API·HTTP

| 자료 | URL | PVC 반영 위치 | 참고 범위 |
|------|-----|---------------|-----------|
| RFC 9457 Problem Details | https://www.rfc-editor.org/rfc/rfc9457.html | `architecture/code-structure.mdc` | 오류 JSON 표준 |
| RFC 9110 HTTP Semantics | https://www.rfc-editor.org/rfc/rfc9110 | `architecture/code-structure.mdc` | 상태 코드 의미 |
| RFC 9111 HTTP Caching | https://www.rfc-editor.org/rfc/rfc9111 | `patterns/caching-strategy.mdc` | 캐시 헤더 의미 |

## 성능·관찰

| 자료 | URL | PVC 반영 위치 | 참고 범위 |
|------|-----|---------------|-----------|
| web.dev Web Vitals | https://web.dev/articles/vitals | `devops/observability.mdc`, `runtime/build-output.mdc` | LCP/INP/CLS Good 임계값 (p75) |

## 프로세스·품질

| 자료 | URL | PVC 반영 위치 | 참고 범위 |
|------|-----|---------------|-----------|
| Conventional Commits 1.0.0 | https://www.conventionalcommits.org/en/v1.0.0/ | `devops/git-workflow.mdc` | 커밋 형식 |
| GitHub Flow | https://docs.github.com/en/get-started/using-github/github-flow | `devops/git-workflow.mdc` | 기본 브랜치 전략 |
| Semantic Versioning 2.0.0 | https://semver.org/ | `devops/git-workflow.mdc` | 버전 의미 |
| Twelve-Factor App | https://12factor.net/ | `devops/ci-cd.mdc`, `runtime/platform-targets.mdc` | 설정·환경 패리티 |
| Martin Fowler TestPyramid | https://martinfowler.com/bliki/TestPyramid.html | `architecture/testing-quality.mdc` | 테스트 계층 |
| WCAG 2.2 | https://www.w3.org/TR/WCAG22/ | `design/accessibility.mdc`, `patterns/form-handling.mdc` | 접근성 |

## 적용하지 않은 것

- 특정 병원·공공기관 전용 업무 규정 (범용 초석 유지)
- 특정 상용 스택(Next/Vercel 등) 강제 — `project-context` 예시로만 안내
- 외부 Skill 저장소 전체 미러링 — `core/03-skill-and-reference-governance.mdc` 절차로 필요 시만
