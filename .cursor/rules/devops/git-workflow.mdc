---
description: "Git 브랜치·커밋·PR 규칙. Conventional Commits와 GitHub Flow를 기본으로 한다."
alwaysApply: true
---

# Git 워크플로

## 1. 기본 브랜치 전략

기본값은 **GitHub Flow**다. (`main`은 항상 배포 가능)

```text
main  ←  PR(리뷰·CI)  ←  feature|fix|chore|docs/<요약>
```

예약된 릴리스 주기가 긴 제품만 Git Flow류(`develop` / `release` / `hotfix`)를 `project-context`에 명시해 쓴다.  
명시가 없으면 GitHub Flow를 따른다.

## 2. 브랜치 이름

- `feature/<요약>`, `fix/<요약>`, `chore/<요약>`, `docs/<요약>`, `hotfix/<요약>`
- 공백·비밀값·이슈 본문 전체를 이름에 넣지 않는다.

## 3. 커밋 메시지 (Conventional Commits 1.0.0)

```text
<type>[optional scope]: <description>

[optional body]

[optional footer(s)]
```

- 필수 유형: `feat`, `fix`
- 권장: `docs`, `style`, `refactor`, `perf`, `test`, `build`, `ci`, `chore`, `revert`
- Breaking change: `type!:` 또는 footer `BREAKING CHANGE:`
- 설명은 현재형·간결. 언어는 `project-context`의 Code Language를 따른다. (미기재 시 영어 권장)

## 4. PR·머지 조건

- PR 설명에 목적·변경 요약·검증 방법·리스크를 적는다.
- CI(빌드·테스트·린트) 통과 전 머지하지 않는다. (프로젝트에 CI가 있으면)
- `main` 직접 푸시는 피하고, 보호 규칙이 있으면 준수한다.
- 강제 푸시·히스토리 재작성은 공유 브랜치에서 금지. 사용자 명시 요청만 예외.
- 시크릿·대용량 바이너리·생성물 디렉터리를 커밋하지 않는다.

## Sources

- Conventional Commits 1.0.0 — https://www.conventionalcommits.org/en/v1.0.0/
- GitHub Flow — https://docs.github.com/en/get-started/using-github/github-flow
- Semantic Versioning 2.0.0 — https://semver.org/
- 확인일: 2026-07-30
