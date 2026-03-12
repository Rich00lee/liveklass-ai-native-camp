# LiveKlass AI Native Camp

> 2주 후, 당신의 업무 방식은 영구적으로 바뀐다.

비개발자를 위한 Claude Code 사내 워크숍. 2주간 총 5세션 — 학습 4회 + 사내 발표 1회.

AI Native Camp 1기(2026-02-14, Naver D2SF)에서 영감을 받아, LiveKlass 실무에 맞게 재설계 한 척 했습니다.
https://github.com/ai-native-camp/camp-1 의 순도 99.99% 카피캣 임을 알립니다

## 캠프 현황

**1기 진행 중** (2026-03-03 ~ 03-14) | 참가자 9명 (일반 7 + 앰버서더 2)

| 날짜 | 세션 | 시간 | 장소 | 상태 |
|------|------|------|------|------|
| 3/3 (화) | Session 1 — 설치 + 핵심 기능 체험 | 20:00~22:00 | 헤이그라운드 세미나실 | ✅ 완료 |
| 3/5 (목) | Session 2 — GitHub로 내 설정 관리하기 | 20:00~22:00 | 온/오프라인 | ✅ 완료 |
| 3/9 (월) | Session 3 — 업무 도구 연결 + Context Sync | 20:00~22:00 | 온/오프라인 | ✅ 완료 |
| 3/10 (화) | Session 4 — 산출물 PR 제출 + 피어리뷰 | 20:00~22:00 | 온/오프라인 | 예정 (오늘) |
| 3/13 (금) | Session 5 — 사내 공유회 | 10:15~11:45 | 온/오프라인 | 예정 |

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
| 2회차 | `session2-github` | GitHub로 내 설정 관리하기 | Private repo + 동기화 루틴 |
| 3회차 | `session3-tools` | 업무 도구 연결 + Context Sync | `/my-context-sync` 스킬 완성 |
| 4회차 | `session4-pr-showcase` | 산출물 PR 제출 + 피어리뷰 | SHOWCASE.md + PR + 리뷰 |
| 5회차 | `session5-showcase` | 사내 공유회 | 발표 + 패널토크 |

```
.claude/skills/
├── session1-onboarding/     # 설치 + 핵심 기능 체험
├── session2-github/         # GitHub로 내 설정 관리하기
├── session3-tools/          # 업무 도구 연결 + Context Sync
├── session4-pr-showcase/    # 산출물 PR 제출 + 피어리뷰
└── session5-showcase/       # 사내 공유회
```

## 참가자

**일반 (7명)**: 김태윤, 김성원, 이보배(Vivi), 최재훈(Terry), 이새봄, 아린, 정영현(Jay)
**앰버서더 (2명)**: 김영호(Ian), 송상수(Eddie)

## 실전 결과물

워크숍이 끝나면 각자 손에 들고 가는 것들:

- 나만의 업무 자동화 시스템 1개
- GitHub 레포지토리
- 커스텀 스킬/워크플로우
- 병렬 에이전트 운용 경험
- 사내 발표 경험

수료가 아니라 시작이다. 각자가 자신의 업무를 AI로 자동화하는 주체가 된다.
