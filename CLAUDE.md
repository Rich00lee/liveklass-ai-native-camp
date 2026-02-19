# CLAUDE.md

This file provides guidance to Claude Code when working with this repository.

## 프로젝트 개요

LiveKlass AI Native Camp — 비개발자를 위한 Claude Code 사내 워크숍 (4세션 × 1.5시간).
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
├── session2-tools/          # 2회차: 업무 도구 연결 (Slack, Notion, 구글시트)
│   ├── SKILL.md
│   └── references/
├── session3-automation/     # 3회차: 나만의 업무 자동화 만들기
│   ├── SKILL.md
│   └── references/
└── session4-showcase/       # 4회차: 결과 공유 + 다음 스텝
    ├── SKILL.md
    └── references/
```

## 워크숍 목표

**최종 결과 이미지**: 터미널 하나에서 데이터 분석, CS 응답 초안, 리포트 작성, Slack 요약 등 다양한 업무를 병렬 처리하며 10x 생산성을 확보하는 것. 개발자 도움 없이, 각자가 직접.

## 핵심 규칙

- **언어**: 모든 응답은 한국어로 작성
- **Skills as Curriculum**: 각 세션별 Skill이 그날의 수업이다
- 교안 파일(`references/*.md`)은 EXPLAIN / EXECUTE / QUIZ 섹션으로 구성된다
- **실무 예시 우선**: 모든 실습은 LiveKlass 실제 업무(CS 응답, Slack 요약, 구글시트 분석)로 진행
