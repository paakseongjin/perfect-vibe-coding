---
description: "인증·세션·토큰 저장 기준. OWASP ASVS/Cheat Sheet와 NIST SP 800-63B를 프로젝트에 맞게 적용한다."
alwaysApply: true
---

# 인증 및 세션 관리

## 1. 선택 원칙

인증 방식은 유행이 아니라 **위협 모델·운영 환경·클라이언트 종류**로 고른다.

| 방식 | 적합한 경우 | 주의 |
|------|-------------|------|
| 서버 세션 + Cookie | 브라우저 중심 웹앱, 즉시 폐기·서버 통제가 중요할 때 | CSRF 방어, 세션 고정 방지 필수 |
| OAuth 2.1 / OIDC | 외부 IdP, 다중 클라이언트, SSO | 리다이렉트 URI·스코프·PKCE 검증 |
| JWT(액세스) + Refresh | SPA/모바일 API, 수평 확장 | 액세스 토큰 단기화, 폐기·회전 전략 필수 |
| API Key / mTLS | 서버 간·기기 간 연동 | 사용자 로그인 대체로 쓰지 않음 |

프로젝트에 이미 확정된 방식이 있으면 **임의로 교체하지 않는다**. 변경은 승인 후다.

## 2. 토큰·세션 저장

- 브라우저에서 액세스/리프레시 토큰을 `localStorage` / `sessionStorage`에 두지 않는다. XSS 시 탈취된다.
- 웹 클라이언트는 기본적으로 **`HttpOnly` + `Secure` + 적절한 `SameSite` Cookie** 로 세션 또는 리프레시 토큰을 전달한다. (OWASP Session Management Cheat Sheet)
- JavaScript가 읽을 수 있는 저장소에 장기 비밀을 두지 않는다.
- 액세스 토큰은 짧게, 리프레시는 회전(rotation)·재사용 감지·서버 측 폐기 목록을 고려한다.
- 인증 성공·재인증 시 **새 세션 식별자를 발급**하고 이전 것을 무효화한다. (세션 고정 방지, OWASP ASVS V7)

## 3. 전송·만료·권한

- 인증·세션 교환은 TLS(HTTPS) 전 구간에서만 수행한다. HSTS 사용을 권장한다.
- Idle / Absolute 타임아웃을 `project-context`에 명시하고 서버에서 강제한다.
- 로그아웃·권한 변경·비밀번호 변경 시 관련 세션·리프레시를 무효화한다.
- 인가(Authorization)는 인증과 분리한다. “로그인됨”만으로 민감 자원에 접근시키지 않는다.
- 비밀번호(memorized secret)는 서버에 평문 저장 금지. 적합한 KDF·솔트 사용. (NIST SP 800-63B)

## 4. 구현 시 필수 확인

- CSRF: Cookie 기반 세션이면 SameSite 및/또는 anti-CSRF 토큰
- CORS: 자격 증명 허용 시 Origin 화이트리스트
- 오류 메시지: 사용자 열거를 과도하게 돕지 않음
- 관리자·고권한 작업: 재인증 또는 step-up 검토

## Sources

- OWASP Session Management Cheat Sheet — https://cheatsheetseries.owasp.org/cheatsheets/Session_Management_Cheat_Sheet.html
- OWASP ASVS V7 Session Management — https://asvs.dev/v5.0.0/V7-Session-Management/
- OWASP Authentication Cheat Sheet — https://cheatsheetseries.owasp.org/cheatsheets/Authentication_Cheat_Sheet.html
- NIST SP 800-63B-4 — https://doi.org/10.6028/NIST.SP.800-63B-4
- 확인일: 2026-07-30
- 적용 방식: 원칙·체크리스트만 PVC에 맞게 변환. 특정 IdP/프레임워크 코드는 복사하지 않음.
