---
name: session2-tools
description: LiveKlass AI Native Camp 2회차. 업무 도구 연결 — Slack, Notion, Google Sheets MCP 설정. "2회차", "Session 2", "MCP 연결", "도구 연결", "Slack 연결", "Notion 연결" 요청에 사용.
---

# Session 2: 업무 도구 연결

이 스킬이 호출되면 STOP PROTOCOL을 반드시 따른다.

---

## STOP PROTOCOL — 절대 위반 금지

Session 1과 동일한 2턴 구조:

```
Phase A: EXPLAIN 읽기 → 설명 → EXECUTE 안내 → STOP
Phase B: QUIZ 읽기 → 퀴즈 출제 → 피드백 → 다음 블록 확인
```

Phase A에서 절대 하지 않는 것: 퀴즈 출제, AskUserQuestion 호출

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
| Block 0 | `references/block0-mcp-concept.md` |
| Block 1 | `references/block1-slack.md` |
| Block 2 | `references/block2-notion.md` |
| Block 3 | `references/block3-gsheets.md` |
| Block 4 | `references/block4-practice.md` |

---

## 진행 규칙

- MCP 설치 중 오류 발생 시: 에러 메시지를 그대로 붙여넣도록 안내하고 함께 해결
- 도구마다 인증(authentication) 방식이 다름 — 각 reference 파일의 설치 절차 정확히 안내
- 설치가 완료되면 **실제 데이터로 테스트**까지 함께 진행

---

## 시작

스킬 시작 시 아래 테이블을 보여주고 AskUserQuestion으로 어디서 시작할지 물어본다.

| Block | 주제 | 내용 |
|-------|------|------|
| 0 | MCP 개념 | MCP가 뭔지 + 오늘 연결할 3가지 도구 |
| 1 | Slack | Slack MCP 설치 + 실제 채널 메시지 읽기 |
| 2 | Notion | Notion MCP 설치 + 실제 페이지 읽기 |
| 3 | Google Sheets | Google Sheets MCP 설치 + 데이터 분석 |
| 4 | 통합 실습 | 3가지 도구 동시에 활용하는 실무 시나리오 |

```json
AskUserQuestion({
  "questions": [{
    "question": "어디서부터 시작할까요?",
    "header": "시작 블록",
    "options": [
      {"label": "Block 0: MCP 개념", "description": "오늘 배울 내용 전체 흐름 파악"},
      {"label": "Block 1: Slack", "description": "Slack MCP 설치 + 메시지 읽기"},
      {"label": "Block 2: Notion", "description": "Notion MCP 설치 + 페이지 읽기"},
      {"label": "Block 3: Google Sheets", "description": "Google Sheets MCP 설치 + 데이터 분석"}
    ],
    "multiSelect": false
  }]
})
```
