---
name: session2-github
description: LiveKlass AI Native Camp 2회차. Git & GitHub로 내 설정을 관리하고 여러 환경에서 동기화하기. "2회차", "Session 2", "GitHub", "git", "설정 동기화", "환경 동기화" 요청에 사용.
---

# Session 2: GitHub로 내 설정 관리하기

이 스킬이 호출되면 아래 **STOP PROTOCOL**을 반드시 따른다.

---

## 용어 정리

| 용어 | 설명 |
|------|------|
| **Git** | 파일의 변경 이력을 기록하는 도구. 게임의 "세이브 포인트"와 같다 |
| **GitHub** | Git으로 저장한 이력을 인터넷에 올리는 서비스. 어디서든 접근 가능 |
| **Repository (repo)** | 프로젝트 파일 + 변경 이력을 담는 저장소. "폴더의 업그레이드 버전" |
| **Private repo** | 나만 볼 수 있는 저장소. 설정 파일처럼 개인적인 것을 올릴 때 사용 |
| **commit** | 변경사항을 세이브하는 행위. "여기까지 저장!" |
| **push** | 내 컴퓨터의 세이브를 GitHub(인터넷)에 올리는 것 |
| **pull** | GitHub에서 최신 세이브를 내 컴퓨터로 가져오는 것 |
| **clone** | 처음으로 GitHub에서 프로젝트를 내 컴퓨터에 복사하는 것 |
| **`.gitignore`** | "이 파일은 올리지 마"라고 Git에게 알려주는 설정 파일 |
| **`gh`** | GitHub CLI — 터미널에서 GitHub를 사용할 수 있게 해주는 도구 |

---

## STOP PROTOCOL — 절대 위반 금지

> 이 프로토콜은 이 스킬의 최우선 규칙이다.
> 아래 규칙을 위반하면 수업이 망가진다.

### 각 블록은 반드시 2턴에 걸쳐 진행한다

```
┌─ Phase A (첫 번째 턴) ──────────────────────────────┐
│ 1. references/에서 해당 블록 파일의 EXPLAIN 섹션을 읽는다    │
│ 2. 기능을 설명한다                                        │
│ 3. references/에서 해당 블록 파일의 EXECUTE 섹션을 읽는다    │
│ 4. "지금 직접 실행해보세요"라고 안내한다                     │
│ 5. ⛔ 여기서 반드시 STOP. 턴을 종료한다.                    │
│                                                          │
│ ❌ 절대 하지 않는 것: 퀴즈 출제, QUIZ 섹션 읽기             │
│ ❌ 절대 하지 않는 것: AskUserQuestion 호출 (Block 0 제외)   │
│ ❌ 절대 하지 않는 것: "실행해봤나요?" 질문                   │
│ ❌ 절대 하지 않는 것: 다음 블록 내용 미리 언급               │
│ ❌ 절대 하지 않는 것: Phase A 종료 문구 이후 추가 텍스트 출력 │
└──────────────────────────────────────────────────────────┘

  ⬇️ 사용자가 돌아와서 "했어", "완료", "다음" 등을 입력한다

┌─ Phase B (두 번째 턴) ──────────────────────────────┐
│ 1. references/에서 해당 블록 파일의 QUIZ 섹션을 읽는다       │
│ 2. AskUserQuestion으로 퀴즈를 출제한다                     │
│ 3. 정답/오답 피드백을 준다                                 │
│ 4. 다음 블록으로 이동할지 AskUserQuestion으로 묻는다         │
│ 5. ⛔ 다음 블록을 시작하면 다시 Phase A부터.                │
└──────────────────────────────────────────────────────────┘
```

### 핵심 금지 사항 (절대 위반 금지)

1. **Phase A에서 AskUserQuestion을 호출하지 않는다 (Block 0 제외)** — Block 0은 사전 확인이 필수이므로 예외
2. **Phase A에서 퀴즈를 내지 않는다** — QUIZ 섹션은 Phase B에서만 읽는다
3. **Phase A에서 "실행해봤나요?"를 묻지 않는다** — 사용자가 먼저 말할 때까지 기다린다
4. **한 턴에 EXPLAIN + QUIZ를 동시에 하지 않는다** — 반드시 2턴으로 나눈다
5. **Phase A 종료 문구 이후 어떤 도구 호출이나 추가 텍스트도 출력하지 않는다**

### 공식 문서 URL 출력 (절대 누락 금지)

모든 블록의 Phase A 시작 시, 해당 reference 파일 상단의 `> 공식 문서:` URL을 **반드시 그대로 출력**한다.

```
📖 공식 문서: [URL]
```

- reference 파일에 URL이 여러 개 있으면 전부 출력한다
- URL을 요약하거나 생략하지 않는다

### Phase A 종료 시 필수 문구

Phase A의 마지막에는 반드시 아래 문구를 출력하고 Stop한다:

```
---
👆 위 내용을 직접 실행해보세요.
실행이 끝나면 "완료" 또는 "다음"이라고 입력해주세요.
```

---

## 블록 특수 규칙

- **Block 0 (Git 기본 + GitHub 계정)**: Phase A에서 Git/GitHub 개념 설명 + AskUserQuestion으로 GitHub 계정 유무 확인. 계정 없으면 가입 안내, 있으면 `gh auth login` 실행 안내 → Stop. Phase B에서 퀴즈.
- **Block 1 (내 설정 올리기)**: Phase A에서 private repo 개념 + `.gitignore` 설명 + Claude가 repo 생성·push 대행하는 방법 안내 → Stop. Phase B에서 퀴즈.
- **Block 2 (동기화 워크플로우)**: Phase A에서 clone/pull/push 워크플로우 설명 + 실습 시나리오(파일 수정 → push → pull) 안내 → Stop. Phase B에서 퀴즈 + 세션 마무리.

### Block 0 예외 규칙

Block 0의 Phase A는 **AskUserQuestion을 사용**한다. GitHub 계정 유무에 따라 진행 방식이 달라지므로 반드시 사용자 입력을 받아야 한다.

Phase A 진행 순서:
1. `references/block0-git-basics.md`의 EXPLAIN 섹션을 읽고 설명한다
2. AskUserQuestion으로 GitHub 계정 유무를 확인한다
3. 계정 유무에 따라 EXECUTE 섹션의 해당 경로를 안내한다
4. Stop한다

---

## References 파일 맵

| 블록 | 파일 | 내용 |
|------|------|------|
| Block 0 | `references/block0-git-basics.md` | Git/GitHub 개념 + 계정 만들기 + gh CLI 설치 |
| Block 1 | `references/block1-first-push.md` | Private repo 생성 + .gitignore + 첫 push |
| Block 2 | `references/block2-sync-workflow.md` | clone/pull/push 동기화 루틴 |

---

## 진행 규칙

- 한 번에 한 블록씩 진행한다
- "다음", "skip", 블록 번호/이름으로 이동한다
- 참가자 대부분이 Git을 처음 접하므로, 용어를 최대한 쉽게 비유로 풀어 설명한다
- **Claude Code가 git 명령어를 대신 실행해주는 경험**이 핵심 — 참가자가 명령어를 외울 필요 없음
- 실습 시 Claude에게 자연어로 시키는 것을 권장 (예: "이 파일 올려줘", "최신 상태로 맞춰줘")
- Git 설정에서 막히는 참가자에게는 `/git-onboarding-auto` 플러그인을 안내한다 (환경 점검 → 설정까지 자동 처리)

---

## 시작 — 복습 + MCP 점검 (5분)

Block으로 넘어가기 전에, **Session 1 과제 복습 + MCP 연결 상태 점검**을 먼저 진행한다.

### 과제 공유 (2분)

참가자에게 간단히 물어본다:
- "Slack MCP 연결해보셨나요? 어땠어요?"
- "Claude에게 3번 질문 중 가장 좋았던 Q&A 공유해주세요"

### MCP 연결 상태 점검 (3분)

Session 1에서 Slack MCP를 연결하는 과제를 했으므로, 지금 상태가 정상인지 함께 확인한다.
참가자에게 아래 3가지를 **Claude에게 자연어로 시켜보라고** 안내한다:

```
1️⃣ "내 MCP 설정 파일 보여줘"
   → Claude가 ~/.claude/mcp.json을 읽어서 어떤 서버가 설정돼 있는지 보여준다

2️⃣ "Slack에서 #lk-ai-camp 채널 최근 메시지 3개 읽어줘"
   → 성공하면 MCP 연결 정상! 실패하면 아래 트러블슈팅 참고

3️⃣ (실패한 경우) "MCP 연결이 안 돼. 도와줘"
   → Claude가 자동으로 설정 파일, 인증 상태 등을 점검해줄 수 있다
```

**자주 발생하는 문제와 해결법:**

| 증상 | 원인 | 해결 |
|------|------|------|
| "MCP 서버를 찾을 수 없다" | mcp.json에 서버가 없음 | Session 1 과제 가이드(`docs/slack-mcp-guide.md`) 다시 따라하기 |
| Slack 메시지 읽기 실패 | 토큰 만료 또는 권한 부족 | Claude Code 재시작 → 다시 시도 |
| 연결은 되는데 채널 접근 불가 | 봇이 채널에 미초대 | Slack에서 봇을 채널에 초대 |

> 5분 안에 해결 안 되면 앰버서더(Ian, Eddie)에게 DM으로 도움 요청하라고 안내한다.
> 점검 후 모두 확인되면 다음 단계로 넘어간다.

### Git 맛보기 — 교재 최신화 (2분)

MCP 점검이 끝나면, 본격적인 Git 학습 전에 **Git을 먼저 체험**시킨다.

진행자가 이렇게 말한다:
> "오늘 배울 Git이 뭔지, 설명 전에 먼저 한 번 써봅시다.
> 여러분이 클론한 캠프 교재가 어제 업데이트됐거든요. 한 줄이면 최신판을 받을 수 있습니다."

참가자에게 클론한 폴더에서 아래를 실행하라고 안내한다:

```bash
cd ~/liveklass-ai-native-camp && git pull
```

> 또는 Claude에게 "캠프 교재 폴더에서 최신 버전 받아줘"라고 시켜도 된다.

실행 후 참가자에게 짚어줄 포인트:
- "방금 한 줄로 바뀐 파일이 전부 최신화됐죠? 이게 **pull** 입니다"
- "오늘 Block 0에서 이 개념을 자세히 배울 거예요"
- "이런 식으로 회사에서 만든 설정을 집에서도 한 줄로 받을 수 있습니다"

---

### 블록 선택

아래 테이블을 보여주고 AskUserQuestion으로 어디서 시작할지 물어본다.

| Block | 주제 | 내용 |
|-------|------|------|
| 0 | Git 기본 | Git/GitHub가 뭔지 + 계정 만들기 |
| 1 | 내 설정 올리기 | Private repo 생성 + .gitignore + 첫 push |
| 2 | 동기화 워크플로우 | 회사 ↔ 집 동기화하는 일상 루틴 |

```json
AskUserQuestion({
  "questions": [{
    "question": "Session 2: GitHub로 내 설정 관리하기\n\n어디서부터 시작할까요?",
    "header": "시작 블록",
    "options": [
      {"label": "처음부터 (Block 0)", "description": "Git/GitHub 개념부터 차근차근"},
      {"label": "설정 올리기 (Block 1)", "description": "GitHub 계정은 있고, repo 만들기부터"},
      {"label": "동기화 (Block 2)", "description": "repo는 만들었고, 동기화 방법만"}
    ],
    "multiSelect": false
  }]
})
```
