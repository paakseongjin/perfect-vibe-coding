---
description: "클라이언트·API·정적 자산 캐시 전략과 무효화 원칙."
alwaysApply: true
---

# 캐싱 전략

## 1. 계층

| 계층 | 예 | 주의 |
|------|----|------|
| 메모리/클라이언트 상태 | 쿼리 캐시, UI 스토어 | 개인정보·권한 바운더리 |
| HTTP 캐시 | Cache-Control, ETag | 인증된 응답 공유 캐시 금지 |
| CDN / 정적 자산 | 해시 파일명, long-cache | HTML과 해시 자산 정책 분리 |
| 서버/데이터 | Redis 등 | TTL·무효화·스탬피드 |

## 2. 기본 규칙

- **정합성 > 미세 성능**. 잘못된 캐시가 권한·결제·재고를 어기면 안 된다.
- 캐시 키에 사용자·테넌트·권한 범위를 포함한다. 키가 짧다고 공유하지 않는다.
- 변경 후 무효화 또는 TTL 전략을 함께 설계한다. “넣기만 하고 안 지움” 금지.
- `Cache-Control: private` vs `public`을 인증 여부에 맞게 고른다.

## 3. 웹 클라이언트

- 정적 자산: 내용 해시 + 장기 캐시가 이상적이다.
- API GET: 신선도가 중요한 자원은 short TTL 또는 revalidate.
- 뮤테이션 후 관련 목록/상세 캐시를 갱신하거나 무효화한다. (`async-patterns`와 연계)

## 4. 금지

- 비밀·토큰을 캐시 레이어에 평문 장기 저장
- 다른 사용자 응답을 공유 CDN에 캐시
- 무효화 없는 영구 캐시로 비즈니스 상태 표현

## Sources

- HTTP Caching (MDN / Fetch Semantics) — https://developer.mozilla.org/en-US/docs/Web/HTTP/Caching
- RFC 9111 HTTP Caching — https://www.rfc-editor.org/rfc/rfc9111
- 확인일: 2026-07-30
