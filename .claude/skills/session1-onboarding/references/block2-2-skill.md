> 공식 문서: https://docs.anthropic.com/ko/docs/claude-code/skills

## EXPLAIN

### Skill — 나만의 명령어 만들기

Skill은 자주 쓰는 작업을 **슬래시 명령어**로 저장하는 기능이다.

예: `/cs-reply` 치면 → CS 응답 초안을 자동으로 생성하는 절차가 실행됨.

**지금 이 워크숍도 Skill이다!**
- `/session1-onboarding` = 1회차 수업 전체가 Skill로 패키징된 것
- 누구든지 이 명령어 하나로 수업을 받을 수 있다

**LiveKlass 활용 예시**:
| Skill 이름 | 하는 일 |
|-----------|---------|
| `/cs-reply` | 고객 문의 → CS 응답 초안 생성 |
| `/pipeline-report` | 파이프라인 데이터 → 주간 리포트 |
| `/slack-summary` | Slack 메시지 → 액션 아이템 요약 |
| `/meeting-prep` | 고객사 정보 → 미팅 준비 체크리스트 |

**구조**:
```
.claude/skills/
└── cs-reply/
    └── SKILL.md    ← 여기에 절차를 적는다
```

Skill은 Session 3에서 직접 만들어볼 것이다. 지금은 "이런 게 있구나" 정도만.

## EXECUTE

지금 이미 설치된 Skill 목록을 확인해보세요:

Claude Code에 입력:
```
/
```
→ 슬래시 키를 치면 사용 가능한 Skill 목록이 나온다

보이는 Skill 이름을 하나 골라서 실행해보세요.

## QUIZ

AskUserQuestion으로 퀴즈 출제:

질문: "Skill의 가장 큰 장점은 무엇일까요?"
- "반복 작업 자동화" → ✅ 정답! "매번 긴 지시문을 입력할 필요 없이, 명령어 하나로 실행할 수 있어요."
- "다른 사람과 공유 가능" → ✅ 정답! "이 워크숍처럼, Skill을 파일로 저장하면 팀원 전체에게 배포할 수 있어요."
- "오류가 없다" → "정확도는 Claude 모델 성능에 달려 있어요. Skill의 장점은 '재사용성'이에요."
