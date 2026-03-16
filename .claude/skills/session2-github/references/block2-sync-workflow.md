# Block 2: 회사 ↔ 집 동기화 워크플로우

> 공식 문서: https://docs.github.com/ko/repositories/creating-and-managing-repositories/cloning-a-repository
> 공식 문서: https://docs.github.com/ko/get-started/using-git/getting-changes-from-a-remote-repository

---

## EXPLAIN

### 핵심 3가지 동작

GitHub 동기화는 딱 3가지만 알면 됩니다:

| 동작 | 언제 | 비유 |
|------|------|------|
| **clone** | 처음 한 번만 | 클라우드 세이브를 새 기기에 다운로드 |
| **pull** | 작업 시작할 때마다 | 최신 세이브 불러오기 |
| **push** | 작업 끝날 때마다 | 클라우드에 세이브 업로드 |

### 일상 동기화 루틴

```
🏢 회사 컴퓨터                    🏠 집 컴퓨터
───────────────                ──────────────
                               [최초 1회] clone
                                    │
   ┌──────────────────────────────────┘
   │
[출근] pull (최신 상태로)
   │
[작업] CLAUDE.md 수정,
       새 스킬 추가 등
   │
[퇴근] push (변경사항 올리기)
   │
   └──────────────────────────────────┐
                                      │
                               [귀가] pull
                                      │
                               [작업] 이어서 작업
                                      │
                               [잠들기 전] push
                                      │
   ┌──────────────────────────────────┘
   │
[다음날 출근] pull ...
```

### Claude에게 시키는 방법

매번 git 명령어를 기억할 필요 없어요. Claude에게 자연어로 말하세요:

| 상황 | Claude에게 할 말 |
|------|-----------------|
| 작업 시작 | "최신 상태로 맞춰줘" |
| 작업 끝 | "오늘 바꾼 거 올려줘" |
| 새 컴퓨터에서 처음 | "내 설정 repo 받아와줘" |
| 뭔가 꼬였을 때 | "git 상태 확인해줘" |

---

## EXECUTE

### 실습 1: 파일 수정 → push 체험

Block 1에서 올린 repo에서 연습합니다.

#### Step 1. 파일 하나 수정하기

CLAUDE.md를 열어서 아무 내용이나 한 줄 추가하세요.

예시:
```markdown
## 오늘 배운 것
- GitHub로 설정을 관리할 수 있다
```

#### Step 2. 변경사항 올리기

Claude에게: **"바뀐 내용 GitHub에 올려줘"**

또는 직접:
```bash
git add .
git commit -m "CLAUDE.md에 오늘 배운 것 추가"
git push
```

#### Step 3. GitHub에서 확인

```bash
gh repo view --web
```

브라우저에서 방금 수정한 내용이 반영되어 있는지 확인하세요.

### 실습 2: 다른 환경에서 받아오기 (시뮬레이션)

집에 가서 할 작업을 미리 연습합니다.

#### Step 1. clone (처음 받아오기)

집 컴퓨터에서 처음으로 내 설정을 받아올 때:

```bash
# 다른 폴더에서 clone 체험 (시뮬레이션)
cd /tmp
gh repo clone my-claude-settings my-claude-settings-test
cd my-claude-settings-test
ls -la
```

또는 Claude에게: **"내 my-claude-settings repo를 여기에 받아와줘"**

#### Step 2. 내용 확인

```bash
cat CLAUDE.md
```

아까 수정한 내용이 그대로 있으면 성공!

#### Step 3. pull (최신 상태로 업데이트)

이미 clone한 상태에서 최신 변경사항을 가져올 때:

```bash
git pull
```

또는 Claude에게: **"최신 상태로 맞춰줘"**

### 일상 루틴 요약

```
[작업 시작] Claude에게 "최신 상태로 맞춰줘" (= git pull)
[작업 중]   평소처럼 CLAUDE.md 수정, 스킬 만들기 등
[작업 끝]   Claude에게 "바꾼 거 올려줘" (= git add + commit + push)
```

이것만 기억하면 됩니다! 명령어는 Claude가 대신 쳐줍니다.

---

## QUIZ

```json
AskUserQuestion({
  "questions": [{
    "question": "회사에서 CLAUDE.md를 수정했습니다. 집에서 이어서 작업하려면 어떤 순서가 맞을까요?",
    "header": "동기화 순서",
    "options": [
      {"label": "회사: push → 집: pull", "description": "회사에서 올리고(push), 집에서 받아오기(pull)"},
      {"label": "회사: pull → 집: push", "description": "회사에서 받아오고(pull), 집에서 올리기(push)"},
      {"label": "회사: clone → 집: clone", "description": "양쪽 다 clone으로 새로 받기"},
      {"label": "회사: commit → 집: commit", "description": "양쪽 다 commit만 하기"}
    ],
    "multiSelect": false
  }]
})
```

정답: **회사: push → 집: pull**

- **push** = 내 변경사항을 GitHub에 올린다 (회사에서 퇴근 전)
- **pull** = GitHub에서 최신 변경사항을 가져온다 (집에 도착 후)
- clone은 처음 한 번만. 이후로는 pull로 최신화
- commit만으로는 GitHub에 올라가지 않음 (push까지 해야 함)

### 세션 마무리

축하합니다! 이제 여러분은:
- ✅ Git과 GitHub가 뭔지 안다
- ✅ 내 설정을 Private repo에 올릴 수 있다
- ✅ 회사 ↔ 집 동기화 루틴을 안다
- ✅ Claude에게 "올려줘", "받아줘"만 말하면 된다

**다음 세션(Session 3)에서는** Slack, Notion, Google Sheets를 Claude에 연결해서 더 강력한 자동화를 만들어볼 거예요!
