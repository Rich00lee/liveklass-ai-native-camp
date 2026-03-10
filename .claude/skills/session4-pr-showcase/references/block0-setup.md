> 공식 문서: https://docs.github.com/ko/repositories/creating-and-managing-repositories/cloning-a-repository
> 공식 문서: https://docs.github.com/ko/pull-requests/collaborating-with-pull-requests/proposing-changes-to-your-work-with-pull-requests/about-branches

## EXPLAIN

### 왜 브랜치를 쓰는가?

Session 2에서 배운 push는 **내 레포에 직접 저장**하는 거였다. 하지만 여러 사람이 같은 레포에서 작업할 때는 다르다.

**비유: 공유 문서 편집**
- Google Docs에서 여러 명이 동시에 편집하면 충돌이 생기죠?
- Git에서는 각자 **브랜치(복사본)**를 만들어서 작업하고, 다 되면 **PR(검토 요청)**을 보낸다
- 원본(main)은 항상 깨끗하게 유지된다

```
main (원본) ─────────────────────────────
    │
    ├── vivi/showcase (비비의 작업 공간) ──→ PR
    ├── terry/showcase (테리의 작업 공간) ──→ PR
    └── jay/showcase (제이의 작업 공간) ──→ PR
```

### 오늘의 흐름 미리보기

```
① clone (레포 복사) → ② branch (내 공간 생성) → ③ 작성 → ④ PR 제출 → ⑤ 리뷰
```

Session 2에서 배운 clone, commit, push를 복습하면서 branch와 PR을 새로 배운다.

## EXECUTE

Claude에게 아래 순서대로 시켜보세요:

**1단계: 레포 클론**
```
"https://github.com/Rich00lee/lk-ai-camp-showcase 레포를 내 홈 폴더에 클론해줘"
```

**2단계: 브랜치 생성**
```
"lk-ai-camp-showcase 폴더에서 '내이름/showcase' 브랜치를 만들어줘"
```
(예: `vivi/showcase`, `terry/showcase`)

**3단계: 확인**
```
"지금 어떤 브랜치에 있는지 확인해줘"
```

> 💡 Claude가 `git clone`, `git checkout -b`, `git branch` 명령어를 대신 실행해줍니다.
> 명령어를 외울 필요 없이 "~해줘"라고 말하면 됩니다.

## QUIZ

```json
AskUserQuestion({
  "questions": [{
    "question": "브랜치(branch)는 왜 쓰는 걸까요?",
    "header": "Block 0 퀴즈",
    "options": [
      {"label": "A. 파일을 삭제하기 위해"},
      {"label": "B. 원본을 건드리지 않고 내 작업 공간을 따로 만들기 위해"},
      {"label": "C. GitHub 계정을 여러 개 만들기 위해"},
      {"label": "D. 인터넷 없이 작업하기 위해"}
    ],
    "multiSelect": false
  }]
})
```

정답: **B**
- 브랜치는 원본(main)을 안전하게 보호하면서, 각자 독립적으로 작업할 수 있게 해준다
- 작업이 끝나면 PR을 통해 원본에 합친다
