> 공식 문서: https://docs.github.com/ko/pull-requests/collaborating-with-pull-requests/reviewing-changes-in-pull-requests/about-pull-request-reviews
> 공식 문서: https://docs.github.com/ko/pull-requests/collaborating-with-pull-requests/reviewing-changes-in-pull-requests/commenting-on-a-pull-request

## EXPLAIN

### PR 리뷰란?

다른 사람의 PR을 보고 **피드백(댓글)**을 다는 것이다.

Session 3에서 서로의 스킬을 피어리뷰했던 것과 같다. 차이는 이번엔 **GitHub 위에서** 한다는 것.

### 좋은 리뷰의 3가지 원칙

1. **구체적으로**: "좋아요" → "병목 분석이 구체적이어서 공감됐어요. 특히 시간 비교 부분이 인상적"
2. **질문으로**: "이거 왜 이렇게 했어요?" → "이 부분은 Slack 연동도 고려해봤나요?"
3. **격려와 함께**: 잘한 점 먼저, 개선점은 제안으로

### 리뷰 코멘트 템플릿

```
👍 잘한 점: [구체적으로 뭐가 좋았는지]
💡 제안: [이렇게 하면 더 좋을 것 같다]
❓ 궁금한 점: [더 알고 싶은 부분]
```

### GitHub에서 리뷰하는 방법

1. PR 페이지에서 **"Files changed"** 탭 클릭
2. 코멘트를 달고 싶은 줄 옆의 **"+"** 버튼 클릭
3. 코멘트 작성 후 **"Add single comment"** 또는 **"Start a review"** 클릭
4. 모든 코멘트를 달았으면 **"Review changes"** → **"Approve"** 클릭

### Session 5 안내

**Session 5: 사내 공유회** (3/13 금 10:15~11:45)

발표 포맷:
- 인당 최대 **5분** + 소감
- SHOWCASE.md 기반으로 발표
- 오프라인 참가자 이벤트 & 질문 참여 가능

Session 5 전까지 할 것:
- [ ] PR에 달린 리뷰 피드백 반영
- [ ] SHOWCASE.md 최종 다듬기
- [ ] 발표 당일 보여줄 실행 결과/데모 준비

## EXECUTE

**1단계: 다른 사람의 PR 찾기**

Claude에게 시켜보세요:
```
"lk-ai-camp-showcase 레포에 올라온 PR 목록 보여줘"
```

**2단계: PR 리뷰하기**

브라우저에서 다른 사람의 PR을 열고:
1. "Files changed" 탭에서 SHOWCASE.md를 읽는다
2. 아래 템플릿을 참고해서 코멘트를 2개 이상 단다:

```
👍 잘한 점: ___
💡 제안: ___
❓ 궁금한 점: ___
```

> 💡 브라우저에서 직접 하는 게 어려우면, Claude에게 시킬 수도 있어요:
> ```
> "[이름]의 PR에 이 코멘트를 달아줘: [내용]"
> ```

**3단계: 리뷰 완료**

코멘트를 다 달았으면 "Review changes" → "Approve" 버튼을 눌러주세요.

**4단계: 내 PR에 달린 피드백 확인**
```
"내 PR에 달린 코멘트 보여줘"
```

피드백을 보고 SHOWCASE.md를 수정하고 싶으면:
```
"피드백 반영해서 SHOWCASE.md 수정하고 다시 푸시해줘"
```

## QUIZ

```json
AskUserQuestion({
  "questions": [{
    "question": "좋은 PR 리뷰의 원칙이 아닌 것은?",
    "header": "Block 3 퀴즈",
    "options": [
      {"label": "A. 구체적으로 피드백한다"},
      {"label": "B. 잘한 점을 먼저 언급한다"},
      {"label": "C. '별로예요'라고만 쓴다"},
      {"label": "D. 개선점은 제안 형태로 쓴다"}
    ],
    "multiSelect": false
  }]
})
```

정답: **C**
- "별로예요"는 상대방에게 도움이 안 된다
- 뭐가 별로인지, 어떻게 하면 좋을지를 구체적으로 써야 좋은 리뷰
- 좋은 리뷰 = 구체적 + 격려 + 제안
