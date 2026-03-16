> 공식 문서: https://docs.github.com/ko/pull-requests/collaborating-with-pull-requests/proposing-changes-to-your-work-with-pull-requests/creating-a-pull-request
> 공식 문서: https://docs.github.com/ko/pull-requests/collaborating-with-pull-requests/proposing-changes-to-your-work-with-pull-requests/about-pull-requests

## EXPLAIN

### PR(Pull Request)이란?

**비유: 회사에서 기안서 올리기**
- 내가 작업한 내용을 "이렇게 했는데 봐주세요"라고 올리는 것
- 다른 사람이 확인하고 "좋아요!" 하면 원본에 합쳐진다
- 피드백이 있으면 "여기 수정해주세요"라고 댓글을 달 수 있다

### PR의 3단계

```
① commit (저장)
   "여기까지 작업 완료!"
   → 내 컴퓨터에 변경사항을 기록한다

② push (업로드)
   "GitHub에 올려!"
   → 내 브랜치를 GitHub 서버에 올린다

③ PR 생성 (검토 요청)
   "이거 봐주세요!"
   → GitHub에서 "합쳐주세요" 요청을 만든다
```

### PR에 들어가는 내용

| 항목 | 설명 | 예시 |
|------|------|------|
| **제목** | 한 줄 요약 | "Add vivi showcase — CS 자동 응답" |
| **설명** | 상세 내용 | "캠프에서 만든 CS 자동 응답 스킬과 발표 자료입니다" |
| **변경 파일** | 자동으로 표시됨 | submissions/vivi/SHOWCASE.md 등 |

## EXECUTE

Claude에게 아래 순서대로 시켜보세요:

**1단계: 변경사항 확인**
```
"lk-ai-camp-showcase에서 내가 뭘 변경했는지 보여줘"
```

**2단계: 커밋 + 푸시**
```
"변경한 파일들을 커밋하고 GitHub에 푸시해줘.
커밋 메시지는 'Add 내이름 showcase'로 해줘"
```

**3단계: PR 생성**
```
"지금 브랜치로 PR을 만들어줘.
제목: 'Add 내이름 showcase — [만든 것 한 줄 요약]'
설명: '캠프에서 만든 [설명]입니다'"
```

> 💡 Claude가 `git add`, `git commit`, `git push`, `gh pr create`를 전부 대신 해줍니다.
> PR이 만들어지면 GitHub URL이 나옵니다. 브라우저에서 확인해보세요!

**4단계: PR 확인**
```
"내가 만든 PR 보여줘"
```

브라우저에서 PR 페이지를 열어보면:
- 내가 변경한 파일 목록이 보인다
- 다른 사람이 댓글을 달 수 있는 공간이 있다
- "Merge" 버튼으로 원본에 합칠 수 있다 (지금은 누르지 마세요!)

## QUIZ

```json
AskUserQuestion({
  "questions": [{
    "question": "PR(Pull Request)을 회사 업무에 비유하면 뭘까요?",
    "header": "Block 2 퀴즈",
    "options": [
      {"label": "A. 퇴근 신청"},
      {"label": "B. 기안서/결재 요청 — '이렇게 했는데 확인해주세요'"},
      {"label": "C. 회의록 작성"},
      {"label": "D. 이메일 발송"}
    ],
    "multiSelect": false
  }]
})
```

정답: **B**
- PR = 기안서와 같다. "이렇게 변경했습니다. 확인해주세요"
- 확인(리뷰)이 끝나면 승인(merge)된다
- 필요하면 수정 요청(코멘트)이 들어온다
- 이렇게 하면 원본이 항상 검증된 상태로 유지된다
