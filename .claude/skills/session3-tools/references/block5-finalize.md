> 공식 문서: https://docs.anthropic.com/ko/docs/claude-code/skills

## EXPLAIN

### 완성된 스킬 확인

Block 0~4를 거치면 `.claude/skills/my-context-sync/SKILL.md`가 완성된다.

지금까지 한 것:
- ✅ Block 0: 도구 선택 + 스킬 골격 생성
- ✅ Block 1: 프로젝트 구조 파악
- ✅ Block 2: MCP 연결
- ✅ Block 3: 실제 데이터 수집 검증
- ✅ Block 4: Output 형식 설정

이제 **완성된 스킬을 처음부터 실행**해서 전체 흐름을 확인한다.

### 실무 정착 팁

스킬은 만드는 게 끝이 아니다. **매일 쓰는 게 핵심**이다.

```
매일 아침 Claude Code를 열면서 첫 번째로 실행:
/my-context-sync
```

점점 나아진다:
- 처음: 데이터가 너무 많거나 적음 → 수집 범위 조정
- 1주: 필요한 정보 파악 → 추출 조건 다듬기
- 1개월: 업무 시작 루틴으로 완전히 정착

## EXECUTE

최종 스킬을 실행한다:

```bash
/my-context-sync
```

실행 결과를 확인하고:
1. 데이터가 잘 수집됐는지 확인
2. Output 형식이 원하는 대로 나왔는지 확인
3. 개선이 필요한 부분 메모

## QUIZ

```json
AskUserQuestion({
  "questions": [{
    "question": "Session 2를 통해 가장 크게 달라진 것은 무엇인가요?",
    "header": "Session 2 마무리",
    "options": [
      {"label": "MCP가 뭔지 알게 됐다", "description": ""},
      {"label": "Claude가 외부 도구에 연결됐다", "description": ""},
      {"label": "매일 쓸 수 있는 나만의 컨텍스트 수집 스킬이 생겼다", "description": ""},
      {"label": "subagent 사용법을 배웠다", "description": ""}
    ],
    "multiSelect": false
  }]
})
```

정답: **세 번째** — 매일 쓸 수 있는 나만의 컨텍스트 수집 스킬이 생겼다

마무리 멘트:
```
수고하셨습니다! 🎉

오늘 만든 /my-context-sync는 Session 3에서 더 발전시킬 거예요.
다음 세션에서는 수집한 컨텍스트를 바탕으로
실제 업무를 자동화하는 스킬을 만들어볼게요.

숙제: 내일 아침 /my-context-sync 한 번 실행해보기.
결과가 어떤지 Session 3 시작 전에 공유해주세요!
```
