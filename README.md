# LiveKlass AI Native Camp

> 2주 후, 당신 팀의 업무 방식은 영구적으로 바뀐다.

비개발자를 위한 Claude Code 워크숍 커리큘럼. 오픈소스(open-source).

## 이게 뭔가요?

코딩을 모르는 세일즈, 운영, 디자인, HR, CX 담당자가 **2주 5세션** 만에 자기 업무를 AI로 자동화하는 워크숍 커리큘럼입니다.

핵심 아이디어는 **Skills as Curriculum** -- 슬라이드를 넘기며 듣는 강의가 아니라, Claude Code의 Skill을 실행하면 AI가 직접 가르치고, 실습을 안내하고, 퀴즈를 냅니다. 매 세션 새로운 Skill이 열리고, 어제 배운 것 위에 오늘을 쌓는 구조입니다.

[ai-native-camp/camp-1](https://github.com/ai-native-camp/camp-1) 커리큘럼을 기반으로 LiveKlass 실무 환경에 맞게 재설계했고, 1기 운영(2026-03-03 ~ 03-13, 9명 참가)을 거쳐 검증된 버전입니다.

## Quick Start

```bash
npx skills add liveklass/liveklass-ai-native-camp --agent claude-code --yes
```

설치가 끝나면 Claude Code에서 `/session1-onboarding`을 실행하세요.

## 커리큘럼

| 세션 | Skill | 주제 | 결과물 |
|------|-------|------|--------|
| 1회차 | `session1-onboarding` | Claude Code 설치 + 핵심 기능 체험 | CLAUDE.md, 첫 Skill 실행 |
| 2회차 | `session2-github` | GitHub로 내 설정 관리하기 | Private repo + 동기화 루틴 |
| 3회차 | `session3-tools` | 업무 도구 연결 + Context Sync | `/my-context-sync` 스킬 완성 |
| 4회차 | `session4-pr-showcase` | 산출물 PR 제출 + 피어리뷰 | SHOWCASE.md + PR + 코드리뷰 |
| 5회차 | `session5-showcase` | 사내 공유회 | 발표 + 패널토크 |

## 실전 결과 -- 1기 참가자 산출물

8명이 2주 만에 만든 것들입니다.

| 참가자 | 직군 | 만든 것 | 효과 |
|--------|------|---------|------|
| Vivi | HR | 폰스크리닝 자동화 (일정 조율 + 인터뷰 기록지) | 1건당 30-40분 → 2-3분 |
| Ethan | 운영 | 거래처 사업자정보 자동 검증 | 412개 채널 전수 검증, 343건 불일치 발견 |
| Theo | 세일즈 | 로켓런칭 리드 자동 분석 (시트 → Notion → Slack) | "리드 분석해줘" 한 마디로 전체 파이프라인 실행 |
| Terry | CX | CX 어시스턴트 (상담 분류 + 유사케이스 검색 + 응대 초안) | 스크린샷 첨부만으로 4단계 자동 처리 |
| Arin | 디자인 | 디자인 요청 취합 에이전트 (Slack + Notion → Task 정리) | 주간 취합 30분 → 자동화 |
| Bom | 디자인 | 디자인 시스템 변경 알림 자동화 (Figma → Notion → Slack) | 수동 공유 단계 제거 |
| Jay | PM | PM 사양 설계 원툴화 (Notion → MD + HTML + Figma 동시 반영) | 4개 도구 수동 동기화 → 명령 한 줄 |
| Sangsu | 세일즈 | 강의 링크 → 리드마그넷 + 워크북 PDF 자동 생성 | 5단계 수작업 → 원스톱 |

## 디렉토리 구조

```
.claude/skills/        -- 5개 세션 스킬 (커리큘럼 본체) + 미사용 원안 2개 (참고용)
docs/slides/           -- 발표 자료
lk-ai-camp-showcase/   -- 참가자 산출물
RETROSPECTIVE.md       -- 캠프 회고
CAMP_PLAN.md           -- 운영 기획서 (참고용)
```

## 커스터마이징 가이드

이 커리큘럼을 포크(fork)해서 자기 조직에 맞게 쓸 수 있습니다.

1. **실습 예시 교체**: `.claude/skills/` 안의 각 SKILL.md에서 LiveKlass 업무 예시(CS 응답, Slack 요약 등)를 자기 회사 업무로 바꾸세요
2. **MCP 연결 조정**: Session 3에서 연결하는 도구(Notion, Google Sheets, Slack 등)를 자기 조직의 스택(stack)에 맞게 변경하세요
3. **STOP PROTOCOL 타이밍 조정**: 각 블록의 설명 분량과 실습 시간을 참가자 수준에 맞게 늘리거나 줄이세요. 비개발자 대상이라면 현재 설정을 유지하는 것을 권장합니다
4. **세션 수/일정**: 5세션이 기본이지만, 3-4회차를 합치거나 Session 5(공유회)를 별도 행사로 분리할 수 있습니다

## Credits

- **원본 커리큘럼**: [ai-native-camp/camp-1](https://github.com/ai-native-camp/camp-1) -- 장원준, 김성중, 정구봉
- **LiveKlass 적용 및 오픈소스 공개**: LiveKlass 팀
- **1기 참가자**: 김태윤, 김성원, 이보배(Vivi), 최재훈(Terry), 이새봄, 아린, 정영현(Jay), 김영호(Ian), 송상수(Eddie) -- 이 커리큘럼을 실제로 검증해준 분들

## License

MIT. `LICENSE` 파일을 참고하세요.
