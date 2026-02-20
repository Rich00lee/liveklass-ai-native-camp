# LiveKlass AI Native Camp

> 2주 후, 당신의 업무 방식은 영구적으로 바뀐다.

비개발자를 위한 Claude Code 사내 워크숍. 2주간 총 5세션 — 학습 4회 + 사내 발표 1회.

AI Native Camp 1기(2026-02-14, Naver D2SF)에서 영감을 받아, LiveKlass 실무에 맞게 재설계 한 척 했습니다.
https://github.com/ai-native-camp/camp-1 의 순도 99.99% 카피캣 임을 알립니다

## 일정

| 날짜 | 세션 | 시간 | 장소 |
|------|------|------|------|
| 3/3 (화) | Session 1 — 설치 + 핵심 기능 체험 | 20:00~22:00 | 헤이그라운드 세미나실 |
| 3/5 (목) | Session 2 — 업무 도구 연결 | 20:00~22:00 | 온/오프라인 |
| 3/9 (월) | Session 3 — 나만의 업무 자동화 만들기 | 20:00~22:00 | 온/오프라인 |
| 3/10 (화) | Session 4 — 자동화 고도화 + 발표 준비 | 20:00~22:00 | 온/오프라인 |
| 3/14 (토) | Session 5 — 사내 발표 | 시간 별도 안내 | 오프라인 |

## 지원하기

👥 **최대 5명** | 코딩 경험 불필요 | 마감: 2/21(토) 자정

👉 [지원서 작성하기](https://futureschole.notion.site/30cc7a52db4f810b99d7e703ea841cf6?pvs=105)

> 개발자 분은 **앰버서더**로 지원할 수 있습니다 (동일 링크, "앰버서더" 선택)

## Skills as Curriculum

이 워크숍의 커리큘럼은 **Claude Code Skills 그 자체**다.

슬라이드를 넘기며 듣는 강의가 아니다. `/session1-onboarding`을 실행하면 Claude가 직접 가르치고, 질문하고, 실습을 안내한다. 매 세션 새로운 Skill이 열리고, 어제 배운 것 위에 오늘을 쌓는다.

### 설치

```bash
npx skills add liveklass/liveklass-ai-native-camp --agent claude-code --yes
```

이 한 줄이면 모든 커리큘럼 스킬이 Claude Code에 설치됩니다. 특정 세션만 설치하려면:

```bash
# 1회차만 설치
npx skills add liveklass/liveklass-ai-native-camp --skill session1-onboarding --agent claude-code --yes
```

> 설치 후 Claude Code에서 `/session1-onboarding`으로 시작하세요.

## 커리큘럼

| 세션 | Skill | 주제 | 결과물 |
|------|-------|------|--------|
| 1회차 | `session1-onboarding` | Claude Code 설치 + 핵심 기능 체험 | CLAUDE.md, 첫 Skill 실행 |
| 2회차 | `session2-tools` | 업무 도구 연결 — Slack, Notion, Google Sheets | `/my-context-sync` 스킬 완성 |
| 3회차 | `session3-automation` | 나만의 업무 자동화 기획 → 제작 → 테스트 | 자동화 시스템 1개 |
| 4회차 | `session4-polish` | 자동화 고도화 + 발표 준비 | GitHub 레포 + 발표 자료 |
| 5회차 | `session5-showcase` | 사내 발표 + 팀 확산 전략 | 데모 발표 |

```
.claude/skills/
├── session1-onboarding/     # 설치 + 핵심 기능 체험
├── session2-tools/          # Slack, Notion, 구글시트 연결
├── session3-automation/     # 나만의 업무 자동화 만들기
├── session4-polish/         # 자동화 고도화 + 발표 준비
└── session5-showcase/       # 사내 발표 + 팀 확산 전략
```

## 참가 대상

- **핵심**: 세일즈, 운영, CS 등 실무 비개발자 (최대 5명)
- **앰버서더**: 개발자 — 기술 서포트 + 팀 내 확산 역할

## 실전 결과물

워크숍이 끝나면 각자 손에 들고 가는 것들:

- 나만의 업무 자동화 시스템 1개
- GitHub 레포지토리
- 커스텀 스킬/워크플로우
- 병렬 에이전트 운용 경험
- 사내 발표 경험

수료가 아니라 시작이다. 각자가 자신의 업무를 AI로 자동화하는 주체가 된다.
