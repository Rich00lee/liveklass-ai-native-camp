> 공식 문서: https://docs.anthropic.com/ko/docs/claude-code/mcp

## EXPLAIN

### MCP — 외부 도구 연결하기

MCP(Model Context Protocol)는 Claude Code에 **외부 도구를 플러그인처럼 연결**하는 표준 규격이다.

MCP 없이: Claude에게 "Slack 확인해줘" → "저는 Slack에 접근할 수 없어요"
MCP 있이: Claude에게 "Slack 확인해줘" → Slack에서 직접 메시지를 가져와서 요약해줌

**LiveKlass에서 쓸 MCP**:
| 도구 | 할 수 있는 것 |
|------|-------------|
| Slack MCP | 채널 메시지 읽기, 답글 작성 |
| Notion MCP | 페이지 읽기/쓰기, 데이터베이스 조회 |
| Google Sheets MCP | 시트 데이터 읽기/쓰기/분석 |

**MCP 연결 = Session 2의 핵심 주제**
오늘은 "이런 게 있구나"를 이해하는 것으로 충분하다.

**비유**: MCP는 스마트폰의 앱스토어 같은 것.
기본 Claude에 원하는 도구를 앱처럼 설치해서 기능을 확장할 수 있다.

## EXECUTE

MCP가 뭔지 Claude에게 직접 물어보세요:

```
MCP가 뭔지 쉽게 설명해줘.
그리고 라이브클래스 세일즈팀에서 MCP로 뭘 할 수 있는지
3가지 예시를 들어줘.
```

## QUIZ

AskUserQuestion으로 퀴즈 출제:

질문: "MCP가 없으면 Claude Code는 외부 도구(Slack, Notion 등)에 어떻게 접근할까요?"
- "직접 접근 가능" → "아니에요! MCP 없이는 Claude가 외부 도구에 접근하지 못해요. 데이터를 직접 붙여넣어야 해요."
- "접근 불가, 데이터를 직접 붙여넣어야 한다" → ✅ 정답! "MCP를 연결하면 이 작업이 자동화되어 훨씬 편해져요. Session 2에서 직접 연결해볼 거예요."
- "모르겠다" → 비유로 설명: "USB 포트가 없는 컴퓨터에 마우스를 연결하려면 어떻게 해야 할까요? MCP가 바로 그 USB 포트예요."
