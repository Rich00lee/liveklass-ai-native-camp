# Block 1: 내 설정을 GitHub에 올리기

> 공식 문서: https://docs.github.com/ko/repositories/creating-and-managing-repositories/creating-a-new-repository
> 공식 문서: https://docs.github.com/ko/get-started/getting-started-with-git/ignoring-files

---

## EXPLAIN

### 어떤 파일을 올릴까?

Claude Code를 쓰면서 만들어지는 파일들이 있어요:

| 파일/폴더 | 설명 | 올려야 할까? |
|-----------|------|-------------|
| `CLAUDE.md` | Claude에게 주는 지시서 (나의 스타일, 규칙) | ✅ 올리기 |
| `.claude/skills/` | 내가 만든 스킬들 | ✅ 올리기 |
| `.claude/settings.json` | Claude Code 설정 | ✅ 올리기 |
| `.claude/mcp.json` | MCP 서버 연결 정보 (API 토큰 포함 가능!) | ❌ 올리면 안 됨 |
| `.env` | 비밀번호, API 키 | ❌ 올리면 안 됨 |

### Private Repository

- **Public repo**: 누구나 볼 수 있는 저장소 (오픈소스 프로젝트용)
- **Private repo**: **나만** 볼 수 있는 저장소

내 CLAUDE.md, 스킬 같은 **개인 설정**은 반드시 **Private repo**에 올려야 해요.

### .gitignore — "이건 올리지 마"

`.gitignore` 파일은 Git에게 **"이 파일들은 추적하지 마"** 라고 알려주는 설정입니다.

왜 필요한가?
- `mcp.json`에 API 토큰이 들어있을 수 있다 → 인터넷에 올리면 보안 사고
- 토큰이 유출되면 다른 사람이 내 Slack, Notion에 접근할 수 있다

### Claude에게 시키면 됩니다

repo 만들기, 파일 올리기 — 이 모든 걸 Claude에게 자연어로 시킬 수 있어요.

"내 Claude 설정을 private GitHub repo에 올려줘" 한 마디면 Claude가:
1. repo를 만들고
2. `.gitignore`를 생성하고
3. 파일을 올려줍니다

---

## EXECUTE

### 실습 시나리오

아래 순서대로 진행합니다. Claude에게 시켜도 되고, 직접 해도 됩니다.

#### Step 1. 프로젝트 폴더 만들기

올리고 싶은 설정 파일이 있는 폴더로 이동하세요. 없다면 새로 만들어도 됩니다.

```bash
mkdir -p ~/my-claude-settings
cd ~/my-claude-settings
```

#### Step 2. 올릴 파일 복사하기

자신의 CLAUDE.md와 설정 파일을 이 폴더에 복사하세요:

```bash
# CLAUDE.md가 이미 있다면 복사
cp ~/.claude/CLAUDE.md ~/my-claude-settings/ 2>/dev/null

# 스킬 폴더가 있다면 복사
cp -r ~/.claude/skills ~/my-claude-settings/ 2>/dev/null
```

또는 Claude에게: **"내 CLAUDE.md랑 스킬 파일들을 ~/my-claude-settings에 모아줘"**

#### Step 3. .gitignore 만들기

```bash
# .gitignore 파일 생성
cat > .gitignore << 'EOF'
# 민감 정보 — 절대 올리면 안 되는 것
mcp.json
.env
*.key
*.pem
credentials.json
token.json

# OS 생성 파일
.DS_Store
Thumbs.db
EOF
```

또는 Claude에게: **"민감 정보 빼고 올릴 수 있게 .gitignore 만들어줘"**

#### Step 4. Private repo 만들기 + push

```bash
# Git 초기화
git init

# 파일 추가
git add .

# 첫 세이브 포인트
git commit -m "내 Claude 설정 첫 업로드"

# GitHub에 private repo 만들고 올리기
gh repo create my-claude-settings --private --source=. --push
```

또는 Claude에게: **"이 폴더를 private GitHub repo로 만들어서 올려줘"**

#### Step 5. 확인

```bash
# GitHub에 올라갔는지 확인
gh repo view --web
```

브라우저에서 내 repo가 보이면 성공!

---

## QUIZ

```json
AskUserQuestion({
  "questions": [{
    "question": ".gitignore 파일의 역할은?",
    "header": ".gitignore",
    "options": [
      {"label": "특정 파일을 Git이 추적하지 않게 한다", "description": "mcp.json 같은 민감 파일을 GitHub에 올리지 않도록 제외"},
      {"label": "GitHub에서 파일을 삭제한다", "description": "이미 올라간 파일을 지우는 기능"},
      {"label": "Git을 무시하고 강제로 올린다", "description": "ignore = 무시니까 Git의 규칙을 무시하는 것"},
      {"label": "비밀번호를 암호화해서 올린다", "description": "민감 정보를 암호화하여 안전하게 저장"}
    ],
    "multiSelect": false
  }]
})
```

정답: **특정 파일을 Git이 추적하지 않게 한다**

- `.gitignore`에 적힌 파일은 `git add .` 해도 추가되지 않는다
- API 토큰이 담긴 `mcp.json` 같은 민감 파일이 실수로 올라가는 것을 방지
- 한 번 올라간 파일은 `.gitignore`에 추가해도 자동 삭제되지 않으니 처음부터 설정하는 게 중요!
