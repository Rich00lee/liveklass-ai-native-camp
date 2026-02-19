# LiveKlass AI Native Camp

> 4세션 후, 당신의 업무 방식은 영구적으로 바뀐다.

비개발자를 위한 Claude Code 사내 워크숍. 2주간 주 2회, 회당 1.5시간 (총 4세션).

AI Native Camp 1기(2026-02-14, Naver D2SF)에서 영감을 받아, LiveKlass 실무에 맞게 재설계했습니다.

## 설치

```bash
npx skills add liveklass/liveklass-ai-native-camp --agent claude-code --yes
```

이 한 줄이면 모든 커리큘럼 스킬이 Claude Code에 설치됩니다. 특정 세션만 설치하려면:

```bash
# 1회차만 설치
npx skills add liveklass/liveklass-ai-native-camp --skill session1-onboarding --agent claude-code --yes
```

> 설치 후 Claude Code에서 `/session1-onboarding`으로 시작하세요.

## Skills as Curriculum

이 워크숍의 커리큘럼은 **Claude Code Skills 그 자체**다.

슬라이드를 넘기며 듣는 강의가 아니다. `/session1-onboarding`을 실행하면 Claude가 직접 가르치고, 질문하고, 실습을 안내한다. 매 세션 새로운 Skill이 열리고, 어제 배운 것 위에 오늘을 쌓는다.

```
.claude/skills/
├── session1-onboarding/     # 설치 + 7개 핵심 기능 체험
├── session2-tools/          # Slack, Notion, 구글시트 연결
├── session3-automation/     # 나만의 업무 자동화 만들기
└── session4-showcase/       # 결과 공유 + 다음 스텝
```

## 커리큘럼

| 세션 | Skill | 주제 |
|------|-------|------|
| 1회차 | `session1-onboarding` | Claude Code 설치 + 핵심 기능 체험 (CLAUDE.md, Skill, MCP, Subagent) |
| 2회차 | `session2-tools` | 업무 도구 연결 — Slack, Notion, Google Sheets MCP 설정 |
| 3회차 | `session3-automation` | 나만의 업무 자동화 기획 → 제작 → 테스트 |
| 4회차 | `session4-showcase` | 결과 공유 데모 + 팀 확산 전략 논의 |

## 참가 대상

- **핵심**: 세일즈, 운영, CS 등 실무 비개발자 (최대 5명)
- **앰버서더**: 개발자 — 기술 서포트 + 팀 내 확산 역할

## 워크숍이 끝나면

수료가 아니라 시작이다. 각자가 자신의 업무를 AI로 자동화하는 주체가 된다.
