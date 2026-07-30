---
description: "관찰성·로그·에러 추적·Core Web Vitals 성능 예산."
alwaysApply: true
---

# 관찰성 및 성능 예산

## 1. 로그

레벨 권장:

| 레벨 | 사용 |
|------|------|
| error | 실패·즉시 대응 필요 |
| warn | 성능 저하·재시도·비정상이나 서비스 유지 |
| info | 비즈니스·배포·중요 상태 전환 |
| debug | 개발·임시 진단 (운영 기본 off) |

- 구조화 로그(JSON 등)를 선호한다.
- 요청 상관 ID를 전파해 추적 가능하게 한다.
- 비밀·비밀번호·토큰·주민/카드 등 민감정보를 로그에 넣지 않는다. (OWASP Logging)

## 2. 에러 추적

- 처리되지 않은 예외·서버 5xx·클라이언트 fatal은 집계 가능해야 한다. (Sentry 등 도구는 프로젝트 선택)
- 사용자 메시지와 내부 진단 정보를 분리한다.
- “임시로 catch해서 무시”로 완료 처리하지 않는다.

## 3. Core Web Vitals 예산 (웹 UI)

Google Web Vitals 권장 “Good” 기준을 기본 예산으로 삼는다. (필드 75th percentile)

| 지표 | Good |
|------|------|
| LCP | ≤ 2.5s |
| INP | ≤ 200ms |
| CLS | ≤ 0.1 |

- 프로젝트별 더 엄격한 예산은 `project-context`에 적는다.
- 측정: CrUX / PageSpeed Insights / Lab(Lighthouse) + 가능하면 RUM
- 성능 최적화는 측정 근거 없이 추측으로 하지 않는다.

## 4. 운영 알림

- 단순 CPU만이 아니라 **사용자 영향**(오류율, 지연, 핵심 API 실패) 중심으로 알린다.
- 알림 피로를 줄이기 위해 임계값·억제를 문서화한다.

## Sources

- web.dev Web Vitals — https://web.dev/articles/vitals (updated 2024-10-31)
- Core Web Vitals thresholds — https://web.dev/articles/defining-core-web-vitals-thresholds
- OWASP Logging Cheat Sheet — https://cheatsheetseries.owasp.org/cheatsheets/Logging_Cheat_Sheet.html
- 확인일: 2026-07-30
