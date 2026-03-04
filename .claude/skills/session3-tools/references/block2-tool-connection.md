> 공식 문서: https://docs.anthropic.com/ko/docs/claude-code/mcp
> 공식 문서: https://modelcontextprotocol.io/introduction

## EXPLAIN

### MCP 연결 방식

선택한 도구를 Claude에 연결하는 두 가지 방법:

| 방법 | 설명 | 추천 상황 |
|------|------|----------|
| **MCP 서버** | 이미 만들어진 연결 모듈 설치 | Slack, Notion 등 공식 MCP 서버가 있을 때 |
| **API 직접 호출** | Claude가 코드를 작성해서 직접 연결 | MCP 서버가 없거나 커스텀이 필요할 때 |

오늘은 **MCP 서버** 방식을 사용한다. 이미 검증된 서버를 쓰는 게 가장 빠르다.

### 핵심 원칙

> **Claude가 설정을 대신 수행한다. 사용자는 결과만 확인한다.**

`claude mcp add` 명령어 한 줄로 서버를 등록하고,
`/mcp` 명령으로 연결 상태를 함께 확인한다.

### 도구별 MCP 서버

| 도구 | MCP 서버 | 설치 명령어 |
|------|---------|-----------|
| **Slack** | `@modelcontextprotocol/server-slack` | `claude mcp add slack -e SLACK_BOT_TOKEN=xoxb-...` |
| **Notion** | `@notionhq/notion-mcp-server` | `claude mcp add notion -e NOTION_API_KEY=secret_...` |
| **Google Sheets** | `@modelcontextprotocol/server-gdrive` | `claude mcp add gdrive` (OAuth 방식) |

## EXECUTE

아래 중 어떤 도구를 연결할지 확인한다:

```json
AskUserQuestion({
  "questions": [{
    "question": "Block 0에서 선택한 도구 중 지금 연결할 것을 선택해주세요.",
    "header": "연결 도구",
    "options": [
      {"label": "Slack", "description": "SLACK_BOT_TOKEN이 필요해요"},
      {"label": "Notion", "description": "NOTION_API_KEY가 필요해요"},
      {"label": "Google Sheets", "description": "Google 계정 OAuth 인증이 필요해요"},
      {"label": "모두 연결", "description": "선택한 도구 전부 순서대로 연결"}
    ],
    "multiSelect": false
  }]
})
```

선택 후 Claude가:
1. 해당 도구의 MCP 서버를 `.mcp.json`에 등록한다
2. 필요한 토큰/키 입력 방법을 안내한다
3. `/mcp` 명령으로 연결 상태를 확인한다
4. 연결 성공 시 실제 데이터 1건을 테스트로 가져온다

## QUIZ

```json
AskUserQuestion({
  "questions": [{
    "question": "MCP 서버 방식의 핵심 장점은 무엇인가요?",
    "header": "Block 2 퀴즈",
    "options": [
      {"label": "무료로 사용할 수 있다", "description": ""},
      {"label": "이미 만들어진 연결 모듈을 그대로 쓸 수 있어 빠르고 안정적이다", "description": ""},
      {"label": "Claude가 더 빠르게 응답한다", "description": ""},
      {"label": "코드를 직접 작성할 필요가 없다", "description": ""}
    ],
    "multiSelect": false
  }]
})
```

정답: **두 번째** — 이미 만들어진 연결 모듈을 그대로 쓸 수 있어 빠르고 안정적이다

오답 시 피드백:
- 1번: 비용은 MCP 방식의 핵심 장점이 아님
- 3번: 응답 속도와 무관
- 4번: API 방식도 Claude가 코드를 작성하므로 이것만의 장점은 아님
