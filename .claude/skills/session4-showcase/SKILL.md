---
name: session4-showcase
description: LiveKlass AI Native Camp 4회차. 결과물 데모 발표 + 팀 확산 전략 논의 + 다음 스텝 설정. "4회차", "Session 4", "데모", "발표", "마무리" 요청에 사용.
---

# Session 4: 결과 공유 + 다음 스텝

이 스킬이 호출되면 STOP PROTOCOL을 반드시 따른다.

---

## STOP PROTOCOL

```
Phase A: EXPLAIN 읽기 → 설명 → EXECUTE 안내 → STOP
Phase B: QUIZ 읽기 → 마무리 확인 → 다음 블록
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
| Block 0 | `references/block0-demo-prep.md` |
| Block 1 | `references/block1-showcase.md` |
| Block 2 | `references/block2-next-steps.md` |

---

## 시작

스킬 시작 시 아래 테이블을 보여주고 AskUserQuestion으로 어디서 시작할지 물어본다.

| Block | 주제 | 내용 |
|-------|------|------|
| 0 | Demo Prep | 발표 준비 — 1분 피칭 연습 |
| 1 | Showcase | 팀 데모 발표 진행 |
| 2 | Next Steps | 팀 확산 전략 + 개인 다음 스텝 |

```json
AskUserQuestion({
  "questions": [{
    "question": "어디서부터 시작할까요?",
    "header": "시작 블록",
    "options": [
      {"label": "Block 0: Demo Prep", "description": "1분 피칭 준비 연습"},
      {"label": "Block 1: Showcase", "description": "팀 데모 발표"},
      {"label": "Block 2: Next Steps", "description": "팀 확산 전략 + 다음 스텝"}
    ],
    "multiSelect": false
  }]
})
```
