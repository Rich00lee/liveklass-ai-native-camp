> 공식 문서: https://docs.anthropic.com/ko/docs/claude-code/skills

## EXPLAIN

### Output 형식 선택

수집한 데이터를 어떻게 보여줄지 결정한다.
같은 데이터도 형식에 따라 활용도가 완전히 달라진다.

| 형식 | 특징 | 추천 상황 |
|------|------|----------|
| **마크다운 문서** | 터미널에서 바로 읽기 좋은 구조화된 텍스트 | 개인 브리핑, 기록용 |
| **Slack 메시지** | Slack에 바로 붙여넣을 수 있는 포맷 | 팀 공유, 데일리 스탠드업 |
| **Notion 페이지** | Notion에 자동 저장되는 일일 기록 | 아카이빙, 팀 공유 |

### 핵심: 간결함

브리핑은 짧을수록 좋다.

```
❌ 나쁜 예: Slack 메시지 50개를 전부 출력
✅ 좋은 예: 핵심 3-5개만 요약 + 원문 링크
```

## EXECUTE

아래에서 Output 형식을 선택한다:

```json
AskUserQuestion({
  "questions": [{
    "question": "수집한 컨텍스트를 어떤 형식으로 받고 싶으세요?",
    "header": "Output 형식",
    "options": [
      {"label": "마크다운 문서", "description": "터미널에서 바로 읽는 깔끔한 브리핑"},
      {"label": "Slack 메시지", "description": "팀 채널에 바로 공유할 수 있는 포맷"},
      {"label": "Notion 페이지", "description": "오늘 날짜로 Notion에 자동 저장"}
    ],
    "multiSelect": false
  }]
})
```

선택 후 Claude가:
1. `my-context-sync/SKILL.md`의 Output 섹션을 선택한 형식에 맞게 수정한다
2. 수정된 내용을 보여준다

## QUIZ

```json
AskUserQuestion({
  "questions": [{
    "question": "좋은 컨텍스트 브리핑의 핵심 원칙은?",
    "header": "Block 4 퀴즈",
    "options": [
      {"label": "가능한 많은 정보를 담는다", "description": ""},
      {"label": "핵심만 간결하게, 원문은 링크로", "description": ""},
      {"label": "매일 동일한 형식을 유지한다", "description": ""},
      {"label": "팀원이 이해하기 쉬운 언어로 작성한다", "description": ""}
    ],
    "multiSelect": false
  }]
})
```

정답: **두 번째** — 핵심만 간결하게, 원문은 링크로

오답 시 피드백:
- 1번: 정보가 많을수록 읽히지 않음
- 3번: 형식 일관성은 좋지만 핵심 원칙은 아님
- 4번: 개인 브리핑이므로 팀원보다 본인 기준이 우선
