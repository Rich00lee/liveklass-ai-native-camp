> 공식 문서: https://docs.anthropic.com/ko/docs/claude-code/mcp
> Notion API: https://developers.notion.com/

## EXPLAIN

### Notion MCP 연결하기

Notion MCP를 연결하면:
- 특정 페이지 내용 읽기
- 데이터베이스 조회 (고객사 목록, 파이프라인 등)
- 페이지 새로 만들기 / 업데이트
- 댓글 읽기/쓰기

**LiveKlass 활용 예시**:
- 파이프라인 Notion 데이터베이스 → Claude가 자동으로 분석
- 미팅 노트 → Notion에 자동 저장
- 고객사 온보딩 체크리스트 → 자동 업데이트

### 설치 절차

**Step 1**: Notion API 토큰 발급
- notion.so/my-integrations → "New integration" 생성
- Integration 이름: "Claude Code"
- Integration Type: Internal
- Generated token 복사 (`secret_...`)

**Step 2**: 사용할 Notion 페이지에 Integration 권한 부여
- Notion 페이지 → "..." 메뉴 → "Connections" → Claude Code 추가

**Step 3**: mcp.json에 추가

```json
{
  "mcpServers": {
    "notion": {
      "command": "npx",
      "args": ["-y", "@notionhq/notion-mcp-server"],
      "env": {
        "OPENAI_API_KEY": "notion-api-키-아님",
        "NOTION_API_KEY": "secret_여기에-토큰-붙여넣기"
      }
    }
  }
}
```

**Step 4**: Claude Code 재시작 → 연결 확인

### 연결 확인

```
Notion에서 [페이지 이름] 페이지 내용 요약해줘.
```

## EXECUTE

1. Notion Integration 생성 → 토큰 복사
2. 접근할 페이지에 Integration 권한 부여
3. `~/.claude/mcp.json`에 Notion 설정 추가
4. Claude Code 재시작
5. 테스트: "Notion에서 [페이지명] 읽어줘"

## QUIZ

AskUserQuestion으로 퀴즈 출제:

질문: "Notion MCP 연결에 성공했나요?"
- "성공!" → ✅ "이제 Notion을 Claude에서 직접 읽고 쓸 수 있어요."
- "아직 진행 중 / 오류" → 어느 단계에서 막혔는지 확인 후 도움

퀴즈 2: "Notion에서 가장 자주 참조하는 페이지는?"
→ 자유 답변. Session 3 자동화 아이디어에 활용.
