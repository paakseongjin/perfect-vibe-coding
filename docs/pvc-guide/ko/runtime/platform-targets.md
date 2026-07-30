---
description: "지원 런타임·브라우저·OS·언어 버전과 폴리필 기준. 호환되지 않는 코드 생성을 막는다."
alwaysApply: true
---

# 플랫폼·런타임 타깃

## 1. 진실 공급원

지원 범위는 **`project-context.mdc`에 명시된 값**이 최우선이다.  
미기재 시 추측으로 최신 문법·실험 API를 쓰지 말고, 먼저 확인하거나 질문한다.

기록할 항목 예:

- 언어/런타임 버전 (예: Node, Bun, Deno, JVM, .NET, Python)
- 패키지 매니저·락파일
- 지원 브라우저 / OS / 모바일 버전
- SSR·CSR·네이티브 등 실행 모델

## 2. 브라우저·JS 기본 태도 (웹)

- Baseline / 공식 호환 표가 있으면 그것을 따른다.
- 필요 시에만 폴리필·트랜스파일한다. “만약을 위한” 전역 폴리필 남발 금지.
- 프로젝트 번들러·타깃(`browserslist`, `tsconfig.target` 등)과 어긋나는 문법을 넣지 않는다.

## 3. 서버·CLI

- 로컬과 CI·배포 런타임 메이저 버전을 맞춘다. (Twelve-Factor: Dev/Prod parity)
- OS별 경로·줄바꿈·권한 차이를 가정한다. 하드코딩된 절대 경로 지양.
- 네이티브 애드온·플랫폼 바이너리는 지원 OS를 문서화한다.

## 4. AI 구현 시

- 타깃 밖 API를 쓰기 전에 대안 또는 폴리필 필요 여부를 보고한다.
- “내 환경에서만” 되는 코드를 완료로 선언하지 않는다.

## Sources

- MDN Browser compatibility / Baseline — https://developer.mozilla.org/
- Twelve-Factor App (Dev/Prod parity) — https://12factor.net/dev-prod-parity
- 확인일: 2026-07-30
