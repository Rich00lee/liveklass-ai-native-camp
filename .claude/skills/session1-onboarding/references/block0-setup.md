> 공식 문서: https://docs.anthropic.com/ko/docs/claude-code/setup
> 빠른 시작: https://docs.anthropic.com/ko/docs/claude-code/quickstart

## EXPLAIN

### Claude Code란?

터미널(terminal)에서 AI와 직접 대화하며 업무를 처리하는 도구입니다.
- 슬랙 요약, CS 응답 초안, 데이터 분석, 리포트 작성을 **동시에 병렬로** 처리 가능
- 개발자 도움 없이 **혼자** 할 수 있다

### 설치

| OS | 명령어 |
|----|--------|
| Mac / Linux | `curl -fsSL https://claude.ai/install.sh \| bash` |
| Windows (PowerShell) | `irm https://claude.ai/install.ps1 \| iex` |

**핵심**: Node.js 불필요, 한 줄 설치, 자동 업데이트 포함.

**설치 오류 시 해결법**:
- Mac 권한 오류 → `sudo` 앞에 붙여서 다시 실행
- 설치 후 `claude` 명령어 안 되면 → 터미널 재시작
- Windows 실행 정책 오류 → `Set-ExecutionPolicy RemoteSigned` 먼저 실행

### 첫 실행

터미널에 `claude` 입력 → Anthropic 계정 로그인 → Claude 플랜 확인 (Pro/Max/Teams/Enterprise 중 하나 필요)

### 출력 스타일 설정

설치 후 Claude Code 대화창에 `/output-style` 입력 → **Explanatory** 선택
→ Claude가 코드와 함께 이유도 설명해줌 (학습에 최적)

## EXECUTE

1. **설치**: 본인 OS에 맞는 명령어 실행
2. **첫 실행**: 터미널에 `claude` 입력
3. **로그인**: Anthropic 계정으로 인증
4. **첫 대화**: "안녕! 나는 [이름], 라이브클래스에서 [직군] 일해. 반가워."
5. **자유 대화**: 5분간 Claude와 자유롭게 대화

## QUIZ

> Block 0는 전통적인 퀴즈 대신 완료 확인으로 대체한다.

AskUserQuestion으로 물어본다:

"설치와 첫 대화가 완료됐나요?"
- "완료!" → Block 1로 이동
- "아직 진행 중" → 더 시간 드리기
- "오류 발생" → 오류 메시지 확인 후 해결 안내
