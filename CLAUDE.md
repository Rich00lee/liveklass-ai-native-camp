# CLAUDE.md

This file provides guidance to Claude Code when working with this repository.

## 프로젝트 개요

LiveKlass AI Native Camp — 비개발자를 위한 Claude Code 사내 워크숍 (5세션 × 1.5시간).
커리큘럼 자체가 Claude Code Skills로 구성되어 있다. 슬라이드가 아니라 `/session1-onboarding` 같은 Skill을 실행하면 Claude가 직접 가르친다.

## 참가 대상

- **핵심 대상**: 세일즈, 운영, CS 등 실무 비개발자 (최대 5명)
- **앰버서더**: 개발자 팀원 — 워크숍 후 팀 내 기술 서포트 역할

## 구조

```
.claude/skills/
├── session1-onboarding/     # 1회차: 설치 + 핵심 기능 체험
│   ├── SKILL.md
│   └── references/
├── session2-github/         # 2회차: GitHub로 내 설정 관리하기
│   ├── SKILL.md
│   └── references/
├── session3-tools/          # 3회차: 업무 도구 연결 + Context Sync (구 Session 2)
│   ├── SKILL.md
│   ├── references/
│   └── templates/
├── session4-pr-showcase/    # 4회차: 산출물 PR 제출 + 피어리뷰
│   ├── SKILL.md
│   └── references/
├── session5-showcase/       # 5회차: 사내 공유회 (완성)
│   ├── SKILL.md
│   └── references/
│
│   # ── 미사용 (1기에서 대체됨, 2기 기획 시 참고용) ──
├── session3-automation/     # 원안 3회차: 나만의 업무 자동화 → session3-tools로 대체
│   ├── SKILL.md
│   └── references/
└── session4-polish/         # 원안 4회차: 고도화 + 발표 준비 → session4-pr-showcase로 대체
    ├── SKILL.md
    └── references/
```

## 워크숍 목표

**최종 결과 이미지**: 터미널 하나에서 데이터 분석, CS 응답 초안, 리포트 작성, Slack 요약 등 다양한 업무를 병렬 처리하며 10x 생산성을 확보하는 것. 개발자 도움 없이, 각자가 직접.

## 세션별 스킬 상태

| 세션 | 스킬 폴더 | 상태 | 비고 |
|------|----------|------|------|
| Session 1 | `session1-onboarding/` | 완성 | STOP PROTOCOL 원형 |
| Session 2 | `session2-github/` | 완성 (2026-03-05 업데이트) | GitHub로 내 설정 관리 — 복습(MCP 점검 + git pull 체험) + 3블록 (Git 기본, 첫 push, 동기화) |
| Session 3 | `session3-tools/` | 완성 (구 session2-tools, 이동) | Context Sync 스킬 만들기 — 6블록 + templates/ 포함 |
| Session 4 | `session4-pr-showcase/` | 완성 (2026-03-10) | 산출물 PR 제출 + 피어리뷰 — 4블록 (세팅, 작성, PR, 리뷰) |
| Session 5 | `session5-showcase/` | 장표 완성 + Pages 배포 (2026-03-12) | 사내 공유회 (3/13 금) — Marp 장표 + GitHub Pages 배포 |

## 핵심 설계 원칙

- **STOP PROTOCOL**: 각 블록 = Phase A(설명+실행 안내) → STOP → Phase B(퀴즈+다음 블록 이동) 2턴 구조 필수. `session1-onboarding/SKILL.md` 및 `session3-tools/SKILL.md` 참고
- **금지 사항 명시**: STOP 전 AskUserQuestion 금지 / 퀴즈 금지 / "실행했나요?" 금지 / 다음 블록 언급 금지 — 미명시 시 AI가 위반함
- **공식 문서 URL 필수**: 각 블록 Phase A 시작 시 reference 파일의 공식 URL 반드시 출력
- **템플릿 먼저 패턴**: Block 0에서 템플릿 기반 골격 생성 → 이후 블록에서 점진적 수정
- **결과물 중심 설계**: 세션 목표 = "완성되는 결과물 1개" (예: `/my-context-sync` 스킬)

## 캠프 운영 현황

- **상태**: ✅ **캠프 완료** (3/3 ~ 3/13)
- **일정**: 5세션 × 2시간, 헤이그라운드 세미나실
- **참가자**: 일반 7명 + 앰버서더 2명 = 총 9명
  - 일반: 김태윤, 김성원, 이보배(Vivi), 최재훈(Terry), 이새봄, 아린, 정영현(Jay)
  - 앰버서더: 김영호(Ian), 송상수(Eddie)
- **Claude 플랜**: Team Standard 시트 전사 지원 (캠프 후 전사 정책으로 전환됨)

### 세션 진행 상태

| 세션 | 날짜 | 상태 |
|------|------|------|
| Session 1 — 설치 + 핵심 기능 체험 | 3/3 (화) | ✅ 완료 |
| Session 2 — GitHub로 내 설정 관리하기 | 3/5 (목) | ✅ 완료 |
| Session 3 — 업무 도구 연결 + Context Sync | 3/9 (월) | ✅ 완료 |
| Session 4 — 산출물 PR 제출 + 피어리뷰 | 3/10 (화) | ✅ 완료 |
| Session 5 — 사내 공유회 | 3/13 (금) 10:15~11:45 | ✅ 완료 |

### lk-ai-camp-showcase (Submodule)
- **위치**: `lk-ai-camp-showcase/` (git submodule)
- **역할**: 참가자 산출물 PR 제출 + 피어리뷰 레포
- **보안 처리 (2026-03-13 완료)**: 내부 URL, 이메일, Notion DB ID, Slack 채널 ID, macOS 사용자 경로 마스킹
- **제출 현황**: bom, arin, ethan, terry, theo, vivi, Jay-jungyounghun, sangsu (총 8명)

### 운영 문서 (docs/)
- `docs/plans/2026-02-19-recruitment-design.md` — 모집공고 + 지원서 설계 + 선발 기준
- `docs/participant-messages.md` — 참가자 안내 DM 템플릿 + 발송 체크리스트
- `docs/slack-channel-plan.md` — `#lk-ai-camp` 채널 개설 계획 + 첫 메시지 초안
- `docs/session1-prep.md` — Session 1 실습 데이터 + 설치 FAQ + 체크리스트
- `docs/slack-mcp-guide.md` — Session 1 과제: Slack 커넥터 연결 + Claude에게 3번 질문하기 가이드
- `docs/slides/session5-showcase.md` — Session 5 Marp 발표 장표 (빌드: `marp --theme theme.css --pdf --allow-local-files`)
- `docs/slides/theme.css` — 커스텀 Marp 테마 (Claude 브랜드 컬러 기반)

## 핵심 규칙

- **언어**: 모든 응답은 한국어로 작성
- **Skills as Curriculum**: 각 세션별 Skill이 그날의 수업이다
- 교안 파일(`references/*.md`)은 EXPLAIN / EXECUTE / QUIZ 섹션으로 구성된다
- **실무 예시 우선**: 모든 실습은 LiveKlass 실제 업무(CS 응답, Slack 요약, 구글시트 분석)로 진행
