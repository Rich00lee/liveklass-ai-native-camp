# Session 3/4/5 구조 재설계 구현 계획

> **For Claude:** REQUIRED SUB-SKILL: Use superpowers:executing-plans to implement this plan task-by-task.

**Goal:** Session 3 보강 + Session 4-polish 신규 생성 + Session 5-showcase 이름 변경/축소로 5세션 커리큘럼 완성

**Architecture:** 기존 Session 2의 STOP PROTOCOL 강화판을 Session 3/4/5에 동일하게 적용. 기존 콘텐츠 최대 재활용, 구조 변경 최소화.

**Tech Stack:** Markdown (SKILL.md + references/*.md), Claude Code Skills 구조

**참조 문서:**
- 설계 문서: `docs/plans/2026-02-20-session-restructure-design.md`
- Session 2 SKILL.md (STOP PROTOCOL 원본): `.claude/skills/session2-tools/SKILL.md`
- CAMP_PLAN: `CAMP_PLAN.md` (세션별 타임테이블)

---

### Task 1: session4-showcase → session5-showcase 이름 변경

**Files:**
- Rename: `.claude/skills/session4-showcase/` → `.claude/skills/session5-showcase/`
- Modify: `.claude/skills/session5-showcase/SKILL.md`
- Delete: `.claude/skills/session5-showcase/references/block0-demo-prep.md`
- Rename: `references/block1-showcase.md` → `references/block0-showcase.md`
- Rename: `references/block2-next-steps.md` → `references/block1-next-steps.md`

**Step 1: 폴더 이름 변경**

```bash
git mv .claude/skills/session4-showcase .claude/skills/session5-showcase
```

**Step 2: block0-demo-prep.md 삭제 (Session 4-polish로 이동 예정)**

삭제 전에 내용을 기억해둔다 (Task 3에서 재활용).

```bash
git rm .claude/skills/session5-showcase/references/block0-demo-prep.md
```

**Step 3: reference 파일 번호 재정렬**

```bash
git mv .claude/skills/session5-showcase/references/block1-showcase.md .claude/skills/session5-showcase/references/block0-showcase.md
git mv .claude/skills/session5-showcase/references/block2-next-steps.md .claude/skills/session5-showcase/references/block1-next-steps.md
```

**Step 4: SKILL.md 수정**

`.claude/skills/session5-showcase/SKILL.md` 수정 사항:
- frontmatter name: `session4-showcase` → `session5-showcase`
- frontmatter description: "4회차", "Session 4" → "5회차", "Session 5", "사내 발표"
- 제목: "Session 4: 결과 공유 + 다음 스텝" → "Session 5: 사내 발표"
- STOP PROTOCOL: Session 2 수준으로 격상 (`.claude/skills/session2-tools/SKILL.md`의 STOP PROTOCOL 섹션 참조)
  - Phase A/B 도식 (ASCII box) 추가
  - 금지사항 5개 명시
  - 공식 문서 URL 출력 규칙 추가
  - Phase A 종료 문구 규칙 추가
- References 파일 맵: block0 → showcase, block1 → next-steps (2개로 축소)
- 시작 테이블: Block 0 Showcase / Block 1 Next Steps (2개)
- AskUserQuestion 시작 옵션: 2개로 축소

**Step 5: references 내용 수정**

`block0-showcase.md`: 기존 block1-showcase.md 내용 유지, 상단에 공식 문서 URL 추가
`block1-next-steps.md`: 기존 block2-next-steps.md 내용에서 "4세션" → "5세션" 전부 수정

**Step 6: 검증**

- 파일 구조 확인: `find .claude/skills/session5-showcase -type f | sort`
- SKILL.md에 "session4" 또는 "4회차" 잔존 여부: `grep -r "session4\|4회차\|4세션" .claude/skills/session5-showcase/`

**Step 7: 커밋**

```bash
git add .claude/skills/session5-showcase/
git commit -m "refactor: session4-showcase → session5-showcase 이름 변경 + 2블록 축소"
```

---

### Task 2: session3-automation SKILL.md 보강

**Files:**
- Modify: `.claude/skills/session3-automation/SKILL.md`
- Modify: `.claude/skills/session3-automation/references/block0-design.md`
- Modify: `.claude/skills/session3-automation/references/block1-build.md`
- Modify: `.claude/skills/session3-automation/references/block2-test.md`

**Step 1: SKILL.md STOP PROTOCOL 격상**

`.claude/skills/session2-tools/SKILL.md`에서 아래 섹션을 복사하여 Session 3에 맞게 수정:
- `## STOP PROTOCOL — 절대 위반 금지` 전체 (Phase A/B 도식 포함)
- `### 핵심 금지 사항 (절대 위반 금지)` 5개
- `### 공식 문서 URL 출력 (절대 누락 금지)`
- `### Phase A 종료 시 필수 문구`

Session 3 전용 수정:
- Block 0 AskUserQuestion 예외 규칙 추가 (아이디어 선택이 필수이므로)
- Block 2 자유 답변 예외 규칙 추가 (피칭 문구 작성)
- 금지사항 1번: "Phase A에서 AskUserQuestion을 호출하지 않는다 (Block 0 제외)"

**Step 2: 용어 정리 섹션 추가**

STOP PROTOCOL 위에 용어 정리 테이블 추가:

| 용어 | 설명 |
|------|------|
| **Skill** | Claude Code에게 특정 작업 방법을 가르치는 문서. Session 1에서 체험, Session 2에서 직접 만든 것 |
| **SKILL.md** | Skill의 본체 파일. 이 안에 Claude의 행동 규칙을 적는다 |
| **frontmatter** | SKILL.md 맨 위 `---` 사이에 적는 메타 정보 (name, description) |
| **description** | frontmatter 안에서 "이 Skill을 언제 쓸지" 정의하는 한 줄 설명 |
| **references** | SKILL.md가 참조하는 교안 파일들. EXPLAIN/EXECUTE/QUIZ 3섹션 구조 |

**Step 3: 블록 특수 규칙 + 진행 규칙 보강**

Session 2 형식 참조하여:
- 블록 특수 규칙 섹션 추가 (Block 0: AskUserQuestion 예외, Block 1: Claude가 파일 생성, Block 2: 자유 답변 예외)
- 진행 규칙에 Session 2 연계 문구 추가: "Session 2에서 만든 /my-context-sync 경험을 기반으로, 이번에는 나만의 Skill을 만든다"

**Step 4: references 3파일 보강**

각 파일 상단에 공식 문서 URL 추가:
```
> 공식 문서: https://docs.anthropic.com/ko/docs/claude-code/skills
```

`block0-design.md`: AskUserQuestion으로 아이디어 선택 명시 (QUIZ 섹션)
`block1-build.md`: "Claude가 대신 파일 생성" 패턴 명시 (EXECUTE 섹션)
`block2-test.md`: 중간 발표 30초 피칭 문구 작성 추가 (EXECUTE 섹션 마지막)

**Step 5: 검증**

- STOP PROTOCOL 핵심 키워드 확인: `grep -c "절대 위반 금지\|Phase A\|Phase B\|금지 사항" .claude/skills/session3-automation/SKILL.md`
  - 예상: 5개 이상 매칭
- 공식 문서 URL 확인: `grep "공식 문서" .claude/skills/session3-automation/references/*.md`
  - 예상: 3파일 모두 매칭

**Step 6: 커밋**

```bash
git add .claude/skills/session3-automation/
git commit -m "enhance: Session 3 STOP PROTOCOL 강화 + references 보강"
```

---

### Task 3: session4-polish 신규 생성

**Files:**
- Create: `.claude/skills/session4-polish/SKILL.md`
- Create: `.claude/skills/session4-polish/references/block0-review.md`
- Create: `.claude/skills/session4-polish/references/block1-polish.md`
- Create: `.claude/skills/session4-polish/references/block2-pitch.md`

**Step 1: SKILL.md 작성**

Session 2 SKILL.md를 뼈대로 사용. 수정 사항:
- frontmatter: name `session4-polish`, description "4회차", "Session 4", "고도화", "피칭", "발표 준비"
- 제목: "Session 4: 고도화 + 발표 준비"
- 용어 정리: 피칭(pitching), 리팩토링(refactoring), 엣지 케이스(edge case)
- STOP PROTOCOL: Session 2 동일 (Phase A/B 도식 + 금지사항 5개)
- Block 0 AskUserQuestion 예외 (개선할 Skill 선택)
- References 파일 맵: block0-review / block1-polish / block2-pitch
- 시작 테이블: 3블록

**Step 2: block0-review.md 작성**

```markdown
> 공식 문서: https://docs.anthropic.com/ko/docs/claude-code/skills

## EXPLAIN

### Skill 사용 후기 + 문제 진단

Session 3에서 만든 Skill을 실제 업무에서 3번 써봤다.
이제 "뭐가 잘 됐고, 뭐가 아쉬웠는지" 정리한다.

**후기 정리 프레임워크**:
1. **잘 된 것**: 기대한 대로 동작한 부분
2. **아쉬운 것**: 결과가 부족하거나 잘못된 부분
3. **못 쓴 것**: 실행 자체가 안 되거나 건너뛴 부분

**흔한 문제 패턴**:
| 증상 | 원인 | 해결 방향 |
|------|------|----------|
| 결과가 너무 길다/짧다 | 출력 형식 미지정 | SKILL.md에 "200자 이내" 등 명시 |
| 원하는 톤이 아니다 | 역할 정의 부족 | "나는 ~이다" 역할 문구 추가 |
| 매번 결과가 다르다 | 절차가 모호 | 처리 절차를 단계별로 구체화 |
| 특정 입력에서 오류 | 예외 처리 없음 | "~인 경우 ~하라" 조건 추가 |

## EXECUTE

Claude Code에 입력:
- Session 3에서 만든 Skill을 3번 써본 경험을 정리해보세요
- 잘 된 것 / 아쉬운 것 / 못 쓴 것으로 나눠서 말해주세요

## QUIZ

AskUserQuestion으로 물어본다:

질문: "가장 먼저 개선하고 싶은 포인트 1가지는?"
→ 자유 답변 → Block 1에서 바로 개선
```

**Step 3: block1-polish.md 작성**

```markdown
> 공식 문서: https://docs.anthropic.com/ko/docs/claude-code/skills

## EXPLAIN

### 3가지 개선 패턴

Block 0에서 찾은 문제를 해결하는 3가지 패턴:

**패턴 1: 출력 형식 조정**
SKILL.md의 "출력 형식" 섹션을 구체화한다.
- "요약해줘" → "3줄 이내, 불릿 포인트로 요약"
- "테이블로 정리" → "| 항목 | 현황 | 액션 | 형식, 최대 10행"

**패턴 2: 예외 처리 추가**
예상치 못한 입력이 들어왔을 때의 행동을 정의한다.
- "입력이 없으면 → '어떤 데이터를 분석할까요?'라고 물어본다"
- "데이터가 너무 많으면 → 최근 7일치만 처리한다"

**패턴 3: 프롬프트 정교화**
SKILL.md의 "역할"과 "처리 절차"를 더 구체적으로 만든다.
- 실제 좋은 결과가 나왔던 입력을 "예시"로 SKILL.md에 추가
- "주의사항"에 하지 말아야 할 것도 명시

## EXECUTE

지금 바로 SKILL.md를 개선해보세요:

Claude Code에 입력:
- 내 Skill [이름]의 SKILL.md를 열어줘
- [Block 0에서 찾은 문제]를 개선해줘
- 수정 전후를 비교해서 보여줘

## QUIZ

AskUserQuestion으로 물어본다:

질문: "개선 후 Skill을 다시 실행해봤을 때, 결과가 나아졌나요?"
- "나아졌다" → ✅ "Block 2에서 이 결과를 발표용으로 다듬어봐요"
- "아직 부족하다" → "어떤 부분이 아쉬운가요? 다른 패턴을 적용해봅시다"
```

**Step 4: block2-pitch.md 작성**

기존 `session4-showcase/references/block0-demo-prep.md` 내용을 기반으로 작성.
피칭 구조(문제 10초→해결 10초→시연 30초→임팩트 10초) 설명 유지.

추가 사항:
- EXECUTE 마지막에 GitHub 숙제 안내 한 줄:
  "발표 준비가 끝났다면, 만든 Skill을 GitHub에 올려보세요 (숙제)"
- QUIZ: 리허설 (자유 답변 → Claude가 팀원 역할로 피드백)

**Step 5: 검증**

- 파일 구조: `find .claude/skills/session4-polish -type f | sort`
  - 예상: SKILL.md + references/block0-review.md + block1-polish.md + block2-pitch.md (4파일)
- STOP PROTOCOL 확인: `grep -c "절대 위반 금지" .claude/skills/session4-polish/SKILL.md`
  - 예상: 1개 이상
- 공식 문서 URL: `grep "공식 문서" .claude/skills/session4-polish/references/*.md`
  - 예상: 3파일 모두 매칭

**Step 6: 커밋**

```bash
git add .claude/skills/session4-polish/
git commit -m "feat: Session 4-polish 신규 생성 — 고도화 + 발표 준비"
```

---

### Task 4: CLAUDE.md 업데이트

**Files:**
- Modify: `CLAUDE.md`

**Step 1: 세션별 스킬 상태 테이블 수정**

| 세션 | 스킬 폴더 | 상태 | 비고 |
|------|----------|------|------|
| Session 1 | `session1-onboarding/` | 완성 | STOP PROTOCOL 원형 |
| Session 2 | `session2-tools/` | 완성 | Context Sync 스킬 만들기 — 6블록 |
| Session 3 | `session3-automation/` | 완성 | STOP PROTOCOL 강화 완료 |
| Session 4 | `session4-polish/` | 완성 | 고도화 + 발표 준비 — 3블록 |
| Session 5 | `session5-showcase/` | 완성 | 사내 발표 — 2블록 |

**Step 2: 구조 섹션의 디렉토리 트리 수정**

```
.claude/skills/
├── session1-onboarding/
├── session2-tools/
├── session3-automation/
├── session4-polish/
└── session5-showcase/
```

**Step 3: 검증**

- "session4-showcase" 잔존 확인: `grep "session4-showcase" CLAUDE.md`
  - 예상: 0건

**Step 4: 커밋**

```bash
git add CLAUDE.md
git commit -m "docs: CLAUDE.md 5세션 스킬 상태 업데이트"
```

---

### Task 5: 최종 검증 + push

**Step 1: 전체 구조 검증**

```bash
find .claude/skills -type f -name "SKILL.md" | sort
```

예상 출력:
```
.claude/skills/session1-onboarding/SKILL.md
.claude/skills/session2-tools/SKILL.md
.claude/skills/session3-automation/SKILL.md
.claude/skills/session4-polish/SKILL.md
.claude/skills/session5-showcase/SKILL.md
```

**Step 2: "session4-showcase" 잔존 확인**

```bash
grep -r "session4-showcase" .claude/ CLAUDE.md README.md
```

예상: 0건

**Step 3: git push**

```bash
git push origin main
```
