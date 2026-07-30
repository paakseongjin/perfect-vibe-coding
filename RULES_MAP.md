.cursor/
└── rules/
    ├── core/
    │   ├── 00-development-governance.mdc           # 전역 헌장
    │   ├── 01-safe-work-protocol.mdc               # 작업 전·중·후 세부 절차
    │   ├── 02-token-efficiency.mdc                 # 토큰·컨텍스트 윈도우 효율
    │   └── 03-skill-and-reference-governance.mdc   # 외부 Skill·레퍼런스·MDC 생성
    ├── architecture/
    │   ├── code-structure.mdc                      # 구조·API envelope·HTTP·에러
    │   ├── data-integrity.mdc                      # DB·API·연동 보호
    │   └── testing-quality.mdc                     # 테스트 피라미드·커버리지·검증
    ├── security/
    │   ├── auth.mdc                                # 인증·세션·토큰 저장
    │   ├── input-validation.mdc                    # XSS·CSRF·인젝션·업로드
    │   └── secret-management.mdc                   # 시크릿·env·스캔
    ├── devops/
    │   ├── git-workflow.mdc                        # 브랜치·Conventional Commits·PR
    │   ├── ci-cd.mdc                               # 환경 분리·게이트·롤백
    │   └── observability.mdc                       # 로그·에러추적·Web Vitals
    ├── runtime/
    │   ├── platform-targets.mdc                    # 런타임·브라우저·폴리필
    │   ├── dependency-policy.mdc                   # 패키지·라이선스·audit
    │   └── build-output.mdc                        # 번들 예산·산출물
    ├── patterns/
    │   ├── async-patterns.mdc                      # async 상태·레이스·재시도
    │   ├── form-handling.mdc                       # 폼 검증·접근성·제출
    │   └── caching-strategy.mdc                    # 클라이언트·HTTP·CDN 캐시
    ├── design/
    │   ├── design-system.mdc                       # 토큰·컴포넌트
    │   ├── typography-korean.mdc                   # 한글 타이포그래피
    │   └── accessibility.mdc                       # WCAG·키보드·포커스
    ├── docs/
    │   ├── codemap-maintenance.mdc                 # CODEMAP 갱신
    │   └── documentation-standard.mdc              # 문서 템플릿
    └── project/
        └── project-context.mdc                     # 프로젝트별 고정 스펙

docs/
└── references/
    └── SOURCES.md                                  # 공인 출처·적용 범위 기록
