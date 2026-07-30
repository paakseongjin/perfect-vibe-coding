---
description: "빌드 산출물·번들 예산·트리쉐이킹·배포 아티팩트 검증."
alwaysApply: true
---

# 빌드 산출물 및 번들 예산

## 1. 산출물 원칙

- 빌드 결과물(`dist`, `.next`, `build` 등)을 소스 진실로 커밋하지 않는다. (예외는 명시적 정책)
- 프로덕션 빌드는 최소화·트리쉐이킹·죽은 코드 제거가 켜진 구성을 기본으로 한다.
- 소스맵은 운영 노출 정책을 `project-context`에 맞게 결정한다. 공개 소스맵에 비밀이 없어야 한다.

## 2. 예산

`project-context`의 Performance Budget이 최우선이다. 예(웹):

- 초기 JS gzip 대략 상한 (프로젝트 기입)
- 이미지·폰트 용량 상한
- Core Web Vitals Good 구간 유지 (observability 규칙)

예산을 넘는 변경은:

1. 측정으로 확인
2. 원인(중복 의존성, 과다 클라이언트 컴포넌트, 미압축 자산 등) 보고
3. 승인 또는 최적화 후 진행

## 3. 검증

- CI에서 프로덕션 빌드가 통과해야 한다.
- 가능하면 번들 분석(예: bundler analyzer)으로 회귀를 감지한다.
- 미사용 CSS/JS·과대 폴리필·전체 라이브러리 import를 피한다. (`import { x }` / 경로 import)

## 4. 정적 자산

- 캐시 버스터·해시 파일명을 빌드 파이프라인에 맡긴다.
- 원본 대용량 미디어를 그대로 배포하지 않는다. 적절한 포맷·해상도·lazy load.

## Sources

- web.dev Web Vitals / performance guidance — https://web.dev/articles/vitals
- MDN Performance — https://developer.mozilla.org/en-US/docs/Web/Performance
- 확인일: 2026-07-30
