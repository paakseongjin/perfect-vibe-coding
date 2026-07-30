---
description: "폼 검증·제출·에러 피드백·접근성 표준 패턴."
alwaysApply: true
---

# 폼 처리 패턴

## 1. 검증 계층

1. **필드 단위**: 형식·필수·길이 (즉시 또는 blur)
2. **폼 단위**: 교차 필드 규칙
3. **서버 단위**: 최종 진실 (보안·비즈니스)

클라이언트만 통과한 데이터를 신뢰하지 않는다. (`security/input-validation`과 동일)

## 2. UX·접근성

- `label`과 컨트롤을 연결한다. placeholder만으로 라벨을 대체하지 않는다.
- 오류는 해당 필드 근처 + 요약(필요 시)으로 전달한다. 색상만으로 오류 표시 금지.
- `aria-invalid`, `aria-describedby`로 오류 메시지를 연결한다.
- 제출 중 중복 제출 방지, 성공/실패 피드백을 명확히 한다.
- 키보드만으로 모든 필드를 조작·제출할 수 있어야 한다.

## 3. 제출

- 클라이언트 검증 실패 시 서버로 보내지 않거나, 보내더라도 서버가 재검증한다.
- 네트워크 실패 시 입력값을 불필요하게 지우지 않는다.
- 멱등이 필요한 생성 API는 idempotency key 등 프로젝트 표준을 따른다.
- 파일 포함 폼은 업로드 규칙(`security/input-validation`)을 적용한다.

## 4. 구현 태도

- 프로젝트에 폼 라이브러리/패턴이 있으면 그것을 우선한다.
- 페이지마다 다른 검증·에러 UI 패턴을 만들지 않는다.
- 비밀번호·OTP 등 민감 필드는 자동완성·마스킹 정책을 존중한다.

## Sources

- W3C WCAG 2.2 (forms, error identification) — https://www.w3.org/TR/WCAG22/
- OWASP Input Validation Cheat Sheet — https://cheatsheetseries.owasp.org/cheatsheets/Input_Validation_Cheat_Sheet.html
- 확인일: 2026-07-30
