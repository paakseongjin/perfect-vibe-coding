---
description: "입력 검증과 XSS·CSRF·인젝션·업로드 방어. OWASP Cheat Sheet / Top 10 기준."
alwaysApply: true
---

# 입력 검증 및 공격 표면 방어

## 1. 기본 원칙

- **모든 외부 입력은 신뢰하지 않는다.** 사용자 입력, 쿼리/바디, 헤더, 쿠키, 파일, 웹훅, 외부 API 응답 포함.
- 검증은 **서버(신뢰 경계)에서 필수**. 클라이언트 검증은 UX용이며 보안 통제로 치지 않는다.
- Allowlist(허용 목록)를 Denylist보다 우선한다.
- 출력 맥락에 맞는 인코딩/이스케이프를 적용한다. (HTML, URL, JS, CSS, SQL 바인딩)

## 2. 인젝션·XSS·CSRF

| 위협 | 최소 대응 |
|------|-----------|
| SQL/NoSQL Injection | 파라미터 바인딩·ORM 쿼리 빌더. 문자열 연결 쿼리 금지 |
| XSS | 템플릿 자동 이스케이프, 위험 HTML은 검증된 새니타이저, CSP 검토 |
| CSRF | Cookie 세션 시 SameSite + CSRF 토큰 또는 동등 통제 |
| Command/Path Injection | 셸 호출 최소화, 경로는 정규화·루트 밖으로 탈출 금지 |
| SSRF | 외부 URL fetch 시 허용 호스트·프로토콜 제한 |

참고: OWASP Top 10의 Injection / Broken Access Control / XSS 계열을 상시 위험으로 취급한다.

## 3. 파일 업로드

- 확장자만 믿지 말고 **콘텐츠 타입·매직 바이트·크기 상한**을 검사한다.
- 실행 가능 경로에 저장하지 않는다. 가능하면 객체 스토리지 + 비실행 ACL.
- 파일명은 사용자 원본을 그대로 쓰지 않고 서버 생성 식별자를 쓴다.
- 이미지/문서 처리는 검증된 라이브러리로 하고, 스크립트 가능 포맷은 정책으로 제한한다.

## 4. API·비즈니스 검증

- 스키마 검증(JSON Schema, Zod, class-validator 등 프로젝트 표준)을 경계에 둔다.
- 타입·범위·길이·형식·열거값을 명시한다.
- 권한 검사는 “이 자원에 대한 이 행위” 단위로 수행한다. IDOR 방지.
- 대량 요청·반복 시도에는 rate limit / lockout 정책을 `project-context`에 맞게 적용한다.

## 5. 실패 시 동작

- 검증 실패는 안전한 기본값(거부)으로 처리한다.
- 사용자에게는 이해 가능한 메시지, 로그에는 내부 상세(스택·쿼리)를 분리한다.
- 보안 이벤트(반복 실패, 권한 거부, 업로드 거부)는 관찰 가능하도록 남긴다.

## Sources

- OWASP Input Validation Cheat Sheet — https://cheatsheetseries.owasp.org/cheatsheets/Input_Validation_Cheat_Sheet.html
- OWASP XSS Prevention Cheat Sheet — https://cheatsheetseries.owasp.org/cheatsheets/Cross_Site_Scripting_Prevention_Cheat_Sheet.html
- OWASP CSRF Prevention Cheat Sheet — https://cheatsheetseries.owasp.org/cheatsheets/Cross-Site_Request_Forgery_Prevention_Cheat_Sheet.html
- OWASP File Upload Cheat Sheet — https://cheatsheetseries.owasp.org/cheatsheets/File_Upload_Cheat_Sheet.html
- OWASP Top 10 — https://owasp.org/www-project-top-ten/
- 확인일: 2026-07-30
