> 공식 문서: https://docs.anthropic.com/ko/docs/claude-code/sub-agents

## EXPLAIN

### Explore 에이전트란?

Claude Code에는 **전문화된 subagent**들이 내장되어 있다.
그 중 `Explore` 에이전트는 프로젝트 폴더 구조를 파악하는 데 특화되어 있다.

```
Task(subagent_type="Explore", prompt="...")
```

왜 쓰나?
- Claude는 대화 시작 시 프로젝트 구조를 모른다
- Explore가 먼저 구조를 파악하면 이후 모든 작업이 정확해진다
- 특히 스킬 생성, 파일 경로 설정에 필수

### 오늘 할 것

Explore 에이전트로 현재 프로젝트를 파악한다:
- `.claude/` 폴더 구조 (기존 스킬 목록)
- 현재 작업 디렉토리
- `my-context-sync` 스킬이 생성될 위치 확인

## EXECUTE

Claude가 Explore 에이전트를 실행해서 아래 내용을 파악한다:

1. 현재 프로젝트의 `.claude/skills/` 폴더 구조
2. `my-context-sync` 폴더 생성 여부 확인
3. 파악한 결과를 간단히 요약해서 보여준다

결과 예시:
```
현재 스킬 목록:
- my-context-sync/ (방금 생성됨)
  - SKILL.md ✅
- session1-onboarding/
- session2-tools/

my-context-sync/SKILL.md 경로: .claude/skills/my-context-sync/SKILL.md
```

## QUIZ

```json
AskUserQuestion({
  "questions": [{
    "question": "Explore 에이전트를 Block 1에서 먼저 실행하는 이유는?",
    "header": "Block 1 퀴즈",
    "options": [
      {"label": "Claude Code의 필수 기능이라서", "description": ""},
      {"label": "프로젝트 구조를 파악해야 이후 파일 경로를 정확히 지정할 수 있어서", "description": ""},
      {"label": "속도가 빠르기 때문에", "description": ""},
      {"label": "MCP 서버 연결 전에 필요한 절차라서", "description": ""}
    ],
    "multiSelect": false
  }]
})
```

정답: **두 번째** — 프로젝트 구조를 파악해야 이후 파일 경로를 정확히 지정할 수 있어서

오답 시 피드백:
- 1번: Explore는 선택적 도구
- 3번: 속도는 이유가 아님
- 4번: MCP 연결과 직접적인 관계 없음
