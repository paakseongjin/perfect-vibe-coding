# perfect-vibe-coding

Cursor용 전역 개발 거버넌스 규칙 세트입니다. 새 프로젝트의 `.cursor/rules/`에 복사해 재사용합니다.

## 구조

```
.cursor/
└── rules/
    ├── core/
    │   ├── 00-development-governance.mdc
    │   ├── 01-safe-work-protocol.mdc
    │   └── 02-token-efficiency.mdc
    ├── architecture/
    │   ├── code-structure.mdc
    │   ├── data-integrity.mdc
    │   └── testing-quality.mdc
    ├── design/
    │   ├── design-system.mdc
    │   ├── typography-korean.mdc
    │   └── accessibility.mdc
    ├── docs/
    │   ├── codemap-maintenance.mdc
    │   └── documentation-standard.mdc
    └── project/
        └── project-context.mdc
```

## 다른 프로젝트에 적용

1. 이 저장소의 `.cursor/rules/` 폴더를 대상 프로젝트로 복사합니다.
2. `project/project-context.mdc`를 해당 프로젝트의 기술 스택·업무 맥락으로 채웁니다.
3. 필요 없는 규칙은 삭제하거나 `alwaysApply` / 설명을 프로젝트에 맞게 조정합니다.

### 빠른 복사 (PowerShell)

```powershell
Copy-Item -Recurse -Force .\perfect-vibe-coding\.cursor\rules 경로\대상프로젝트\.cursor\
```

## 규칙 분배 요약

| 경로 | 내용 |
|------|------|
| `core/00-development-governance` | 헌장, 우선순위, 핵심 원칙, 금지·최종 기준 |
| `core/01-safe-work-protocol` | 작업 전·중·후 절차, 보고 형식, 중단 조건 |
| `core/02-token-efficiency` | 토큰·비용 효율 |
| `architecture/*` | 구조·웹 표준, 데이터/연동 보호, 검증 |
| `design/*` | 디자인 시스템, 한글 타이포, 접근성 |
| `docs/*` | CODEMAP·문서 표준 |
| `project/project-context` | 프로젝트별 맥락 템플릿 |
