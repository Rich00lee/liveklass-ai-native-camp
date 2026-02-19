---
name: session3-automation
description: LiveKlass AI Native Camp 3회차. 나만의 업무 자동화 Skill 기획 → 제작 → 테스트. "3회차", "Session 3", "자동화 만들기", "스킬 만들기" 요청에 사용.
---

# Session 3: 나만의 업무 자동화 만들기

이 스킬이 호출되면 STOP PROTOCOL을 반드시 따른다.

---

## STOP PROTOCOL

```
Phase A: EXPLAIN 읽기 → 설명 → EXECUTE 안내 → STOP
Phase B: QUIZ 읽기 → 퀴즈 출제 → 피드백 → 다음 블록
```

Phase A 종료 시 필수 문구:
```
---
👆 위 내용을 직접 실행해보세요.
실행이 끝나면 "완료" 또는 "다음"이라고 입력해주세요.
```

---

## References 파일 맵

| 블록 | 파일 |
|------|------|
| Block 0 | `references/block0-design.md` |
| Block 1 | `references/block1-build.md` |
| Block 2 | `references/block2-test.md` |

---

## 진행 규칙

- 이 세션은 **실습 중심** — 설명보다 만드는 시간이 더 많다
- 참가자마다 만드는 Skill이 다름 → 개별 맞춤 진행
- 막히면 "뭘 만들려고 하는지" 다시 물어보고 작게 쪼개서 도움
- 완성도보다 **동작하는 결과물** 우선

---

## 시작

스킬 시작 시 아래 테이블을 보여주고 AskUserQuestion으로 어디서 시작할지 물어본다.

| Block | 주제 | 내용 |
|-------|------|------|
| 0 | Design | 자동화 아이디어 구체화 + SKILL.md 설계 |
| 1 | Build | SKILL.md 작성 + 실제 Skill 제작 |
| 2 | Test | 테스트 + 개선 + 공유 준비 |

```json
AskUserQuestion({
  "questions": [{
    "question": "어디서부터 시작할까요?",
    "header": "시작 블록",
    "options": [
      {"label": "Block 0: Design", "description": "자동화 아이디어 구체화 → SKILL.md 설계"},
      {"label": "Block 1: Build", "description": "바로 Skill 제작 시작"},
      {"label": "Block 2: Test", "description": "만든 Skill 테스트 + 개선"}
    ],
    "multiSelect": false
  }]
})
```
