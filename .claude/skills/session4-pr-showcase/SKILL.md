---
name: session4-pr-showcase
description: LiveKlass AI Native Camp 4회차. 산출물을 정리하고 공용 레포에 PR로 제출하는 법을 배운다. "4회차", "Session 4", "PR 제출", "산출물 공유", "showcase" 요청에 사용.
---

# Session 4: 산출물 PR 제출 + 피어리뷰

이 스킬이 호출되면 아래 **STOP PROTOCOL**을 반드시 따른다.

---

## 용어 정리

| 용어 | 설명 |
|------|------|
| **branch (브랜치)** | 원본을 건드리지 않고 내 작업 공간을 따로 만드는 것. "복사본에서 작업하기" |
| **PR (Pull Request)** | "내가 이렇게 바꿨는데, 봐주세요"라고 요청하는 것. 코드 리뷰의 시작점 |
| **collaborator** | 레포에 직접 push할 수 있는 권한을 받은 사람 |
| **review (리뷰)** | 다른 사람의 PR을 보고 피드백(댓글)을 다는 것 |
| **merge (머지)** | PR이 승인되면 브랜치의 변경사항을 원본(main)에 합치는 것 |
| **SHOWCASE.md** | 발표 자료 템플릿. 문제 → 병목 → 방향 → 구현 → 과제 순서로 정리 |

---

## STOP PROTOCOL — 절대 위반 금지

> 이 프로토콜은 이 스킬의 최우선 규칙이다.
> 아래 규칙을 위반하면 수업이 망가진다.

### 각 블록은 반드시 2턴에 걸쳐 진행한다

```
┌─ Phase A (첫 번째 턴) ──────────────────────────────┐
│ 1. references/에서 해당 블록 파일의 EXPLAIN 섹션을 읽는다    │
│ 2. 기능을 설명한다                                        │
│ 3. references/에서 해당 블록 파일의 EXECUTE 섹션을 읽는다    │
│ 4. "지금 직접 실행해보세요"라고 안내한다                     │
│ 5. ⛔ 여기서 반드시 STOP. 턴을 종료한다.                    │
│                                                          │
│ ❌ 절대 하지 않는 것: 퀴즈 출제, QUIZ 섹션 읽기             │
│ ❌ 절대 하지 않는 것: AskUserQuestion 호출                  │
│ ❌ 절대 하지 않는 것: "실행해봤나요?" 질문                   │
│ ❌ 절대 하지 않는 것: 다음 블록 내용 미리 언급               │
│ ❌ 절대 하지 않는 것: Phase A 종료 문구 이후 추가 텍스트 출력 │
└──────────────────────────────────────────────────────────┘

  ⬇️ 사용자가 돌아와서 "했어", "완료", "다음" 등을 입력한다

┌─ Phase B (두 번째 턴) ──────────────────────────────┐
│ 1. references/에서 해당 블록 파일의 QUIZ 섹션을 읽는다       │
│ 2. AskUserQuestion으로 퀴즈를 출제한다                     │
│ 3. 정답/오답 피드백을 준다                                 │
│ 4. 다음 블록으로 이동할지 AskUserQuestion으로 묻는다         │
│ 5. ⛔ 다음 블록을 시작하면 다시 Phase A부터.                │
└──────────────────────────────────────────────────────────┘
```

### 핵심 금지 사항 (절대 위반 금지)

1. **Phase A에서 AskUserQuestion을 호출하지 않는다** — 사용자가 먼저 말할 때까지 기다린다
2. **Phase A에서 퀴즈를 내지 않는다** — QUIZ 섹션은 Phase B에서만 읽는다
3. **Phase A에서 "실행해봤나요?"를 묻지 않는다** — 사용자가 먼저 말할 때까지 기다린다
4. **한 턴에 EXPLAIN + QUIZ를 동시에 하지 않는다** — 반드시 2턴으로 나눈다
5. **Phase A 종료 문구 이후 어떤 도구 호출이나 추가 텍스트도 출력하지 않는다**

### 공식 문서 URL 출력 (절대 누락 금지)

모든 블록의 Phase A 시작 시, 해당 reference 파일 상단의 `> 공식 문서:` URL을 **반드시 그대로 출력**한다.

```
📖 공식 문서: [URL]
```

- reference 파일에 URL이 여러 개 있으면 전부 출력한다
- URL을 요약하거나 생략하지 않는다

### Phase A 종료 시 필수 문구

Phase A의 마지막에는 반드시 아래 문구를 출력하고 Stop한다:

```
---
👆 위 내용을 직접 실행해보세요.
실행이 끝나면 "완료" 또는 "다음"이라고 입력해주세요.
```

---

## 블록 특수 규칙

- **Block 0 (세팅)**: Phase A에서 레포 clone + 브랜치 생성 방법 설명 + Claude가 대신 실행해주는 안내 → Stop. Phase B에서 퀴즈.
- **Block 1 (산출물 작성)**: Phase A에서 SHOWCASE.md 템플릿 구조 설명 + 자기 폴더에 템플릿 복사 안내 → Stop. Phase B에서 퀴즈.
- **Block 2 (PR 제출)**: Phase A에서 commit → push → PR 생성 흐름 설명 + Claude에게 자연어로 시키는 안내 → Stop. Phase B에서 퀴즈.
- **Block 3 (피어리뷰)**: Phase A에서 좋은 리뷰 작성법 설명 + 다른 사람 PR에 코멘트 다는 실습 안내 → Stop. Phase B에서 퀴즈 + Session 5 안내.

---

## References 파일 맵

| 블록 | 파일 | 내용 |
|------|------|------|
| Block 0 | `references/block0-setup.md` | 레포 clone + 브랜치 생성 |
| Block 1 | `references/block1-showcase.md` | SHOWCASE.md 작성 가이드 |
| Block 2 | `references/block2-pr.md` | commit → push → PR 생성 |
| Block 3 | `references/block3-review.md` | PR 리뷰 + 피드백 + Session 5 안내 |

---

## 진행 규칙

- 한 번에 한 블록씩 진행한다
- "다음", "skip", 블록 번호/이름으로 이동한다
- **Claude Code가 git 명령어를 대신 실행해주는 경험**이 핵심 — 참가자가 명령어를 외울 필요 없음
- 실습 시 Claude에게 자연어로 시키는 것을 권장 (예: "브랜치 만들어줘", "PR 만들어줘")
- Git에서 막히는 참가자에게는 진행자 또는 앰버서더(Ian, Eddie)에게 도움 요청 안내

---

## 공용 레포 정보

- **레포**: `https://github.com/Rich00lee/lk-ai-camp-showcase`
- **구조**:
  ```
  lk-ai-camp-showcase/
  ├── README.md                ← PR 제출 가이드
  ├── template/
  │   └── SHOWCASE.md          ← 발표 자료 템플릿
  └── submissions/
      └── (각자 이름 폴더)
  ```

---

## 시작

아래 테이블을 보여주고 AskUserQuestion으로 어디서 시작할지 물어본다.

| Block | 주제 | 시간 | 내용 |
|-------|------|------|------|
| 0 | 세팅 | 15분 | 레포 clone + 브랜치 생성 |
| 1 | 산출물 작성 | 40분 | SHOWCASE.md 템플릿 채우기 |
| 2 | PR 제출 | 20분 | commit → push → PR 생성 |
| 3 | 피어리뷰 | 30분 | 다른 사람 PR에 리뷰 달기 |

```json
AskUserQuestion({
  "questions": [{
    "question": "Session 4: 산출물 PR 제출 + 피어리뷰\n\n어디서부터 시작할까요?",
    "header": "시작 블록",
    "options": [
      {"label": "처음부터 (Block 0: 세팅)", "description": "레포 clone + 브랜치 생성부터"},
      {"label": "산출물 작성 (Block 1)", "description": "세팅은 했고, SHOWCASE.md 작성부터"},
      {"label": "PR 제출 (Block 2)", "description": "작성은 했고, PR 만들기부터"},
      {"label": "피어리뷰 (Block 3)", "description": "PR은 올렸고, 리뷰 달기부터"}
    ],
    "multiSelect": false
  }]
})
```
