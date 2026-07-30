---
description: "비동기·로딩·에러·성공 상태 처리의 표준 패턴."
alwaysApply: true
---

# 비동기 처리 패턴

## 1. 제어 흐름

- 신규 코드는 `async/await`를 기본으로 하고, 에러는 `try/catch` 또는 호출부 계약으로 처리한다.
- Promise를 fire-and-forget 하지 않는다. 의도적 백그라운드 작업은 실패 로깅·재시도 정책을 명시한다.
- 병렬은 `Promise.all` / `allSettled`를 구분해 쓴다. 하나 실패 시 전체 중단이 맞는지 먼저 판단한다.
- 취소 가능한 작업은 `AbortController` 등 플랫폼 표준을 우선한다.

## 2. UI 상태 모델

비동기 UI는 최소 다음 상태를 구분한다.

```text
idle | loading | success | error
```

- 로딩 중 중복 제출을 막는다. (버튼 disable, in-flight 가드)
- 에러는 사용자 메시지 + 재시도/복구 경로를 제공한다. 빈 화면·무반응 금지.
- 성공 후 캐시·목록·상세 일관성을 갱신한다.
- 레이스: 늦은 응답이 최신 UI를 덮어쓰지 않게 요청 순서/ID를 관리한다.

## 3. 서버·API

- 타임아웃·재시도는 멱등성 있는 요청에만 공격적으로 적용한다.
- 부분 실패를 숨기지 않는다.
- 상위로 전파할 예외와 도메인 에러 타입을 구분한다.

## 4. 금지

- 빈 `catch`로 삼키기
- 로딩 없이 긴 대기
- 에러를 `any`로 캐스팅해 상세 유실
- UI 스레드를 막는 동기 대량 연산 (가능하면 분할·워커)

## Sources

- MDN Promise / AbortController — https://developer.mozilla.org/
- 확인일: 2026-07-30
