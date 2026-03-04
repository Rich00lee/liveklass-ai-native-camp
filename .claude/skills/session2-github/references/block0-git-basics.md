# Block 0: Git & GitHub 기본 개념

> 공식 문서: https://docs.github.com/ko/get-started/start-your-journey/about-github-and-git
> 공식 문서: https://cli.github.com/manual/

---

## EXPLAIN

### Git이 뭔가요?

여러분이 보고서를 쓸 때 이런 경험 있으세요?

```
보고서_최종.docx
보고서_최종_수정.docx
보고서_최종_진짜최종.docx
보고서_최종_진짜최종_v2.docx
```

**Git은 이 문제를 해결하는 도구입니다.**

- 파일 하나만 유지하면서, 변경할 때마다 **세이브 포인트**(commit)를 만든다
- 잘못되면 이전 세이브 포인트로 돌아갈 수 있다
- 언제, 뭘, 왜 바꿨는지 기록이 남는다

### GitHub는 뭔가요?

- **Git** = 내 컴퓨터에서 세이브 포인트를 만드는 도구
- **GitHub** = 세이브 포인트를 **인터넷에 올려서** 어디서든 쓸 수 있게 하는 서비스

비유하면:
| 개념 | 비유 |
|------|------|
| Git | 내 컴퓨터의 세이브 파일 |
| GitHub | 클라우드 세이브 (어디서든 이어하기) |
| commit | 세이브하기 |
| push | 클라우드에 업로드 |
| pull | 클라우드에서 다운로드 |

### 왜 필요한가요?

우리 캠프에서 GitHub가 필요한 이유:

1. **회사 ↔ 집 동기화**: 회사에서 만든 CLAUDE.md, Skill을 집에서도 쓸 수 있다
2. **버전 관리**: 설정을 바꿨다가 망해도 이전 상태로 돌아갈 수 있다
3. **Claude Code와 찰떡궁합**: Claude에게 "올려줘", "받아줘"만 말하면 git 명령어를 대신 실행해준다

### gh CLI — 터미널에서 GitHub 사용하기

`gh`는 GitHub의 공식 터미널 도구입니다. 브라우저를 열지 않고도 터미널에서 GitHub를 사용할 수 있어요.

---

## EXECUTE

### GitHub 계정이 없는 경우

1. 브라우저에서 https://github.com/signup 접속
2. 이메일, 비밀번호, 사용자 이름 입력
3. 이메일 인증 완료

### gh CLI 설치 (모든 참가자)

Mac에서:
```bash
brew install gh
```

> `brew`가 없다면 Claude에게 "brew 설치해줘"라고 말해보세요.

### GitHub 로그인

터미널에서 아래를 입력하세요:
```bash
gh auth login
```

선택지가 나오면:
1. **GitHub.com** 선택
2. **HTTPS** 선택
3. **Login with a web browser** 선택
4. 브라우저가 열리면 인증 완료

### 확인

로그인이 잘 됐는지 확인:
```bash
gh auth status
```

`Logged in to github.com` 이 보이면 성공!

---

## QUIZ

```json
AskUserQuestion({
  "questions": [{
    "question": "Git과 GitHub의 관계를 가장 잘 설명한 것은?",
    "header": "Git vs GitHub",
    "options": [
      {"label": "Git = 세이브, GitHub = 클라우드 세이브", "description": "Git은 내 컴퓨터에서 변경 기록, GitHub는 인터넷에 올려서 어디서든 접근"},
      {"label": "Git = 프로그래밍 언어, GitHub = 코드 에디터", "description": "Git은 코드를 작성하는 언어이고 GitHub는 편집기"},
      {"label": "Git = GitHub의 옛날 이름", "description": "같은 서비스의 이전 버전"},
      {"label": "Git = 무료, GitHub = 유료", "description": "기능은 같고 유료/무료 차이만 있다"}
    ],
    "multiSelect": false
  }]
})
```

정답: **Git = 세이브, GitHub = 클라우드 세이브**

- Git은 내 컴퓨터에서 파일 변경 이력을 기록하는 도구
- GitHub는 그 이력을 인터넷에 올려서 여러 컴퓨터에서 공유하는 서비스
- 둘은 서로 다른 것이지만, 함께 쓸 때 강력하다
