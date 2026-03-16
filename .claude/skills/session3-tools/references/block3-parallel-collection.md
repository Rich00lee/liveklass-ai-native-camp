> 공식 문서: https://docs.anthropic.com/ko/docs/claude-code/sub-agents

## EXPLAIN

### 병렬 수집이란?

여러 도구에서 동시에 데이터를 가져오는 것.

**순차 수집** (느림):
```
Slack 조회 (3초) → Notion 조회 (3초) → GSheets 조회 (3초) = 9초
```

**병렬 수집** (빠름):
```
Slack 조회 ─┐
Notion 조회 ─┼─ 동시 실행 = 3초
GSheets 조회 ─┘
```

어떻게? **subagent**를 사용한다.
Claude가 여러 명의 Claude를 동시에 호출해서 각자 다른 도구에서 데이터를 가져오게 한다.

### 수집 후 검증

수집이 끝나면 반드시 결과를 검증한다:

| 상태 | 조치 |
|------|------|
| ✅ 성공 | 수집된 데이터 품질 확인 (너무 많거나 적지 않은지) |
| ❌ 실패 | 에러 메시지 확인 → 토큰/권한 문제인지 MCP 연결 문제인지 구분 → 재시도 |

## EXECUTE

Claude가 subagent를 사용해서 선택한 도구들에서 병렬로 데이터를 수집한다:

```
각 도구에서 수집할 내용:
- Slack: 최근 24시간 내 중요 메시지 (멘션, 키워드 포함 메시지)
- Notion: 오늘 마감 할일 + 업데이트된 페이지
- Google Sheets: 지정한 시트의 최신 데이터 요약
```

수집 완료 후:
1. 성공/실패 결과를 도구별로 보여준다
2. 수집된 데이터 샘플을 보여준다 (너무 많으면 첫 3건만)
3. "이 내용이 맞나요?" 확인을 요청한다

## QUIZ

```json
AskUserQuestion({
  "questions": [{
    "question": "subagent로 병렬 수집을 하는 가장 큰 이유는?",
    "header": "Block 3 퀴즈",
    "options": [
      {"label": "Claude를 여러 개 동시에 쓸 수 있어서 비용이 줄어든다", "description": ""},
      {"label": "여러 도구에서 동시에 데이터를 가져와 전체 시간을 단축한다", "description": ""},
      {"label": "MCP 서버 연결이 더 안정적이다", "description": ""},
      {"label": "데이터 오류가 줄어든다", "description": ""}
    ],
    "multiSelect": false
  }]
})
```

정답: **두 번째** — 여러 도구에서 동시에 데이터를 가져와 전체 시간을 단축한다

오답 시 피드백:
- 1번: subagent는 비용을 줄이지 않음 (오히려 API 호출이 늘어남)
- 3번: 병렬과 안정성은 직접적 관계 없음
- 4번: 데이터 오류는 검증 단계에서 처리
