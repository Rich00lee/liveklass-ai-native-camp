> 공식 문서: https://docs.anthropic.com/ko/docs/claude-code/mcp
> Google Sheets API: https://developers.google.com/sheets

## EXPLAIN

### Google Sheets MCP 연결하기

Google Sheets MCP를 연결하면:
- 특정 시트 데이터 읽기
- 셀 값 업데이트
- 수식 적용
- 데이터 분석 후 결과를 시트에 바로 쓰기

**LiveKlass 활용 예시**:
- 세일즈 파이프라인 시트 → Claude가 자동으로 주간 리포트 생성
- VoC 시트 → 카테고리별 자동 분류 + 트렌드 분석
- 매출 데이터 → 예측 분석 + 시각화 코드 생성

### 설치 절차

**Step 1**: Google Cloud 프로젝트 생성 + OAuth 설정
- console.cloud.google.com → 새 프로젝트 생성
- "APIs & Services" → "Enable APIs" → "Google Sheets API" 활성화
- "OAuth consent screen" 설정 → "Credentials" → OAuth 2.0 Client ID 생성
- credentials.json 다운로드

**Step 2**: mcp.json에 추가

```json
{
  "mcpServers": {
    "google-sheets": {
      "command": "npx",
      "args": ["-y", "@modelcontextprotocol/server-google-sheets"],
      "env": {
        "GOOGLE_CREDENTIALS_PATH": "/Users/[이름]/.config/google-sheets-mcp/credentials.json"
      }
    }
  }
}
```

**Step 3**: 첫 실행 시 브라우저에서 Google 계정 인증

### 연결 확인

```
구글시트 [시트 이름 또는 URL]에서 데이터 읽어줘.
```

## EXECUTE

1. Google Cloud 프로젝트 생성 + Sheets API 활성화
2. OAuth credentials 다운로드
3. mcp.json에 설정 추가
4. Claude Code 재시작 → Google 계정 인증
5. 테스트: 실제 쓰는 시트 URL 붙여넣고 "이 데이터 분석해줘"

> 💡 이미 Google Sheets MCP가 설치되어 있는 분은 `/mcp`로 확인해보세요.

## QUIZ

AskUserQuestion으로 퀴즈 출제:

질문: "Google Sheets MCP 연결에 성공했나요?"
- "성공!" → ✅ "이제 구글시트 데이터를 Claude가 직접 읽어서 분석할 수 있어요!"
- "아직 진행 중 / 오류" → 단계별 확인 후 도움

퀴즈 2: "구글시트에서 Claude로 자동화하면 가장 도움이 될 작업은?"
→ 자유 답변. 파이프라인 분석 / VoC 정리 / 매출 리포트 등
