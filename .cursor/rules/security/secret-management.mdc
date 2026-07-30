---
description: "비밀값·환경변수·키 관리. 저장소·로그·클라이언트 번들 노출 금지."
alwaysApply: true
---

# 시크릿 및 환경 설정 관리

## 1. 절대 금지

- API 키, 비밀번호, 토큰, 인증서, 연결 문자열을 **소스코드·커밋·이슈·PR·스크린샷**에 넣지 않는다.
- 클라이언트 번들·공개 환경 변수에 서버 전용 비밀을 넣지 않는다. (`NEXT_PUBLIC_*`, `VITE_*` 등 공개 접두사는 공개로 간주)
- 로그·에러 응답·텔레메트리에 비밀·개인식별·세션 원문을 남기지 않는다.
- `.env` 실파일을 저장소에 커밋하지 않는다. `.env.example`에는 **이름과 더미 값만**.

## 2. 관리 방식

- 로컬: `.env` / 시크릿 매니저 + `.gitignore`
- 공유 환경: 플랫폼 시크릿 스토어, CI secrets, Vault 등 **프로젝트에 정한 한 곳**
- 시크릿은 최소 권한·회전(rotation) 가능하게 설계한다.
- 유출 의심 시 즉시 회전하고 영향 범위를 보고한다.

## 3. 코드 패턴

- 설정은 부팅 시 한 곳에서 로드·검증한다. 누락 시 빠르게 실패(fail fast).
- `process.env` / 동등 API를 파일 곳곳에 흩뿌리지 않는다.
- 기본값에 실운영 비밀을 넣지 않는다.
- 예시·테스트 픽스처에는 가짜 값만 사용한다.

## 4. 저장소 방어

- pre-commit / CI에 시크릿 스캔(gitleaks, trufflehog, GitHub secret scanning 등)을 권장한다.
- 실수로 커밋된 비밀은 “커밋 삭제만”으로 끝나지 않는다. **키 자체를 폐기·재발급**한다.

## Sources

- OWASP Secrets Management Cheat Sheet — https://cheatsheetseries.owasp.org/cheatsheets/Secrets_Management_Cheat_Sheet.html
- OWASP Logging Cheat Sheet — https://cheatsheetseries.owasp.org/cheatsheets/Logging_Cheat_Sheet.html
- NIST SP 800-63B-4 (authenticator/secret handling principles) — https://doi.org/10.6028/NIST.SP.800-63B-4
- 확인일: 2026-07-30
