# Session 3/4/5 구조 재설계

> 작성일: 2026-02-20 | 접근 방식: A안 (내용 보강 중심)

---

## 배경

- Session 1·2는 완성 (STOP PROTOCOL 강화판 적용)
- Session 3은 STOP PROTOCOL이 골격 수준, 블록 내용 얕음
- Session 4는 원래 showcase였으나, CAMP_PLAN에서 Session 4 = "고도화 + 발표 준비", Session 5 = "사내 발표"로 분리
- 커리큘럼이 실시간 피드백으로 수정될 예정이므로, 완벽보다 동작하는 커리큘럼 우선

## 설계 원칙

- 기존 구조 최대 활용 — 구조 변경 최소화, STOP PROTOCOL + 금지사항만 Session 2 수준으로 격상
- Session 3는 참가자마다 만드는 스킬이 다르므로 고정 템플릿 불필요 (Session 2의 Context Sync와 다름)
- 기존 콘텐츠 재활용 — session4-showcase의 demo-prep, next-steps 내용을 각각 session4-polish, session5-showcase에 분배

---

## Session 3: 자동화 만들기 — 내용 보강

### 변경 범위

- SKILL.md: STOP PROTOCOL을 Session 2 수준으로 상세화 (Phase A/B 도식 + 금지사항 5개 + 공식 문서 URL 규칙)
- 용어 정리 추가: Skill, SKILL.md, frontmatter, description, references
- 블록 특수 규칙 추가: Block 0 AskUserQuestion 예외 (아이디어 선택), Block 2 자유 답변 예외
- Session 2 결과물 연계 문구 추가

### 블록 구조 (3블록 유지)

| Block | 주제 | Phase A | Phase B |
|-------|------|---------|---------|
| 0 — Design | 아이디어 구체화 + SKILL.md 설계 | 좋은 자동화 조건 설명 + AskUserQuestion으로 아이디어 선택 → STOP | 입력/출력 명확성 확인 |
| 1 — Build | SKILL.md 작성 + 제작 | 작성 원칙 설명 + Claude가 파일 생성 → STOP | 실행 결과 확인 |
| 2 — Test | 테스트 + 개선 + 중간 발표 준비 | 3가지 테스트 시나리오 + 30초 피칭 문구 → STOP | 피칭 문구 다듬기 |

### References 변경

| 파일 | 변경 |
|------|------|
| `block0-design.md` | 공식 문서 URL 추가 + AskUserQuestion 명시 |
| `block1-build.md` | 공식 문서 URL 추가 + "Claude가 대신 파일 생성" 명시 |
| `block2-test.md` | 공식 문서 URL 추가 + 중간 발표 30초 피칭 추가 |

---

## Session 4-polish: 고도화 + 발표 준비 — 신규 생성

### 컨셉

"만든 걸 다듬고, 보여줄 준비를 한다" — Session 3 Skill을 실무에 3회 써본 후 개선 + 1분 피칭 완성.

### SKILL.md 구조

| 항목 | 내용 |
|------|------|
| name | `session4-polish` |
| description | "4회차", "Session 4", "고도화", "피칭", "발표 준비" 트리거 |
| STOP PROTOCOL | Session 2 수준 (Phase A/B 도식 + 금지사항 5개) |
| 용어 정리 | 피칭(pitching), 리팩토링(refactoring), 엣지 케이스(edge case) |

### 블록 설계

| Block | 주제 | Phase A | Phase B |
|-------|------|---------|---------|
| 0 — Review | 사용 후기 + 문제 진단 | 3회 사용 경험 공유 프레임워크 + 개선 포인트 정리 → STOP | 개선 포인트 1가지 선택 |
| 1 — Polish | Skill 개선 실습 | 3가지 개선 패턴(출력 형식/예외 처리/프롬프트 정교화) + SKILL.md 수정 → STOP | 수정 전후 비교 |
| 2 — Pitch | 1분 피칭 + 리허설 | 피칭 구조(문제→해결→시연→임팩트) + 스크립트 작성 → STOP | 리허설 (자유 답변 → 피드백) |

### References

```
session4-polish/
├── SKILL.md
└── references/
    ├── block0-review.md
    ├── block1-polish.md
    └── block2-pitch.md    # session4-showcase/block0-demo-prep.md 내용 재활용
```

### 특수 규칙

- Block 0: AskUserQuestion 예외 (어떤 Skill을 개선할지 선택)
- Block 2: 피칭 콘텐츠는 기존 session4-showcase/block0-demo-prep.md에서 가져옴
- GitHub push는 숙제로 안내 (Block 2 EXECUTE 마지막)

---

## Session 5-showcase: 사내 발표 — 이름 변경 + 2블록 축소

### 변경 범위

- session4-showcase → session5-showcase 이름 변경
- Block 0 (demo-prep) 삭제 — Session 4-polish Block 2에서 완료
- Block 1·2 → Block 0·1로 번호 이동
- STOP PROTOCOL Session 2 수준으로 격상
- "4세션" → "5세션" 문구 전부 수정

### 블록 설계

| Block | 주제 | Phase A | Phase B |
|-------|------|---------|---------|
| 0 — Showcase | 팀 데모 발표 | 체크리스트 확인 + 발표 진행 (1인 2분 × 5명) → STOP | 발표 소감 |
| 1 — Next Steps | 확산 + 다음 스텝 | 3단계 확산 로드맵 + 앰버서더 역할 → STOP | "가장 크게 변한 것" + "다음 달 할 일 1가지" → 마무리 |

### References

```
session5-showcase/
├── SKILL.md
└── references/
    ├── block0-showcase.md     # 기존 block1-showcase.md 기반
    └── block1-next-steps.md   # 기존 block2-next-steps.md 기반 + "5세션" 수정
```

---

## 디렉토리 변경 요약

```
작업 1: session4-showcase/ → session5-showcase/ (rename)
작업 2: session4-polish/ 신규 생성 (SKILL.md + references/ 3파일)
작업 3: session3-automation/ SKILL.md 보강 + references/ 3파일 보강
작업 4: CLAUDE.md 세션별 스킬 상태 테이블 업데이트
```
