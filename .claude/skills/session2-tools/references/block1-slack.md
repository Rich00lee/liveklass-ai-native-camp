> 공식 문서: https://docs.anthropic.com/ko/docs/claude-code/mcp

## EXPLAIN

### Slack MCP 연결하기

Slack MCP를 연결하면:
- 특정 채널의 최근 메시지 읽기
- 스레드 내용 요약
- 언급된 액션 아이템 추출
- (쓰기 권한이 있으면) 메시지 발송도 가능

### 설치 절차

**Step 1**: Slack 앱에서 토큰 발급
- workspace.slack.com/apps → "Build" → "Create New App"
- OAuth & Permissions → "User Token Scopes" 추가:
  - `channels:history` (채널 읽기)
  - `channels:read` (채널 목록)
  - `groups:history` (비공개 채널)
  - `users:read` (사용자 정보)
- "Install to Workspace" → User OAuth Token 복사 (`xoxp-...`)

**Step 2**: mcp.json에 추가

```json
{
  "mcpServers": {
    "slack": {
      "command": "npx",
      "args": ["-y", "@modelcontextprotocol/server-slack"],
      "env": {
        "SLACK_BOT_TOKEN": "xoxp-여기에-토큰-붙여넣기",
        "SLACK_TEAM_ID": "워크스페이스-ID"
      }
    }
  }
}
```

**Step 3**: Claude Code 재시작 → `/mcp`로 연결 확인

### 연결 확인

```
Slack에서 #general 채널 최근 5개 메시지 보여줘.
```
→ 실제 메시지가 나오면 성공!

## EXECUTE

1. Slack 앱에서 토큰 발급 (위 Step 1 따라하기)
2. `~/.claude/mcp.json` 파일에 Slack 설정 추가
3. Claude Code 재시작
4. 연결 테스트: "Slack에서 #[채널명] 최근 메시지 요약해줘"

> ⚠️ 토큰이 외부에 노출되지 않도록 주의하세요. `.env` 파일에 저장하거나, `.gitignore`에 `mcp.json`을 추가하세요.

## QUIZ

AskUserQuestion으로 퀴즈 출제:

질문: "Slack MCP 연결에 성공했나요?"
- "성공! 메시지가 보인다" → ✅ "훌륭해요! 이제 Claude에게 Slack 요약을 자동으로 시킬 수 있어요."
- "아직 진행 중" → 어느 단계에서 막혔는지 확인 후 도움
- "오류 발생" → 에러 메시지 공유 요청 → 함께 해결

퀴즈 2: "Slack MCP로 가장 먼저 자동화하고 싶은 것은?"
→ 자유 답변. 기억해두고 Session 3에서 활용 예고.
