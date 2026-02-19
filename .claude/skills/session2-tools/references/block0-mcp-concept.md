> 공식 문서: https://docs.anthropic.com/ko/docs/claude-code/mcp
> MCP 서버 목록: https://github.com/modelcontextprotocol/servers

## EXPLAIN

### 오늘의 목표

Session 1에서 배운 MCP를 **실제로 설치하고 연결**한다.
세션이 끝나면: Slack, Notion, 구글시트를 Claude에서 직접 읽고 쓸 수 있게 된다.

### MCP 동작 원리

```
Claude Code
    ↓ (요청)
MCP 서버 (중간 다리)
    ↓ (API 호출)
외부 도구 (Slack / Notion / Google Sheets)
    ↑ (데이터 반환)
MCP 서버
    ↑ (결과 전달)
Claude Code → 사용자에게 응답
```

### MCP 설정 방법

설정 파일: `~/.claude/mcp.json`

```json
{
  "mcpServers": {
    "slack": { ... },
    "notion": { ... },
    "google-sheets": { ... }
  }
}
```

### 오늘 설치할 3가지

| 도구 | MCP 서버 | 설치 후 가능한 것 |
|------|----------|-----------------|
| Slack | ai-native-camp-slack | 채널 읽기, 메시지 요약, 스레드 확인 |
| Notion | claude_ai_Notion | 페이지 읽기/쓰기, 데이터베이스 조회 |
| Google Sheets | google-sheets | 시트 읽기/쓰기, 수식 적용, 데이터 분석 |

## EXECUTE

지금 현재 연결된 MCP를 확인해보세요:

Claude Code에 입력:
```
/mcp
```

→ 현재 연결된 MCP 목록이 나온다.
→ 없으면 "No MCP servers configured" 메시지가 보임.

## QUIZ

AskUserQuestion으로 퀴즈 출제:

질문: "MCP 없이도 Claude에게 Slack 메시지를 요약시킬 수 있을까요?"
- "가능하다" → "맞아요! 하지만 매번 메시지를 직접 복사해서 붙여넣어야 해요. MCP를 연결하면 Claude가 자동으로 가져와요."
- "불가능하다" → "가능하긴 해요! 다만 매번 복사-붙여넣기가 필요해요. MCP가 이 과정을 자동화해줘요."
