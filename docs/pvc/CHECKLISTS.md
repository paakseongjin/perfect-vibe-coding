# PVC 체크리스트

## A. 적용 직후 (설치 스모크)

- [ ] `.cursor/rules/` · `.cursor/skills/` 가 프로젝트에 있다  
- [ ] `project-context.mdc`에 제품·금지·검사 명령이 있다  
- [ ] Cursor에서 Rules가 보인다  
- [ ] Agent에게 CODEMAP 초안만 요청해 봤다  
- [ ] (권장) `개발방향-설문.md` Quick 또는 Standard 답변을 준비했다  

## B. 위험도별 권장 깊이

| 모드 | 언제 | 권장 |
|------|------|------|
| Quick | 실험·단일 화면 | 설문 Quick 4문항 또는 project-context만 |
| Standard | MVP·실서비스 | 설문 전체 + CODEMAP |
| High Risk | 인증·결제·DB·배포·대규모 | 설문 + Feature Brief + 승인 |

## C. 적용 후 회고 (프로젝트 1건 끝날 때)

1. 설문/문서가 **너무 길어서** 미룬 적이 있었나?  
2. README **처음 10분**만으로 시작이 가능했나?  
3. 규칙이 **과하게** 붙거나 **부족**했던 순간은?  
4. `skill-router`가 도움이 됐나?  
5. 토큰·응답이 이전보다 가벼웠나?  

메모:

→ 반복되는 불편은 `docs/pvc/DECISIONS.md`에 남기고, 새 규칙 파일보다 **기존 파일 한 줄 수정**을 우선한다.
