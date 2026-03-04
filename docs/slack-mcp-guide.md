# Session 1 과제: Slack MCP 연결 가이드

> 이 가이드를 따라하면 Claude Code에서 직접 `#lk-ai-camp` 채널에 메시지를 보낼 수 있어요!
> 막히면 앰버서더(Ian, Eddie)에게 DM 주세요.

---

## Step 1: mcp.json 파일 열기

Claude Code 터미널에서 이렇게 말하세요:

```
~/.claude/mcp.json 파일을 열어줘
```

> 이 파일이 Claude가 외부 도구(Slack, Notion 등)와 연결하는 설정 파일이에요.
> 파일이 없으면 Claude가 만들어줍니다.

---

## Step 2: Slack MCP 설정 추가

Claude에게 이렇게 말하세요:

```
mcp.json에 아래 Slack 설정을 추가해줘:

서버 이름: slack-ai-native-camp
command: npx
args: ["-y", "slack-mcp-server@latest", "--transport", "stdio"]
환경변수:
  SLACK_BOT_TOKEN: (채널에 공유된 토큰)
  SLACK_TEAM_ID: (채널에 공유된 팀 ID)
```

> **토큰과 팀 ID는 `#lk-ai-camp` 채널 상단 고정 메시지에서 확인하세요.**
> 보안상 이 문서에는 직접 적지 않습니다.

### 완성된 mcp.json 예시

```json
{
  "mcpServers": {
    "slack-ai-native-camp": {
      "command": "npx",
      "args": ["-y", "slack-mcp-server@latest", "--transport", "stdio"],
      "env": {
        "SLACK_BOT_TOKEN": "여기에-토큰-붙여넣기",
        "SLACK_TEAM_ID": "여기에-팀ID-붙여넣기"
      }
    }
  }
}
```

> 이미 다른 MCP 설정이 있다면 `"mcpServers": { }` 안에 추가하면 됩니다.

---

## Step 3: Claude Code 재시작

설정을 저장한 후 Claude Code를 한번 종료했다가 다시 시작하세요:

```
exit
```

그리고 다시:
```
claude
```

---

## Step 4: 연결 확인

Claude Code가 다시 켜지면, 이렇게 물어보세요:

```
Slack MCP가 잘 연결됐는지 확인해줘
```

또는 `/mcp` 명령어로 직접 확인:
```
/mcp
```

`slack-ai-native-camp` 서버가 **connected** 상태면 성공!

---

## Step 5: 채널에 메시지 보내기

연결이 됐으면, Claude에게 이렇게 말해보세요:

```
#lk-ai-camp 채널에 "안녕하세요! [내 이름]입니다. Slack MCP 연결 성공!" 이라고 보내줘
```

채널에 메시지가 올라오면 과제 1번 완료!

---

## 트러블슈팅

### "npx를 찾을 수 없다"는 에러

Node.js가 설치되어 있지 않아요. Claude에게:
```
Node.js 설치해줘
```

### "invalid_auth" 에러

토큰이 잘못 입력된 경우예요:
1. `#lk-ai-camp` 고정 메시지에서 토큰을 다시 복사
2. `mcp.json`의 `SLACK_BOT_TOKEN` 값을 다시 붙여넣기
3. Claude Code 재시작

### "channel_not_found" 에러

채널 이름이 정확한지 확인하세요:
- ✅ `#lk-ai-camp`
- ❌ `#lk-ai-native-camp` (다른 채널)

### 그래도 안 되면?

Claude에게 이렇게 물어보세요:
```
Slack MCP 연결이 안 돼. 에러 메시지를 확인하고 해결 방법을 알려줘.
```

Claude가 에러를 분석하고 해결 방법을 안내해줍니다.
안 되면 앰버서더(Ian, Eddie)에게 DM 주세요!

---

## 과제 2: Claude에게 3번 질문하기

Slack MCP 연결이 됐으면, 이제 본격 과제입니다.

### 할 일

Session 1에서 정한 **"해결하고 싶은 과제"** 에 대해 Claude에게 **3번 질문**해보세요.

### 올릴 내용

3번 중 **가장 마음에 든 질문과 답변 1개**를 골라서 `#lk-ai-camp` 채널에 올려주세요:

1. **질문과 답변** (스크린샷 또는 텍스트)
2. **왜 이 질문을 했는지**
3. **왜 이 답변이 가장 좋았는지**

### 올리는 방법

Claude에게 직접 시켜도 되고, 직접 올려도 됩니다:

```
#lk-ai-camp 채널에 아래 내용을 보내줘:

[Session 1 과제] 내 이름

질문: (내가 한 질문)
답변: (Claude의 답변 요약)

이 질문을 한 이유: ...
이 답변이 좋았던 이유: ...
```

---

## 마감

**Session 2 (3/5 목 20:00) 시작 전까지** 완료해주세요!
