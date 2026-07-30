---
description: "코드 구조·모듈·명명, API 응답 envelope, HTTP 상태·에러 처리, 웹 표준·성능."
alwaysApply: true
---

# 코드 구조 및 API·웹 구현 기준

## 1. 모듈·폴더·관심사 분리

- UI 표현, 상태 관리, 비즈니스 규칙, 데이터 접근, 외부 API 연동, 유틸리티, 설정, 테스트를 명확히 분리한다.
- 하나의 파일이나 함수가 여러 책임을 과도하게 맡지 않도록 한다.
- 공통 로직은 검증 후 재사용 가능한 모듈, 컴포넌트, 유틸리티 또는 서비스로 분리한다.
- 페이지별 구현에 공통 스타일, 공통 데이터 로직, 공통 비즈니스 규칙을 중복 작성하지 않는다.
- 기존 프로젝트의 파일 구조, 명명 규칙, 모듈 경계, 의존성 방향을 우선 존중한다.
- 구조 변경이 필요한 경우에는 기존 구조의 문제점, 변경 범위, 영향도, 마이그레이션 방법을 먼저 보고하고 승인을 받는다.

## 2. API 응답 계약

프로젝트에 기존 envelope가 있으면 **그것을 최우선**한다.  
신규 API이고 관례가 없으면 아래 중 하나를 프로젝트 표준으로 채택해 `project-context` / OpenAPI에 고정한다.

### 2.1 성공 응답 (권장 envelope)

```json
{
  "data": {},
  "meta": {}
}
```

- `data`: 본문 리소스 또는 목록
- `meta`: 페이지네이션, 요청 ID, 서버 시각 등 부가 정보 (없으면 생략 가능)
- 목록은 `data` + `meta.page` / `meta.total` 등으로 일관되게

### 2.2 오류 응답 (IETF RFC 9457 Problem Details 권장)

가능하면 `Content-Type: application/problem+json` 과 다음 필드를 사용한다.

```json
{
  "type": "https://example.com/problems/out-of-credit",
  "title": "You do not have enough credit.",
  "status": 403,
  "detail": "Your current balance is 30, but that costs 50.",
  "instance": "/account/1234/msgs/abc"
}
```

- `type`, `title`, `status`, `detail`, `instance` 의미를 RFC 9457에 맞게 유지한다.
- 레거시 `{ "error": { "code", "message" } }` 가 이미 있으면 혼용하지 말고 문서화 후 점진 이관한다.
- 내부 스택·SQL·시크릿을 클라이언트 error body에 넣지 않는다.

### 2.3 HTTP 상태 코드 (RFC 9110 관행)

| 상황 | 코드 예 |
|------|---------|
| 성공·생성 | 200, 201, 204 |
| 잘못된 요청·검증 실패 | 400 |
| 미인증 | 401 |
| 권한 없음 | 403 |
| 없음 | 404 |
| 충돌·중복 | 409 |
| 검증 실패(도메인) | 422 (프로젝트에서 사용할 때만 일관 적용) |
| 과도한 요청 | 429 |
| 서버 오류 | 500, 503 |

상태 코드와 body의 `status`/`code`가 모순되지 않게 한다.

## 3. 에러 처리 전략

- **전역/경계 핸들러**에서 미처리 예외를 사용자용 메시지와 로그용 상세로 분리한다.
- 도메인 예측 가능 오류는 예외 남발보다 명시적 결과 타입·Problem Details를 선호할 수 있다.
- 프레임워크 기본 에러 페이지·JSON 형식이 있으면 그것을 확장한다. 페이지마다 다른 형식 금지.
- 재시도 가능한 오류와 불가능한 오류를 구분한다.

## 4. 표준 기반 웹 구현

- 국제 웹 표준, 브라우저 호환성, 시맨틱 HTML, CSS 표준, 표준 JavaScript API를 우선 사용한다.
- 브라우저 또는 프레임워크에 과도하게 종속되는 구현은 필요한 근거가 있을 때만 도입한다.
- 레이아웃은 CSS Grid와 Flexbox를 적절히 사용한다.
- 화면 크기·기기·업무 흐름 기준으로 폭·열·간격·터치 영역을 설계한다.

## 5. 성능 기준

- 초기 화면에 필요한 코드와 자산만 우선 로드한다.
- 번들·이미지·폰트를 불필요하게 키우지 않는다. (`runtime/build-output`, `devops/observability` 참고)
- 반복 렌더링, 불필요한 API 호출, 중복 이벤트, 메모리 누수를 점검한다.
- 최적화는 측정 근거가 있을 때만 한다.

## Sources

- RFC 9457 Problem Details for HTTP APIs — https://www.rfc-editor.org/rfc/rfc9457.html
- RFC 9110 HTTP Semantics — https://www.rfc-editor.org/rfc/rfc9110
- 확인일: 2026-07-30
