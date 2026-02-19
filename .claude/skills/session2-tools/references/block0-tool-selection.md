> 공식 문서: https://docs.anthropic.com/ko/docs/claude-code/mcp

## EXPLAIN

### 오늘 만들 것

Session 2가 끝나면 `/my-context-sync`라는 나만의 스킬이 생긴다.

매일 아침 이 한 줄로 업무를 시작하게 된다:

```
/my-context-sync
```

결과:
- Slack에서 어제 이후 중요 메시지 요약
- Google Sheets에서 파이프라인/업무 현황
- Notion에서 오늘 할일 + 미팅

세 곳을 따로따로 열어보는 대신, 한 번에 오늘의 컨텍스트를 확보하는 것.

### 도구 선택

연결할 도구를 먼저 고른다. 오늘 세션에서 모두 연결할 필요는 없다.
**지금 당장 쓸 수 있는 것부터 시작**하는 게 핵심이다.

| 도구 | 얻을 수 있는 것 | 추천 대상 |
|------|---------------|----------|
| **Slack** | 어제~오늘 중요 메시지, 멘션, 채널 요약 | 슬랙을 주 소통 채널로 쓰는 분 |
| **Notion** | 오늘 할일, 미팅 일정, 주요 문서 업데이트 | Notion으로 업무를 관리하는 분 |
| **Google Sheets** | 파이프라인 현황, KPI, 집계 데이터 | 시트로 데이터를 관리하는 분 |

## EXECUTE

아래 질문에 답해주세요.

오늘 연결할 도구를 선택한다 (여러 개 선택 가능):

```json
AskUserQuestion({
  "questions": [{
    "question": "오늘 Context Sync에 연결할 도구를 선택해주세요.",
    "header": "도구 선택",
    "options": [
      {"label": "Slack", "description": "채널 메시지, 멘션, DM 요약"},
      {"label": "Notion", "description": "할일, 미팅, 문서 업데이트"},
      {"label": "Google Sheets", "description": "파이프라인, KPI, 집계 데이터"}
    ],
    "multiSelect": true
  }]
})
```

선택이 완료되면:
1. `templates/context-sync.md` 파일을 읽는다
2. 선택한 도구만 남기고 나머지는 제거한 형태로 `.claude/skills/my-context-sync/SKILL.md`를 생성한다
3. 생성된 파일의 전체 구조(섹션 목록)만 간략히 보여주고 Stop한다

## QUIZ

```json
AskUserQuestion({
  "questions": [{
    "question": "Context Sync 스킬을 만드는 이유는 무엇인가요?",
    "header": "Block 0 퀴즈",
    "options": [
      {"label": "Slack, Notion, 시트를 자동으로 열어주는 것", "description": ""},
      {"label": "흩어진 업무 정보를 한 번에 수집해 오늘의 컨텍스트를 만드는 것", "description": ""},
      {"label": "MCP 서버를 설치하는 것", "description": ""},
      {"label": "Claude에게 업무 일정을 알려주는 것", "description": ""}
    ],
    "multiSelect": false
  }]
})
```

정답: **두 번째** — 흩어진 업무 정보를 한 번에 수집해 오늘의 컨텍스트를 만드는 것

오답 시 피드백:
- 1번: 도구를 여는 게 아니라 데이터를 가져오는 것
- 3번: MCP 설치는 수단, 목적은 컨텍스트 수집
- 4번: 일방적으로 알려주는 게 아니라 Claude가 직접 수집
